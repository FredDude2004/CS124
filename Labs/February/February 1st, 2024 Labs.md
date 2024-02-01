# February 1st, 2024 Lab
## Lab 1
Java has the ArrayList class and you can create an ArrayList<Integer> that contains only integer values. But what if you want a list of only positive integers? How can you restrict the kind of integers that go into a list?

Below is a class defined for you called RestrictedList that shows one way to solve this problem. The RestrictedList class is a subclass of ArrayList<Integer> but RestrictedList itself does not put any restrictions on what can go in a list. The restrictions are in further subclasses of RestrictedList.

Below are classes ListOfPositive, ListOfStrictlyPositive, ListOfNegative, RangeOfInteger, and ListOfBoundedInteger that you need to complete. Each of these classes is a subclass of RestrictedList and each class defines a different kind of restriction on the integers that can be put in a list.

The ArrayList class has several methods for adding an element to a list. When an element is being added to a list is a good time to check if the element satisfies the restriction that a list wants to enforce. Each of the classes below overrides the add methods from ArrayList and in each of these classes you need to write the code that checks that the given integer satisfies the list's restriction. If an integer being added to a list does not satisfy the list's restriction, your code should throw an IllegalArgumentException with an appropriate error message.

Two of the classes, RangeOfInteger and ListOfBoundedInteger, need parameters that determines the list's restrictions. For these two classes you need to complete a constructor for the class that sets the parameters of the list's restriction.

When you throw an IllegalArgumentException the exception should contain useful information. You need to program the error message in each IllegalArgumentException. To see what kind of message you need to create, first get your code to compile with just a simple error message (even an empty string will do). Then submit your code for grading. The output from the grader will show you exactly what the error messages should look like. Then go back and edit your exception's error messages to make them match the desired results.
<pre>
  ArrayList<Integer>
                          |
                          |
                          |
                     RestrictedList
                    /     |        \
                   /      |         \
                  /       |          \
    ListOfPositive   ListOfNegative   RangeOfInteger
           |
           |
           |
 ListOfStrictlyPositive
</pre>
The class ListOfStrictlyPositive is a subclass of ListOfPositive. It would seem that every "list of strictly positive integers" is also a "list of positive integers". But unfortunately, that is wrong. The above class design is problematic; it should NOT have ListOfStrictlyPositive as a subclass of ListOfPositive. Test case 4 in Tester.java shows that you cannot substitute a ListOfStrictlyPositive object in place of a ListOfPositive object. This is a really subtle aspect of object-oriented design.

You do not need to write any code that tests your classes. Your classes will be tested by the Tester.java program. The Tester.java program expects a single input integer between 1 and 4. The Tester.java program then runs one of its four built in test cases.
### RestrictedList
```java
/*
                  ArrayList<Integer>
                          |
                          |
                          |
                     RestrictedList
                    /     |        \
                   /      |         \
                  /       |          \
    ListOfPositive   ListOfNegative   RangeOfInteger
           |
           |
           |
 ListOfStrictlyPositive


NOTE: It is not correct to say that a ListOfStrictlyPositive is a ListOfPositive.
      This inheritance structure is not correct and it will lead to problems.
*/

import java.util.ArrayList;
import java.util.Collection;

/**
   Define an abstract base class for integer lists that
   restrict the values of the integers allowed into the list.
*/
@SuppressWarnings("serial")
public abstract class RestrictedList extends ArrayList<Integer>
{
   @Override
   public void add(int index, Integer i)
   {
      super.add(index, i);
   }

   @Override
   public boolean add(Integer i)
   {
      return super.add(i);
   }

   @Override
   public boolean addAll(Collection<? extends Integer> collection)
   {
      for (Integer i : collection)
      {
         add(i);
      }
      return true;
   }
}
```

### ListOfPositive
```java
import java.util.ArrayList;

/**
   Allow only integers that are greater
   than or equal to zero into the list.
*/
@SuppressWarnings("serial")
public class ListOfPositive extends RestrictedList
{
   /**
      @param index  where in the list to add the integer
      @param i  positive integer to add to this list
      @throws IllegalArgumentException when i is not positive
   */
   @Override public void add(int index, Integer i)
   {
      if (i < 0)
         throw new IllegalArgumentException("i is not posotive");
         
      super.add(index, i);
   }


   /**
      @param i  positive integer to add to this list
      @throws IllegalArgumentException when i is not positive
   */
   @Override public boolean add(Integer i)
   {
      if (i < 0)
         throw new IllegalArgumentException("i is not posotive");

      super.add(i);
      return true;
   }
}
```

