---
layout: post
title:      "HOW TO SOLVE A LAB IN FIRST MILE?!"
date:       2020-08-19 05:57:21 -0400
permalink:  how_to_solve_a_lab_in_first_mile
---


This is a challenge. It is different for everyone. The way I go about solving labs is creating notes in the file of what the lab is asking me to do, as I read through it the first time. As I am trying to translate that into code the computer can understand. I have an idea of what it's asking me to do. I can then reference the readme file, as I am working the code. 

Once, I have a generic layout of what it is asking me to do. I run learn with every addition to the code. Making sure that the tests are spelled correctly even if it has errors and a letter isn't capitalized but you know it should be. Because, the tests for learn are extremely finicky. They will fail if you miss a period. So, if it says a method is supposed to return

` "Hello #{name}. How are you doing in class today?"`

and you put 

`"Hello #{name} How are you doing in class today"`

The test will fail because you don't have a period after `#{name} && ?` after today.

An advanced note:
If you have a long string and you want to break it up into multiple lines. I suggest using 
`string name = <<END` this will create a string until the word END is seen again in the code.

Example:
```poem = <<END

\tThe lovely world
with logic so firmly planted
cannot discern \n the needs of love 
nor comprehend passion from intuition
and require an explanation
\n\t\twhere there is none.
END``` "This word can be anything"

This is an example from the book Ruby The Hard Way. Lesson 24.rb.
I highly suggest reading this book and doing some or all of the lessons if you find your self looking for some extra practice.

To distinguish the 'here doc operator' an arbitrary String delimiter has to immediately follow the '<<'. Everything inbetween that initial delimiter and the second occurrence of that same delimiter will be part of the final string. It is also possible to use '<<-', the difference is that using the latter will ignore any leading or trailing whitespace.

In the poem string it also uses \n, \t. 
\n creates a linebreak. 
\t tabs in the line.

The following commands are used in the terminal to test and submit your labs. 
learn is used to test the labs. Make sure to save your file before running learn. This can be done using command S. Once you have all labs passing you would type the learn submit command into the terminal. If you want to test the file without submitting it. I recommend saving the file. Going into the directory where the file is located using cd - change directory. pwd - print working directory, and ls - list the files in the directory.

pwd to find out what directory your currently in.

Then, go to the directory that contains your file.

#Where you keep your lab files
cd Flatiron\ code/ 
#Use this to print a list of files in the directory
ls
#The list of files in that directory
filename.rb filename.rb and so on...
#Once, you find the file you want to run in the directory. Run this in the terminal
ruby filename.rb

Then the file will run in the terminal. If you have properly setup the file. If not take it one step at a time and work through the error messages they are their to help you. Become one with them. I know they seem overwhelming, but they are your friend. After, you have spent several minutes on it and tried to work through it on your own. You have researched, went through your notes, used google to its fullest and you still cant seem to get the tests to pass. ASK A QUESTION. In the slack community. on the learn.co page. Reach out. Someone is willing and able to help. FInd a partner and start a Zoom chat. Working with others is a great way to talk it out. Explaining it to someone helps to help you understand it better. 

Well I hope you found something useful in this blog. I will be updateing it as I go through the course. Good luck to everyone. Have fun, the challenge is real but totally do able. Don't forget NO question is a dumb question! We all look at things differently and sometimes we just need to work together.
