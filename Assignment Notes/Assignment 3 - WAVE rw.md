**MIND THE** *Endian–ness*. 
WAVE files require that multi–byte values be stored in little–endian format. *(LSB first)*
```
the integer 1 in:

Little-Endian
 (LSB)             (MSB)
[ 0x1 | 0x0 | 0x0 | 0x0 ]

Big-Endian
 (MSB)             (LSB)
[ 0x0 | 0x0 | 0x0 | 0x1 ]
```

For this assignment, you are to assume that the code is being run on a machine that uses
little–endian architecture (most machines are). This means that you can use uint16 t for an
unsigned 16–bit integer stored in a WAVE file, and uint32 t for an unsigned 32–bit integer
stored in a WAVE file. 
If you want more of a programming challenge, write your code in
a way that is applicable to both little–endian and big–endian machines (again, this is not a
requirement of the assignment).

