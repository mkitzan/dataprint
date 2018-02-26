# DataPrint
A lightweight python tabular data printer module. Prints a table that scales column widths to fit the data. Written to mesh with the sqlite3 python module, specifically cursor.description (list comp-ed to only have the col names), and cursor.fetchall().

# Usage
First import the function 'table' from dataprint

    from dataprint import table

For a standard table use

    table(col_labels, values)

For an augmented table use the expected arguments, and any combination of the four non-standard arguments

    table(col_labels, values, edge="#", buffer=2, transpose=True, funct=lambda x: out_file.write(x + "\n"))
    
# Non-Standard Arguments
- edge (default "\*"): when a horizontal line ("-") intersects a vertical line ("|") in the table, an edge character is placed. By default a star is used, but by including an argument for edge when table is called, you can augment what this character is.

- buffer (default 1): buffer declares the amount of whitespace between the end of the longest value in a column and that column's right vertical divider. Example: |example of buffer=1 |

- transpose (default False): will transpose the values argument if the transpose=True. Helpful if a row in your values corresponds to a row in the table rather than the expected row in values = col in table (format of a sqlite3 fetchall call)

- funct (default print): allows user to write the output of dataprint to a file, or call some function with the dataprint row as an argument.
