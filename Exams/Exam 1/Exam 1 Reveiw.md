# CS 12400-001 Exam 1 Review

The exam is on Thursday, February 15.

The exam is over the following sections:

Section 6.3 Enhanced for Loop  https://learn.zybooks.com/zybook/PNWCS12400KraftSpring2024/chapter/6/section/3<br>
Section 6.17 ArrayList         https://learn.zybooks.com/zybook/PNWCS12400KraftSpring2024/chapter/6/section/17<br>
Chapter 6 Writing classes      https://runestone.academy/ns/books/published/csjava/Unit6-Writing-Classes/toctree.html<br>
Chapter 9 Inheritance          https://learn.zybooks.com/zybook/PNWCS12400KraftSpring2024<br>

In Chapter 9 of the zyBook, the most important sections are
9.1, 9.2, 9.3, 9.4, 9.5, 9.10, 9.12, 9.13, 9.15.

Here are the analogous chapters from the other textbook we have used:<br>
Chapter 8 ArrayList      https://runestone.academy/ns/books/published/csjava/Unit8-ArrayList/toctree.html<br>
Chapter 10 Inheritance   https://runestone.academy/ns/books/published/csjava/Unit10-Inheritance/toctree.html<br>



Here are a few review problems.


## Problem 1
Suppose that you are given the following ArrayList.
```java
   ArrayList<Integer> myList = new ArrayList<>(Arrays.asList(2, 3, 5));
```
Write exactly three lines of code so that myLlist will contain
the elements [1, 2, 3, 4, 5, 6].


## Problem 2 
a) What does the following code print out? Briefly explain why.
```java
   ArrayList<Integer> list1 = new ArrayList<>(Arrays.asList(1, 2, 3));
   ArrayList<Integer> list2 = new ArrayList<>(Arrays.asList(10, 11, 12));
   ArrayList<Integer> list3 = new ArrayList<>();
   for (int i : list1)
   {
      for (int j : list2)
      {
         list3.add(i);
         list3.add(j);
      }
   }
   System.out.println( list3 );
```
b) Replace the two lines nested in the innermost loop with the following
two lines. What does the code print out after this replacement?
```java
         list3.add(0, i);
         list3.add(0, j);
```
c) How would you write the nested loops to use list1 and list2
to make list3 contain these values?

[1, 10, 11, 12, 2, 10, 11, 12, 3, 10, 11, 12]



## Problem 3 
Suppose we have defined a class A which
has a constructor that takes a single integer.

After the following statements have been executed,
how many A objects will exist (not counting garbage
objects) and which objects are they? Explain your answer
and include in your explanation a picture of Java's memory.
Draw Java's memory the way it is shown by the Java Visualizer.
https://cscircles.cemc.uwaterloo.ca/java_visualize/
```java
   A a = new A(100);
   A b = new A(150);
   A c = b;
   b = a;
   a = null;
```


## Problem 4
Suppose we have defined a class A which
has a constructor that takes a single integer.

After the following statements have been executed,
how many A objects will exist (not counting garbage
objects) and which objects are they? Explain your answer
and include in your explanation a picture of Java's memory.
Draw Java's memory the way it is shown by the Java Visualizer.
https://cscircles.cemc.uwaterloo.ca/java_visualize/
```java
   A a1 = new A(200);
   A a2 = new A(250);
   A a3 = a2;
   a1 = null;
   a2 = a1;
```


## Problem 5 
Suppose we have defined a class Pair whose constructor
takes two int values. Draw a picture of Java's memory (both stack
and heap) after the following two lines of code are executed. Your
picture should be similar to the ones drawn by the Java Visualizer.
```java
   Pair[][] pairs = new Pair[2][3];
   pairs[1][1] = new Pair(200, 100);
```

## Problem 6 
What does the following program print out? Explain why.
```java
class Thing
{  public int a;
   public int b;
   public Thing(int a, int b){this.a=a; this.b=b;}
   public String toString() {return "a=" + a + " and b=" + b;}
}

public class TestThing
{
   public static void f(Thing x, int y)
   {  x.a++;
      y++;
   }
   public static void main(String[] args)
   {  Thing x = new Thing(1,1);
      int y = 1;
      f(x, y);
      System.out.println("x = " + x);
      System.out.println("y = " + y);
   }
}
```


## Problem 7 
Here is a simple Point and Circle class.
```java
class Point                                   class Circle
{  private double x, y;                       {  private double x, y; // center
                                                 private double r;    // radius
   public Point(double x, double y)
   {  this.x = x;                                public Circle(Point c, double r)
      this.y = y;                                {  this.r = r;
   }                                                this.x = c.getX();
                                                    this.y = c.getY();
   public double getX(){ return x; }             }
   public double getY(){ return y; }             // more stuff
}                                             }
```
a) Write code that creates a circle of
radius 5 with its center at (2, 3).

b) For the Circle class, write an implementation
for the following get method.
```java
   public Point getCenter()
   {


   }
```


## Problem 8 
What does the following program print out? Explain why.
```java
   public class Mystery
   {
      public static void doSomething(String a, String b)
      {  System.out.println( a + b ); }

      public static void doSomething(String a, int b)
      {  System.out.println( a + b ); }

      public static void doSomething(int a, String b)
      {  System.out.println( a + b ); }

      public static void doSomething(int a, int b)
      {  System.out.println( a + b ); }

      public static void main(String[] args)
      {  String x = "cat", y = "dog";
         int n = 3, m = 5;
         doSomething(n, m);
         doSomething(x, y);
         doSomething(x+n, m);
         doSomething(y, m+x);
      }
   }
```

