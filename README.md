# GSFORTH
Generic Subroutine Thread Forth for the BBC Micro
=================================================

This was my first large assember program. I wrote it the summer of 1983 (at the age of 16)

The program is written in BBC Basic using the build-in assembler. Because the source has to be in memory to assemble, this limits the maximum size of any assembly program built using BBC Basic. As work around I split the code into modules each chain-loding as overlays at the top of memory.

each module has a compainion file which is executed when the module as assembled. The compainion has the same name as the module but with a 'E.' prefix.

hence 

CHAIN 
will EXEC "E.NUCLEUS"
with will load the overlay "MORE" and so on

the load sequnece is:
"NUCLEUS"
"MORE"
"O.STACK"
"O.ASTACK"
"O.IO"
"O.MATHS"
"O.LOGIC"
"PRIMARY"
"AUX"
"SECOND"
"OTHER"
"PRELUDE"
"EXTRA"
"GSFORTH"
"FINAL"

To build GSFORTH

type
chain "NECLUES"




