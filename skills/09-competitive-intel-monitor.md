# Competitive Intelligence Monitor

> **Search Volume Signal:** "competitive intelligence" (2,900/mo), "competitor analysis" (6,600/mo), "competitive analysis tools" (1,600/mo)
> **Composio Toolkits:** Firecrawl, Exa, Ahrefs, Google Sheets, Slack, HubSpot, Reddit, Twitter

## What This Does

Continuous competitive monitoring that:
1. Tracks competitor websites for pricing changes, feature launches, new pages
2. Monitors mentions across Twitter, Reddit, HN, and press
3. Alerts sales team on competitive deals (competitor mentioned in CRM)
4. Builds and maintains competitive battle cards
5. Tracks competitor job postings (hiring = product investment signals)

## Composio Actions Used

### Firecrawl (Website Monitoring)
- `Scrape URL` — Pull competitor pricing pages, feature pages, changelog
- `Crawl site` — Deep crawl competitor docs/blog for new content

### Exa (Mention Tracking)
- `Search` — Find competitor mentions in articles, blogs, forums

### Ahrefs (SEO Intelligence)
- `Get keywords` — What competitors rank for (SEO gaps)
- `Get backlinks` — Who's linking to competitors (partnership signals)
- `Get domain overview` — Traffic trends

### Reddit (Community Sentiment)
- `Search posts` — Competitor mentions in relevant subreddits
- `Get comments` — User complaints and praise (positioning intel)

### Twitter (Social Monitoring)
- `Search tweets` — Real-time competitor mentions
- `Get user tweets` — Track competitor's official account

### Google Sheets (Battle Cards)
- `Update spreadsheet` — Maintain competitive comparison matrix
- `Append row` — Log new competitive intel chronologically

### HubSpot (Deal Intelligence)
- `Search deals` — Find deals where competitor is mentioned
- `Update deal` — Tag competitive deals
- `List activities` — Check call notes for competitor mentions

### Slack (Distribution)
- `Send message` — Daily competitive digest to #competitive-intel
- `Send message` — Real-time alerts for pricing changes or major launches

## Monitoring Schedule

```
DAILY:
├── Check competitor pricing pages (Firecrawl)
├── Search Twitter for competitor mentions
├── Search Reddit for competitor discussions
└── Post digest to Slack

WEEKLY:
├── Full competitor blog/changelog crawl (Firecrawl)
├── Ahrefs keyword + backlink analysis
├── Update battle cards in Google Sheets
├── Check competitor job postings (Apollo)
└── Post weekly intel report to Slack

MONTHLY:
├── Deep competitive analysis report (Google Docs)
├── Feature comparison matrix update
├── Win/loss analysis from CRM data
└── Strategy recommendations
```

## Battle Card Template

```markdown
# {Competitor Name} Battle Card
Updated: {date}

## Quick Stats
- Est. ARR: {range} | Employees: {count} | Funding: {total}
- Key customers: {logos}

## How We Win Against Them
1. {advantage_1} — proof: {customer_quote_or_data}
2. {advantage_2}
3. {advantage_3}

## Where They Beat Us (be honest)
1. {their_advantage_1} — our counter: {response}
2. {their_advantage_2}

## Recent Changes (auto-updated)
- {date}: {pricing_change / feature_launch / hire}

## Trap Questions (what prospects ask)
- "How is this different from {competitor}?"
  → Response: {scripted_answer}

## Competitive Deals in Pipeline
- {deal_1}: {stage}, {amount} — competitor: {status}
```

## Setup

```bash
composio add firecrawl
composio add exa
composio add ahrefs          # API key
composio add reddit           # OAuth2
composio add twitter          # OAuth2
composio add googlesheets
composio add hubspot
composio add slack
```

## Example Usage

```
"Monitor Competitor X's website daily for pricing and feature changes.
 Track mentions on Twitter and Reddit. Update the battle card in
 Google Sheets. Alert #competitive-intel for any pricing changes
 immediately. Weekly, generate a competitive digest with Ahrefs
 traffic and SEO data."
```
