CASE 1 --------------------------------------------------

   {n}       -> repeat n times ( already demonstrated )
   { ,n }    -> repeat n times at most
   { n, }    -> repeat n times at minimum
   { a , b } -> repeat between a and b times

   The last three expressions are inclusive in both ends,
   now lets go to the examples.

   1 - "^\w{ ,3}\s\W{3 , }$" matches:

   "abc @$%$#"
   "a1 #@$(*&%@(&#"
   "78B #-+=§\]"

   2 - "^\d{2,10}$"

   "137495"
   "6698"
   "09253480"
   
   The following cases could be covered by this one, but
   the chars that will be introduced are useful for the 
   sake of compactness.

CASE 2 --------------------------------------------------

   * -> repeat the preceding char or group 0 or more times.
        It could be replaced by {0,} and implies that the char
        is optional.

   "^[a-z]\d*\[a-z]$" matches:

   "a1935870981476901832647019867498076109873465b"
   "z1234567890u"
   "ac"
       
CASE 3 --------------------------------------------------

   + -> its similar to case 2, but it should be repeated
        at least once. So if you replace the star of the
        previous by the plus sign in the last example, it
        would match the all the strings, except the last
        one.


CASE 1 --------------------------------------------------
CASE 1 --------------------------------------------------

