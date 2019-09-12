In the shell command language, a token that performs a redirection function. It is one of the following symbols:

1. `<`
2. `<>`
3. `>`
4. `>|`
5. `>>`
6. `>&`
7. `<<`
8. `<<<`

These allow you to control the input and output of your commands. They can appear anywhere within a simple command or may follow a command. Redirections are processed in the order they appear, from left to right.

1. `<`: Gives input to a command.
    
    ```
    command < file.txt
    ```
    
    The above will execute `command` on the contents of `file.txt`.

2. `<>`: same as above, but the file is open in read+write mode instead of read-only.

    ```
    command <> file.txt
    ```
    
    If the file doesn't exist, it will be created. That operator is rarely used because commands generally only read from their stdin, though it can come handy in a number of specific situations.

3. `>`: Directs the output of a command into a file.

    ```
    command > out.txt
    ```
    
    The above will save the output of `command` as `out.txt`. If the file exists, its contents will be overwritten and if it does not exist it will be created.
    
    This operator is also often used to choose whether something should be printed to standard error or standard output:
    
    ```
    command >out.txt 2>error.txt
    ```
    
    In the example above, `>` will redirect standard output and `2>` redirects standard error. Output can also be redirected using `1>` but, since this is the default, the `1` is usually omitted and it's written simply as `>`.
    
    Redirect stderr to stdout (`&1`), and then redirect stdout to a file:
    
    ```
    command >out 2>&1
    ```
    
    So, to run `command` on `file.txt` and save its output in `out.txt` and any error messages in `error.txt` you would run:
    
    ```
    command < file.txt > out.txt 2> error.txt
    ```

4. `>|`: Does the same as `>`, but will overwrite the target, even if the shell has been configured to refuse overwriting (with `set -C` or `set -o noclobber`).

    ```
    command >| out.txt
    ```
    
    If `out.txt` exists, the output of command will replace its content. If it does not exist it will be created.
    
5. `>>`: Does the same as `>`, except that if the target file exists, the new data are appended.

    ```
    command >> out.txt
    ```
    
    If `out.txt` exists, the output of command will be appended to it, after whatever is already in it. If it does not exist it will be created.

6. `&>`, `>&`, `>>&` and `&>>`: (non-standard). Redirect both standard error and standard output, replacing or appending, respectively.

    ```
    command &> out.txt
    ```
    
    Both standard error and standard output of `command` will be saved in `out.txt`, overwriting its contents or creating it if it doesn't exist.
    
    ```
    command &>> out.txt
    ```
    
    As above, except that if `out.txt` exists, the output and error of command will be appended to it.
    
    The `&>` variant originates in bash, while the `>&` variant comes from csh (decades earlier). They both conflict with other POSIX shell operators and should not be used in portable sh scripts.

7. `<<`: A here document. It is often used to print multi-line strings.

    ```
    command << WORD
        Text
    WORD
    ```
    
    Here, `command` will take everything until it finds the next occurrence of `WORD`, `Text` in the example above, as input . While `WORD` is often `EoF` or variations thereof, it can be any alphanumeric (and not only) string you like. When `WORD` is quoted, the text in the here document is treated literally and no expansions are performed (on variables for example). If it is unquoted, variables will be expanded.
    
    If you want to pipe the output of `command << WORD ... WORD` directly into another command or commands, you have to put the pipe on the same line as `<< WORD`, you can't put it after the terminating WORD or on the line following. For example:
    
    ```
    command << WORD | command2 | command3...
        Text
    WORD
    ```

8. `<<<`: Here strings, similar to here documents, but intended for a single line. These exist only in the Unix port or rc (where it originated), zsh, some implementations of ksh, yash and bash.

    ```
    command <<< WORD
    ```
    
    Whatever is given as `WORD` is expanded and its value is passed as input to `command`. This is often used to pass the content of variables as input to a command. For example:
    
    ```
    $ foo="bar"
    $ sed 's/a/A/' <<< "$foo"
    bAr
    # as a short-cut for the standard:
    $ printf '%s\n' "$foo" | sed 's/a/A/'
    bAr
    # or
    sed 's/a/A/' << EOF
    $foo
    EOF
    ```

## References

1. [What are the shell's control and redirection operators?](https://unix.stackexchange.com/questions/159513/what-are-the-shells-control-and-redirection-operators/159514#159514)
2. [How to redirect stderr to a file?](https://askubuntu.com/questions/625224/how-to-redirect-stderr-to-a-file)
