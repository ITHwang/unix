## 1. Metacharacters
- ?: one random character
- \[\]: one character in the square bracket
- cd -: change the directory which you worked before using last 'cd'.
- ;: execute orderly arranged commands divided by semicolon.
- \`\`(back quote): replace the string in the back quote with the result of the string.

## 2. stdin & stdout & stderr
| file descriptor |  name  | symbol |
|:---------------:|:------:|:------:|
|        0        | stdin  |   <    |
|        1        | stdout | >, >>  |
|        2        | stderr |   2>   |
- CMD > FILE: overwrite FILE with stdout
- `set -o noclobber` for preventing from overwriting  
- `set +o noclobber` for release `set -o noclobber`
- cat > FILE: save stdout to FILE
- CMD >> FILE: append stdout to FILE 
- CMD 2> FILE: overwrite stderr to FILE
- CMD > FILE1 2> FILE2: the execution of CMD is success, stdout is saved in FILE1, else stderr is saved in FILE2.
- If you don't want to save stderr, replace stderr file with `/dev/null`.
- `/dev/null` is like trash bin, but unlike trash bin, nothing is left there. 
- CMD < FILE: read the content of FILE and execute CMD with it.

## 3. Environment Setting
- Shell variable can be used only in the shell in which the variable are defined.(can't be used in subshell)
- Environment variable can be used in a subshell as well as the shell by which the subshell inherited.
- set: print shell variables and environment variables.
- env: print only environment variables.
- export: change a shell variable to a env variable.
- unset: release assigned variable.

## 4. Handling Bash Command
- `set -o vi` help you modify previous command using vim.

## 5. Environment Setting File(Bash)
- Environment Setting File: the file in which commands are saved that are automatically executed whenever user logins.
- `/etc/profile`: **System Wide User Profiles** that contain Linux system wide environment and other startup scripts.
- `~/.bash_profile`, `~/.profile`, `~/.bashrc`: **Bash Startup Files** that contain commands that are to be executed on shell startup.
- Actually, `~/.bash_profile` is equal to `~/.profile`, and bash shell takes `~/.bash_profile` as a priority.
- whereas `~/.bash_profile` or `~/.profile` is executed only when user logins, `~/.bashrc` is executed only when subshell is executed.
- Threrefore, if you want to work always in the same environment, you should put all variables into `~/.bashrc` and execute the file in `~/.bash_profile`.