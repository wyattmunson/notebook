---
title: "Bash Scripting"
description: ""
lead: ""
date: 2023-06-26T17:35:47-07:00
lastmod: 2023-06-26T17:35:47-07:00
draft: false
images: []
menu:
  docs:
    parent: ""
    identifier: "bash-scripting-73191668904528a482e44afaddf33e5c"
weight: 999
toc: true
---

## Variables

```bash
# set a variable
VARIABLE_NAME=some_text

# reference a variable
echo $VARIABLE_NAME
```

### Bash Builtin Variables

```bash
$0        # Name of the Bash script
$1 - $9   # First 9 arguments to the script
$#        # Number of arguments were passed to script
$@        # All the arguments supplied to the Bash script.
$?        # The exit status of the most recently run process.
$$        # The process ID of the current script.
$USER     # The username of the user running the script.
$HOSTNAME # The hostname of the machine the script is running on.
$SECONDS  # The number of seconds since the script was started.
$RANDOM   # Returns a different random number each time is it referred to.
$LINENO   # Returns the current line number in the Bash script.
```

### Reading Input

Read input is used to get input from a user which can be set to a variable.

```bash
# set a variable
read VARIABLE_NAME
# set a variable, with prompt statement
read -p 'Enter name: ' VARIABLE_NAME
# set a variable, with prompt statement, password
read -sp 'Enter password: ' VARIABLE_NAME
```

### Check if Variable Exists

```bash
#check if variable exists
if [ -n "$1" ]; then
  echo "You supplied the first parameter!"
else
  echo "First parameter not supplied. Exiting."
  exit 1
fi

# variable does not exist
if [ -z "$1" ]; then
  echo "Does not exists"
fi

# check if exists, otherwise set
if [ -z ${var+x} ]; then echo "var is unset"; else echo "var is set to '$var'"; fi
```

---

## If Statements

```bash
if [[ $1 -gt 100]]
then
  echo "Some text"
fi
```

Use semicolons (`;`) to condense if statements down to one line.

```bash
# check if exists, otherwise set
if [ -z ${var+x} ]; then echo "var is unset"; else echo "var is set to '$var'"; fi
```

Extend logic with `if`, `elif`, and `else`.

{{< alert icon="👉" >}}
Extend logic with `if`, `elif`, and `else`.
{{< /alert >}}

```bash
if [ $1 -gt 100]
then
  echo "Some text"
elif [ $2 == 'no']
then
  echo "Alternate matching condition"
else
  echo "Final catch condition"
fi
```

### Wildcards

Use the asterisk wildcard (`*`) for partial matches of one or more occurences of any charachter. Can match beginning, end, or both.

```bash
if [[ $1 == *"$SUBSTRING"* ]]
then
  echo "Matches substring"
fi
```

Use the question mark (`?`) to match a single occurence of any chatachter.

```bash
if [[ $1 == ??"log.txt" ]]
then
  echo "Matches substring"
fi
```

### Boolean Operators

```bash
&&  # and
||  # or
```

```bash
if [[ $1 -gt 100 && $2 == 'yes']]
then
  echo "And condition met"
elif [[ $1 -gt 50 || $2 == 'no']]
then
  echo "Or condition met"
fi
```

### Equality Operators

```bash
=
==  # string comparisons
-eq # equals, numeric comparisons
-gt # greater than
-ge # greater than or equal to
-lt # less than
-le # less than or equal to
-ne # not equal
```

---

## Redirection

```bash
# redirect stdout to file
command >file
# same as above
command 1>file
# redirect stderr to file
command 2>file
# redirect stdout & stderr to file
command &>file
# same as above
# redirect stdout out to file, redirect stderr to stdout, which outputs to file
command >file 2>&1
# discard stdout of command
command > /dev/null
# discard stdout & stderr of command
command &> /dev/null
# redirect contents of file to stdin of command
command <file
```

### Redirect Multiple Lines

```bash
command &lt;&lt;EOL
multi
line
text
goes
here
EOL
```

---

## Bracket Syntax

Bash has two types of syntax when dealing with if statements: `[single]` and `[[double]]`. Single is an older supported syntax and double allow for more features.

### Single Bracket Notation

1. File based conditions `if [-L symlink]; then`
1. String-based conditions `if ["$some_var" == "foo"]; then`
1. Numeric-based conditions `if ["$some_var" -gt 100]; then`

### Double Bracket Notation

1. **Equality operators**: introduces and (`&&`), or (`||`)
   - `if [[ "$some_var" == "test" && $1 -gt 2 ]]; then`
1. **Regex pattern matching**: introduces and (`&&`), or (`||`)
   - `if [[ "$some_var" == "test" && $1 -gt 2 ]]; then`
1. **Shell globbing**: asterisk will expand to anything
   - `if [[ "$some_var" == *[Ff]oo ]]; then`
1. **Word Splitting is prevented:** so quotes can be omitted around variables
   - `if [[ $some_var == *[Ff]oo ]]; then`
1. **Filenames are not expanded:**
   - With the older single bracked notation `if [ -a *.sh ]; then`. This will return true if there's a single matching shell file. Return false if there are no files. Return an error if
   - With double bracket notation, it will return true if there are one or more shell files
   - `if [[ $some_var == *[Ff]oo ]]; then`
