# February 27th, 2024 Lab
## Lab 1
Write a program that opens three files called input1, input2, and input3. Each of these three files contain numbers separated by delimiters. Each file has different kinds of numbers and uses different delimiters.

The file input1 contains integer numbers that use commas, like 1,001. The delimiters used in that file are spaces, the period character, and the semi-colon character.

The file input2 contains decimal numbers, like 1000.001. The delimiters are spaces, commas, semi-colons, and vertical bar (the '|' character).

The file input3 contains decimal numbers that use commas in their integer part, like 1,234,567.89. The delimiters are spaces, semi-colons, the vertical bar character, and the '#' character.

Create a Scanner object for each input file. Call the useDelimiter() method on each Scanner object and give it the appropriate delimiters. Then write a while-loop for each input file and read all the numbers in the file as tokens (not as numbers, because the numbers with commas in them will not parse as valid numbers). Print each number in the console on its own lime. But a blank line between the outputs from the files.

### Main.java
```java
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;

public class Main {
    public static void main(String[] args) throws FileNotFoundException {
        File input1 = new File("input1");
        File input2 = new File("input2");
        File input3 = new File("input3");

        Scanner in1 = new Scanner(input1);
        Scanner in2 = new Scanner(input2);
        Scanner in3 = new Scanner(input3);

        in1.useDelimiter("[\\s.;]+");
        while (in1.hasNext()) {
            String n = in1.next();
            System.out.println(n);
        }
        System.out.println();

        in2.useDelimiter("[\\s,;|]+");
        while (in2.hasNext()) {
            String n = in2.next();
            System.out.println(n);
        }
        System.out.println();

        in3.useDelimiter("[\\s;|#]+");
        while (in3.hasNext()) {
            String n = in3.next();
            System.out.println(n);
        }
    }
}
```

### input1.txt
<pre>
1,001;123;2,000,000;
1,300  455  ;  10,000
1000000  ;3
-34,567 ;;; 0

-1,000;-2,000;-3,000

8 . -7 .  6
</pre>

### input2.txt
<pre>
1.35,  23.67,  88.0,
23,34,56,
6 7 8.0 9 10.5
12.3 | 45.6 | 0 | 0.0

89 |;| 90.2 ,,, 1000.00
8;9;10
</pre>

### input3.txt
<pre>
1,000.23;4,567.89;
-2 -3 -4,000.567

12345.67 # 7,650000.0001 #

-4,321.002|80.1#.123
1|2;3#4
</pre>


### Output
<pre>
1,001
123
2,000,000
1,300
455
10,000
1000000
3
-34,567
0
-1,000
-2,000
-3,000
8
-7
6
1.35
23.67
88.0
23
34
56
6
7
8.0
9
10.5
12.3
45.6
0
0.0
89
90.2
1000.00
8
9
10
1,000.23
4,567.89
-2
-3
-4,000.567
12345.67
7,650000.0001
-4,321.002
80.1
.123
1
2
3
4
</pre>
