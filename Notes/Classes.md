Class: Describes objects

Objects: Store data and have methods to manipulate and access that data

```java
class MyClassA
{

}

class MyClassB
{
    private int n; 
    private double y;

    public void setN(int newN)
    {
        this.n = newN;
    }
}

public class ClassNameHere
{
    public static void main(String[] args)
    {
        MyClassA r1 = null;
        MyClassA r2 = new MyClassA();
        MyClassA r3 = new MyClassA();
        MyClassA r4 = r2;

        MyClassB b1 = new MyClassA(); // This will create a compiler error because 
                                      // the types are different.
        int n = 3;
        double x = 4.5;

        MyClassB b1 = new MyClassB();
        MyClass b2 = new MyClassB();
        //b1.n = 5
        //b2.n = 6
        b1.setN(5);
        b2.setN(6);
    }
}```