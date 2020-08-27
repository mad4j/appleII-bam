# Apple II DOS Mini-Manual

## References 
 * [Jeff Hurlburt DOS Mini-Manual](https://apple2.org.za/gswv/a2zine/GS.WorldView/Resources/ARTICLES/DOS.MiniManual.html)

Mainly, this mini-manual covers DOS 3.3. There is a short 'intro' section on
ProDOS at the end.


## DOS

**DOS** means **Disk Operating System**. A DOS is a collection of machine language
routines and data which lets a computer Read and Write information to/from disk.
Apple II DOS, Commodore 64 DOS, and the DOS used on PC's are all called "DOS";
but, they are different systems.

DOS 3.3 is the first DOS to be widely used on Apple II computers. Many programs
were written to use DOS 3.3 commands and saved on DOS 3.3 diskettes. Apple
'officially' replaced DOS 3.3 with ProDOS back in the early '80's. However, DOS
3.3 continues to be popular with II users.


DOS 3.3 Versions:

Today, most "DOS 3.3 users" do not actually use DOS 3.3. Long ago, Beagle Bros
introduced patches which resulted in much better speed, freed-up extra disk
space, and added a CATALOG command which shows number of Free Sectors. Their
ProntoDOS or some modification of it is, for practical purposes, the "current
version" of DOS 3.3.

ES DOS ][ adds a few mods to ProntoDOS: CATALOG shows Free Sectors and Number of
Tracks, default is to scroll entire Catalog (scrolling stopped by pressing any
key), and the semi-colon can be used as a terminating 'wildcard' character.

There are also several small, special-purpose versions of DOS 3.3. For example,
one game maker used RDOS to save space and to make its diskettes harder to copy.


DOS Commands

To get very far with "DOS 3.3" you will need the DOS Manual. This is especially
true when it comes to using TEXT files. Other good sources of DOS 3.3 info
include _Beneath Apple DOS_ and _Apple II User's Guide_. For now, the following
is a quickie guide to most Apple II DOS 3.3 commands:


LOAD NARF- loads a BASIC file named NARF.

SAVE NARF- saves current BASIC program in memory as file named NARF.

DELETE NARF - deletes file named NARF

CATALOG - lists contents of diskette to screen

RENAME NARF, NEWNARF - renames file NARF to NEWNARF

RUN NARF- loads and starts a BASIC file named NARF.

BLOAD NARF.PICTURE, A$2000 - loads in a binary file named NARF.PICTURE starting
at address $2000.

>>note: $2000 is a hexadecimal number ($2000 = 8192 in decimal). DOS commands
can use hex or decimal numbers.


BSAVE NARF, A$300, L$7F - saves $7F bytes of memory starting at address $300 as a
binary file named NARF. (BSAVE NARF, A768, L127 uses decimal numbers to do the
same thing.)

>>note: The above command statement illustrates typical DOS syntax ...

BSAVE-- the DOS command

NARF-- the file name (the space between the command and file name is not a
requirement; BSAVENARF is okay)

,-- a comma to separate file name from parms which follow

A-- means an Address follows

$300-- the address in hex from which you want to start saving bytes (= 768).
Again, spaces do not matter; A768, A 768, A $ 300 are all okay

,-- a comma to separate one parm from another

L-- means a Length follows

$7F-- the length in hex (= 127); this is the number of bytes to be saved

The command statement says Save $7F bytes, starting at address $300, to a file
named "NARF". NARF will have the bytes found at addresses $300 through $37E.


>>note: The order of parms following a file name does not matter.


BRUN NARF.DISP, A$1000 - loads in a binary file named NARF.DISP starting at
address $1000 and starts executing machine instructions at address $1000

LOCK NARF- locks file NARF (indicated by * in a CATALOG). LOCKed files cannot be
deleted, over-written, etc.

UNLOCK NARF - cancels LOCKed status of NARF.

VERIFY NARF - uses checksums to verify that NARF is not a damaged file

MON C, I, O - tells DOS to display Commands, Inputs from disk, Outputs to disk.
You can specify one, two, or all three (e.g. MON C, O etc.).

NOMON C, I, O - cancels all MON requests. NOMON I cancels just the "I" request.

MAXFILES 7 - sets the number of file buffers to 7. (Upon booting DOS, the default
for the MAXFILES value is 3.)

PR#1 - sets the destination for Apple outputs to the device in Slot 1 (usually a
printer). PR# 3 sets it to Slot 3, etc.. PR# 0 sets the destination back to the
display screen.
PR#6 - normally, boots the diskette in Drive 1, Slot 6.

IN# 6 - sets the source for Apple inputs to the device in Slot 6. IN# 0 - sets
the source for Apple inputs to the keyboard (default).

INT - (integer) puts system into Integer BASIC if it is present.

