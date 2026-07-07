# executive

Control Defect #	1
Title	Privileged Service Account with Excessive Permissions on CSF Source Systems (SQL Server, DB2 and File Servers) and SECADM Authority on the AS/400
Threat Category	Least privilege enforcement
Control Taxonomy	Privilege Access Management
Standards Impacted	Critical Information Asset Security Standard
Application Security Standard
Information And Systems Classification Standards.
Control Deficiency	The service account used by the Sterling MFT application has been granted admin (privileged) permissions on the CSF source systems from which the information is extracted — the SQL Server and DB2 databases and the file servers. This allows the account to access sensitive data and execute tasks or processes on those systems beyond what is necessary for the application to function.
In addition, on the AS/400 (iSeries) platform — which hosts the DB2 environment — the same account holds the SECADM special authority together with broad privileges over AS/400 objects. This allows the account to create application users and objects directly, without the authorization or identification of the Logical Access Control (LAC) team, which under the standard process is the only team authorized to create and approve new users. As a result, the account can provision access and create objects outside of established access-control governance.
Inherent Risk:	Impact: High
Likelihood: High
Inherent Rating: High
Risk Description	Loss of confidential information or unauthorized access due to the service account having privileged (admin) permissions on the SQL Server and DB2 databases and the file servers, allowing it to access sensitive data and execute tasks or processes on those systems. Additionally, through the SECADM authority on the AS/400 (iSeries), the account can create users and objects without LAC authorization, which could allow unauthorized provisioning of access, creation of accounts outside the standard flow, and unauthorized changes on the platform.
Existing Mitigating / Compensating Controls	1.  Permissions will be granted by Logical Access Control.
2.  Service account used by the application and not by named users.
Residual Rating	Impact: High
Likelihood: Medium
Residual Rating: Medium
Is an Issue?	No
Action Plan	Limit privileges for the CDADMIN user used in the CD Sterling tool and also prevent users from unsubscribing until support is obtained from the third-party entity (Santander Consumer).
Due date	July 1st 2027
Required Evidence for Closure	Updated application architecture documentation from Otilio confirming the reduced privilege model for the Sterling MFT service account; configuration evidence on the SQL Server and DB2 databases and the file servers showing removal of the admin/privileged access, and on the AS/400 (iSeries) showing removal/restriction of the SECADM special authority and elevated object privileges; functional testing report validating that Sterling MFT continues to operate correctly under the reduced permissions; and final sign-off from Luis Otilio Carrillo Lopez – IT Engineering Manager, confirming implementation.
Remediation Owner	Miguel Angel Bastidas Parco – IT Engineering Senior Manager
Target Rating	Target Rating: Medium-Low
Target Impact: High
Target Likelihood: Low
