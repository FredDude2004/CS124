# February 6th, 2024 Lab
## Lab 1
In each of the classes below, complete the implementation of any method that does not compile.

You do not need to make any changes to the Shape.java class.

You do not need to write any code that tests the classes. The classes will be tested by the Tester.java program. The Tester.java program expects a single input integer between 1 and 3. The Tester.java program then runs one of its three built in test cases.
### Shape
```java
/**
   This abstract class represents geometric shapes in the plane.

           Shape
          /     \
         /       \
    Circle       Rectangle
                    |
                    |
                  Square
*/
public abstract class Shape
{
   /**
      Every Shape should know how to compute its area.
   */
   public abstract double area();


   /**
      Every Shape should know how to compute its periemter.
   */
   public abstract double perimeter();


   /**
      Every Shape should know how to translate itself to a new location.

      @param p  Point for the new Shape's location
      @return a Shape with the same dimensions but a different location
   */
   public abstract Shape translateTo(Point p);


   /**
      Every Shape should know how to translate itself by a given amount.

      @param dx  amount by which to change the x-coordinate of the Shape's location
      @param dy  amount by which to change the y-coordinate of the Shape's location
      @return a Shape with the same dimensions but a different location
   */
   public abstract Shape translateBy(double dx, double dy);


   /**
      Force subclasses of Shape to implement toString().
   */
   @Override public abstract String toString();


   /**
      Force subclasses of Shape to implement equals().
   */
   @Override public abstract boolean equals(Object o);


   /**
      Provide a trivial implementation of hashCode().
   */
   @Override public int hashCode(){ return 1; }
}
```

### Circle
```java
/**
   This class represents immutable circles in the plane.

           Shape
          /     \
         /       \
    Circle       Rectangle
                    |
                    |
                  Square
*/
public class Circle extends Shape
{
   private double radius;
   private Point  center;
   final double PI = 3.1415926535897932;

   public Circle()
   {
      this.radius = 0;
      this.center = new Point(0,0);
   }

   public Circle(double r)
   {
      this.radius = r;
      this.center = new Point(0,0);
   }

   public Circle(double r, Point c)
   {
      this.radius = r;
      this.center = c;
   }

   public double getRadius()
   {
      return this.radius;
   }

   public Point getCenter()
   {
      return this.center;
   }


   /**
      Return a Circle object that has the same center as this Circle
      but with the given radius.

      @param r  the radius for the new Circle
      @return a Circle with the given radius and the same center as this Circle
   */
   public Circle setRadius(double r)
   {
      return new Circle(r, this.center);
   }


   /**
      Return a Circle object that has the same radius as this Circle
      but with the given center.

      @param center  the center Point for the new Circle
      @return a Circle with the given center Point and the same radius as this Circle
   */
   public Circle setCenter(Point center)
   {
      return new Circle(this.radius, center);
   }


   /**
      @return the value of this Circle's area
   */
   @Override
   public double area()
   {
      // implementation
      return PI * this.radius * this.radius;
   }


   /**
      @return the value of this Circle's perimeter
   */
   @Override
   public double perimeter()
   {
      // implementation
      return 2 * PI * this.radius;
   }


   /**
      Return a Circle object that has the same radius as this Circle
      but the new Circle should have its center at the given Point.

      @param p  Point for the new Circle's center
      @return a Circle with the same radius but a different center
   */
   @Override
   public Circle translateTo(Point p)
   {
      return new Circle(this.radius, p);
   }


   /**
      Return a Circle object that has the same radius as this Circle
      but the new Circle should have its center translated from where
      this Circle's center is.

      @param dx  how much to move the center of this Circle in the x-direction
      @param dy  how much to move the center of this Circle in the y-direction
      @return a Circle with the same radius but a different center
   */
   @Override
   public Circle translateBy(double dx, double dy)
   {
      Point newCenter = new Point(this.center.getX() + dx, this.center.getY() + dy);
      return new Circle(this.radius, newCenter);
   }


   @Override
   public String toString()
   {
      // Circle: r = 0.0, center = Point: [0.0, 0.0]
      return "Circle: r = " + this.radius + ", center = Point: [" + this.center.getX() + ", " + this.center.getY() + "]";
   }


   @Override
   public boolean equals(Object o)
   {
      if (o == this)
      {
         return true;
      }
      if (o == null)
      {
         return false;
      }
      if (!(o instanceof Circle))
      {
         return false;
      }

      Circle c = (Circle)o;
      // Determine if Circle c is equal to this Circle.
      return (this.radius == c.getRadius() && this.center == c.getCenter());
   }
}
```

