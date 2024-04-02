# April 2nd, 2024 Labs
## Lab 1
Write a recursive method called replace that takes three parameters, a non-negative integer n, a String str1. and a String str2. The method should return a String in which the first n characters from str1 are replaced with the first n characters from str2.

For example, the following calls should return the following strings:
<pre>
replace(3, "elephants", "dogs")  ==>  "dogphants"
replace(0, "elephants", "dogs")  ==>  "elephants"
replace(3, "cat", "dog")  ==>  "dog"
replace(3, "cats", "dog") ==>  "dogs"
replace(3, "cats", "")    ==>  "cats"
replace(3, "", "dogs")    ==>  ""
replace(5, "elephant", "dog")  ==>  "dogphant"
</pre>

Your recursive method call need to "shrink" both string parameters and the integer parameter. The string parameters should lose their first character and the integer should decrease by 1.

Your recursive method will need three base cases, when the input integer is 0. when the first input string is empty, "", and when the second input string is empty, "".  In each base case, there is nothing that needs to be done to the first input string, so the first input string should be returned.

```java
public class Main
{
    public static String replace(int n, String str1, String str2) // recursive method
    {
        if (n == 0) // base case 1
        {
            return str1;
        }
        else if (str1.equals("")) // base case 2
        {
            return str1;
        }
        else if (str2.equals("")) // base case 3
        {
            return str1;
        }
        else // recursion
        {
            String result = replace(n - 1, str1.substring(1), str2.substring(1));
            return str2.charAt(0) + result;                                                                        
        }
    }

    public static void main(String[] args)
    {
        boolean b1 = false, b2 = false, b3 = false, b4 = false,
                b5 = false, b6 = false, b7 = false, b8 = false;
        if ( (b1 = replace(3, "elephants", "dogs").equals("dogphants"))
          && (b2 = replace(0, "elephants", "dogs").equals("elephants"))
          && (b3 = replace(3, "cat", "dog").equals("dog"))
          && (b4 = replace(3, "cats", "dog").equals("dogs"))
          && (b5 = replace(3, "cats", "").equals("cats"))
          && (b6 = replace(3, "", "dogs").equals(""))
          && (b7 = replace(5, "elephant", "dog").equals("dogphant")) )
       {
          System.out.println("All tests passed.");
       }
       else
       {
          System.out.println("At least one test failed.");
       }
    }
}
```

## Lab 2
Write a recursive method called replace that takes two string inputs and returns a string with the same length as the longer of the two input strings. At any position in the return string where the two input strings have the same character, the return string should also have that character. At any position in the return string where the two input strings have different characters, the return string should have the '-' character. The positions in the return string that are past the length of the shorter input string should have the '*' character.

For example, the following calls should return the following strings:
<pre>
replace("cats", "dogs") ==> "---s"
replace("cats", "bat")  ==> "-at*"
replace("bats", "battery") ==> "bat-***"
replace("", "dogs") ==> "****"
replace("cats", "") ==> "****"
replace("catalog", "cats") ==> "cat-***"
</pre>

Your recursive method will have just one real base case, where both input strings are empty. But you also need two other "kind of" base cases, where either the first or the second input string is empty. In these "kind of" base cases, you still need a recursive call, but you can only shrink one of the two parameters (the non-empty one). Then you need a "recursive case" in which both parameters are non-empty and the recursion shrinks both parameters.

```java
public class Main
{
    public static String replace(String str1, String str2) // recursive method
    {
        if (str1.equals(""))
        {
            if (str2.length() > 0)
            {
                String result = replace(str1, str2.substring(1));
                return result + "*";
            }
            else 
            {
                return "";
            }
        }
        else if (str2.equals(""))
        {
            if (str1.length() > 0)
            {
                String result = replace(str1.substring(1), str2);
                return result + "*";
            }
            else 
            {
                return "";
            }
        }
        else 
        {
            String result = replace(str1.substring(1), str2.substring(1));
            if (str1.charAt(0) == str2.charAt(0))
            {
                return str1.charAt(0) + result;
            }
            else 
            {
                return "-" + result;
            }
        }
    }

    public static void main(String[] args)
    {
        boolean b1 = false, b2 = false, b3 = false,
                b4 = false, b5 = false, b6 = false;
        if ( (b1 = replace("cats", "dogs").equals("---s"))
          && (b2 = replace("cats", "bat").equals("-at*"))
          && (b3 = replace("bats", "battery").equals("bat-***"))
          && (b4 = replace("", "dogs").equals("****"))
          && (b5 = replace("cats", "").equals("****"))
          && (b6 = replace("catalog", "cats").equals("cat-***")) )
       {
          System.out.println("All tests passed.");
       }
       else
       {
          System.out.println("At least one test failed.");
       }
    }
}
```