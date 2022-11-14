# Lab Report 5

## Part 1
The task I will be choosing for Part 1 is:

- In DocSearchServer.java, change the name of the **start** parameter of **getFiles**, and all of its uses, to instead be called **base**.

After cloning the repository, changing to the correct directory and entering vim for DocSearchServer.java, 
type into the terminal "`/` `s` `t` `a` `r` `<Enter>` `c` `e` `b` `a` `s` `e` `<Esc>` `n` `.` `n` `.` `:` `w` `<Enter>`" 
for a total of 20 keystrokes.

Typing `/` `s` `t` `a` `r` moves your cursor to the first instance of "star":
![image](https://user-images.githubusercontent.com/114563712/201603351-a3df2011-b9a3-4c93-839a-ca121fc88ad0.png)

Typing `<Enter>` `c` `e` deletes the entirety of the first "start" and puts you into insert mode:
![image](https://user-images.githubusercontent.com/114563712/201603724-f24a43b5-1690-40e9-9d92-a1eadb3be0cd.png)

Typing `b` `a` `s` `e` `<Esc>` inserts the text "base" into vim:
![image](https://user-images.githubusercontent.com/114563712/201603875-b5251e5d-a2aa-4198-b77f-b35b9f1dd09e.png)

Typing `n` `.` moves to the next instance of "star" and 

repeats your `<Enter>` `c` `e` `b` `a` `s` `e` `<Esc>` actions (x2)and then your result should end up looking like this: 
![image](https://user-images.githubusercontent.com/114563712/201603028-3849494e-8aaa-4f12-8418-8dc0a6bb1696.png)


## Part 2 
- Once, start in Visual Studio Code and make the edit there, then scp the file to the remote server and run it there to confirm it works

Assuming that I already git cloned the repository, making the edit only took several seconds; however, using the scp command:
``scp -r /Users/alexn/Documents/Github/week6-skill-demo1 cs15lfa22hm@ieng6.ucsd.edu:~/`` had taken around 10-15 minutes, while running the test afterwards
took several seconds.

- Second, start already logged into a ssh session. Then, make the edit for the task you chose in Vim, then exit Vim and run bash test.sh.

Assuming that I already git cloned the repository, changing directories and entering vim only took several seconds. Also repeating the steps from Part 1
only took several seconds as well as I had practiced it many times over to ensure it was the shortest number of keystrokes I could have done. Then running the 
test after also only took a few seconds.

- Which of these two styles would you prefer using if you had to work on a program that you were running remotely, and why?

I believe more often than not I would rather work on the program locally and then scp it over because I still find it difficult to view and maneuver in vim.

- What about the project or task might factor into your decision one way or another? (If nothing would affect your decision, say so and why!)

If the project calls for writing everything about the program from scratch, then I would rather write with my own IDE and then scp it over. However, if the task
calls for making miniscule edits, I would rather just use the vim editor to quickly make those changes as needed.

# This concludes the lab report!
