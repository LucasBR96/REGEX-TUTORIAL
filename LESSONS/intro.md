# Characters and their meaning

Broadly speaking, I like to split the Regex characters in two groups.

The first ones are the literal characters. Wicht, you guessed, should be literally searched by the code. they are:

1. all letters ( lower and upper case )
2. all numerals ( 0 , 1 ... 9 )
3. the underscore

to illustrate better, here is an example: the regex "cat" matches the word **cat** in the sentence "i have a cat and

## CASE 1 

   .   -> anything but a newline
   \.  -> literal dot
   {n} -> repeat exactly n times
   ^   -> begin
   $   -> end

   "^.{3}\..{3}\..{3}\..{3}$" matches:

   "abc.def.ghi.jkx"
   " u . 87.+[{.ab "
   "123.456.789.acd"

CASE 2 --------------------------------------------------

   \d -> digit ( 0 , 1 , 2 ... 9 )
   \D -> non digit
   d  -> literal d

   "^\d{2}\D\d{2}\D\d{4}$" matches:

   "12a34b5678"
   "90 21~6666"
   "77.77.5555"

CASE 3 --------------------------------------------------

   \s -> whitespace ( simple space, tabs, newlines )
   \S -> not whitespace
   s  -> literal s

   "^s\s\d{2}\s\S$" matches:

   "s 54 A"
   "s 87 5"
   "s 97
   +"
   
CASE 4 --------------------------------------------------

   \w -> word char ( a ... z, A .. Z, 0...9, _ )
   \W -> not word char
   w  -> literal w

   "^\w{3}\W$" matches:

   "abc#"
   "Cd1="
   "Gh2@"

EXTRA CASE ----------------------------------------------

   As you've already guessed, the chars "\.{}^$" are special
   characters. Like the dot, to get the literal, you must put
   a backslash before the character, ex:

   \" -> literal quote
   \^ -> literal hat
   \\ -> literal backslash

   All special chars introduced in the following lessons will
   also follow this rule.
