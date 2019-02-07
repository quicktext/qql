# QQL Courses

## Background

Understanding and using compiler is very important to programmers, however, it's very difficult for beginners.

In most of the schools, the design principles of compilers are designed for undergraduates.

But when the students graduate, they don't use the knowledge of the design principles of compilers.

They just use the programming language. 

They haven't requirements in design compilers when they work with most of the customers.

However, if they have to process the big data, such as the processing of US patents, they have to design the program to make processing data automatically.

Although the program can be designed without using the compiles, yet the program will be ugly.

For example:

Parse the comma-separated value (CSV) file, you can write the code as follows:

`line = line.split['\\.']`

But you also can write the code as follows;

`grammar CSV;`

`csvFile: hdr row+ ;`

`hdr : row ;`

`row : field (',' field)* '\r'? '\n' ;`

`field : TEXT | STRING |  ;`

We  have designed the Quicktext Query Language, if you want to take part in this project.

Please complete courses firstly.

For these programmers understanding what we have done, this course can be omitted.

## Before learning this course

Books to read firstly:

1. Parr, Terence. The Definitive ANTLR 4 Reference. 2013.
2. Horstmann, Cay S., and Gary Cornell. Core Java 2: Volume I, Fundamentals. Pearson Education, 2002.
3. Eckel, Bruce. Thinking in JAVA. Prentice Hall Professional, 2003.
4. Cormen, Thomas H., et al. Introduction to algorithms. MIT press, 2009.
5. Aho, Alfred V. Compilers: principles, techniques and tools (for Anna University), 2/e. Pearson Education India, 2003.
6. Knuth, Donald Ervin. The art of computer programming: sorting and searching. Vol. 3. Pearson Education, 1997.
7. Robbins, Arnold, Elbert Hannah, and Linda Lamb. Learning the vi and Vim Editors: Text Processing at Maximum Speed and Power. " O'Reilly Media, Inc.", 2008.
8. Daniels, John, and J. Cheesman. UML components: a simple process for specifying component-based software. Addison-Wesley, 2001.
9. Gamma, Erich. Design patterns: elements of reusable object-oriented software. Pearson Education India, 1995. 

Software and IDE:

1. [Antlr 4.0](https://www.antlr.org/)
2. [Oracle Java Development Kit 1.8](https://www.oracle.com/technetwork/java/javase/downloads/index.html)
3. Python 3(http://www.python.org)
4. [Git](https://git-scm.com/)
5. [GraphVIZ](http://graphviz.org/)

We use Ubuntun Linux system and Windows system.
For beginners, we recommend using windows system.
We have tested on Linux, Windows and Mac OS.

