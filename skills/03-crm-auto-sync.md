# CRM Auto-Sync from Email & Calendar

> **Search Volume Signal:** "sales automation CRM" (390/mo), "CRM automation tool" (210/mo), "hubspot automation" (480/mo), "salesforce automation" (590/mo)
> **Composio Toolkits:** Gmail, Outlook, Google Calendar, HubSpot, Salesforce, Pipedrive, Slack

## What This Does

Eliminates manual CRM data entry by automatically:
1. Scanning your inbox for prospect/customer emails
2. Extracting key information (meeting notes, deal updates, action items, objections)
3. Updating the correct CRM record (contact, deal, activity log)
4. Creating follow-up tasks based on commitments mentioned in emails
5. Updating deal stages based on conversation signals (e.g., "send me a proposal" → move to Proposal stage)

## Workflow

```
Email Inbox (Gmail/Outlook)
    │
    ├── New email from known contact
    │   │
    │   ▼
    │   ┌─────────────────────────────┐
    │   │ AI Analysis:                │
    │   │ - Is this deal-related?     │
    │   │ - Extract: action items,    │
    │   │   objections, next steps,   │
    │   │   sentiment, buying signals │
    │   │ - Detect stage change signal│
    │   └─────────────┬───────────────┘
    │                 │
    │                 ▼
    │   ┌─────────────────────────────┐
    │   │ CRM Update:                 │
    │   │ HubSpot: Log email activity │
    │   │ HubSpot: Update deal notes  │
    │   │ HubSpot: Move deal stage    │
    │   │ HubSpot: Create task for    │
    │   │          follow-up          │
    │   └─────────────────────────────┘
    │
    ├── Calendar event completed
    │   │
    │   ▼
    │   ┌─────────────────────────────┐
    │   │ Post-Meeting:               │
    │   │ Google Calendar: Get event  │
    │   │ AI: Generate meeting summary│
    │   │ HubSpot: Log meeting note   │
    │   │ HubSpot: Create follow-up   │
    │   │          tasks              │
    │   │ Slack: Post summary to      │
    │   │        deal channel         │
    │   └─────────────────────────────┘
    │
    └── New email from unknown contact
        │
        ▼
        ┌─────────────────────────────┐
        │ New Lead Detection:         │
        │ AI: Is this a sales inquiry?│
        │ Apollo: Enrich contact      │
        │ HubSpot: Create contact     │
        │ HubSpot: Create deal        │
        │ Slack: Alert sales team     │
        └─────────────────────────────┘
```

## Composio Actions Used

### Gmail/Outlook (Email Monitoring)
- `List messages` — Scan inbox for new prospect emails
- `Get message` — Read full email content for AI analysis
- `List threads` — Get conversation context

### Google Calendar (Meeting Tracking)
- `List events` — Find completed meetings
- `Get event` — Get meeting details, attendees, notes

### HubSpot (CRM — primary)
- `Search contacts` — Match email sender to CRM record
- `Update contact` — Add new data extracted from email
- `Log email activity` — Record email as activity on deal
- `Update deal` — Change deal notes, amount, stage
- `Create task` — Auto-create follow-up tasks from commitments
- `Batch read companies` — Pull company context for AI analysis

### Salesforce (CRM — alternative)
- `Log email activity` — Record email interactions
- `Update opportunity` — Sync deal changes
- `Create task` — Follow-up reminders
- `Log call` — Record call activities

### Pipedrive (CRM — alternative)
- `Update deal` — Sync pipeline changes
- `Create activity` — Log meetings and calls
- `Add note` — Attach AI-generated summaries

### Slack (Notifications)
- `Send message` — Post deal updates to team channels
- `Send direct message` — Alert deal owner on important signals

### Apollo (Enrichment for new leads)
- `Enrich person with Apollo` — Auto-enrich unknown senders

## Stage Change Detection

The AI looks for these signals in email content:

| Signal in Email | CRM Action |
|----------------|------------|
| "Send me a proposal" / "What's pricing?" | → Move to **Proposal** stage |
| "Let me check with my team" / "Need to discuss internally" | → Move to **Decision Maker Review** |
| "Can we schedule a demo?" / "Show me how it works" | → Move to **Demo Scheduled** |
| "We've decided to go with..." / "Send the contract" | → Move to **Closed Won** |
| "Not a priority right now" / "Maybe next quarter" | → Move to **Closed Lost** or **Nurture** |
| "Can you send more info about X?" | → Create task: "Send info about X" |

## Setup

```bash
composio add gmail          # or: composio add outlook
composio add googlecalendar
composio add hubspot        # or: composio add salesforce / composio add pipedrive
composio add apollo
composio add slack
```

## Example Usage

```
"Monitor my Gmail inbox. For every email from a contact in HubSpot,
 analyze the conversation, update the deal record with key takeaways,
 and create follow-up tasks. If someone asks for pricing, auto-move
 the deal to Proposal stage and alert me in Slack."
```
