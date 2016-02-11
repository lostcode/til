# char vs. varchar 

* CHAR is a fixed length text field. 
* regardless of how many characters your value actually has, CHAR will store the "length" number of characters.
* VARCHAR by default does *not* error out if you try to add a value greater than "length", it simply truncates it to fit the "length" 

This table from this [link](http://dev.mysql.com/doc/refman/5.7/en/char.html) summarizes it: 

Value      | CHAR(4) | Storage Required | VARCHAR(4)  | Storage Required
-----------|---------|------------------|-------------|-----------------
''         | ' '     | 4 bytes          | ''          | 1 byte
'ab'       | 'ab '   | 4 bytes          | 'ab'        | 3 bytes
'abcd'     | 'abcd'  | 4 bytes          | 'abcd'      | 5 bytes
'abcdefgh' | 'abcd'  | 4 bytes          | 'abcd'      | 5 bytes

