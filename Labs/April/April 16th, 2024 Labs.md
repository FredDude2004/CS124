# April 16th, 2024 Labs
## Lab 1 
In this lab you will write a version of Insertion Sort that sorts a List of Triple objects.

A Triple is an object that holds three integers. Here is an example of a List of Triple objects.
<pre>
[<2, 3, 2>, <4, 4, 1>, <2, 4, 0>, <5, 1, 1>, <0, 6, 3>, <2, 2, 2>, <4, 1, 4>, <5, 0, 4>]
</pre>
We want to sort lists of triples. There are many ways in which we can compare two Triple objects and decide which one is the lesser of the two. For this lab, we will compare two triples by comparing the sum of their components. If the sums are equal, we will use the first number from each triple as a tie breaker. If the first numbers are equal, use the second number as the second tie breaker.

So <a,b,c> is less than <x,y,z> if a+b+c<x+y+z, or if a+b+c==x+y+z and a<x, or if a+b+c==x+y+z and a==x and b<y. (Why do we not need another tie breaker?)

Using this order, the triples in the above list will sort to
<pre>
[<2, 2, 2>, <2, 4, 0>, <2, 3, 2>, <5, 1, 1>, <0, 6, 3>, <4, 1, 4>, <4, 4, 1>, <5, 0, 4>]
</pre>

```java
import java.util.List;

/**
   The sort method of this class sorts an array
   using the recursive selection sort algorithm.
*/
public class InsertionSort
{
   /**
      Sort a List of Triple objects using recursive insertion sort.

      @param list the List to sort
   */
   public static void sort(List<Triple> list)
   {
      if (list.isEmpty())
      {
         return;
      }
      else
      {
         Triple first = list.remove(0);
         sort(list);
         insert(first, list);
      }
   }


   /**
      @param list a sorted List of Triple objects
      @param n a Triple object to insert into the sorted List
   */
   public static void insert(Triple n, List<Triple> list)
   {
      if (list.isEmpty())
      {
         list.add(0, n);
      }
      else if (lessThan(n, list.get(0)))
      {
         list.add(0, n);
      }
      else
      {
         Triple first = list.remove(0);
         insert(n, list);
         list.add(0, first);
      }
   }


   /**
      Compare two Triple objects and determine if
      the fisrt one is "less than" the second one.

      @param t1 1st Triple object
      @param t2 2nd Triple object
      @return true if t1 is "less than" t2
   */
   public static boolean lessThan(Triple t1, Triple t2)
   {
      int sum1 = t1.x + t1.y + t1.z;
      int sum2 = t2.x + t2.y + t2.z;
      
      if (sum1 < sum2) { return true; }
      else if (sum1 == sum2 && t1.x < t2.x) { return true; }
      else if (sum1 == sum2 && t1.x == t2.x &&  t1.y < t2.y) { return true; }
      else { return false; }
   }
}
```

## Lab 2 
Redo Lab 1 using the following order on Triple objects.

Compare two triples by comparing the sum of their components. If the sums are equal, we will use the sum of the first two components from each triple as a tie breaker. If the sums of the first numbers are equal, use the first number as the second tie breaker.

So <a,b,c> is less than <x,y,z> if a+b+c<x+y+z, or if a+b+c==x+y+z and a+b<x+y, or if a+b+c==x+y+z and a+b==x+y and a<x.

Using this order, the triples in the following list
<pre>
[<2, 3, 2>, <4, 4, 1>, <2, 4, 0>, <5, 1, 1>, <0, 6, 3>, <2, 2, 2>, <4, 1, 4>, <5, 0, 4>]
</pre>
will sort to
<pre>
[<2, 2, 2>, <2, 4, 0>, <2, 3, 2>, <5, 1, 1>, <4, 1, 4>, <5, 0, 4>, <0, 6, 3>, <4, 4, 1>]
</pre>

```java
import java.util.List;

/**
   The sort method of this class sorts an array
   using the recursive selection sort algorithm.
*/
public class InsertionSort
{
   /**
      Sort a List of Triple objects using recursive insertion sort.

      @param list the List to sort
   */
   public static void sort(List<Triple> list)
   {
      if (list.isEmpty())
      {
         return;
      }
      else
      {
         Triple first = list.remove(0);
         sort(list);
         insert(first, list);
      }
   }


   /**
      @param list a sorted List of Triple objects
      @param n a Triple object to insert into the sorted List
   */
   public static void insert(Triple n, List<Triple> list)
   {
      if (list.isEmpty())
      {
         list.add(0, n);
      }
      else if (lessThan(n, list.get(0)))
      {
         list.add(0, n);
      }
      else
      {
         Triple first = list.remove(0);
         insert(n, list);
         list.add(0, first);
      }
   }


   /**
      Compare two Triple objects and determine if
      the fisrt one is "less than" the second one.

      @param t1 1st Triple object
      @param t2 2nd Triple object
      @return true if t1 is "less than" t2
   */
   public static boolean lessThan(Triple t1, Triple t2)
   {
      int sum1 = t1.x + t1.y + t1.z;
      int sum2 = t2.x + t2.y + t2.z;
      
      if (sum1 < sum2) { return true; }
      else if (sum1 == sum2 && t1.x + t1.y < t2.x + t2.y) { return true; }
      else if (sum1 == sum2 && t1.x + t1.y == t2.x + t2.y &&  t1.x < t2.x) { return true; }
      else { return false; }
   }
}
```