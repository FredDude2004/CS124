# April 18th, 2024 Labs
# Lab 1 
In this lab you will write the compareTo method for the Triple class so that a generic sorting algorithm can sort a List of Triple objects into their "natural" order.

A Triple is an object that holds three integers. Here is an example of a List of Triple objects.
<pre>
[<2, 3, 2>, <4, 4, 1>, <2, 4, 0>, <5, 1, 1>, <0, 6, 3>, <2, 2, 2>, <4, 1, 4>, <5, 0, 4>]
</pre>
Implement the compareTo method in the Triple class so that the "natural" order of triples compares their third component. Then their second component should be used as a tie breaker and the first component should be the second tie breaker.

So <a,b,c> is less than <x,y,z> if c<z, or if c==z and b<y, or if c==z and b==y and a<x.

Using this order, the triples in the above list will sort to
<pre>
[<2, 4, 0>, <5, 1, 1>, <4, 4, 1>, <2, 2, 2>, <2, 3, 2>, <0, 6, 3>, <5, 0, 4>, <4, 1, 4>]
</pre>

### Triple.java
```java
/**
   This version of the Triple class
   implements the Comparable<T> interface.

   A generic sorting algorithm can use
   Triple's compareTo() method to sort
   a list of Triple objects.
*/
public class Triple implements Comparable<Triple>
{
   public int x, y, z;

   public Triple(int x, int y, int z)
   {
      this.x = x;
      this.y = y;
      this.z = z;
   }


   @Override public String toString()
   {
      return "<" + x + ", " + y + ", " + z + ">";
   }


   /**
      Compare Triples in "reverse order" by first comparing
      the z-component, then the y-component, then the
      x-component.
   */
   @Override public int compareTo(Triple that)
   {
      if (this.z < that.z)
      {
         return -1;
      }
      else if (this.z == that.z && this.y < that.y)
      {
         return -1;
      }
      else if (this.z == that.z && this.y == that.y && this.x < that.x)
      {
         return -1;
      }
      else if (this.z == that.z && this.y == that.y && this.x == that.x)
      {
         return 0;
      }
      else
      {
         return 1;
      }
   }
}
```


# Lab 2
In this lab you will write a Comparator class for the Triple class so that a generic sorting algorithm can sort a List of Triple objects in the order determined by the Comparator.

A Triple is an object that holds three integers. Here is an example of a List of Triple objects.
<pre>
[<2, 3, 2>, <4, 4, 1>, <2, 4, 0>, <5, 1, 1>, <0, 6, 3>, <2, 2, 2>, <4, 1, 4>, <5, 0, 4>]
</pre>
Implement the compare method in TripleComparator so that it orders triples by first comparing the sum of their first tow components. Then their first component should be used as a tie breaker and their third component should be the second tie breaker.

So <a,b,c> is less than <x,y,z> if a+b<x+y, or if a+b==x+y and a<x, or if a+b==x+y and a==x and c<z.

Using this order, the triples in the above list will sort to
<pre>
[<2, 2, 2>, <2, 3, 2>, <4, 1, 4>, <5, 0, 4>, <0, 6, 3>, <2, 4, 0>, <5, 1, 1>, <4, 4, 1>]
</pre>

### TripleComparator.java
```java
import java.util.Comparator;

/**
   A Comparator<Triple> class for Triple class.
*/
class TripleComparator implements Comparator<Triple>
{
   /**
      Implement this compare() method so that it first
      compares the sum of the first two components from
      the Triple objects. Use the first componenet from
      the Triple objects as the tie breaker, and then use
      the third component as the second tie breaker.

      So <a,b,c> is less than <x,y,z> if a + b < x + y,
      or if a+b==x+y and a < x,
      or if a+b==x+y and a == x and c < z.

   */
   @Override public int compare(Triple first, Triple second)
   {
      if (first.x + first.y < second.x + second.y) 
      { return -1; }
      else if (first.x + first.y == second.x + second.y && first.x < second.x) 
      { return -1; }
      else if (first.x + first.y == second.x + second.y && first.x == second.x && first.z < second.z) 
      { return -1; }
      else 
      { return 1; }
   }
}
```
