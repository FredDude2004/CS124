# February 20th, 2024 Lab
## Lab 1

Write a program that opens the files data1, data2, and data3. The file data1 contains a sequence of double values. The file data2 contains a sequence of int values. The file data3 contains a sequence of String values (a sequence of words).

Create three Scanner objects, one for each of these three data files. Read all the double values from the first file and add the values together. Read all the  int values from the second file and add them together. Then read all the words from the third file and add (concatenate) them together.

Print out the sum of all the doubles from the first data file, the sum of all the ints from the second data file, and the String that results from concatenating all the words from the third data file.

### Main.java
```java
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;

public class Main
{
    public static void main(String[] args) throws FileNotFoundException
    {
        File data1 = new File("data1");
        File data2 = new File("data2");
        File data3 = new File("data3");
        Scanner in1 = new Scanner(data1);
        Scanner in2 = new Scanner(data2);
        Scanner in3 = new Scanner(data3);

        double sum1 = 0.0;
        int sum2 = 0;
        String sum3 = "";
        while ( in1.hasNextDouble() )
        {
            double n = in1.nextDouble();
            sum1 += n;
        }
        while ( in2.hasNextInt() )
        {
            int n = in2.nextInt();
            sum2 += n;
        }
        while ( in3.hasNext() )
        {
            String n = in3.next();
            sum3 += n;
        }
        System.out.println(sum1);
        System.out.println(sum2);
        System.out.println(sum3);
    }
}
```

### data1.txt
<pre>
23.5   44.6   32.6
56.9  34.2

66.7   89.7
50.0
12.4
        88.8
</pre>

### data2.txt
<pre>
76      52      35
     27     62
100     9
     11

1001
</pre>

### data3.txt
<pre>
Cat  Dogs
Apples
    Pears
Banana
The   End


Maybe
</pre>
