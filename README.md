# executive

backgroung
Crediscotia, a financial institution previously part of the Scotiabank group, has been sold to Santander Consumer Bank. In this context, the Sterling MFT information transfer initiative is being developed to send Santander Consumer information from SQL and DB2 (AIX and iSeries) databases to Santander, using the existing Linux SFTP server and the Connect Direct service (Sterling MFT). The solution proposed by SBP is being adapted to CrediScotia's infrastructure/architecture.

The purpose of this TRA is to assess the cybersecurity risks associated with the Sterling MFT file transfer initiative from CrediScotia systems to Santander Consumer Bank via a dedicated Linux SFTP server. The primary identified risk involves a privileged service account (local admin) that can access sensitive data and execute processes on the server. Mitigating controls include Logical Access Control permissions management and the use of service accounts rather than named user accounts. The overall residual risk level is rated Medium, with a target rating of Medium-Low once remediation actions are implemented


BJG3 – Sterling Secure File Transfer – Perú
Sending information from the various CSF platforms and services to the SFTP server (Linux) in a planned, progressive, and coordinated manner. Retrieval of information temporarily stored on the SFTP service by the external entity Santander Consumer Bank.


The overall risk of this assessment is rated as Medium. The identified risks involve the possible loss or unavailability of information due to privileged permissions. However, mitigation controls prevent data leaks or the materialization of the risk. This contributes to the overall risk level of all identified risks being medium.

