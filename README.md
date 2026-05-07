# Founder Outreach Tracker

Lightweight founder outreach CRM and follow-up tracker for relationships, message angles, stages, and next actions.

<!-- FOUNDER_OS_STANDARD_README -->

## The founder problem

Founder-led outreach breaks down when contacts, message angles, follow-up dates, and next actions live across LinkedIn, Gmail, notes, and spreadsheets. The failure mode is usually weak follow-up discipline, not lack of outreach ideas.

## What this repo does

- provides a sheet-based outreach tracker
- documents Make.com and Gmail follow-up automation
- tracks contacts, stage, angle, status, and follow-up date
- pairs with GTM research outputs

## What a founder gets in 10 minutes

- copyable outreach CSV template
- Make scenario setup guide
- founder follow-up cadence
- tracker fields for relationship workflow

## Before and after

Before:

- contacts scattered across tabs and notes
- no follow-up owner
- unclear status
- manual reminders

After:

- single relationship tracker
- clear next action
- follow-up dates
- automation-ready reminders

## Who this is for

- early-stage founders
- Founder's Office candidates
- GTM operators
- startup generalists
- BizOps operators

## Quick start

- Fork the repo.
- Open `sheet-template.csv` first.
- Copy the columns into Google Sheets or Airtable.
- Open `docs/make-scenario-setup.md` if you want reminders.

## How to fork and use this for your company

1. Click Fork.
2. Rename the repo if needed.
3. Replace sample rows in `sheet-template.csv` with your own public-safe contacts or private local copy.
4. Customize stages, message angles, and follow-up intervals.
5. Connect to Gmail, Make.com, Airtable, HubSpot, Pipedrive, Attio, or your internal tracker only in a private workspace.
6. Keep private contact details out of public forks.

### Non-technical path

- Replace one file: `sheet-template.csv`.
- Edit one workflow guide: `docs/make-scenario-setup.md`.
- Run no code.
- Read one artifact first: your copied sheet.

## Input format

- contact name or company
- relationship context
- message angle
- status
- last touch date
- next follow-up date
- owner

The default sample data and examples are synthetic, anonymized, or template-only unless the repo explicitly documents a public source. Keep private customer, prospect, employee, investor, borrower, merchant, payment, or company data out of public forks.

## Output files

- `sheet-template.csv`: outreach tracker starter
- `docs/make-scenario-setup.md`: reminder automation setup
- `docs/scenario-1.png` and `docs/scenario-2.png`: automation screenshots

## Example founder workflow

- Monday: add new targets.
- Tuesday: send or draft outreach.
- Wednesday: update stage and notes.
- Thursday: review follow-up dates.
- Friday: move active opportunities into the GTM or sales-call workflow.

## Customization guide

Customize these before using the repo for a real company:

- relationship stages
- message angle taxonomy
- follow-up timing
- CRM columns
- automation rules

## Where this fits in the Founder OS

Use this after `ai-gtm-command-center` creates target accounts and before `founder-led-sales-call-os` turns conversations into learning. It is the relationship tracking layer.

## Why this matters

This is not a contact spreadsheet. It is a lightweight relationship operating system for founder-led follow-up.

## Roadmap

- Google Sheets template link
- Airtable base template
- HubSpot/Pipedrive/Attio import mapping
- Make.com scenario export
- weekly follow-up report

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) if present. Practical improvements are welcome when they make the workflow easier to fork, run, or adapt.

## License

MIT License. See [LICENSE](LICENSE).

## Built by

Built by Shubham Singh, a founder-facing operator focused on RevOps, GTM systems, startup metrics, AI workflows, and operating systems for early-stage teams.

## Use this in your company

Fork it, replace the sample inputs with your company context, and run the workflow. Start with the main output listed in the Quick Start section. Keep private data out of public forks.

## If you are a Founder's Office candidate

Use this repo to understand how a founder-facing operator turns messy inputs into decisions, cadence, and execution artifacts. Fork it, adapt it to a real company example, and write a short case note explaining what changed.

---

## Detailed implementation notes

The founder-facing guide above is the fastest path. The original repo-specific notes are preserved below for deeper implementation context.

A lightweight founder outreach CRM and follow-up operating system for tracking founder/operator contacts, repo angles, statuses, and follow-up dates using Google Sheets, Make.com, and Gmail.

## Problem

Founder-led outreach breaks down when contacts, message angles, next actions, and follow-up dates live across LinkedIn tabs, notes, and ad hoc spreadsheets. The failure mode is usually not lack of outreach volume. It is weak follow-up discipline and unclear ownership of the next action.

