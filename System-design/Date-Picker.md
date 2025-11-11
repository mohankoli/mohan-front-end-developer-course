# ✅ LLD: Date Picker with **Range Selection** & **Disabled Dates**

A clean, interview-ready Low-Level Design (LLD) written fully in **.md format** — **no code included**.

---

# 🕐 0–5 min — Requirements Gathering

### ✅ Clarifying Questions
- Should the Date Picker support both **single** and **range** mode?
- Should the component block users from selecting **disabled dates**?
- Should the picker support **min/max date boundaries**?
- Should the calendar show **one or multiple months** at a time?
- Should the UI include **hover preview** for range mode?
- Should disabled dates include:  
  - specific dates,  
  - ranges,  
  - weekends,  
  - custom rules?

### ✅ Finalized Functional Requirements
- Select **single date** or **date range**
- Ability to define **disabled dates**
- Ability to define **min/max dates**
- **Hover preview** between start → hovered date
- Month navigation (next/prev)
- Prevent range selection across disabled dates
- Keyboard navigation support (arrows, enter, escape)
- Localization (first day of week, locale)
- Accessible via ARIA roles

### ✅ Non-Functional Requirements
- High performance rendering
- Easy theming for design systems
- Reusable across applications
- Predictable selection behavior (auto-swap range)
- Mobile-responsive layout

---

# ⚙️ 5–10 min — Components Breakdown

### ✅ Main Components & Responsibilities

#### **1. DatePicker**
- Parent component controlling state and behavior
- Manages mode (single/range)
- Handles opening/closing of calendar popover

#### **2. Calendar Grid**
- Displays the days of the month in a 7×5/6 layout
- Applies disabled, selected, and hover states

#### **3. Day Cell**
- Represents a single date
- Handles hover, focus, and click interactions
- Applies visual states:  
  - disabled  
  - selected  
  - in range  
  - hovered range preview  

#### **4. Navigation Bar**
- Displays current month/year
- Supports switching months and years

#### **5. Range Preview Layer**
- Visual highlight between start date → hovered date

#### **6. Disabled Date Engine**
- Receives disabled rules
- Standardizes rules and evaluates them for each date

#### **7. Utils (Date Helpers)**
- All calculations:  
  - isBefore  
  - isAfter  
  - isBetween  
  - isSameDay  
  - daysInMonth  
  - getStartOfMonth

> **This modular breakdown ensures reusability and clear separation of responsibilities.**

---

# 🧠 10–15 min — State & Data Management

### ✅ Core State Variables
- **Selected Value**
  - Single mode → single date
  - Range mode → `{ start: date | null, end: date | null }`
- **Hovered Date** (for range preview)
- **Visible Month** (for the currently displayed calendar)
- **Focused Date** (for keyboard navigation)
- **Disabled Dates Config**

### ✅ Derived State
- **Days of Current Month**
- **Disabled Dates Matrix**
- **Range Preview**
- **Comparison Markers** (before start, after end, etc.)

### ✅ Rules & Constraints
- Cannot select disabled dates
- Cannot hover disabled dates for range preview
- Range cannot cross a disabled date
- If end < start and auto-swap is enabled → auto adjust

---

# 🧭 15–20 min — Interaction Flow

### ✅ **Single Selection Flow**
1. User clicks a date  
2. If date is valid → set selected date  
3. Close the popover (optional)  
4. Trigger `onChange`

---

### ✅ **Range Selection Flow**
1. User clicks a date to set **start**
2. User hovers → show **range preview**
3. User clicks again → set **end**
4. If `end < start` and auto-swap is true → swap values  
5. Validate that no disabled date exists inside the selected range  
6. Trigger `onChange({ start, end })`

---

### ✅ **Disabled Dates Behavior**
Disabled dates may include:
- Specific individual dates  
- Date ranges  
- Weekends  
- Custom rule functions  
- Min/Max boundaries  

Picker must:
- Render disabled dates differently  
- Block clicks  
- Block hover range  
- Prevent forming invalid ranges  

---

### ✅ **Navigation Flow**
- Next/Prev buttons → change month
- Keyboard:
  - Arrow keys → move focus by 1 day
  - PageUp/PageDown → change month
  - Enter → select date
  - Escape → close

---

# 🚀 20–25 min — Performance & Accessibility

### ✅ Performance Considerations
- Compute only visible months
- Cache disabled dates calculation
- Memoize month grids
- Avoid re-rendering all day cells on hover (batch updates)
- Efficient date comparison utilities

---

### ✅ Accessibility (WCAG)
- Calendar grid uses `role="grid"`
- Each day cell uses `role="gridcell"`
- `aria-selected` for selected dates
- `aria-disabled` for disabled dates
- Focusable date cells for keyboard users
- Range preview includes screen-reader-friendly hints
- Respect local calendar formats (locale, first day of week)

---

# ⚖️ 25–30 min — Trade-offs & Extensions

### ✅ Trade-offs

| Decision | Pros | Cons |
|----------|------|------|
| Auto-swap range | Cleaner UX | Might confuse new users |
| Allow function-based disabled rules | Very flexible | Hard to cache efficiently |
| Multi-month display | Better visibility | More DOM complexity |
| Heavy keyboard support | Accessibility | More code complexity |

---

# ✅ Possible Extensions (Future Enhancements)

- Multi-month view (2/3 months side by side)
- Time picker integration (Datetime range)
- Presets like “Last 7 days”, “Last Month”
- Support for fiscal year calendars
- Integration with booking systems (checking availability)
- Mobile-friendly month/year dropdowns
- Highlight holidays and special events

---

# ✅ Final Interview Summary

> “My Date Picker LLD focuses on modular components, clean state management, predictable range selection behavior, and efficient disabled-date handling.  
> It also fully supports accessibility, keyboard navigation, and theming for large-scale applications.”  

✅ **This .md file is structured exactly for interview presentation — no code included.**
