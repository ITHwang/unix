## 1. count content: `wc`
- definition: word count
- options
	- -c: the number of bytes
	- -m: the number of characters
	- -C: same as -m
	- -l: the number of rows
	- -w: the number of words separated by white space.

> In English, one character consists of one byte, hence the number of bytes and the number of characters are the same.
> 
> In Korean, however, one character consists of two bytes, hence the number of bytes and the number of characters are different.

## 2. sort content: `sort`
- options:
	- -k: assigns the field number by which rows are sorted.
	- +(num): assigns (num + 1) to the field number by which rows are sorted.
	- +(num1) -(num2): assigns (num1+1 ~ num2) to the field numbers by which rows are sorted.
	- -n: switches numbers in the type of string to ones in the type of number.
	- -r: reverse
	- -o (file): saves the result as the file.
	- -t (char): field separator

## 3. split content: `split`
- options
	- -b (num): splits the file by (num) bytes.
	- -(num): splits the file by (num) rows.
	- 

