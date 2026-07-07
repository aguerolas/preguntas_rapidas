# executive

Risk Description
Loss of confidential information or unauthorized access. The service account has admin permissions on the SQL Server and DB2 databases and file servers, so it can access sensitive data and run processes on those systems with no real restrictions. On top of that, the account has SECADM authority on the AS/400 (iSeries), which means it can create users and objects without any LAC approval. This opens the door to unauthorized access provisioning, rogue user accounts created outside the standard process, and unauthorized changes on the platform.
