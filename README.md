# sales-data-analysis
sales data analysis

🧹 Data Cleaning: Issues Faced & Fixes

While preparing the dataset in Excel 2007, I encountered a few tricky data formatting challenges — especially with the Order Date column. Here's how I tackled them:

1. ❌ Date Formatting Errors

Problem:The Order Date column looked fine visually, but formulas like =TEXT(..., "mmm") and =MONTH(...) returned #VALUE! errors.

Cause:Many of the dates were actually stored as text, not as real Excel date values.

Fix:

Used Excel's "Text to Columns" tool

Selected Delimited → Next → Next → Column Data Format: Date (DMY)

The moment I converted to DMY, the dates automatically adjusted to valid date format — no need for TRIM() or additional cleanup.

2. ✅ Structured Reference Formula Saved the Day

Problem:Even after converting the dates, regular formulas still behaved inconsistently.

Solution:Using a structured reference formula inside a table:

=TEXT(Table3[[#This Row],[Order Date]],"mmm")

This worked perfectly and extracted the month name reliably. Structured references inside Excel tables forced Excel to treat the column as proper date values.

✅ Final Checks

Used =ISNUMBER(...) to confirm all cells returned TRUE

Month names were extracted properly using TEXT(...)

Dataset was ready for pivot tables and further analysis

💡 Key Takeaway

In Excel 2007, even well-formatted-looking columns may store data as text. The "Text to Columns" tool with DMY conversion was the real game changer. Structured references further ensured stability across formulas.
