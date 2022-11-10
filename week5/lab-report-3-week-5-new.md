# **Week 5 Lab Report** #
## By: Lorenzo Bato ##
*This report aims to documment interesting command-line options for the* `grep` *command This is all within a directory in an SSH account called* `skill-demo1/technical`.

## `-c`
*Syntax:*
```
grep -c "<<string>>" <<path>>
```
## Example 1
*Input:*
```
$ grep -c "TSA" 911report/*.txt
```
*Output:*
```
911report/chapter-1.txt:0
911report/chapter-10.txt:0
911report/chapter-11.txt:0
911report/chapter-12.txt:17
911report/chapter-13.1.txt:0
911report/chapter-13.2.txt:6
911report/chapter-13.3.txt:0
911report/chapter-13.4.txt:0
911report/chapter-13.5.txt:1
911report/chapter-2.txt:0
911report/chapter-3.txt:0
911report/chapter-5.txt:0
911report/chapter-6.txt:0
911report/chapter-7.txt:0
911report/chapter-8.txt:0
911report/chapter-9.txt:0
911report/preface.txt:0
```
In this example of `-c`, I used the string "TSA" in order to find the chapter where they specifically talk about the effects of 911 on national security. This command can be useful when isolating what specific topic is talked about in what specific text.
## Example 2
*Input:*
```
$ grep -c "Al Qaeda" 911report/chapter-13.4.txt
```
*Output:*
```
14
```
In this example, we isolate the `.txt` file we are searching in, which allows us to show the frequency of certain strings in the file. This command helps with quantifying information within a larger text
## Example 3
*Input:*
```
$ grep -c "Osama" 911report/*.txt
```
*Output:*
```
911report/chapter-1.txt:0
911report/chapter-10.txt:0
911report/chapter-11.txt:0
911report/chapter-12.txt:0
911report/chapter-13.1.txt:0
911report/chapter-13.2.txt:0
911report/chapter-13.3.txt:2
911report/chapter-13.4.txt:5
911report/chapter-13.5.txt:0
911report/chapter-2.txt:0
911report/chapter-3.txt:0
911report/chapter-5.txt:0
911report/chapter-6.txt:0
911report/chapter-7.txt:2
911report/chapter-8.txt:0
911report/chapter-9.txt:0
911report/preface.txt:0
```
In this example, I wanted to find references to a certain person. This command can be useful when looking to reference, cite, or otherwise recall pieces of information in larger texts

## `-h`
*Syntax:*
```
grep -h "<<string>>" <<path>>
```
## Example 1
*Input:*
```
grep -h "9/11" 911report/preface.txt
```
*Output:*
![Image](grep-h1.png "pic1")
In this example, the command actually printed out the lines from within the text and highlights them. This is useful visually, as the highlight helps with specifying where the specific keyword is.
## Example 2
*Input:*
```
grep -h '\$' government/Media/Abuse_penalties.txt
```
*Output:*
![Image](grep-h2.png "pic2")
For this example, we used a trick to find monetary values. The keyword is input differently because "$" (dollar sign) is actually a special character. To denote that we want to actually search for a dollar sign, we use `'\$'` to specify that. This command is also prints out the line of the highlight, so we can discern whether we want to look for fines, grants, cost, etc. from using the provided context
## Example 3
*Input:*
```
 grep -h 200* plos/pmed.0020023.txt
```
*Output:*
![Image](grep-h3.png "pic3")
This command, in combination with the properties of `*`, was used to find statistics and their years. It can be useful when highlighting patterns we are searching for when we traditionally use `grep`, and its nature allows that information to be contextualized.

## `-l`
*Syntax:*
```
$ grep -l "<<string>>" <<path>>
```
## Example 1
*Input:*
```
$ grep -l "Al Qaeda" 911report/*.txt
```
*Output:*
```
911report/chapter-1.txt
911report/chapter-10.txt
911report/chapter-11.txt
911report/chapter-12.txt
911report/chapter-13.3.txt
911report/chapter-13.4.txt
911report/chapter-13.5.txt
911report/chapter-2.txt
911report/chapter-5.txt
911report/chapter-6.txt
911report/chapter-7.txt
911report/chapter-8.txt
```
In this example, we print out ever `.txt` file in `911report` that contains that string. This differs from `-c` as `-c` will still print out those with 0 instances of the string. `-l` seems useful for when dealing with paths, as the listed paths can then be used in succeeding commands.
## Example 2
*Input:*
```
 grep -l "FBI" government/*/*.txt
```
*Output:*
```
government/Gen_Account_Office/Testimony_Jul15-2002_d02940t.txt
government/Gen_Account_Office/Testimony_Jul17-2002_d02957t.txt
government/Media/Raising_the_Bar.txt
```

In this example, our goal was to look for all instances of where "FBI" was mentioned. This is useful for narrowing down what `.txt` files were relevent to the keyword given.
## Example 3
*Input:*
```
grep -l "product manufacturing" plos/pmed*.txt
```
*Output:*
```
pmed.0020035.txt
```
In this example, we wanted to find a mention of "product" manufacturing, but only within the file with the pretext of `pmed`. This command, in tandem with `*`, allows us to isolate files with instances of our keyword, but also control where we are searching, so that it does not just print out irrelevent files that also contain that keyword.