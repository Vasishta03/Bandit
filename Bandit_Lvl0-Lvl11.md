## Bandit: Walkthrough and Notes

This document details the process of completing the Bandit War Game challenges on OverTheWire.org. It provides a step-by-step breakdown of each level, along with explanations and additional notes.

**Disclaimer:** While this walkthrough offers guidance, it's recommended to attempt solving the challenges yourself first. This strengthens your problem-solving skills and understanding of the concepts involved.

### Level Breakdown

**Level 0**

* **Command:** `ssh bandit0@bandit.labs.overthewire.org -p 2220`
* **Username:** bandit0
* **Password:** bandit0 (found in `readme` file)

**Level 1**

* **Command:** `ssh bandit1@bandit.labs.overthewire.org -p 2220`
* **Password:** NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL (found in `readme` file)

**Level 2**

* **Command:** `ssh bandit2@bandit.labs.overthewire.org -p 2220`
* **Password:** aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG (found in file named "spaces in the filename")

**Level 3**

* **Command:** `ssh bandit3@bandit.labs.overthewire.org -p 2220`
* **Password:** 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe (found in hidden file named ".hidden" in the "inhere" directory)

**Level 4**

* **Command:** `ssh bandit4@bandit.labs.overthewire.org -p 2220`
* **Password:** lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR (found in file named ".file07" in the "inhere" directory)

**Level 5**

* **Command:** `ssh bandit5@bandit.labs.overthewire.org -p 2220`
* **Password:** P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU (found in file under "inhere" with size 1033 bytes, human-readable, and non-executable)

**Level 6**

* **Command:** None mentioned (use `find` command with specified properties)
* **Password:** Z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S (found using `find / -user bandit7 -group bandit6 -size 33c` to locate the file containing the password and then using `cat /var/lib/dpkg/info/bandit7.password`)

**Level 7**

* **Command:** `cat data.txt | grep millionth` (not `cat data.txt`)
* **Password:** TESKZC0XvTetK0S9xNwm25STk5iWrBvP (found by using `grep millionth` to search for the word near the password)

**Level 8**

* **Command:** `cat data.txt | sort | uniq -u`
* **Password:** EN632PlfYiZbn3PhVK3XOGSlNInNE00t (found by sorting the lines in the file and using `uniq` to identify the unique line)

**Level 9**

* **Command:** `cat data.txt | strings | grep ^=`
* **Password:** G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s (found using `strings` to extract printable strings and `grep ^=` to filter for lines starting with several `=` characters)

**Level 10**

* **Command:** `cat data.txt | base64 -d`
* **Password:** 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM (found by decoding the base64 encoded data in the file)

**Level 11**

* **Command:** `cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'`
* **Password:** JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv (found by performing a Caesar cipher shift of 13 positions on the lowercase and uppercase letters)

