# MySQL ignores ASC/DESC keyword in CREATE INDEX

While wondering whether I should be creating ASC or DESC ordered indexes in MySQL, I came across this nice little surprise:
http://dev.mysql.com/doc/refman/5.7/en/create-index.html

> An index_col_name specification can end with ASC or DESC. These keywords are permitted for future extensions for specifying ascending or descending index value storage. **Currently, they are parsed but ignored; index values are always stored in ascending order.**
