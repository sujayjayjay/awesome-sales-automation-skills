# Deal Room Automator & Stakeholder Tracker

> **Search Volume Signal:** "sales process automation" (480/mo), "deal management" (390/mo), "sales enablement" (3,600/mo)
> **Composio Toolkits:** HubSpot, Salesforce, Google Drive, Google Docs, Slack, Gmail, Asana, Notion

## What This Does

For every deal above a certain value, automatically:
1. Creates a structured deal room (Google Drive folder + Notion page)
2. Maps all stakeholders and their roles (champion, decision maker, blocker)
3. Tracks mutual action plan progress
4. Generates personalized follow-up content for each stakeholder
5. Alerts on stalled mutual action plans

## Composio Actions Used

### HubSpot (Deal Data)
- `Get deal` — Pull deal details, amount, stage, properties
- `Search contacts` — All contacts associated with deal
- `List activities` — Interaction history per contact
- `Update deal` — Sync mutual action plan status
- `Create task` — Follow-up reminders for stalled items

### Google Drive (Deal Room)
- `Create folder` — Deal room folder structure
- `Upload file` — Proposals, case studies, security docs
- `Share folder` — Grant prospect access to deal room
- `List files` — Track what prospect has viewed

### Google Docs (Documents)
- `Create document` — Mutual Action Plan template
- `Update document` — Update MAP with completed items
- `Create document` — Business case / ROI calculator

### Notion (Alternative Deal Room)
- `Create page` — Deal room page with databases
- `Update page` — Keep deal room current
- `Create database entry` — Track action items

### Slack (Internal Coordination)
- `Create channel` — #deal-{company-name} for internal coordination
- `Send message` — Deal updates and stalled action alerts
- `Pin message` — Pin key deal info (MAP link, stakeholder map)

### Gmail (Stakeholder Communication)
- `Send email` — Personalized follow-ups per stakeholder role
- `Create draft` — Executive summary for economic buyer

### Asana (Action Tracking)
- `Create project` — Mutual action plan as project
- `Create task` — Individual action items
- `Update task` — Mark items complete
- `List tasks` — Check for overdue items

## Stakeholder Map

```
Each deal contact is classified:

👑 Economic Buyer (EB)
   - Approves budget
   - Needs: ROI, business case, risk mitigation
   - Content: Executive summary, ROI calculator

🏆 Champion
   - Internal advocate
   - Needs: Ammunition to sell internally, technical proof
   - Content: Case studies, competitive comparison, demo recordings

🔧 Technical Evaluator
   - Validates technical fit
   - Needs: Documentation, API docs, security questionnaire
   - Content: Technical architecture doc, integration guide

⚖️ Legal/Procurement
   - Reviews contracts
   - Needs: Redlines, compliance docs, vendor forms
   - Content: MSA, DPA, SOC2 report, vendor questionnaire

🚫 Blocker (if identified)
   - Risks derailing the deal
   - Needs: Direct addressing of concerns
   - Content: Objection-specific one-pagers
```

## Mutual Action Plan Template

```markdown
# Mutual Action Plan: {Company} × {Your Company}
Target Close Date: {date}

| Step | Owner | Due | Status |
|------|-------|-----|--------|
| Technical evaluation complete | {Tech Lead} | {date} | ✅ |
| Security review submitted | {Your Team} | {date} | 🔄 |
| Business case presented to CFO | {Champion} | {date} | ⬜ |
| Legal review of MSA | {Procurement} | {date} | ⬜ |
| Pilot kickoff | {Both} | {date} | ⬜ |
| Final contract signed | {EB} | {date} | ⬜ |

⚠️ At Risk: {item} is {X} days overdue
```

## Setup

```bash
composio add hubspot        # or: composio add salesforce
composio add googledrive
composio add googledocs
composio add slack
composio add gmail
composio add asana          # or: composio add notion
```

## Example Usage

```
"For every deal over $50K that moves to 'Proposal' stage in HubSpot,
 create a deal room in Google Drive, a Mutual Action Plan in Google
 Docs, a Slack channel #deal-{company}, and map all stakeholders.
 Alert me when any MAP item is overdue by 3+ days."
```
