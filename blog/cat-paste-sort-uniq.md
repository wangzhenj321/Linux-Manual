**Table of Contents**

[Part 1 `cat` `paste` `sort` `uniq`](#part-1-cat-paste-sort-uniq)

[Part 2 `cat`](#part-2-cat)

[Part 3 `sort`](#part-3-sort)

[Part 4 `uniq`](#part-4-uniq)


## Part 1 `cat` `paste` `sort` `uniq`

**两个文件的交集、并集（前提条件：每个文件中不得有重复行）**

1. 取出两个文件的并集（重复的行只保留一份）

    ```
    cat file1 file2 | sort | uniq > file3
    ```

2. 取出两个文件的交集（只留下同时存在于两个文件中的文件）

    ```
    cat file1 file2 | sort | uniq -d > file3
    ```

3. 删除交集，留下其他的行

    ```
    cat file1 file2 | sort | uniq -u > file3
    ```

**两个文件合并**

1. 一个文件在上，一个文件在下

    ```
    cat file1 file2 > file3
    ```

2. 一个文件在左，一个文件在右

    ```
    paste file1 file2 > file3
    ```

**一个文件去掉重复的行**

1. 重复的多行记为一行

    ```
    sort file | uniq
    ```

2. 重复的行全部去掉

    ```
    sort file | uniq -u
    ```


## Part 2 `cat`

#### Description

Concatenate FILE(s) to standard output.

#### Options

- `-A`

    equivalent to `-vET`

- `-v`, `--show-nonprinting`

    use ^ and M- notation, except for LFD and TAB

- `-E`

    display $ at end of each line

- `-T`

    display TAB characters as ^I

- `-b`

    number nonempty output lines, overrides `-n`

- `-n`

    number all output lines

#### Examples

1. 以上下顺序合并所有files: `cat filename1 filename2 … filenameN`


## Part 3 `sort`

#### Description

Write sorted concatenation of all FILE(s) to standard output. With no FILE, or when FILE is `-`, read standard input.

#### Options

- `-n`

    compare according to string numerical value

- `-r`

    reverse the result of comparisons

- `-k`

    sort via a key; **KEYDEF** gives location and type

- `-o`

    write result to FILE instead of standard output

- `-t`

    use SEP instead of non-blank to blank transition

- `-u`

    with `-c`, check for strict ordering; without `-c`, output only the first of an equal run

> **KEYDEF** is `F[.C][OPTS][,F[.C][OPTS]]` for start and stop position, where F is a field number and C a character position in the field; both are origin 1, and **the stop position defaults to the line's end**. If neither `-t` nor `-b` is in effect, characters in a field are counted from the beginning of the preceding whitespace. OPTS is one or more single-letter ordering options `[bdfgiMhnRrV]`, which override global ordering options for that key. If no key is given, use the entire line as the key. Use `--debug` to diagnose incorrect key usage.

**References:** [linux sort 命令详解](https://www.cnblogs.com/51linux/archive/2012/05/23/2515299.html)


## Part 4 `uniq`

#### Description

Filter **adjacent matching lines** from INPUT (or standard input), writing to OUTPUT (or standard output). **With no options, matching lines are merged to the first occurrence.**

> **Note:** `uniq` does not detect repeated lines unless they are adjacent. You may want to sort the input first, or use `sort -u` without `uniq`.

#### Options

- `-c, --count`

    prefix lines by the number of occurrences

- `-d, --repeated`

    only print duplicate lines, one for each group

- `-i, --ignore-case`

    ignore differences in case when comparing

- `-u, --unique`

    only print unique lines