FP - (floating point) puts system into standard Applesoft BASIC.

OPEN NARFOO - prepares to read or write a TEXT file named NARFOO.

READ NARFOO - tells DOS that INPUT and GET statements will obtain characters from
a TEXT file named NARFOO.

WRITE NARFOO - tells DOS that PRINTed characters will go to a TEXT file named
NARFOO.

CLOSE NARFOO - used to terminate access to a TEXT file named NARFOO. Just CLOSE
terminates access to all OPENed TEXT files.

EXEC NARFGO - tells DOS to execute the BASIC and DOS commands found in a TEXT
file named NARFGO

The above TEXT file commands handle 'normal' sequential TEXT files. DOS can also
OPEN, READ, WRITE, ... random access TEXT files. (See DOS manual.)


Most DOS commands also let you specify Drive and/or Slot. For example CATALOG, D2
lists the contents of the diskette in Drive 2 to screen. SAVE NARF,S5,D2 saves
NARF to Drive 2 in Slot 5.

NOTE --> Using Drive or Slot parms in a DOS command sets the default Drive or
Slot. So, after CATALOG, D2, a plain LOAD or SAVE will access Drive 2.


To use a DOS command from the keyboard, type it in. (A few commands can be issued
only from a program.) To use a DOS command in a program enclose it in quotes
preceded by PRINT CHR$(4). For example:

100 PRINT CHR$(4) "BLOAD NARF, A$2000"

Use variables in a command this way:

120 PRINT CHR$(4) "BSAVE NARF, A$2000, L"; NB

Line 120 says that the Length of NARF is the value of variable NB. NB is used
here to represent the number of bytes, a decimal number.


One of the best features of DOS 3.3 is that any bootable DOS diskette can create
other bootable diskettes.

INIT HELLO - formats the diskette in the currently active drive, adds DOS, and
saves the current program as HELLO.

The program that's automatically placed on the new diskette is the one in memory
when INIT is executed. The "hello program" is run when the diskette is booted.
Usually, the program is named HELLO; but, you can INIT HOWDY, or any name you
like. The program can be very simple, such as ...

100 PRINT CHR$(4) "CATALOG"
110 END

Each DOS 3.3 diskette has a Volume Number set at the time it is initialized. The
default Volume Number used by INIT is 254. You can set the number to something
else at the time a diskette is initialized:

INIT HELLO, V19

Several DOS commands can specify Volume--

LOAD NARF, D2, V5 ...

However, few DOS programs use Volume Number information. Unless an application
needs to employ Volume Numbers, it is best to stay with the default value (254)
to avoid unnecessary complications.

Here are a few DOS terms that will help explain what's going on:

FORMAT means to write 35 empty Tracks of 16 256-byte sectors each, verify the
Tracks and create a "Contents" record called the "VTOC". The VTOC has such basic
information as Number of Tracks, Sectors per Track, DOS version, ..., and the
'map' of used/un-used sectors. DOS 3.3 writes the VTOC at Track 17, Sector 0.
FORMAT does not put a copy of DOS 3.3 on the diskette.

INIT HELLO means to FORMAT a diskette; AND, to Copy DOS to the diskette, mark-off
the sectors used, AND Save the current program under the name HELLO. The version
of DOS written to the diskette will be the one operating when INIT is executed.

The current program-- i.e. whatever BASIC program is in memory when you do the
INIT-- is the one which DOS will execute when the INITed diskette is booted. It
is called the "greeting program" or "hello program" and is usually named "HELLO".

You are free to load in and change the hello program or even delete it, just like
any other. The one restriction is that once a diskette is INITed, the name of the
hello program is fixed for that diskette unless you use a utility (like Copy II+)
to make a change. This is why it's a good idea to stick with the name HELLO. You
will always know what the hello program's name is.

Again, when INIT-ing a DOS 3.3 diskette, it is almost always best to avoid
specifying a Volume number. The default, 254, is fine. Differences in Volume
numbers can cause all sorts of problems.

BOOT comes from the idea of 'pulling yourself up by your bootstraps'. The Apple
II disk controller ROM has just enough smarts to load-in DOS's Bootstrap Loader
from Track 0, Sector 0 (it comes in at address $800 ...). The Loader loads in a
still smarter, bigger routine from several sectors of Track 0. This routine is
the one which loads in the rest of DOS, moves it to the proper place in memory,
and ends up going to DOS's Cold Start routine.

When it comes to the way it is stored on-disk, DOS 3.3 is not like the PC's MSDOS
or Apple's ProDOS. DOS 3.3 is 'hidden' on reserved tracks. There is no "DOS 3.3"
file. If a DOS 3.3 diskette boots, DOS 3.3 is present.


Below is some useful 'nuts-and bolts' information:

