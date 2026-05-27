# School Calendar Generator

A single-file HTML school calendar with built-in vacation planning intelligence.

## Features

### Calendar Display
- Full school year view (Aug–Jun) with monthly grid layout
- Color-coded days:
  - **Red** — Holidays
  - **Blue** — Teacher Workdays
  - **Green** — Vacation Days
  - **Orange circle** — First/Last Day of School
  - **Green pulsing circle** — Today's date
- Thin grid lines for readability
- Month descriptions below each month showing grouped date ranges

### Vacation Planning Mode (V toggle)
- Click the **V** button next to the title to enable
- Auto-detects strategic "pull days" — school days worth skipping to create long weekends/breaks
- Logic:
  - **Friday** before a holiday cluster → pull (weekend bridges to off days)
  - **Thursday** → only if adjacent Friday is a scheduled off day (H/W/V)
  - **Monday** after a holiday cluster → pull (weekend bridges back)
  - **Tuesday** → only if adjacent Monday is a scheduled off day (H/W/V)
  - Only creates blocks of 4+ total days
  - Plain weekends alone don't trigger pull suggestions
- Pull days shown with dashed orange outline
- Full vacation blocks outlined with thick orange border (Excel-style grouped selection)

### Dark/Light Theme (☾ toggle)
- Click the **☾** button to toggle themes
- Auto-detects system/browser preference on load
- Light theme: white background, pastel day colors (printer-friendly)
- Dark theme: black background, vibrant day colors, high contrast

### Tooltips
- Hover any day to see details
- Shows description (Holiday name, Workday, Pull Day, etc.)
- Shows number of days from today (e.g. "Labor Day - 103d away" or "5d ago")

### Print Support
- Light theme optimized for printing
- 3-column layout in print mode
- Months avoid page breaks

## Configuration

Edit the `CONFIG` object at the top of the `<script>` section to use for any school year:

```javascript
const CONFIG = {
  title: '2027-2028 School Calendar',
  firstDay: '2027-08-23',    // YYYY-MM-DD
  lastDay: '2028-06-08',     // YYYY-MM-DD

  // Use MM/DD format — year is auto-resolved from session dates
  holidays: {
    '09/06': 'Labor Day',
    '11/25': 'Thanksgiving',
    // ...
  },
  workdays: {
    '09/20': 'Workday',
    // ...
  },
  vacations: {
    '12/23': 'Winter Break',
    // ...
  }
};
```

The calendar will:
1. Auto-resolve MM/DD dates to the correct year based on session start
2. Generate the correct month range
3. Auto-calculate all pull days and vacation blocks
4. Render everything — no manual pull day or combo range configuration needed

## Files

- `school-calendar.html` — Self-contained single HTML file (no dependencies)
