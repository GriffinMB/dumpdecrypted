Dumps decrypted iOS Applications to a file - better solution than those GDB scripts for non working GDB versions.

(C) Copyright 2011-2014 Stefan Esser

_Includes modifications from conradev and ericcastro. In particular, is able to dump encrypted frameworks._


## Compile

First adjust the Makefile if you have a different iOS SDK installed.

And then just: 

```
make
```

## Usage:

```
# chmod a+rx dumpdecrypted.dylib
# cp dumpdecrypted.dylib /usr/lib/
# su mobile

$ cd /var/mobile/Documents
$ DYLD_INSERT_LIBRARIES=(usr/lib/dumpdecrypted.dylib /var/containers/Bundle/Application/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/YYYY.app/YYYY


[+] Dumping YYYY
[+] detected 64bit ARM binary in memory.
[+] offset to cryptid found: @0x100018c08(from 0x100018000) = c08
[+] Found encrypted data at address 00004000 of length 720896 bytes - type 1.
[+] Opening /private/var/containers/Bundle/Application/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/YYYY.app/YYYY for reading.
[+] Reading header
[+] Detecting header type
[+] Executable is a plain MACH-O image
[+] Opening YYYY.decrypted for writing.
[+] Copying the not encrypted start of the file
[+] Dumping the decrypted data into the file
[+] Copying the not encrypted remainder of the file
[+] Setting the LC_ENCRYPTION_INFO->cryptid to 0 at offset c08
[+] Closing original file
[+] Closing dump file

```
