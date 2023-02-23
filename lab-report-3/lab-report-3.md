Name: Hargen Zheng\
PID: A17383701\
Sources: [geeksforgeeks](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)

Lab Session: Wednesday 11:00 - 12:50 @EBU3B_B270

# Lab Report 3
Welcome to my lab report 3 webpage. In this lab report, we will explore four 
command-line options for the command `grep`. Each option is followed by two
examples to demonstrate its use and output. Without further due, let's start
the lab report!

# Option 1: `-c`
When dealing with a huge amount of `.txt` files, we may want to know how many
times a specific pattern -- words, phrases, or even sentences -- appear in our
files. Therefore, we can do further analysis with our `.txt` file. `grep` has
`-c` command-line option that enables us to count the number of lines that the 
pattern appear, which would give us a general sense of how frequent the pattern
appears in our file(s).

+ Example 1.

I want to start my lab report with some greetings, so I wanted to 
know how many lines of my `.txt` files in current working directory contain 
the word "Hello." I navigated different directories in `\written_2` and happened
to be at `\written_2\non-fiction\OUP\Berk`, so I want to start from there. 

By inspection, there are four `.txt` files in my current working directory -- 
`CH4.txt`, `ch1.txt`, `ch2.txt`, and `ch7.txt`. Let's try to see how many "Hello"
we have in `ch1.txt`! I think there will be some counts because it is the 
starting chapter and perhaps the characters wants to say "Hello" to each other
as well! Here is my command and the corresponding output:
```ruby 
❯ grep -c "Hello" ch1.txt
0
```

+ Example 2.

Unfortunately, the characters do not seem to greet each other with the word
"Hello" as we wanted, and we obtained an output of zero here. What about the
other `.txt` files in the directory? Let's try to apply the command to all 
`.txt` files in the directory and see if even a single line of all `.txt` files
would contain "Hello".
```ruby
❯  grep -c "Hello" *.txt
CH4.txt:2
ch1.txt:0
ch2.txt:0
ch7.txt:0
```

Yes! We finally find out that two lines of `CH4.txt` file contains the word 
"Hello". Maybe it's because characters meet with each other late in the fourth
chapter. But the count 2 is all we can get as of now. We want to use other
command-line options to further explore the context in the file.

# Option 2: `-l`
Before we could delve into the contextual information, it seems we are displaying useless information in our output. We do not want to see these 0 counts when the number of files grows huge. We just cannot immediate identify which files would contain the pattern we want. The option `-l` comes in handy as it displays only the file names that contain the phrase we want to search. 

+ Example 1.

We try to see how many files in our working directory (the same as previous command-line option) contain the word "Hello".
```ruby
❯ grep -l Hello *.txt
CH4.txt
```
As expected, we are only getting one single output because, as we see in previous examples, only the file `CH4.txt` contains 2 lines of "Hello". We are done with the first exploratory example.

+ Example 2.

Let's now search and see how many files contain the word "today".
```ruby
❯ grep -l today *.txt
CH4.txt
ch1.txt
ch2.txt
ch7.txt
```
It seems "today" appears at least once in each of the file in our working directory. Let's dig deeper into the file with other commands now!


# Option 3: `-h`
+ Example 1.

Upon checking the other command-line options for `grep`, I noticed that there is an option `-h` that could display the matched lines. Building on previous commands, let's see the lines that contain the word "Hello" first.
```ruby
❯ grep -h Hello *.txt
Children’s earliest efforts at make-believe also reveal how challenging they ﬁnd the task of detaching thought from reality. Initially, object substitutions are closely tied to the real things they represent. Toddlers between ages 1 1/2 and 2 generally use only realistic-looking objects while pretending—a toy telephone to talk into or a cup to drink from.9 Once, I handed a 21-month-old a small wooden block, put another to my ear, and called her on the phone: “Ring! Ring! Hello, Lynnay!” She responded by throwing down the block and turning to another activity. Yet when given a plastic replica of a push-button phone, Lynnay readily put the receiver to her ear and pretended to converse.
As children engage in play talk, they not only build their vocabularies but correct one another’s errors, either directly or by demonstrating the acceptable way to speak. In one instance, a kindergartner enacting a telephone conversation said, “Hello, come to my house, please.” Her play partner quickly countered with appropriate telephone greeting behavior: “No, ﬁrst you’ve got to say ‘How are you? What are you doing?’”28
```
As we expect, there are two "Hello" appearing in our text -- "Hello, Lynnay!" and "Hello, come to my house, please." 

+ Example 2.

Let's now try to see how the word "today" appear in the context of the files. Since all four files contain the word, we try to count the number of appearance of the word to avoid long output. 
```ruby
❯ grep -c today *.txt
CH4.txt:2
ch1.txt:4
ch2.txt:5
ch7.txt:3
```
The file `CH4.txt` contains the least "Today." Since we have did some analysis with the word "Hello," let's try to see how "today" appears in `ch7.txt` in this example.

