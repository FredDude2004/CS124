# February 22nd, 2024 Lab
## Lab 1
Write a program that opens the file called
input and copies all of the int values from
that file into a file called output1 and copies
all of the words from input into a file called
output2. Each int value should be written on its
own line in the output1 file and each word should
be written on its own line in the output2 file.

Create a Scanner object for the input file.
Create one PrintWriter object for the output1
file and another PrintWriter object for the
output2 file.

After all of the data from input has been copied
to output1 and output2, close all three files and
then reopen output1 and output2 using a Scanner object
for each file. Print to the console all of the integers
from output1 and then print to the console all the words
from output2.

```java
import java.util.Scanner;
import java.io.File;
import java.io.PrintWriter;
import java.io.FileNotFoundException;

public class Main
{
   public static void main(String[] args) throws FileNotFoundException
   {
       File Fileinput = new File("input");
       Scanner in = new Scanner(Fileinput);

       PrintWriter output1 = new PrintWriter("output1");
       PrintWriter output2 = new PrintWriter("output2");

       while (in.hasNext())
       {
           if (in.hasNextInt())
           {
               int n = in.nextInt();
               output1.println(n);
           }
           else if (in.hasNext())
           {
               String s = in.next();
               output2.println(s);
           }
       }
       output1.close();
       output2.close();
       
       File printOut1 = new File("output1");  
       Scanner in1 = new Scanner(printOut1);
       while (in1.hasNextInt())
       {
           int n = in1.nextInt();
           System.out.println(n);
       }

       File printOut2 = new File("output2");
       Scanner in2 = new Scanner(printOut2);
       while (in2.hasNext())
       {
           String s = in2.next();
           System.out.println(s);
       }
   }
}
```
