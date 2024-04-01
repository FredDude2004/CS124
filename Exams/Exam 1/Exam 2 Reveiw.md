# CS 12400-001 Exam 2 Review

The exam is on Thursday, April 4.

The exam is over the following chapters:

Chapter  7 Input/Output and Exception Handling  https://learn.zybooks.com/zybook/PNWCS12400KraftSpring2024/chapter/7/section/1
Chapter 13 Recursion  https://learn.zybooks.com/zybook/PNWCS12400KraftSpring2024/chapter/13/section/1

In Chapter 7 of the zyBook, the most important sections are
7.1, 7.5, 7.8, 7.12, 7.16, 7.21, 7.22.

In Chapter 13 of the zyBook, the most important sections are
13.1, 13.2, 13.4, 13.8, 7.16, 7.21, 7.22.


Here are a few review problems.


### Problem 1
Consider the following program.
```java
   import java.util.Scanner;
   public class Problem1
   {
      public static void main(String[] args)
      {
         Scanner stdin = new Scanner(System.in);
         String s1 = stdin.nextLine();
         String s2 = stdin.next();
         String s3 = stdin.next();
         String s4 = stdin.nextLine();
         String s5 = stdin.next();
         System.out.println(s1);
         System.out.println(s2);
         System.out.println(s3);
         System.out.println(s4);
         System.out.println(s5);
      }
   }
```
Suppose we run this program with the following input
(the input is what is in the following "box", as it's
done in the Java Visualizer). What would the program
print out? Briefly explain why.
<pre>
  stdin
  +-------------------------------+
  |Hello there everyone.          |
  |What do you think?             |
  |Here are numbers, 23 45 56     |
  +-------------------------------+
</pre>


### Problem 2
Suppose we run the following program.
```java
   import java.util.Scanner;
   public class ScannerProblem
   {
      public static void main(String[] args)
      {
         Scanner stdin = new Scanner(System.in);
         double d = stdin.nextDouble();
         String s = stdin.next();
         int n = Integer.parseInt(s);
      }
   }
```
Which of the following exceptions will be thrown by the program when
the program is given each of the following inputs? In each case,
which line of this program causes the exception?
<pre>
   java.lang.NumberFormatException
   java.util.NoSuchElementException
   java.util.InputMismatchException
</pre>
#### (a) The input is:
1.23<br>

#### (b) The input is:
1.23<br>
4.56<br>

#### (c) The input is:
1.2x<br>
456<br>

#### (d) The input is:
cat<br>
dog<br>

#### (e) The input is empty:



### Problem 3 
Suppose you see in the console window the following stack trace.
```java
java.lang.Exception
        at StackTraceProblem.methodC(StackTraceProblem.java:17)
        at StackTraceProblem.methodB(StackTraceProblem.java:13)
        at StackTraceProblem.methodE(StackTraceProblem.java:25)
        at StackTraceProblem.methodA(StackTraceProblem.java:9)
        at StackTraceProblem.methodD(StackTraceProblem.java:21)
        at StackTraceProblem.main(StackTraceProblem.java:5)

Was this stack trace caused by StackTraceProblem on the left
or StackTraceProblem on the right? Explain why the stack trace
could not have been cause by the other program.

/* 1*/ public class StackTraceProblem                       /* 1*/ public class StackTraceProblem
/* 2*/ {                                                    /* 2*/ {
/* 3*/    public static void main(String[] args)            /* 3*/    public static void main(String[] args)
/* 4*/    {                                                 /* 4*/    {
/* 5*/       methodD();                                     /* 5*/       methodD();
/* 6*/    }                                                 /* 6*/    }
/* 7*/    public static void methodA()                      /* 7*/    public static void methodA()
/* 8*/    {                                                 /* 8*/    {
/* 9*/       new Exception().printStackTrace(System.out);   /* 9*/       methodE();
/*10*/    }                                                 /*10*/    }
/*11*/    public static void methodB()                      /*11*/    public static void methodB()
/*12*/    {                                                 /*12*/    {
/*13*/       methodE();                                     /*13*/       methodC();
/*14*/    }                                                 /*14*/    }
/*15*/    public static void methodC()                      /*15*/    public static void methodC()
/*16*/    {                                                 /*16*/    {
/*17*/       methoB();                                      /*17*/       new Exception().printStackTrace(System.out);
/*18*/    }                                                 /*18*/    }
/*19*/    public static void methodD()                      /*19*/    public static void methodD()
/*20*/    {                                                 /*20*/    {
/*21*/       methodC();                                     /*21*/       methodA();
/*22*/    }                                                 /*22*/    }
/*23*/    public static void methodE()                      /*23*/    public static void methodE()
/*24*/    {                                                 /*24*/    {
/*25*/       methodA();                                     /*25*/       methodB();
/*26*/    }                                                 /*26*/    }
/*27*/ }                                                    /*27*/ }
```


