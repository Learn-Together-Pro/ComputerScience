# PostgresSQL Cheat sheets

## String Conversion

Retrieves the ASCII code of a given character.

```sql
ASCII ('y') = 121
ASCII ('B') = 66
```

Transforms a string to ASCII from a different encoding system.

```sql
TO_ASCII ('hello') = 'hello'
```

Maps a given code to its corresponding character.

```sql
CHR (66) = 'B'
CHR (128) = 'Ç'
CHR (NULL) = NULL
```

Converts text to a specified encoding format.

```sql
CONVERT ('Example', 'UTF8', 'LATIN9') = 'Example'
```

Translates binary data into a textual representation or vice versa.

```sql
ENCODE ('4321', 'base64') = 'NDMyMQ=='
DECODE ('NDMyMQ==', 'base64') = 4321
```

Capitalizes the first letter of each word in a string.

```sql
INITCAP ('good morning') = 'Good Morning'
INITCAP ('welcome-home') = 'Welcome-Home'
INITCAP ('sleepwell') = 'Sleepwell'
```

Alters the case of a string to lower or upper.

```sql
LOWER ('LOWER') = 'lower'
UPPER ('upper') = 'UPPER'
```

Computes the MD5 hash of a string and returns the result in hexadecimal form.

```sql
MD5 ('xyz') = 'd16fb36f0911f878998c136191af705e'
```

Identifies the current client encoding.

```sql
PG_CLIENT_ENCODING () = 'LATIN1'
```

Appropriately quotes a string for use as an identifier in SQL statements.

```sql
QUOTE_IDENT ('USER_ID') = '"USER_ID"'
```

Properly quotes a string for use as a literal in SQL queries.

```sql
QUOTE_LITERAL ('xyz') = '''xyz'''
QUOTE_LITERAL ('D''Angelo') = '''D''Angelo'''
QUOTE_LITERAL (100) = '100'
QUOTE_LITERAL ('XYZ') = '''XYZ'''
```

Quotes a string for use in SQL, or returns NULL if the input is null.

```sql
QUOTE_NULLABLE (NULL) = NULL
QUOTE_NULLABLE (100.5) = '''100.5'''
```

Converts numbers into their hexadecimal equivalents.

```sql
TO_HEX (15) = 'f'
TO_HEX (123) = '7b'
TO_HEX (1023) = '3ff'
```
## String Measurement

Determines the bit length of a string.

```sql
BIT_LENGTH ('hello') = 40
BIT_LENGTH ('ß') = 16
BIT_LENGTH ('ñ') = 16
```

Counts the characters in a string.

```sql
CHAR_LENGTH ('hello') = 5
CHARACTER_LENGTH ('world') = 5
LENGTH ('text', 'UTF8') = 4
```

Calculates the byte length of a string.

```sql
OCTET_LENGTH ('CD') = 2
OCTET_LENGTH ('ß') = 2
OCTET_LENGTH ('ñ') = 2
```

## String Modification

Concatenates two or more strings together.

```sql
'Hello' || 'World' = 'HelloWorld'
'Count: ' || 100 = 'Count: 100'
```

Trims characters from both ends of a string.

```sql
BTRIM (' XY ') = 'XY'
BTRIM ('+XY+', '+') = 'XY'
TRIM (' ' FROM ' XY ') = 'XY'
LTRIM ('+XY+', '+') = 'XY+'
RTRIM (leading '_' from '__XY__') = 'XY__'
RTRIM ('__XY__','_') = '__XY'
RTRIM (trailing '_' from '__XY__') = '__XY'
```

Pads a string to a certain length with another string.

```sql
LPAD ('DEF', 6) = '   DEF'
RPAD ('DEF', 6) = 'DEF   '
LPAD ('456', 6, '0') = '000456'
RPAD ('e', 3, '-') = 'e--'
```

Substitutes part of a string with a different string.

```sql
OVERLAY('456' placing '2' from 2 for 3)='42'
OVERLAY('456' placing '-' from 1 for 2)='-6'
OVERLAY('456' placing 'L' from 2 for 1)='4L6'
```

Duplicates a string a specified number of times

```sql
REPEAT ('Ab', 3) = 'AbAbAb'
```

