# January 18th 2024, Labs
## Lab 1
Implement the Pair class that is outlined below.

Implement each class method according to the method's given Javadoc comment.

You do not need to write any code that calls your methods. Your methods will be called and tested by the Tester.java program. The Tester.java program expects a single input integer between 1 and 3. The Tester.java program then runs one of its three built in test cases.
```java
/**
   This class represents pairs of integers.
*/
public class Pair
{
   private int x;
   private int y;
   
   public Pair() // default constructor
   {
      this.x = 0;
      this.y = 0;
   }


   /**
      Create a Pair object with the given values.

      @param x  x-value for the new Pair object
      @param y  y-value for the new Pair object
   */
   public Pair(int x, int y)
   {
      this.x = x;
      this.y = y;
   }


   /**
      Create a Pair object with the given value
      as both its x and y values.

      @param v  value for both numbers in the new Pair object
   */
   public Pair(int v)
   {
      this.x = v;
      this.y = v;
   }


   /**
      Create a Pair object with the same values
      as the given Pair object.

      @param p  Pair object whose values should be copied
   */
   public Pair(Pair p)
   {
      this.x = p.getX();
      this.y = p.getY();
   }


   /**
      Get the x-value of this Pair object.

      @return this Pair's x-value
   */
   public int getX()
   {
      return this.x;
   }


   /**
      Change this Pair object to have the given x-value.

      @param x  new x-value for this Pair object
   */
   public void setX(int x)
   {
      this.x = x;
   }


   /**
      Change this Pair object to have the same x-value
      as the given Pair.

      @param p  Pair object whose x-value should be copied
   */
   public void setX(Pair p)
   {
      this.x = p.getX();
   }


   /**
      Get the y-value of this Pair object.

      @return this Pair's y-value
   */
   public int getY()
   {
      return this.y;
   }

   /**
      Change this Pair object to have the given y-value.

       @param y  new y-value for this Pair object
   */
   public void setY(int y)
   {
      this.y = y;
   }


   /**
      Change this Pair object to have the same y-value
      as the given Pair.

      @param p  Pair object whose y-value should be copied
   */
   public void setY(Pair p)
   {
      this.y = p.getY();
     
   }


   /**
      Change this Pair object to have the same x-value
      and y-value as the given Pair.

      @param p  Pair object whose x-value and y-value should be copied
   */
   public void set(Pair p)
   {
      this.x = p.getX();
      this.y = p.getY();
   }


   /**
      Create a new Pair object that contains the swapped x-value
      and y-value from this Pair object.
     
      @return a new Pair that has the swapped values from this Pair
   */
   public Pair swap()
   {
      Pair result = new Pair(this.y, this.x);
      return result;
   }


   /**
      Determine if this Pair object has the same x-value
      and the same y-value as the given Pair.

      @param p  a reference to a second Pair object
      @return true if the given Pair is equal to this Pair
   */
   public boolean equals(Pair p)
   {
      return (this.x == p.getX() && this.y == p.getY());
   }


   /**
      Determine if the two numbers in this Pair object are the
      same two numbers that are in the given Pair without
      regard for the order of the numbers. So (2,3) and (3,2)
      would have "equal numbers".

      @param p  a reference to a second Pair object
      @return true if this Pair and the other Pair contain the same two numbers
   */
   public boolean equalNumbers(Pair p)
   {
      return (this.x == p.getX() && this.y == p.getY()) || (this.y == p.getX() && this.x == p.getY());
   }


   public String toString()
   {
      return "Pair: (" + x + ", " + y + ")";
   }
}
```

## Lab 2
Implement the Point and Circle classes that are outlined below.

Implement each class method according to the method's given Javadoc comment.

You do not need to write any code that calls your methods. Your methods will be called and tested by the Tester.java program. The Tester.java program expects a single input integer between 1 and 3. The Tester.java program then runs one of its three built in test cases.

