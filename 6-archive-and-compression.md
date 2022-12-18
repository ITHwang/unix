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
- notes
	1. paths of files in the archive
		- When `tar` creates a archive, it also saves path of each file in it.
		- These paths of files are used to extract the tar file.
		- Hence it would be desirable to check out paths of files in archive by `tar tvf`.
	2. file permissions
		- to be continue..






