## 1. Overview
- archive: tying multiple files into one file.
- extensions
| ext  |        create         |      extract      |      view      |        update         | compression | leave the origin | dir |
|:----:|:---------------------:|:-----------------:|:--------------:|:---------------------:|:-----------:|:----------------:|:---:|
| .tar | tar cvf (.tar) (tgts) |  tar xvf (.tar)   | tar tvf (.tar) | tar uvf (.tar) (tgts) |     no      |       yes        | yes |
| .jar | jar cvf (.jar) (tgts) |  jar xvf (.jar)   | jar tvf (.jar) | jar uvf (.jar) (tgts) |     yes     |       yes        | yes |
|  .Z  |    compress (tgts)    | uncompress (tgts) |   zcat (.Z)    |           -           |     yes     |        no        | no  |
| .gz  |      gzip (tgts)      |   gunzip (.gz)    |  gzcat (.gz)   |           -           |     yes     |        no        | no  |
| .zip |   zip (.zip) (tgts)   |   unzip (.zip)    |       -        |           -           |     yes     |       yes        | yes |
| .bz2 |     bzip2 (tgts)      |  bunzip2 (.bz2)   |  bzcat (.bz2)  |           -           |     yes     |        no        | no  |

## 2. tar
- Definition: tape archive

### 2.1. create: `tar cvf`
- options
	- c: create
	- v: verbose
	- f: file, assigns created archive name.
	
### 2.2. extract: `tar xvf`
- options
	- x: extract

> notes
> 1. paths of files in the archive
>> - When `tar` creates a archive, it also saves path of each file in it.
>> - These paths of files are used to extract the tar file.
>> - Hence it would be desirable to check out paths of files in archive by `tar tvf`.
> 2. file permissions
>> - The permission of extracted file is depending on **default umask**.
>> - If the original permission should be maintained, use `p` option.

### 2.3. view: `tar tvf`
- options
	- t: table of contents
- columns
	1. the type of the file
	2. the file permission
	3. UID/GID
	4. file size
	5. last modified date
	6. file name

### 2.4. update: `tar uvf`
- options
	- u: update
- adds a file to the tar file
- 'cause the files of the archive are extracted in order from top to bottom, <u>the last file overwrites the first file.</u>

> rvf
>> r: replace
>> uvf checks if the same file already exists in the archive, whereas rvf adds a file to the archive unconditionally.

## 3. jar
- Definition: Java ARchive tool

### 3.1. create & compress: `jar cvf`
- options: same as `tar`.
- only create: `jar c0vf`

### 3.2. extract: `jar xvf`
- options: same as `tar`.

> note: when extracts the symbolic file
>> tar xvf: extract the symbolic file.(-h: extracts the origin file.)
>> jar xvf: extract not the symbolic file but the origin file.

### 3.3. view: `jar tvf`
- options: same as `tar`.
- `META-INF/MANIFEST.MF`: management and authentication info

### 3.4. update: `jar uvf`
- options: same as `tar`.
- Unlike `tar uvf` which adds updated file to the archive, `jar uvf` substitutes the origin file with the updated file.