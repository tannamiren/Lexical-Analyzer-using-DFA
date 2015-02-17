#Lexical-Analyzer-using-DFA
Program to perform lexical analysis of a program written in ASN.1 notation. 

Part of **CS 6353 Compiler Construction** coursework.

####ASN.1 Notation
Available character sets:

* A to Z (LATIN CAPITAL LETTER A to LATIN CAPITAL LETTER Z) 
* a to z (LATIN SMALL LETTER A to LATIN SMALL LETTER Z) 
* 0 to 9 (DIGIT ZERO to DIGIT 9) 
* " (QUOTATION MARK)
* ( (LEFT PARENTHESIS)  
* ) (RIGHT PARENTHESIS) 
* , (COMMA)
* - (HYPHEN-MINUS)
* : (COLON)
* = (EQUALS SIGN) 
* { (LEFT CURLY BRACKET) 
* | (VERTICAL LINE) 
* } (RIGHT CURLY BRACKET)

####Type of tokens and rules:

1. A lexical item shall be separated from a following lexical item by one or more instances of white-space.
2. `White-space` - numbers represent the ASCII Code: <br>
HORIZONTAL TABULATION (9) 
LINE FEED (10) 
VERTICAL TABULATION (11) 
FORM FEED (12) 
CARRIAGE RETURN (13) 
SPACE (32) 

3. Type references <br>
Name of lexical item – `typereference`
A "typereference" shall consist of an arbitrary number (one or more) of letters, digits, and hyphens. The initial  
character shall be an upper-case letter. A hyphen shall not be the last character. A hyphen shall not be immediately 
followed by another hyphen. 

4. Identifiers <br>
Name of lexical item – `identifier`
An "identifier" shall consist of an arbitrary number (one or more) of letters, digits, and hyphens. The initial 
character shall be a lower-case letter. A hyphen shall not be the last character. A hyphen shall not be 
immediately followed by another hyphen. 

5. Numbers <br>
Name of lexical item – `number` 
A "number" shall consist of one or more digits. The first digit shall not be zero unless the "number" is a single digit. 

6. Assignment lexical item<br> 
Name of lexical item – `::=` 
This lexical item shall consist  of the sequence of characters: `::=` 

7. Range separator <br>
Name of lexical item – `..` 
This lexical item shall consist of the sequence of characters: `..` 
8. `{`  - LURLY
9. `}` – RCURLY
10.	`,` – COMMA
11.	`(` – LPAREN
12.	`)` – RPAREN
13.	`|` – BAR
14.	`"`  QUOTE

####Files:

#####DFA.tif
Image file of Deterministic Finite Automata (DFA), describing the acceptable states for the grammar involving the above
listed lexical items. The DFA states emulate the working of a regular expression. This DFA is stored in the form a 
square matrix in **`main.c`**, where `DFA[row_index][column_index]=next_state`. `row_index` is the current character that 
was read by the program from the test file, and the `column_index` is the current state of the DFA. The `next_state` 
is used with the current character that was read, to obtain the next possible state.

#####main.c
Consists of the main code that performs lexical analysis on the test file. The code reads the test file character by
character and based on the DFA switches from one state to another. On arriving at the final state, the program detects
the nature of the lexical item based on the flags that were set during the state transitions. If the program encounters
a failed state, it stops reading the test file, and returns all the lexical items that were identified till the point
where error had occurred, along with an error message.

#####test.txt
Text file containing code on which Lexical Analysis needs to be performed. 
