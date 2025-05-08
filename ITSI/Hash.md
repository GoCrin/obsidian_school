hash-only-1 in picoctf

ls -> flaghasher
file flaghasher -> **setuid** ELF 64-bit ...
ls -l -> -rwsr-xr-x flaghasher
./flaghasher
schreibt irgendwas in /root/

strings flaghasher