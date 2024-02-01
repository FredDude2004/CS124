```java
# January 25th 2024 Labs
## Lab 1
Given a Book base class, define a subclass called Encyclopedia with member methods to get and set private fields of the following types:

String to store the edition
int to store the number of pages
In the Encyclopedia subclass, define a toString() method that adds the two additional fields to the result from the toString() method from the Book class. Look at the implementation of toString() in the Book class to get a sense of how to implement the toString in Encyclopedia (the toString method in Encyclopedia needs to use the super keyword to call the toString method in Book).

Ex. If the input is:
<pre>
The Hobbit
J. R. R. Tolkien
George Allen & Unwin
21 September 1937
The Illustrated Encyclopedia of the Universe
Ian Ridpath
Watson-Guptill
2001
2nd
384
</pre>
the output is:
<pre>
Book Information:
   Book Title: The Hobbit
   Author: J. R. R. Tolkien
   Publisher: George Allen & Unwin
   Publication Date: 21 September 1937
Book Information:
   Book Title: The Illustrated Encyclopedia of the Universe
   Author: Ian Ridpath
   Publisher: Watson-Guptill
   Publication Date: 2001
   Edition: 2nd
   Number of Pages: 384
</pre>
### Encyclopedia
```java
public class Encyclopedia extends Book
{
   // TODO: Declare two private fields
   private String edition;
   private int pages;
   
   
   // TODO: Define mutator methods -
   //       setEdition(), setNumPages()
   public void setEdition(String s)
   {
      this.edition = s;
   }
   public void setNumPages(int n)
   {
      this.pages = n;
   }
 
 
   // TODO: Define accessor methods -
   //       getEdition(), getNumPages()
   public String getEdition()
   {
      return this.edition;
   }
   public int getNumPages()
   {
      return this.pages;
   }
   
   
   // TODO: Define a toString() method that adds the new fields
   //       to the toString() result from the Book class
   @Override
   public String toString()
   {
      String result = super.toString();
             result += "\n   Edition: " + this.edition + "\n";
             result += "   Number of Pages: " + this.pages;
      return result;
   }
}
```

## Lab
This lab continues the previous lab.

Give the Book and Encyclopedia classes proper constructors that set all of the fields in the class.

You only need to define one constructor in each class, the "full" constructor that takes values for all the fileds in the class.

The constructor in the Encyclopedia class will need to use the super keyword to call the constructor in the Book class and give it its share of the fileds.

Start this lab by copying your solution for the Encyclopedia class from the previous lab into thiis lab. Then add the constructor to each of the Book and Encyclopedia classes.

NOTE: There are some intentional typos and errors in the BookInformation class that you have to find and correct.

### BookInformation
```java
import java.util.Scanner;

public class BookInformation
{
   public static void main(String[] args)
   {
      Scanner in = new Scanner(System.in);

      String title = in.nextLine();
      String author = in.nextLine();
      String publisher = in.nextLine();
      String publicationDate = in.nextLine();

      Book myBook = new Book(title, author, publisher, publicationDate);

      System.out.println( myBook );


      String eTitle = in.nextLine();
      String eAuthor = in.nextLine();
      String ePublisher = in.nextLine();
      String ePublicationDate = in.nextLine();
      String edition = in.next();
      int numPages = in.nextInt();

      Encyclopedia myEncyclopedia = new Encyclopedia(eTitle, eAuthor, ePublisher,
                                                     ePublicationDate, edition, numPages);

      System.out.println( myEncyclopedia );
    }
}
```

### Book
```java
public class Book
{
   private String title;
   private String author;
   private String publisher;
   private String publicationDate;

   // TODO: Define a full constructor
   public Book(String newTitle, String newAuthor, String newPublisher, String newPublicationDate)
   {
      this.title = newTitle;
      this.author = newAuthor;
      this.publisher = newPublisher;
      this.publicationDate = newPublicationDate;
   }

   public void setTitle(String userTitle)
   {
      title = userTitle;
   }

   public String getTitle()
   {
      return title;
   }

   public void setAuthor(String userAuthor)
   {
      author = userAuthor;
   }

   public String getAuthor()
   {
      return author;
   }

   public void setPublisher(String userPublisher)
   {
      publisher = userPublisher;
   }

   public String getPublisher()
   {
      return publisher;
   }

   public void setPublicationDate(String userPublicationDate)
   {
      publicationDate = userPublicationDate;
   }

   public String getPublicationDate()
   {
      return publicationDate;
   }

   @Override
   public String toString()
   {
      String result  = "Book Information:\n";
             result += "   Book Title: " + title + "\n";
             result += "   Author: " + author + "\n";
             result += "   Publisher: " + publisher + "\n";
             result += "   Publication Date: " + publicationDate;
      return result;
   }
}
```

### Encyclopedia
```java
// Copy your version of Encyclopedia from the previous lab and
// then define a full constructor for the Encyclopedia class.

public class Encyclopedia extends Book
{
   // TODO: Declare two private fields
   private String edition;
   private int pages;
   
   public Encyclopedia(String newTitle, String newAuthor, String newPublisher,
                       String newPublicationDate, String newEdition, int newPages)
   {
      super(newTitle, newAuthor, newPublisher, newPublicationDate);
      this.edition = newEdition;
      this.pages = newPages;
   }
   
   // TODO: Define mutator methods -
   //       setEdition(), setNumPages()
   public void setEdition(String s)
   {
      this.edition = s;
   }
   public void setNumPages(int n)
   {
      this.pages = n;
   }
 
 
   // TODO: Define accessor methods -
   //       getEdition(), getNumPages()
   public String getEdition()
   {
      return this.edition;
   }
   public int getNumPages()
   {
      return this.pages;
   }
   
   
   // TODO: Define a toString() method that adds the new fields
   //       to the toString() result from the Book class
   @Override
   public String toString()
   {
      String result = super.toString();
             result += "\n   Edition: " + this.edition + "\n";
             result += "   Number of Pages: " + this.pages;
      return result;
   }
}
```
```