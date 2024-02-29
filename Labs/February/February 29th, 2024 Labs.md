# February 29th, 2024 Labs
## Lab 1
Write a program that opens the file called input. Each line of this file contains the name of a team followed by a comma separated list of integer scores. The scores are all positive integers that are less than 1,000.

Your program should print out one line of information for each team listed in the input file. The line should start with the team name, followed by the team's minimum score, the team's maximum score, and the team's total score (the sum of all the scores on that team's line from input). The min, max, and total scores should be separated by one space.

Create a Scanner object and use it to read lines (one line per team) from the input file. After you read one line from the input file, you need to process the information in that String. To process one line from the input file, you can either 

(a) use another Scanner object that scans the String from the file using the useDelimiter() method, or 

(b) use the String method split() to split up the data in the String into an array of String.

Use which ever technique seems easier to you.

### Main.java
```java
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;

public class Main 
{
    public static void main(String[] args) throws FileNotFoundException
    {
        File input = new File("input");
        Scanner in = new Scanner(input);
        while (in.hasNextLine())
        {
            String oneLine = in.nextLine().trim();
            String[] line = oneLine.split("[,\\s]+");

            int[] nums = new int[line.length - 1];
            for (int i = 1; i < line.length; i++) 
            {
                nums[i - 1] = Integer.parseInt(line[i]);
            }
            int max = nums[0], min = nums[0], sum = 0;
            for (int n : nums)
            {
                if (min > n) {min = n;}
                if (max < n) {max = n;}
                sum += n;
            }
            System.out.printf("%s %d %d %d\n", line[0], min, max, sum);

        }
    }
}
```

### input.txt
<pre>
Team1  12, 6, 23, 8, 10, 11
Team2  13, 100, 72, 5, 18, 11, 20
Team3  5, 9, 2, 0
Team4  1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15
Team5  100, 90, 80, 70, 60, 50, 40, 30, 20, 10
Team6  2
</pre>

## Lab 2
The file called input contains a list of students and the courses they are taking. Each line of the file contain a student's first name, last name, id number, and course numbers.

Write a program that reads a single integer from System.in. That integer represents a course number. Your program should output the name and id number of each student taking that course. A student's name should be printed last name first, first name last, with a comma after the last name.

You need two Scanner objects, one to read from System.in and one to read from the file. First read in the course number (as an integer) from System.in. Then use the other Scanner to loop through the lines of the file. For each line of the file, get the fist name, last name, id number. The rest of the line is then the course numbers. Loop through the course numbers using either another Scanner or the split() method. If you find a match between a student's course and the search number, print a line of output for that student.

Notice that the first line of the file input contains the names of the columns in the file. That line is not useful to your program (its useful to someone looking at the file). Each time you want to search the file, you need to first read that line and throw it away (that is, you need to skip over the first line of the file).

### Main.java
```java
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;

public class Main 
{
    public static void main(String[] args) throws FileNotFoundException
    {
        Scanner systemIn = new Scanner(System.in);
        Scanner fileIn = new Scanner(new File("input"));

        String num = systemIn.next();
        String garbage = fileIn.nextLine();
        while (fileIn.hasNextLine())
        {
            String oneLine = fileIn.nextLine().trim();
            String[] line = oneLine.split("[,\\s]+");
            
            for (int i = 3; i < line.length; i++)
            {
                if (line[i].equals(num))
                {
                    System.out.printf("%s, %s %s\n", line[1], line[0], line[2]);
                }
            }
        }
    }
}
```
### input.txt
<pre>
First Last    ID      Courses...
Bob   Doe     53672   124  126  309
Jane  Adams   98134   100  123
Sue   Jones   90813   126  275  302 309
Adam  Henry   63901   223  275  302
Betty Smith   81255   126  223  275
Beth  Jacob   10274   126  302  309
Joe   Fox     66295   100  123
</pre>


