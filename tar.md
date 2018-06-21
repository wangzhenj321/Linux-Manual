#### Description

打包程序(tar)，本身不具有压缩功能，调用压缩功能(gzip/bzip2/compress)

#### Options

- `-c` 建立新的压缩文件（打包）
- `-x` 从压缩文件中提取文件（解包）
- `-z` 支持gzip解压文件
- `-j` 支持bzip2解压文件
- `-Z` 支持compress解压文件
- `-v` 显示操作过程
- `-f` 指定压缩文件
- `-t` 显示压缩文件的内容

#### Examples

- *.tar

    ```
    tar -xvf *.tar
    tar -cvf *.tar dirname
    ```

- *.gz

    ```
    gunzip *.gz （或者gunzip -d *.gz）
    gunzip filename
    ```

- *.tar.gz(*.tgz)

    ```
    tar -zxvf *.tar.gz
    tar -zcvf *.tar.gz dirname
    ```

- *.bz2

    ```
    bzip2 -d *.bz2 （或者bunzip2 *.bz2）
    bzip2 -z filename
    ```

- *.tar.bz2

    ```
    tar -jxvf *.tar.bz2
    tar -jcvf *.tar.bz2 filename
    ```

- *.Z

    ```
    uncompress *.Z
    compress *.Z
    ```

- *.tar.Z

    ```
    tar -Zvxf *.tar.Z
    tar -Zcvf *.tar.Z dirname
    ```

- *.zip

    ```
    unzip *.zip
    zip *.zip dirname
    ```

- *.rar

    ```
    rar x *.rar
    rar a *.rar dirname
    ```