```ruby
❯ grep -h today ch7.txt
In this chapter, I take up dilemmas that today’s parents face in rearing young children. Throughout this book, we have touched on myriad forces that make contemporary parenting highly challenging. These include one-sided, contradictory messages in the parenting-advice literature; career pressures that impinge on parent involvement in children’s lives; abysmally weak American child-care services to assist employed parents in their child-rearing roles; cultural violence and excessive materialism permeating children’s worlds; schools with less than optimal conditions for children’s learning; and impediments to granting children with deﬁcits and disabilities social experiences that maximize their development. 
I intend these answers to parents’ questions to reﬂect a way of thinking about child rearing, not a set of recipes for dealing with speciﬁc events. When parents are familiar with principles that are grounded in contemporary theory and research on children’s development, they can better deal with the quandaries generated by the changing home, school, and community contexts in which today’s children grow up. Although adverse cultural trends have complicated and threatened good child rearing, parents—as agents of change, buffers against stressful life circumstances, and gatekeepers of learning opportunities—can do much to protect, restore, and reshape children’s experiences.
The typical preschool child devotes nearly 13 percent of his or her waking hours to watching television, a ﬁgure that rises to 30 percent by school age. Clearly today’s children spend far too many hours in front of the TV set, a circumstance that restricts time available for joint parent–child activities, play, reading, and other worthwhile pursuits. Television is so pervasive an inﬂuence in children’s lives that I discussed it at length in Chapter 2.
```
As with the output, "today" is used twice before the word "Children" and once before the word "parents" in the text.


# Option 4: `-n`
We can use the command options to find the information we want, but it takes some time to check if the word/pattern we want is indeed there. How can we use command-line options to locate the output faster -- to spend less time on and protect our eyes? Well, it seems the option `-n` would be good because it tells us the line number of that matching! We can go directly to the line and see if the word is there, instead of skimming through the whole text and find nothing at the end.

Let's try our first example with the word "Hello" again.

+ Example 1.
```ruby
❯ grep -n Hello CH4.txt
69:Children’s earliest efforts at make-believe also reveal how challenging they ﬁnd the task of detaching thought from reality. Initially, object substitutions are closely tied to the real things they represent. Toddlers between ages 1 1/2 and 2 generally use only realistic-looking objects while pretending—a toy telephone to talk into or a cup to drink from.9 Once, I handed a 21-month-old a small wooden block, put another to my ear, and called her on the phone: “Ring! Ring! Hello, Lynnay!” She responded by throwing down the block and turning to another activity. Yet when given a plastic replica of a push-button phone, Lynnay readily put the receiver to her ear and pretended to converse.
151:As children engage in play talk, they not only build their vocabularies but correct one another’s errors, either directly or by demonstrating the acceptable way to speak. In one instance, a kindergartner enacting a telephone conversation said, “Hello, come to my house, please.” Her play partner quickly countered with appropriate telephone greeting behavior: “No, ﬁrst you’ve got to say ‘How are you? What are you doing?’”28
```
The line numbers are there. We can quickly open the text and locate the word faster than before. What about the word "today"? Let's see in the second example!

+ Example 2.
```ruby
❯ grep -n today ch7.txt
5:In this chapter, I take up dilemmas that today’s parents face in rearing young children. Throughout this book, we have touched on myriad forces that make contemporary parenting highly challenging. These include one-sided, contradictory messages in the parenting-advice literature; career pressures that impinge on parent involvement in children’s lives; abysmally weak American child-care services to assist employed parents in their child-rearing roles; cultural violence and excessive materialism permeating children’s worlds; schools with less than optimal conditions for children’s learning; and impediments to granting children with deﬁcits and disabilities social experiences that maximize their development. 
8:I intend these answers to parents’ questions to reﬂect a way of thinking about child rearing, not a set of recipes for dealing with speciﬁc events. When parents are familiar with principles that are grounded in contemporary theory and research on children’s development, they can better deal with the quandaries generated by the changing home, school, and community contexts in which today’s children grow up. Although adverse cultural trends have complicated and threatened good child rearing, parents—as agents of change, buffers against stressful life circumstances, and gatekeepers of learning opportunities—can do much to protect, restore, and reshape children’s experiences.
28:The typical preschool child devotes nearly 13 percent of his or her waking hours to watching television, a ﬁgure that rises to 30 percent by school age. Clearly today’s children spend far too many hours in front of the TV set, a circumstance that restricts time available for joint parent–child activities, play, reading, and other worthwhile pursuits. Television is so pervasive an inﬂuence in children’s lives that I discussed it at length in Chapter 2.
```
Again, we can use the line numbers to refer back to the text and locate the word(s) of our interest.

---

With all these words and examples, we have explored some command-line options for the command `grep`. 

This is the end of Lab Report 3.\
Hargen Zheng

