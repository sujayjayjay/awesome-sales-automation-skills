# Lead Enrichment & Qualification Pipeline

> **Search Volume Signal:** "lead enrichment" (720/mo), "b2b lead generation" (8,100/mo), "lead gen" (8,100/mo)
> **Composio Toolkits:** Apollo, HubSpot, Clearout, FullEnrich, Dropcontact

## What This Does

Takes a raw list of leads (company name + person name/title) and automatically:
1. Enriches each lead with verified emails, phone numbers, company data, and LinkedIn profiles
2. Scores and qualifies leads using BANT criteria (Budget, Authority, Need, Timeline)
3. Pushes qualified leads into your CRM with full enrichment data
4. Flags unqualified leads with reasons for disqualification

## Workflow

```
Raw Lead List (CSV/Google Sheet)
    │
    ▼
┌─────────────────────────────┐
│ Step 1: Bulk Enrichment     │
│ Apollo: Bulk people enrichment│
│ Apollo: Bulk organization    │
│         enrichment           │
│ Clearout: Verify emails      │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│ Step 2: AI Qualification    │
│ Score using:                │
│ - Company size (from Apollo)│
│ - Funding stage             │
│ - Job title (decision maker?)│
│ - Industry fit              │
│ - Tech stack match          │
└─────────────┬───────────────┘
              │
              ▼
┌─────────────────────────────┐
│ Step 3: CRM Push            │
│ HubSpot: Create contact     │
│ HubSpot: Create company     │
│ HubSpot: Associate contact  │
│          with company       │
│ HubSpot: Update deal stage  │
└─────────────────────────────┘
```

## Composio Actions Used

### Apollo (Lead Data)
- `Enrich person with Apollo` — Get email, phone, LinkedIn, title, company for each person
- `Bulk people enrichment` — Enrich up to 10 people at once (batch processing)
- `Bulk organization enrichment` — Get company size, funding, revenue, tech stack for up to 10 orgs
- `Apollo people search` — Find new leads matching your ICP criteria

### Clearout (Email Verification)
- `Verify email` — Confirm deliverability before outreach (prevents bounces, protects sender reputation)

### HubSpot (CRM)
- `Create contact` — Push enriched lead into CRM
- `Create company` — Create company record with enrichment data
- `Associate contact with company` — Link contact to their org
- `Create deal` — Create opportunity for qualified leads
- `Update deal stage` — Set initial pipeline stage based on qualification score

### Google Sheets (Data)
- `Read spreadsheet` — Pull raw lead list
- `Update spreadsheet` — Write back enrichment results + qualification scores

## Qualification Scoring Logic

```
Score 0-100:

+25 points: Title contains VP, Director, Head, C-level (Authority)
+20 points: Company size 50-500 employees (sweet spot for most B2B)
+15 points: Raised Series A-C in last 18 months (Budget signal)
+15 points: Industry matches your ICP
+10 points: Uses complementary tech stack (from Apollo technographics)
+10 points: Email verified (deliverability)
+5 points:  LinkedIn profile active (posted in last 30 days)

≥70 = Hot Lead → Create deal, assign to AE
50-69 = Warm Lead → Add to nurture sequence
<50 = Cold → Park in marketing list
```

## Setup

```bash
# Connect your tools via Composio
composio add apollo        # API key from apollo.io
composio add hubspot       # OAuth2
composio add clearout      # API key
composio add googlesheets  # OAuth2
```

## Example Usage

```
"Enrich all leads in my Google Sheet 'Q2 Prospects', verify emails,
 qualify using BANT scoring, and push hot leads (score ≥70) into
 HubSpot with deal stage 'Qualified Lead'."
```
