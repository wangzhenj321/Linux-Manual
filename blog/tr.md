## Description

Translate, squeeze, and/or delete characters from standard input, writing to standard output.

## Synopsis

- `tr [OPTION]... SET1 [SET2]`

## Options

1. `-c, -C, --complement`

    use the complement of SET1

2. `-d, --delete`

    delete characters in SET1, do not translate

3. `-s, --squeeze-repeats`

    replace each sequence of a repeated character that is listed in the last specified SET, with a single occurrence of that character

4. `-t, --truncate-set1`

    first truncate SET1 to length of SET2

---

SETs are specified as strings of characters. Most represent themselves. Interpreted sequences are:

| SET | Description |
| --- | --- |
| \NNN | character with octal value NNN (1 to 3 octal digits) |
| \\ | backslash |
| \a | audible BEL |
| \b | backspace |
| \f | form feed |
| \n | new line |
| \r | return |
| \t | horizontal tab |
| \v | vertical tab |
| CHAR1-CHAR2 | all characters from CHAR1 to CHAR2 in ascending order |
| [CHAR\*] | in SET2, copies of CHAR until length of SET1 |
| [CHAR\*REPEAT] | REPEAT copies of CHAR, REPEAT octal if starting with 0 |
| [:alnum:] | all letters and digits |
| [:alpha:] | all letters |
| [:blank:] | all horizontal whitespace |
| [:cntrl:] | all control characters |
| [:digit:] | all digits |
| [:graph:] | all printable characters, not including space |
| [:lower:] | all lower case letters |
| [:print:] | all printable characters, including space |
| [:punct:] | all punctuation characters |
| [:space:] | all horizontal or vertical whitespace |
| [:upper:] | all upper case letters |
| [:xdigit:] | all hexadecimal digits |
| [=CHAR=] | all characters which are equivalent to CHAR |

## Examples

### Without any options

Running `tr` without any options replaces each of the characters specified in SET1 with the characters from SET2 that have the same position.

```
$ echo "hellole" | tr el mn
hmnnonm
```

### Change character case

There are three ways of changing character case with `tr`:

1. Specify which characters from the input you want to convert. This option changes the character case or entire characters, replacing the ones from SET1 with the ones from SET2.

    ```
    $ tr WWW www
    WWW.google.com
    www.google.com
    ^C
    ```
    
    Press CTRL+C to exit input mode.

2. Specifying a range allows tr to change the case of any character within that specified range. The following example shows how to convert uppercase characters to lowercase:

    ```
    $ tr A-Z a-z
    HELLO
    hello
    ^C
    ```

3. Match and convert characters by specifying interpreted sequences. For example, the sequence for lowercase characters is [:lower:], and the sequence for uppercase characters is [:upper:]. Specifying the two sequences instructs `tr` to match and convert the character case:

    ```
    $ tr [:upper:] [:lower:]
    EXAMPLE
    example
    ^C
    ```

### Remove repeated characters

The `-s` option squeezes repeated characters into a single instance of that character. The option is particularly useful when converting whitespaces to tabs or newline characters, and the input text contains multiple continuous whitespace characters.

For example, the following input contains multiple whitespace characters. Converting them to tabs without squeezing provides the following result:

```
$ echo "Hello  world!" | tr [:space:] '\t'
Hello       world!
```

To avoid multiple tabs and whitespaces in the output, specify the `-s` option:

```
$ echo "Hello  world!" | tr -s [:space:] '\t'
Hello   world!
```

### Delete characters

Remove specific characters using the `-d` option. In the following example, `tr` deletes each instance of the e character:

```
$ echo "Hello world!" | tr -d 'e'
Hllo world!
```

Optionally, specify a group of characters using interpreted sequences. For example, remove all digits by specifying the [:digit:] sequence:

```
$ echo "PIN: 1234" | tr -d [:digit:]
PIN: 
```

### Complement sets

Use the `-c` option to complement the characters in SET1. In the following example, we remove all characters except digits:

```
$ echo "PIN: 1234" | tr -cd [:digit:]
1234
```

### Remove newline characters

Shrink the space a text occupies by converting newline characters into spaces. The content then appears in a single line.

```
$ tr -s '\n' ' '
```

### Truncate set

By default, if SET1 is longer than SET2, `tr` reuses the last character from SET2 when processing the input. For example:

```
$ echo "Hello world!" | tr Hello 12
12222 w2r2d!
```

Use the `-t` option to truncate SET1 to the length of SET2:

```
$ echo "Hello world!" | tr -t Hello 12
12llo world!
```

### Print each word separately

Print a file's contents line by line using the `-c` option and replace the non-alphanumerical characters with a newline character.

```
$ echo "Hello world!" | tr -cs [:alnum:] '\n'
Hello
world
```

## References

1. [Linux tr Command with Examples](https://phoenixnap.com/kb/linux-tr)
