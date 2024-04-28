# CS 12400-001 Final Exam Answers

### Problem 1
a)
[4, 7, 11, 4, 9, 5, 11, 7, 3, 5]
[3, 7, 11, 4, 9, 5, 11, 7, 4, 5]
[3, 4, 11, 7, 9, 5, 11, 7, 4, 5]
[3, 4, 4, 7, 9, 5, 11, 7, 11, 5]
[3, 4, 4, 5, 9, 7, 11, 7, 11, 5]
[3, 4, 4, 5, 5, 7, 11, 7, 11, 9]
[3, 4, 4, 5, 5, 7, 7, 11, 11, 9]
[3, 4, 4, 5, 5, 7, 7, 9, 11, 11]

b)
[–7, 6, 8, 7, 5, 9, 0, 11, 10, 5, 8]
[–7, 6, 8, 7, 5, 9, 0, 11, 10, 5, 8]
[–7, 0, 8, 7, 5, 9, 6, 11, 10, 5, 8]
[–7, 0, 5, 7, 8, 9, 6, 11, 10, 5, 8]
[–7, 0, 5, 5, 8, 9, 6, 11, 10, 7, 8]
[–7, 0, 5, 5, 6, 9, 8, 11, 10, 7, 8]
[–7, 0, 5, 5, 6, 7, 8, 11, 10, 9, 8]
[–7, 0, 5, 5, 6, 7, 8, 8, 10, 9, 11]
[–7, 0, 5, 5, 6, 7, 8, 8, 9, 10, 11]


### Problem 2
a)
[4, 7, 11, 4, 9, 5, 11, 7, 3, 5]
[4, 4, 7, 11, 9, 5, 11, 7, 3, 5]
[4, 4, 7, 9, 11, 5, 11, 7, 3, 5]
[4, 4, 5, 7, 9, 11, 11, 7, 3, 5]
[4, 4, 5, 7, 7, 9, 11, 11, 3, 5]
[3, 4, 4, 5, 7, 7, 9, 11, 11, 5]
[3, 4, 4, 5, 5, 7, 7, 9, 11, 11]

b)
[–7, 6, 8, 7, 5, 9, 0, 11, 10, 5, 8]
[–7, 6, 7, 8, 5, 9, 0, 11, 10, 5, 8]
[–7, 5, 6, 7, 8, 9, 0, 11, 10, 5, 8]
[–7, 0, 5, 6, 7, 8, 9, 11, 10, 5, 8]
[–7, 0, 5, 6, 7, 8, 9, 10, 11, 5, 8]
[–7, 0, 5, 5, 6, 7, 8, 9, 10, 11, 8]
[–7, 0, 5, 5, 6, 7, 8, 8, 9, 10, 11]

### Problem 3
a) 20 seconds

b) 80 seconds

### Problem 4
Because sorting the Array first to find the largest element might take a really long time, especially if its a really large array. So it would just be faster to loop through the array and have a variable to keep track of the largest integer. 

### Problem 5
Insertion sort would return faster because it just compares each element to the previous element, and if it needs sorted then it will insert it into the correct position. 

### Problem 6
You should use the sort method that takes the comparator object, because You are trying to sort the same set of objects in five different ways, whats going to change is how they are being compared. So you are going to need a comparator object that tells you how to compare the objects

### Problem 7
Because in all of these boolean comparisons there are really three possibillietes, lets take == for example. When you are compariing two numbers the first number can either be less than, equal too, or greater than the second number. You can't represent these three cases with only true or false. So instead a comparator returns an int to represent either of the three cases. 

### Problem 8
```java
class Box implements comparable<Box>
{
    public double width, length, height;

    // implement the compareTo() method
    public int compareTo(Box that) 
    {
        int thisMax = this.width, thisOther = this.length + this.height;
        if (this.length > thisMax) { 
            thisMax = this.length; 
            thisOther = this.width + this.height;
        }
        if (this.height > thisMax) {
            thisMax = this.height;
            thisOther = this.length + this.width;
        }

        int thatMax = that.width, thatOther = that.length + that.height;
        if (that.length > thatMax) { 
            thatMax = that.length; 
            thatOther = that.width + that.height;
        }
        if (that.height > thatMax) {
            thatMax = that.height;
            thatOther = that.length + that.width;
        }

        int thisLengthGirth = thisMax + 2(thisOther);
        int thatLengthGirth = thatMax + 2(thatOther);

        return thisLengthGirth - thatLengthGirth;
    }
}

class CompareBoxes implements comparator<Box>
{
    // implement the compare() method
    THIS IS BIG GAY
}
```

### Problem 9
ALSO BIG GAY