In a DOS 3.3 Catalog sector, the third byte in each file's entry tells the type
of the file:

Byte Contents* File Type
00 Text
01 Integer BASIC
02 AppleSoft BASIC
04 Binary
08 S type
10 R: Relocatable object module
20 new A type
40 new B type


*DOS sets bit 7 of the byte if the file is locked. (e.g. 84 --> a locked Binary
file)

Type R files show up in just a few applications. An R file begins with 6 bytes
which a "loader" routine can use to tell Target location of file contents, How
many bytes to move, and Source location to move from.

Although S, new A, and new B are included, no official application was defined
for them and no DOS commands were created to make any special use of these files.
_______

There was an "R" type relocating loader included with the toolkit for use with
BASIC programs and relocatable routines being loaded into upper memory.

"S" was used by some programs for a generic image file, or something that was not
likely to be touchable with normal code.

The LISA assembler used the second "B" type for its source files. It had a
patched version of DOS that changed the file type list to read "LARSBAIT", so the
source files appeared in the catalog as "L" if you booted LISA, or "B" if you
booted a normal disk.

The "B", "A", "R" and "S" special file types cannot be accessed by BASIC programs
(unless you patch DOS) - commands are only provided for dealing with "B", "A",
"I" and "T" files.

The four special types can only be accessed using direct calls to the File
Manager. -- David Empson
_______

DOS 3.3 file structure is not heirarchial-- there are no subdirectories or
"folders". There are eight filetypes, of which B, A, I, and T are the most
common. A DOS 3.3 Catalog display looks something like this:

DISK VOLUME 254
*A 002 THE LAST FILE
B 033 TETRA/SOFT LOGO
T 142 DAVE'S LIST OF DOS COMMANDS
I 002 INTEGER BASIC PROGRAM
^^ ^^^ ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
|| ||| ||||||||||||||||||||||||||||||
|| ||| |______________________________Filename ||
|__________________________________File length (MOD 256)
||____________________________________File type
|_____________________________________* means the file is locked


A NOTE ABOUT DOS 3.3 FILENAMES:
DOS 3.3 filenames may be up to 30 characters long, and must conform to the
following restrictions:
a. The first character must have an ASCII code greater than 63 ("@") b. Commas
and colons may not be used.
Apart from that, anything goes, including uppercase, lowercase, numbers, symbols,
and CONTROL characters.

All file commands (including CATALOG and INIT) have optional switches available:

,Sn Specifies disk controller slot number n, usually 6. Default is
the most recently accessed slot.

,Dn Specifies which drive on the controller. Unless patched, DOS 3.3
only knows about D1 and D2.

,Vn Seldom used; specifies a disk volume number. Most disks are V254, and
the default is V0, which matches any disk. --Dave Althoff, Jr. _________

ProDOS

ProDOS is the official Apple ][ DOS which came after DOS 3.3. Do not confuse
"ProDOS" and "ProntoDOS". ProntoDOS is a slightly modified DOS 3.3 which provides
much faster disk I/O than standard DOS 3.3. ProDOS is a whole new disk operating
system.

ProDOS has lots of nice features-- mainly, you can create sub-directories,
diskettes ("volumes") can be named, and ProDOS works well on hard disks. The GS
System 6 Finder can handle ProDOS files and launch programs from ProDOS
diskettes. ProDOS shares many commands with DOS 3.3, too; so, it is not difficult
for DOS 3.3 users to get started with the newer operating system.

All Apple II's, from the 64k Apple II+ through the IIgs, can run versions of
ProDOS up through version 1.9. Versions 2.x.x require a 128k Apple IIe, IIc, or
IIgs.

Creating bootable ProDOS diskettes is a bit more bother because, unlike DOS 3.3,
ProDOS is not automatically written to protected sectors on the diskette via an
INIT command. (ProDOS does not have an INIT command.)
Instead, ProDOS is in a file on the diskette and so is the ProDOS 'connection' to
BASIC, called BASIC.SYSTEM.

To make new bootable ProDOS diskettes, the easiest approach is to use Disk
Muncher or some other whole-disk copier to just copy a bootable ProDOS diskette.
You can delete the files you don't want from the copy.

Another option is to use Copy II+ (ProDOS version) to FORMAT a ProDOS diskette.
(FORMAT writes blank tracks so that the diskette can be used to hold files.)
Then, copy BASIC.SYSTEM and PRODOS to the new diskette. On a IIgs, all of these
operations are easily handled via the Finder.

If you want ProDOS to boot and start a BASIC program, then both PRODOS and
BASIC.SYSTEM must be present. (BASIC.SYSTEM should be the first .SYSTEM file on
the diskette.) The "hello" program on a ProDOS diskette is named "STARTUP". This
is the program which will be run upon booting the diskette.
