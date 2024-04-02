# CS 12400-001 Exam 2 Answers

### Problem 1 
<pre>
Hello there everyone.
What
do
 you think?
Here
</pre>

### Problem 2
a)  NoSuchElementException
    Line 8

b)  NumberFormatException
    Line 9

c)  InputMismatchException
    Line 7

d)  InputMismatchException
    Line 7

e)  NoSuchElementException
    Line 7

### Problem 3
The Program on the right. Becuase Line 17 on the first Program calls methodB(). 
When it should print the stack trace like it does on the right
```java
// Program on the left
/*15*/    public static void methodC()
/*16*/    {                                                 
/*17*/       methoB();                                      
/*18*/    }   

// Program on the right
/*15*/    public static void methodC()
/*16*/    {
/*17*/       new Exception().printStackTrace(System.out);
/*18*/    }
```

### Problem 4
<pre>
main
methodC
methodF
methodB
methodE
</pre>

### Problem 5 
<pre>
methodE
caught
methodD
methodB
main
</pre>

### Problem 6
a)  4

b)  3

c)  3

d)  7

e)  1

### Problem 7 
a)  Line 8, index 2 out of bounds for length 2.

b)  Line 7, cat can't parse to int.

c)  Line 5, 1.2 can't parse into an int.

d)  Line 6, index 1 out of bounds for length 1.

### Problem 8
678

### Problem 9
### Problem 10
### Problem 11

### Problem 12
a)  It reverses the string 

b)  Reverse

### Problem 13
a)  I returns the amount of characteers that are in the string

b)  length

### Problem 14
It removes the spaces from the input String. 

### Problem 15
It checks if the input string ends with 's'

### Problem 16
```java
public static String change(String str) // recursive 
{
    if (str.equals("")) 
    {
        return "";
    }
    else if (str.charAt(0) == ' ') 
    {
        return "-" + hyphenate(str.substring(1));
    }
    else 
    {
        return str.charAt(0) + hyphenate(str.substring(1));
    }
}
```

### Problem 17
It removes all the characters that come after the nth character. 