# getoptsy: getopts alternative for long options

This `getoptsy` Unix shell script is demonstration of how to parse command
line arguments to long options, by using a while loop and pure POSIX code.

The source code and detailed comments show how to process these options:

  * Long options, such as `--help` for help, `--verbose` for verbose, etc.

  * Short options, such as `-h` for help, `-v` for verbose, etc.

  * Short options as runs, such as `-hv` for help and verbose.

  * Value options such as `--foo=bar`, `--foo bar`, `-f bar`, etc.


## About this demonstration

This demonstration aims to show how you can write your own code.

This demonstration does not aim to provide a drop-in replacement for 
getopts, or its specification, or its way of describing options, etc.;
if you want that, then we can suggest `getopts_long`, linked below.

We welcome constructive feedback and ideas for improvements.


## Usage

Syntax:

```sh
getoptsy [options] [arguments]
```

Options:

```txt
-h|--help            Print this help
-v|--verbose         Increment the verbose level (multiple use)
--foo bar|--foo=bar  Set foo to bar
--                   Finish options parsing
```

Examples:

```sh
getoptsy --help 
#=> Print this help

getoptsy -vvv 
#=> Increment the verbose three times

getoptsy --foo bar 
#=> Set foo to bar
```

## Comparisons

Comparisons to other command line arguments options parsing:

* POSIX getopts supports short options and runs, but not long options.

* POSIX-compatibe getops_long supports everything her, but is complex.

* Bash shell getopt supports both options, but not other shells.


## Why use POSIX?

This script aims to work with the POSIX standard, because this tends
improves portability and compatibility with a wide range of systems.

The POSIX standard provides a tool to get options, named `getopts`.
This supports for one-character "short options", such as `-h` for help,
and does not support multi-character "long options", such as `--help`.

We know that some developers strongly favor runs of short options,
such as `-abc` which is intended to be equivalent to `-a -b -c`.

We believe that long options tend to help people learn and use scripts.
For example some of our daily tools now offer an option `--dry-run`,
and some of our administration tools now offer an option `--danger`
to help caution the user to take more care about the command usage.

We believe the best approach will use POSIX compatibilty, short options,
runs of short options, and long options. So we created the code below.


## Why use a shell script?

If you're reading this, then you probably already know there are many
alternatives for writing commands, such as by using higher-structure
languages, which provide better argument parsing, more capabilties, etc.

If you're writing a shell script, then it's wise to know the limitations.
For example, you may want to consider changing to a different language if
your shell script has above a hundred or so lines of code, or has many
options, or uses complex logic, or involves work of high value to you.


## For the future

We advocate for the POSIX standard group members to consider a future POSIX
release that upgrades the getopts tool by adding support for long options.

A new getops with long options will supersede the "getoptsy" script.
It will help many shell scripts, and many users, and many developers,
by providing a standard built-in way to parse arguments into options.


## Tracking

* Package: unix-shell-script-posix-args-opts-like-getops
* Version: 1.0.0
* Created: 2022-10-23T10:25:48Z
* Updated: 2022-10-25T18:54:19Z
* License: GPL-2.0-or-later or contact us for custom
* Website: https://github.com/sixarm/unix-shell-script-posix-args-opts-like-getops
* Contact: Joel Parker Henderson (joel@joelparkerhenderson.com)
