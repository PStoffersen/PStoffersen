# Program Aktiv - New Season Setup Guide

## Overview
This is a **semi-automated template** for managing seasons in the Program Aktiv sheet. You only need to:
1. Enter the season name and start date
2. The rest calculates automatically (week numbers, dates)
3. Randomize team matchups as desired

---

## Sheet Structure

### Part 1: INPUT SECTION (Rows 1-8)
Keep this section at the top for easy season setup.

```
Row 1: [BLANK]
Row 2: SEASON CONFIGURATION
Row 3: Season Name:          [2025-2026]
Row 4: Season Start Date:    [2025-09-01]
Row 5: (Autocalculates from here)
Row 6: [BLANK]
Row 7: [BLANK]
Row 8: [HEADERS START]
```

**Formulas in Input Section:**
- **C3**: Season name (text input) - e.g., "2025-2026"
- **C4**: Season start date (date input) - e.g., "2025-09-01"

### Part 2: SCHEDULE SECTION (Starting Row 8)

**Headers (Row 8):**
```
A: Runde        (Round number/label)
B: Uge          (Week number)
C: Dato Start   (Week start date - Monday)
D: Dato Slut    (Week end date - Sunday)
E: Hold 1       (Team 1)
F: Hold 2       (Team 2)
G: Fri Odds     (Team with bye/fri odds)
H: Noter        (Notes/scores - optional)
```

**Data Rows (Starting Row 9):**
- 10 regular rounds (each with 2 matches)
- 3-4 FRI ODDS only rounds
- Each round = 1 week

---

## How It Works

### Step 1: Set Season Parameters
1. Go to the INPUT SECTION
2. In C3: Enter season name (e.g., "2025-2026")
3. In C4: Enter season start date (e.g., "2025-09-01")
   - Use format: YYYY-MM-DD or your local date format

**The formulas will automatically calculate:**
- Week numbers for each round
- Date ranges (Monday-Sunday for each week)

### Step 2: Randomize Team Assignments (Manual Step)
Since we're using a semi-automated template:

1. **The schedule template has:**
   - All 10 regular rounds already set up
   - 3-4 FRI ODDS rounds mixed in
   - Team assignments that you can modify

2. **To randomize:**
   - Option A: Manually edit the Team 1, Team 2, and Fri Odds columns
   - Option B: Copy the team list to a separate area and use a randomizer

3. **Important:** Ensure each team plays each other exactly twice
   - Kardinalus ↔ Pingvinus (twice)
   - Kardinalus ↔ Gorilla (twice)
   - Kardinalus ↔ King (twice)
   - Kardinalus ↔ Kaninus (twice)
   - Pingvinus ↔ Gorilla (twice)
   - ... (and so on for all pairs)

### Step 3: Verify the Schedule
Check that:
- [ ] All 5 teams appear in the schedule
- [ ] Each team plays every other team exactly 2 times
- [ ] ~3-4 FRI ODDS rounds are present (no matches)
- [ ] Week numbers are sequential and correct
- [ ] Dates span ~15 weeks

---

## Formula Reference

### Week Number Calculation
For each round, calculate the ISO week number:
```
= ISOWEEKNUM(C4 + (ROW() - 9) * 7)
```
- C4 = Season start date
- ROW() - 9 = which round this is (0 for first, 1 for second, etc.)
- * 7 = number of days

Or simpler (if you prefer calendar weeks):
```
= WEEKNUM(C4 + (ROW() - 9) * 7, 21)
```

### Week Start Date (Monday)
```
= DATE(YEAR(C4 + (ROW() - 9) * 7), MONTH(C4 + (ROW() - 9) * 7), DAY(C4 + (ROW() - 9) * 7) - WEEKDAY(C4 + (ROW() - 9) * 7, 2) + 1)
```

### Week End Date (Sunday)
```
= [Week Start Date] + 6
```

---

