Download Link: https://assignmentchef.com/product/solved-cs39003-assignment4
<br>
<h1>1           Preamble – tinyC</h1>

This assignment follows the phase structure grammar specification of C language from the International Standard <strong>ISO/IEC 9899:1999 (E)</strong>. To keep the assignment within our required scope, we have chosen a subset of the specification as given below. We shall refer to this language as tinyC.

The lexical specification of tinyC, also taken and abridged from the Standard, has already been discussed in Assignment 3. The phase structure grammar specification is written using the common notation of language specifications as discussed in the last assignment.

<h1>2           Phrase Structure Grammar of tinyC</h1>

<ol>

 <li><strong>Expressions</strong></li>

</ol>

primary-expression: identifier constant string-literal

<strong>( </strong>expression <strong>) </strong>postfix-expression:

primary-expression postfix-expression <strong>[ </strong>expression <strong>] </strong>postfix-expression <strong>( </strong>argument-expression-list<sub>opt </sub><strong>) </strong>postfix-expression <strong>. </strong>identifier postfix-expression − &gt; identifier postfix-expression ++ postfix-expression −− <strong>( </strong>type-name <strong>) </strong>{ initializer-list }

<strong>( </strong>type-name <strong>) </strong>{ initializer-list <strong>, </strong>} argument-expression-list:

assignment-expression

argument-expression-list <strong>, </strong>assignment-expression

unary-expression:

postfix-expression ++ unary-expression −− unary-expression unary-operator cast-expression <strong>sizeof </strong>unary-expression <strong>sizeof ( </strong>type-name <strong>)</strong>

unary-operator: one of

&amp; * + – ~ !

cast-expression:

unary-expression

<strong>( </strong>type-name <strong>) </strong>cast-expression multiplicative-expression:

cast-expression multiplicative-expression ∗ cast-expression multiplicative-expression / cast-expression multiplicative-expression % cast-expression additive-expression:

multiplicative-expression additive-expression + multiplicative-expression additive-expression − multiplicative-expression

shift-expression:

additive-expression shift-expression &lt;&lt; additive-expression shift-expression &gt;&gt; additive-expression

relational-expression:

shift-expression relational-expression &lt; shift-expression relational-expression &gt; shift-expression relational-expression &lt;= shift-expression relational-expression &gt;= shift-expression

equality-expression:

relational-expression equality-expression == relational-expression equality-expression ! = relational-expression AND-expression:

equality-expression

AND-expression &amp; equality-expression exclusive-OR-expression: AND-expression exclusive-OR-expressionˆAND-expression

inclusive-OR-expression:

exclusive-OR-expression inclusive-OR-expression | exclusive-OR-expression

logical-AND-expression:

inclusive-OR-expression logical-AND-expression &amp;&amp; inclusive-OR-expression

logical-OR-expression:

logical-AND-expression logical-OR-expression || logical-AND-expression

conditional-expression:

logical-OR-expression logical-OR-expression ? expression : conditional-expression

assignment-expression:

conditional-expression unary-expression assignment-operator assignment-expression

assignment-operator: one of

= *= /= %= += -= &lt;&lt;= &gt;&gt;= &amp;= ^= |=

expression:

assignment-expression expression , assignment-expression

constant-expression: conditional-expression

<ol start="2">

 <li><strong>Declarations </strong>declaration:</li>

</ol>

declaration-specifiers init-declarator-list<sub>opt </sub>;

declaration-specifiers:

storage-class-specifier declaration-specifiers<sub>opt </sub>type-specifier declaration-specifiers<sub>opt </sub>type-qualifier declaration-specifiers<sub>opt </sub>function-specifier declaration-specifiers<sub>opt</sub>

init-declarator-list:

init-declarator init-declarator-list <strong>, </strong>init-declarator

init-declarator:

declarator declarator <strong>= </strong>initializer storage-class-specifier: <strong>extern static</strong>

type-specifier: <strong>void char short int long float double </strong>specifier-qualifier-list:

type-specifier specifier-qualifier-list<sub>opt </sub>type-qualifier specifier-qualifier-list<sub>opt</sub>

enumerator-list:

type-qualifier: <strong>const restrict volatile</strong>

function-specifier: <strong>inline</strong>

declarator: pointer<sub>opt </sub>direct-declarator

direct-declarator: identifier

<strong>( </strong>declarator <strong>) </strong>direct-declarator <strong>[ </strong>type-qualifier-list<sub>opt </sub>assignment-expression<sub>opt </sub><strong>] </strong>direct-declarator

