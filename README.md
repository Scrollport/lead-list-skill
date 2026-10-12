# Lead List: a lead-list Skill for AI agents

**100 companies → 30 people → 3 decision-makers with verified work emails, for $0.0829.**
One real run on 12 October 2026: ten paid calls across four data providers.

Give your agent one sentence, such as *"UK fintech companies with 11 to 50
employees, CEO or managing director"*. It returns a CSV of companies, the
right person at each, their work email and its verification status, plus the
bill for every call. There's no seat, subscription or provider API key: your
agent pays per call from one prepaid [Scrollport](https://scrollport.com)
wallet.

## The run, line by line

| Step | Tool | Calls | Result | Cost |
| --- | --- | ---: | --- | ---: |
| Find companies | Hunter Discover | 1 | 100 UK companies for the profile | $0.0025 |
| People at each company | LeadMagic Employee Finder | 3 | 30 people with titles | $0.0525 |
| Work email | QuickEnrich Email Finder | 3 | 3 of 3 emails found | $0.0204 |
| Verify | MillionVerifier | 3 | 3 of 3 `ok` | $0.0075 |
| **Total** | | **10** | **3 verified decision-makers** | **$0.0829** |

The three companies were an insurance-placing platform, an online mortgage
broker and a specialist lender. Names and email addresses are withheld here;
the full receipt with run IDs is in the
[verification record](https://github.com/Scrollport/sales-prospecting-skills/blob/v5.1.0/skills/lead-list/evidence/2026-10-12-verification.md).

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
Your first connected agent gets $1 of trial credit, enough for roughly ten runs
like the one above.

It works in any agent that supports Agent Skills and can connect to
Scrollport, such as Claude Code, Codex, Cursor, OpenClaw and Hermes.

## Use it

```text
Build a lead list: UK fintech companies with 11 to 50 employees.
CEO, founder or managing director. 5 companies. Spend at most $0.25.
```

Your agent quotes the maximum cost before it spends anything, asks you to
approve it once, then works through the list. You get:

- **a CSV** of company, domain, decision-maker, title, profile URL, work email
  and verification status;
- **the funnel**: companies found, shortlisted, people found, decision-makers
  matched, emails found and verified;
- **the bill**: every paid call with its tool, provider, run ID and settled cost.

Run it again later with the same CSV and it skips everyone you already have,
so nobody is paid for twice.

## How it works

1. **One discovery call** returns up to 100 companies for the profile.
2. **A free shortlist.** Your agent drops excluded and off-profile companies
   before paying for anything else.
3. **People by domain.** One call per company lists people with their titles,
   and the agent picks the first match for your title order.
4. **Cheapest email first.** It tries a low-cost email finder, and falls back
   to a second finder only when the first finds nothing.
5. **Verify** every address and mark anything catch-all or unknown as not
   verified.

## Limits

- **Fit is judged from company names and discovery data, not researched.**
  For evidence of fit, timing or pain, use
  [Qualified Accounts to Contact](https://github.com/Scrollport/sales-prospecting-skills).
- **Yield varies.** This is one measured run. Small companies may have no
  matching decision-maker, and the Skill returns fewer rows rather than weaker
  ones.
- **A verified address is deliverable today.** That doesn't prove consent or
  current role.
- **It never sends anything.** No outreach and no CRM writes. If you're
  contacting people in the UK or EU, you need a lawful basis, and suppression
  lists come first.

## Pricing

Every call is priced per use from your prepaid wallet, and the price is shown
before each run. Failed calls are not charged. There's no subscription and no
ongoing minimum spend.

---

⭐ **Star this repo for updates.** More one-outcome Skills are coming.

[Set up Scrollport](https://scrollport.com/start) ·
[Scrollport Skills](https://scrollport.com/skills) ·
[@scrollport_com](https://x.com/scrollport_com)

This Skill is maintained in
[Scrollport/sales-prospecting-skills](https://github.com/Scrollport/sales-prospecting-skills/tree/main/skills/lead-list)
and published here as a standalone copy of release v5.1.0. MIT licence.
