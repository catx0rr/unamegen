## Username and Email Wordlist Generator

This Python script generates a wordlist of potential usernames and email addresses based on provided names. You can input a single name or a file containing multiple names, and optionally specify a domain to format the output as email addresses.

## Originally forked from [hac01/uwg](https://github.com/hac01/uwg)

- Added new iterations (since common usernames sometimes have '2' i.e. jsmith2)
- Append usage instead of write so the script can be used in bash for loops

## Features

- Generates various username formats:
  - `first.last`
  - `f.last`
  - `first_last`
  - `first.l`
  - `flast`
  - `firstl`
  - `f.l`
  - `last.first`
  - `first-last`
  - `last.f`
- Supports single name input or multiple names from a file.
- Optionally appends a domain to generate email addresses.


# Usage
## Single Name Input
Generate a wordlist for a single name and save it to a file:

```bash
python unamegen.py --name "John Doe" --output mywordlist.txt
```
## Multiple Names from a File
Generate a wordlist for multiple names provided in a file:

```bash
python unamegen.py --file names.txt --output mywordlist.txt
```
## Adding a Domain for Email Format
Generate email addresses by appending a domain to each username format:

```bash
python unamegen.py --name "John Doe" --domain yoooh.com --output mywordlist.txt
```

## Adding an Iteration of the Username
Generate the same wordlist for usernames or emails 

```
python unamegen.py --name "John Doe" --domain yoooh.com --iterations 2 --output mywordlist.txt
```

## Using names file in generating emails
```
DOMAIN='domain.com'; NAMESFILE='samplenames.txt'; names=(); while IFS= read -r l; do names+=("$l"); done < ${NAMESFILE} && for x in ${names[@]}; do python3 unamegen.py -n $x -d ${DOMAIN} -o emails_${DOMAIN}; done
``` 

## Command-Line Options
- `-n`, `--name`: A single name to process (format: "First Last").
- `-f`, `--file`: A file containing multiple names (each on a new line).
- `-d`, `--domain`: Optional domain to append for email format.
- `-i`, `--iterations` : Number of iterations for common name formats
- `-o`, `--output`: Output file name (default: `wordlist.txt`).
