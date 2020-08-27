# BAM Code Walkthrough

``` basic
> CATALOG

DISK VOLUME 254

  I 023 BENEATH APPLE MANOR
  B 005 BAMSUB
  I 003 HELLO
  I 047 BAM1
  I 068 BAM >=32K
  T 002 TEST
```

## HELLO
``` basic
   10  DIM A$(1):A$=""
   15  PRINT A$;"NOMON C"
   20  TEXT : CALL -936
   30  PRINT "****************************************";
   35  PRINT "*                                      *";
   40  PRINT "*  B E N E A T H  A P P L E  M A N O R *";
   45  PRINT "*                                      *";
   46  PRINT "*    DISKETTE VERSION 1.1 - 7/30/79    *";
   47  PRINT "*                                      *";
   50  PRINT "****************************************";
   55  PRINT 
   60  PRINT A$;"CHAIN BENEATH APPLE MANOR"
  100  END 
```
