# Characters and their meaning

Broadly speaking, I like to split the Regex characters in two groups.

The first ones are the literal characters. Wicht, you guessed, should be literally searched by the code. they are:

1. all letters ( lower and upper case )
2. all numerals ( 0 , 1 ... 9 )
3. the underscore

To illustrate better, here is an example: the regex "cat" matches the word **cat** in the sentence "i have a cat and a dog"

Now what makes regex really useful are the special characters. In a pattern they represent especial conditions to match, not their literal meaning. 

Let's take the dollar sign character. In a pattern, they mean "end of the string". so the pattern "cat$" will only match the second "cat" in the sentence "black cat, white **cat**".

   The special characters are **[]{}|()\?!*=+^$** ( The ones I remember at least ). In the following lessons each one will be given the proper attention owed. Except one..

You might be wondering: "What if I want to match a literal dollar sign for something like finding all the price tags in text?". For that I'll introduce you to the ( probably already known ) **\\** ( backslash ) character. This is the most special of the charachters, as he flips the status of the character to its right.

Back the dollar sign character, if want to find all the price tags in a sentence, you'll use "\\$" as pattern, matching all dollar signs in the sentence: "the shirt was **$**10 while the shoes were **$** 25" It should be noted, however, that the regex only matches the dollar sign, not the following number.

The backslash works the other way arround. To the left of a literal character, it turns it into a special one. look at the following examples.

## CASE 1 

   .   -> anything but a newline\
   \.  -> literal dot           \
   {n} -> repeat exactly n times\
   ^   -> begin                 \
   $   -> end                   \

   "^.{3}\..{3}\..{3}\..{3}$" matches:

   "abc.def.ghi.jkx"\
   " u . 87.+[{.ab "\
   "123.456.789.acd"

## CASE 2 

   \d -> digit ( 0 , 1 , 2 ... 9 )\
   \D -> non digit\

   "^\d{2}\D\d{2}\D\d{4}$" matches:

   "12a34b5678"\
   "90 21~6666"\
   "77.77.5555"

## CASE 3 

   \s -> whitespace ( simple space, tabs, newlines )\
   \S -> not whitespace

   "^s\s\d{2}\s\S$" matches:

   "s 54 A"\
   "s 87 5"\
   "s 97   \
   +"
   
## CASE 4 

   \w -> word char ( a ... z, A .. Z, 0...9, _ )\
   \W -> not word char\
   w  -> literal w

   "^\w{3}\W$" matches:

   "abc#"
   "Cd1="
   "Gh2@"

## OBSERVATIONS 

   As you've already guessed, the chars "\.{}^$" are special
   characters. Like the dot, to get the literal, you must put
   a backslash before the character, ex:

   \" -> literal quote\
   \^ -> literal hat\
   \\ -> literal backslash

   All special chars introduced in the following lessons will
   also follow this rule.

   numbers can also be turned in special characters, but this will be discussed later
