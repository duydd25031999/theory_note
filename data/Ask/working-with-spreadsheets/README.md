# Ways data analysts use spreadsheets

organize your data
- Pivot table
- sort and filter 

calculate your data
- Fomula
- Function

The first steps a data analyst takes when working with data in a spreadsheet are to sort and filter the data.

# the data life cycle

1. `Plan` for the users who will work within a spreadsheet by developing organizational standards. 
    - This can mean formatting your cells, the headings you choose to highlight, the color scheme, and the way you order your data points. W
    - hen you take the time to set these standards, you will improve communication, ensure consistency, and help people be more efficient with their time.
    - Tạo label, heading, standard cho spreadsheet

1. `Capture` data by the source by connecting spreadsheets to other data sources
    - such as an online survey application or a database. 
    - This data will automatically be updated in the spreadsheet. 
    - That way, the information is always as current and accurate as possible.

1. `Manage` different kinds of data with a spreadsheet. 
    - This can involve storing, organizing, filtering, and updating information. 
    - Spreadsheets also let you decide 
        - who can access the data, 
        - how the information is shared, 
        - how to keep your data safe and secure. 

1. `Analyze` data in a spreadsheet to help make better decisions. 
    - Some of the most common spreadsheet analysis tools
        - formulas to aggregate data or create reports
        - pivot tables for clear, easy-to-understand visuals. 

1. `Archive` any spreadsheet that you don’t use often, but might need to reference later with built-in tools. 
    - This is especially useful if you want to store historical data before it gets updated. 

1. `Destroy` your spreadsheet when you are certain that you will never need it again
    - if you have better backup copies, or for legal or security reasons. 
    - Keep in mind, lots of businesses are required to follow certain rules or have measures in place to make sure data is destroyed properly.

# Step-by-step in spreadsheets

Bôi đen toàn bộ column rồi kéo width của 1 column ➞ các columns khác cũng kéo theo

# Formula 
a set of instructions that perform a specific calculation.
- Formulas are built on operators
- Là phép tính default của spreadsheet

## Operator
Symbols that name that type of operation or calculation to be performed

Mathematical operators
- Subtraction – minus sign ( - )
- Addition – plus sign ( + )
- Division – forward-slash ( / )
- Multiplication – asterisk ( * )

## Cell reference
single cell or range of cells in a worksheet that can be used in a formula.

Range 
- include cells from the same row or column, or from different columns and rows collected together

Absolute referencing
- marked by a dollar sign ($): `=$A$10`
- `=$A10`: Absolute columnn ➞ copy thì vẫn là `$A`
- `=A$10`: Absolute row ➞ copy thì vẫn là `$10`

# Error

```ts
#DIV/0!
```
- A formula is trying to divide a value in a cell by 0 (or an empty cell with no value)
> =B2/B3, when the cell B3 contains the value 0 
- Chia cho 0

<hr />

```ts
function IFERROR(fomula: Fomula, if_value: any, else_value?: any): IFELSE`
```
- Try/catch trong spreadsheet

<hr />

```ts
#ERROR!
```
- (Google Sheets only)  Something can’t be interpreted as it has been input. 
- This is also known as a parsing error. 
> =COUNT(B1:D1 C1:C10) is invalid because the cell ranges aren't separated by a comma
- Error khi input sai syntax

<hr />

```ts
#N/A
```
- the data in your formula can't be found by the spreadsheet.
- A formula can't find the data.
> The cell being referenced can't be found
- không tìm thấy data = LOOKUP
    - nếu ô khác có fomula trỏ tới `#N/A` ➞ cũng `#N/A`

```ts
#NAME?
```
- error can happen when a formula's name isn't recognized or understood.
- The name of a formula or function used isn't recognized
> The name of a function is misspelled 
- Lỗi khi gõ sai tên formula

<hr />

```ts
#NUM!
```
- A formula's calculation can't be performed as specified by the data
- The spreadsheet can't perform a formula calculation because a cell has an invalid numeric value
> =DATEDIF(A4, B4, "M")  is unable to calculate the number of months between two dates because the date in cell A4 falls after the date in cell B4
- Lỗi input sai làm fomula không calculate được
- Input đúng type nhưng sao logic

<hr />

```ts
#REF!
```
- Lỗi do reference tới 1 ô đã bị xóa
- Ref tới 1 ô ➞ không lỗi
    - xóa ô đó đi ➞ ô ref bị lỗi sau khi xóa
- A formula is referencing a cell that isn't valid
> A cell used in a formula was in a column that was deleted

<hr />

