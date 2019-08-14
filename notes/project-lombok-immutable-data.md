Today I want to start what will be a series about using Project Lombok to make writing code in Java easier, with less boilerplate.

What is immutable data, you ask? Data where the attributes or values are set once and never changed again. They can't be changed. Ever.

The reason this is great (awesome really) is as your application grows an object with immutable data gets passed from one piece of logic (method) to another and is transformed. This produces unexpected consequences in that path.

For example, let's take a Person class (I know, boring example, but bear with me):

```java
public class Person {
  private String name;
  
  public Person(String name) {
    this.name = name;
  }
  
  public String getName() {
    return name;
  }
  
  public void setName(String name) {
    this.name = name;
  }
}
```

Let's imagine the life of this person object.

A person is created with a name, but only a first name. That person is passed to a method that prints the name to the screen. Everything is great so far.

Then this person object is passed to a method designed to add a last name. Instead of changing the design of the person object to include the last name, it just reads the first name and adds the last name to it then sets it back to the same object:

```java
String name = person.getName();
String name = name + " Smith";
person.setName(name);
```

Any remaining logic in this flow is now unaware the name has changed and to expect a first and last name.

This is just a rudimentary example of how mutable data can create bugs and other unintended results.

There are loads of ways to alter our objects to make them immutable, but the easiest with the least code I've found is 
[Project Lombok](https://projectlombok.org/).

Once setup (I'll address the short configuration required to get Lombok later), you only need to use some special annotations provided:

```java
@Value
public class Person {

    private String name;

}
```

Notice that Project Lombok also generates the getter method and others for you:

```java
public final class Person {
    private final String name;

    @SuppressFBWarnings(
        justification = "generated code"
    )
    @Generated
    public Person(String name) {
        this.name = name;
    }

    @SuppressFBWarnings(
        justification = "generated code"
    )
    @Generated
    public String getName() {
        return this.name;
    }

    @SuppressFBWarnings(
        justification = "generated code"
    )
    @Generated
    public boolean equals(Object o) {
        if (o == this) {
            return true;
        } else if (!(o instanceof Person)) {
            return false;
        } else {
            Person other = (Person)o;
            Object this$name = this.getName();
            Object other$name = other.getName();
            if (this$name == null) {
                if (other$name != null) {
                    return false;
                }
            } else if (!this$name.equals(other$name)) {
                return false;
            }

            return true;
        }
    }

    @SuppressFBWarnings(
        justification = "generated code"
    )
    @Generated
    public int hashCode() {
        int PRIME = true;
        int result = 1;
        Object $name = this.getName();
        int result = result * 59 + ($name == null ? 43 : $name.hashCode());
        return result;
    }

    @SuppressFBWarnings(
        justification = "generated code"
    )
    @Generated
    public String toString() {
        return "Person(name=" + this.getName() + ")";
    }
}
```

There's a lot going on here, but the most important part is there are now no built-in ways to change the data once it is set. If you want to change it, create a new object!

Normally this might seem like lots of extra work just to create a POJO (Plain Old Java Object), but Project Lombok makes it a breeze!

Now make your code more immutable and your life easier in the process!

# 🐾