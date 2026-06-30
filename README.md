# executive

IS&C Access Control Standards; Least Privilege Principle
The service account used by the Sterling MFT application has been granted local admin (privileged) permissions on the Linux SFTP server. This allows the account to access sensitive data and execute tasks or processes on the server beyond what is necessary for the application's function.
Impact: High Likelihood: High Inherent Rating: High
Loss of confidential information or unauthorized access due to the service account having privileged permissions (local admin) that allow it to access sensitive data and execute tasks or processes on the server.
1. Permissions will be granted by Logical Access Control. 2. Service account used by the application and not by named users.
Impact: High Likelihood: Medium-Low Residual Rating: Medium
No
Analyze the specific permissions that the application user requires and limit the permissions, removing the local admin privileged permission.
To be indicated
Screenshots of updated permission configuration in the Linux SFTP server confirming removal of local admin privileges from the service account.
Miguel Angel Bastidas Parco – IT Engineering Senior Manager
Refers to the risk rating after the action plan is implemented. Target Rating: Medium-Low Target Impact: High Target Likelihood: Low
