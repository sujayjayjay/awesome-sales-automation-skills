# Revenue Operations Dashboard Builder

> **Search Volume Signal:** "revenue operations" (2,400/mo), "revops" (1,900/mo), "sales dashboard" (1,600/mo), "sales reporting" (1,300/mo)
> **Composio Toolkits:** HubSpot, Salesforce, Google Sheets, Google Docs, Slack, Airtable

## What This Does

Builds and maintains a live RevOps dashboard by:
1. Pulling data from your CRM (pipeline, bookings, activity metrics)
2. Calculating key RevOps metrics (win rate, cycle length, pipeline coverage, ACV)
3. Building a formatted Google Sheets dashboard with charts
4. Generating weekly/monthly narrative reports
5. Posting metric alerts when KPIs deviate from targets

## Composio Actions Used

### HubSpot (Data Source — primary)
- `List deals` — All deals by stage, owner, close date
- `Batch read deals` — Efficient bulk pull
- `Search contacts` — Activity metrics per rep
- `Audit pipeline changes` — Stage-to-stage velocity
- `List activities` — Call/email/meeting counts per rep

### Salesforce (Data Source — alternative)
- `List opportunities` — Pipeline by stage and owner
- `List reports` — Pull native SF reports
- `Get report instance results` — Extract report data programmatically
- `List dashboards` — Link to existing dashboards

### Google Sheets (Dashboard)
- `Create spreadsheet` — Initialize dashboard
- `Update spreadsheet` — Write metrics data
- `Read spreadsheet` — Pull historical baselines for trend comparison

### Airtable (Alternative Dashboard)
- `Create record` — Log weekly metrics snapshot
- `List records` — Pull historical data for trends
- `Update record` — Refresh current period metrics

### Google Docs (Narrative Reports)
- `Create document` — Weekly RevOps report
- `Update document` — Monthly board-ready summary

### Slack (Distribution)
- `Send message` — Weekly metrics to #revenue-ops
- `Send message` — Alert when KPIs breach thresholds

## Metrics Calculated

```
📊 PIPELINE METRICS
- Total pipeline value (by stage)
- Pipeline coverage ratio (pipeline ÷ quota)
- New pipeline created this week/month
- Pipeline velocity (deals × win rate × ACV ÷ cycle length)

💰 BOOKINGS METRICS
- Closed-won this period
- Average Contract Value (ACV)
- Win rate (closed-won ÷ total closed)
- Quota attainment (% of target)

⏱️ EFFICIENCY METRICS
- Average sales cycle length (by segment)
- Stage-to-stage conversion rates
- Time in stage (median and P90)
- Activities per deal (calls, emails, meetings)

👥 REP PERFORMANCE
- Pipeline per rep
- Bookings per rep
- Activity metrics per rep
- Win rate per rep

🚨 ALERT THRESHOLDS
- Pipeline coverage < 3x → "Low pipeline coverage"
- Win rate drops > 10% MoM → "Win rate declining"
- Avg cycle length +20% → "Deals slowing down"
- Rep has <$X pipeline → "Rep needs pipeline help"
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
"Build me a RevOps dashboard in Google Sheets. Pull all HubSpot
 deals from Q1, calculate win rate, ACV, pipeline velocity, and
 stage conversion rates. Break down by rep. Post the top-line
 numbers to #revenue-ops in Slack every Monday at 9am."
```
