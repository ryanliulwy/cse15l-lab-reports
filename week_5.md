# Lab Report 3

## Exploring the `grep` Command
The source used for all of the below information is [https://www.geeksforgeeks.org/grep-command-in-unixlinux/](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)

The `grep` command searches a file for a pattern, and prints out all lines that contain a match to the pattern. The following are some useful options for the command that can take care of several useful functions:

### `-r`
The `-r` option allows us to recursively search through every file in a directory and its subdirectories, which is very useful for finding the location of a desired pattern within a directory especially if we don't know the specific file which the pattern is in. Using `-r` is much faster than manually inputting every possible combination of `\*.txt`, `\*/\*.txt`, `\*/\*/\*.txt`, etc., and the more subdirectories exist, the more efficient simply using `-r` becomes.

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

I'll be using `-r` for the many of the following options demonstrations as well, since I want to search through the directory as opposed to a single file. I imagine there are many actual applications where searching through directories rather than single files is desireable, so I hope the below examples will suffice for showing how useful `r` can be.

### -l 
By default, `grep` will print every line in its entirety that contains the searched pattern. Going back to the "Lucayans" example from above, the actual task was just to find the file name, and while technically we do see it is located in `written_2/travel_guides/berlitz2/Bahamas-History.txt`, there's quite a bit of extra text that's unnecessary for completing the task. The `-l` option will make it so that grep only displays the filenames and not every line, cutting down on unwanted clutter when just the file name is wanted.

~~~
$ grep -r -l "Lucayans" written_2/
written_2/travel_guides/berlitz2/Bahamas-History.txt
~~~



### -c
What if we didn't need to know which lines the pattern is located in, but simply needed to know how many times the pattern appears in total? Once again, grep's default return behaviour doesn't quite suit our needs, as counting through every single line by hand for the pattern would be incredibly inefficient.

For example, an extremely common word like "the" would absolutely flood the terminal, and you probably wouldn't get much usable information out of your command. If we just wanted to know how many times "the" appears in a given file, we could more fittingly use:
~~~

~~~

If there are multiple files that contain the pattern, grep will show how many times the pattern appears in each individual file separately. I've cut down the below output to just the first few lines since it was actually still quite large:


For good measure, let's see how many times "Lucayans" appears in `Bahamas-History.txt`:
~~~
$ grep -r -c "Lucayans" written_2/travel_guides/berlitz2/Bahamas-History.txt
2
~~~

### -w
