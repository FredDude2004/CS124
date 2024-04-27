# CS 12400-001 Final Exam Review

The exam is on Thursday, May 2.

The exam is over the whole semester. It includes all the
chapters from Exam 1 and Exam 2 and also Chapter 14, which
was covered after Exam 2. Be sure to study all the review
problems for exams 1 and 2 and also study your graded
copies of those two exams.

Chapter 14 Sorting and Searching  https://learn.zybooks.com/zybook/PNWCS12400KraftSpring2024/chapter/14/section/1

In Chapter 14 of the zyBook, the most important sections are
14.1, 14.2, 14.5, 14.12, 14.13.

In addition to those sections of Chapter 14, review Section 15 of Chapter 9
on the Comparable interface, https://learn.zybooks.com/zybook/PNWCS12400KraftSpring2024/chapter/9/section/15#bjlo-2-ch9-sec6_3


Here are a few review problems for Chapter 14.


### Problem 1
 Trace the steps that selection sort takes to sort these lists.
That is, for each list, show how each iteration of selection sort will
change the list.

a) [4, 7, 11, 4, 9, 5, 11, 7, 3, 5]

b) [–7, 6, 8, 7, 5, 9, 0, 11, 10, 5, 8]


### Problem 2
 Trace the steps that insertion sort takes to sort these lists.
That is, for each list, show how each iteration of insertion sort will
change the list.

a) [4, 7, 11, 4, 9, 5, 11, 7, 3, 5]

b) [–7, 6, 8, 7, 5, 9, 0, 11, 10, 5, 8]



### Problem 3
a) 
Suppose algorithm A takes five seconds to handle a data set
of 1,000 items. If the algorithm A is a linear algorithm, approximately
how long will it take to handle a data set of 4,000 items?

b) 
Suppose algorithm B takes five seconds to handle a data set
of 1,000 items. If the algorithm B is a quadratic algorithm, approximately
how long will it take to handle a data set of 4,000 items?



### Problem 4
 If you want to find the largest integer in an array of ints,
 ```java
   int[] a = { ... };
```
what is wrong with sorting the array and them getting the last element
from the sorted array?
```java
   sort(a); // sort from smallest to largest
   int max = a[a.length-1];
```


### Problem 5
 Suppose you give an already sorted array as input to both
selection sort and insertion sort. Which method will return faster?
Briefly explain why.



### Problem 6
 Suppose you need to sort the same list of objects five
different ways. Should you use the sort method that takes a list
of Comparable objects, or should you use the sort method that
takes a Comparator object? Briefly explain why.


### Problem 7
 When you compare numbers, you use the <, >, <=, >=, ==, and != operators.
These are all boolean operators that return true or false. When you implement the
Comparable or the Comparator interface, you don't write a boolean method, you write
a method that returns -1, 0, or 1. Why? Why were Comparable and Comparator designed
to return int instead of boolean?



### Problem 8
 A Box has three dimensions, width, length, and height.
```java
class Box implements Comparable<Box>
{
   public double width, length, height;

   // implement the compareTo() method
}
```

Shipping companies define a measure of boxes called "length plus girth".
It is defined to be the sum of the largest dimension plus two times the
sum of the two smaller dimensions.

   length_plus_girth = largest_dim + 2*(smallest_dim + middle_dim)

a) Write the compareTo method for the Box class so that is compares
boxes by their "length plus girth".


b) Complete the implementation of the CompareBoxes class so that the
comparator compares two boxes by their "length plus girth".
```java
class CompareBoxes implements Comparator<Box>
{
   // implement the compare() method
}
```


### Problem 9
 An Interval is two integers where the first integer
must be less than the second one.
```java
class Interval implements Comparable<Interval>
{
   private int a, b;
   public Interval(int a, int b)
   {
      if (b < a) throw new IllegalArgumentException();
      this.a = a;
      this.b = b;
   }

   @Override public int compareTo(Interval that)
   {
      // implement the compareTo() method
   }
}
```
a) 
Complete the definition of the compareTo() method so
that two Interval objects are compared by their length.


b) 
Complete the definition of the compare() method so that the
Comparator compares two Interval objects by where they begin
on the number line. An Interval is less than any other
Interval that begins after it. If two Interval objects begin
at the same number, use their other number as the tie breaker
(the shorter Interval is less than the longer Interval).
```java
class CompareIntervals implements Comparator<Interval>
{
   @Override public int compare(Interval i1, Interval i2)
   {
      // implement the compare() method
   }
}
```