## WAVE file format
- **RIFF** format ("full format") 
	- hierarchical data format
	- composed of (nested) "chunks"
	- label (4 bytes) + size (4 bytes) + data (size bytes)
	- data portion of a chunk can contain other chunks
![[Pasted image 20260121150903.png]]
- **WAVE** file is a **RIFF** file with a specific format

```
+-[RIFF]---------------------------------+
| ["WAVE" - (wave tag - 4 bytes)       ] | \
|    |                                   |  \
| ["fmt "                              ] |   > header
| |       at least 16 bytes            | |  /
| [       about audio data format      ] | / 
|    |                                   |
| ["data"                              ] | \
| |       raw audio data !             | |  >  raw data
| [    interleaved 8/16 bit audio      ] | /
|    |                                   |
|    | (possibly more chunks v)          |
+----------------------------------------+
```

**simplified form:** no optional chunks; header + data.
```
Although there is a hierarchical structure to a WAVE file, it is more conve-
nient to view the structure as a header followed by the audio data. In this
point of view, and with Intel architecture, the header of the file consists of
the following C++ structure.

struct 
{
char riff_label[4]; // (00) = {’R’,’I’,’F’,’F’}
uint32_t riff_size; // (04) = 36 + data_size

char file_tag[4]; // (08) = {’W’,’A’,’V’,’E’}

char fmt_label[4]; // (12) = {’f’,’m’,’t’,’ ’}
uint32_t fmt_size; // (16) = 16
uint16_t audio_format; // (20) = 1
uint16_t channel_count; // (22) = 1 or 2
uint32_t sampling_rate; // (24) = (anything)
uint32_t bytes_per_second; // (28) = (see above)
uint16_t bytes_per_frame; // (32) = (see above)
uint16_t bits_per_sample; // (34) = 8 or 16

char data_label[4]; // (36) = {’d’,’a’,’t’,’a’}
uint32_t data_size; // (40) = # bytes of data
};
```

**"fmt"**
```
The data portion of the "fmt " chunk consists of a 16 byte data structure
containing the sampling rate, resolution, and other pertinent information. In
C++, the structure has the following form.

struct 
{
uint16 audio_format; // = 1                   UNCOMPRESSED
uint16 channel_count; // = 1 or 2             can be more than 2 in principle
uint32 sampling_rate; // = 8000, 44100, etc.
uint32 bytes_per_second; // = (see below)     \ redundant for us rn...
uint16 bytes_per_frame; // = (see below)      / used for compression
uint16 bits_per_sample; // = 8 or 16          bit resolution (others are supported)
};
```

