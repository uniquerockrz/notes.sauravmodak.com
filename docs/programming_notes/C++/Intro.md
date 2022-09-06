---
sidebar_position: 1
---
# Intro

C++ is a compiled and systems language that is very useful for building systems and applications. My main motivation for learning C++ has been to master competitive programming. 

This is the most basic program in C++ which just prints Hello, World!

```cpp
#include <iostream>
using namespace std;
int main()
{
	cout << "Hello, World!" << endl;
	return 0;
}
```

To compile a C++ program, we have to first build it to run it. Building a program means to convert the human written source code to the executable code that a computer can understand. This is done using a compiler, and various IDEs have tools that can automate this process. 

Like some languages, the C++ program needs to have a `main()` function where the execution of the code starts. It also needs to return a value, and the standards say that main function should ideally return an int. 

We see two instructions in the above program, that is `cout` and `endl`. The `cout` is used for printing text to the standard output, which is usually the console, and the `endl` is used to end the line, which is same as adding a newline at the end of the string. 

## Variables

Like other languages, variables are store of data. C++ has a diverse set of data types which can be used to store different types of data. 

```cpp
#include <iostream>
using namespace std;

int main(int argc, char *argv[]) {
    string characterName = "John";
    int characterAge;
    characterAge = 70;

    cout << "There once was a man named " << characterName << endl;
    cout << "He was " << characterAge << " years old" << endl;
    cout << "He liked the name " << characterName << endl;
    cout << "But he did not like being " << characterAge << endl;
    return 0;
}
```

Here we are seeing a program that is using variables, two types specifically, strings and integers. We can declare variables and directly assign them, or we can declare the variable and assign it the value later, as shown in the `characterAge` example above. 

## Data Types

As discussed, these are some of the common data types used in C++.

```cpp
#include <iostream>

using namespace std;
int main(int argc, char *argv[]) {
    char grade = 'A';
    string phrase = "Hello, World!";
    int age = 32;
    double gpa = 7.2;
    bool isMale = true;
    
    return 0;
}
```

`char` are variables that hold a single character, `string` holds a bunch of characters, `int` stores whole numbers and `double` stores numbers with fractional points. Apart from that, there is a variable called `bool` which is boolean and stores boolean values, `true` and `false`.

Some other data types are also present in C++, namely `long` and `float`. 