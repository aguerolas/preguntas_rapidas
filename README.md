# executive

Risk Statement:

The residual risk rating is assessed as Medium based on the completion of risk assessment activities, given that the system handles confidential data with valuable integrity and Critical continuity requirements, which exposes the organization to the risk of unauthorized or wrong file transmission to the BCRP, which could result in inadvertent disclosure of confidential information or submission of incorrect regulatory data.



STRIDE Category
Threat Category
Existing Mitigating / Compensating Controls
Advisory Findings
Spoofing Identity
User authentication (IAM, SSO, federation)
Interactive access to the dedicated workstation is authenticated against the corporate domain using the accounting user's individual network credentials. The onward SFTP session to the BCRP is authenticated with credentials issued and controlled by the regulator. Authentication is enforced at both the endpoint and the destination; no anonymous or unauthenticated path exists.
N/A
Spoofing Identity
Unauthorized access (API, service, workload identity)
Not applicable. The transmission is a manual, human-operated process. No APIs, service accounts, or workload/machine identities participate in the workflow, so there is no programmatic identity surface to protect within the current scope.
N/A
Spoofing Identity
Privileged account protection (human + non-human identities)
Not applicable. The process runs under a standard, non-privileged accounting user account. No administrative, root, or other privileged human or non-human identities are used to execute the transmission.
N/A
Spoofing Identity
Phishing / social engineering
The workstation is a dedicated, single-purpose physical device with remote access disabled and outbound connectivity restricted to the single registered BCRP IP on port 9055. These controls limit the exploitability of any credential compromised via phishing. Enterprise-wide security-awareness controls apply to the user but sit outside the scope of this assessment.
N/A
Spoofing Identity
Certificate & key validation (mTLS, cert lifecycle)
The SFTP/SSH protocol authenticates the BCRP server through its SSH host key, validated by the client on connection. Mutual TLS is not part of the regulator-defined transport protocol; server authentication is provided via SSH host-key verification.
N/A
Tampering with Data
Unauthorized modification of bank data
The workflow only reads and transmits pre-generated regulatory files; it does not write to or alter source bank data. Files are produced by the AS-400 and consolidated on the file server upstream of this process. The risk of transmitting incorrect content is assessed under Control Defect #1.
N/A
Tampering with Data
Data leaving approved environments (egress risk)
Outbound connectivity scoped exclusively to BCRP registered IP address on port 9055.
Control Defect #1
Tampering with Data
Secret, password, and token protection
The BCRP-issued credentials are entered manually by a single named accounting user for each session, on a dedicated physical workstation that has remote access disabled and is not shared with other users. Outbound connectivity is restricted to the registered BCRP IP on port 9055, so the credential can only be used against the intended regulator endpoint. These controls constrain the exposure and misuse surface of the credential during the manual session.
N/A
Tampering with Data
Authorization enforcement (RBAC, ABAC, policy)
Authorization is enforced by restricting execution of the transmission to a single named accounting user on a single dedicated device. The task is not exposed to other users or roles; access to the physical workstation and the user account constitutes the authorization boundary for this process.
N/A
Tampering with Data
Cryptographic integrity protections
Data in transit is protected by the SFTP/SSH channel, which provides cryptographic integrity (message authentication) and confidentiality for the transmitted files, preventing undetected modification in transit.
N/A
Tampering with Data
Direct access to databases or storage
Not applicable. The process does not connect to any database. It reads consolidated flat files from the file server for transmission only; there is no direct or interactive database/storage access within scope.
N/A
Repudiation
Shared or non-attributable account usage
Interactive access to the workstation is tied to the accounting user's individual domain credentials, making endpoint actions attributable to a named individual. The absence of session-level logging for the transmission is addressed under Control Defect #1.
N/A
Repudiation
Logging, auditability, and non-repudiation
No centralized logging or automated audit trail for WinSCP sessions.
Control Defect #1
Repudiation
Digital signatures and transaction integrity
The regulator's protocol does not require client-applied digital signatures on the RCD files. End-to-end transaction integrity is evidenced by the BCRP delivery-confirmation email received on successful submission (Annex B), which serves as proof of receipt for each transmission.
N/A
Repudiation
Functional, system, and service accounts
Not applicable. No functional, system, or service accounts are used; the process is entirely interactive under a named user.
N/A
Information Disclosure
Data exfiltration or bulk download
Outbound connectivity is scoped exclusively to the registered BCRP IP on port 9055, so data cannot be redirected to an arbitrary destination; volume is limited to the defined monthly regulatory files. The absence of DLP inspection on this channel is captured under Control Defect #1.
N/A
Information Disclosure
Data protection at rest
The regulatory files reside transiently on the workstation and on the file server (PELMVIPR2AS20071). At-rest protection of these hosts is governed by the enterprise endpoint/server hardening and encryption standards, which fall outside the transmission scope of this assessment.
N/A
Information Disclosure
Data protection in transit
Files are transmitted over SFTP (SSH), providing encryption in transit between the workstation and the BCRP server. This satisfies the data-in-transit protection requirement for the Confidential classification.
N/A
Information Disclosure
Data lifecycle and records management
Retention and disposal of the regulatory files are governed by the institution's records-management policy and the BCRP's regulatory retention requirements. The data lifecycle is not managed by the transmission process itself and is out of scope for this assessment.
N/A
Denial of Service
Availability attacks (infra, app, API)
Not applicable. The service exposes no application, API, or infrastructure endpoint to inbound traffic; it is an outbound-initiated manual client. There is no attack surface for volumetric or application-layer availability attacks against the institution's side of this process.
N/A
Denial of Service
Internet-facing exposure
Not applicable. The workstation initiates outbound connections only and has remote access disabled; it presents no inbound or internet-facing listening service.
N/A
Denial of Service
Resilience, scaling, and failover
Scaling and failover are not relevant to this low-frequency, manual monthly process, which exposes no application or infrastructure service. Operational continuity of the transmission is managed under the institution's business-continuity arrangements and is outside the scope of this assessment, which is focused on the file-transfer control environment.
N/A
Elevation of Privilege
Least privilege enforcement
The accounting user operates with standard, non-administrative privileges limited to what is required to run the SFTP client and select the files for transmission. No privilege elevation is required or granted for the process.
N/A
Elevation of Privilege
Role design and entitlement management
A single, narrowly-scoped entitlement (execute the monthly BCRP transmission) is assigned to one role/user. The limited, well-defined entitlement minimizes role/entitlement complexity and scope for misassignment.
N/A
Elevation of Privilege
Lateral movement
The workstation is a dedicated physical device with remote access disabled and outbound traffic restricted to the single BCRP IP/port. This isolation constrains the ability to use the device as a pivot for lateral movement within the network.
N/A
General
Security monitoring and detection
Endpoint-level monitoring is provided by the enterprise security tooling deployed on the corporate workstation. Application-level visibility over the WinSCP transmission sessions specifically (session / audit events) is not centralized and is addressed under Control Defect #1.
N/A
General
Data loss prevention
No DLP controls on outbound SFTP transmissions.
Control Defect #1
General
Artificial intelligence / model risk
Not applicable. The system contains no artificial-intelligence or machine-learning components; it performs deterministic file transmission only.
N/A
General
System and workload hardening
The transmission runs on a dedicated, single-purpose physical device with remote access disabled, reducing its exposure surface. The use of WinSCP as non-standard, unapproved file-transfer tooling is the underlying deviation and is remediated by the migration to the approved Control-M tooling under Control Defect #1.
N/A
General
Other
No additional threat vectors beyond those enumerated above were identified as applicable to the current scope of this assessment.
