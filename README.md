# executive

Data Flow Review:
Control-M is required to establish connectivity to a specific and predefined IP address registered within the bank’s infrastructure. Unlike WinSCP, Control-M does not store or expose credentials locally, as authentication is managed centrally through the platform’s secure credential vault, ensuring that sensitive access information is never handled manually or retained on endpoint devices.

Scope:
This assessment covers the temporary use of WinSCP as an SFTP file transfer client to transmit mandatory financial reporting documents to the BCR regulator, following the disruption caused by the regulator’s IP address change. The scope includes the evaluation of associated security risks, the existing compensating controls, and the definition of a remediation path toward the adoption of Control-M as the bank’s standardized and approved file transfer solution.

Considerations:
Since Control-M operates as an automated file transfer scheduler, it must be considered that automated jobs are subject to execution errors, connectivity failures, or misconfigurations that may go undetected without proper alerting. Therefore, adequate monitoring, error handling, and notification mechanisms must be established to ensure timely detection and response to any transfer failures, particularly given the regulatory nature of the transmitted files.

