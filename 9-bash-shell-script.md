## 1. Variable

### 1.1. variable substitution
- `${name}`: expand to the string value.
- `${name:-string}`: if `$name` is not declarated, replace `$name` with `string`.
- `${name:=string}`: if `$name` is not declarated or null, replace `$name` with `string`, assigning `string` to `$name`.

### 1.2. string handling
- `${variable%pattern}`: remove the smallest substring which matches `pattern` from behind.
- `${variable#pattern}`: remove the smallest substring which matches `pattern` from the front.
- `${#variable}`: the length of `$variable`

### 1.3. positional parameter
- `$0`: the name of the current script
- `$1 - $9`: no.1 ~ no.9 positional parameters
- `$#`: total number of parameters
- `$*` | `$@`: all parameters

### 1.4. quote symbols
1. **single quote** escapes all metacharacters($, \*, ?, etc.)
2. **double quote** permits replacement of variable or command and escapes other metacharacters.
3. **backslash** escapes only one metacharacter.

### 1.5. command substitution
- use backtick or `$(command)`.

## 2. Handling user input
- `read (x)`: declare user input `x` as a variable.
- `read -p (message)`: print `message` and assign user input to the variable `REPLY`.

## 3. Operator
- statement with operators
	- ex1. `let x=3*5`
	- ex2. `let "a = 20"`
	- ex3. `(( a = 30 ))`
- expression with operators
	- ex1. `let 3*5`
	- ex2. `(( y < 4 && z > 73 ))`

## 4. Conditional Statements

### 4.1. `if` expression
```bash
read ans

if [[ $ans = [Yy]* ]]
then
	echo "Happy to hear it."
else
	echo "That's too bad."
fi
```

### 4.2. `case` expression
```bash
read cmd

case $cmd in
	[0-9])
		date
		;;
	cd|CD)
		echo $HOME
		;;
	[aA-C]*)
		pwd
		;;
	*)
		echo "Usage: select command"
		;;
esac
```

## 5. Loop

### 5.1. `for` loop
```bash
for x in a b c
do
	echo $x
done
```

### 5.2. `while` loop
```bash
while (( $i < 3 ))
do
	let i+=1
	echo $i
done
```

### 5.3. `until` loop
```bash
until (( $i >= 3 ))
do
	let i+=1
	echo $i
done
```

### 5.4. `select`
- description: the loop creating menu.
```bash
select x in a b c
do
	case $x in
		a|b|c)
			echo $x
			;;
		*)
			break
			;;
	esac
done
```

## 6. Function
- definition
```bash
function add {
	typeset sum # local variable

	(( sum = $1 + $2 ))
	
	return $sum
}
```
- removal
```bash
unset -f add
```

## 7. Debugging
- `bash -x {script}`: execute and print line by line.
- `trap {command} DEBUG`: execute the `command` every time running line by line.