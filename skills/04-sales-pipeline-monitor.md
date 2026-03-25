# Sales Pipeline Health Monitor & Forecaster

> **Search Volume Signal:** "sales pipeline" (3,600/mo), "revenue operations" (2,400/mo), "sales pipeline management" (1,300/mo)
> **Composio Toolkits:** HubSpot, Salesforce, Google Sheets, Slack, Google Docs

## What This Does

Real-time pipeline health monitoring that:
1. Pulls all open deals from your CRM daily
2. Flags at-risk deals (stale, missing next steps, single-threaded)
3. Calculates weighted pipeline and forecasts revenue
4. Generates weekly pipeline review reports
5. Sends proactive alerts for deals needing attention

## Workflow

```
Daily Schedule (Cron)
    │
    ▼
┌─────────────────────────────┐
│ Step 1: Pull Pipeline       │
│ HubSpot: List all deals     │
│ HubSpot: Get deal properties│
│ HubSpot: List activities    │
│          per deal           │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│ Step 2: Health Analysis     │
│ For each deal, check:       │
│ ⚠️ Days in current stage    │
│ ⚠️ Days since last activity │
│ ⚠️ Missing close date       │
│ ⚠️ No next step scheduled   │
│ ⚠️ Single contact (no multi-│
│    thread)                  │
│ ⚠️ Amount = $0 (not sized)  │
│ ⚠️ Close date in past       │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│ Step 3: Forecast            │
│ Weighted pipeline:          │
│ Deal amount × stage prob    │
│ Commit vs Best Case vs Pipe │
│ Month/Quarter rollup        │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│ Step 4: Report & Alert      │
│ Google Sheets: Pipeline     │
│   dashboard spreadsheet     │
│ Google Docs: Weekly review  │
│   document                  │
│ Slack: At-risk deal alerts  │
│ Slack: Weekly forecast post │
└─────────────────────────────┘
```

## Composio Actions Used

### HubSpot (Pipeline Data)
- `List deals` — Pull all open deals with properties
- `Get deal` — Detailed deal data including custom properties
- `Batch read deals` — Efficient bulk retrieval
- `List activities` — Get last activity date per deal
- `Search contacts` — Check multi-threading (contacts per deal)
- `Audit pipeline changes` — Track stage movement velocity

### Salesforce (Alternative)
- `List opportunities` — SOQL query for open pipeline
- `Get opportunity` — Detailed opp data
- `List reports` — Pull existing forecast reports
- `Get report instance results` — Extract report data

### Google Sheets (Dashboard)
- `Update spreadsheet` — Write pipeline data for charts/pivots
- `Create spreadsheet` — Initialize dashboard if not exists
- `Read spreadsheet` — Pull historical data for trend analysis

### Google Docs (Reports)
- `Create document` — Weekly pipeline review doc
- `Update document` — Append new analysis

### Slack (Alerts)
- `Send message` — Daily at-risk alerts to #sales-ops
- `Send message` — Weekly forecast to #sales-leadership

## Risk Scoring

```
Each deal gets a Health Score (0-100):

-20 points: In same stage > 14 days (stale)
-15 points: No activity in > 7 days (going cold)
-15 points: Close date in the past (zombie deal)
-10 points: No next step/task scheduled
-10 points: Only 1 contact (single-threaded risk)
-10 points: Amount = $0 (unqualified)
-5 points:  No close date set

Score interpretation:
≥80 = Healthy (green)
50-79 = Needs attention (yellow)
<50 = At risk (red) → Slack alert
```

## Setup

```bash
composio add hubspot        # or: composio add salesforce
composio add googlesheets
composio add googledocs
composio add slack
```

## Example Usage

```
"Pull my entire HubSpot pipeline, score every deal for health risks,
 update the Pipeline Dashboard spreadsheet, and post a summary in
 #sales-ops with the top 5 at-risk deals and this week's forecast."
```