```ts
#VALUE!
```
- A general error that could indicate a problem with a formula or reference cells
> There could be problems with spaces or text, or with referenced cells in a formula; you may have additional work to find the source of the problem.
- Lỗi chung cho fomula || reference cell

# Function
A preset command that automatically performs a specific process or task using the data

## Difference between formulas and functions
A formula is a set of instructions used to perform a calculation using the data in a spreadsheet.

A function is a preset command that automatically performs a specific process or task using the data in a spreadsheet.

## Popular functions
| Command | Chromebook | PC | Mac |
| -- | --| --| --| 
| Create new workbook | Control+N | Control+N | Command+N |
| Open workbook | Control+O | Control+O | Command+O |
| Save workbook | Control+S | Control+S | Command+S |
| Close workbook | Control+W | Control+W | Command+W |
| Undo | Control+Z | Control+Z | Command+Z |
| Redo | Control+Y | Control+Y | Command+Y |
| Copy | Control+C | Control+C | Command+C |
| Cut | Control+X | Control+X | Command+X |
| Paste | Control+V | Control+V | Command+V |
| Paste values only | Control+Shift+V | Control+Shift+V | Command+Shift+V |
| Find | Control+Shift+F | Control+F | Command+F |
| Find and replace | Control+H | Control+H | Command+Shift+F |
| Insert link | Control+K | Control+K | Command+K |
| Bold | Control+B | Control+B | Command+B |
| Italicize | Control+I | Control+I | Command+I |
| Underline | Control+U | Control+U | Command+U |
| Zoom in | Control+Plus (+) | Control+Plus (+) | Option+Command+Plus (+) |
| Zoom out | Control+Minus (-) | Control+Minus (-) | Option+Command+Minus (-) |
| Select column | Control+Spacebar | Control+Spacebar | Command+Spacebar |
| Select row | Shift+Spacebar | Shift+Spacebar | Up Arrow+Spacebar |
| Select all cells | Control+A | Control+A | Command+A |
| Edit the current cell | Enter | F2 | F2 |
| Comment on a cell | Ctrl + Alt + M | Alt+I+M | Option+Command+M |
| Insert column to the left | Ctrl + Alt + = (with existing column selected)  | Alt+Shift+I, then C | ⌘ + Option + = (with existing column selected)  |
| Insert column to the right | Alt + I, then O | Alt+Shift+I, then O | Ctrl + Option + I, then O |
| Insert row above | Ctrl + Alt + = (with existing row selected)  | Alt+Shift+I, then R  | ⌘ + Option + = (with existing row selected) |
| Insert row below | Alt + I, then R, then B | Alt+Shift+I, then B | Ctrl + Option + I, then B |

# Work with functions.

AVERAGE: trung bình cộng
- Statistical: number
- Returns the numerical average value in a dataset, ignoring text.

AVERAGEIFS: trung bình cộng với điều kiện
- Statistical: return number
- Returns the average of a range that depends upon multiple criteria.

CHOOSE: lấy giá trị = thứ tự trong range
- Lookup: any
- Returns an element from a list of choices based on index.

COUNT: đếm
- Statistical: number
- Returns the count of the number of numeric values in a dataset.

COUNTIF: đếm với điều kiện
- Statistical: number
- Returns a conditional count across a range.

DATE: parse Date
- Date: date
- Converts a provided year, month, and day into a date.

FIND: 
- Text
- Returns the position at which a string is first found within text.

GETPIVOTDATA
- Text
- Extracts an aggregated value from a pivot table that corresponds to the specified row and column headings.

IF
- Logical
- Returns one value if a logical expression is true and another if it is false.

INDEX
- Lookup
- Returns the content of a cell, specified by row and column offset.

INT
- Math
- Rounds a number down to the nearest integer that’s less than or equal to it.

LOOKUP
- Lookup
- Looks through a row or column for a key and returns the value of the cell in a result range located in the same position as the search row or column.

MATCH
- Lookup
- Returns the relative position of an item in a range that matches a specified value.

MAX
- Statistical
- Returns the maximum value in a numeric dataset.

MIN
- Statistical
- Returns the minimum value in a numeric dataset.

NOW
- Date
- Returns the current date and time as a date value.

ROUND
- Math
- Rounds a number to a certain number of decimal places according to standard rules.

SUM
- Math
- Returns the sum of a series of numbers and/or cells.

SUMIF
- Math
- Returns a conditional sum across a range.

TODAY
- Date
- Returns the current date as a date value.

VLOOKUP
- Lookup
- Searches down the first column of a range for a key and returns the value of a specified cell in the row found.

TEXT: format text
- TEXT
