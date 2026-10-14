# Find Leads: a lead-list Skill for AI agents

**Describe your customer in one sentence; get 25 decision-makers with verified
work emails and why each company fits.**

One real run on 14 October 2026, for *"UK accounting firms with 10 to 50
staff"*: 100 firms found, 32 that fit, and **25 of 25 contacts ready with
verified work emails, for $1.42 in 9 minutes.**

Your agent returns a table and a CRM-ready CSV: the right person at each
company, their title, a work email checked the same day, a one-line reason the
company fits and the page where the person was found, plus the bill for every
call. There's no seat, subscription or provider API key: your agent pays per
call from one prepaid [Scrollport](https://scrollport.com) wallet.

## The run, line by line

| Step | Tool | Calls | Result | Cost |
| --- | --- | ---: | --- | ---: |
| Find companies | Hunter Discover | 1 | 100 firms for the description | $0.0025 |
| Check fit | Hunter Company Enrichment | 39 | 32 fit; 7 left out, each with a reason | $0.2613 |
| List the staff | LeadMagic Employee Finder | 30 | 16 decision-makers picked from the lists | $0.5250 |
| Search by title, only where the list had no match | Hunter Domain Search | 13 | 9 more, each with a work email | $0.4355 |
| Work email for the staff-list picks | QuickEnrich Email Finder | 19 | an email for each of the 16 | $0.1292 |
| Check every email | MillionVerifier | 26 | all 25 contacts `ok` | $0.0650 |
| **Total** | | **128** | **25 of 25 ready** | **$1.4185** |

The maximum quoted before the run was $1.76, and the agent's summary line was
`25 of 25 ready · 25 verified · 0 catch-all · $1.42 · 9 min`. Firm names,
people and email addresses are withheld here; the full receipt with every run
ID is in the
[verification record](https://github.com/Scrollport/sales-prospecting-skills/blob/v6.1.0/skills/lead-list/evidence/2026-10-14-verification.md).

## Install

```bash
npx skills add Scrollport/lead-list-skill
```

Or in Claude Code:

```text
/plugin marketplace add Scrollport/lead-list-skill
/plugin install lead-list@scrollport-lead-list
```

Then connect your agent to Scrollport once:

```bash
npx scrollport setup
```

Or give your agent this prompt: `Read https://scrollport.com/start and then help me set up Scrollport.`
Your first connected agent gets $1 of trial credit: enough for a 10-contact
run, which costs at most $0.71.

It works in any agent that supports Agent Skills and can connect to
Scrollport, such as Claude Code, Codex, Cursor, OpenClaw and Hermes.

## Use it

```text
Find leads: UK accounting firms with 10 to 50 staff. 25 contacts.
```

Your agent asks who you sell to, which job titles and how many contacts, with
a default for each. It shows the titles it will use, quotes the maximum cost
before it spends anything and asks you to approve it once, then works through
the list. You get:

- **a one-line summary**: contacts ready, verified, catch-all, amount spent and
  minutes taken;
- **a table and a CRM-ready CSV**: name, title, company, website, why it
  matched, industry, size, city, country, work email, email status, the date
  it was checked and the page where the person was found;
- **what couldn't be done**, with a priced retry;
- **a short note on email rules** in the US, UK, EU and Germany;
- **an offer to research the best 10** with Research My Accounts;
- **the bill**: every paid call with its tool, run ID and cost.

Run it again later with the same CSV and it skips everyone you already have,
so nobody is paid for twice.

## How it works

1. **One search** finds up to 100 companies that match your sentence.
2. **Fit from company data, never the name alone.** The agent opens each
   website for free and leaves out firms that now redirect to another company,
   then checks industry, size and location, and writes a one-line reason for
   every company it keeps.
3. **Titles that fit the company.** Managing Partner, Partner, Director or
   Owner at accountants, law firms, agencies and consultancies; Owner, Founder
   or Director up to 10 staff; Founder, CEO or Managing Director up to 50;
   above that, the Head or VP of the team that would use what you sell. You
   can change them before the run.
4. **Staff list first.** One low-cost call lists people at the company with
   their titles, and the agent picks the best match. A title search runs only
   when the list has no match.
5. **One email, checked the same day.** It looks up the work email for the
   chosen person only and checks it: verified, or catch-all marked "test
   first". It never guesses an address or uses a personal one.
6. **A stop-loss.** If fewer than 3 of the first 10 companies give a ready
   contact, the run pauses, shows what has been spent and the titles it is
   seeing, and offers other titles or a smaller batch.

## Limits

- **Fit comes from company data and websites, not buying intent.** To see
  which companies to contact now and why, with dated sources, hand the list to
  [Research My Accounts](https://github.com/Scrollport/sales-prospecting-skills/tree/main/skills/sales-qualified-accounts).
- **Yield varies.** This is one measured run, in one industry and one country.
  Where no one has the wanted titles, the Skill moves to the next company and
  returns fewer rows rather than weaker ones.
- **A verified address accepts mail today.** That doesn't prove consent,
  current role or that anyone will reply.
- **It never sends anything.** No outreach and no CRM writes. If you're
  contacting people in the UK or EU, you need a lawful basis and must tell
  them where you got their details, and suppression lists come first.

## Pricing

You approve one maximum before the first paid call and pay only for calls that
complete. Refused calls are not charged. At prices checked on 14 October 2026,
for companies of up to 50 staff:

| Contacts | Maximum |
| ---: | ---: |
| 10 | $0.71 |
| 25 | $1.76 |
| 50 | $3.51 |
| 100 | $7.01 |

Above 50 staff the maximums are $0.89, $2.20, $4.39 and $8.76. Most runs cost
less: a contact found on the first try costs about $0.03, and the run above
spent $1.42 of its $1.76. Your agent checks prices again before every quote.
There's no subscription and no ongoing minimum spend.

---

⭐ **Star this repo for updates.** More one-outcome Skills are coming.

[Set up Scrollport](https://scrollport.com/start) ·
[Scrollport Skills](https://scrollport.com/skills) ·
[@scrollport_com](https://x.com/scrollport_com)

This Skill is maintained in
[Scrollport/sales-prospecting-skills](https://github.com/Scrollport/sales-prospecting-skills/tree/main/skills/lead-list)
and published here as a standalone copy of release v6.1.0. MIT licence.
