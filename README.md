# executive

The Sterling MFT application's service account has been granted admin permissions on the CSF source systems (SQL Server, DB2 databases, and file servers). This means the account can access sensitive data and run processes on these systems well beyond what the application actually needs.
On the AS/400 (iSeries) side, things are worse. The same account has SECADM special authority, which gives it broad privileges over AS/400 objects. This allows it to create users and objects directly, without going through the Logical Access Control (LAC) team. Normally, LAC is the only team authorized to approve and create new users.
The result is that access and object creation happen outside the established governance controls, which creates a clear gap in the access-control framework.
