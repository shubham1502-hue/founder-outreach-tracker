# Make Scenario Setup Guide

## Prerequisites

- Free Make account (make.com)
- Google account connected to Make
- Gmail connected to Make
- Google Sheet created from `sheet-template.csv` (File → Import → Upload)

---

## Scenario 1: New Row Handler

**Purpose**: When you add a new contact to the sheet, automatically set the Follow-up Due date to 5 days from today.

### Modules in order

| # | App | Module | Key settings |
|---|-----|--------|--------------|
| 1 | Google Sheets | Watch Rows | Spreadsheet: your tracker sheet. Sheet: Sheet1. Trigger on: New rows only. Max rows: 1. |
| 2 | Tools | Set Variable | Variable name: `followUpDate`. Variable value: `{{formatDate(addDays(now; 5); "YYYY-MM-DD")}}` |
| 3 | Google Sheets | Update a Row | Spreadsheet: same sheet. Row number: `{{1.rowNumber}}`. Column L (Follow-up Due): `{{2.variable}}` |

### Schedule
Set to run every **15 minutes**.

---

## Scenario 2: Daily Follow-up Reminder

**Purpose**: Every morning at 9 AM IST, scan every row in the sheet and send yourself a Gmail for each contact whose follow-up is due today and whose stage is not Closed.

### Modules in order

| # | App | Module | Key settings |
|---|-----|--------|--------------|
| 1 | Make | Schedule | Run every day at 03:30 UTC (= 09:00 IST) |
| 2 | Google Sheets | Search Rows | Spreadsheet: your tracker sheet. Sheet: Sheet1. Filter: leave blank (get all rows). Limit: 500. |
| 3 | Make | Iterator | Array: `{{2.values}}` |
| 4 | Make | Filter | Label: "Due today and open". Condition: `{{formatDate(3.followUpDue; "YYYY-MM-DD")}}` equals `{{formatDate(now; "YYYY-MM-DD")}}` AND `{{3.stage}}` does not equal `Closed - No Response` AND `{{3.stage}}` does not equal `Closed - Converted` AND `{{3.stage}}` does not equal `Meeting Booked` |
| 5 | Gmail | Send an Email | To: your Gmail. Subject: `Follow up today: {{3.contactName}} at {{3.company}}`. Body: see template below. |

### Gmail body template

```
Hi Shubham,

Time to follow up with {{3.contactName}} ({{3.role}} at {{3.company}}).

LinkedIn: {{3.linkedInUrl}}
Stage: {{3.stage}}
Last activity: {{3.lastActivityDate}}
Notes: {{3.notes}}
Next action: {{3.nextAction}}

--
Founder Outreach Tracker (automated)
```

### Column mapping for Iterator (0-indexed from your sheet)
Make the Iterator output matches these field names by renaming in the Iterator module:

| Field name in Make | Sheet column |
|---|---|
| `contactName` | B |
| `company` | C |
| `role` | D |
| `linkedInUrl` | E |
| `messageType` | F |
| `stage` | G |
| `fitScore` | H |
| `dateAdded` | I |
| `messageSentDate` | J |
| `lastActivityDate` | K |
| `followUpDue` | L |
| `source` | M |
| `notes` | N |
| `nextAction` | O |

---

## Stage values (use exactly these for the filter to work)

- `Identified`
- `Connection Request Sent`
- `Message Sent`
- `Replied`
- `Meeting Booked`
- `Followed Up`
- `Closed - No Response`
- `Closed - Converted`

---

## Screenshot checklist (for the README)

After building both scenarios, take screenshots of:

1. Scenario 1 full canvas (all 3 modules visible, connections drawn)
2. Scenario 2 full canvas (all 5 modules visible)
3. The Google Sheet with 3-5 sample rows filled in

Save as `docs/scenario-1.png`, `docs/scenario-2.png`, `docs/sheet-preview.png`.
