# Intent
1. Filter values in a record so that:
    1. nulls are removed and
    1. a new table is made which preserves the ordinality of each record's remaining values
1. Assign a user-defined specific `recordCase` to each record
    + Based on a string that will match one of the values within the record

# Out of scope
1. Maintaining the original record's column name associations
1. Identifying a record based on part of a value instead of a whole value match

# Assumptions 
## Preconditions
1. The following query or query steps exist:
    1. `myMessyTable` which contains the data to be transformed.
    1. `myMappingDict` which contains the `recordCase` assignment associations.

## About `myMessyTable`
1. Table contains at least 1 record and contains no columns named `recordAsList` or `recordCase`
1. There are a variable number of values within each record.
    + Different `recordCase`es in the table don't have anything in common, even cell count.
1. Column associations within each record do not matter, only the order of the values.

Sample `myMessyTable`:
| Col1      | Col2        | Col3       | Col4       | Col5      |
| --------- | ----------- | ---------- | ---------- |---------- |
| "Hide"    | null        | "Table3"   | "Leather"  | null      |
| "Buckler" | "tblShield" | null       | null       | "-"       |
+ `TODO` add rows, sources

## About `myMappingDict`
1. Maps which string to match (`stringToMatch`) to a `recordCase` using 2 columns in a table. 
1. The `stringToMatch` column consists of unique values (records are mapped only to a single case). 
    + Many strings can map to a single `recordCase` so only `stringToMatch` needs to have unique values.   

Sample `myMappingDict`:
| recordCase  | stringToMatch |
| ------------ | ------------- |
| "armorTypes" | "Table3"      |
| "shield"     | "tblShield"   |

# Power Query plan
1. Convert each record in the table to a list (`recordAsList`) so nulls can be removed and ordinality preserved. 
1. Pass each `recordAsList` into a separate function which will determine and assign each a `recordCase`.

# Activities
## Query: `_recordCondense` moves each record in `myMessyTable` to a list 
1. Set a name for the new column. 
1. Convert each record in the table to a list, remove the nulls, then populate a new table column with the result. 
1. Place the code for the following two steps in a comment block:
    1. Add mapping logic for each row once the new list is added.
    1. Select only the list and case columns.

    ```fs
    = let
    rec = let
        messyTbl = myMessyTable,
        mapDict = myMappingDict,        
        tblWithRecList = Table.AddColumn( messyTbl, "recordAsList", 
                each List.RemoveNulls( 
                            Record.ToList(_) 
                        ) 
                    ) //,
        // tblWithCaseList = Table.AddColumn(tblWithRecList,"recordCase",each _caseMapping(_[recordAsList],mapDict)),
        // tblCaseAndList = tblWithCaseList[[recordAsList],[recordCase]]
        //+ `TODO` add extraction based on case and list ordinality
    in
        tblWithRecList
    ```
## Query: `_caseMapping` returns `recordCase` based on `stringToMatch`
1. Prepare a function for processing records to determine case. 
1. Provide the function with:
    1. The list from the transformed record
    1. The table to use as a dictionary through a 2 way lookup.
1. Look for the position of any of the `stringToMatch` values.
1. Define a local function to return `recordCase` based on which `stringToMatch` was found.
    ```fs
    = (recordAsList as list,dict as table) => let
        ind = List.PositionOfAny(recordAsList,dict[stringToMatch]),
        getCase = (rowMatchesCase) => dict{[stringToMatch = rowMatchesCase{ind}]}[recordCase],
        myCase = if ind=-1 then null else getCase(recordAsList)
    in
        myCase
    ```

