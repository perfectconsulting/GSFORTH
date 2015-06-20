
   10 PROCheader("emit")

   20 emit%=P%

   30 FORo%=0TO3STEP3

   40   P%=emit%

   50   [:OPTo%

   60   CPX#stkbot%

   70   BEQunderflow

   80   LDAstk%+1,X

   90   JSR&FFEE

  100   INX:INX

  110   CLC

  120   LDY#uvout%

  130   LDA(up%),Y

  140   ADC#&01

  150   STA(up%),Y

  160   BCCfinish

  170   INY

  180   LDA(up%),Y

  190   ADC#&00

  200   STA(up%),Y

  210   .finish

  220   RTS

  230   .underflow

  240   LDA#estku%

  250   JMP(svct%)

  260   ]:NEXTo%

  270 PROCheader(">vdu")

  280 tovdu%=P%

  290 FORo%=0TO3STEP3

  300   P%=tovdu%

  310   [:OPTo%

  320   CPX#stkbot%

  330   BEQunderflow

  340   LDAstk%+1,X

  350   JSR&FFEE

  360   INX:INX

  370   RTS

  380   .underflow

  390   LDA#estku%

  400   JMP(svct%)

  410   ]:NEXTo%

  420 PROCheader("key")

  430 key%=P%

  440 FORo%=0TO3STEP3

  450   P%=key%

  460   [:OPTo%

  470   CPX#stktop%

  480   BEQoverflow

  490   DEX:DEX

  500   LDA#&00

  510   STAstk%+2,X

  520   JSR&FFE0

  530   STAstk%+1,X

  540   BCCkeyend

  550   CMP#&1B

  560   BNEkeyend

  570   LDA#&7E

  580   STXsc%

  590   JSR&FFF4

  600   LDXsc%

  610   .keyend

  620   RTS

  630   .overflow

  640   LDA#estko%

  650   JMP(svct%)

  660   ]:NEXTo%

  670 PROCheader("?key")

  680 qkey%=P%

  690 FORo%=0TO3STEP3

  700   P%=qkey%

  710   [:OPTo%

  720   CPX#stkbot%

  730   BEQunderflow

  740   STXsc%

  750   LDA#&0F

  760   LDX#&00

  770   JSR&FFF4

  780   LDXsc%

  790   LDYstk%+2,X

  800   LDAstk%+1,X

  810   TAX

  820   LDA#&81

  830   JSR&FFF4

  840   TXA

  850   LDXsc%

  860   STAstk%+1,X

  870   TYA

  880   STAstk%+2,X

  890   RTS

  900   .underflow

  910   LDA#estku%

  920   JMP(svct%)

  930   ]:NEXTo%

  940 PROCheader("?terminal")

  950 term%=P%

  960 FORo%=0TO3STEP3

  970   P%=term%

  980   [:OPTo%

  990   CPX#stktop%

 1000   BEQoverflow

 1010   DEX:DEX

 1020   STXsc%

 1030   LDA#&0F

 1040   LDX#&00

 1050   JSR&FFF4

 1060   LDA#&81

 1070   LDX#&8F

 1080   LDY#&FF

 1090   JSR&FFF4

 1100   LDXsc%

 1110   TYA

 1120   STAstk%+1,X

 1130   STAstk%+2,X

 1140   RTS

 1150   .overflow

 1160   LDA#estko%

 1170   JMP(svct%)

 1180   ]:NEXTo%

 1190 PROCheader("expect")

 1200 expect%=P%

 1210 FORo%=0TO3STEP3

 1220   P%=expect%

 1230   [:OPTo%

 1240   CPX#stkbot%-2

 1250   BCSunderflow

 1260   LDAstk%+3,X

 1270   STAsc%

 1280   LDAstk%+4,X

 1290   STAsc%+1

 1300   LDAstk%+1,X

 1310   STAsc%+2

 1320   LDA#&20

 1330   STAsc%+3

 1340   LDA#&8E

 1350   STAsc%+4

 1360   STXsc%+5

 1370   LDA#&00

 1380   LDX#sc%MOD&100

 1390   LDY#sc%DIV&100

 1400   JSR&FFF1

 1410   LDA#&00

 1420   STA(sc%),Y

 1430   INY

 1440   STA(sc%),Y

 1450   LDXsc%+5

 1460   INX:INX:INX:INX

 1470   BCCexpectend

 1480   LDA#&7E

 1490   STXsc%

 1500   JSR&FFF4

 1510   LDXsc%

 1520   .expectend

 1530   RTS

 1540   .underflow

 1550   LDA#estko%

 1560   JMP(svct%)

 1570   ]:NEXTo%

 1580 PROCheader("type")

 1590 type%=P%

 1600 FORo%=0TO3STEP3

 1610   P%=type%

 1620   [:OPTo%

 1630   CPX#stkbot%-2

 1640   BCSunderflow

 1650   LDAstk%+3,X

 1660   STAsc%

 1670   LDAstk%+4,X

 1680   STAsc%+1

 1690   LDAstk%+1,X

 1700   BEQendtype

 1710   STXsc%+2

 1720   TAX

 1730   LDY#uvout%

 1740   CLC

 1750   ADC(up%),Y

 1760   STA(up%),Y

 1770   INY

 1780   LDA(up%),Y

 1790   ADC#&00

 1800   STA(up%),Y

 1810   LDY#&00

 1820   .typeloop

 1830   LDA(sc%),Y

 1840   JSR&FFEE

 1850   INY

 1860   DEX

 1870   BNEtypeloop

 1880   LDXsc%+2

 1890   .endtype

 1900   INX:INX:INX:INX

 1910   RTS

 1920   .underflow

 1930   LDA#estku%

 1940   JMP(svct%)

 1950   ]:NEXTo%

 1960 PROCheader("count")

 1970 count%=P%

 1980 FORo%=0TO3STEP3

 1990   P%=count%

 2000   [:OPTo%

 2010   CPX#stkbot%

 2020   BEQunderflow

 2030   CPX#stktop%

 2040   BEQoverflow

 2050   DEX:DEX

 2060   LDA(stk%+3,X)

 2070   STAstk%+1,X

 2080   LDA#&00

 2090   STAstk%+2,X

 2100   INCstk%+3,X

 2110   BNEfinish

 2120   INCstk%+4,X

 2130   .finish

 2140   RTS

 2150   .overflow

 2160   LDA#estko%

 2170   JMP(svct%)

 2180   .underflow

 2190   LDA#estku%

 2200   JMP(svct%)

 2210   ]:NEXTo%

 2220 PROCheader("-trailing")

 2230 trail%=P%

 2240 FORo%=0TO3STEP3

 2250   P%=trail%

 2260   [:OPTo%

 2270   CPX#stkbot%-2

 2280   BCSunderflow

 2290   LDAstk%+3,X

 2300   STAsc%

 2310   LDAstk%+4,X

 2320   STAsc%+1

 2330   LDAstk%+1,X

 2340   TAY

 2350   .trailloop

 2360   DEY

 2370   BMItrailend

 2380   LDA(sc%),Y

 2390   CMP#&20

 2400   BEQtrailloop

 2410   .trailend

 2420   INY

 2430   TYA

 2440   STAstk%+1,X

 2450   RTS

 2460   .underflow

 2470   LDA#estku%

 2480   JMP(svct%)

 2490   ]:NEXTo%

 2500 PROCheader("id.")

 2510 id%=P%

 2520 FORo%=0TO3STEP3

 2530   P%=id%

 2540   [:OPTo%

 2550   CPX#stkbot%

 2560   BEQunderflow

 2570   STXsc%+2

 2580   CLC

 2590   LDAstk%+1,X

 2600   ADC#&01

 2610   STAsc%

 2620   LDAstk%+2,X

 2630   ADC#&00

 2640   STAsc%+1

 2650   LDY#&00

 2660   .idloop

 2670   LDA(sc%),Y

 2680   TAX

 2690   AND#&7F

 2700   JSR&FFEE

 2710   INY

 2720   TXA

 2730   AND#&80

 2740   BEQidloop

 2750   LDXsc%+2

 2760   LDA(stk%+1,X)

 2770   AND#&1F

 2780   BEQidend

 2790   STAsc%+2

 2800   CPYsc%+2

 2810   BEQidend

 2820   LDA#ASC(".")

 2830   JSR&FFEE

 2840   INY

 2850   .idend

 2860   CLC

 2870   TYA

 2880   LDY#uvout%

 2890   ADC(up%),Y

 2900   STA(up%),Y

 2910   INY

 2920   LDA(up%),Y

 2930   ADC#&00

 2940   STA(up%),Y

 2950   INX:INX

 2960   RTS

 2970   .underflow

 2980   LDA#estku%

 2990   JMP(svct%)

 3000   ]:NEXTo%

 3010 PROCheader("cr")

 3020 cr%=P%

 3030 FORo%=0TO3STEP3

 3040   P%=cr%

 3050   [:OPTo%

 3060   JSR&FFE7

 3070   LDY#uvout%

 3080   LDA#&00

 3090   STA(up%),Y

 3100   INY

 3110   STA(up%),Y

 3120   RTS

 3130   ]:NEXTo%

 3140 PROCheader("space")

 3150 space%=P%

 3160 FORo%=0TO3STEP3

 3170   P%=space%

 3180   [:OPTo%

 3190   LDA#&20

 3200   JSR&FFEE

 3210   LDY#uvout%

 3220   CLC

 3230   LDA(up%),Y

 3240   ADC #&01

 3250   STA(up%),Y

 3260   BCC endspace

 3270   INY

 3280   LDA(up%),Y

 3290   ADC #&00

 3300   STA(up%),Y

 3310   .endspace

 3320   RTS

 3330   ]:NEXTo%

 3340 PROCheader("(open)")

 3350 bopen%=P%

 3360 FORo%=0TO3STEP3

 3370   P%=bopen%

 3380   [:OPTo%

 3390   CPX#stkbot%-2

 3400   BCSunderflow

 3410   LDY#&00

 3420   STXsc%

 3430   LDA(stk%+3,X)

 3440   BEQopenend

 3450   CMP#&0B

 3460   BCCopenlen

 3470   LDA#&0A

 3480   .openlen

 3490   STAsc%+1

 3500   .openloop

 3510   INCstk%+3,X

 3520   BNEopenmove

 3530   INCstk%+4,X

 3540   .openmove

 3550   LDA(stk%+3,X)

 3560   STAsc%+2,Y

 3570   INY

 3580   DECsc%+1

 3590   BNEopenloop

 3600   .openend

 3610   LDA#&0D

 3620   STAsc%+2,Y

 3630   LDAstk%+1,X

 3640   LDX#sc%+2

 3650   LDY#&00

 3660   JSR&FFCE

 3670   LDXsc%

 3680   INX:INX

 3690   STAstk%+1,X

 3700   LDA#&00

 3710   STAstk%+2,X

 3720   RTS

 3730   .underflow

 3740   LDA#estku%

 3750   JMP(svct%)

 3760   ]:NEXTo%

 3770 PROCheader("close")

 3780 close%=P%

 3790 FORo%=0TO3STEP3

 3800   P%=close%

 3810   [:OPTo%

 3820   CPX#stkbot%

 3830   BEQunderflow

 3840   LDAstk%+1,X

 3850   TAY

 3860   LDA#&00

 3870   JSR&FFCE

 3880   INX:INX

 3890   RTS

 3900   .underflow

 3910   LDA#estku%

 3920   JMP(svct%)

 3930   ]:NEXTo%

 3940 PROCheader("osbget")

 3950 osbget%=P%

 3960 FORo%=0TO3STEP3

 3970   P%=osbget%

 3980   [:OPTo%

 3990   CPX#stkbot%

 4000   BEQunderflow

 4010   LDAstk%+1,X

 4020   TAY

 4030   JSR&FFD7

 4040   STAstk%+1,X

 4050   LDA#&00

 4060   STAstk%+2,X

 4070   RTS

 4080   .underflow

 4090   LDA#estku%

 4100   JMP(svct%)

 4110   ]:NEXTo%

 4120 PROCheader("osbput")

 4130 osbput%=P%

 4140 FORo%=0TO3STEP3

 4150   P%=osbput%

 4160   [:OPTo%

 4170   CPX#stkbot%-2

 4180   BCSunderflow

 4190   LDYstk%+3,X

 4200   LDAstk%+1,X

 4210   JSR&FFD4

 4220   INX:INX:INX:INX

 4230   RTS

 4240   .underflow

 4250   LDA#estku%

 4260   JMP(svct%)

 4270   ]:NEXTo%

 4280 PROCheader("osgbpb")

 4290 osgbpb%=P%

 4300 FORo%=0TO3STEP3

 4310   P%=osgbpb%

 4320   [:OPTo%

 4330   CPX#stkbot%-14

 4340   BCSunderflow

 4350   LDAstk%+3,X

 4360   STAsc%

 4370   LDAstk%+7,X

 4380   STAsc%+1

 4390   LDAstk%+8,X

 4400   STAsc%+2

 4410   LDAstk%+5,X

 4420   STAsc%+3

 4430   LDAstk%+6,X

 4440   STAsc%+4

 4450   LDAstk%+11,X

 4460   STAsc%+5

 4470   LDAstk%+12,X

 4480   STAsc%+6

 4490   LDAstk%+9,X

 4500   STAsc%+7

 4510   LDAstk%+10,X

 4520   STAsc%+8

 4530   LDAstk%+15,X

 4540   STAsc%+9

 4550   LDAstk%+16,X

 4560   STAsc%+10

 4570   LDAstk%+13,X

 4580   STAsc%+11

 4590   LDAstk%+14,X

 4600   STAsc%+12

 4610   STXsc%+13

 4620   LDAstk%+1,X

 4630   LDX#sc%

 4640   LDY#&00

 4650   JSR&FFD1

 4660   CLC

 4670   LDAsc%+13

 4680   ADC#16

 4690   TAX

 4700   RTS

 4710   .underflow

 4720   LDA#estku%

 4730   JMP(svct%)

 4740   ]:NEXTo%

 4750 PROCheader("osbyte")

 4760 osby%=P%

 4770 FORo%=0TO3STEP3

 4780   P%=osby%

 4790   [:OPTo%

 4800   CPX#stkbot%-2

 4810   BCSunderflow

 4820   STXsc%

 4830   LDAstk%+4,X

 4840   TAY

 4850   LDAstk%+3,X

 4860   STAsc%+1

 4870   LDAstk%+1,X

 4880   LDXsc%+1

 4890   JSR&FFF4

 4900   STXsc%+1

 4910   LDXsc%

 4920   STAstk%+1,X

 4930   TYA

 4940   STAstk%+4,X

 4950   LDAsc%+1

 4960   STAstk%+3,X

 4970   RTS

 4980   .underflow

 4990   LDA#estku%

 5000   JMP(svct%)

 5010   ]:NEXTo%

 5020 PROCheader("osword")

 5030 oswd%=P%

 5040 FORo%=0TO3STEP3

 5050   P%=oswd%

 5060   [:OPTo%

 5070   CPX#stkbot%-2

 5080   BCSunderflow

 5090   STXsc%

 5100   LDAstk%+4,X

 5110   TAY

 5120   LDAstk%+3,X

 5130   STAsc%+1

 5140   LDAstk%+1,X

 5150   LDXsc%+1

 5160   JSR&FFF1

 5170   STXsc%+1

 5180   LDXsc%

 5190   STAstk%+1,X

 5200   TYA

 5210   STAstk%+4,X

 5220   LDAsc%+1

 5230   STAstk%+3,X

 5240   RTS

 5250   .underflow

 5260   LDA#estku%

 5270   JMP(svct%)

 5280   ]:NEXTo%

 5290 PROCheader("oscli")

 5300 oscli%=P%

 5310 FORo%=0TO3STEP3

 5320   P%=oscli%

 5330   [:OPTo%

 5340   CPX#stkbot%

 5350   BEQunderflow

 5360   STXsc%

 5370   LDA(stk%+1,X)

 5380   CMP#&20

 5390   BCCoslen

 5400   LDA#&20

 5410   .oslen

 5420   STAsc%+1

 5430   LDY#&00

 5440   .osloop

 5450   INCstk%+1,X

 5460   BNEosmove

 5470   INCstk%+2,X

 5480   .osmove

 5490   LDA(stk%+1,X)

 5500   STAsc%+2,Y

 5510   INY

 5520   DECsc%+1

 5530   BNEosloop

 5540   LDA#&0D

 5550   STAsc%+2,Y

 5560   LDX#sc%+2

 5570   LDY#&00

 5580   JSR&FFF7

 5590   LDXsc%

 5600   INX:INX

 5610   RTS

 5620   .underflow

 5630   LDA#estku%

 5640   JMP(svct%)

 5650   ]:NEXTo%

 5660 PROCheader("?eof")

 5670 eof%=P%

 5680 FORo%=0TO3STEP3

 5690   P%=eof%

 5700   [:OPTo%

 5710   CPX#stkbot%

 5720   BEQunderflow

 5730   TXA:TAY

 5740   LDAstk%+1,X

 5750   TAX

 5760   LDA#&7F

 5770   JSR&FFF4

 5780   CPX#&00

 5790   BEQeoffalse

 5800   TYA:TAX

 5810   LDA#&FF

 5820   STAstk%+1,X

 5830   STAstk%+2,X

 5840   RTS

 5850   .eoffalse

 5860   TYA:TAX

 5870   LDA#&00

 5880   STAstk%+1,X

 5890   STAstk%+2,X

 5900   RTS

 5910   .underflow

 5920   LDA#estku%

 5930   JMP(svct%)

 5940   ]:NEXTo%

 5950 OSCLI("EXEC E.IO")

 5960 END

 5970 DEFPROCheader(name$)

 5980 PRINT:PRINT

 5990 PRINT"  *** ";~P%;" nfa '";name$;"'"

 6000 LETxhere%=P%

 6010 LETspan%=LEN(name$)

 6020 ?P%=span%

 6030 PROCsetbit(7,P%)

 6040 LETP%=P%+1

 6050 IFspan% > length%THENspan%=length%

 6060 FORi%=1TOspan%

 6070   ?P%=ASC(MID$(name$,i%,1))

 6080   LETP%=P%+1

 6090   NEXTi%

 6100 PRINT"  *** ";~P%;" lfa (";~last%;")"

 6110 PROCsetbit(7,P%-1)

 6120 PROCpoke(last%,P%)

 6130 LETP%=P%+2

 6140 LETlast%=xhere%

 6150 LETlabel%=label%+1

 6160 PRINT:PRINT

 6170 ENDPROC

 6180 DEFPROCsetbit(bit%,addr%)

 6190 ?addr%=?addr%OR(2^bit%)

 6200 ENDPROC

 6210 DEFPROCpoke(val%,addr%)

 6220 ?addr%=val%MOD256

 6230 ?(addr%+1)=val%DIV256

 6240 ENDPROC

 6250 DEFFNliteral(value%):[:OPTo%:JSRlit%:]:PROCpoke(value%,P%):P%=P%+2:=o%