Substitutes characters in a string based on a mapping set

```sql
TRANSLATE ('45654', '45', 'xy') = 'xy6yx'
```

Alters a string by replacing sequences that match a regular expression pattern

```sql
REGEXP_REPLACE('Jump','p','l') = 'Juml'
REGEXP_REPLACE ('Jump','p(.*)', '1') = 'J1'
REGEXP_REPLACE('Jump','p','q') = 'Jumq'
REGEXP_REPLACE('Jump','p(.{1})','1') = 'Ju1'
REGEXP_REPLACE('20 hh','[^\d]','0') = '200 hh'
REGEXP_REPLACE('20 h','\s','+') = '20+h'
REGEXP_REPLACE ('20 h','[\s]{2,}',' ') = '20 h'
REGEXP_REPLACE('def','\W.+','') = ''
```

Divides a string based on a delimiter and returns a specified segment

```sql
SPLIT_PART ('4,5,6',',',2) = '5'
```

Retrieves a portion of a string starting at a particular position for a specified length

```sql
SUBSTRING ('67890' from 2 for 3) = '789'
SUBSTR ('67890', 3, 2) = '78'
```

Extracts a substring from a string that matches a regular expression pattern

```sql
SUBSTRING ('Abcdef' from '\(.{3}\)') = 'bcd'
```

Extracts a substring using a SQL pattern matching condition

```sql
SUBSTRING('FGHIJ' from '%#"FG_"H' for'#') = 'GH'
SUBSTRING('FGHIJ' from '%#"FG_"H' for'_'') = NULL
```

Replaces all instances of a specified substring within a string with a different substring

```sql
REPLACE ('X-Y-Z', '-', '+') = 'X+Y+Z'
```
## String Search and Match

Identifies the position of a specified substring within a string

```sql
POSITION ('la' in 'Salad') = 3
STRPOS ('Salad', 'la') = 3
```

Captures all the substrings that match a regular expression pattern within a string

```sql
REGEXP_MATCHES('a,b,c', '(\w),(\w),(\w)') = {"a","b","c"}
REGEXP_MATCHES('123', '\d') = {'1','2','3'}
```

Separates a string into an array or table based on a regular expression delimiter

```sql
REGEXP_SPLIT_TO_ARRAY ('Hello World', E'\\s+') = {Hello,World}
REGEXP_SPLIT_TO_TABLE ('Hello World', E'\\s+') = Hello | World (2 rows)
```

Determines if a string matches a specified pattern

```sql
'Hello' LIKE '_e%' = true
'Hello' NOT LIKE 'H%' = false
'Hello' SIMILAR TO 'He%' = true
'Hello' NOT SIMILAR TO '_e%' = false
```
## DCL Permissions

Instructions to become the postgres superuser to avoid permission errors.

```shell
sudo su - postgres
psql
```

Commands to grant all permissions on a specific database.

```sql
GRANT ALL PRIVILEGES ON DATABASE db_example TO user_example;
```

Commands to allow a user to connect to a specific database.

```sql
GRANT CONNECT ON DATABASE db_example TO user_example;
```

Commands to allow usage of a specific schema.

```sql
GRANT USAGE ON SCHEMA public TO user_example;
```

Commands to permit execution of all functions within a schema.

```sql
GRANT EXECUTE ON ALL FUNCTIONS IN SCHEMA public TO user_example;
```

Commands to allow various operations on all tables within a schema.

```sql
GRANT SELECT, UPDATE, INSERT ON ALL TABLES IN SCHEMA public TO user_example;
```

Commands to grant specific operations on a single table.

```sql
GRANT SELECT, UPDATE, INSERT ON table_example TO user_example;
```

Commands to permit only select operation on all tables within a schema.

```sql
GRANT SELECT ON ALL TABLES IN SCHEMA public TO user_example;
```

## DCL Users

Command to list all roles.

```sql
SELECT rolname FROM pg_roles;
```

Command to create a new user.

```sql
CREATE USER user_example WITH PASSWORD 'password123';
```

Command to remove a user.

```sql
DROP USER IF EXISTS user_example;
```

Command to change a user's password.

```sql
ALTER ROLE user_example WITH PASSWORD 'newpassword123';
```