### Point Class
```java
/**
   This class represents points in the plane.
*/
public class Point
{
   private double x;
   private double y;
   
   public Point() // default constructor
   {
      this.x = 0.0;
      this.y = 0.0;
   }


   /**
      Create a Point object with the given coordinates.

      @param x  x-coordinate value for the new Point object
      @param y  y-coordinate value for the new Point object
   */
   public Point(double x, double y)
   {
      this.x = x;
      this.y = y;
   }


   /**
      Change this Point object to have the given x-coordinate.

      @param newX  new x-coordinate for this Point object
   */
   public void setX(double newX)
   {
      this.x = newX;
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
      Change this Point object to have the given y-coordinate.

       @param newY  new y-coordinate for this Point object
   */
   public void setY(double newY)
   {
      this.y = newY;
   }

   /**
      Get the y-coordinate of this Point object.

      @return this Point's y-coordinate
   */
   public double getY()
   {
      return this.y;
   }

   /**
      Determine if this Point object has the same x-coordinate
      and the same y-coordinate as the given Point.

      @param p  a reference to a second Point object
      @return true if the given Point is equal to this Point
   */
   public boolean equals(Point p)
   {
      return (this.x == p.getX() && this.y == p.getY());
   }

   /**
      Determine which quadrant of the plane this Point is in.
      Quadrant 1 has positive x and y coordinates.
      Quadrant 2 has negative x coordinates and positive y coordinates.
      Quadrant 3 has negative x and y coordinates.
      Quadrant 4 has positive x coordinates and negative y coordinates.

      Note: The positive x and y axes are in quadranr 1.
            The negative x axis is in quarant 2.
            The negative y axis is in quadrant 3.

      @return the quadrant number of this Point object
   */
   public int quadrant()
   {
      int quadrant = 0;
      if (this.x >= 0.0 && this.y >= 0.0)
      {
         quadrant = 1;
      }
      else if (this.x < 0.0 && this.y >= 0.0)
      {
         quadrant = 2;
      }
      else if (this.x >= 0.0 && this.y < 0.0)
      {
         quadrant = 4;
      }
      else
      {
         quadrant = 3;
      }
      return quadrant;
   }


   public String toString()
   {
      return "Point: [" + x + ", " + y + "]";
   }
}
```
### Circle Class
```java
/**
   This class represents circles in the plane.
*/
public class Circle
{
   private double radius;
   private Point center;

   public Circle() // default constructor
   {
      this.radius = 0;
      this.center = new Point(0, 0);
   }

   public Circle(double r)
   {
      this.radius = r;
      this.center = new Point(0, 0);
   }

   /**
      Create a Circle object with the given radius and center Point.

      @param r  radius for the new Circle object
      @param c  center Point for the new Circle object
   */
   public Circle(double r, Point c)
   {
      this.radius = r;
      this.center = new Point(c.getX(), c.getY());
   }


   /**
      Change this Circle's center point to be the given point.

      @param center  new center Point for the this Circle object
   */
   public void setCenter(Point center)
   {
      this.center = new Point(center.getX(), center.getY());
   }


   public Point getCenter()
   {
      return this.center;
   }


   public void setRadius(double r)
   {
      this.radius = r;
   }

   public double getRadius()
   {
      return this.radius;
   }


   /**
      Translate the center of this circle by the given
      amounts in the x and y directions.
   
      @param dx  how much to move the center of this Circle in the x-direction
      @param dy  how much to move the center of this Circle in the y-direction
   */
   public void translateBy(double dx, double dy)
   {
      this.center = new Point(this.center.getX() + dx, this.center.getY() + dy);
   }


   /**
      Translate the center of this circle to the given
      amounts in the x and y directions.
   
      @param x  new x-coordinate for the center of this Circle
      @param y  new y-coordinate for the center of this Circle
   */
   public void translateTo(double x, double y)
   {
      this.center.setX(x);
      this.center.setY(y);
   }


   public String toString()
   {
      return "Circle: r = " + radius + ", center = [" + center.getX() + ", " + center.getY() + "]";
   }
}
```