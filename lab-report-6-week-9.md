
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
