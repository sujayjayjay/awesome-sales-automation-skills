# Pre-Meeting Prospect Dossier Generator

> **Search Volume Signal:** "sales meeting preparation" (170/mo), "prospect research" (260/mo), "seamless ai" (14,800/mo), "apollo io" (12,100/mo)
> **Composio Toolkits:** Google Calendar, Apollo, LinkedIn, Firecrawl, Exa, HubSpot, Google Docs, Slack

## What This Does

30 minutes before every sales meeting, automatically generates a 1-page dossier:
1. Scans your calendar for upcoming meetings with external participants
2. Enriches every attendee via Apollo (title, LinkedIn, company data)
3. Pulls recent company news, job postings, and funding
4. Summarizes past interactions from your CRM
5. Delivers the dossier to Slack + Google Doc before the meeting

## Composio Actions Used

### Google Calendar
- `List events` — Find meetings in next 2 hours with external attendees
- `Get event` — Pull attendee emails, agenda, meeting notes

### Apollo (Prospect Intelligence)
- `Enrich person with Apollo` — Title, LinkedIn, phone, seniority
- `Enrich organization data` — Company size, revenue, funding, tech stack
- `Get Organization Job Postings` — What they're hiring for (budget signals)

### HubSpot (Relationship History)
- `Search contacts` — Find attendee in CRM
- `Get deal` — Pull active deals with this contact
- `List activities` — Last 10 interactions (emails, calls, meetings)
- `Get notes` — Previous meeting notes and deal context

### Firecrawl + Exa (Real-time Intel)
- `Scrape URL` — Pull company blog, press page, about page
- `Search` — Find recent press mentions, product launches, funding rounds

### LinkedIn
- `Get profile` — Recent posts, shared connections, endorsements

### Google Docs (Dossier Output)
- `Create document` — Generate formatted dossier
- `Update document` — Append to existing meeting prep folder

### Slack (Delivery)
- `Send direct message` — DM the dossier to the meeting owner 30min before

## Dossier Template

```markdown
# Meeting Prep: {Company Name}
**Meeting:** {event_title} | {date} {time}
**Attendees:** {names + titles}

## 🏢 Company Snapshot
- Industry: {industry} | Size: {employees} | Revenue: {revenue}
- Funding: {last_round} ({amount}, {date})
- Tech Stack: {technologies}
- Currently Hiring: {open_roles} ← buying signal

## 👤 Key People in This Meeting
### {Person 1 Name} — {Title}
- LinkedIn: {url}
- At company since: {tenure}
- Previously: {previous_role} at {previous_company}
- Recent LinkedIn activity: {summary}

## 📰 Recent News (Last 30 Days)
- {headline_1} ({source}, {date})
- {headline_2} ({source}, {date})

## 💼 Our Relationship History
- Deal: {deal_name} | Stage: {stage} | Amount: {amount}
- Last contact: {date} via {channel}
- Key notes: {summary_of_last_3_interactions}
- Open action items: {tasks}

## 🎯 Talking Points
1. {AI-generated based on news + deal context}
2. {AI-generated based on job postings}
3. {AI-generated based on past objections}
```

## Setup

```bash
composio add googlecalendar
composio add apollo
composio add hubspot
composio add firecrawl
composio add exa
composio add googledocs
composio add slack
```

## Example Usage

```
"Check my calendar for the next 2 hours. For any external meetings,
 build a prospect dossier with company intel, attendee profiles,
 our deal history, and recent news. DM me in Slack before each call."
```
