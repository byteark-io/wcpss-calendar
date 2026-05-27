# WCPSS School Calendar Generator

Single-file HTML school calendars for Wake County Public School System (Traditional) with built-in vacation planning intelligence.

## Features

### Calendar Display
- Full school year view (Aug–Jun) with monthly grid layout
- Color-coded days:
  - **Red** — Holidays
  - **Blue** — Teacher Workdays
  - **Green** — Vacation Days
  - **Orange circle** — First/Last Day of School
  - **Green pulsing circle** — Today's date
- Auto-scrolls to current month on load
- Month descriptions below each month (inline flex layout)

### Vacation Planning Mode (V toggle)
- Auto-detects strategic "pull days" — school days worth skipping to create long weekends/breaks
- Logic:
  - **Friday** before a holiday cluster → pull (weekend bridges to off days)
  - **Thursday** → only if adjacent Friday is a scheduled off day (H/W/V)
  - **Monday** after a holiday cluster → pull (weekend bridges back)
  - **Tuesday** → only if adjacent Monday is a scheduled off day (H/W/V)
  - Only creates blocks of 4+ total days
  - Plain weekends alone don't trigger pull suggestions
- Pull days shown with dashed orange outline
- Full vacation blocks outlined with thick orange border

### Font Size (+/− toggle)
- Stacked +/− button to increase/decrease day number font size
- 5 levels: 0.8rem → 1.0rem (default) → 1.3rem → 1.6rem → 2.0rem

### Dark/Light Theme (☾ toggle)
- Auto-detects system/browser preference on load
- Light theme: white background, pastel day colors
- Dark theme: black background, vibrant day colors, high contrast

### Print Support (⎙ button)
- A4 page size with 8mm margins
- 3-column layout, compact fonts
- Uniform 1px black grid lines on all cells
- Hides all toggle buttons in print

### Tooltips
- Hover any day to see details
- Shows description and days from today (e.g. "Labor Day - 103d away")

## Configuration

Edit the `CONFIG` object at the top of the `<script>` section:

```javascript
const CONFIG = {
  title: 'WCPSS Calendar (Traditional) 27-28',
  firstDay: '2027-08-23',    // YYYY-MM-DD
  lastDay: '2028-06-08',     // YYYY-MM-DD

  // Use MM/DD format — year is auto-resolved from session dates
  holidays: { '09/06': 'Labor Day', ... },
  workdays: { '09/20': 'Workday', ... },
  vacations: { '12/23': 'Winter Break', ... }
};
```

## Files

- `wcpss-trad-25-26.html` — 2025-2026 Traditional Calendar
- `wcpss-trad-26-27.html` — 2026-2027 Traditional Calendar
- `wcpss-trad-27-28.html` — 2027-2028 Traditional Calendar

Each file is self-contained (no dependencies).
