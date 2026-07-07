# executive

Summary
This TRA assesses the cybersecurity risks of the Sterling MFT file transfer initiative between CrediScotia and Santander Consumer Bank systems, carried out through a dedicated Linux SFTP server.
The main finding has to do with a service account holding privileged permissions beyond what's actually needed: admin access on the CSF source systems (SQL Server and DB2 databases, as well as the file servers), and SECADM special authority on the AS/400 (iSeries). This allows the account to access sensitive data, execute processes, and even create users and objects without going through the Logical Access Control (LAC) provisioning process.
The mitigating controls in place include permissions management through LAC and the use of service accounts rather than named user accounts. With these in place, the residual risk remains at Medium, with the expectation of lowering it to Medium-Low once the remediation actions are implemented.


risk statement

The overall risk of this assessment is rated as Medium. The identified risk arises from the service account's possession of privileged permissions, including administrative access on SQL Server, DB2, and the file servers, as well as SECADM authority on the AS/400, which grants the account the ability to create users and objects outside the standard Logical Access Control process. This exposes the organization to a potential loss or unavailability of information, as well as to unauthorized access provisioning. The existing mitigating controls reduce the likelihood of a data leak or of the risk materializing, thereby maintaining the residual risk level at Medium.
