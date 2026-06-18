# executive

Durante el análisis del ecosistema, la financiera opera un proceso de replicación de datos de tarjetas desde el Core BT hacia el Switch, donde se mantiene un card file consolidado que alimenta las autorizaciones de tarjetas de débito Mastercard. Este proceso se realiza mediante full refresh o partial refresh periódicos, lo que genera ventanas de inconsistencia durante las cuales el card file puede quedar con datos incompletos o viciados, incluyendo el PAN. La recomendación técnica, alineada con la práctica de Scotiabank y las capacidades de Evertech como proveedor, es migrar a un modelo de replicación event-driven donde cada cambio de estado en el Core gatille una actualización inmediata al Switch.

Un hallazgo de mayor severidad que identifiqué durante las conversaciones técnicas es la ambigüedad en la separación de llaves criptográficas en el HSM entre el banco y la financiera. No está claro si ambas entidades comparten llaves o si están correctamente segregadas, lo cual podría representar un riesgo de contaminación cruzada del CDE del banco comprador y comprometer su certificación PCI-DSS activa.

Finalmente, cse mencionó que la financiera opera con 3DES en los puntos de captura de PIN, específicamente en POS, ATMs y ventanillas. Si bien esto es un diseño válido para PIN Block encryption, PCI-DSS v4.0 exige la migración a AES, por lo que la financiera deberá tener un plan de migración de terminales como parte del proceso de integración post-adquisición.

