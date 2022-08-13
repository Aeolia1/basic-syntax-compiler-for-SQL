# basic-language-compiler-for-SQL
Refer to the syntax of SQL to implement the parser and interpreter for inputs. The function is similar to the basic SQL syntax, including create, update, select, etc. and compound logic processing;

## Project Background


## SQL Syntax Implemented
- USE
- CREATE
- DROP
- ALTER
- INSERT
- SELECT
- UPDATE
- DELETE
- JOIN


## SQL Syntax BNF
```

<Command>        ::=  <CommandType> ";"

<CommandType>    ::=  <Use> | <Create> | <Drop> | <Alter> | <Insert> | <Select> | <Update> | <Delete> | <Join>

<Use>            ::=  "USE " <DatabaseName>

<Create>         ::=  <CreateDatabase> | <CreateTable>

<CreateDatabase> ::=  "CREATE DATABASE " <DatabaseName>

<CreateTable>    ::=  "CREATE TABLE " <TableName> | "CREATE TABLE " <TableName> "(" <AttributeList> ")"

<Drop>           ::=  "DROP DATABASE " <DatabaseName> | "DROP TABLE " <TableName>

<Alter>          ::=  "ALTER TABLE " <TableName> " " <AlterationType> " " <AttributeName>

<Insert>         ::=  "INSERT INTO " <TableName> " VALUES(" <ValueList> ")"

<Select>         ::=  "SELECT " <WildAttribList> " FROM " <TableName> | "SELECT " <WildAttribList> " FROM " <TableName> " WHERE " <Condition> 

<Update>         ::=  "UPDATE " <TableName> " SET " <NameValueList> " WHERE " <Condition> 

<Delete>         ::=  "DELETE FROM " <TableName> " WHERE " <Condition>

<Join>           ::=  "JOIN " <TableName> " AND " <TableName> " ON " <AttributeName> " AND " <AttributeName>

<Digit>          ::=  "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

<Uppercase>      ::=  "A" | "B" | "C" | "D" | "E" | "F" | "G" | "H" | "I" | "J" | "K" | "L" | "M" | "N" | "O" | "P" | "Q" | "R" | "S" | "T" | "U" | "V" | "W" | "X" | "Y" | "Z"

<Lowercase>      ::=  "a" | "b" | "c" | "d" | "e" | "f" | "g" | "h" | "i" | "j" | "k" | "l" | "m" | "n" | "o" | "p" | "q" | "r" | "s" | "t" | "u" | "v" | "w" | "x" | "y" | "z"

<Letter>         ::=  <Uppercase> | <Lowercase>

<PlainText>      ::=  <Letter> | <Digit> | <Letter> <PlainText> | <Digit> <PlainText>

<Symbol>         ::=  "!" | "#" | "$" | "%" | "&" | "(" | ")" | "*" | "+" | "," | "-" | "." | "/" | ":" | ";" | ">" | "=" | "<" | "?" | "@" | "[" | "\" | "]" | "^" | "_" | "`" | "{" | "}" | "~"

<Space>          ::=  " "

<NameValueList>  ::=  <NameValuePair> | <NameValuePair> "," <NameValueList>

<NameValuePair>  ::=  <AttributeName> "=" <Value>

<AlterationType> ::=  "ADD" | "DROP"

<ValueList>      ::=  <Value> | <Value> "," <ValueList>

<DigitSequence>  ::=  <Digit> | <Digit> <DigitSequence>

<IntegerLiteral> ::=  <DigitSequence> | "-" <DigitSequence> | "+" <DigitSequence> 

<FloatLiteral>   ::=  <DigitSequence> "." <DigitSequence> | "-" <DigitSequence> "." <DigitSequence> | "+" <DigitSequence> "." <DigitSequence>

<BooleanLiteral> ::=  "TRUE" | "FALSE"

<CharLiteral>    ::=  <Space> | <Letter> | <Symbol>

<StringLiteral>  ::=  "" | <CharLiteral> | <CharLiteral> <StringLiteral>

<Value>          ::=  "'" <StringLiteral> "'" | <BooleanLiteral> | <FloatLiteral> | <IntegerLiteral> | "NULL"

<TableName>      ::=  <PlainText>

<AttributeName>  ::=  <PlainText>

<DatabaseName>   ::=  <PlainText>

<WildAttribList> ::=  <AttributeList> | "*"

<AttributeList>  ::=  <AttributeName> | <AttributeName> "," <AttributeList>

<Condition>      ::=  "(" <Condition> ")AND(" <Condition> ")" | "(" <Condition> ")OR(" <Condition> ")" | <AttributeName> <Operator> <Value>

<Operator>       ::=  "==" | ">" | "<" | ">=" | "<=" | "!=" | " LIKE "

```