### Rectangle
```java
/**
   This class represents immutable rectangles in the plane.

           Shape
          /     \
         /       \
    Circle       Rectangle
                    |
                    |
                  Square
*/
public class Rectangle extends Shape
{
   private final Point p;  // p is the upper left-hand corner of this rectangle
   private final double width;
   private final double height;

   /**
      @param p       this Rectangle's upper left-hand corner Point
      @param width   width of this Rectangle, must be strictly positive
      @param height  height of this Rectangle, must be strictly positive
      @throws IllegalArgumentException when width is not strictly positive
      @throws IllegalArgumentException when height is not strictly positive
   */
   public Rectangle(Point p, double width, double height)
   {
      if (width <= 0)
      {
         throw new IllegalArgumentException("Width must be strictly posotive");
      }
      if (height <= 0)
      {
         throw new IllegalArgumentException("Height must be strictly posotive");
      }

      this.p = p;
      this.width = width;
      this.height = height;
   }


   /**
      @return the this Rectangle's upper left-hand corner Point
   */
   public Point getPoint()
   {
      return this.p;
   }


   /**
      @return the value of this Rectangle's width
   */
   public double getWidth()
   {
      return this.width;
   }


   /**
      @return the value of this Rectangle's height
   */
   public double getHeight()
   {
      return this.height;
   }


   /**
      Return a Rectangle object that has the same upper left-hand
      corner and height as this Rectangle but with the given width.

      @param width  the width for the new Rectangle
      @return a Rectangle with the given width and the same upper left-hand corner and height as this Rectangle
   */
   public Rectangle setWidth(double width)
   {
      // implementation
      return new Rectangle(this.p, width, this.height);
   }


   /**
      Return a Rectangle object that has the same upper left-hand
      corner and width as this Rectangle but with the given height.

      @param height  the height for the new Rectangle
      @return a Rectangle with the given height and the same upper left-hand corner and width as this Rectangle
   */
   public Rectangle setHeight(double height)
   {
      // implementation
      return new Rectangle(this.p, this.width, height);
   }


   /**
      @return the value of this Rectangle's area
   */
   @Override
   public double area()
   {
      // implementation
      return this.width * this.height;
   }


   /**
      @return the value of this Rectangle's perimeter
   */
   @Override
   public double perimeter()
   {
      // implementation
      return 2 * width + height * 2;
   }


   /**
      Return a Rectangle object that has the same width and height
      as this Rectangle but the new Rectangle should have its upper
      left-hand corner at the given Point.

      @param p  Point for the new Rectangle's upper left-hand corner
      @return a Rectangle with the same dimensions but a different upper left-hand corner
   */
   @Override
   public Rectangle translateTo(Point p)
   {
      // implementation
      return new Rectangle(p, this.width, this.height);
   }


   /**
      Return a Rectangle object that has the same width and height
      as this Rectangle but the new Rectangle should have its upper
      left-hand corner translated from where this Rectangle's upper
      left-hand corner is.

      @param dx  amount by which to change the x-coordinate from this Rectangle
      @param dy  amount by which to change the y-coordinate from this Rectangle
      @return a Rectangle with the same dimensions but a different upper left-hand corner
   */
   @Override
   public Rectangle translateBy(double dx, double dy)
   {
      Point newCorner = new Point(this.p.getX() + dx, this.p.getY() + dy);
      return new Rectangle(newCorner, this.width, this.height);
   }


   @Override
   public String toString()
   {
      // Rectangle[corner=Point: [1.0, -2.0], width=3.0, height=4.0]
      String result = "Rectangle[corner=Point: [" + this.p.getX() + ", " + this.p.getY() + "]";
      result += ", width=" + this.width +", height=" + this.height + "]";
      return result;
   }


   @Override
   public boolean equals(Object o)
   {
      if (o == this)
      {
         return true;
      }
      if (o == null)
      {
         return false;
      }
      if (!(o instanceof Rectangle))
      {
         return false;
      }

      Rectangle r = (Rectangle)o;
      // Determine if Rectangle r is equal to this Rectangle.
      return (this.p == r.getPoint() && this.width == r.getWidth() && this.height == r.getHeight());
   }
}
```