## Pre-Made Team Matchups (Fair & Balanced)

### All Possible Matchups (Each Team vs Every Other)
**Matchup Table** (Total: 20 matches = 10 rounds × 2 matches/round)

| Cycle | Round | Match 1 | Match 2 | Fri Odds |
|-------|-------|---------|---------|----------|
| 1 | 1 | Kardinalus vs Pingvinus | Gorilla vs King | Kaninus |
| 1 | 2 | Kardinalus vs Gorilla | Pingvinus vs King | Kaninus |
| 1 | 3 | Kardinalus vs King | Pingvinus vs Gorilla | Kaninus |
| 1 | 4 | Kardinalus vs Kaninus | Pingvinus vs Gorilla | King |
| 1 | 5 | Pingvinus vs Kaninus | Gorilla vs King | Kardinalus |
| 2 | 6 | Kardinalus vs Pingvinus | Gorilla vs King | Kaninus |
| 2 | 7 | Kardinalus vs Gorilla | Pingvinus vs King | Kaninus |
| 2 | 8 | Kardinalus vs King | Pingvinus vs Gorilla | Kaninus |
| 2 | 9 | Kardinalus vs Kaninus | Pingvinus vs Gorilla | King |
| 2 | 10 | Pingvinus vs Kaninus | Gorilla vs King | Kardinalus |

### FRI ODDS Only Rounds (Insert These Randomly)
- **FRI ODDS Round A**: All 5 teams get money only (no matches)
- **FRI ODDS Round B**: All 5 teams get money only (no matches)
- **FRI ODDS Round C**: All 5 teams get money only (no matches)
- (Optional) **FRI ODDS Round D**: All 5 teams get money only (no matches)

**Where to insert:** Scatter these among the 10 regular rounds. For example:
- After Round 3, insert FRI ODDS Round A
- After Round 6, insert FRI ODDS Round B
- After Round 9, insert FRI ODDS Round C

---

## Setup Checklist

- [ ] **Input Section Created**
  - [ ] Row 2: "SEASON CONFIGURATION" header
  - [ ] Row 3: "Season Name:" label + input cell (C3)
  - [ ] Row 4: "Season Start Date:" label + input cell (C4)

- [ ] **Schedule Headers Created** (Row 8)
  - [ ] A8: "Runde"
  - [ ] B8: "Uge"
  - [ ] C8: "Dato Start"
  - [ ] D8: "Dato Slut"
  - [ ] E8: "Hold 1"
  - [ ] F8: "Hold 2"
  - [ ] G8: "Fri Odds"
  - [ ] H8: "Noter"

- [ ] **Schedule Data Entered** (Rows 9+)
  - [ ] 10 regular rounds with team matchups
  - [ ] 3-4 FRI ODDS rounds
  - [ ] Formulas for week numbers and dates

- [ ] **Formatting**
  - [ ] Regular rounds: light background
  - [ ] FRI ODDS rounds: orange/yellow background
  - [ ] Headers: bold
  - [ ] Team matchups: verified for fairness

- [ ] **Testing**
  - [ ] Input test date: 2025-09-01
  - [ ] Verify week numbers (should start at week 36)
  - [ ] Verify each team plays all others twice
  - [ ] All dates calculate correctly

---

## For Next Season: Copy & Modify
1. Copy the entire schedule
2. Paste to a new sheet or keep in same sheet (add below current schedule)
3. Update C3 & C4 with new season name and start date
4. All formulas auto-recalculate!
5. Randomize team assignments if desired

---

## Tips
- **Keep formulas:** Don't convert to static values - this way dates auto-update if you change the start date
- **Color coding:** Use consistent colors to distinguish regular rounds from FRI ODDS rounds
- **Backup:** Keep previous season visible below (or in a separate sheet) for reference
- **Team list:** Always use: Kardinalus, Pingvinus, Gorilla, King, Kaninus (consistent spelling)
