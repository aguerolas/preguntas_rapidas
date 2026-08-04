# executive

En la iniciativa de Actualización Masiva de Datos de Contactabilidad de clientes en VCAS el tema es que entre junio 2022 y mayo 2024 se deshabilitó el canal digital que permitía afiliar y actualizar la Clave Dinámica, y desde entonces los datos de contacto de nuestros clientes (teléfono, correo) dejaron de actualizarse automáticamente en VCAS.

VCAS es el servicio de Visa (3D Secure) que usamos para autenticar las compras online — cuando un cliente compra por internet, VCAS es quien genera y/o envía el OTP al cliente para validar la transacción. El tema es que si el dato de contacto que tiene VCAS está desactualizado (por ejemplo porque el cliente renovó su tarjeta o perdió el plástico y actualizó sus datos con nosotros, pero eso nunca llegó a VCAS), el OTP se manda al canal equivocado o simplemente no llega, y el cliente no puede terminar su compra.

Esto nos está generando abandono en el proceso de autenticación, transacciones no concretadas, y reclamos. Y como la SBS exige autenticación reforzada para operaciones digitales (Resolución 2286-2024 y el Reglamento de Seguridad de la Información 504-2021), estamos en falta si no lo resolvemos.

El objetivo es restablecer la actualización automática de esos datos hacia VCAS, para que la autenticación funcione bien, mejore la experiencia del cliente y reduzcamos el riesgo operacional y regulatorio.

La solución que estamos definiendo es un proceso batch mensual, donde Scotiabank sube un archivo con la información de contacto actualizada de los clientes a VCAS a través de un canal SFTP (que nos da el cifrado y seguridad en el transporte). Ya tenemos 3 historias de usuario mapeadas: (1) que los datos se sincronicen automáticamente vía batch, (2) que el cliente reciba el OTP correctamente con esos datos actualizados, y (3) habilitar el canal SFTP para que el equipo de tarjetas pueda cargar el archivo mensualmente.

Todavía nos falta: aprobar el Business Case, confirmar si la iniciativa entra en el plan anual, definir fechas de compromiso, y cerrar algunos puntos de seguridad de la información (cifrado, integridad del archivo, manejo de credenciales, trazabilidad/logs de cada carga) dado que estamos manejando datos personales de clientes y esto está enmarcado como una iniciativa de mitigación de riesgos.