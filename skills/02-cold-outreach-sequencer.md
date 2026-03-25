# Cold Outreach Sequencer

> **Search Volume Signal:** "cold outreach" (590/mo), "outreach automation" (210/mo), "cold email automation" (170/mo), "instantly" (27,100/mo)
> **Composio Toolkits:** Apollo, Gmail, HubSpot, LinkedIn, Slack

## What This Does

Builds and executes personalized cold outreach sequences across email and LinkedIn:
1. Pulls qualified leads from your CRM or Apollo searches
2. AI-generates hyper-personalized email copy using prospect data (company news, job changes, tech stack)
3. Creates multi-touch sequences: Email → LinkedIn connection → Follow-up → Break-up email
4. Tracks opens, replies, and meetings booked — updates CRM automatically
5. Alerts you in Slack when a prospect replies or books a meeting

## Workflow

```
Qualified Lead List (from CRM or Apollo Search)
    │
    ▼
┌─────────────────────────────┐
│ Step 1: Prospect Research   │
│ Apollo: Enrich person       │
│ Apollo: Get Organization    │
│         Job Postings        │
│ Firecrawl: Scrape company   │
│           news page         │
│ Exa: Search recent mentions │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│ Step 2: AI Personalization  │
│ Generate email using:       │
│ - Recent company news       │
│ - Prospect's role & pain pts│
│ - Mutual connections        │
│ - Tech stack overlap        │
│ - Job postings (hiring =    │
│   growth signal)            │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│ Step 3: Sequence Execution  │
│ Day 1: Gmail: Send email    │
│ Day 2: LinkedIn: Connection │
│        request + note       │
│ Day 4: Gmail: Follow-up #1  │
│ Day 7: Gmail: Follow-up #2  │
│        (value-add content)  │
│ Day 10: Gmail: Break-up     │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│ Step 4: Track & Update      │
│ Gmail: Check for replies    │
│ HubSpot: Log email activity │
│ HubSpot: Update deal stage  │
│ Slack: Alert on replies     │
└─────────────────────────────┘
```

## Composio Actions Used

### Apollo (Prospecting)
- `Enrich person with Apollo` — Full prospect profile
- `Enrich organization data` — Company context for personalization
- `Get Organization Job Postings` — Hiring signals = budget exists
- `Add Contacts to Sequence` — Use Apollo's built-in sequencing
- `Search organizations in Apollo` — Find new targets matching ICP

### Gmail (Outreach)
- `Send email` — Deliver personalized cold emails
- `Create draft` — Queue emails for review before sending
- `List messages` — Track replies and engagement
- `Get message` — Read reply content for AI analysis

### LinkedIn (Social Selling)
- `Send connection request` — With personalized note
- `Send message` — Follow-up after connection accepted

### HubSpot (CRM Tracking)
- `Create contact` — Add prospect to CRM
- `Log email activity` — Record all touches
- `Update deal stage` — Move to "Contacted" → "Replied" → "Meeting Booked"

### Slack (Notifications)
- `Send message` — Alert #sales-alerts channel on replies
- `Send direct message` — Notify assigned rep

### Firecrawl + Exa (Research)
- `Scrape URL` — Pull company blog/news for personalization hooks
- `Search` — Find recent press mentions, funding announcements

## Email Template Framework

```
Subject: {personalization_hook} — {value_prop}

Hi {first_name},

{opening_line_from_research}  ← AI-generated from company news/job postings

{1-2 sentences connecting their pain to your solution}

{social_proof: "We helped {similar_company} achieve {result}"}

{clear_CTA: question or calendar link}

{signature}
```

## Setup

```bash
composio add apollo
composio add gmail          # OAuth2 (use your outreach email)
composio add hubspot
composio add linkedin       # OAuth2
composio add slack
composio add firecrawl      # API key
composio add exa            # API key
```

## Example Usage

```
"Find 50 VP Engineering leads at Series B SaaS companies using Apollo.
 Research each company, generate personalized emails, and start a
 5-touch sequence. Log everything to HubSpot and alert me in
 #sales-alerts when someone replies."
```
