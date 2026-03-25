# Post-Call Action Automator

> **Search Volume Signal:** "gong call analysis" (20/mo but $13.51 CPC = high commercial intent), "sales call recording" (480/mo), "revenue intelligence" (320/mo)
> **Composio Toolkits:** Gong, HubSpot, Salesforce, Gmail, Slack, Google Docs, Google Tasks

## What This Does

After every recorded sales call, automatically:
1. Pulls call transcript and AI summary from Gong
2. Extracts action items, objections, next steps, and buying signals
3. Updates the CRM deal record with call notes
4. Creates follow-up tasks with deadlines
5. Drafts a follow-up email based on what was discussed
6. Posts a deal update to the team Slack channel

## Composio Actions Used

### Gong (Call Intelligence)
- `List calls` — Find recently completed calls
- `Get call transcript` — Full conversation text
- `Get call details` — Duration, participants, topics discussed

### HubSpot (CRM Updates)
- `Search contacts` — Match call participants to CRM
- `Update deal` — Add call notes, update amount if discussed
- `Update deal stage` — Move based on buying signals
- `Create task` — Follow-up tasks with deadlines
- `Log email activity` — Record follow-up email sent

### Gmail (Follow-up)
- `Create draft` — Draft follow-up email for review
- `Send email` — Auto-send if confidence > threshold

### Google Docs (Documentation)
- `Create document` — Detailed call notes for deal room

### Google Tasks (Action Items)
- `Create task` — Personal follow-up reminders

### Slack (Team Updates)
- `Send message` — Post call summary to #deal-room or #sales-updates

## AI Extraction Template

From each call transcript, the AI extracts:

```yaml
call_summary:
  duration: "32 minutes"
  sentiment: "positive"
  participants: ["John (AE)", "Sarah (VP Eng at Acme)"]

action_items:
  - owner: "John"
    task: "Send pricing proposal for Enterprise tier"
    deadline: "2 business days"
  - owner: "Sarah"
    task: "Get security questionnaire from compliance team"
    deadline: "end of week"

buying_signals:
  - "Asked about annual pricing (budget allocated)"
  - "Mentioned evaluating 2 other vendors (active buying cycle)"
  - "Wants to pilot with 5 users first (land-and-expand)"

objections:
  - "Concerned about SSO integration with Okta"
  - "Current contract with competitor expires in 3 months"

next_steps:
  - "Send proposal by Thursday"
  - "Schedule technical deep-dive with Sarah's team"
  - "Follow up on security questionnaire next Monday"

deal_update:
  stage_change: "Discovery → Proposal"
  amount_update: "$45,000 ARR (Enterprise, 50 seats)"
```

## Setup

```bash
composio add gong
composio add hubspot        # or: composio add salesforce
composio add gmail
composio add googledocs
composio add googletasks
composio add slack
```

## Example Usage

```
"After my Gong calls today, extract action items, update HubSpot
 deals, create follow-up tasks, draft reply emails, and post
 summaries to #sales-updates in Slack."
```
