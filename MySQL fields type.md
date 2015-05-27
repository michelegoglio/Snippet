#MySQL Field Types

##Text Types

`CHAR ( )`
A fixed section from 0 to 255 characters long.

`VARCHAR ( )`
A variable section from 0 to 255 characters long.

`TINYBLOB, TINYTEXT`
A string with a maximum length of 255 characters.

`BLOB, TEXT`
A string with a maximum length of 65535 characters.

`MEDIUMBLOB, MEDIUMTEXT`
A string with a maximum length of 16777215 characters.

`LONGBLOB, LONGTEXT`
A string with a maximum length of 4294967295 characters.



##Number Types

`TINYINT ( )`
-128 to 127 normal
0 - 255 UNSIGNED.

`SMALLINT ( )`
-32768 to 32767 normal
0 to 65535 UNSIGNED.

`MEDIUMINT ( )`
The signed range is -8388608 to 8388607 normal
0 to 16777215 UNSIGNED.
 
`INT ( )`
-2147483648 to 2147483647 normal
0 to 4294967295 UNSIGNED.

`BIGINT ( )`
-9223372036854775808 to 9223372036854775807 normal
0 to 18446744073709551615 UNSIGNED.

`FLOAT`
A small number with a floating decimal point.
DOUBLE ( , )
A large number with a floating decimal point.

`DECIMAL ( , )`
A DOUBLE stored as a string, allowing for a fixed decimal point.



##Date Types

`DATE`
YYYY-MM-DD

`DATETIME`
YYYY-MM-DD HH:MM:SS

`TIMESTAMP`
YYYYMMDDHHMMSS

`TIME`
HH:MM:SS

`YEAR`
4-digit year (YYYY)



##Miscellaneous Types

`ENUM ( )`
Short for ENUMERATION which means that each column may have one of a specified possible values.

`SET`
Similar to ENUM except each column may have more than one of the specified possible values.


Note: The `( )` brackets allow you to enter a maximum number of characters will be used in the column 
ex. `VARCHAR(20)`. 

For double and decimal, there are two items allowed: length followed by the number of digits after the decimal point (significant digits) 
ex. `double (10,3)` would allow 10 digits and keep 3 numbers after the decimal point.
