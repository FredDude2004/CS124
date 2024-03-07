# March 7th, 2024 Lab

## Lab 1

Complete the definitions of the classes ClassA.java, ClassB.java, ClassC.java and ClassD.java so that when Main.java is run, it produces the following stack trace.



Exception in thread "main" java.lang.NumberFormatException: For input string: "12.3"

        at java.base/java.lang.NumberFormatException.forInputString(NumberFormatException.java:67)

        at java.base/java.lang.Integer.parseInt(Integer.java:668)

        at java.base/java.lang.Integer.parseInt(Integer.java:786)

        at ClassD.methodC(ClassD.java:17)

        at ClassD.methodA(ClassD.java:5)

        at ClassD.methodB(ClassD.java:11)

        at ClassC.methodA(ClassC.java:5)

        at ClassC.methodC(ClassC.java:17)

        at ClassB.methodB(ClassB.java:11)

        at ClassC.methodB(ClassC.java:11)

        at ClassB.methodA(ClassB.java:5)

        at ClassA.methodA(ClassA.java:5)

        at Main.main(Main.java:5)



You need to read this stack trace carefully and "reverse engineer" it to figure out what methods to put in each class and what other method each method should call. Notice that, to get the correct output, your code has to have all the correct line numbers.

### Main.java
```java
public class Main
{
   public static void main(String[] args)
   {
      ClassA.methodA();
      System.out.println("Main.main is done.");
   }
}
```

### ClassA.java
```java
public class ClassA
{
    public static void methodA()
    {
        ClassB.methodA();
    }
}
```

### ClassB.java
```java
public class ClassB
{
    public static void methodA()
    {
        ClassC.methodB();
    }

    public static void methodB()
    {

        ClassC.methodC();
    }
}
```

### ClassC.java
```java
public class ClassC
{
    public static void methodA()
    {
        ClassD.methodB();
    }

    public static void methodB()
    {

        ClassB.methodB();
    }

    public static void methodC()
    {

        ClassC.methodA();
    }
}
```

### ClassD.java
```java
public class ClassD
{
   public static void methodA()
   {
      ClassD.methodC();
   }
   
   
   public static void methodB()
   {
      ClassD.methodA();
   }
 
   
   public static void methodC()
   {
      int n = Integer.parseInt("12.3");
   }
}
```

### out.txt
<pre>
Exception in thread "main" java.lang.NumberFormatException: For input string: "12.3"
        at java.base/java.lang.NumberFormatException.forInputString(NumberFormatException.java:67)
        at java.base/java.lang.Integer.parseInt(Integer.java:668)
        at java.base/java.lang.Integer.parseInt(Integer.java:786)
        at ClassD.methodC(ClassD.java:17)
        at ClassD.methodA(ClassD.java:5)
        at ClassD.methodB(ClassD.java:11)
        at ClassC.methodA(ClassC.java:5)
        at ClassC.methodC(ClassC.java:17)
        at ClassB.methodB(ClassB.java:11)
        at ClassC.methodB(ClassC.java:11)
        at ClassB.methodA(ClassB.java:5)
        at ClassA.methodA(ClassA.java:5)
        at Main.main(Main.java:5)

</pre>
