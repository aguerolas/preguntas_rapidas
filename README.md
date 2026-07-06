# executive

Background
What does this system or service provide?
Credit Card Core (CSF) is an information system responsible for the operational transfer of embossed credit card files between Credi Scotia Financiera (CSF) and its card personalization vendors. Regulatory-adjacent operational files are generated through Control M (system PETESBSTCD000) and retrieved by the SFTP user “usdsac”, which connects using WinSCP — an SFTP client — from designated workstations (IPs: 10.237.83.135, 10.37.168.178, and 192.168.100.55) to the destination server “CL_7737_7738.per.bns”, owned by Scotiabank.
The files are originally transmitted by the provider Izipay and subsequently consumed by the vendors Prosegur and DocFlow for the physical embossing and dispatch of credit cards. The end-to-end process is executed by designated users within the Operaciones Tarjetas de Crédito - Santander area (Marco Antonio Merino and Rony Arturo Huaman).

Executive Summary
The request was presented related to the EPM number “BBL7 - Credit Card Core (CSF)”. The application team requested the enablement of firewall port 22, required for a designated user to send and retrieve documents via SFTP using the WinSCP tool.
The urgency of this request was driven by an operational requirement: due to a Disaster Recovery (DR) related issue, the assigned user was unable to connect to the destination server, preventing the Santander operations team from reviewing and processing the requirements sent by the provider Izipay toward the vendors Prosegur and DocFlow.
As part of the security review, it was identified that this file transfer is being performed through WinSCP, an SFTP client that does not align with the bank’s approved and standardized file transfer tooling — consistent with the findings documented in the related prior assessment TRA-19458. Additionally, it was identified that the SFTP credential (user “usdsac”) used to authenticate the connection is not stored within an enterprise credential vault (PAM or Hashicorp), and is instead known and manually entered by operational personnel at the start of each session.
Given the risks identified in the use of this tool — including credential exposure to users not governed by centralized security controls — this security artifact (TRA) was requested, together with the conformity of the IT Owner, the VP, and the EPM, prior to enabling the requested connectivity.
A defined group of users within the Operaciones Tarjetas de Crédito - Santander area was granted access to perform the file retrieval process in support of the operational continuity of the embossed card file exchange.

Data Element
The system processes credit card personalization data classified as Confidential, including:
●	Tipo de Emisión
●	Tipo de Tarjetas
●	Número de Tarjeta Encriptada
●	Dirección
●	DOI
●	Nombre

In Scope
●	Use of WinSCP as an SFTP file transfer client for the user “usdsac” to retrieve embossed card files from the destination server CL_7737_7738.per.bns.
●	Manual enablement of firewall port 22 to restore connectivity following a Disaster Recovery (DR) related disruption.
●	Use of an SFTP credential (“usdsac”) that is not stored within an enterprise credential vault (PAM/Hashicorp).
●	End-to-end handling of the transfer workflow, including session initiation, file retrieval, and delivery to the vendors Prosegur and DocFlow, carried out by designated users within Operaciones Tarjetas de Crédito - Santander.

Risk Statement:
The residual risk rating is assessed as Medium based on the completion of risk assessment activities, given that the system handles confidential cardholder data (encrypted card number, DOI, name, and address) with valuable integrity, high availability, and critical continuity requirements, which exposes the organization to unauthorized access, credential misuse, or erroneous file handling. This risk could result in inadvertent disclosure of confidential cardholder information or disruption of the embossed card issuance process.
Assumptions
The workstations used to connect to the destination server (10.237.83.135, 10.37.168.178, and 192.168.100.55) are accessed only by designated users within the Operaciones Tarjetas de Crédito - Santander area (Marco Antonio Merino and Rony Arturo Huaman), who authenticate using the SFTP credential “usdsac” at the start of each WinSCP session. This credential is not currently stored within an enterprise credential vault (PAM or Hashicorp).


