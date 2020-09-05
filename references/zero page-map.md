```
Apple II Zero Page (by Andy McFadden; I don't remember the reference sources)

LOCATION   | USE DESCRIPTION
-----------+----------------------------------------------------------------+
$00 - $02  | Jump instructions for Applesoft soft entry (ctrl-C)
$03 - $05  | Jump instructions for Applesoft hard entry (ctrl-B)
$06 - $09  | Used for sweet-16 registers
$0A - $0C  | Holds location for USR function's jump
$0D - $1F  | Temporary Applesoft/DOS 3.3 locations
$20        | Left column of scroll window (def=$00)
$21        | Width of scroll window (def=$28)
$22        | Top line of scroll window (def=$00)
$23        | Bottom line of scroll window (def=$18)
$24        | Horizontal cursor displacement (from top)
$25        | Vertical cursor position (abs)
$26 - $27  | Hires byte position, lores left end point, DOS scratch
$28 - $29  | Pointer to current text line
$2A        | Used as scratch during scrolling; DOS scratch
$2B        | Boot slot X 16 (after boot)
$2C - $2F  | RWTS storage for checksum, sector, track, volume
$30        | Hires temporary bit mask; lores color value X 17
$31        | Used by monitor command processing
$32        | Video format control: $FF=norm, $7F=flash, $3F=inverse
$33        | Prompt character for input line
$34 - $35  | Used by monitor command processing to save Y-reg
$36 - $37  | Character output pointer
$38 - $39  | Character input pointer
$3A - $3B  | Save area for program counter; set by L)ist and G)oto
$3C - $3D  | General use by monitor; source pointer for memory move
$3E - $3F  | General use by monitor
$40 - $47  | General scratch for DOS
$48 - $49  | RWTS IOB block pointer
$4A - $4B  | LOMEM address (INT)
$4C - $4D  | HIMEM address (INT)
$4E - $4F  | Random number field (seeded by RDKEY)
$50 - $53  | 32-bit accumulator for use with Applesoft mult & divide
$54 - $61  | Applesoft scratch locations
$62 - $66  | Result of last multiply/divide
$67 - $68  | Start of program address (Applesoft)
$69 - $6A  | Start of variable space address (Applesoft)
$6B - $6C  | Start of array space address (Applesoft)
$6D - $6E  | End of numeric storage address (Applesoft)
$6F - $70  | Start of string storage address (Applesoft)
$71 - $72  | Temporary pointer (string storage routines - Applesoft)
$73 - $74  | HIMEM address (Applesoft)
$75 - $76  | Line number being executed (Applesoft)
$77 - $78  | Line where program stopped (Applesoft)
$79 - $7A  | Line being executed (Applesoft)
$7B - $7C  | Line where DATA is being read (Applesoft)
$7D - $7E  | Pointer to absolute memory location where DATA is (App)
$7F - $80  | Pointer to source of input ($201 for INPUT statement)
$81 - $82  | Last used variable name (Applesoft)
$83 - $84  | Last used variable address
$85 - $9C  | General Applesoft usage
$9D - $A3  | Main floating point accumulator
$A4        | General use in Applesoft math routines
$A5 - $AB  | Secondary floating point accumulator
$AC - $AE  | General use Applesoft flags & pointers
$AF - $B0  | Pointer to end of Applesoft program
$B1 - $C8  | CHRGET routine: Applesoft calls whenever needs char
$C9        | Applesoft scratch
$CA - $CB  | APRND random number; start of program address (INT)
$CC - $CD  | End of variable storage (INT)
$CE - $CF  | Math accumulator (INT)
$D0 - $D5  | Applesoft hires scratch
$D6        | Applesoft RUN flag (auto-run if >$80)
$D7        | Scratch flag for Integer
$D8        | Applesoft ONERR flag (active if >$80)
$D9        | Used by DOS to test for Applesoft Def/Imm mode
$DA - $DB  | Line number where ONERR error occured
$DC - $DD  | TXTPTR save location for HNDLERR routine
$DE        | ONERR error code
$DF        | Applesoft stack pointer before error occured
$E0 - $E1  | X-coordinate of last HPLOT
$E2        | Y-coordinate of last HPLOT
$E4        | HCOLOR value
$E5        | Hires map byte for horizontal bit position
$E6        | Hires plotting page
$E7        | Scale value
$E8 - $E9  | Start of shape table address
$EA        | Hires collision counter
$EB - $EF  | Totally, completely, unreasoningly unused
$F0        | Applesoft lores scratch pointer
$F1        | 256 minus SPEED value
$F2        | Applesoft trace flag
$F3        | FLASH mask ($40=flash, with $32 set to $7F)
$F4 - $F8  | Applesoft ONERR pointers
$F9        | Applesoft shape table ROT value
$FA - $FE  | Applesoft math temporary storage
$FF        | Unused (Integer scratch?)
-----------+----------------------------------------------------------------+
```
