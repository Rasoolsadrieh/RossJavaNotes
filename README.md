# RossJavaNotes
# Java Overview

## Basics

-   Java is a popular programming langauge, that was created in 1995
-   Has a huge community for support and millions developers use it
-   Java it is an **\*object oriented programming(OOPs)** languaged gices a clear structure to programs and allows code to be reused lowering development costs
-   Java is close to C++ and C#, easy to swap betweent the two
-   **Platform Independence**
    -   Windows, Unix, Linux, MacOS
    -   **Write Once Run Anywhere (WORA)**
        -   programmers can delveop code on one system and can expect it to run on any toher Java-enabled systsm w/o any adjustments
-   **STrictly Typed**
    -   data types must be define during declaration and on implementation
-   **High Level Language**
    -   Memory is handled automatically **Garbage collection**
        -   finds unused objects and deletes them to free up memory
-   **Verbose Language**
    -   writting a lot of code to make sure things compile correctly
-   **Compiled** Language
    -   Converted directly into machine code that the processor can execute
    -   Tend to be faster and more efficient to execute than interpreted language
    -   need to build and rebuild for every change
-   **Multi-paradigmed**Language
    -   Primarily OOP
    -   In the newer version of Java, the language does support declarative syntax
    -   make java flexible

## JVM vs JRE vs JDK

-   Bytecode is used to send these compiled java programs
    -   **OS cannot read the bytecodde**
        -   JVMs for each OS convert the bytecode to machine code
    -   TWOS:
        -   Compilation:
            -   converts the java code to bytecode
        -   Execution:
            -   JVM converts the bytecode into the OS machine code for execution