## Problem 9 
Draw an inheritance tree for these classes.
```java
   class A {}
   class B extends A {}
   class C extends B {}
   class D extends A {}
   class E extends C {}
   class F extends C {}
   class G extends E {}
   class H extends F {}
```

## Problem 10 
Draw an inheritance tree for these classes
and interfaces. Try to draw as neat a diagram as you can.
(You should draw it without any lines crossing each other.)
```java
   interface I {}
   interface J {}
   class A {}
   class B extends A {}
   class C implements I {}
   class D extends C implements J {}
   class E extends B {}
   class F extends A implements I, J {}
```


## Problem 11 
Only one of the following four class definitions
defines a proper abstract class. Which one of the four is it?
For the remaining three classes, briefly explain why it does
not properly define an abstract class.
```java
   class A1 {
      abstract void unfinished();
   }

   abstract class A2 {
      abstract void unfinished(){ }
   }

   abstract class A3 {
      abstract void unfinished();
   }

   abstract class A4 {
      private abstract void unfinished();
   }
```


## Problem 12 
Suppose we have the following class definitions.
```java
   class A {
      private int aValue;
      public A(int a){aValue = a;}
      public int getA(){return aValue;}
   }
   class B extends A {
      private int bValue;
      public B(int a, int b){super(a); bValue = b;}
      public void setB(int b){bValue = b;}
   }
   class C extends B {
      private int cValue;
      public C(int a, int b, int c){super(a,b); cValue = c;}
      public int getC(){return cValue;}
   }
```
Which of the following lines of code will compile?
If a line of code does not compile, briefly explain why.
<pre>
   /* 1*/  A a = new B(1,2);
   /* 2*/  B b = new C(3,4,5);
   /* 3*/  C c = new C(6,7,8);
   /* 4*/  C d = new A(6,7,8);
   /* 5*/  int a1 = a.getA();
   /* 6*/  a.setB(10);
   /* 7*/  int a2 = b.getA();
   /* 8*/  int b2 = b.getb();
   /* 9*/  int c2 = b.getC();
   /*10*/  int a3 = c.getA();
   /*11*/  c.setB(10);
   /*12*/  ((C)a).setB(11);
   /*13*/  ((C)b).setB(12);
   /*14*/  int b3 = ((C)b).getC();
</pre>


## Problem 13 
Suppose that we have classes A, B, C and D.
Suppose that B is a subclass of A, that C is a subclass
of B, and D is a subclass of A. Suppose that we make the
following declarations.
```java
   A a1 = new A();
   A a2 = new C();
   D d1 = new D();
```
For each line below, explain what, if any, errors would be
caused by the statement in that line. Be sure to consider
both compile time and run time errors.
<pre>
   /*1*/  A a3 = new B();
   /*2*/  B b1 = new A();
   /*3*/  B b2 = (B) a1;
   /*4*/  B b3 = (B) a2;
   /*5*/  B b4 = (B) d1;
</pre>


## Problem 14 
Suppose that we have classes A, B, C, D, E and
an interface G that are related to each other this way.
<pre>
             Object
               |
               A    G
              / \  /
             B    C
                 / \
                D   E
</pre>
a) In the following code fragment, from which class definitions can
we choose method names to replace the "????" (where ... represents
appropriate parameters)? Be precise.
```java
   C c = new D();
   c.????(...);
```
b) In the following code fragment, what class names can we replace
the "?" with?
```java
   G g = new ?();
```
c) In this code fragment, what class names can replace the "?" in
the declaration for x?
```java
   ? x = new E();
```
d) In this code, what class names can replace "?" in the cast
of c so that the code compiles?
```java
   C c;
   // some code where c gets a value
   A a = (?)c;
```


## Problem 15
a) Explain the meaning of the keywords super and this when they are used as method names.

b) Explain the meaning of the keywords super and this when they are used as a "calling object".



## Problem 16 
Suppose we have defined a class A which
has a constructor that takes two integers. Suppose
that in the definition for A we DO NOT override
the equals() method.

Consider this code that creates some A objects:
```java
   A a, b, c;
   a = new A(10, 20);
   b = new A(10, 20);
   c = b;
```
After the following code executes, what is the
value for each of the six boolean variables?
```java
   boolean b1 = a == b;
   boolean b2 = a.equals(b);
   boolean b3 = a == c;
   boolean b4 = a.equals(c);
   boolean b5 = b == c;
   boolean b6 = b.equals(c);
```


## Problem 17 
For the previous problem, here is
an outline for the definition of class A.
```java
   class A
   {
      private int n, m;
      public A(int n, int m){this.n=n; this.m=m;}
   }
```
Write the definition for an equals() method that
overrides the equals() method from the Object class.
With the same definitions for a, b, and c from the
previous problem, your equals() method should give
the following results.
```java
   boolean b2 = a.equals(b);  // true
   boolean b4 = a.equals(c);  // true
   boolean b6 = b.equals(c);  // true
```


## Problem 18 
Consider the following class definition.
```java
   class TwoPairs
   {
      private int x1, y1, x2, y2;

      public TwoPairs(int x1, int y1, int x2, int y2)
      {
         this.x1 = x1;
         this.y1 = y1;
         this.x2 = x2;
         this.y2 = y2;
      }

      // implement toString()

   }
```
Write an implementation that overrides the toString()
method from the Object class so that the following
lines of code,
```java
   TwoPairs tp1 = new TwoPairs(3, 4, 5, 6);
   TwoPairs tp2 = new TwoPairs(0, -1, -2, 10);
   System.out.println( tp1 );
   System.out.println( tp2 );
```
print the following lines of text.
<pre>
TwoPairs: <3, 4> and <5, 6>
TwoPairs: <0, -1> and <-2, 10>
</pre>