### Problem 4 
What will the following program print out?
```java
/* 1*/ public class ThrowProblem
/* 2*/ {
/* 3*/    public static void main(String[] args)
/* 4*/    {
/* 5*/       System.out.println("main");
/* 6*/       methodC();
/* 7*/    }
/* 8*/    public static void methodA()
/* 9*/    {
/*10*/       System.out.println("methodA");
/*11*/       methodD();
/*12*/    }
/*13*/    public static void methodB()
/*14*/    {
/*15*/       System.out.println("methodB");
/*16*/       methodE();
/*17*/    }
/*18*/    public static void methodC()
/*19*/    {
/*20*/       System.out.println("methodC");
/*21*/       methodF();
/*22*/    }
/*23*/    public static void methodD()
/*24*/    {
/*25*/       System.out.println("methodD");
/*26*/       methodA();
/*27*/    }
/*28*/    public static void methodE()
/*29*/    {
/*30*/       System.out.println("methodE");
/*31*/       throw new IllegalArgumentException();
/*32*/    }
/*33*/    public static void methodF()
/*34*/    {
/*35*/       System.out.println("methodF");
/*36*/       methodB();
/*37*/    }
/*38*/ }
```


### Problem 5 
What will the following program print out?
```java
/* 1*/ public class ThrowCatchProblem
/* 2*/ {
/* 3*/    public static void main(String[] args)
/* 4*/    {
/* 5*/       methodB();
/* 6*/       System.out.println("main");
/* 7*/    }
/* 8*/    public static void methodA()
/* 9*/    {
/*10*/       methodF();
/*11*/       System.out.println("methodA");
/*12*/    }
/*13*/    public static void methodB()
/*14*/    {
/*15*/       methodD();
/*16*/       System.out.println("methodB");
/*17*/    }
/*18*/    public static void methodC()
/*19*/    {
/*20*/       methodE();
/*21*/       System.out.println("methodC");
/*22*/    }
/*23*/    public static void methodD()
/*24*/    {
/*25*/       try {
/*26*/          methodA();
/*27*/       }
/*28*/       catch (Exception e) {
/*29*/          System.out.println("caught");
/*30*/       }
/*31*/       System.out.println("methodD");
/*32*/    }
/*33*/    public static void methodE()
/*34*/    {
/*35*/       System.out.println("methodE");
/*36*/       throw new IllegalArgumentException();
/*37*/    }
/*38*/    public static void methodF()
/*39*/    {
/*40*/       methodC();
/*41*/       System.out.println("methodF");
/*42*/    }
/*43*/ }
```


### Problem 6 
Consider the following program.
```java
   public class Problem6
   {
      public static void main(String[] args)
      {
         System.out.println( args.length );
      }
   }
```
In each part below, we run this program with a different command-line.
For each command-line, what does the program print out?
Briefly explain why.

(a) The command-line is:
<pre>
> java Problem6  hello there my friends
</pre>
(b) The command-line is:
<pre>
> java Problem6  hello there "my friends"
</pre>
(c) The command-line is:
<pre>
> java Problem6  hello-there my friends
</pre>
(d) The command-line is:
<pre>
> java Problem6  hello : there : my : friends
</pre>
(e) The command-line is:
<pre>
> java Problem6  hello,there,my,friends
</pre>


