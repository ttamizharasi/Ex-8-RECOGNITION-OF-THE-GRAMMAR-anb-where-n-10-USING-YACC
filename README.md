# Ex-8-RECOGNITION-OF-THE-GRAMMAR-anb-where-n-10-USING-YACC
RECOGNITION OF THE GRAMMAR(anb where n>=10) USING YACC
# Date:
# Aim:
To write a YACC program to recognize the grammar anb where n>=10.
# ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the variables a and b.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter a string as input and it is identified as valid or invalid.
# PROGRAM:
Program: ex8.l file
```
%{
/* Lex Program for
   anb (n>=10) */
#include "y.tab.h"
%}

%%

a { return A; }
b { return B; }
\n { return '\n'; }

%%

int yywrap() {
    return 1;
}
```
Program: ex8.y file
```
%{
/* YACC program for recognizing anb(n>=10) */
#include <stdio.h>
%}

%token A B

%%

stmt: A A A A A A A A A
      anb '\n' { printf("\nValid string\n"); return 0; }
    ;

anb: A anb
    | A B
    ;

%%

int main() {
    printf("\nEnter some valid string\n");
    yyparse();
    return 0;
}

int yyerror(char *s) {
    printf("\nInvalid string\n");
    return 0; // Return 0 to indicate error handling
}
```
# OUTPUT
![image](https://github.com/ttamizharasi/Ex-8-RECOGNITION-OF-THE-GRAMMAR-anb-where-n-10-USING-YACC/assets/119657317/2b43df2e-1bdb-4659-b745-42c662754e44)

# RESULT
The YACC program to recognize the grammar anb where n>=10 is executed successfully and the output is verified.
 

