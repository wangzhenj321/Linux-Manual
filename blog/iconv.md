#### Description

The `iconv` program reads in text in one encoding and outputs the text in another encoding. If no input files are given, or if it is given as a dash (-), `iconv` reads from standard input. If no output file is given, `iconv` writes to standard output.

If no **from-encoding** is given, the default is derived from the current locale's character encoding. If no **to-encoding** is given, the default is derived from  the current locale's character encoding.

#### Synopsis

- `iconv [options] [-f from-encoding] [-t to-encoding] [inputfile]...`

#### Options

- `-f from-encoding, --from-code=from-encoding`

    Use **from-encoding** for input characters.

- `-t to-encoding, --to-code=to-encoding`

    Use **to-encoding** for output characters.

- `-l, --list`

    List all known character set encodings.

- `-o outputfile, --output=outputfile`

    Use **outputfile** for output.
