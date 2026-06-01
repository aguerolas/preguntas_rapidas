# executive

Executive Summary / Background:

The Scotia Correo – CSF system is an application that enables the automated sending of files via email, FTP, and SFTP to both internal and external clients. It currently operates through the mailbox crediscotiacorreo@crediscotia.com.pe, which holds an active DLP exemption for sending attachments, as the process runs in a fully automated manner requiring no manual intervention.

As part of the Transition Service Agreement (TSA) process, this mailbox has been identified for decommissioning upon the conclusion of the transition period, once all associated operational services have been formally transferred. Given that the mailbox serves as the central dispatch point of the CSF system, its decommissioning represents a critical event that must be managed with appropriate controls to ensure operational continuity until its definitive closure and proper deactivation.

Scope of Impact:

The following business processes directly depend on this mailbox and will be affected by its decommissioning:

	•	Telebanking (B3QW)
	•	Collections / Recaudaciones (BBKY)
	•	Electronic Factoring (B3TD)

Operational Flow at Risk:

The CSF service operates under the following flow, which will be disrupted upon mailbox decommissioning:

	1.	The GetAS400 service continuously reads files left by client applications and copies them to the SPLA-WFTP2 server.
	2.	Applications outside the AS400 environment copy files directly to the SPLA-WFTP2 server.
	3.	The ScotiaCorreo service verifies, validates, and transfers files to the file server SPLA-WCFS3.
	4.	The file configuration is validated against the database and the recipient’s registration is confirmed.
	5.	The email is sent to the configured recipient via SMTP.
	6.	The sent file is stored in the OUTBOX folder and all operations are recorded in the LOG folder.

Risk Considerations Associated with Decommissioning:

	•	Loss of the automated communication channel with clients currently receiving files via email.
	•	Potential disruption of the sending flow if the mailbox decommissioning is not properly coordinated with the migration or replacement of the receiving service.
	•	The active DLP exemption on this mailbox must be formally revoked as part of the closure process.
	•	The associated servers (SPLA-WFTP2, SPLA-WCFS3) are currently undergoing migration under a Software Currency project; therefore, the mailbox decommissioning must be aligned with the progress of said initiative.
	•	Historical sending records stored in the OUTBOX folder and LOG files must be preserved or migrated prior to executing the definitive decommissioning.