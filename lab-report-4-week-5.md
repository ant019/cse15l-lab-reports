# Lab Report 4
For this lab report, I have the opportunity to choose between ``less, find, and grep`` to observe 3 command-
line options. For my lab report, I have chosen the ``less`` command.

## The Less Command
The less command is interesting as it allows you to view files directly from your terminal with several options
for navigation and editing. You can also input commands while viewing files, which I believe can be handy, such
as searching for another term while viewing the file. The 3 command-line options that I chose that I think would
be helpful to know are the ``-p, -W, and -X,``In my examples for these commands, I will not be using code blocks as 
they cannot show the things that make these commands stand out. Also for these examples, I will also be starting in 
the biomed directory within technical.

### -p(pattern)
First off, we have the ``-p(pattern)`` option, which will highlight and search for the first term that has the pattern in the
file. For instance, if we input ``less -psmallpox 1471-2334-3-9.txt`` into the terminal (starting from the biomed
directory in technical), we would get:
![image](https://user-images.githubusercontent.com/114563712/198921723-1b17364f-33df-417c-9bf8-7851585496c7.png)

Furthermore, while we are viewing this file, we are able to use the pattern options from within, so if we type
``/cells`` and hit enter the command would search for and highlight anything that has cells in it. 
![image](https://user-images.githubusercontent.com/114563712/198922271-bc10462e-554f-40c0-a3c2-1d8b1f4cf711.png)

However, the ``/pattern`` command only searches forwards, so in order to search backwards we can use the ``?pattern``
command. So if we type ``?pox`` and press ``g`` to move back to the start of the file, we would get:
![image](https://user-images.githubusercontent.com/114563712/198922409-41e952c4-20fe-4010-8683-186e3cdffa25.png)

Here are some examples of me just using the ``-p(pattern)`` option:
#### Example 1
``less -ppharmacokinetic 1471-2334-3-10.txt``
![image](https://user-images.githubusercontent.com/114563712/198923466-cff3c579-a3c0-445e-86f0-9be763e2dcea.png)

Here the command takes you to the first line where pharmacokinetic appears and highlights all the terms that contain 
it, which is handy as it helps me look more specifically for the terms I want.

#### Example 2
``less -phospital 1471-2334-3-11.txt``
![image](https://user-images.githubusercontent.com/114563712/198923755-2b1eb242-e654-4c35-acf7-3e2cafa6df0e.png)

Here the command takes you to the first line where hospital appears and highlights all the terms that contain 
it, which is handy as it helps me look more specifically for the terms I want.

#### Example 3
``less -pHPV 1471-2334-3-12.txt``
![image](https://user-images.githubusercontent.com/114563712/198923973-a3cfc223-35b6-4d6e-b378-b295d6a79f44.png)

Here the command takes you to the first line where HPV appears and highlights all the terms that contain 
it, which is handy as it helps me look more specifically for the terms I want.


### -W
Next, we have the ``-W`` option, which highlights the entire first line everytime you move in the file by an entire window.
This is handy to have as you can keep track of where you are in the text if you keep jumping around in the file. 

Here are some examples of me just using the ``-W`` option (in these examples I will be moving a window down by pressing
``SPACE`` for the highlight to work):
#### Example 1
``less -W 1471-2334-3-10.txt`` + ``SPACE``
![image](https://user-images.githubusercontent.com/114563712/198924584-e7fd22ca-d803-4944-a694-6bbf2377ec8d.png)

Here the command highlighted the first line of the next window in my terminal:``patients [ 11 ] . In a 64-week trial in treatment-na<C3><AF>ve``,
which is handy as it shows where I am in the file.


#### Example 2
``less -W 1471-2334-3-11.txt``+ ``SPACE``
![image](https://user-images.githubusercontent.com/114563712/198924832-c8d33c4c-5bab-418a-a6ba-f983f490ce03.png)

Here the command highlighted the first line of the next window in my terminal:``costing as much as 20 times outpatient antimicrobial``,
which is handy as it shows where I am in the file.

#### Example 3
``less -W 1471-2334-3-12.txt`` + ``SPACE``
![image](https://user-images.githubusercontent.com/114563712/198924911-b1205ede-618c-4443-a2bc-f691185aeaf9.png)

Here the command highlighted the first line of the next window in my terminal:``automated device that would eliminate laborious, and time``,
which is handy as it shows where I am in the file.


### -X
For our third command-line option, we have the ``-X`` option, which will leave the file you were viewing after you exited
the less command viewer. I believe this would be handy as you would not have to re-enter the viewing mode to see
the file from the terminal. For my examples, I will be using ``q`` to exit out of the viewing mode for less, you will
notice that, instead of the usual colon or file name, you will see the text [cs15lfa22hm@ieng6-203]:biomed:XXX$, where
the XXX is the command number. This means that I am currently not viewing the file and can input another command that
is not a part of ``less``.

Here are some examples of me just using the ``-X`` option:
#### Example 1
``less -X 1471-2334-3-10.txt`` + ``q``
![image](https://user-images.githubusercontent.com/114563712/198925286-0b9bcd0f-8fb0-4763-8304-6667680e1b40.png)

Here the command kept the view the ``less`` command provided even after exiting the ``less`` command, which is handy
as I can use other commands while still seeing what the text was about.

#### Example 2
``less -X 1471-2334-3-11.txt`` + ``q``
![image](https://user-images.githubusercontent.com/114563712/198925576-45fa7817-17d8-4bc3-93e0-863816caeecf.png)

Here the command kept the view the ``less`` command provided even after exiting the ``less`` command, which is handy
as I can use other commands while still seeing what the text was about.


#### Example 3
``less -X 1471-2334-3-12.txt`` + ``q``
![image](https://user-images.githubusercontent.com/114563712/198925626-2e9e934e-e680-41da-9f47-b06fb87e2c1e.png)

Here the command kept the view the ``less`` command provided even after exiting the ``less`` command, which is handy
as I can use other commands while still seeing what the text was about.


# This Concludes the Lab Report!
