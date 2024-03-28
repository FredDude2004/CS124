# March 28th, 2024 Labs
## Lab 1
Write a recursive method called replace that takes a String as input and returns a String with every space character from the input String replaced with a hyphen, '-'.

For example, the following calls should return the following strings:
<pre>
replace("hello there class")  ==>  "hello-there-class"
replace("   ")  ==>  "---"
replace("---")  ==>  "---"
replace("")  ==>  ""
replace(" a b c d e f g ")  ==>  "-a-b-c-d-e-f-g-"
</pre>

```java
import java.util.Scanner;
public class Main
{
    public static String replace(String str) // recursive method
    {
        if (str.equals(""))
        {
            return "";
        }
        else  // recursive case
        {  
            String hyphenated = replace(str.substring(1));
            String possibleSpace = str.substring(0,1);
            if (" ".indexOf(possibleSpace) < 0)
            {
                return possibleSpace + hyphenated;
            }
            else
            {
                return "-" + hyphenated;
            }
        }
    }


    public static void main(String[] args)
    {
        Scanner stdin = new Scanner(System.in);
        String str = stdin.nextLine();
        System.out.println( replace(str) );
    }
}
```

## Lab 2
Write a recursive method called createPattern that takes an integer n and returns a String with n characters. If n is an odd number, then the middle character of the returned String should be an asterisk, "*". If n is an even number, then the middle two characters of the returned String should be two asterisks, "**". To the left of the asterisk(s) you should put less-than characters, '<'. To the right of the asterisk(s) you should put greater-than characters, '>'.

For example, the following calls should return the following strings:
<pre>
createPattern(1)  ==>  "*"
createPattern(2)  ==>  "**"
createPattern(3)  ==>  "<*>"
createPattern(4)  ==>  "<**>"
createPattern(5)  ==>  "<<*>>"
createPattern(6)  ==>  "<<**>>"
createPattern(7)  ==>  "<<<*>>>"
createPattern(8)  ==>  "<<<**>>>"
createPattern(9)  ==>  "<<<<*>>>>"
</pre>
If the value of the parameter n is less than 1, then throw an IllegalArgumentException.

Hint: Your recursive method needs two base cases.

```java
public class Main
{
    public static String createPattern(int n) // recursive method
    {
        if (n == 1) // base case #1 n is odd
        {
            return "*";
        }
        else if (n == 2) // base case #2 n is even
        {
            return "**";
        }
        else
        {
            return "<" + createPattern(n - 2) + ">";
        }
    }

    public static void main(String[] args)
    {
        for (int i = 1; i <= 16; ++i)
        {
            System.out.println( createPattern(i) );
        }
    }
}
```

## Lab 3
Write a recursive method called replace that takes two parameters, a non-negative integer n and a String str. The method should return a String in which each of the first n characters from str is replaced with a hyphen, '-'.

For example, the following calls should return the following strings:
<pre>
replace(3, "elephants")  ==>  "---phants"
replace(0, "elephants")  ==>  "elephants"
replace(3, "cat")  ==>  "---"
replace(4, "cat")  ==>  "---"
replace(8, "elephants")  ==>  "--------s"
</pre>

Your recursive method call need to "shrink" both the string parameter and the integer parameter. The string parameter should lose its first character and the integer should decrease by 1.

Your recursive method will need two base cases, when the input string is empty, "", and when the input integer is 0. In both base cases, there is nothing that needs to be done to the input string, so the input string should be returned.

```java
import java.util.Scanner;
public class Main
{
    public static String replace(int n, String str) // recursive method
    {
        if (str.equals(""))
        {
            return str;
        }
        else if (n == 0)
        {
            return str;
        }
        else
        {
            return "-" + replace(n - 1, str.substring(1));
        }
    }

    public static void main(String[] args)
    {
        Scanner stdin = new Scanner(System.in);
        int n = stdin.nextInt();
        String str = stdin.next();
        System.out.println( replace(n, str) );
    }
}
```