![Bytecode Conversion](https://static.javatpoint.com/blog/images/java-bytecode.png)

-   **JVM**
    -   Java Virtual Machine
    -   translates bytecode to machine code
    -   executes it
-   **JRE**
    -   Java Runtime Environment
    -   needed to run Java Application
    -   JVM + Core Libraries + Other components (in-built Java Classes)
-   **JDK**
    -   Java Development Toolkit
    -   Need to create and run java Applications
    -   JRE + Compilers + Debuggers + other useful stuff

![JVM vs JRE vs JDK](https://miro.medium.com/max/636/1*8oNn6HxcWFmrCsgUt27k0w.jpeg)

## Main Method

-   _Significance_
    -   Main method is the entry point for ANY java program
    -   Typically thess are in:
        -   Driver.java, MainDriver.java, Runner.java
    -   Whenever we run our java code, the JVM searches for the main method with the correct type **signature**
-   **Signature**
    -   public static void main(String[] args)
        -   Alternative, but valid and rarely used signature:
            -   public static void main(String... args)
-   If the JVM cannot find the main method in the java source file then it will either:
    -   not execute at all
    -   or throw a runtime error

# Expressions

-   **Operators**
    -   \+ addition
    -   \- subtraction
    -   \* multiplication
    -   / division
    -   % modulus (remainder)
-   **Operants** or **Literals**
    -   values that don't change, it is consistent and remains the same where present
    -   numbers
-   PEMDAS

```java
5 ** 6 // Expected: Illegal expression

5 / 2 // Expect: 2.5
// Output: 2

5.0 / 2.0 // Expect: 2.5
// Output: 2.5

5 + 5 * 6 //
// 35

(5 - 2) * 2 //
// 6

5 + "2" + 10 // Expect 17 String type coercion plays a roll in the output
// 5210
```

# Syntax

-   Computers understandd the commnads you give them by the appropriate syntax for the specific language
-   **Statements**
    -   Instructions for the computer to execute some command/method
    -   Example: System.out.println("Hello World");
-   **Method call**
    -   System.out._println();_
        -   invocates the println function of the out variable
-   **Variable of the class**
    -   System._out_.println();
-   **Class**
    -   _System_.out.println();

## Console output

```java
// Print Hello World to command line
System.out.println("Hello World")

// Print 5 * 3 as in
System.out.println("5 * 3")

// Print Calculated value of 5 * 3
System.out.println(5 * 3)

// Print equation and calculated result for number of seconds in a day
// Exmaple of String interpolation and Type Coercion
System.out.println("5 * 3 = " + 5 * 3)
// output: "5 * 3 = 15"

// %(character) is a formatt specifier
System.out.printf("%s %d", "5 * 3 =", 5 * 3);
// output: "5 * 3 = 15"

System.out.println("Hello " World"")
// Output: Error

System.out.println("Hello \"World\"") // \ is used to "escape" characters to the program reads them as their literal value
// Output: Hello "World"

System.out.println("Hello \nWorld") // \n is used to include a new line in the output
// Output: Hello
//         World
```

# Variables

-   Something whos value _can_ change over the life of a program

```java
int number = 12;
String name = "Charles";

int number2; // default declaration 0
String lname; // Default to null
```

-   Declaration of the variable is when it's first declared
-   Reassign is when you change the contents of that variable

```java

int num1 = 5;
int num2 = 10;
int int1 = 10;

num2 = 11;
num2 += 11; // num2 is now 22
num2 *= 2; // num2 is now 44
```

# Naming Convetions

-   Combination of letters & numbers
-   Cannot start with a number!!!!!!!!!!
-   Cannot be a keyword
-   No limit on the lengths of identity
-   camelCase
    -   noOfGoals
    -   thisIsAnExampleOfCamelCase
-   Best practice is to be as CLEAR as possible with your variable names
    -   String hello = "Hello";

# Primitive Datatypes

## Byte

```java
byte b = 5;

byte b = 1000000000000; // throw an error
// 8 bits
// any number between -128 to 127
```

## Short

```java
short s = 128;
//16 bits
// any number between -32,768 and 32,767
```

## Integer

```java
int i = 50000;
// 32 bits
// any number -2,147,483,648 to 2,147,483,647
```

## Long

```java
long l = 109837412903846712378;

// 64 bits/ 8 bytes
// - 18,446,744,073,709,551,616 to 18,446,744,073,709,551,615
byte i;
i = (int) 10010000;
```

## Float

```java
float f = 4.0f;
// 32 bits
```

## Double

```java
double d = 57.0;
// 64 bits
```

## Char

```java
char c = 'A';
// 16 bits rang '\u0000' to '\uffff'
```

## Boolean

```java
boolean isTrue = false;

// true or false is ALWAYS all lowercase
```

-   **Choosing Variable types**
    -   make sure the type you require has the range you require.
    -   Cannot take a double and put into a float
        -   bigger values cannot be usedd for smaller ones

# Casting

-   Allows you to take larger datatypes and put into smaller datatype
-   intValue = (int) longValue; this works as long as the long value is within range

## Implicit Conversion

-   Taking a smaller to a larger type
-   int to a long
    -   long longValue = intValue

# Comparison Operators

-   These are used to help compare two given values and will return either true or false
-   Commonly used when using conditionals for itereating through statements
-   IF-else

```java
int i = 5;
i == 5; // return true

i >= 5; // return true
i <= 5;// return true
i <= 4;// return false

i == "Hello";// return false
i != "Hello"; // return true
i == "HeLlO"
```

# Logical Operators

-   !(conditional) Returns false is the condition is true
-   && is the AND operator
    -   both condition must be met to return true
-   || is the OR operator
    -   one conditional must be met to return true
-   ^ exclusive or (XOR)
    -   immediately returns false the first instance

## Ternary operators

-   can be used to replace if-else statements
-   condtion ? true : false

# Control Flow

## If-Else Statements

-   Checking whether or not some conditional value is true
-   If it's true
    -   execute the following statements
-   ELSE
    -   execute the other statements

```java

int i = 10;

if(i == 10){
    System.out.println("Oh yea the numbers match");
} else {
    System.out.println("Oh NOOOOOOOOOO");
}

```

## If Else If

```java

int b = 4;
int c = 5;
if( c + b == 10){
    System.out.println("Oh yea the numbers match");
} else if(i > 10) {
    System.out.println("That's one big number");
} else {
    System.out.println("Done, your number is weak.");
}
```

## For Loop

-   Loop over a set a statements multiple times until the condition is no logner true
-   basic syntax of forloops
    -   for(initializaiton; conditional; update intial value)

```java
for(int i = 0; i < 10; i++){
    System.out.println(i);
}

for(int i = 0, j = 9; i < 10; i++){
    System.out.println(i);
    System.out.println(j);
}
```

## While loop

-   Performs the block statements as long as the conditional is true

```java
boolean isRunning = true;
int counter = 0;

while(isRunning){
    System.out.println("Am dog bork bork");
    counter++;
    if(counter == 10){
        isRunning = false;
    }
}

```

## Do/While Loop

-   This perfroms the block statement at LEAST once, will repeat if the conditional is still met

```java
int counter = 9;

do{
    System.out.println(counter);
    counter++;
} while(counter = 11);
```

## Switches

-   Very useful for given input, some value is assigned
-   perfroms a particular task

```java
switch(userInput){
    case "10":
    case "8":
    case "2":
        System.out.println("Hello");
        break;
    case "5":
    case "3":
        System.out.println("Hola");
        break;
    default:
        System.out.println("You didn't enter a valid choose. Please try again.");
        break;
}

if(day.equals("Monday") || day.equals("Tuesday") || )
```

# Objects

-   Just instances of classes and all there elements
    -   String is a class, therefore it is an object type when define in memory
-   It contains methods and variables to actually apply or alter values
-   Objects have states and behaviors that **CAN** be chagned (mutable)
-   _CREATION_

    -   making a reference to this object
    -   Reference vs Primitive
        -   memory
        -   assignment
        -   initiliaztion
    -   Pre-defined Objects in Java
        -   String (immutable)
        -   Wrapper Classes(immutable)
        -   LocalDate, LocalDateTime(immutable)
    -   **Reference variable**
        -   stored in stack memoery
        -   copies the reference
        -   if the reference changes so does the copy
        -   comparing two objects of different references would always return false with ==

![Comparison](images/primitive-vs-object.png)

## Memory

-   **Stack Memory**
    -   Static memory alolocation and execution of a particular thread
    -   Temporary memory where variables values are stored when methods are invoke
    -   New method invocation creates new blocks and can reset those variable
    -   **ONLY accessible by the current running method and will not exist once it ends**
    -   Fase access to those values needed and easy to find
    -   Threadsafe
    -   IF full, java.lang.StackOverFlowError
-   **Heap Memory**
    -   used for dynamic memory allocation of java objects and JRE classes
    -   Object creation always created in HEAP and has global access
    -   reference to variable names store stack memory
-   **Garbage Collection**
    -   Automatically handles
    -   Removes unused objects from the heap memory
        -   4 ways to make an object eligible for GC
            -   1. Nullifying the reference var
            -   2. Reassign the reference
            -   3. Object created inside the method
            -   4. Island of Isoaltion

![Stack & Heap Example](https://www.baeldung.com/wp-content/uploads/2018/07/java-heap-stack-diagram.png)

# String Intro

-   **Spring Literal**
    -   String is specicial in that you don't need to use a constructor to create it
    -   Can print length of a string
    -   Can print each character within a string
        -   str.charAt(#)

```java
String someString = "This is a lot of text in a string"
//would return the location of the first char "l" in the word lot
someString.indexOf("lot")
someString.endsWith()
someString.startsWith()

/
"".equals("value")
"value".equals("value")
"value".equalsIgnoreCase("VaLuE")
```

# String Pool

-   Due to the immutable nature of Strings in Java, we can optimize the amount of memory allocated for them
    -   **STORE ONLY ONE COPY** of each literal String in the pool
        -   This is call _interning_
    -   When we create a String variable and assign a value to it and the JVM searches the pool for a String of equal value
        -   **If found**
            -   Java compiler will simply return a refernce to its' memory address, without allocating additional memory
        -   **NOT found**
            -   it'll be added to the pool (interned) and its' reference will be returned

## Manipulating String Values

-   Strings are **immutable**

```java
String str = "Charles is awesome";
System.out.println(str.concat(", SIKE!"));
//output: Charles is awesome, SIKE!
String newStr = str.concat(", SIKE!");
str = str.concat(", SIKE!");

System.out.println(str); // Output: Charles is awesome
// Must reassign the string in order to call this

str.toUpperCase()
str.toLowerCase()
```

-   String. or str. and tab will let you see what methods are possible, you can use this so search documentation to explore specific methods
-   _Creating objects is "expensive" in java_
-   **StringBuffer**
    -   class to create new string objects
    -   THIS allows you to mutate you string
    -   this helps prevent multiple uses of object
    -   **Synchronized** class
    -   Ready for multithreading
    -   **Single-threaded scenarios StringBuffer might be slow**
-   **StringBuilder**
    -   very similar to StringBuffer
    -   if not worries about multi-threading then use the StringBuilder

# == vs .equals()

-   Both == operator and .equals() methods are used to compare two objecsts in Java
-   == **operator** compares reference or memory location of objects in a heap,
    -   whether they point to the same location or not
-   .equals() **method** compares content between one another
    -   whether the values in objects match
    -   defaults to equals(Object o)
    -   **CAN** be overriden, read more [here](https://www.geeksforgeeks.org/override-equalsobject-hashcode-method/)

```java
String s1 = "Hello";
String s2 = "Hello";
String s3 = new String("Hello");

System.out.println(s1 == s2); // true
System.out.println(s1 == s3); // false
System.out.println(s1.equals(s2)); // true
System.out.println(s1.equals(s3)); // false
```

# Wrapper Classes

-   What is a Wrapper Class?
    -   A wrapper class wraps (encloses) around a data type and gives it an object appearance
    -   Wrapper Classes are ALL **FINAL** and **IMMUTABLE**
-   Types:
    -   Wrapper: Boolean, Byte, Character, Double, Float, Integer, Long, Short
    -   Primitive: boolean, byte, char, double, float, int, long, short
-   Why Wrapper Class?
    -   Creation from other data
    -   methods attached

```java
Integer hundred = Integer.valueOf("100");

Integer seven = Integer.valueOf("111", 2);
Integer.toString(seven, 2);
```

## Auto-Boxing

-   Can just declare Integer seven = 7;

```java
Integer seven = 7;
Integer seven = new Integer(7);
```

-   We as programmers are generally lazy!!!
-   **Syntactic Sugar**

# Intro Arrays

## Concepts

-   List of ints, Strings, booleans.
-   Creating an array you must specifiy the type
-   int[] intArr;
-   Arrays are mutable, exclused **SIZE**

```java

// initilize an empty array with 25 values (result to default)
int[] intArr = new int[25];
intArr.add(123984712349);
intArr[24] = 12938471234;

int[] grades = {75, 90, 1000};

```

## Enhanced for loops

-   Arrays have the option to use the enhanced for structure

```java
int[] grades = {50, 75, 100, 35};

// Traditional for loop
for(int i = 0; i < grades.length; i++){
    System.out.println(marks[i]);
}

// Enhanced for loop
for(int grade:grades){
    System.out.println(grade);
}
```

# Classes

-   **Blueprint/Templates**
    -   constructe the attributes related to an object
    -   3 Important Steps
        1. Declaration
            1. Must declare a variable to refer to the object
            2. can declare on it's own
        2. Instantiation
            1. **new** keyword
            2. instatiates the class by allocated memory for a new object
            3. returns the reference to that memory
        3. Initialization
            1. the new keyword requires on, postfice argument as **constructor**
            2. **DOES NOT** need to be assigned to a variable
            3. Can be directly used in a expression

```java
int height = new Rectangle(13).addHeight(2);
```

## Class design basics

-   Nothing but a template to create objects
-   Each of these objects can have their own specific state
-   What are the values? That's up to you/library/package.
-   3 Determinations
    -   What is the state(variables)?
    -   How do we allow the construction?
    -   Behaviors/Operations/Methods you want to allow on the object?

## Basic Design class

-   What are the States(variables) of an object?
-   Dog Class
    -   String breed
    -   String name
    -   int barkPitch
    -   int weight
    -   int height
    -   int width
-   How do we construct this Dog?
    -   new Dog();
    -   new Dog(breed, name) // personal knowledge
    -   new Dog(breed, name, weight, height, width) // clinic purpose
-   Behaviors
    -   borkbork();
    -   isTailWag();
    -   isWalking();
    -   isRunning();
    -   catChasing();
    -   mailmanBiting();
    -   isEating();
    -   isHungry();

```java
public class Dog{

    // State
    private String breed; // Can no longer use the dog1.breed;
    public String doggoName;
    protected int barkPitch;
    int weight;
    int height;
    int width;
    int[] offspringWeight;

    // Constructor

    // default constructor that you DON'T need to specify
    // UNLESS you make you
    public Dog(){
        super(); // default class Object!
    }

    // writing your own constructor OVERWRITES
    public Dog(String breed, String doggoName, int... offspringWeight){
        this.breed = breed;
        this.doggoName = doggoName;
        // dog(Burnese, Atlas, 12,12,10,8,9 )
        this.offspringWeight = offspringWeight;
    }

    public void borkbork(){
        String hello = "Hello";
        System.out.println("Am dog, bork bork!" + hello);
        int counter = 0;
        if(hello.equals("Hello")){
            counter++;
            String actorName = "Bruce Willis";
        }
        // System.out.println(actorName); would fail because
        System.out.println(counter); //
    }
}

Dog atlas = new Dog("Burnese Mountain Dog", "Atlas");

System.out.println(atlas.breed); // return: wouldn't be able to write because it's private
System.out.println(atlas.doggoName); // return Atlas

atlas.doggoName = "Banana";


```

# Scopes

-   **Class**
    -   scoped to the classes itself not to any particular instance
    -   if a class is need to start an application it is loaded in (class loading)
-   **Instance**
    -   Declarations are scoped to a particular instance
    -   Declarations are not shared across instances
-   **Method**
    -   Declarations are scoped to the method body
    -   Parameters within the method signature scoped here as well
-   **Block**
    -   Declarations are scoped to the block they are declared in

# Modifiers

-   **public** - Big Kahoona
    -   is Access modifier
    -   it is used to set access level for
        -   classes
        -   attributes
        -   methods
        -   constructors
-   Two modifier
    -   **Access Modifiers**
        -   Class-based:
            -   _public_
                -   accessible by any other class
            -   _default_
                -   only accessible to classes in the same package
        -   Attributes, method and constructor:
            -   **public**
            -   **default**
            -   **private**
                -   only accessible in the declared class
            -   **protected**
                -   code is accessible only to classes in the same package and subclasses.
    -   **Non-Access Modifiers**
        -   Class-based:
            -   **final**
                -   class cannot be inherited by other classes
            -   **abstract**
                -   these class cannot be instantiated in memory
        -   Attributes and Methods:
            -   **final**
            -   **abstract**
            -   **static**
                -   Attributes and methods belong to the class rather the object
            -   **synchronized**
                -   Methods can only be accessed by one thread at any given time
            -   **transient**
                -   Attributes and methods are skipped when serializing the object
            -   **volatile**
                -   Value of any attribute is not cached thread-locally, it is always read from the main memory

# Intro to the OOPs

## Programming Paradigms

-   simply a school of though or model that has distinct features, frameworks, styles and patterns to help provide solutions to particular problems.
-   **Not all tools are good for all jobs**
    -   some tasks are much easier to solve with functional programming
    -   where otheres are esiter with object-orient programming
-   Note that there are 4 major programming paradigms
    -   [Whirlwind Tour of Programming Paradigms](https://hackr.io/blog/programming-paradigms)

### Proecedural

### logical

### Functional

### Object Oriented Programming

-   a programming paradigm
-   relies on the concept of classes and objects to structure a software program
-   Simple, reusable pieces of code
-   Classes = blueprint
-   Think of all the objects, person and different things involved in our programming
    -   **State**
        -   What data to you with to use for this specific class
    -   **Behavior**
        -   What are some of the potential actions/methods/verbs/behaviors
    -   **Construction**
        -   What does it NEEED

# 4 Pillars of OOPs

-   Inheritence
-   Polyphorism
-   Encapsulation
-   Abstraction

## Inheritance Basics

-   This allows you to **_extend_** information from one class to another
-   You can get the state and methods from one class and use it within another
-   Object is at the top of the Inheritance hierarchy
-   Whenever you call the subclass constructor the super class constructor is always called
    -   DEFAULTED SUPER();
-   Can hold the subcalass reference variables in a super class

```java

class Animal {
    ...
}

class Dog extends Animal {

}

// This is allowed and will result in the passing of the subclass reference variables and methods
Animal figs = new Dog();

// This will error as our Animal is the super class of dog
Dog digs = new Animal();
```

## Polyphorism

-   Simply means "many forms"
-   WE have many class that are related to each other by inheritance
-   This allows us to perform single actions in different ways
-   Superclass Animal
-   Method called animalSound()
    -   Pig sub-class w/ Method animalSound that pritns out "OINK"
    -   Cat sub-class w/ Method animaleSound that prints out "MEOW"
-   Same code, different behavior
-   based on the content of the reference variables

## Overloading

-   we can overload constructors or methods
-   Change the parameteres of a constructor or methods
-   uses the name
-   Different ways this is done
    -   change the number of parameters
    -   change the datatype of paramaters

```java
public class Calculator{
    public static int add(int x, int y){
        return x + y;
    }

    public long add(long x, long y){
        return x + y;
    }

    public void add(double x, double y){
        System.out.println(x + y);
    }

    public float add(float x, float y){
        return x + y;
    }

    public byte add(byte x, byte y){
        return x + y;
    }

    public short add(short x, short y){
        return x + y;
    }

    public Calculator getCalculator(){
        return new Calculator();
    }
}
```

## Overriding

-   dynimacially bind the method from the subclass in response to a method call from a subclass object reference by the super class type
-   This can only be done on methods!!!!!!!
-   changes the overall function of a method for that subclass
-   Allows programming for interface then implementation

```java

public class Animal {
    public void animalSound(){
        System.out.println("Am animal that makes sounds, woo");
    }
}

class Dog extends Animal {

    @Override
     public void animalSound(){
    }

    @Override // error from your IDE because you Animal class doesn't have this method
    public void isTailWagging(){

    }


}

```

# Annotations

-   A form of metadata, provide data about a program that is not part of the program
-   **NO DIRECT EFFECT** on the operation of program
-   Use cases:
    -   Information for the compiler
    -   Compile-time and deployment time processing
    -   Runtime processing

## Common Annotations

### @Override

-   informs the compiler that the element is meant to tbe overridden from a delcared method in the super class
-   **ITS NOT REQUIRED**
    -   prevent any errors
    -   if the method fails to correctly override the compiler generates an error

### @Deprecated

-   indicates that the marked element is deprecated and hsould no longer be used
-   Compiler generates a warning whenever a program uses a method, class or field with that annotation

![JavaDocs](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html)

## Encapsulation

-   Direct acces to the state of a class or being able to change that state shouldn't be allowed
-   Better to allow behaviors of that class handle the changes to state
-   Senistive data is hidden from the user
    -   Declare variables as private
    -   provide public get & set methods (doesn't always need to be pubblic)
-   **Getters & Setters**

```java

public class Animal{

    private String animalName;
    private int animalAge;
    private final isBreathing = true;

    public String getAnimalName(){
        return animalName;
    }

    public void setAnimalName(String animalName){
        this.animalName = animalName;
    }

    public int getAnimalAge(){
        return animalAge;
    }

    public void setAnimalAge(int animalAge){
        this.animalAge = animalAge;
    }

}
```

## Abstraction

-   the key role is having the innerworking not really be known
-   hiding all the complexities
-   they can call a method and expect it to work via the methods invoked (NOMENCLATURE (namig of methods and variables) is DRASTICALLY important)

### Abstract classes

-   Provided a feature by which you don't need to specify the implementation of it
-   Cannot instantiate an abstract
-   You need to use the keywords **_extends_** to have a subclass inherit this abstract class
-   Requires you provide that non-access modifier key word **abstract** before both the class and methods
-   If a class extends an abstract class it REQUIRES that you provided the implementation for any abstract method
-   What are the use cases:
    -   Think about cooking a dish
        -   Steps:
            1. Prep
            2. Recipe
            3. Cleanup

### Interfaces

-   Interfaces establish the communication agreement( or contract) between two classes which are talking with on another
-   One interface can extend another interface
-   If a class wants to implemente the interface intot the subclass **implements** keyword

```java
public interface CrudDAO{
    ... // some methods here to be implemented later
    int speed = 0; // considre a constant variable in your interface
    public void makeSound();
}


/// some other file

public class Animal implements CrudDAO{
    ... // Animal components
    public String getAnimalName(){
        return this.animalName;
    }
    @Override
    public void makeSound(){
    }
}
```

## Interfaces vs Abstract class

-   Interfaces
    -   useful for when you want two classes, componenets talk with one another to have similar methods
    -   you want to defined communication between two
    -   CANNOT have private, everything public
    -   CANNOT include variables, none of those variables with change. Consider **_CONSTANT VARIABLEs_**
-   Abstract Classes
    -   high level structure provided to the subclass to ensure those variables/states and methods are always generated and implemented
    -   Leaves the implementationto when you are defining classes extending your abstract class
    -   CAN have private methods

<hr>
<hr>
<hr>
<hr>
<hr>

# Generics

-   introduced in Java 5
-   enforce compile time safety by allowing you to use parameterized types.
-   They are covered here because the are frequently and heavily used with collections.
-   Generics can be declared on a
    -   **class** (generic types)
    -   **method parameters**(generic methods)
    -   **return types**

Before Java 5, you had to write something like this and hope other developers understood to only put Strings inside:

```java
List names = new ArrayList();
names.add("Alice"); // good use
name.add(new Object()); // uh oh - we want to prevent this from happening
```

With generics, you can restrict a class to only accept objects of a given type and the compiler will prevent you from using any other type:

```java
List<String> names = new ArrayList<>(); // using a List of Strings only
names.add("Alice"); // nice!
names.add(new Object()); // now we get a compilation error to stop this - generics save the day!
```

# Generic Classes

To make a class (or interface) generic, use the angle brackets when declaring it, and use an arbitrary "generic type" which is determined by the invoking code. The generic type can then be reused throughout the class to enforce type safety.

## Naming Convention for Generics

Technically, type parameters can be named anything you want. The convention is to use single, uppercase letters to make it obvious that they are not real class names.

-   E => Element
-   K => Map Key
-   V => Map Value
-   N => Number
-   T => Generic data type
-   S, U, V, and so on => For multiple generic data types

# Exceptions/Errors

## Error

-   Error class is used to indicate more serious problems in the architecture and shouldn't be handled in the application code
-   This refers to problems that the application cannot recover from.
    -   How to fix?
        -   Modifiying application architecture
        -   refactoring code
    -   Examples:
        -   InternalError
        -   OutOfMemoryError
        -   AssertionError

## Exception

-   events that occurs during the execution of a prgram that disrupts the normal flow of instructions
-   unexpected or unwanted event which can happen either at compile-time or run-time in application code
-   can happen frequently in the course of development
-   Exceptions can be several types and all exception types are organized in a fundamental hierarchy

## Class Hieracrhy

![Hierarchy](https://rollbar.com/wp-content/uploads/2021/07/java-exceptions-hierarchy-example.png)

## Unchecked vs Checked

### Runtime Exception (Unchecked)

-   It reflects some error inside the program logic
    -   Example: Dividing by Zero throws a ArthimetixException
-   Java does not verify unchecked exceptions at compile-time.
-   We don't have to declare unchecked exception in a method with the throws keyword.
-   Some common unchecked exceptions include:
    -   **NullPointerException**
        -   occurs when a variable is accessed which is not pointing to any object and refers to nothing or null.
        -   Since the NullPointerException is a runtime exception, it doesn't need to be caught and handled explicitly in application code.J
    -   **ArrayIndexOutOfBoundsException**
    -   **IllegalArgumentException**
-   _RuntimeException_ is the superclass of all unchecked exceptions
    -   we can use this class to create a custom unchecked exception by extending RuntimeException
    -

### Compile-time Exception (Checked)

-   Checked exceptions are handles at compile time
    -   IF a method dis throwing a **checked** exception then it should be handled using a try-catch block
    -   OR it should declar the exception using throws keyword, otherwise it will give an compilation error.
-   These exceptions represent errors outisde the control of the program.
-   Java will verify these exceptions are caught at compile-time
-   Two Methods for Handling the
    -   **Try/Catch/Finally** blocks
    -   _Ducking_ or _Declaring_ Exceptions
-   _Exception_ class is used to create custom checkedd exceptions
    -   extends Exception

## Try/Catch/Finally blocks

-   _Anatomy of a Try/Catch/Finally_
    -   **Try-block**
        -   this is where "risky" code is executed
        -   this is where a set of statements that might throw and exception might occur
        -   always has a following catch-block after it
    -   **Catch-block**
        -   used to handle the uncertain condition of the try blacok
        -   this _ALWAYS_ follows a try-block
        -   Completely ignored if no exception (or not specific exception) has been thrown (think of multi-exception throws)
    -   **Finally-block**
        -   executed after catch block
        -   basically used
-   Try-catch-finally or try-catch has 3 cases scenarios
    -   Exception occurs in try block and handled in the catch blcok
    -   Exception occurs in the try-block and NOT handled in the catch block
    -   Exception doesn't occur in try block
    -

## Ducking/Declaring Exceptions

-   These are exceptions that will be handled later by the parent method
-   You don't want to handle it in your current method so you throw it to the parent to be handle
-   **Ducking your responsibility** ;P
    -   we can all vibe with this
-   Uses the throws keyword along with the exception name your throwing

```java
public void methodName() throws Exception{
    if(charles == "dumdum"){
        throw new Exception();
    }
}
```

### Rules for multi-blocks

-   Try-block **MUST ALWAYS** be followed by at least one catch!
-   Can have multiple catches for one try block
-   this is useful to handle multiple types of exceptions thrown to more easily interrupt

```java
class Example{
   public static void main(String args[]){
     try{
         int a[]=new int[5];
         a[4]=30/0;// Throws ArithmeticException
         a[100]=10; // Throws ArrayIndexOutOfBoundException
         System.out.println("First print statement in try block");
     }
     catch(ArithmeticException e){
        System.out.println("Warning: ArithmeticException");
     }
     catch(ArrayIndexOutOfBoundsException e){
        System.out.println("Warning: ArrayIndexOutOfBoundsException");
     }
     catch(Exception e){
        System.out.println("Warning: Some Other exception");
     }
   System.out.println("Out of try-catch block...");
  }
}

```

### Try with resources

-   allows us to declare reosurces to be used in a try blcok with the assurance that the resources will be clsoed after execution of that block
-   **Resources decalred NEED to implement the AutoCloseable interface**
-   resources must both be declared and intialized inside a try
-   They **CAN** still have a catch and finally block to handle everything as a normal trycatch block would

## Why Make Custom Exceptions?

-   Java exceptions cover almost all general exceptions that are bound to happen in programming
-   However, we sometimes need to supplement these with our own.
-   Main Reasons why?
    -   Business logic exceptions
        -   specific to the business logic and workflow
        -   these help the application users or devs understand the exact problem is
    -   to catch and provide specific treatment to a subset of existing java exceptions
-   These can be checked or unchecked.

## When to use Checked vs Unchecked?

-   Important and good practice to use Exceptions to separate error-handling code from regular code
-   Oracle provides documentation on the matter [here](https://docs.oracle.com/javase/tutorial/essential/exceptions/runtime.html)
-   "If a client can reasonably be expected to recover from an exception, make it a checked exception. If a client cannot do anything to recover from the exception, make it an unchecked exception"
    -   Example. Think of validating that a file exists, if the user input was invalid we can throw a custom

# Serialization

-   java provides a functionality called object serialization
-   **\*implements Serializable**
    -   marker interface
        -   no data or methods associated
        -   USed to "mark" java classes so that objects of these class may get certain capabilities
-   this is where an object can be represented as a sequence of bytes
    -   This includes the objects data
    -   information about the object's type
    -   types of data stored in the object
-   Serializaed objects are written to files and can be read from files and de-serialized
    -   this process can recreate the object in memory
    -   this process is JVM **independent**
        -   meaning you can perform this process on a completely different machine/platform
-   The two classes with high-level streams that contain the methods for serialization and deserialization are
    -   **ObjectInputStream**
        -   reads in serialized data and de-serializes it
        -   the return value is of type Object so you will need to cast it to it's appropriate data type
    -   **ObjectOutputStream**
        -   serializes the object and sends it to the output stream

## Points on Serialization

1. If a parent class has implemented Serializable interface then child class doesn’t need to implement it but vice-versa is not true.
2. Only non-static data members are saved via Serialization process.
3. Static data members and transient data members are not saved via Serialization process.So, if you don’t want to save value of a non-static data member then make it transient.
4. Constructor of object is never called when an object is deserialized.
5. Associated objects must be implementing Serializable interface.

## Why Use it?

-   **_Communication_**
    -   If you have two machines that are running the same code, and they need to communicate
    -   an easy way is for one machine to build an object with information that it would like to transmit
    -   then serialize that object to the other machine.
    -   _It's not the best method for communication, but it gets the job done._
-   **_Persistence_**
    -   If you want to store the state of a particular operation in a database
    -   it can be easily serialized to a byte array, and stored in the database for later retrieval.
-   **_Deep Copy_**
    -   If you need an exact replica of an Object
        -   don't want to go to the trouble of writing your own specialized clone() class
        -   simply serializing the object to a byte array
        -   de-serializing it to another object achieves this goal.
-   **_Caching_**
    -   Really just an application of the above,
    -   but sometimes an object takes 10 minutes to build, but would only take 10 seconds to de-serialize.
    -   Rather than hold onto the giant object in memory, just cache it out to a file via serialization
    -   Read it in later when it's needed.
-   **_Cross JVM Sycnhronization_**
    -   Serialization works across different JVMs that may be running on different architectures.

## Comparable vs Comparator

-   [**Comparable**](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html)
    -   A comparable objecet is capable of comparing itself with another object
    -   Class itself must implement the java.lang.Comparable interface to compare its instances
    -   We can implement the Comparable interface within our class
        -   implements Comparable\<Classname>
        -   Override the method compareTo()
-   [**Comparator**](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html)
    -   This is an exterenal element type we are comparing
    -   **A seperate class**
    -   We create multiple separate classes the implements the Comparator.
        -   To make comparisons we must do 3 things:
            -   Create a class that implements Comparator
            -   make an instance of the Comparator class
            -   Call the overloaded sort() method, giving it both the list and the instance of the class that implements Comparator
-   _When to use what_
    -   Comparable is meant for objects with natural ordering
    -   Logically comparable interface compares "this" reference with the object specified
    -   Classes implementing Comparable can either List or Array can be sorted automatically by using Collections.sort() or Arrays.sort()
        -   They will then be sorted based on their natural order defined by the compareTo() method (or the one you overriden)
    -   Comparable can use only **ONE** comparison!
    -   You can write more custom comparators as you want for a gicen type, all using different interpretations of what the sorting is meant to do.

# Iterator and Iterable

# **Iterator**

-   use to iterate or traverse or retrieve a collection or stream objects elements one by one
    -   we can perform borth read and remove operations
    -   improved version of enumeration with the additional functionality of removing an element
    -   _ONLY_ cursor available for the entire collection framework
    -   Iterator object can be created by calling interator() method prsent in the collection framework
-   **Methods**:
    -   hasNext(): returns true if the iteration has more elements
    -   next(): returns the next element in the iteration. _*Throws*_ _NoSuchElementException_ if no more element present
    -   removes(): removes the next element in the iteration. This method can be called only once per call to next();
        -   Throws two Exceptions:
        -   _UnsupportedOperationException_: if the remove operation is not supported by this iterator
        -   _IllegalStateException_: if the next method has not yet been classed, or the remove method has already been called after the last call to the next method.
-   **Advantages**:
    -   We can use it for any Collection Class
    -   It supports both READ and REMOVE operations
    -   Universal Cursor for the Collection API
    -   Method names are simple and easy to use.
-   **Limitations**:
    -   In CRUD operations, it does not support CREATE and UPDATE operations
    -   It supports only Forward direction iteration that is Uni-Directional iterator
-   This is one of three java Cursors, the others are:
    -   **_Enumeration_**
        -   used for legacy class (Vector, Hashtable)
        -   Remove operation can't be performed using Enumeration
        -   Only forward direction
    -   **_ListIterator_**
        -   only applicable for List collection implemented classes like ArrayList, LinkedList, etc
        -   has more methods than iterator and can move forward and backward
        -   has methods to replace elements

# **Iterable**

-   interfact that allows an onject implementing the interface to be iterated. Allows the object to be the target of enhanced for loop
-   Three ways in which objects of Iterable can be iterated
    -   Using enhanced for loop
        -   Objects of classes implementing collection interface can be iterated using for-each loop
        -   Collection interface extends Iterable itnerface
    -   Using Iterable forEach loop
        -   the forEach() method takes the lambda expression as a parameter. This lambda expression is called for each element.
    -   using Itator<T> interface

## Iterator vs Iterable

-   Iterator stores the iteration state
    -   means that it provides utility methods to get the current element, check if the next element exists and move forward
    -   Remember current location in a collection and return sthe next element if present.
-   Iterable on the other hand doesn't maintian any such iteration state
-   Iterable should produce a new isntance of an Iterator every time the iterator() method is called.
    -   Iterator maintains the iteration state, so if you return the same Iterator twice it won't work.
-   Iterable only allows for the uni-directional flow\
    -   Iterator has sub-interfaces like ListIterator that allows us to move back and forth.
-   Iterable doesn't allow for use to modify elements using the for-each loop
    -   Iterators allow removing elements from thte underlying colection during the iteration with the remove method.

## Threads

-   Sometimes referred to as lightweight processes.
-   Both processes and threads provide execution environments
    -   **BUT** creating a new thread requires fewer resources than creating a new process.
    -   They are created in processes
-   Every process has at _LEAST_ one thread.
-   Threads share process's resources
    -   can make more efficient communication
    -   BUT potentially problematic
-   **Multithreading** execution is an essential feature of threads.
    -   These additional threads can be used to perform complicated tasks in the background without interrupting the main program
-   Two basic strategies
    -   **Directly control thread creation and management**
        -   simply instatiate Thread each time the application needs to initiate an asynchronous task
    -   To abstract thread management from the rest of your application, pass the application's task to an executor

### States

-   **New**
    -   A thread that has not yet started, but is intialized
-   **Runnable**
    -   A thread executing in the JVM
    -   Also further broken down into
        -   Ready for Execution
        -   Running
-   **Blocked**
    -   A thread that is blocked waiting for a monitor lock
-   **Waiting**
    -   A thread waiting for another thread to perfrom an action for up to a specified waiting time
-   **Timed Waiting**
    -   How much time has elapsed over the course
-   **Terminated**
    -   Thread that has exited/completed

### Lifecyle

![Lifecycle](https://www.baeldung.com/wp-content/uploads/2018/02/Life_cycle_of_a_Thread_in_Java.jpg)

### Creation

-   Two ways:
    -   **extends Thread**
        -   extending the Thread Class
    -   **implement Runnable**
        -   interface used for passing instances of the class to a Thread object's constructor

#### Class & Methods

-   The thread class has overloaded constructors
-   Main Two we will use:
    -   Thread()
    -   Thread(Runnable r)
-   Important Methods
    -   run()
        -   Entry point for a thread
    -   start()
        -   start a thread by calling the run method
    -   sleep()
        -   suspend thread for specified time
        -   while using sleep(), always handle the exception it throws
        -   throws InterruptedException

#### Runnable interfaces

-   It also used to create thread
-   should only be used if you are only planning to override the run() method
-   No other thread method needs to be overriden
-   Provides only single method that must be implemented by the class

# Synchronization

-   Threads communicate primarily by sharing access to fields and objects reference fields refer to
-   Extremely efficient but makes two kinds of errors possible
    -   _thread interference_
        -   describes how errors are introduced when multiple threads access shared data
    -   _memory consistency errors_
        -   describes errors that result from inconsistent views of shared memory
-   Be mindful of when you have concurrent threads running if they are accessing the same mutable object
    -   this can lead to inconsistencies known as a _race condition_
        -   this means the behavior and results of that variables/attrivute is dependent on the sequence or timing of other uncontrollable events, resulting in various outputs each time it is run.
        -   to help prevent this when multi-threading please be mindful to use the synchronized keyword in the methods declaration

# Lambda Expression

-   short block of code which takes in parameters and returns a value
    -   aka shortcut code
    -   multiple lines require {} and an explicit return
-   **Single line** does NOT require a return
-   similar to methods, but they do not need a name and they can be implemented right in the body of a method
-   can be stored as variables **IF** the variables type is an interface which has only one method
-   can be uses as an argument
-   java treats a lambda expression as on Object, which is infact the true first-class citizen

# Functional Interfaces

-   [Functional interfaces](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html) are interfaces that have only one abstract method.
-   This method is what lambdas are implementing when they are declared
    -   the parameter types and return types of the lambda must match the functional interface method declaration.
    -   The Java 8 JDK comes with many built-in functional interfaces, listed in the Javadocs link above.

```java
interface MyFunctionalInt {
  int doMath(int number);
}

public class Execute {
  public static void main(String[] args) {
    MyFunctionalInt doubleIt = n -> n * 2;
	MyFunctionalInt subtractIt = n -> n - 2;
	int result1 = doubleIt.doMath(2);
	int result2 = subtractIt.doMath(8);
	System.out.println(result1); // 4
	System.out.println(result2); // 6
  }
}
```

## POJO vs Bean

-   **Plain old java object**
    -   not bound by any special restriction other than those forced by the Java Language.
    -   used for increasing the readability and re-usability of a program.
    -   Most acceptance, due to being easy to write and understand
    -   **POJO should not:**
        -   Extend prespecified classes, Ex: public class GFG extends javax.servlet.http.HttpServlet { … } is not a POJO class.
        -   Implement prespecified interfaces, Ex: public class Bar implements javax.ejb.EntityBean { … } is not a POJO class.
        -   Contain prespecified annotations, Ex: @javax.persistence.Entity public class Baz { … } is not a POJO class.
    -   Baiscally defines an entity
        -   Employee class with name, id, and salary defined
-   **Java Beans**
    -   Special type of POJOs. Some restriction on a POJO to be a bean.
        -   **All JavaBeans are POJOs** but not all POJOs are JavaBeans.
        -   **Serializable** i.e. they should implement Serializable interface. Still, some POJOs who don’t implement a Serializable interface are called POJOs because Serializable is a marker interface and therefore not of many burdens.
        -   Fields are **private**. This is to provide complete control on fields.
        -   Fields should have **getters or setters** or both.
        -   A **no-arg constructor** should be there in a bean.
        -   Fields are accessed only by constructor or getter setters.

![POJO vs BEAN](.\images\pojo-v-bean.png)
