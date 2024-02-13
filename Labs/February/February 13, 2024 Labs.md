# February 13th, 2024 Lab
## Lab 1
This lab is a puzzle that you have to solve.

The A, B, C, and D classes below have the following inheritance tree.
<pre>
         A
        / \
       /   \
      B     C
            |
            |
            D
</pre>
Every class has a method called method_1. You have to write an implementation for each method_1 so that the output of your code matches the correct output.

Start by immediately submitting the code given below for grading. The given code will not produce any output, but you will get to see what the required output looks like. Then look at the code in the Tester.java program and compare that code to the required output. The code in Tester.java polymorphically calls method_1 on the objects in an array. Match up the order of the objects in the array with the lines of output and figure out exactly what the implementation of method_1 needs to be in each class. Remember that any given method_1 can possibly call its super class version of method_1.

### Class A
```java
public class A
{
   private String secret;

   public void setSecret(String secret)
   {
      this.secret = secret;
   }

   public void method_1()
   {
      System.out.println("method_1 in class A, my secret is " + this.secret);
   }
}
```

### Class B
```java
public class B extends A
{
   @Override
   public void method_1()
   {
      super.method_1();
   }
}
```

### Class C
```java
public class C extends A
{
   private String secret;

   public void setSecret(String secret)
   {
      this.secret = secret;
   }

   @Override
   public void method_1()
   {
      System.out.println("method_1 in class C, my secret is " + this.secret);
   }
}
```

### Class D
```java
public class D extends C
{
   @Override
   public void method_1()
   {
      super.method_1();
      System.out.println("method_1 in class D");
   }
}
```

### Tester
```java
import java.util.Scanner;

public class Tester
{
   public static void main(String[] args)
   {
      Scanner in = new Scanner(System.in);
      final int testCase = in.nextInt();
      if (1 == testCase)
      {
         A[] array_of_A = new A[6];

         array_of_A[0] = new B();
         array_of_A[1] = new D();
         array_of_A[2] = new A();
         array_of_A[3] = new C();
         array_of_A[4] = new B();
         array_of_A[5] = new D();

         array_of_A[0].setSecret("apples");
         array_of_A[1].setSecret("banana");
         array_of_A[2].setSecret("grape");
         array_of_A[3].setSecret("oranges");
         array_of_A[4].setSecret("pears");
         array_of_A[5].setSecret("watermelon");

         for (A a : array_of_A)
         {
            a.method_1();
         }
      }
      else if (2 == testCase)
      {
         A[] array_of_A = new A[6];

         array_of_A[0] = new B();
         array_of_A[1] = new D();
         array_of_A[2] = new A();
         array_of_A[3] = new C();
         array_of_A[4] = new B();
         array_of_A[5] = new D();

         array_of_A[0].setSecret("cat");
         array_of_A[1].setSecret("bear");
         array_of_A[2].setSecret("dog");
         array_of_A[3].setSecret("horse");
         array_of_A[4].setSecret("panda");
         array_of_A[5].setSecret("wolf");

         for (A a : array_of_A)
         {
            a.method_1();
         }
      }
      else
      {
         System.out.println("Please provide a test case number between 1 and 2.");
      }
   }
}
```