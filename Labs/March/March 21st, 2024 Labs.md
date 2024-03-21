# March 21st, 2024 Labs
## Lab 1
Write a recursive method that takes a single positive integer parameter, n, and draws a triangle that "ponts down", like this (for n = 5).
<pre>
*****
****
***
**
*
</pre>
Notice that a triangle of size n is a row of n stars with a triangle of size n-1 below the row.

Use a for-loop to draw the row of stars and then use recursion to draw the triangle below the row of stars.

Your base case will be a triangle of size 1 (just one star).

When your recursive method gets to its base case, just before it returns have your method print a stack trace using this line of code.
<pre>
   new Exception().printStackTrace(System.out);
</pre>

```java
import java.util.Scanner;

public class Main
{
   public static void drawTriangle(int n) // recursive function
   {
      if(n == 1) // base case, stops the recursion
      {
         System.out.println("*");
         new Exception().printStackTrace(System.out);
      }
      else // recursive case
      {
         for (int i = 0; i < n; i++)
         {
            System.out.print("*");
         }
         System.out.println();
         drawTriangle(n - 1);
      }
     
   }
   
   public static void main(String[] args)
   {
      Scanner in = new Scanner(System.in);
      int n = in.nextInt();
      drawTriangle(n);
   }
}
```

## Lab 2
Write a recursive method that takes a single positive integer parameter, n, and returns a String made up of n less-than symbols followed by n greater-than symbols. So if n = 5, your method should return this string.
<pre>
<<<<<>>>>>
</pre>
Let us call a string like this a "progress-bar".

Notice that a progress-bar has the following recursive definition.

A progress-bar of size n is a '<' followed by a progress-bar of size n-1 followed by a '>'.

Your base case should be a progress-bar of size 0, which is the empty string, "".

When your recursive method gets to its base case, just before it returns have your method print a stack trace using this line of code.
<pre>
   new Exception().printStackTrace(System.out);
</pre>

```java
import java.util.Scanner;

public class Main
{
   public static String progreessBar(int n) // recursive function
   {
      if (n == 0)
      {
         new Exception().printStackTrace(System.out);
         return "";
      }
      else
      {
         String ProgressBar = progreessBar(n - 1);
         return "<" + ProgressBar + ">";
      }
   }
   
   public static void main(String[] args)
   {
      Scanner in = new Scanner(System.in);
      int n = in.nextInt();
      System.out.println( progreessBar(n) );
   }
}
```