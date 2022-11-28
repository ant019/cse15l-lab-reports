
# Lab Report 6

## Auto Grader Code

```
CPATH=.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar
set -e
rm -rf student-submission
git clone $1 student-submission
if [[ -f student-submission/"ListExamples.java" ]]; then
        echo "FOUND: student-submission/ListExamples.java"
        cp -v student-submission/ListExamples.java ListExamples.java
        set +e
        echo "Compiling"
        javac -cp $CPATH *.java 2> compile.log
        if [[ $? != 0 ]]; then
                echo "Compile Test Failed"
                cat compile.log >/dev/stderr
                echo "See compile.log for result."
                exit
        else
                echo "Compilation Succeeded!";
                echo "Running tests";
                java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > run.log
                if [[ $? != 0 ]]; then
                        echo "Run Tests failed."
                        cat run.log >/dev/stderr
                        echo "See run.log for result"
                        FAILED=`grep "Tests run" run.log | awk '{print $5}' | cut -c 1`                        
                        TOTAL=`grep "Tests run" run.log | awk '{print $3}' | cut -c 1`
                        echo "Score: $FAILED/$TOTAL"
                else
                        echo "Run Tests passed."
                        echo "Score: 3/3" 
                        exit
                fi
        fi
else
        echo "ERROR: ListExamples.java does not exist." >/dev/stderr
        exit
fi
```

## Grader Examples

### Example 1

Tested using https://github.com/ucsd-cse15l-f22/list-methods-corrected
![image](https://user-images.githubusercontent.com/114563712/204357612-593e9cb7-2409-49e0-aaab-08baf575e440.png)

### Example 2

Tested using https://github.com/ucsd-cse15l-f22/list-methods-lab3
![image](https://user-images.githubusercontent.com/114563712/204357710-58a99e50-082f-47a6-94eb-508b9e2f7e1b.png)

### Example 3

Tested using https://github.com/ucsd-cse15l-f22/list-methods-signature
![image](https://user-images.githubusercontent.com/114563712/204357789-866a655e-1b23-45d8-84fb-ccd4badf366c.png)

## Tracing

I will trace what my code did in example 1.
Line 1 of my code sets a variable for the classpath for JUnit `CPATH=.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar` and the exit code for this is 0.
Line 2 of the code is `set -e` which forces the script to exit if there is a non-zero exit code, and the exit code for this is 0. Next, we use 
`rm -rf student-submission`, which recursively removes all the files of inside the directory, the exit code for this is always 0. After, we use 
`git clone $1 student-submission` to clone the file into the directory student-submission,the exit code for this is 0. Next, we check if the ListExamples.java
exists inside the student-submission directory, and here it returns true, the exit code is 0. After this, we have an echo statement
`"FOUND: student-submission/ListExamples.java"` which has an exit code of 0. Next, we copy ListExamples.java to the current directory,
which has an exit code of 0. On line 8, we run the command `set +e` which will cause the script to ignore any non-zero exit code, 
the exit code for this is 0. The purpose of this is to grade files that may have errors in it. Next, we echo the line `"Compiling"`, this has an exit code of 0.
After, we compile the program and the tests, and send any stderr output to the compile.log file using javac `-cp $CPATH *.java 2> compile.log`, 
this has an exit code of 0. Next, we run `if [[ $? != 0 ]]; then`, which checks if the compile succeeded using the exit code of the last command. Since the
javac command did not have an exit code of 0, the next four lines are not run. On lines 17 & 18, echo commands are displayed to show the status of compilation,
the exit code of this is 0. Next, we run the line `java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > run.log`, which runs the JUnit tests on
the new program, this exit code for this is 1. After, we check the exit code of the previous command again, since it is not 0, the if statement continues.
On line 21, we echo `"Run Tests failed."`, which has an exit code of 0. Next, we print the run.log file to stderr, which has an exit code of 0. The line after
this is another echo command, which has an exit code of 0. On lines 24 and 25, we the commands `grep`, `awk`, and `cut` on the run.log file to get the number
of tests failed, which has an output of 1, and then the total number of tests run, which has an output of 3. The rest of the code do not run due to the if
statement.

