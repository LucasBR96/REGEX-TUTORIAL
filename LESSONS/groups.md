## MATCH ONE

   [] -> matches one char inside. ie "If a character is in the group
   between both brackets, return true". For a pratical example, we have
   the Regex "[xyz]\d". On inspection:

   [xyz] <- first character must be in this group\
   \d    <- the second must be a digit
 
   So would then match with:

   "x8"\
   "x3"\
   "y0"\
   "z8"

   For compactness, some groups can be represented with
   the dash character ( \- ). The group must be a range.
   For example:

   [a-z] -> lowercase characters ( a to z )\
   [A-Z] -> uppercase ones\
   [1-9] -> digits ( except zeroes )

   So if you want o isolate all words with 5 chars and beggining
   with the uppercase **A** the regex would be. 


## MATCH NONE

   [^] -> matches with no char inside

   "^[^aeiou] is not a vowel$" matches

   "p is not a vowel"\
   "g is not a vowel"\
   "$ is not a vowel"

## MATCH ALL

   \\- -> literal dash\
   () -> matches with the whole pattern inside. Like isola
   tes it.

   "\d{3}\\-" -> three digits followed by a dash\
   "(\d{3}\\-){3}" -> the above pattern repeated three times\
   "(\d{3}\\-){3}\d{2}" matches:

   "178-587-281-28"\
   "555-970-310-00"\
   "776-543-220-10"

## MATCH EITHER

   | -> pattern either( or ). This one is a bit tricky.
   Suppose there are two patterns represented by the varia-
   bles a and b. ( a | b ) would mean "matches with either
   pattern a or b "

   A simple example would be (\d{4}|\W{2}), matching with:

   "7581"\
   "?]"  \
   "+*"  \
   "2222"

   For a more complex and real life example lets use some python.
   The Brazilian equivalent of social security number is the CPF,
   portuguese for "Record for Physical Person" ( As opposed to 
   "Judicial Person", the legal term for private businesses in the
   country ) Most databases accept two formats: Three clusters of
   three digits, with a final one of two digits, all separated by
   a dash; or plain eleven digits. A string would for this would be
   like.
   
   "((\d{3}\\-){3}\d{2}|\d{11})"

   The returning pattern would math all examples of CASE 3, plus:

   '47289401742'
   '87565632154'
   '87542369932'