### Problem 7 
Suppose we run the following program.
```java
   public class Problem7
   {
      public static void main(String[] args)
      {
         int n1 = Integer.parseInt(args[0]);
         String s1 = args[1];
         double n2 = Double.parseDouble(s1);
         String s2 = args[2];
      }
   }
```
In each part below, we run this program with a different command-line.
Each of these command-lines will cause the program to crash. In each
case, what is wrong with the command-line and which line of code is
throwing an exception? (You don't need to remember what the exact
name for the exception is.)

(a) The command-line is:
<pre>
> java Problem7  12  34
</pre>
(b) The command-line is:
<pre>
> java Problem7 12  cat  dog
</pre>
(c) The command-line is:
<pre>
> java Problem7  1.2  3.4  5.6
</pre>
(d) The command-line is:
<pre>
> java Problem7  12
</pre>


### Problem 8 
Suppose that the following program,
```java
   public class Problem8
   {
      public static void main(String[] args)
      {
         int n1 = Integer.parseInt( args[1] );
         int n2 = Integer.parseInt( args[n1] );
         System.out.println( n2 );
      }
   }
```
is run with the following command-line. What does the
program print out? Briefly explain why.
<pre>
> java Problem8  2  3  45  678  901
</pre>


### Problem 9



### Problem 10




### Problem 11




### Problem 12 
What does the following recursive method compute?

That is, how is the string returned by the method related
to the input string? Hint: Hand trace the method with a
simple input string, like "cats".

What would be an appropriate name for this function?
```java
public static String mystery(String str)
{
   if ( str.equals("") ) // base case
   {
      return "";
   }
   else // recursive case
   {
      return mystery( str.substring(1) ) + str.charAt(0);
   }
}
```


### Problem 13 
What does the following recursive method compute?

That is, how is the integer returned by the method related
to the input string? Hint: Hand trace the method with an
input string like "elephants".

What would be an appropriate name for this method?
```java
public static int mystery(String str)
{
   if ( str.equals("") ) // base case
   {
      return 0;
   }
   else // recursive case
   {
      return 1 + mystery( str.substring(1) ); // recursion
   }
}
```


### Problem 14 
What does the following recursive method compute?

That is, how is the string returned by the method related
to the input string? Hint: Hand trace the method with an
input string like "Hello and how are you" (spaces are
important to this method).
```java
public static String mystery(String str)
{
   if ( str.equals("") ) // base case
   {
      return "";
   }
   else if ( str.charAt(0) == ' ' ) // compare to a space character
   {
      return mystery( str.substring(1) ); // recursion
   }
   else
   {
      return str.charAt(0) + mystery( str.substring(1) ); // recursion
   }
}
```


### Problem 15 
What does the following recursive method compute?

That is, how is the boolean returned by the method related
to the input string? Hint: Hand trace the method with an
input string like "dogs".
```java
public static boolean mystery(String str)
{
   if ( str.equals("") ) // first base case
   {
      return false;
   }
   else if ( str.equals("s") ) // second base case
   {
      return  true;
   }
   else // recursive case
   {
      return mystery( str.substring(1) ); // recursion
   }
}
```


### Problem 16 
Write a recursive function
```java
   public static String change(String str) // recursive
```
that replaces every space character, ' ', in the input
string with a hyphen character, '-'. So
<pre>
   change("hello there every one")  ==>  "hello-there-every-one"
</pre>
Hint: Modify one of the above recursive methods.




### Problem 17 
What does the following recursive method compute?

That is, how is the string returned by the method
related to the input string and input integer?
Hint: Hand trace the method call
```java
   mystery("elephant", 4).
```
```java
public static String mystery(String str, int n)
{
   if ( str.equals("") ) // a base case
   {
      return "";
   }
   else if ( n == 0 ) // another base case
   {
      return "";
   }
   else // recursive case
   {
      return str.charAt(0) + mystery( str.substring(1), n-1 );
   }
}
```