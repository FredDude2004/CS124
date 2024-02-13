# Exam 1 Reveiw 
## Question 1
```java
import java.util.ArrayList;
import java.util.Arrays;

public class Main
{
	public static void main(String[] args) {
        ArrayList<Integer> myList = new ArrayList<>(Arrays.asList(2, 3, 5));
        myList.add(0, 1);
        myList.add(3, 4);
        myList.add(6);
        
        for (int value : myList)
        {
            System.out.print(value + " ");
        }
	}
}
```

## Question 2 
### a) 
<pre>
[1, 10, 1, 11, 1, 12, 2, 10, 2, 11, 2, 12, 3, 10, 3, 11, 3, 12]
</pre>

For each item in list1 it will loop all the way through list2, adding the item from list1 followed by the 
item in list2 that comes next. It will repeat that process until you reach the end of the second loop, then 
it will change the item from list1 

so you get somthing like 
l1a, l2a, l1a, l2b, l1a, l2c, l1b, l2a, . . . 

### b)
<pre>
[12, 3, 11, 3, 10, 3, 12, 2, 11, 2, 10, 2, 12, 1, 11, 1, 10, 1]
</pre>

It will reverse the order because it is continually adding the items to the start of list3

### c) 
```java
import java.util.ArrayList;
import java.util.Arrays;

public class Main
{
	public static void main(String[] args) {
        ArrayList<Integer> list1 = new ArrayList<>(Arrays.asList(1, 2, 3));
        ArrayList<Integer> list2 = new ArrayList<>(Arrays.asList(10, 11, 12));
        ArrayList<Integer> list3 = new ArrayList<>();
        for (int i : list1)
        {
            list3.add(i);
            for (int j : list2)
            {
               list3.add(j);
            }
        }
        System.out.println( list3 );
	}
}
```
Put the first add statment above the nest, and it will solve the problem, by not also printing out 
the first item for each item in list2

## Question 3 
2
<pre>
a --> null

b --> A instance
     | a | 100 |

c -- A instance
     | a | 150 |
</pre>
The a is a null pointer value, so its "garbage" and we don't count it.

## Question 4 
1
<pre>
a1 --> null
        ^
a2 -----| 

a3 -- A instance
     | a | 250 |
</pre>
a1 and a2 both point at null, so they are "garbage" and we don't count them. 

## Question 5 
<pre>
pairs --> | 1 | --> | null | null | null |
          | 2 | --> | null |      | null |
                               |
                               |
                               ---> Pair instance
                                    | p1 | 200 |
                                    | p2 | 100 | 
</pre>

## Question 6 
<pre>
x = a=2 and b=1
y = 1
</pre>

First you create a "Thing" object that holds two public integer values 'a' and 'b', construct it to hold the values 1 and 1, and you create a reference variable 'x' that points to that "Thing" object. then you create a integer variable 'y' and set it equal to 1. Next you call the 'f' method which increments the 'a' value in the thing object 'x', so that it equals 2. the method also increments the y variable but it is never returned so it has no effect. Then you print out "x = " and the values in the Thing object 'x', new line "y = " and the value of the y variable which is 1. Giving you you're final output. 

## Question 7 
### a) 
```java
public class Main 
{
   public static void main(String[] args) 
   {
      Point center = new Point(2, 3);
      Circle c1 = new Circle(center, 5);
   }
}
```
### b) 
```java
public Point getCenter()
{
    return new Point(this.x, this.y);
}
```

## Question 8
<pre>
8
catdog
cat35
dog5cat
</pre>

Because each method takes parameters with different data types. 
So whatever data types you put call the method with determines what will happen. 

## Question 9
<pre>
        A
       / \
      B   D
      |
      C
     / \
    E   F
    |   |
    G   H
</pre>

## Question 10
<pre>
         A
    I   / \
   / \ /   B
  C J-F    |
  |/       E
  D
</pre>
## Question 11
