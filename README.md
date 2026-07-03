# executive

1.	¿Qué CA emite el certificado del servidor y ya confirmaron que seguirá siendo válido bajo las nuevas reglas (solo ServerAuth)?
	2.	¿Cómo está configurado el servidor hoy para validar el certificado de cliente entrante? ¿Contra qué CA(s) valida la cadena de confianza?
	3.	Cuando cambie el origen del certificado de cliente (de público a privado), ¿qué cambios se necesitan en el trust store / configuración del servidor para que reconozca la nueva CA?
	4.	¿El servidor va a aceptar certificados de cliente de una sola CA privada, o de múltiples (una por cada tercero)? ¿Cómo se gestiona esa lista de confianza?
	5.	¿Qué mecanismo usa el servidor para revocación (CRL/OCSP) de los certificados de cliente que reciba? ¿Está definido y probado?

	6.	¿Quién es responsable de generar y gestionar el certificado de cliente en este proyecto: Scotiabank, el tercero, o ambos según el caso?
	7.	Si es el banco quien conecta como cliente hacia otro sistema (BNS es cliente), ¿ya está usando o planea usar la CA privada interna del banco para ese certificado?
	8.	Si es el tercero quien se conecta como cliente hacia el banco, ¿con qué PKI va a generar su certificado — CA privada propia, servicio administrado, u otra opción?
	9.	¿Cómo se va a compartir e instalar la confianza en esa CA de cliente (intercambio de certificado raíz/intermedio, proceso de onboarding)?
	10.	¿Qué controles tiene definidos esa PKI de cliente en cuanto a vigencia del certificado, algoritmos permitidos y longitud de llave?
	11.	¿Cómo se gestiona la revocación del lado del cliente si se compromete una llave privada?

	12.	¿Cuál es el cronograma de migración: primero se ajusta el servidor, primero el cliente, o en paralelo?
	13.	¿Hay un ambiente de pruebas donde ya se validó el handshake completo con el certificado de cliente nuevo (de la CA privada) contra el servidor?
	14.	¿Qué pasa durante la transición — hay un periodo donde el servidor debe aceptar certificados de ambos orígenes (CA pública vieja y CA privada nueva) para no romper producción?
	15.	¿Está mapeado cada tercero/integración con su estado actual: cuál ya migró, cuál está en proceso, cuál no ha empezado?