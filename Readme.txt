
Title: Information Retrieval CS6322.001 Fall 18- Homework 1
Description: Tokenisation and Stemming of Cranfield collection
Author: Sheetal Arun Kadam (sak170006)
Date: 10/02/2018
Content: sak170006_Homework1.zip
Default Source files:/people/cs/s/sanda/cs6322/Cranfield on the UTD cs1, cs2, and csgrads1 machines
----------------------------------------------------------------------------------------------------------------------------------------
The program parses through the Cranfield files and creates dictionary of tokens and stems. 

Zip folder contains: 1. Readme.txt 
		     2. runscript.sh
		     3. Java package
Package has 3 files: TokenisationStemmer.java, Stemmer.java, ValCustomComparator.java

TokenisationStemmer.java - Process tokens and stems and adds to dictionary. It takes an optional parameter for path of files
Stemmer.java -Implementation of Porters Stemming algorithm. Open source implementation available  http://www.tartarus.org/~martin/PorterStemmer
ValCustomComparator.java - Custom comparator for TreeMap to sort by values

Run time: 1319 ms (averaged over 5 runs).

----------------------------------------------------------------------------------------------------------------------------------------
##How to run the program:

A. unzip sak170006_Homework1.zip

With runscript

1. chmod 777 runscript.sh
2. ./runscript.sh filepath 
   OR ./runscript.sh  (takes files from /people/cs/s/sanda/cs6322/Cranfield)
3. Dictionary stats and most frequent words are printed
4. User may press 1 to view Token Dictionary, 2 to view Stem Dictionary
5. Press 0 to exit

Without runscript
1. javac sak170006_hw1/* 
3. java sak170006_hw1/TokenisationStemmer (takes files from /people/cs/s/sanda/cs6322/Cranfield) 
   OR java sak170006_hw1/TokenisationStemmer newfile_path
4. Dictionary stats and most frequent words are printed
5. User may press 1 to view Token Dictionary, 2 to view Stem Dictionary
6. Press 0 to exit
----------------------------------------------------------------------------------------------------------------------------------------

##Design decisions:

1. All SGML tags are removed
2. All tokens are in lowercase. For example, Apple -> apple
3. Words with dashes are split into individual tokens. For example, middle-class-> middle  and class
4. Posessives - Apostrophe('s) is removed. For example, university's -> university 
5. All dots are removed. For example, U.S.A -> USA
6. Words are split by comma, white space and other special characters like /, +,_, -, =,(,), \
7. Words with only numbers are removed. For example, 1234 is removed
8. Alphanumeric words are stripped of the numbers. For example, sc123ool -> school 
9. Lastly any remaining characters other than a-z are removed from the word 
 

---------------------------------------------------------------------------------------------------------------------------------------

## Data Structures
1. Both token and stem dictionary use HashMap as it  supports fast retreival of keys in O(1) time
2. Sorted dictionary is stored in TreeMap with custom comparator that sorts by values and orders in O(log(n)) time.

----------------------------------------------------------------------------------------------------------------------------------------
##Program Flow
1.Each file is parsed and line is extracted
2.Every line is sent for processing
3.Each token is split and cleaned
4.Cleaned token is added to token dictionary
5.Stem is extracted from the cleaned token using Porter's Stemming rules and then inserted to stem dictionary 
6.Both dictionaries are sorted by frequency and stored into another dictionary for retrieval of frequent tokens/stems
7.Dictionary stats are computed

---------------------------------------------------------------------------------------------------------------------------------------

## Sample output 

A: TOKENISATION OUTPUT 
1. The number of tokens in the Cranfield text collection: 230824
2.The number of unique words in the Cranfield text collection: 8780
3. The number of words that occur only once in the Cranfield text collection: 3316
4. The 30 most frequent tokens in the Cranfield text collection : 
the: 19450
of: 12717
and: 6677
a: 5987
in: 4651
to: 4563
is: 4114
for: 3493
are: 2429
with: 2265
on: 1944
flow: 1849
at: 1834
by: 1756
that: 1570
an: 1388
be: 1272
pressure: 1207
boundary: 1156
from: 1116
as: 1113
this: 1081
layer: 1002
which: 975
number: 973
results: 885
it: 857
mach: 824
theory: 788
shock: 712

5. The average number of word tokens per document: 164

B: STEMMING 
1.The number of distinct stems in the Cranfield text collection: 6075
2. The number of stems that occur only once in the Cranfield text collection: 2254
3. The 30 most frequent stems in the Cranfield text collection : 
the: 19450
of: 12717
and: 6677
a: 5987
in: 4651
to: 4563
is: 4114
for: 3493
ar: 2458
with: 2265
on: 2262
flow: 2080
at: 1834
by: 1756
that: 1570
an: 1388
pressur: 1382
be: 1369
number: 1347
boundari: 1185
layer: 1134
from: 1116
as: 1113
result: 1087
thi: 1081
it: 1044
effect: 996
which: 975
method: 887
theori: 881

4. The average number of word stems per document: 164
Time of execution: 1751 milliseconds
0
