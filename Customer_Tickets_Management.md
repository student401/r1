# Customer Tickets Management Guidelines

## Last Improvements Proposed by Support
- RCA: When support asks for RCA, they do not ask for the five why. They are asking to share what we found and what led us to accept or reject the ticket.
- No need to open a separate ticket. In case the SLA is ticking, we can set a lower severity.
- Lowering Priority: When we provide a validated workaround on an issue, we can lower the priority of a ticket.
- Customer's Data - DU (Deployment Unit): When we need to change customer's data, we should ask for customer's approval as well as managerial approval with a dedicated TPOPS JIRA ticket of type DU.
- Moving Bug to WI: If support cannot reproduce a customer issue reported through a bug by support, we can move it to Work Item.
- Testing/Validation by Support: Support is glad to test any fix we can provide (applicable for RE and On-Prem deliveries).

## Dedicated Team
- Since Feb 2022, the Forensic Team is in charge of monitoring and first investigations of incoming customer issues (WI & Bugs).
- Team is led by ().

## Team’s Objectives
- Monitor incoming customer issues and provide the first level of analysis.
- Follow-up with support on findings, RCA, and potential fixes through comments in Jira.
- Based on the analysis, dispatch tickets among TPOPS teams or other projects.
- Keep SLA at 100%.
- If feasible, provide a quick fix to unblock customers.
- Continue to enhance our knowledge base [TMC Support FAQ](https://wiki.talend.com/display/rd/TMC+Support+FAQ) as we often have similar tickets and searching in Jira on closed tickets is challenging. This will also help share knowledge on troubleshooting techniques, links, code references, etc. This page should be organized by precise theme with Jira ticket references.

## Tools
- **Customer Issues Jira Board:** [TMC Customer Issues - Agile Board - Talend Open Integration Solution](https://jira.talendforge.org/login.jsp?os_destination=%2Fsecure%2FRapidBoard.jspa%3FrapidView%3D483).
- **Jira Template:** Usage for Talend Support - Wiki R and D Team - Talend In.
- **Slack Channel Creation Script:** [GitHub Repository](https://github.com/Talend/talend-slack-bots/tree/main/jira-to-slack).
- **SLA Script:** The automated script is run a few times a day, and detailed results of customer issues in New status are published in the `#tmc_customer_issues` Slack channel.
- **Script for SF Case Closure:** (Owned by Support).
- **Customer Issues Dashboards:** TMC/TPOPS Customer Issues Data - Talend Open Integration Solution.
- **Tableau:** Charts, metrics, and historical data - Tableau SLA Dashboards.

## Customer Ticket Life Cycle (Activities & Actions)
### New
- Support creates a new ticket under TMC or TPOPS project.
- Check if the Jira template was used for the problem description. If not, or if information is missing, request template usage and set the ticket to On Hold.
- If enough details are provided, start the investigation. Share findings in the dedicated Slack channel for the ticket. Invite other TPOPS team members if needed or folks from external teams. Do not change ticket status until you come to a conclusion.
  - If more inputs are needed from support, request them in Jira comments and set the ticket to On Hold.
  - If the described issue is not a bug or the problem is on the customer side (network, infra, wrong product usage, etc.), add a comment in the Jira ticket with a short RCA and set Jira status to Rejected.
  - If it's a real product bug, propose a "fix version" in the dedicated Slack channel and set ticket status to Accepted.

### On Hold
- Set a ticket On Hold when requesting template usage or if information is missing.
- Regularly check tickets that remain On Hold for 3 weeks. Relaunch support through comments in the Jira ticket.

### Accepted
- After investigations confirm that the reported issue is a product bug. Confirm the feasibility of a fix and the fix version in the dedicated Slack channel. It’s mandatory to set a "fix version" when accepting a customer ticket.

### In Progress / Code Review / Validation / Done
- Follow the same process as for internal tickets.

### Moving Tickets Under a Different Project
- If, after investigations, you find that an issue is not related to TMC, move your ticket to the corresponding project (TPSVC, ESB, etc.) and communicate this change to the right person or post a message in the appropriate Slack channel.
- Main contacts per product or component can be found here: Products Org - Wiki R and D Team - Talend In.
- How to move Jira under a different project: [Link](https://login.microsoftonline.com/...).

## SLA
- Customer bugs (OTRS ID attached to Jira tickets) are part of Talend SLA engagement. SLA is calculated from the time (precise time, not just the day) the ticket was created or the status changed to New until the current date:
  - Blocker issue 2 business days
  - Critical issues 3 business days
  - Major issues 10 business days
  - Minor no SLA

- To check when SLA expires, review SLA script results in the `#tmc_customer_issues` Slack channel. The script runs multiple times daily.
- SLA stops if a ticket is set to On Hold, Accepted, or Rejected. SLA restarts (being reset) if a ticket is set back to New.

## Communication with Support
- Support should not contact you directly, except for specific cases (e.g., calls with a customer, or necessary calls with support).
- Communication should only be through comments in the Jira ticket.
  - Be polite, factual, and precise in your answers and requests, as all comments are visible to customers.
  - Do not promise a solution but confirm with your PO or EM potential delivery milestone. Do not change status to Accepted without confirmation from PO or EM. The same goes for the Fix Version.
  - If you have doubts about how or what to communicate in a support ticket assigned to you, check with your PO, EM, or QA Lead.

## #salesforce
- Tag to be used in Jira comments when:
  - Asking for more details on the ticket.
  - Providing results of first investigations and asking for confirmation or more info.
  - Providing RCA.

## Ask-tmc Slack Channel
- [Ask-tmc Slack Channel](https://talend.slack.com/archives/CEWQ3BZGA)
  - No SLA or obligation to reply on this channel. We reply on a best-effort basis.
  - Very active with many questions from Talend support. We avoid unnecessary ticket creation by answering questions here.
  - If a question from support is tricky or needs investigation into a potential product bug, ask support to create a ticket (WI for questions, bug for potential product defects using our official Jira template).

## How QA Team Members Can Help
- **Review the Bug Item:**
  - Review priority: is it matching the support statement?
  - Found in version: Ensure it is correct as the support team might have errors due to monthly releases.
  - Ensure the ticket is not duplicated with an internal bug.
- **Validate the Fix.**
- **Analyze Why the Bug Was Missed by Testing:**
  - Add missing tests or update existing tests so that the bug is caught next time.
  - Check that the new or updated test properly fails on an unfixed stack.
  - If the action is too large to be handled within the same ticket, create a work item and collaborate with your Team and QA leaders to prioritize it.

## SLA Monitoring Script
- To simplify SLA expiration monitoring, use the automated Jenkins job located [here](https://jenkins-tmc.datapwn.com/job/tmc-qa-sla-monitoring/).
- The script currently supports TMC, TPOPS & TPSVC projects.
  - Provides a list of items and SLA expiration calculations. You can comment under any ticket and tag people to review it.
  - In TMC & TPOPS, this job is scheduled to run 3 times a day. It is possible to automate for other projects.
- In case of a Jenkins issue, the script can be run manually as explained [here](https://github.com/Talend/tmc-qa/tree/master/scripts/prod_issues_sla_monitoring).
- Script results are published in the `#tmc_customer_issues` Slack channel.
- Output can be directly copied/pasted into Slack.

### Common Questions on Script Usage
- **I can't run a job. Is Jenkins disabled?**  
  No. You need to be authorized in Talend Github/Okta to run it.
- **Does the Jenkins job still use the JS script (the one I ran manually in Chrome console)?**  
  No. The script is located [here](https://github.com/Talend/tmc-qa/tree/master/scripts/prod_issues_sla_monitoring). The Jenkins job pulls the latest changes from GIT each time it runs.
- **Can we use a custom script since we updated it a bit to meet our requirements?**  
  Yes. Don’t hesitate to improve the script [here](https://github.com/Talend/tmc-qa/tree/master/scripts/prod_issues_sla_monitoring). If it’s a filter change, we can discuss how to adjust our common script. Ping () or create a PR.
- **Our project in Jira is XXXX, Slack channel for posting issues would be the same name?**  
  If there is no Slack channel with your project name, feel free to create one following our [documentation](https://github.com/Talend/tmc-qa/blob/master/README.md). Ping () for validation.
## Using Technical Users for API Access (Jira & Slack)
We have already requested technical users to utilize APIs for Jira and Slack. Currently, we have one technical user for Jira, and we are waiting for approval for Slack. For access and implementation, only a Jira user is necessary.

### How Other Teams Can Utilize the Technical Setup
1. **Improve the Script**: Customize the script available at [https://github.com/Talend/tmc-qa/tree/master/scripts/prod_issues_sla_monitoring](https://github.com/Talend/tmc-qa/tree/master/scripts/prod_issues_sla_monitoring) based on your team's needs. Be particularly cautious with the JQL query. At present, it searches for all new items with an `OTTRS_ID`.
2. **Request Jira Credentials**: Obtain credentials for a technical (Jenkins) account. This is a security requirement. Submit a Zendesk ticket to request access.
3. **Clone a Jenkins Job**: Duplicate the Jenkins job found at [https://github.com/Talend/tmc-qa/blob/master/.Jenkins/Jenkinsfile-slamonitoring](https://github.com/Talend/tmc-qa/blob/master/.Jenkins/Jenkinsfile-slamonitoring) to your Continuous Integration (CI) environment. For testing purposes, you can validate your project's report using the TMC Jenkins setup.
