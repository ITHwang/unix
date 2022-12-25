## 1. count content: `wc`

- definition: word count
- options
	- -c: the number of bytes
	- -m: the number of characters
	- -C: same as -m
	- -l: the number of rows
	- -w: the number of words separated by white space.

> In English, one character consists of **one byte**, hence the number of bytes and the number of characters are **the same**.
> 
> In Korean, however, one character consists of **two bytes**, hence the number of bytes and the number of characters are **different**.

## 2. sort content: `sort`

- options:
	- -k: assign **the field number** by which rows are sorted.
	- +(num): assign <u>(num + 1) to the field number</u> by which rows are sorted.
	- +(num1) -(num2): assign <u>(num1+1 ~ num2) to the field numbers</u> by which rows are sorted.
	- -n: switch numbers in the type of string to ones <u>in the type of number.</u>
	- -r: reverse
	- -o (file): save the result as the file.
	- -t (char): field separator

## 3. split content: `split`

- options
	- -b (num): split the file by (num) bytes.
	- -(num): split the file by (num) rows.

## 4. delete duplication: `uniq`

- options
	- -c: print duplicate count.
	- -d: print duplicat rows.(one per row)
	- -u: print not duplicat rows.

> Note that `uniq` checks duplicate rows not in the whole file but in adjacent rows.
> 
> Hence, for removal of duplicate rows in the whole, connect `uniq` to `sort` through the pipe.
```bash
sort (file) | uniq
```

## 5. cut off field: `cut`

- description: extract selected fields in each row.(**A field** is a column separated by tab in each row.)
- options
	- -c (start idx)-(end idx): slice row from start idx to end idx(included, first idx is 1) 
	- -f (field nums): cut off the field.(multiple nums separated by comma is possible.)

## 6. concatenate files: `paste`

- description: concatenate two files **horizontally**(axis=1).
- options
	- -d (char): field separator
	- -s: concatenate all rows in the file **horizontally**.(change newline character to tab.)

## 7. file dump: `dd`

- definition: data duplicate
- description: transform input file into output file.(ex. lower to upper, etc.)

### 7.1. delete all in the file
```bash
dd if=/dev/null of={target file}
```