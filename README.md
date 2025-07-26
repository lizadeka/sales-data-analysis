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

This successfully converted all text-formatted dates into real dates

2. ❌ Extra Spaces in Cells

Problem:Some cells had leading or trailing spaces, making them act like text even if they looked like dates.

Fix:

Used =TRIM([Order Date]) to remove unnecessary spaces

Verified date recognition with =ISNUMBER(...)

3. ✅ Structured Reference Formula Saved the Day

Problem:Even after cleaning, traditional formulas in regular cells still returned #VALUE!.

Solution:Using a structured reference formula inside a table:

=TEXT(Table3[[#This Row],[Order Date]],"mmm")

This worked perfectly and extracted the month name reliably. Structured references inside Excel tables forced Excel to treat the column as proper date values.

✅ Final Checks

Used =ISNUMBER(...) to confirm all cells returned TRUE

Month names were extracted properly using TEXT(...)

Dataset was ready for pivot tables and further analysis

💡 Key Takeaway

In Excel 2007, even well-formatted-looking columns may store data as text. Using structured references in a table not only solved formula issues but also improved stability across calculations.

Feel free to reuse or adapt this cleaning guide in your own Excel workflows!


