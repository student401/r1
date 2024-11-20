# Customer Tickets Management Guidelines

## Last Improvements Proposed by Support

- **RCA:** When support requests RCA, share findings and reasons for accepting/rejecting the ticket. No need for a separate ticket.
- **Lowering Priority:** Provide a validated workaround to lower the ticket priority.
- **Customer's Data - DU:** Seek customer and managerial approval for changing customer data via a dedicated TPOPS JIRA ticket.
- **Moving Bug to WI:** If support cannot reproduce the reported issue, move it to a Work Item.
- **Testing/Validation by Support:** Support can test fixes for RE and On-Prem deliveries.

---

## Dedicated Team

- **Role:** Forensic Team monitors and investigates customer issues (WI & Bugs) since Feb 2022.
- **Objectives:**
  - Monitor incoming issues and provide first-level analysis.
  - Share findings, RCA, and fixes via JIRA comments.
  - Dispatch tickets among teams/projects.
  - Maintain 100% SLA.
  - Provide quick fixes to unblock customers if feasible.
  - Enhance knowledge base: [TMC Support FAQ](https://wiki.talend.com/display/rd/TMC+Support+FAQ).

---

## Tools

- **JIRA Board:** [TMC Customer Issues - Agile Board](https://jira.talendforge.org/secure/RapidBoard.jspa?rapidView=483).
- **Slack Integration Script:** [JIRA to Slack](https://github.com/Talend/talend-slack-bots/tree/main/jira-to-slack).
- **Metrics & Dashboards:** Tableau SLA Dashboards.

---

## Customer Ticket Life Cycle

### New
1. Support creates a ticket under TMC or TPOPS project.
2. Verify the problem description template. If missing, set the ticket **On Hold**.
3. Investigate and document findings in the dedicated Slack channel.

   **Outcomes:**
   - Request more inputs: Set status to **On Hold**.
   - Not a bug or customer-side issue: Add RCA and set status to **Rejected**.
   - Real bug: Propose a fix version in Slack and set status to **Accepted**.

### On Hold
- Status for missing information or template usage requests.
- Check and follow up after 3 weeks.

### Accepted
- Confirm issue as a product bug.
- Determine feasibility and set a "fix version" before marking **Accepted**.

### In Progress / Code Review / Validation / Done
- Follow internal ticket processes.

---

## Moving Tickets to Different Projects

- Investigate if the issue pertains to a different project (e.g., TPSVC, ESB).
- Communicate changes via Slack or to the appropriate contact. Refer to the [Products Org](https://wiki.talend.com/display/rd/Products+Org).

---

## SLA Guidelines

- SLA starts from ticket creation or status change to **New**:
  - **Blocker:** 2 business days.
  - **Critical:** 3 business days.
  - **Major:** 10 business days.
  - **Minor:** No SLA.
- SLA halts when the ticket is **On Hold**, **Accepted**, or **Rejected** and resets when returned to **New**.
- SLA script results are available in the Slack channel.

---

## Communication with Support

- Use **JIRA comments** exclusively for communication.
- Be factual and polite. Customer-facing comments should be professional.
- Avoid promises; confirm with PO/EM before committing.
- If unsure, consult PO, EM, or QA Lead.

---

## How QA Team Members Can Help

- **Review:** Validate priority, version, and duplicate checks.
- **Fix Validation:** Analyze and address testing gaps.
- **Enhance Testing:** Add or update tests for better coverage.

---

## SLA Monitoring Script

- **Automated Job:** [Jenkins SLA Monitoring](https://jenkins-tmc.datapwn.com/job/tmc-qa-sla-monitoring/).
- Runs thrice daily for TMC, TPOPS, and TPSVC projects.
- Results published in Slack for action.

**FAQs:**
- For script issues, use manual instructions at [GitHub](https://github.com/Talend/tmc-qa/tree/master/scripts/prod_issues_sla_monitoring).

---

For further details, refer to:
- [JIRA Template Usage](https://wiki.talend.com/display/rd/Jira+Template+Usage+for+Talend+Support).
- [SLA Automation Script](https://github.com/Talend/tmc-qa/tree/master/scripts/prod_issues_sla_monitoring).
