# Week 8 Lab Report #
## *By: Lorenzo Bato* ## 
# Code #
```
set -e

rm -rf student-submission
rm-f printout.txt
git clone $1 student-submission
score=0

CPATH=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

cp TestListExamples.java student-submission
cp -r lib student-submission
cp StringThing.java student-submission

cd student-submission
if [[ -e ListExamples.java ]]
then
    echo "File is found in repository"
else
    echo "File is not found in repository. 0/2"
    exit 1
fi

if javac -cp $CPATH *.java
then
    echo "ListExamples.java compiled"
else
    echo "ListExamples.java did not compile. 0/2"
    exit 1
fi

java -cp $CPATH orgjunit.runner.JUnitCore TestListExamples > printout.txt

echo "Analyzing merge..."
if [ $(grep -c "testMerge" printout.txt) -ne 0 ]
then
    echo "testMerge Failed!"
else
    let "score+=1"
    echo "testMerge passed!"
fi

echo "Analyzing filter..."
if [ $(grep -c "testFilter" printout.txt) -ne 0 ]
then
    echo "testFilter Failed!"
else
    let "score+=1"
    echo "testFilter passed!"
fi

if [ $score -eq 2 ]
then
    echo "Score: [2/2]"
    echo "Autograder passed"
fi
if [ $score -eq 1 ]
then
    echo "Score: [1/2]"
    echo "Check failed test methods above"
fi
if [ $score -eq 0 ]
then
    echo "Score [0/2]"
    echo "Check failed tests or compile"
fi
```