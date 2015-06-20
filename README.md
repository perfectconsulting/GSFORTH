# GSFOTH
Generic Subroutine Thread Forth for the BBC Micro
=================================================

This was my first large assember program. I wrote it the summer of 1983 (at the age of 16)

The program is written in BBC Basic using the build-in assembler. Because the source has to be in memory to assemble, this limits the maximum size of any assembly program build using BBC Basic. As work arounf I split the code into modules each chain-loding as overlays at the top of memory.

each module has a compainion file which is executed the module as when the module as assembled. The compainion has the same name as the module but with a 'E.' prefix.

hence 

CHAIN 
will EXEC "E.NUCLEUS"
with will load the overlay "MORE" and so on

the load sequnece is:
"NUCLEUS"

"NUCLEUS"



To build GSFORTH

type
chain "NECLUES"




