# Lab Report 3

## Exploring the `grep` Command
The source used for all of the below information is [https://www.geeksforgeeks.org/grep-command-in-unixlinux/](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)

The `grep` command searches a file for a pattern, and prints out all lines that contain a match to the pattern. The following are some useful options for the command that can take care of several useful functions:

### `-r`
The `-r` option allows us to recursively search through every file in a directory and its subdirectories, which is very useful for finding the location of a desired pattern within a directory especially if we don't know the specific file which the pattern is in. Using `-r` is much faster than manually inputting every possible combination of `*.txt`, `*/*.txt`, `*/*/*.txt`, etc., and the more subdirectories exist, the more efficient simply using `-r` becomes.

Let's use the "Lucayans" task from Skill Demo 1 as our first example:
~~~
$ grep -r "Lucayans" written_2/
written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had 
settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they
caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San 
Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. 
Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two 
weeks before sailing towards Cuba.
written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons 
frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well 
— at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with 
their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — 
in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
~~~

As we see here, I didn't have to know how many subdirectories the command would need to traverse before reaching the correct file.

I'll be using `-r` for the many of the following options demonstrations as well, since I often want to search through the entire directory as opposed to a single file. I imagine there are many actual applications where searching through directories rather than single files is desireable, so I hope the below examples will suffice for showing how useful `-r` can be too.

### `-l`
By default, `grep` will print every line in its entirety that contains the searched pattern. Going back to the "Lucayans" example from above, the actual task was just to find the file name, and while technically we do see it is located in `written_2/travel_guides/berlitz2/Bahamas-History.txt`, there's quite a bit of extra text that's unnecessary for completing the task. The `-l` option will make it so that `grep` only displays the file names and not every line, cutting down on unwanted clutter when just the file name is wanted.

~~~
$ grep -r -l "Lucayans" written_2/
written_2/travel_guides/berlitz2/Bahamas-History.txt
~~~

Much better! Just as another example, let's see if we can display the names of every file that contains the pattern "ice cream":
~~~
$ grep -r -l "ice cream" written_2/
written_2/non-fiction/OUP/Berk/CH4.txt
written_2/travel_guides/berlitz1/WhereToEdinburgh.txt
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz1/WhereToIndia.txt
written_2/travel_guides/berlitz1/WhereToItaly.txt
written_2/travel_guides/berlitz2/Boston-WhereToGo.txt
written_2/travel_guides/berlitz2/China-WhereToGo.txt
written_2/travel_guides/berlitz2/Cuba-WhereToGo.txt
written_2/travel_guides/berlitz2/Paris-WhatToDo.txt
written_2/travel_guides/berlitz2/Paris-WhereToGo.txt
~~~
Nice!

### `-c`
What if we didn't need to know which lines the pattern is located in, but simply needed to know how many total lines contain the pattern? Once again, `grep`'s default return behaviour doesn't quite suit our needs, as counting every single returned line by hand would be incredibly inefficient.

For example, an extremely common pattern like "the" would absolutely flood the terminal, and you probably wouldn't get much usable information out of your command. If we just wanted to know how many lines contain "the" in a given file, we could more fittingly use:
~~~
$ grep -r -c "the" written_2/travel_guides/berlitz2/Bahamas-History.txt
30
~~~
We see that the pattern "the" appears in 30 lines total in the file `Bahamas-History.txt`.

If there are multiple files that contain the pattern, grep will show how many lines the pattern appears in each individual file separately. I've cut down the below output to just a few lines since "the" is likely to be found most of the text files:
~~~
$ grep -r -c "the" written_2/
written_2/non-fiction/OUP/Abernathy/ch1.txt:68
written_2/non-fiction/OUP/Abernathy/ch14.txt:57
written_2/non-fiction/OUP/Abernathy/ch15.txt:62
written_2/non-fiction/OUP/Abernathy/ch2.txt:63
.
.
.
written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt:111
~~~
So, the pattern "the" appears in 68 lines for `ch1.txt`, 57 lines for `ch14.txt`, and so forth.

For good measure, let's see how many lines contain "Lucayans" in `Bahamas-History.txt`:
~~~
$ grep -r -c "Lucayans" written_2/travel_guides/berlitz2/Bahamas-History.txt
2
~~~
If we go back to our first `grep` search for "Lucayans" that displayed the lines, we can manually count and confirm that "Lucayans" indeed appears in two lines of the file.
Unfortunately, this command does not count a pattern multiple times if it appears more than once in a single line, but it can still have its uses. For example, if you're working with data that you know only contains one word per line, you can use `grep -l` in the same way you would otherwise use the `wc` command.

### `-w`
Let's consider the following command:
~~~
$ grep -r -l "ice crea" written_2/
written_2/non-fiction/OUP/Berk/CH4.txt
written_2/travel_guides/berlitz1/HistoryItaly.txt
written_2/travel_guides/berlitz1/WhereToEdinburgh.txt
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz1/WhereToIndia.txt
written_2/travel_guides/berlitz1/WhereToItaly.txt
written_2/travel_guides/berlitz2/Boston-WhereToGo.txt
written_2/travel_guides/berlitz2/China-WhereToGo.txt
written_2/travel_guides/berlitz2/Cuba-WhereToGo.txt
written_2/travel_guides/berlitz2/Paris-WhatToDo.txt
written_2/travel_guides/berlitz2/Paris-WhereToGo.txt
~~~
It's the same result as when we typed out "ice cream" fully, because "ice cream" will always contain the pattern "ice crea" as well, and therefore anything that matches with "ice cream" will also match with "ice crea".
However, adding `-w` changes this:
~~~
$ grep -r -l -w "ice crea" written_2/

~~~
Instead of accepting any time the pattern "ice crea" appears as a match, `-w` will only return a match if the pattern is found as a whole word and not a substring.
Returning to the "Lucayans" example, let's try searching for "Lucayan" without the "s":
~~~
$ grep -r -l "Lucayan" written_2/
written_2/travel_guides/berlitz2/Bahamas-History.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
~~~
The pattern "Lucayan" can be found in both `Bahamas-History.txt` and `Bahamas-WhereToGo.txt`.
Now, let's do the same thing but include the `-w` modifier this time:
~~~
$ grep -r -l -w "Lucayan" written_2/
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
~~~
Because there is no instance of the specific word "Lucayan" without the "s" in the file `Bahamas-History.txt`, the `-w` option causes the command to only match with `Bahamas-WhereToGo.txt`.
We see that the `-w` option matters if we want to locate exactly the desired pattern, and not also include words that have the pattern as a substring.
