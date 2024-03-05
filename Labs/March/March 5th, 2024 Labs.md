# March 5th, 2024 Labs
## Lab 1
Write a program that uses a Scanner to try to read two tokens from System.in and then tries to convert each token to an integer value.

If there are two tokens and both tokens convert to an integer, then print out the their sum.

If there are two tokens and only one token converts to an integer, print out its value.

If there are two tokens and neither token converts to an integer, print out 0.

If there is only one token and it converts to an integer, then print out its value.

If there is only one token but it doesn't convert to an integer, then out print 0.

If there are no tokens, then print out 0.

You need to use a try-catch with a NumberFormatException to attempt to convert a token to an integer.

```java
import java.util.Scanner;
import java.util.InputMismatchException;
import java.util.NoSuchElementException;

public class Main
{
    public static void main(String[] args)
    {
        Scanner in = new Scanner(System.in);

        int x = 0;
        int y = 0;

        try
        {
            String token1 = in.next();
            x = Integer.parseInt(token1);
        }
        catch (InputMismatchException e)
        {
            //System.out.println(e);
        }
        catch (NoSuchElementException e)
        {
            //System.out.println(x);
        }
        catch (NumberFormatException e)
        {
            //System.out.println(e);
        }  

        try
        {
            String token2 = in.next();
            y = Integer.parseInt(token2);
        }
        catch (InputMismatchException e)
        {
            //System.out.println(e);
        }
        catch (NoSuchElementException e)
        {
            //System.out.println(x);
        }
        catch (NumberFormatException e)
        {
            //System.out.println(e);
        }  

        System.out.println(x+y);
    }
}
```

## Lab 2
Complete the definition of the method lookupAndConvert() in the Main.java file. The method should catch any exceptions that can happen when it looks up a String in its parameter array and tries to convert it to an int. If an exception should happen, the method should print an appropriate error message (submit the program to see what the error messages should be) and return -1.

The Tester.java program tests your version of the lookupAndConvert() method. The Tester program has three test cases with input 1 or 2 or 3.

### Main.java
```java
import java.util.Scanner;
import java.util.InputMismatchException;
import java.util.NoSuchElementException;

public class Main
{
    public static int lookupAndConvert(String[] num, int index)
    {
        int x = -1;
        try
        {
            x = Integer.parseInt( num[index] );
        }
        catch (NumberFormatException e)
        {
            System.out.println("Error: bad integer.");
            return x;
        }
        catch (ArrayIndexOutOfBoundsException e)
        {
            System.out.println("Error: bad index.");
            return x;
        }
        catch (NullPointerException e)
        {
            System.out.println("Error: bad reference.");
            return x;
        }

        return x;
    }
}
```

### Tester.java
```java
import java.util.Scanner;

public class Tester
{
   public static void main(String[] args)
   {
      String[] nums = {"11", "two", "3", "four", "55", "6.5"};
      Scanner in = new Scanner(System.in);
      int testCase = in.nextInt();
      if (testCase == 1)
      {
         System.out.println( Main.lookupAndConvert(nums, 0) );
         System.out.println( Main.lookupAndConvert(nums, 2) );
         System.out.println( Main.lookupAndConvert(nums, 6) );
      }
      else if (testCase == 2)
      {
         System.out.println( Main.lookupAndConvert(nums, 4) );
         System.out.println( Main.lookupAndConvert(nums, 1) );
         System.out.println( Main.lookupAndConvert(nums, 5) );
      }
      else if (testCase == 3)
      {
         System.out.println( Main.lookupAndConvert(null, 0) );
         System.out.println( Main.lookupAndConvert(nums, -1) );
         System.out.println( Main.lookupAndConvert(new String[]{"1001"}, 0) );
      }
      else
      {
         System.out.println("Please enter a test case number between 1 and 3.");
      }
   }
}
```