### ListOfStrictlyPositive
```java
import java.util.ArrayList;

/**
   Allow only integers that are strictly
   greater than zero into the list.
*/
@SuppressWarnings("serial")
public class ListOfStrictlyPositive extends ListOfPositive  // This is NOT correct.
{
   /**
      @param index  where in the list to add the integer
      @param i  strictly positive integer to add to this list
      @throws IllegalArgumentException when i is not positive
   */
   @Override public void add(int index, Integer i)
   {
      if (i <= 0)
         throw new IllegalArgumentException("integer " + i + " must be strictly positive");// integer 0 must be strictly positive
         
      super.add(index, i);
   }


   /**
      @param i  strictly positive integer to add to this list
      @throws IllegalArgumentException when i is not positive
   */
   @Override public boolean add(Integer i)
   {
      if (i <= 0)
         throw new IllegalArgumentException("integer " + i + " must be strictly positive");

      super.add(i);
      return true;
   }
}
```

### ListOfNegative
```java
import java.util.ArrayList;

/**
   Allow only integers that are less
   than zero into the list.
*/
@SuppressWarnings("serial")
public class ListOfNegative extends RestrictedList
{
   /**
      @param index  where in the list to add the integer
      @param i  negative integer to add to this list
      @throws IllegalArgumentException when i is not negative
   */
   @Override public void add(int index, Integer i)
   {
      if (i >= 0)
         throw new IllegalArgumentException("integer " + i + " must be negative");
         
      super.add(index, i);
   }


   /**
      @param i  negative integer to add to this list
      @throws IllegalArgumentException when i is not negative
   */
   @Override public boolean add(Integer i)
   {
      if (i >= 0)
         throw new IllegalArgumentException("integer " + i + " must be negative");

      super.add(i);
      return true;
   }
}
```

### RangeOfInteger
```java
import java.util.ArrayList;

/**
   Allow only integers that are within
   the specified bounds into the list.
*/
@SuppressWarnings("serial")
public class RangeOfInteger extends RestrictedList
{
   private int lowerBound;
   private int upperBound;

   /**
      This constructor sets the lower and upper bounds on this list.

      @param lowerBound  the lower bound of the integer values allowed into this list
      @param upperBound  the upper bound of the integer values allowed into this list
   */
   public RangeOfInteger(int lowerBound, int upperBound)
   {
      this.lowerBound = lowerBound;
      this.upperBound = upperBound;
   }


   /**
      @param index  where in the list to add the integer
      @param i  bounded integer to add to this list
      @throws IllegalArgumentException when i is not between the bounds
   */
   @Override public void add(int index, Integer i)
   {
      if (!(lowerBound <= i && i <= upperBound))
         throw new IllegalArgumentException("integer " + i + " must be between the bounds " + lowerBound + " and " + upperBound);
         //integer 21 must be between the bounds 10 and 20
      super.add(index, i);
   }


   /**
      @param i  bounded integer to add to this list
      @throws IllegalArgumentException when i is not between the bounds
   */
   @Override public boolean add(Integer i)
   {
      if (!(lowerBound <= i && i <= upperBound))
         throw new IllegalArgumentException("integer " + i + " must be between the bounds " + lowerBound + " and " + upperBound);
         
      super.add(i);
      return true;
   }
}
```

### ListOfBoundedInteger
```java
import java.util.ArrayList;

/**
   Allow only integers that are less than
   the specified bound into the list.
*/
@SuppressWarnings("serial")
public class ListOfBoundedInteger extends RestrictedList
{
   private int upperBound;

   /**
      This constructor sets the upper bound on this list.

      @param upperBound  the upper bound of the integer values allowed into this list
   */
   public ListOfBoundedInteger(int upperBound)
   {
      this.upperBound = upperBound;
   }
   
   


   /**
      @param index  where in the list to add the integer
      @param i  bounded integer to add to this list
      @throws IllegalArgumentException when i is not below the bound
   */
   @Override public void add(int index, Integer i)
   {
      if (!(i <= upperBound))
         throw new IllegalArgumentException("integer " + i + " must be below the bound " + upperBound);
         
      super.add(index, i);
   }


   /**
      @param i  bounded integer to add to this list
      @throws IllegalArgumentException when i is not below the bound
   */
   @Override public boolean add(Integer i)
   {
      if (!(i <= upperBound))
         throw new IllegalArgumentException("integer " + i + " must be below the bound " + upperBound);
         
      super.add(i);
      return true;
   }
}
```