# executive

“Una vez autenticado con Passport, ¿el API valida que el card-key consultado pertenece al usuario de la sesión activa, o solo valida que el usuario esté logueado?”

holaa, me quedé revisando la arquitectura del API que mostraste y me demoré un poco, pero tengo algunas observaciones:

Lo primero que me llama la atención es el cifrado, sé que ya lo mencionaron, pero quiero dejarlo marcado. El canal va por HTTPS, eso está bien, pero si el payload no está cifrado por separado, en cualquier punto donde se haga TLS termination, ya sea un gateway o un load balancer, el PAN, el celular y el correo quedan viajando en claro internamente. Y eso para un atacante que ya esté adentro de la red es un pase libre.

“Lo otro es la Trace Table en RDX, si la trama llega ahí sin cifrar, básicamente estaríamos guardando el PAN en claro en base de datos, y eso ya es un hallazgo PCI-DSS directo.

Y una pregunta concreta sobre el endpoint GET /cards/{card-key}: ¿el API valida que el card-key que se consulta pertenece al usuario autenticado en la sesión, o solo valida que el usuario esté logueado? Porque si es lo segundo, alguien autenticado legítimamente podría consultar datos de otros clientes solo cambiando ese valor, ¿no?.

Por todo esto creo que sí debería entrar a Pentest antes de salir a producción.