<strong>[ static </strong>type-qualifier-list<sub>opt </sub>assignment-expression <strong>] </strong>direct-declarator <strong>[ </strong>type-qualifier-list <strong>static </strong>assignment-expression <strong>] </strong>direct-declarator <strong>[ </strong>type-qualifier-list<sub>opt </sub><strong>* ] </strong>direct-declarator <strong>( </strong>parameter-type-list <strong>) </strong>direct-declarator <strong>( </strong>identifier-list<sub>opt </sub><strong>)</strong>

pointer:

<ul>

 <li>type-qualifier-list<sub>opt</sub></li>

 <li>type-qualifier-list<sub>opt </sub>pointer type-qualifier-list:</li>

</ul>

type-qualifier type-qualifier-list type-qualifier

parameter-type-list: parameter-list parameter-list <strong>, … </strong>parameter-list:

parameter-declaration parameter-list <strong>, </strong>parameter-declaration parameter-declaration: declaration-specifiers declarator declaration-specifiers

identifier-list:

identifier identifier-list <strong>, </strong>identifier

type-name:

specifier-qualifier-list

initializer:

assignment-expression { initializer-list }

{ initializer-list <strong>, </strong>} initializer-list:

designation<sub>opt </sub>initializer initializer-list <strong>, </strong>designation<sub>opt </sub>initializer

designation: designator-list <strong>=</strong>

designator-list:

designator designator-list designator

designator:

<strong>[ </strong>constant-expression <strong>]</strong>

<strong>. </strong>identifier

<ol start="3">

 <li><strong>Statements </strong>statement:</li>

</ol>

labeled-statement compound-statement expression-statement selection-statement iteration-statement jump-statement

labeled-statement:

identifier <strong>: </strong>statement <strong>case </strong>constant-expression <strong>: </strong>statement <strong>default : </strong>statement

compound-statement:

{ block-item-list<sub>opt </sub>} block-item-list:

block-item block-item-list block-item

block-item: declaration statement

expression-statement: expression<sub>opt </sub><strong>;</strong>

selection-statement:

<strong>if ( </strong>expression <strong>) </strong>statement <strong>if ( </strong>expression <strong>) </strong>statement <strong>else </strong>statement <strong>switch ( </strong>expression <strong>) </strong>statement iteration-statement:

<strong>while ( </strong>expression <strong>) </strong>statement <strong>do </strong>statement <strong>while ( </strong>expression <strong>) ; for ( </strong>expression<sub>opt </sub><strong>; </strong>expression<sub>opt </sub><strong>; </strong>expression<sub>opt </sub><strong>) </strong>statement <strong>for ( </strong>declaration expression<sub>opt </sub><strong>; </strong>expression<sub>opt </sub>) statement

jump-statement: <strong>goto </strong>identifier <strong>; continue ; break ; return </strong>expression<sub>opt </sub><strong>;</strong>

<ol start="4">

 <li><strong>External definitions </strong>translation-unit:</li>

</ol>

external-declaration translation-unit external-declaration

external-declaration: function-definition declaration

function-definition: declaration-specifiers declarator declaration-list<sub>opt </sub>compound-statement

declaration-list:

declaration declaration-list declaration

<h1>3           The Assignment</h1>

<ol>

 <li>Write a bison specification for defining the tokens of tinyC and generate the required y.tab.h file.</li>

 <li>Write a bison specification for the language of tinyC using the above phase structure grammar. Use the flex specification that you had developed for Assignment 3 (if required, you may fix your flex specification).</li>

 <li>While writing the bison specification, you may need to make some changes to the grammar. For example, some non-terminals like</li>

</ol>

argument-expression-list<sub>opt</sub>

are shown as optional on the right-hand-side as: postfix-expression:

postfix-expression <strong>( </strong>argument-expression-list<sub>opt </sub><strong>)</strong>

One way to handle them would be to introduce a new non-terminal, argument-expression-list-opt, and a pair of new productions:

argument-expression-list-opt:

argument-expression-list

and change the above rule as: postfix-expression:

postfix-expression <strong>( </strong>argument-expression-list-opt <strong>)</strong>

<ol start="4">

 <li>Names of your .l and .y files should be asgn4 roll.l and asgn4 roll.y respectively. The .y or the .l file should not contain the function main(). Write your main() (in a separate file asgn4 roll.c) to test your lexer and parser.</li>

 <li>Prepare a Makefile to compile the specifications and generate the lexer and the parser.</li>

 <li>Prepare a test input file asgn4 roll c that will test all the rules that you have coded.</li>

 <li>Prepare a tar-archive with the name asgn4 roll.tar containing all the files and upload to Moodle.</li>

</ol>

<h1>4           Credits</h1>

<ol>

 <li>Specifications and testing: <strong>70</strong></li>

 <li>Main file and makefile: <strong>10</strong></li>

 <li>Test file: <strong>20</strong></li>

</ol>