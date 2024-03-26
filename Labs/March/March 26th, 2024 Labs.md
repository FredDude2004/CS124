# March 26th, 2024 Labs
## Lab 1
Write a recursive method that removes all the vowels from a String. The vowels are aeiou.

Use the "structural recursion" definition of a String:
<pre>
            /    ""             // base case
A String is | or
            \    char + String  // recursion
</pre>
If s0 is a single character String, then here is a nice way to check if s0 is a vowel.
<pre>
   "aeiou".indexOf(s0) >= 0
</pre>
If s0 is not in "aeiou", then the indexOf method return -1.

```java
import java.util.Scanner;

public class Main
{
   /**
      @return the input String with all its vowels removed
   */
   public static String remove(String str)  // recursive method
   {
      if (str.equals("") )
      {
         return "";
      }
      else  // recursive case
      {  
         String noVowels = remove(str.substring(1));
         String possibleVowel = str.substring(0,1); 
         if ("aeiou".indexOf(possibleVowel) < 0)
         {
            return possibleVowel + noVowels;
         }
         else
         {
            return noVowels;
         }
      }
   }
   
   public static void main(String[] args)
   {
      Scanner in = new Scanner(System.in);
      String s = in.nextLine();
      System.out.println( remove(s) );
   }
}
```

## Lab 2
Write a recursive method that takes as input an array of integers, a low index and a high index, and then replaces with 0 every negative number in the array between the low index and the high index (not including the high index).

For example, if the array holds
<pre>
[0, 1, -2, -3, -4, 5, 6, -7, -8, 9]
</pre>
and the low index is 3 and the high index is 8, then the array should be changed to
<pre>
[0, 1, -2, 0, 0, 5, 6, 0, -8, 9]
</pre>

```java
import java.util.Scanner;
import java.util.Arrays;

public class Main
{
   /**
      Write a recursive method that replaces every negative entry
      in the array between the index lo and the index hi (not
      including hi) with the value 0.
      
      If lo == hi, that represents an "empty" subarray with nothing
      that needs to be replaced.
      
      If lo > hi, throw IllegalArgumentException.
   */
   public static void convert(int[] arr, int lo, int hi)  // recursive method
   {
      if (lo == hi) {}
      else if (lo > hi)
      {
         throw new IllegalArgumentException("You're Gay");
      }
      else 
      {
         convert(arr, lo + 1, hi);
         if (arr[lo] < 0)
         {
            arr[lo] = 0;
         }
      }
   }


   public static void main(String[] args)
   {
      Scanner in = new Scanner(System.in);
      int length = in.nextInt();
      int[] array = new int[length];
      for (int i = 0; i < length; ++i)
      {
         array[i] = in.nextInt();
      }
      convert(array, 0, length);
      System.out.println( Arrays.toString(array) );
   }
}
```