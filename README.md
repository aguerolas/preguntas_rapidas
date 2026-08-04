# executive

Role design and entitlements for these applications were inherited from the pre-transition setup and continue to operate on top of the Scotiabank platform’s own privileged-access controls under the TSA. No evidence has been found in the documentation formally validating the role design of each legacy application after the transition, which is what Control Defect #1 records here.

Authorization roles were carried over unchanged from the pre-transition setup and are enforced by each application’s own authorization layer within the Scotiabank OnPrem environment inherited under the TSA. No new roles or permission schemes were created as part of the transition.

Access to these applications is mediated by the identity and access management services inherited from the Scotiabank environment under the TSA. Together with the network segmentation in place, this limits service and workload level exposure. No new interfaces or integrations were added during the transition

Entitlements are administered through the roles inherited from before the transition, on top of the Scotiabank platform’s own privileged-access controls under the TSA. Users hold the access their business role requires and nothing broader.