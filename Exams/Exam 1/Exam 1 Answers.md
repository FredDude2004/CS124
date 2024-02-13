# Exam 1 Reveiw 
## Question 1
```java
import java.util.ArrayList;
import java.util.Arrays;

public class Main
{
	public static void main(String[] args) {
        ArrayList<Integer> myList = new ArrayList<>(Arrays.asList(2, 3, 5));
        myList.add(0, 1);
        myList.add(3, 4);
        myList.add(6);
        
        for (int value : myList)
        {
            System.out.print(value + " ");
        }
	}
}
```

## Question 2 
### a) 
<pre>
[1, 10, 1, 11, 1, 12, 2, 10, 2, 11, 2, 12, 3, 10, 3, 11, 3, 12]
</pre>

For each item in list1 it will loop all the way through list2, adding the item from list1 followed by the 
item in list2 that comes next. It will repeat that process until you reach the end of the second loop, then 
it will change the item from list1 

so you get somthing like 
l1a, l2a, l1a, l2b, l1a, l2c, l1b, l2a, . . . 

### b)
<pre>
[12, 3, 11, 3, 10, 3, 12, 2, 11, 2, 10, 2, 12, 1, 11, 1, 10, 1]
</pre>

It will reverse the order because it is continually adding the items to the start of list3

### c) 
```java
import java.util.ArrayList;
import java.util.Arrays;

public class Main
{
	public static void main(String[] args) {
        ArrayList<Integer> list1 = new ArrayList<>(Arrays.asList(1, 2, 3));
        ArrayList<Integer> list2 = new ArrayList<>(Arrays.asList(10, 11, 12));
        ArrayList<Integer> list3 = new ArrayList<>();
        for (int i : list1)
        {
            list3.add(i);
            for (int j : list2)
            {
               list3.add(j);
            }
        }
        System.out.println( list3 );
	}
}
```
Put the first add statment above the nest, and it will solve the problem, by not also printing out 
the first item for each item in list2

## Question 3 
2
<pre>
a --> null

b --> A instance
     | a | 100 |

c -- A instance
     | a | 150 |
</pre>
The a is a null pointer value, so its "garbage" and we don't count it.

## Question 4 
1
<pre>
a1 --> null
        ^
a2 -----| 

a3 -- A instance
     | a | 250 |
</pre>
a1 and a2 both point at null, so they are "garbage" and we don't count them. 

## Question 5 
<pre>
pairs --> | 1 | --> | null | null | null |
          | 2 | --> | null |      | null |
                               |
                               |
                               ---> Pair instance
                                    | p1 | 200 |
                                    | p2 | 100 | 
</pre>

## Question 6 
<pre>
x = a=2 and b=1
y = 1
</pre>

First you create a "Thing" object that holds two public integer values 'a' and 'b', construct it to hold the values 1 and 1, and you create a reference variable 'x' that points to that "Thing" object. then you create a integer variable 'y' and set it equal to 1. Next you call the 'f' method which increments the 'a' value in the thing object 'x', so that it equals 2. the method also increments the y variable but it is never returned so it has no effect. Then you print out "x = " and the values in the Thing object 'x', new line "y = " and the value of the y variable which is 1. Giving you you're final output. 

## Question 7 
### a) 
```java
public class Main 
{
   public static void main(String[] args) 
   {
      Point center = new Point(2, 3);
      Circle c1 = new Circle(center, 5);
   }
}
```
### b) 
```java
public Point getCenter()
{
    return new Point(this.x, this.y);
}
```

## Question 8
<pre>
8
catdog
cat35
dog5cat
</pre>

Because each method takes parameters with different data types. 
So whatever data types you put call the method with determines what will happen. 

## Question 9
<pre>
        A
       / \
      B   D
      |
      C
     / \
    E   F
    |   |
    G   H
</pre>

## Question 10
<pre>
         A
    I   / \
   / \ /   B
  C J-F    |
  |/       E
  D
</pre>
## Question 11
```java
   class A1 { // doesn't use the keyword abstract when declaring the class
      abstract void unfinished();
   }

   abstract class A2 {
      abstract void unfinished(){ } // abstract methods can't have a body {}
   }

   abstract class A4 {
      private abstract void unfinished(); // abstact method can't be private
   }
```
This is the only one that is declared properly
```java
abstract class A3 {
    abstract void unfinished();
}
```

## Question 12
```java
A a = new B(1,2);       /*1 */
B b = new C(3,4,5);     /*2 */
C c = new C(6,7,8);     /*3 */
// C d = new A(6,7,8);  /*4 */
int a1 = a.getA();      /*5 */
// a.setB(10);          /*6 */
int a2 = b.getA();      /*7 */
// int b2 = b.getb();   /*8 */
// int c2 = b.getC();   /*9 */
int a3 = c.getA();      /*10*/
c.setB(10);             /*11*/
// ((C)a).setB(11);     /*12*/
((C)b).setB(12);        /*13*/
int b3 = ((C)b).getC(); /*14*/
```

Line 4 doesn't compile because a 'C' reference type cannot refer to an 'A' object because it is above it in the tree

Line 6 doesn't compile because a is an 'A' reference type refering to a 'B' object, so because it is an 'A' reference type, when it calls the method "setB()" it looks for the method in the A class and cannot find it. 

Line 8 the method call has a typo, "setb()" should be uppercase B --> "setB()"

Line 9 doesn't compile because a is an 'B' reference type refering to a 'C' object, so because it is a 'B' reference type, when it calls the method "getC()" it looks for the method in the B class and cannot find it. 

Line 12 doesn't work because it tries to cast a 'B' refence type to a 'C' reference type which is below it in the tree

## Question 13
```java
A a1 = new A();
A a2 = new C();
D d1 = new D();
   
A a3 = new B();      /*1*/  
// B b1 = new A();   /*2*/  
// B b2 = (B) a1;    /*3*/  
B b3 = (B) a2;       /*4*/  
// B b4 = (B) d1;    /*5*/  
```
Line 2 doesn't compile because a 'B' reference type cannot refer to an 'A' object because it is above it in the tree

Line 3 will have a runtime error because it tries to cast an 'A' reference type refering to an 'A' object, to a 'B' reference type and you can't refer to an object above you in the tree. Because of the beetle.

Line 5 bad casting smd

## Question 14
### a)
```java
C c = new D();
c.????(...);
```
we can call methods from the C, A, G, and Object class definitions
### b) 
```java
G g = new ?();
```
You can replace the '?' with C, D, or E because they all implement or inherit the G interface. 

### c) 
```java
? x = new E();
```
you can replace the '?' with a E, C, A, G, or Object because those are all above E in the tree. 

### d)
Can only cas to A to run, think through the trr, for it to compile all possibilities are A, G, D, E, and Object

## Question 15 
### a) 
super and this used as method names calls the constructor in that class. so "super(x, y)" would call the constructor in the super class, and "this(x, y)" would call the constructor in this class.

### b) 
using super and this as calling objects will call the method in that class. So say that you override a method in and class that extends another class. But you want to call the method in the super class, you would use the super keyword to call he method in the super class, not the method in the 

## Question 16 
b1 --> false
b2 --> false
b3 --> false
b4 --> false
b5 --> true
b6 --> true

## Question 17 
```java
public boolean equals(A a)
{
    return (this.n == a.n && this.m == a.m);
}
```

## Question 18
```java
@Override
public String toString()
{
    String result = "TwoPairs: <" + x1 + ", " + y1 + ">";
    result += " and <" + x2 + ", " + y2 + ">";
    return result;
}
```