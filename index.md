Name: Hargen Zheng\
PID: A17383701\
Sources: Week 2 Lab `NumberServer.java`, `Handler.class`, ad `URLHandler.class` files.\
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

+ Example 1. I want to start my lab report with some greetings, so I wanted to 
know how many lines of my `.txt` files in current working directory contain 
the word "Hello." I navigated different directories in `\written_2` and happened
to be at `\written_2\non-fiction\OUP\Berk`, so I want to start from there. 

By inspection, there are four `.txt` files in my current working directory -- 
`CH4.txt`, `ch1.txt`, `ch2.txt`, and `ch7.txt`. Let's try to see how many "Hello"
we have in `ch1.txt`! I think there will be some counts because it is the 
starting chapter and perhaps the author wants to say "Hello" as well! Here is 
my command and the corresponding output:
```ruby 
❯ grep -c "Hello" ch1.txt
0
```



# Option 2: `-n`

```ruby
❯ grep -n "Hello" *.txt
CH4.txt:69:Children’s earliest efforts at make-believe also reveal how challenging they ﬁnd the task of detaching thought from reality. Initially, object substitutions are closely tied to the real things they represent. Toddlers between ages 1 1/2 and 2 generally use only realistic-looking objects while pretending—a toy telephone to talk into or a cup to drink from.9 Once, I handed a 21-month-old a small wooden block, put another to my ear, and called her on the phone: “Ring! Ring! Hello, Lynnay!” She responded by throwing down the block and turning to another activity. Yet when given a plastic replica of a push-button phone, Lynnay readily put the receiver to her ear and pretended to converse.
CH4.txt:151:As children engage in play talk, they not only build their vocabularies but correct one another’s errors, either directly or by demonstrating the acceptable way to speak. In one instance, a kindergartner enacting a telephone conversation said, “Hello, come to my house, please.” Her play partner quickly countered with appropriate telephone greeting behavior: “No, ﬁrst you’ve got to say ‘How are you? What are you doing?’”28
```

---
This is the end of Lab Report 3.
Hargen Zheng

