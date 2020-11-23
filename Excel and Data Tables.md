# Excel and Data Tables

## What are DataTables?
DataTable is the type of variable that can store data as a simple spreadsheet with rows and columns, so that each piece of data can be identified based on their unique column and row coordinates. Think of it as the memory representation of an Excel worksheet. 

In DataTables, the regular convention of identifying the columns and the rows is applied - columns are identified through capital letters, and rows through numbers.

## How are DataTables created?
- **Build Data Table**: By using this activity, you get to choose the number of columns and the data type of each of them. Moreover, you get to configure each column with specific options like allow null values, unique values, auto-increment (for numbers), default value and length (for strings).
- **Read Range**: This activity gets the content of a worksheet (or a selection from that worksheet) and stores it in a DataTable variable, which can be created from the Properties panel using Ctrl + K.
- **Read CSV**: This activity captures the content of a CSV file and stores it in a DataTable variable. Although not commonly used anymore, there are still legacy or internal-built applications that work with this kind of documents. 
- **Data Scraping**: This functionality of UiPath Studio enables you to extract structured data from your browser, application or document to a DataTable.

## DataTable Activites
- **Add Data Column**: Adds a column to an existing DataTable variable. The input data can be of DataColumn type or the column can be added empty, by specifying the data type and configuring the options (allowing null values, requesting unique values, auto-incrementing, default value and maximum length). 
- **Add Data Row**: Adds a new row to an existing DataTable variable. The input data can be of DataRow type or can be entered as an Array Row, by matching each object with the data type of each column.
- **Build Data Table**: Is used to create a DataTable using a dedicated window. This activity allows the customization of number of columns and type of data for each column.  
- **Clear Data Table**: Clears all the data in an existing DataTable variable.
- **Filter Data Table**: Allows filtering a DataTable through a Filter Wizard, using various conditions. This activity can be configured to create a new DataTable for the output of the activity, or to keep the existing one and filter out (delete) the entries that do not match the filtering conditions.
- **For Each Row**: Is used to perform a certain activity for each row of a DataTable (similar to a For Each loop).
- **Generate Data Table**: Can be used to create a DataTable from unstructured data, by letting the user indicate the row and column separators.
- **Join Data Tables**: Combines rows from two tables by using values common to each other, according to a Join rule that answers the question "What to do with the data that doesn't match?". It is one of the most useful activities in business scenarios, where working with more than one Data Table is very common. This is why we'll cover in more in depth below.
- **Lookup Data Table**: Is similar to vLookup in Excel, as it allows searching for a provided value in a specified DataTable and returns the RowIndex at which it was found, or can be configured to return the value from a cell with given coordinates (RowIndex and Target Column).
- **Merge Data Table**: Is used to append a specified DataTable to the current DataTable. The operation is more simple than the Join Data Type activity, as it has 4 predefined actions to perform over the missing schema.
- **Output Data Table**: Writes a DataTable to a string using the CSV format.
- **Remove Data Column**: Removes a certain column from a specified DataTable. The input may consist of the column index, column name or a Data Column variable.
- **Remove Data Row**: Removes a row from a specified DataTable. The input may consist of the row index or a Data Row variable.
- **Remove Duplicate Rows**: Removes the duplicate rows from a specified DataTable variable, keeping only the first occurrence.
- **Sort Data Table**: Can sort a DataTable ascending or descending based on the values in a specific column.

## Join Data Tables
### How Does it work?
1. **3 Data Table Variables** have to be specified - 2 Input DataTables and 1 Output DataTable. Please note that the order of the first 2 is very important, as there is one option that keeps the values from Data Table 1 and it cannot be changed.
2. The **Join Type** has to be chosen - there are 3 options:
    - Inner: Keep all rows from both tables that meet the Join rule. Any rows that do not meet the rule are removed from the resulting table.
    - Left: Keep all rows from DataTable1 and only the values from DataTable2 which meet the Join rule. Null values are inserted into the column for the rows from DataTable1 that don't have a match in the DataTable2 rows.
    - Full: Keep all rows from DataTable1 and DataTable2, regardless of whether the join condition is met. Null values are added into the rows from both tables that don't have a match.
3. The **Join rules** have to be configured (there can be one or more rules):
    - One column from each DataTable has to be specified by their names (String), by their index (Int32) or by ExcelColumn variables
    - The operator has to be chosen: = (Equal to), != (Not equal to), > (Greater than), < (Less than), >= (Greater than or equal to), <= (Less than or equal to)
