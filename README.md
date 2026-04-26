# executive

Code Review Observations by Architecture & Security Advisory Teams:
	•	The bank’s security standards mandate the use of Control-M as the approved file transfer solution, as it provides enhanced security controls, centralized logging, and governance capabilities that align with the institution’s risk management framework.
	•	WinSCP, as a standalone SFTP client, operates outside the bank’s managed tooling ecosystem, lacking the auditability, access control enforcement, and automated alerting capabilities required for regulated data transmission.
	•	The current file transfer architecture does not meet the bank’s baseline security requirements and represents a gap that must be remediated through the formal adoption of Control-M.

Short-Term – Compensating Controls During WinSCP Temporary Exception:
	•	Restrict WinSCP usage exclusively to the authorized user account designated for BCR file transmission. No additional users should have access to this client.
	•	Ensure that SFTP credentials used by WinSCP are unique, non-shared, and stored in a secure password vault. Manual storage of credentials in configuration files is strictly prohibited.
	•	Firewall rules must be configured to allow outbound traffic exclusively to the BCR’s registered IP address on the approved port, with no broader access permitted.
	•	All file transfer sessions conducted via WinSCP must be logged and retained in accordance with the bank’s log management policy.

Medium-Term – Migration to Control-M:
	•	The application team must submit a migration plan to adopt Control-M as the file transfer mechanism for BCR reporting.
	•	Control-M jobs must be configured to connect exclusively to the BCR’s predefined and registered IP address.
	•	Credentials must be managed through Control-M’s centralized credential vault, targeting to eliminate any manual handling of authentication information.
	•	A UAT (User Acceptance Testing) phase must be completed before decommissioning WinSCP to validate end-to-end file transmission through Control-M.

Long-Term – Governance & Monitoring:
	•	Automated alerting must be implemented to notify the responsible team of any job failure, timeout, or connectivity issue during file transmission.
	•	Periodic access reviews must be conducted to ensure only authorized accounts interact with the Control-M jobs and the BCR endpoint.
	•	This architecture must be documented and registered as the approved standard for regulatory file transmissions going forward.



