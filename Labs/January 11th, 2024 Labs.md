# January 11th, 2024 Labs
## Lab 1
```java
import java.util.ArrayList;
import java.util.Arrays;

public class ArrayList_problem_1
{
   /**
      The ArrayList returned by this method should contain those
      entries from the input list that are strictly greater than
      the input integer n. The input list should not be changed.

      Write this method using an enhanced for-loop.
   */
   public static ArrayList<Integer> filter(int n, ArrayList<Integer> list)
   {
      ArrayList<Integer> result = new ArrayList<>();
      for (Integer value : list)
      {
         if (value > n)
         {
            result.add(value);
         }
      }
      return result;
   }



   public static void main(String[] args)
   {
      ArrayList<Integer> list1 = new ArrayList<>(Arrays.asList(1,2,3,4));
      ArrayList<Integer> list2 = new ArrayList<>(Arrays.asList(5,6));
      ArrayList<Integer> list3 = new ArrayList<>(Arrays.asList(5,4,3,2,1));
      ArrayList<Integer> list4 = new ArrayList<>(Arrays.asList(3,4,5,6,7,8,9,10));

      ArrayList<Integer> list1a = filter(1, list1);
      ArrayList<Integer> list2a = filter(6, list2);
      ArrayList<Integer> list3a = filter(3, list3);
      ArrayList<Integer> list4a = filter(1, list4);

      System.out.println(list1 + "   " + list1a);
      System.out.println(list2 + "   " + list2a);
      System.out.println(list3 + "   " + list3a);
      System.out.println(list4 + "   " + list4a);
   }
}
```

## Lab 2
```java
import java.util.ArrayList;
import java.util.Arrays;

public class ArrayList_problem_2
{
   /**
      The ArrayList returned by this method should contain all the
      entries from the input list but with all the 0 numbers from
      the input list coming first, followed by the all the negative
      numbers from the input list, followed by all the positive numbers.

      Write this method using an enhanced for-loop.

      Hint: Use three temporary list objects and then
      combine them together using the addAll() method.
   */
   public static ArrayList<Integer> split(ArrayList<Integer> list)
   {
      ArrayList<Integer> zero = new ArrayList<>();
      ArrayList<Integer> negative = new ArrayList<>();
      ArrayList<Integer> posotive = new ArrayList<>();
     
      for (Integer value : list)
      {
         if (value == 0)
         {
            zero.add(value);
         }
         else if (value < 0)
         {
            negative.add(value);
         }
         else // (value > 0)
         {
            posotive.add(value);
         }
      }
     
      zero.addAll(negative);
      zero.addAll(posotive);
      return zero;
   }



   public static void main(String[] args)
   {
      ArrayList<Integer> list1 = new ArrayList<>(Arrays.asList(0-1,0,-2,0,3,0,-4,0));
      ArrayList<Integer> list2 = new ArrayList<>(Arrays.asList(5,-6,0));
      ArrayList<Integer> list3 = new ArrayList<>(Arrays.asList(-5,0,3,0,-2,1,-1));
      ArrayList<Integer> list4 = new ArrayList<>(Arrays.asList(3,-4,-5,0,6,-7,8,9,-10,0));

      ArrayList<Integer> list1a = split(list1);
      ArrayList<Integer> list2a = split(list2);
      ArrayList<Integer> list3a = split(list3);
      ArrayList<Integer> list4a = split(list4);

      System.out.println(list1 + "   " + list1a);
      System.out.println(list2 + "   " + list2a);
      System.out.println(list3 + "   " + list3a);
      System.out.println(list4 + "   " + list4a);
   }
}
```

## Lab 3
```java
import java.util.ArrayList;
import java.util.Arrays;

public class ArrayList_problem_3
{
   /**
      If one of the input lists is longer that the other one,
      then remove an appropriate number of elements from the front
      of the longer list and add them at the front of the shorter
      list so that the longer list ends up at most one item longer
      than the shorter list.

      balance([1,2,3,4], [5,6]) should take one element from the
      front of the first list and place it at the front of the
      second list, [2,3,4] and [1,5,6].

      balance([1,2], [3,4,5,6,7,8,9,10]) should take three elements
      from the front of the second list and place them at the front
      of the first list, [5,4,3,1,2] and [6,7,8,9,10].

      balance([1,2,3], [4,5]) should not change either list.

      balance([1,2,3,4,5,6,7,8], [9,10,11]) should take two elements
      from the front of the first list and place them at the front of
      the second list, [3,4,5,6,7,8] and [2,1,9,10,11].
*/
   public static void balance(ArrayList<Integer> list1,
                              ArrayList<Integer> list2)
   {
      if (list1.size() < list2.size())
      {
         ArrayList<Integer> tempList = list1;
         list1 = list2;
         list2 = tempList;
      }
     
      while (list1.size() > list2.size() + 1)
      {
         list2.add(0, list1.remove(0));
      }
   }

   public static void main(String[] args)
   {
      ArrayList<Integer> list1 = new ArrayList<>(Arrays.asList(1,2,3,4));
      ArrayList<Integer> list2 = new ArrayList<>(Arrays.asList(5,6));
      ArrayList<Integer> list3 = new ArrayList<>(Arrays.asList(1,2));
      ArrayList<Integer> list4 = new ArrayList<>(Arrays.asList(3,4,5,6,7,8,9,10));
      ArrayList<Integer> list5 = new ArrayList<>(Arrays.asList(1,2,3));
      ArrayList<Integer> list6 = new ArrayList<>(Arrays.asList(4,5));
      ArrayList<Integer> list7 = new ArrayList<>(Arrays.asList(1,2,3,4,5,6,7,8));
      ArrayList<Integer> list8 = new ArrayList<>(Arrays.asList(9,10,11));
     
      balance(list1, list2);
      balance(list3, list4);
      balance(list5, list6);
      balance(list7, list8);

      System.out.println(list1 + "   " + list2);
      System.out.println(list3 + "   " + list4);
      System.out.println(list5 + "   " + list6);
      System.out.println(list7 + "   " + list8);
   }
}
```
