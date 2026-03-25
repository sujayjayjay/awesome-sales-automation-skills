# LinkedIn Prospect Researcher & Signal Tracker

> **Search Volume Signal:** "linkedin scraping" (1,300/mo), "linkedin automation" (2,400/mo), "linkedin outreach" (880/mo), "linkedin sales navigator" (6,600/mo)
> **Composio Toolkits:** LinkedIn, Apollo, Google Sheets, HubSpot, Slack, Exa

## What This Does

Systematic LinkedIn intelligence gathering:
1. Monitors target accounts for buying signals (job changes, promotions, new hires, posts)
2. Identifies decision-makers at target companies
3. Maps org charts (who reports to whom)
4. Tracks engagement signals (who's liking competitor content, posting about pain points)
5. Feeds warm signals to your outreach sequencer

## Composio Actions Used

### LinkedIn (Profile & Activity Intelligence)
- `Get profile` — Full profile data for prospects
- `Search people` — Find decision-makers at target accounts
- `Get posts` — Recent activity and thought leadership
- `Get connections` — Mutual connections for warm intros

### Apollo (Enrichment & Search)
- `Apollo people search` — Search by title, company, location, seniority
- `Enrich person with Apollo` — Get verified email + phone from LinkedIn profiles
- `Search organizations in Apollo` — Find companies matching ICP filters
- `List Apollo contact stages` — Track where each prospect is in your pipeline

### Google Sheets (Tracking)
- `Read spreadsheet` — Pull target account list
- `Update spreadsheet` — Write prospect data + signal scores
- `Append row` — Add new prospects as discovered

### HubSpot (CRM Sync)
- `Create contact` — Push high-signal prospects to CRM
- `Update contact` — Add LinkedIn intel to existing records
- `Create deal` — Auto-create opportunity for hot signals

### Slack (Alerts)
- `Send message` — Alert on buying signals to #prospect-intel

### Exa (Research)
- `Search` — Find content prospects have published or been mentioned in

## Signal Detection

```
🔥 HOT SIGNALS (auto-alert + create deal):
- Job change to target title at target company
- Posted about pain point you solve
- Liked/commented on competitor's content
- Company posted VP/Director hiring in your category

🟡 WARM SIGNALS (add to outreach queue):
- Promoted to decision-maker title
- Company raised new funding round
- Engaged with your company's content
- Connected with your existing customers

❄️ TRACK SIGNALS (monitor, don't act):
- Active on LinkedIn but no buying intent
- At target company but wrong department
- Junior title, may become champion later
```

## Setup

```bash
composio add linkedin
composio add apollo
composio add googlesheets
composio add hubspot
composio add slack
composio add exa
```

## Example Usage

```
"Monitor my 50 target accounts on LinkedIn. Find all VP/Director/
 C-level contacts, enrich with Apollo, track their posting activity,
 and alert me in Slack whenever someone changes jobs, posts about
 our category, or engages with competitor content."
```
