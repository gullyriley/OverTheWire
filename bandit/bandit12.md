\# Bandit Level 12 → Level 13



\## Objective

Recover the password from `data.txt`, which contains a hexdump of a file that has been repeatedly compressed.



---



\## Given Information

\- Logged in as user `bandit12`

\- `data.txt` is a hexdump of a file

\- The file has been compressed multiple times using different formats

\- A temporary working directory should be created under `/tmp`



---



\## Approach



First, a temporary working directory was created:



```bash

mktemp -d

cd /tmp/<generated\_directory>

```



The original file was copied into the workspace:



```bash

cp ~/data.txt .

```



Since the file was a hexdump, it needed to be reversed back into binary form:



```bash

xxd -r data.txt file.bin

```



The file type was identified:



```bash

file file.bin

```



This revealed it was gzip compressed data.



Because gzip requires the proper suffix, the file was renamed and decompressed:



```bash

mv file.bin file.gz

gzip -d file.gz

```



After decompression, the file type was checked again:



```bash

file file

```



This revealed bzip2 compressed data.



The process was repeated:



```bash

mv file file.bz2

bzip2 -d file.bz2

file file

```



The output indicated gzip compression again. The file was renamed and decompressed:



```bash

mv file file.gz

gzip -d file.gz

file file

```



This revealed a POSIX tar archive.



The archive was extracted:



```bash

mv file file.tar

tar -xf file.tar

```



A new file appeared and the identification/decompression cycle continued:



```bash

file data5.bin

mv data5.bin data5.tar

tar -xf data5.tar



file data6.bin

mv data6.bin data6.bz2

bzip2 -d data6.bz2



file data6

mv data6 data6.tar

tar -xf data6.tar



file data8.bin

mv data8.bin data8.gz

gzip -d data8.gz

```



Finally, the file type was identified as ASCII text:



```bash

file data8

cat data8

```



---



\## Solution



The final extracted file contained readable text revealing the password for the next level.



---



\## Key Takeaways



\- `xxd -r` reverses a hexdump back into binary form

\- The `file` command is essential for identifying unknown file types

\- Compression formats may require proper file extensions before decompression

\- Layered compression requires iterative identification and extraction

\- Creating a temporary workspace prevents accidental modification of original files



