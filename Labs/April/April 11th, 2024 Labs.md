# April 11th, 2024 Labs
## Lab 1

In this lab you will write a version of Selection Sort that sorts the rows of a 2-dimensional array.

Suppose we have a 2-dimensional array in which every row has two columns. Here is an example array.
<pre>
[ [2, 3], [4, 5], [2, 4], [1, 5], [3, 2], [2, 2], [4, 4], [4, 1] ]
</pre>
We want to sort the rows of this array. If we sort by just the first column from each row, then we don't know what order to put [2, 4] and [2, 2].. We need to use the second column as a "tie breaker" (like in the alphabetical ordering of words). So we will say that [2, 2] is less than (or, comes before) [2, 4].

Using this dictionary like order on the rows of the above array, it will sort to
<pre.>
[ [1, 5], [2, 2], [2, 3], [2, 4], [3, 2], [4, 1], [4, 4], [4, 5] ]
</pre>

```java
import java.util.Arrays;

public class Main
{
   public static void main(String[] args)
   {
      int[][] a = {{2,3}, {4,5}, {2,4}, {1,5}, {3,2}, {2,2}, {4,4}, {4,1}};
      System.out.println( Arrays.deepToString(a) );

      sort2D(a);
      System.out.println( Arrays.deepToString(a) );
   }


   /**
      Sort the rows of a 2-dimensional array, using selection sort.

      @param array2D the 2-dimensional array to sort
   */
   public static void sort2D(int[][] array2D)
   {
      for (int front = 0; front < array2D.length - 1; ++front)
      {
         int minRow = minimumRow(array2D, front);
         swapRows(array2D, minRow, front);
      }
   }


   /**
      Find the smallest row in a tail range of a 2-dimensional array.

      Suppose that the 2-dimensional array has only 2 columns.
      So one row looks like this, [a, b].

      If [a_i, b_i] and [a_j, b_j] are two different rows,
      we say that
         [a_i, b_i] is "smaller" than [a_j, b_j]
      if
         a_i < a_j or ( a_i == a_j and b_i < b_j )

      Notice how this is like a "dictionary" ordering
      for the rows of the 2-dimensional array. We first
      compare the first entries in the rows. If the first
      entries agree, then we "tie break" using the second
      entries from the row.

      @param a the 2-dimensional array to sort
      @param fromIndex the first row in a to compare
      @return the smallest row from the range a[fromIndex] ... a[a.length - 1]
   */
   private static int minimumRow(int[][] a, int fromIndex)
   {
      int minRow = fromIndex; // initial guess of where the minimum row is positioned
      for (int i = fromIndex; i < a.length; i++)
      {
         if (a[i][0] < a[minRow][0] || (a[i][0] == a[minRow][0] && a[i][1] < a[minRow][1]))
         {
            minRow = i;
         }
      }
            
      return minRow;
   }


   /**
      Swap two rows of a 2-dimensional array.

      @param a the 2-dimensional array
      @param i the first row to swap
      @param j the second row to swap
   */
   public static void swapRows(int[][] a, int i, int j)
   {
      int[] temp = new int[2];
      temp[0] = a[i][0];
      temp[1] = a[i][1];

      a[i][0] = a[j][0];
      a[i][1] = a[j][1];
      
      a[j][0] = temp[0];
      a[j][1] = temp[1];
   }
}
```

## Lab 2 
In this lab you will write another version of Selection Sort that sorts the rows of a 2-dimensional array.

Suppose we have a 2-dimensional array in which every row has two columns. Here is an example array.
<pre>
[ [2, 3], [4, 5], [2, 4], [1, 5], [3, 2], [2, 2], [4, 4], [4, 1] ]
</pre>
We want to sort the rows of this array by the sum of each row. One row of the array is "less than" another row if the sum of the entries from that row is less than the sum from the other row.

Using this ordering on the rows of the above array, it will sort to
<pre>
[ [2, 2], [3, 2], [2, 3], [4, 1], [2, 4], [1, 5], [4, 4], [4, 5] ]
</pre>

```java
import java.util.Arrays;

public class Main
{
   public static void main(String[] args)
   {
      int[][] a = {{2,3}, {4,5}, {2,4}, {1,5}, {3,2}, {2,2}, {4,4}, {4,1}};
      System.out.println( Arrays.deepToString(a) );

      sort2D(a);
      System.out.println( Arrays.deepToString(a) );
   }


   /**
      Sort the rows of a 2-dimensional array, using selection sort.

      @param array2D the 2-dimensional array to sort
   */
   public static void sort2D(int[][] array2D)
   {
      for (int front = 0; front < array2D.length - 1; ++front)
      {
         int minRow = minimumRow(array2D, front);
         swapRows(array2D, minRow, front);
      }
   }


   /**
      Find the smallest row in a tail range of a 2-dimensional array.

      Suppose that the 2-dimensional array has only 2 columns.
      So one row looks like this, [a, b].

      If [a_i, b_i] and [a_j, b_j] are two different rows,
      we say that
         [a_i, b_i] is "smaller" than [a_j, b_j]
      if
         a_i + b_i < a_j + b_j

      @param a the 2-dimensional array to sort
      @param fromIndex the first row in a to compare
      @return the smallest row from the range a[fromIndex] ... a[a.length - 1]
   */
   private static int minimumRow(int[][] a, int fromIndex)
   {
      int minRow = fromIndex; // initial guess of where the minimum row is positioned
      for (int i = fromIndex; i < a.length; i++)
      {
         if (a[i][0] + a[i][1] < a[minRow][0] + a[minRow][1])
         {
            minRow = i;
         }
      }
            
      return minRow;
   }


   /**
      Swap two rows of a 2-dimensional array.

      @param a the 2-dimensional array
      @param i the first row to swap
      @param j the second row to swap
   */
   public static void swapRows(int[][] a, int i, int j)
   {
      int[] temp = new int[2];
      temp[0] = a[i][0];
      temp[1] = a[i][1];

      a[i][0] = a[j][0];
      a[i][1] = a[j][1];
      
      a[j][0] = temp[0];
      a[j][1] = temp[1];
   }
}
```