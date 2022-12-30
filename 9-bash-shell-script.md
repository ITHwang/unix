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
1. single quote escapes all metacharacters($, \*, ?, etc.)
2. double quote permits replacement of variable or command and escapes other metacharacters.
3. backslash escapes only one metacharacter.

### 1.5. command substitution
- use backtick or `$(command)`.

## 2. Handling user input
