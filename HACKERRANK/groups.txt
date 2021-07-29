CASE 1 --------------------------------------------------

   [] -> matches one char inside
   
   "[xyz]{3}" matches:

   "xyz"
   "xxx"
   "xyx"
   "zxy"

CASE 2 --------------------------------------------------

   [^] -> matches with no char inside

   "^[^aeiou] is not a vowel$" matches

   "p is not a vowel"
   "g is not a vowel"
   "$ is not a vowel"

CASE 3 --------------------------------------------------
   
   \- -> literal dash
   () -> matches with the whole pattern inside. Like isola
   tes it.

   "\d{3}\-" -> three digits followed by a dash
   "(\d{3}\-){3}" -> the above pattern repeated three times
   "(\d{3}\-){3}\d{2}" matches:

   "178-587-281-28"
   "555-970-310-00"
   "776-543-220-10"

CASE 4 --------------------------------------------------

   | -> pattern either( or ). This one is a bit tricky.
   Suppose there are two patterns represented by the varia-
   bles a and b. ( a | b ) would mean "matches with either
   pattern a or b "

   A simple example would be (\d{4}|\W{2}), matching with:

   "7581"
   "?]"
   "+*"
   "2222"

   For a more complex and real life example lets use some python.
   The Brazilian equivalent of social security number is the CPF,
   portuguese for "Record for Physical Person" ( As opposed to 
   "Judicial Person", the legal term for private businesses in the
   country ) Most databases accept two formats: Three clusters of
   three digits, with a final one of two digits, all separated by
   a dash; or plain eleven digits. A string would for this would be
   like.

   '''
   def load_cpf_patterns():

      a = '(\d{3}\-){3}\d{2}'
      b = '\d{11}'

      cpf_pat = r( '(' + a + '|' + b + ')' )
      return re.compile( cpf_pat )
   '''

   The returning pattern would math all examples of CASE 3, plus:

   '47289401742'
   '87565632154'
   '87542369932'
