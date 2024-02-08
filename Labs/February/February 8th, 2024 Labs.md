# February 8th, 2024 Labs
## Lab 1
Complete the definition of the RectangleWithFixedWidth class outlined below.
```java
/**
   The public interface of this class is that it has three fields
   named width, height, and area, but the implementation should be
   that this class contains only two fields, width and area. Also,
   the width of a rectangle cannot be changed once it has been set.

   Write implementations for the constructor, the three get methods,
   and the two set methods in such a way that height is derived from
   the width and area fields.
*/
class RectangleWithFixedWidth
{
   private final double width;  // blank final
   private double area;

   /**
      Construct a RectangleWithFixedWidth object
      with the given values for its width and height.
      Once the width is set, it cannot be changed (but
      the height can be).

      @param width   the immutable value for the width of the new RectangleWithFixedWidth object
      @param height  the value for the height of the new RectangleWithFixedWidth object
      @throws IllegalArgumentException if width is not strictly positive
      @throws IllegalArgumentException if height is not strictly positive
   */
   public RectangleWithFixedWidth(double width, double height)
   {
      if (width <= 0)
         throw new IllegalArgumentException("width must be strictly positive");
      if (height <= 0)
      throw new IllegalArgumentException("height must be strictly positive");
     
      this.width = width;
      this.area = width * height;
   }


   /**
      @return the height of this RectangleWithFixedWidth object
   */
   public double getHeight()
   {
      return this.area / this.width;
   }


   /**
      @return the width of this RectangleWithFixedWidth object
   */
   public double getWidth()
   {
      return this.width;
   }


   /**
      @return the area of this RectangleWithFixedWidth object
   */
   public double getArea()
   {
      return this.area;
   }


   /**
      @param height  the new value for the height of this RectangleWithFixedWidth object
   */
   public void setHeight(double height)
   {
      this.area = this.width * height;
   }


   /**
      @param area  the new value for the area of this RectangleWithFixedWidth object
   */
   public void setArea(double area)
   {
      this.area = area;
   }


   @Override
   public String toString()
   {
      return "RectangleWithFixedWidth[width = " + width + ", height = " + getHeight() + "]";
   }
}
```

## Lab 2
### Class_A
```java
public class Class_A implements I_1
{
   /*
   method1 in Class_A does this.
   method2 in Class_A does THIS!
   */
   @Override
   public void method1()
   {
      System.out.println("method1 in Class_A does this.");
   }
   
   @Override
   public void method2()
   {
      System.out.println("method2 in Class_A does THIS!");
   }
}
```

### Class_B
```java
public class Class_B implements I_2
{
   /*
   method3 in Class_B is easy.
   method4 in Class_B is hard to figure out.
   method5 in Class_B is starting to make sense.
   */
   @Override
   public void method3()
   {
      System.out.println("method3 in Class_B is easy.");
   }

   @Override
   public String method4()
   {
      System.out.print("method4 in Class_B is hard to figure out.");
      return"";
   }
   
   @Override
   public String method5()
   {
      System.out.print("method5 in Class_B is starting to make sense.");
      return "";
   }
}
```

### Class_C
```java
public class Class_C implements I_1, I_2
{
   /*
   method1 in Class_C would rather do something else.
   method2 in Class_C is bored.
   method3 in Class_C is getting repetitious.
   method4 in Class_C is getting to be too much.
   You're done.
   */
   @Override
   public void method1()
   {
      System.out.println("method1 in Class_C would rather do something else.");
   }
   
   @Override
   public void method2()
   {
      System.out.println("method2 in Class_C is bored.");
   }
   
   @Override
   public void method3()
   {
      System.out.println("method3 in Class_C is getting repetitious.");
   }
   
   @Override
   public String method4()
   {
      System.out.print("method4 in Class_C is getting to be too much.");
      return"";
   }
   
   @Override
   public String method5()
   {
      System.out.print("You're done.");
      return "";
   }
}
```

### Interface_1
```java
public interface I_1
{
   public void method1();

   public void method2();
}
```

### Interface_2
```java
public interface I_2
{
   public void method3();

   public String method4();

   public String method5();
}
```
