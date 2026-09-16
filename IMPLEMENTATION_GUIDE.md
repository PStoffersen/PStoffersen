# IMPLEMENTATION GUIDE: New Program Aktiv Sheet

## What You're Getting

Three files have been created to make your season setup faster and easier:

1. **Program_Aktiv_Setup_Guide.md** - Comprehensive overview of the new structure
2. **Program_Aktiv_Template_Formulas.txt** - Copy-paste ready formulas and data
3. **QUICK_REFERENCE.txt** - Quick reminder card for future seasons

---

## How to Implement (Choose One Approach)

### APPROACH A: Build It Yourself in Google Sheets (5-10 minutes)

**What to do:**
1. Open your Google Sheet "Kopi af Program Aktiv"
2. Create a new sheet called "program_aktiv_v2" (backup the old one first)
3. Copy the structure from **Program_Aktiv_Setup_Guide.md**:
   - Set up INPUT SECTION (rows 1-8)
   - Add SCHEDULE HEADERS (row 8)
   - Enter 10 rounds + 3-4 FRI ODDS rounds
4. Copy formulas from **Program_Aktiv_Template_Formulas.txt** for each row
5. Test with start date: 2025-09-01
6. Verify week numbers and dates calculate correctly

**Pros:** Full control, learn how it works
**Cons:** Takes a bit longer (but still quick)

---

### APPROACH B: Copy the Template Data Directly

1. Open **Program_Aktiv_Template_Formulas.txt**
2. Copy each section (input section, headers, rows 9-31)
3. Paste directly into your Google Sheet
4. Adjust C3 and C4 with your season info
5. Done!

**Pros:** Fastest - copy and paste
**Cons:** Need to understand the formulas if something needs changing

---

## Step-by-Step for Approach A (Recommended)

### Step 1: Backup Your Current Sheet
- Go to "program_aktiv" sheet tab
- Right-click → Move to... → (create copy)
- Name it "program_aktiv_OLD_[current season]"

### Step 2: Create New Sheet
- Click "+" button to add new sheet
- Name it "program_aktiv_v2"
- Keep it blank for now

### Step 3: Set Up Input Section
In the new sheet, create rows 1-7:

```
Row 1: [empty]
Row 2: [A2:B2 merged] "SEASON CONFIGURATION"
Row 3: A3: "Season Name:"        C3: [input box - text]
Row 4: A4: "Season Start Date:"  C4: [input box - date]
Row 5-7: [empty]
```

Test: Put "2025-2026" in C3 and "2025-09-01" in C4

### Step 4: Create Schedule Headers
Row 8: Create columns:
```
A8: Runde      (Round)
B8: Uge        (Week)
C8: Dato Start (Date Start - Monday)
D8: Dato Slut  (Date End - Sunday)
E8: Hold 1     (Team 1)
F8: Hold 2     (Team 2)
G8: Fri Odds   (Bye/Fri Odds Team)
H8: Noter      (Notes)
```

### Step 5: Enter Schedule Data

**For each round (row by row):**

Copy the structure from **Program_Aktiv_Template_Formulas.txt**, sections "Round 1" through "FRI ODDS Round C"

The key is:
- Column A: Round label
- Columns B, C, D: Formulas (auto-calculate dates)
- Columns E, F, G: Team names
- Column H: Leave empty for now (for future results)

Example for Round 1, Match 1 (Row 9):
```
A9: Round 1
B9: =ISOWEEKNUM($C$4+(ROW()-9)*7)
C9: =DATE(YEAR($C$4+(ROW()-9)*7),MONTH($C$4+(ROW()-9)*7),DAY($C$4+(ROW()-9)*7)-WEEKDAY($C$4+(ROW()-9)*7,2)+1)
D9: =C9+6
E9: Kardinalus
F9: Pingvinus
G9: Kaninus
H9: [empty]
```

### Step 6: Copy Formulas Down

Once you have the formulas in row 9:
1. Select cells B9:D9
2. Copy the formulas to all rows below (through row 31 for all rounds)
3. The formulas will auto-adjust because they use ROW()

### Step 7: Add Team Assignments

Enter teams for all 20 matchups (10 rounds × 2 matches) + 4 FRI ODDS rounds

Use this structure (from setup guide):
- **Rounds 1-5**: Regular rounds
- **FRI ODDS Round A**: All teams (money only)
- **Rounds 6-9**: Regular rounds
- **FRI ODDS Round B**: All teams (money only)
- **Round 10**: Regular rounds
- **FRI ODDS Round C**: All teams (money only)

### Step 8: Formatting

Make it look nice:
1. **Headers (Row 8)**: Bold, light background color
2. **Regular rounds**: Light green or white background
3. **FRI ODDS rounds**: Orange or yellow background
4. **Freeze top rows**: Freeze rows 1-8 for easy scrolling
5. **Set column widths**: Make dates readable

### Step 9: Test It

Enter test data:
- C3: "2025-2026"
- C4: "2025-09-01"

Check:
- [ ] Week numbers start at 36 (correct for early September)
- [ ] Dates are sequential
- [ ] All teams appear in schedule
- [ ] Each team plays others twice (count matchups)
- [ ] ~13-14 total rounds

### Step 10: Done!

Now for NEXT season, just:
1. Copy this sheet
2. Update C3 & C4
3. All formulas recalculate automatically!

---

## Troubleshooting

**Problem: Formulas show error or blank**
- Solution: Check C4 has a valid date in format YYYY-MM-DD
- Solution: Check you used = sign at start of formula
- Solution: Check $C$4 reference is correct (should be absolute, not C4)

**Problem: Week numbers are wrong**
- Solution: Verify C4 date is correct
- Solution: Try using WEEKNUM instead of ISOWEEKNUM (if different standard)
- Solution: Check ROW() adjustment matches where your data actually starts

**Problem: Dates are in wrong format**
- Solution: Format column C & D as Date (right-click → Format cells)
- Solution: Adjust date format to your locale (dd-mm-yyyy vs mm-dd-yyyy)

**Problem: Some teams appear more/less than twice**
- Solution: Double-check team assignments in columns E, F, G
- Solution: Count each matchup pairing to verify

---

## Next Steps

1. **For this season:**
   - Follow the implementation steps above
   - Get it working with today's season
   - Test that everything calculates correctly

2. **For next season:**
   - Copy the entire sheet
   - Update C3 (new season name) and C4 (new start date)
   - All formulas auto-recalculate!
   - Done in 2 minutes

3. **Optional: Randomize**
   - If you want different matchups: edit columns E, F, G
   - But only if you have fairness rules to ensure all teams play all others twice

---

## Questions or Issues?

Refer to:
- **Setup details:** Program_Aktiv_Setup_Guide.md
- **Formulas:** Program_Aktiv_Template_Formulas.txt
- **Quick reminder:** QUICK_REFERENCE.txt

Good luck! This should save you hours of manual work each season.
