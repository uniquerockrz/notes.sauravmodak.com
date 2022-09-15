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

The first text we see in the program is called `#include` which is a statement to include header files into the program. In simple words what it basically does is copies all the source code of the `iostream` file into our program. We are using two functions from those header files, the `cout` and the `endl`.

C++ also has these concept of namespaces, which you can think of as referring several functions together. We are using the namespace `std` here, which allows us to call the `cout` and `endl` directly, without referring them as `std::cout` and `std::endl`.

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

## Constants

We can use the `const` keyword to declare constants. Since constants cannot be changed, trying to change them will result in an error. 

```cpp
#include <iostream>

using namespace std;
int main(int argc, char *argv[]) {
    const int number = 20;
    cout << "Number is " << number << endl;
}
```

## Comments & White Spaces

C++ comments can be single line with `//` and multiline with `/*  */`. The compiler also ignores whitespaces and indentations. You can use comments, whitespaces and indents to make the code more readable. 

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

## Strings

You can use a number of functions with strings. Some of them are demonstrated below:

```cpp
#include <iostream>

using namespace std;
int main(int argc, char *argv[]) {
    string phrase = "Saurav Modak";
    
    cout << "Length: " << phrase.length() << endl;
    cout << "Index: " << phrase[0] << endl;
    phrase[0] = 's';
    cout << "Modifying: " << phrase << endl;
    cout << "Find: " << phrase.find("au", 0) << " " << phrase.find("ag", 0) << endl;
    cout << "Subtring: " << phrase.substr(1, 3) << endl;
}
```

Like most languages, indexing starts from zero. You can also modify the string on the fly using indexes. The `find` function finds a substring in string, and the `substr` function finds a substring in string. It takes two arguments, the index to start with and the length of the substring. 

## Math Functions

C++ supports basic math functions by default. However, you can use the `cmath` library to access more range of math functions. 

```cpp
#include <iostream>
#include <cmath>

using namespace std;
int main(int argc, char *argv[]) {
    cout << 1.3 + 2.5 << endl;
    cout << 5 % 3 << endl;
    cout << 5 / 0 << endl;
    cout << 5 / 3 << endl;
    cout << 5.0 / 3 << endl;
    
    cout << pow(2, 5) << endl;
    cout << sqrt(2) << endl;
    cout << round(3.5) << endl;
    cout << ceil(3.5) << endl;
    cout << floor(3.5) << endl;
    cout << fmax(3, 5) << endl;
    cout << fmin(3, 5) << endl;
    
    float a = 1.4149;
    double b = 4567.8954321;
    
    cout.precision(2);
    cout << std::fixed << a << endl;
    cout.precision(1);
    cout << std::scientific << b << endl;
    
    return 0;
}
```

Note that dividing between an integer and integer always returns an integer, even when that's not the correct answer. However, when a double is introduced, it returns a double. 

You can use the `precision()` method to set the precision while printing out a float or double. There are two ways to print these. The first is the fixed notation, and the second is the scientific notion which converts the variable to base 10 raised to the power. 

In fixed notation, the precision controls the number of digits to be printed after the decimal. In scientific notation, it controls the number of digits before the `e` in scientific notation. 

## User Input

User input is usually taken using the `cin` statement, which is opposite of what `cout` does. 

```cpp
#include <iostream>

using namespace std;
int main(int argc, char *argv[]) {
    int age;
    string name;
    
    cout << "Enter your age: ";
    cin >> age;
    cout << "You are " << age << " years old." << endl;
    
    cout << "Enter your name: " << endl;
    cin.ignore(256, '\n');
    getline(cin, name);
    cout << "Hello " << name << "!" << endl;
}
```

However, remember to use `getline()` to get strings. There is a caveat though. This function doesn't work that well with the `<<` operator. When you enter a ext and press enter, the newline character stays in the buffer. If you use `getline()`, the newline character will just get into the variable and you will not be able to get any usable user input. 

To prevent that, we use `cin.ignore()`. It Takes two arguments, the number of characters to ignore and the character that terminates the ignore. 

## Arrays

Arrays are one of the most fundamental data types that can be used to store a list of data. In C++ though, all the elements of the array has to be of the same type. 

You can declare array either by giving it's size, or directly assigning elements to it. 

```cpp
int numbers[20]; // 20 integers
int nums[] = {1, 2, 3, 4}; // 4 integers
```

Like other languages, arrays can be modified using their index and also accessed using it. 

```cpp
#include <iostream>

using namespace std;
int main(int argc, char *argv[]) {
    int numbers[] = {1, 2, 3, 4};
    
    cout << numbers[2] << endl;
    numbers[2] = 23;
    cout << numbers[2] << endl;
    
}
```

## Functions

Like other languages, in C++, functions are a group of statement that are run together. They are declared using the `function` keyword. You can pass parameters and also return values from it. 

```cpp
#include <iostream>
using namespace std;
void sayHi(string name);

int main(int argc, char *argv[]) {
    sayHi("Saurav");
    
    return 0;
}

void sayHi(string name) {
    cout << "Hi! " << name << endl;
}
```

In the above example, we also have created a function stub, which declares the function at the top of the file. This is useful in case we need to access the function from `main()` but it is actually declared after `main()`.

Incase the function doesn't return anything, we can use `void` else we can have the data type to return. 

```cpp
#include <iostream>
using namespace std;

double cube(double num){
    double result = num * num * num;
    return result;
}

int main(int argc, char *argv[]) {
    cout << "Cube of 5 is " << cube(5) << endl;
}
```