This tracker creates a small operating cadence: identify the right contact, log the angle, set the stage, trigger a follow-up date, and surface a daily reminder before the conversation goes cold.

## What This Repo Includes

- A Google Sheets-compatible outreach tracker template in [`sheet-template.csv`](sheet-template.csv).
- A Make.com setup guide for row handling and daily Gmail reminders in [`docs/make-scenario-setup.md`](docs/make-scenario-setup.md).
- Scenario screenshots for the new-row handler and daily follow-up reminder.
- A reusable schema for contact status, fit score, source, notes, next action, and follow-up due date.
- A simple workflow that can support founder outreach, investor follow-up, partnership development, hiring outreach, or targeted job-search relationship tracking.

## How The Tracker Works

The Google Sheet is the source of truth. Each row represents one contact or relationship target.

Core fields include:

| Field | Purpose |
|---|---|
| Contact Name | Person being contacted |
| Company | Company or organization |
| Role / Title | Current role |
| LinkedIn URL | Research and follow-up reference |
| Message Type | Connection request, direct DM, InMail, referral, or other channel |
| Stage | Current outreach status |
| Fit Score | Simple 1-5 prioritization field |
| Message Sent Date | First outreach date |
| Follow-up Due | Date generated by the automation |
| Source | Where the contact came from |
| Notes | Context for personalization |
| Next Action | The next specific operator action |

Suggested stages:

`Identified` -> `Connection Request Sent` -> `Message Sent` -> `Replied` -> `Meeting Booked` -> `Followed Up` -> `Closed - No Response` / `Closed - Converted`

## Make.com / Gmail Follow-Up Automation

The workflow uses two Make.com scenarios:

1. **New row handler**: watches for new sheet rows, calculates the follow-up date from the message sent date, and writes it back to the tracker.
2. **Daily follow-up reminder**: runs on a schedule, filters rows due for follow-up, and sends a Gmail reminder with the contact, company, stage, LinkedIn URL, and next action.

![Scenario 1 - new row handler](docs/scenario-1.png)

![Scenario 2 - daily reminder](docs/scenario-2.png)

The automation does not send LinkedIn messages or automate outreach on behalf of the user. It only keeps the manual follow-up queue visible and timely.

## Use This In Your Own Outreach Workflow

Use this when a full CRM is too heavy, but a plain spreadsheet is not enough.

1. Import [`sheet-template.csv`](sheet-template.csv) into Google Sheets.
2. Add your target contacts, message channel, source, fit score, notes, and next action.
3. Build the two Make.com scenarios from [`docs/make-scenario-setup.md`](docs/make-scenario-setup.md).
4. Review the Gmail follow-up queue daily.
5. Keep the tracker as the operating source of truth for outreach status.

This can support founder-led GTM, investor follow-up, hiring pipelines, partnership motions, or curated relationship tracking.

## Minimum Edits Before First Use

| Edit | Where | Why |
|---|---|---|
| Replace sample contacts and notes | `sheet-template.csv` | Makes the tracker specific to your outreach motion |
| Confirm your stages | `sheet-template.csv` | Keeps status reporting clear and consistent |
| Adjust fit-score meaning | `sheet-template.csv` | Helps prioritize high-value contacts first |
| Set the follow-up delay | `docs/make-scenario-setup.md` | Aligns reminders with your outreach cadence |
| Rewrite Gmail reminder copy | Make.com Gmail module | Makes the reminder actionable for your team |
| Confirm time zone and schedule | Make.com scenario settings | Prevents reminders from arriving at the wrong time |

## Pair This With AI GTM Command Center

For account research and manual LinkedIn DM drafting, pair this tracker with [`ai-gtm-command-center`](https://github.com/shubham1502-hue/ai-gtm-command-center).

Recommended workflow:

1. Use the GTM command center to structure target accounts and message angles.
2. Manually review each founder or operator before sending.
3. Add approved contacts to this tracker.
4. Move the row to `Message Sent` after outreach.
5. Let the Make.com/Gmail reminder flow manage follow-up discipline.

This keeps the system useful without scraping LinkedIn, automating DMs, or risking account reputation.

## Folder Structure

```text
.
├── README.md
├── LICENSE
├── sheet-template.csv
└── docs/
  ├── make-scenario-setup.md
  ├── scenario-1.png
  └── scenario-2.png
```

## Portfolio Note

This repo shows a practical founder/operator workflow: take a repeated GTM execution problem, reduce it to a simple operating cadence, and connect lightweight tools so the next action is always visible. It is intentionally small because the value is in adoption, not software complexity.
