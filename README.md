# executive
El principio general
Santander compró Crediscotia, pero durante el TSA el banco (BNS) sigue dando soporte técnico. La arquitectura está diseñada para que los colaboradores de Santander puedan operar Crediscotia sin tocar jamás los sistemas ni datos de BNS.


Las 4 capas de protección
1. Red : separación física/lógica
	•	Firewalls e IPS entre BNS y Crediscotia
	•	VRFs (redes virtuales separadas dentro del mismo equipo) que aíslan el tráfico
	•	VPN Vendor solo para proveedores autorizados, con perfil restringido
1. Acceso de usuarios : solo los aprobados entran
	•	Zscaler controla el acceso a internet/sistemas: solo 64 usuarios en un AD Group específico pueden pasar
	•	El Active Directory compartido PER.BNS, se está limpiando: todos los usuarios de Santander deben ser eliminados post-LD1
	•	Certificación de accesos lógicos antes de LD1 para verificar quién tiene qué
1. El puesto de trabajo: Cloud PC como caja sellada
	•	Los colaboradores de Santander que necesitan acceso operan desde un Cloud PC en el tenant de Santander (no en infraestructura BNS)
	•	Sin copy/paste, sin drives mapeados, con DLP y MFA
	•	Lo que ven no puede salir de esa sesión
1. Transferencia de datos - un único canal controlado
	•	El único canal autorizado para mover datos es el SFTP en DMZ
	•	Autenticación mutua por clave pública SSH (equivalente a mTLS pero en SFTP)
	•	IP Whitelist + puerto no estándar = solo quien debe conectarse puede hacerlo

Posible riesgo que aún puede existir
Lo que aún está pendiente o es riesgo
Posibles huecos, los más relevantes al tema son:
	•	Reglas firewall heredadas any-to-any. Podrían heredar cosas no especificas para esta situación ya que el enfoque fue otro en un principio 
	•	SFTP sin logs en QRadar todavía: transfieren datos pero no se menciona un monitoreo centralizado
	•	Cloud PC controlado por Santander (BNS no puede auditar qué pasa dentro): 
El Cloud PC está en el tenant de Santander, o sea que Santander administra ese entorno : las políticas, los logs, quién puede ver qué dentro de esa sesión.
BNS sí diseñó controles sobre el Cloud PC sin copy/paste, sin drives, DLP, MFA y eso está bien. Pero no se puede verificar de forma independiente que esos controles se estén cumpliendo, porque no tiene visibilidad dentro del tenant de Santander.