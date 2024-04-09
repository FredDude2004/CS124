
Conversation opened. 1 unread message.

Skip to content
Using Purdue University Northwest Mail with screen readers

1 of 101
Todays Lab
Inbox

Kaleb Michael Duchesneau <kduchesn@pnw.edu>
1:12 PM (45 minutes ago)
to me

# July 9th, 2024 Labs
Write a method called uniqueElements that takes an array of integers and returns an array containing all the unique integers from the input array without any duplicates. For example, if the array arr contains
<pre>
   int[] arr = {1, 5, 2, 4, 2, 3, 5, 1, 4, 6};
</pre>
then uniqueElements(arr) should return this array.
<pre>
[1, 5, 2, 4, 3, 6]
</pre>
Notice that the elements in this array have the same order that they had in the original array, but without the repetitions.

Here is the algorithm that you should use. Create an empty ArrayList called uniques. Put the first element from the input array into the list. For each other element from the input array, determine if it appears earlier in the array. If not, then put it in the list.

After you have checked every element from the input array, check the length of the list and create a second array with that size. Copy the elements from the list into the second array. Return the second array.

```java
import java.util.ArrayList;
import java.util.Arrays;

public class Main
{
   public static void main(String[] args)
   {
      int[] arr1 = {1, 5, 2, 4, 2, 3, 5, 1, 4, 6};
      int[] arr2 = uniqueElements(arr1);
      System.out.println( Arrays.toString(arr1) );
      System.out.println( Arrays.toString(arr2) );
   }


   public static int[] uniqueElements(int[] arr)
   {
      // Create the empty ArrayList, uniques.
      ArrayList<Integer> uniques = new ArrayList<>();
     
      // Put the first element from arr into uniques.
      uniques.add(arr[0]);
     
      // For every other element from arr, check if it is a
      for (int i = 1; i < arr.length; i++)
      {
         // repetition of some element from its left in the array.
         boolean unique = true;
         for (int j = 0; j < i; j++)
         {
            if (arr[i] == arr[j])
            {
               unique = false;
            }
         }
         // If the element from arr is not a repetition, then put it in uniques.
         if (unique)
         {
            uniques.add(arr[i]);
         }
      }
     
      // Create a new array whose length is the same as the size of uniques.
      int[] resultUniques = new int[uniques.size()];
     
      // Copy all the elements from uniques into the new array.
      for (int i = 0; i < resultUniques.length; i++)
      {
         resultUniques[i] = uniques.get(i);
      }
     
      // Return the new Array.
      return resultUniques;
     
   }
}
```

