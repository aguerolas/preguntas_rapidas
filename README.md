# preguntas_rapidas

PREGUNTAS TRA - SEGURIDAD DE APLICACIONES
Basado en OWASP ASVS + SBS 504
==========================================
 
1. AUTENTICACIÓN Y GESTIÓN DE SESIONES
---------------------------------------
1. ¿Cómo se implementa la autenticación de usuarios? ¿MFA obligatorio?
2. ¿Qué mecanismo se usa para gestionar sesiones (JWT, cookies, tokens)?
3. ¿Cuál es el tiempo de expiración de sesión activa e inactiva?
4. ¿Cómo se invalidan sesiones al cerrar sesión o cambiar contraseña?
5. ¿Existe protección contra fuerza bruta o bloqueo de cuenta?
6. ¿Las contraseñas se almacenan con hashing seguro (bcrypt, Argon2)?
 
2. AUTORIZACIÓN Y CONTROL DE ACCESO
--------------------------------------
7. ¿Cómo se implementa el control de acceso? ¿RBAC, ABAC, ACL?
8. ¿Se valida autorización en cada endpoint del lado del servidor?
9. ¿Existe riesgo de IDOR (acceso a recursos de otro usuario por ID)?
10. ¿Los usuarios pueden escalar privilegios horizontalmente o verticalmente?
11. ¿Existe separación de ambientes (dev, QA, prod) con accesos distintos?
 
3. SEGURIDAD DE APIs
----------------------
12. ¿Las APIs exponen datos sensibles innecesarios en sus respuestas?
13. ¿Existe rate limiting para prevenir abuso o DDoS a nivel de API?
14. ¿Se validan y sanitizan todos los parámetros de entrada en la API?
15. ¿Las APIs internas están protegidas igual que las externas?
16. ¿Se usa TLS en todos los endpoints? ¿Qué versión mínima?
17. ¿Cómo se gestiona el versionado y deprecación de endpoints?
 
4. MANEJO DE DATOS SENSIBLES
------------------------------
18. ¿Qué datos sensibles maneja la app? ¿PII, datos financieros, credenciales?
19. ¿Los datos en tránsito y en reposo están cifrados?
20. ¿Se aplica enmascaramiento o tokenización para datos de tarjetas (PAN)?
21. ¿Los logs registran datos sensibles accidentalmente?
22. ¿Existe una política de retención y eliminación segura de datos?
 
5. VALIDACIÓN DE ENTRADAS Y LÓGICA
-------------------------------------
23. ¿Se validan entradas tanto del lado del cliente como del servidor?
24. ¿Existe protección contra inyección SQL, NoSQL, LDAP, comandos OS?
25. ¿Cómo se previene XSS en outputs renderizados al usuario?
26. ¿Se procesan archivos subidos? ¿Qué validaciones existen sobre tipo y contenido?
27. ¿Existe lógica de negocio susceptible a manipulación de parámetros?
 
6. INFRAESTRUCTURA Y DESPLIEGUE
---------------------------------
28. ¿Dónde se despliega la app? ¿Cloud, on-premise, híbrido?
29. ¿Existe WAF delante de la aplicación?
30. ¿Los contenedores o instancias corren con el mínimo privilegio?
31. ¿Cómo se gestionan los secretos y credenciales en el despliegue?
32. ¿Existe un proceso de gestión de parches y vulnerabilidades de dependencias?
 
7. LOGGING, MONITOREO E INCIDENTES
-------------------------------------
33. ¿Qué eventos se registran en logs? ¿Intentos de login, cambios de privilegio, errores?
34. ¿Los logs son inmutables y están centralizados (SIEM)?
35. ¿Existe alertamiento ante comportamientos anómalos?
36. ¿Cuál es el RTO/RPO ante un incidente de seguridad?
37. ¿Existe un playbook de respuesta a incidentes para esta aplicación?
 
8. GESTIÓN DE TERCEROS Y CADENA DE SUMINISTRO
------------------------------------------------
38. ¿La app consume APIs o librerías de terceros? ¿Se revisa su seguridad?
39. ¿Se realiza análisis de composición de software (SCA) sobre dependencias?
40. ¿Los proveedores externos tienen acceso directo a datos o sistemas internos?
41. ¿Existe un proceso de due diligence de seguridad para nuevos proveedores?
