# ROM-0 exploit ZyXEL file reversing resources 

## Vulnerable URL
http://device.ip/rom-0

## ROM file description

### ROM file structure
- [0x00000000 - MEMORY BLOCK]
- [0x00002000 - FILE BLOCK]

#### Block structure
- BYTE     blocknumber
- BYTE     unknown
- WORD     nr of objects
- DWORD    blockLength
- foreach object:
   - CHAR[14] objectname
   - DWORD    uncompressed size
   - DWORD    compressed size
   - DWORD    offset to data from start of block

##### Compression algorithm
Lempel-Ziv-Stac (LZS)

##### File block
Contains "boot", "spt.dat" and "autoexec.net"

###### File spd.dat structure
- DWORD	Unclear (Load-addres?, Magic?, Endianness?)
- WORD	Major Version
- WORD	Minor version
- DWORD	Unclear (Chunks?)
- until EOF:
   - WORD		  org_size
   - WORD		  raw_size
   - BYTE[raw_size]  Compressed data
	
## Links
- [http://everlost.nl/kender/zyxel/source.zip](https://web.archive.org/web/20130113175043/http://everlost.nl/kender/zyxel/source.zip) working link from archive.org !
- http://www.hakim.ws/huawei/rom-0/kender.html
- http://www.ixo.de/info/zyxel_uclinux/
- http://blog.anidear.com/2014/01/hunting-for-zyxel-rom-0-file-decrypter.html
