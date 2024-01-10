# January 9th, 2024 Labs
## Problem 1
Fix the following code so that it compiles. The code should instantiate an ArrayList of Strings names and fill it with the Strings from the array friends. It should then print out names.
```java
import java.util.List;
import java.util.ArrayList;

public class Test
{
    public static void main(String[] args)
    {
        ArrayList<String> names = new ArrayList<String>();
        String[] friends = {"Sam", "Jessica", "Mark", "Alexis"};
        for (int i = 0; i < friends.length; i++)
        {
            names.add(friends[i]);
        }
        System.out.println(names);
    }
}
```

## Problem 2
Fix the following class so that it will compile and the method reverse will return an ArrayList containing Integers in the reversed order of the ArrayList parameter list. Hint: for this solution, only one line needs to be added to the for-loop inside of the reverse method.

```java
import java.util.List;
import java.util.ArrayList;

public class Test
{
    public static ArrayList<Integer> reverse(ArrayList<Integer> list)
    {
        ArrayList<Integer> reversed = new ArrayList<Integer>();
        for (int i = list.size() - 1; i > -1; i--)
        {
            reversed.add(list.get(i));
        }
        return reversed;
    }

    public static void main(String[] args)
    {
        //instantiate ArrayList and fill with Integers
        ArrayList<Integer> values = new ArrayList<Integer>();
        int[] nums = {1, 5, 7, 9, -2, 3, 2};
        for (int i = 0; i < nums.length; i ++)
        {
            values.add(nums[i]);
        }
        ArrayList<Integer> result = reverse(values);
        System.out.println("Expected Result:\t [2, 3, -2, 9, 7, 5, 1]");
        System.out.println("Your Result:\t\t " + result);
    }
}
```

## Problem 3
Fix the following method printEvenIndex so that it will print out the Integers at even indices of the passed-in ArrayList list.
```java
import java.util.List;
import java.util.ArrayList;

public class Test
{
    public static void printEvenIndex(ArrayList<Integer> list)
    {
        for (int i = 0; i < list.size(); i++)
        {
            if (i % 2 == 0)
            {
                System.out.print(list.get(i) + ", ");
            }
        }
    }

    public static void main(String[] args)
    {
        //instantiate ArrayList and fill with Integers
        ArrayList<Integer> values = new ArrayList<Integer>();
        int[] nums = {1, 5, 7, 9, -2, 3, 2};
        for (int i = 0; i < nums.length; i ++)
        {
            values.add(nums[i]);
        }
        System.out.println("Expected Result:\t 1, 7, -2, 2,");
        System.out.print("Your Result:\t\t ");
        printEvenIndex(values);
    }
}
```

## Problem 4
Fix the following method printEvenElements so that it will print out all of the even Integers that are in the passed-in ArrayList list.
```java
import java.util.List;
import java.util.ArrayList;

public class Test
{
    public static void printEvenElements(ArrayList<Integer> list)
    {
        for (int i = 0; i < list.size(); i++)
        {
            if (list.get(i) % 2 == 0)
            {
                System.out.print(list.get(i) + ", ");
            }
        }
    }

    public static void main(String[] args)
    {
        //instantiate ArrayList and fill with Integers
        ArrayList<Integer> values = new ArrayList<Integer>();
        int[] nums = {1, 44, 7, 9, -16, 3, 2};
        for (int i = 0; i < nums.length; i ++)
        {
            values.add(nums[i]);
        }
        System.out.println("Expected Result:\t 44, -16, 2,");
        System.out.print("Your Result:\t\t ");
        printEvenElements(values);
    }
}
```

## Problem 5
Rewrite the following code so that it fills the ArrayList values with the elements of the array nums using a for-each loop instead of a for loop.

```java
import java.util.List;
import java.util.ArrayList;

public class Test
{
    public static void main(String[] args)
    {
        ArrayList<Integer> values = new ArrayList<Integer>();
        int[] nums = {1, 44, 7, 9, -16, 3};
        for (Integer value : nums)
        {
            values.add(value);
        }
        System.out.println("Expected Result:\t [1, 44, 7, 9, -16, 3]");
        System.out.println("Your Result:\t\t " + values);
    }
}
```

## Problem 6
Finish the following method sumNegVal to return the sum of all of the negative numbers in the ArrayList list, the parameter.
```java
import java.util.List;
import java.util.ArrayList;

public class Test
{
    public static int sumNegValues(ArrayList<Integer> list)
    {
        int sumNeg = 0;
        for (Integer value : list)
        {
            if (value < 0)
            {
                sumNeg += value;
            }
        }
        return sumNeg;
    }

    public static void main(String[] args)
    {
        //instantiate ArrayList and fill with Integers
        ArrayList<Integer> values = new ArrayList<Integer>();
        int[] nums = {-2, 34, -11, 9, -6, 3};
        for (int i = 0; i < nums.length; i ++)
        {
            values.add(nums[i]);
        }
        System.out.println("Expected Result:\t -19");
        System.out.print("Your Result:\t\t ");
        System.out.println(sumNegValues(values));
    }
}
```
