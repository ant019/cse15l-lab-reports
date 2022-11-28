# Lab Report 6

## Auto Grader Code
```CPATH=.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar
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
fi```
