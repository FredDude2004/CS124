# January 16th, 2024 Labs
## Lab 1
Write a static method that takes as input an int array and returns a 2-dimensional int array.
<pre>
   public static int[][] split(int[] array)
</pre>
The 2-dim array should have three rows.

The first row should contain the zero integers from the input array.

The second row should contain the negative integers from the input array.

The third row should contain the positive integers from the input array.

The entries in each row should be in the same order that they were in in the input array.

Any one of the three rows could be an empty array (even all three of them).

Use an enhanced for-loop whenever possible.

```java
import java.util.Scanner;
import java.util.Arrays;

public class Main
{
   /**
      The 2-dim return array array should have three rows.

      The first row should contain the zero integers from the input array.
      The second row should contain the negative integers from the input array.
      The third row should contain the positive integers from the input array.

      The entries in each row should be in the same order that they were in in the input array,

      Any one of the three rows could be an empty array (even all three of them).

      Use an enhanced for-loop whenever possible.
   */
   public static int[][] split(int[] array)
   {
      // This is just the "array of rows". You still need
      // to create the three rows (after you know how big
      // each row needs to be).
      int[][] result = new int[3][];
     
      int zeroCount = 0;
      int negCount = 0;
      int posCount = 0;
     
      for (Integer value : array)
      {
         if (value == 0)
         {
            zeroCount++;
         }
         else if (value < 0)
         {
            negCount++;
         }
         else // value > 0
         {
            posCount++;
         }
      }
     
      result[0] = new int[zeroCount];
      result[1] = new int[negCount];
      result[2] = new int[posCount];
     
      int zeroIndex = 0;
      int negIndex = 0;
      int posIndex = 0;
     
      for (Integer value : array)
      {
         if (value == 0)
         {
            result[0][zeroIndex] = value;
            zeroIndex++;
         }
         else if (value < 0)
         {
            result[1][negIndex] = value;
            negIndex++;
         }
         else // value > 0
         {
            result[2][posIndex] = value;
            posIndex++;
         }
      }
     
      return result;
   }



   // Do not modify this main method.
   public static void main(String[] args)
   {
      final Scanner in = new Scanner(System.in);
     
      final int size = in.nextInt();
      final int[] array = new int[size];
      for (int i = 0; i < array.length; ++i)
      {
         array[i] = in.nextInt();
      }
      System.out.println(Arrays.toString(array));
      System.out.println();
     
      final int[][] splitArray = split(array);
      System.out.println(Arrays.deepToString(splitArray));
   }
}
```

## Lab 2
Write a static method that takes as input an ArrayList<Integer> and returns a "two-dimensional" ArrayList of ArrayLists, that is an ArrayList<ArrayList<Integer>>.
<pre>
   public static ArrayList<ArrayList<Integer>> split(ArrayList<Integer> list)
</pre>
The ArrayList<ArrayList<Integer>> should contain three (sub) lists.

The first list should contain the zero integers from the input list.

The second list should contain the negative integers from the input list.

The third list should contain the positive integers from the input list.

The entries in each sub list should be in the same order that they were in in the input list.

Any one of the three sub lists could be an empty list (even all three of them).

Use an enhanced for-loop whenever possible.

```java
import java.util.Scanner;
import java.util.ArrayList;
import java.util.Arrays;

public class Main
{
   /**
      The returned ArrayList<ArrayList<Integer>> should have three sub lists.

      The first sub list should contain the zero integers from the input list.
      The second sub list should contain the negative integers from the input list.
      The third sub list should contain the positive integers from the input list.

      The entries in each sub list should be in the same order that they were in in the input list,

      Any one of the three sub lists could be an empty list (even all three of them).

      Use an enhanced for-loop whenever possible.
   */
   public static ArrayList<ArrayList<Integer>> split(ArrayList<Integer> list)
   {
      // This is the outer ArrayList. You still need to create
      // the three sub lists (that act like rows) and add
      // each sub list to this list. Then add the appropriate
      // integers to each sub list.
      ArrayList<ArrayList<Integer>> result = new ArrayList<ArrayList<Integer>>();
     
      ArrayList<Integer> zero = new ArrayList<>();
      ArrayList<Integer> neg = new ArrayList<>();
      ArrayList<Integer> pos = new ArrayList<>();
     
      for (Integer value : list)
      {
         if (value == 0)
         {
            zero.add(value);
         }
         else if (value < 0)
         {
            neg.add(value);
         }
         else // value > 0
         {
            pos.add(value);
         }
      }
     
      result.add(0, zero);
      result.add(1, neg);
      result.add(2, pos);
     
      return result;
   }



   // Do not modify this main method.
   public static void main(String[] args)
   {
      final Scanner in = new Scanner(System.in);
      final ArrayList<Integer> list = new ArrayList<>();
      while ( in.hasNextInt() )
      {
         list.add( in.nextInt() );
      }
      System.out.println(list);
      System.out.println();
     
      final ArrayList<ArrayList<Integer>> splitList = split(list);
      System.out.println(splitList);
   }
}
```
