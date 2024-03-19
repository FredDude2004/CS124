# March 19th, 2024 Labs
## Lab 1 
Write a Java program that expects 5 integer values on its command-line. Your program should print out the maximum, the minimum, the sum, and the average values of the five command-line arguments.

If there are fewer than five command-line arguments, then your program should print the following "usage message" and terminate.

Usage: java Arithmetic int1 int2 int3 int4 int5

If there are more than five command-line arguments, then your program should just ignore any arguments after the fifth one.

If one of the five command-line arguments does not parse properly to an integer value, then your program should catch the NumberFormatException and print the above usage message and terminate.

If the command-line is the following,
<pre>
java Arithmetic 1 2 3 4 5
</pre>
then your output should look like this.
<pre>
max = 5

min = 1

sum = 15

avg = 3.0
</pre>

```java
public class Arithmetic
{
    public static void main(String[] args)
    {
        int[] arr = new int[5];
        try
        {
            for (int i = 0; i < 5; i++)
            {
                arr[i] = Integer.parseInt(args[i]);
            }
        }
        catch (NumberFormatException ex) 
        {
            System.out.println("Usage: java Arithmetic int1 int2 int3 int4 int5");
            return;
        }
        catch (ArrayIndexOutOfBoundsException ex)
        {
            System.out.println("Usage: java Arithmetic int1 int2 int3 int4 int5");
            return;
        }

        int max = arr[0]; 
        int min = arr[0]; 
        int sum = arr[0]; 

        for (int i = 1; i < 5; i++)
        {
            if (arr[i] > max)
                max = arr[i];
            if (arr[i] < min)
                min = arr[i];
            sum += arr[i];
        }
        double avg = (double) sum / 5;

        System.out.printf("max = %d\nmin = %d\nsum = %d\navg = %.1f\n", max, min, sum, avg);
    }
}
```

## Lab 2 
Write a Java program that takes a single strictly positive integer value, n, on the command line. Your program should open the file
<pre>
   /usr/share/dict/words
</pre>
and find the n'th word in the words file. The Linux words file is a list of thousands of words, with one word on each line of the file. To find the n'th word you need to create a Scanner object that reads the words file and either call next() n times or call nextLine() n times. The last time you call next() or nextLine(), the returned String is the word you want. Print out the word you find.

```java
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;

public class WordFind
{
    public static void main(String[] args) throws FileNotFoundException
    {
        File file = new File("/usr/share/dict/words");
        int n = Integer.parseInt(args[0]);
        String word = "";
        
        try 
        {
            Scanner in = new Scanner(file);
            for (int i = 0; i < n; i++)
            {
                if (in.hasNext())
                {
                    word = in.next();
                }
                else 
                {
                    in.nextLine();
                }
            }
        }
        catch (FileNotFoundException e)
        {
            System.out.println("File Not Found");
        }
        System.out.println(word);
    }
}
```