### Square
```java
/**
   This class represents immutable squares in the plane.

           Shape
          /     \
         /       \
    Circle       Rectangle
                    |
                    |
                  Square
*/
public class Square extends Rectangle
{
   /**
      @param p       this Square's upper left-hand corner Point
      @param width   width of this Square, must be strictly positive
      @throws IllegalArgumentException when width is not strictly positive
   */
   public Square(Point p, double width)
   {
      super(p, width, width);
   }


   /**
      Return a Square object that has the same upper left-hand
      corner as this Square but with the given width.

      @param width  the width for the new Square
      @return a Square with the given width and the same upper left-hand corner as this Square
   */
   public Square setWidth(double width)
   {
      // implementation
      return new Square(super.getPoint(), width);
   }


   /**
      Return a Rectangle object that has the same width and height
      as this Rectangle but the new Rectangle should have its upper
      left-hand corner at the given Point.

      @param p  Point for the new Rectangle's upper left-hand corner
      @return a Rectangle with the same dimensions but a different upper left-hand corner
   */
   @Override
   public Square translateTo(Point p)
   {
      // implementation
      return new Square(p, super.getWidth());
   }


   /**
      Return a Rectangle object that has the same width and height
      as this Rectangle but the new Rectangle should have its upper
      left-hand corner translated from where this Rectangle's upper
      left-hand corner is.

      @param dx  amount by which to change the x-coordinate from this Rectangle
      @param dy  amount by which to change the y-coordinate from this Rectangle
      @return a Rectangle with the same dimensions but a different upper left-hand corner
   */
   @Override
   public Square translateBy(double dx, double dy)
   {
      // implementation
      Point newCorner = new Point(super.getPoint().getX() + dx, super.getPoint().getY() + dy);
      return new Square(newCorner, super.getWidth());
   }


   @Override
   public String toString()
   {
      // Square[corner=Point: [2.0, 3.0], width=4.0]
      String result = "Square[corner=Point: [" + super.getPoint().getX() + ", " + super.getPoint().getY() + "]";
      result += ", width=" + super.getWidth() + "]";
      return result;
   }


   @Override
   public boolean equals(Object o)
   {
      if (o == this)
      {
         return true;
      }
      if (o == null)
      {
         return false;
      }
      if (!(o instanceof Square))
      {
         return false;
      }

      Square s = (Square)o;
      // Determine if Square s is equal to this Square.
      return (super.getPoint() == s.getPoint() && super.getWidth() == s.getWidth());
   }
}
```

### Point
```java
/**
   This class represents immutable points in the plane.
*/
public class Point
{
   private double x;
   private double y;

   public Point()
   {
      this.x = 0.0;
      this.y = 0.0;
   }

   public Point(double x, double y)
   {
      this.x = x;
      this.y = y;
   }


   /**
      Get the x coordinate of this Point object.

      @return this Point's x-coordinate
   */
   public double getX()
   {
      return this.x;
   }

   /**
      Get the y-coordinate of this Point object.

      @return this Point's y-coordinate
   */
   public double getY()
   {
      return y;
   }


   /**
      Return a Point object that has the same y-coordinate
      as this Point but with the given x-coordinate.

      @param x  x-coordinate for the new Point object
      @return a Point with the given x-coordinate
   */
   public Point setX(double x)
   {
      // implementation
      return new Point(x, this.y);
   }


   /**
      Return a Point object that has the same x-coordinate
      as this Point but with the given y-coordinate.

      @param y  y-coordinate for the new Point object
      @return a Point with the given y-coordinate
   */
   public Point setY(double y)
   {
      // implementation
      return new Point(this.x, y);
   }


   @Override
   public String toString()
   {
      return getClass().getName() + ": [" + x + ", " + y + "]";
   }


   @Override
   public boolean equals(Object o)
   {
      if (o == this)
      {
         return true;
      }
      if (o == null)
      {
         return false;
      }
      if (!(o instanceof Point))
      {
         return false;
      }

      Point p = (Point)o;
      // Determine if Point p is equal to this Point.
      return (this.x == p.getX() && this.y == p.getY());
   }


   /**
      Provide a trivial implementation of hashCode().
   */
   @Override public int hashCode(){ return 1; }
}
```