# Misc
## 1. List down methods present in the Object class

1. clone() : this method is used to create a clone of the object. 

#### [click here ](https://www.youtube.com/watch?v=ANApEG7imgU&t=24s) -> for deep copy and shallow copy explanation.
```java
protected native Object clone() throws CloneNotSupportedException;
// ex :
Customer c4=(Customer) c3.clone();
```


2. Equals() : method is used to check equality of an object.without implementing it will comapre with references of the object to comapre with ***content*** comparrision override the equals method.
```java
 public boolean equals(Object obj) {
        return (this == obj);
    }
```

3. hashcode() : A unique ***ID*** that is assigned to an object is called hashcode of the object.(Assigned by JVM)
```java
    public native int hashCode();
```
4. tostring() : This method Used to return a String representation of the object 
```java 
    public String toString()
```
5. wait()
6. notify()
7. notifyall()
8. finalize() : this method is called by garbage collector on an object when garbage colllection determines that there are no more references to the object.
[click here](https://youtube.com/shorts/vQmzLmAGIA4?feature=share)
```java 
protected void finalize() throws Throwable { }
```
# Strings
## 4. what is String immutable(final class) ? and diff b/w buffer and builder.
A string in Java is a sequence of characters

### Diff's 
1. String  is immutable and cannot be modified once created.
2. StringBuilder  and StringBuffer are mutable and allow modification of strings. 
3. StringBuilder is not thread-safe, while StringBuffer is thread-safe.

### ways to create object
1. String literal

	To make Java more memory efficient (because no new objects are created if it exists already in the string constant pool). 

	String s = “GeeksforGeeks”;

2. Using new keyword

	In such a case, JVM will create a new string object in normal (non-pool) heap memory and the literal “Welcome” will be placed in the string constant pool. The variable s will refer to the object in the heap (non-pool)

	String s = new String (“GeeksforGeeks”);

# OOPS

# Interfaces and Abstract classes

## 2. What is marker interface

No methods: A marker interface does not define any methods. It is empty and serves as a tag or label for the implementing classes.
Some common examples of marker interfaces in Java include 
1. Serializable
2. Cloneable

# Exception handling
# Multithreading
# Java 8












## 5. what is inner class ? and whatis annoymous innerclass ?

## 6. What are Wrapper classes.

## 7. What is Super  keyword.

## 8. What is this keyword.

## 9. what is static block and non static block


# collection framework

## 1. what is Collection class


## 2. what is comaprator and comaparable


### Comaparable
```java
import java.util.*;

class Person implements Comparable<Person> {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
// for age
    @Override
    public int compareTo(Person other) {
        return this.age - other.age;
    }

	// for name 
	// @Override
    // public int compareTo(Person other) {
    //     return this.name.compareTo(other.name);
    // }
}

public class Main {
    public static void main(String[] args) {
        List<Person> personList = new ArrayList<>();
        personList.add(new Person("Alice", 25));
        personList.add(new Person("Bob", 30));
        personList.add(new Person("Charlie", 20));

        System.out.println("Before sorting:");
        for (Person person : personList) {
            System.out.println(person.getName() + " - " + person.getAge());
        }

        Collections.sort(personList);

        System.out.println("\nAfter sorting by age using Comparable:");
        for (Person person : personList) {
            System.out.println(person.getName() + " - " + person.getAge());
        }
    }
}

```
### Comaparator

```java 
import java.util.*;

class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}

public class Main {
    public static void main(String[] args) {
        List<Person> personList = new ArrayList<>();
        personList.add(new Person("Alice", 25));
        personList.add(new Person("Bob", 30));
        personList.add(new Person("Charlie", 20));

        // Custom comparator for sorting by age in descending order
        Comparator<Person> ageComparator = Comparator.comparing(Person::getAge).reversed();
// 		// for name
//  Comparator<Person> ageComparator = Comparator.comparing(Person::getName).reversed();
        // Sort the list using the custom comparator
        Collections.sort(personList, ageComparator);

        // Print the sorted list
        for (Person person : personList) {
            System.out.println("Name: " + person.getName() + ", Age: " + person.getAge());
        }
    }
}


differences

Sorting:

1. With Comparable, the natural ordering of objects is determined within the class itself. Objects can be directly sorted using methods like Collections.sort() or Arrays.sort().

2. With Comparator, the comparison logic is external to the class being compared. Objects can be sorted based on different criteria by passing the appropriate Comparator implementation to methods like Collections.sort() or Arrays.sort().


```



## 3. what is concurrent Hashmap

Thread-Safety: ConcurrentHashMap provides ****thread-safe*** operations, allowing multiple threads to read and modify the map concurrently without the need for external synchronization. It achieves this by internally dividing the map into segments and applying separate locks on each segment.
```java 
// Convert HashMap to synchronized version
        Map<String, Integer> synchronizedMap = Collections.synchronizedMap(hashMap);
```

## Diff b/w concurrent hasmap and hashtable

1. ConcurrentHashMap:
ConcurrentHashMap was introduced in Java 5 as a high-performance concurrent map. It is designed to be used in concurrent multi-threaded environments, allowing multiple threads to access and modify the map concurrently without external synchronization.  
    Concurrency: ConcurrentHashMap uses a different locking mechanism compared to Hashtable. It divides the underlying map into multiple segments, each of which can be locked independently, allowing multiple threads to perform concurrent operations on different segments.

2. Hashtable:
Hashtable is one of the legacy classes in Java that has been available since the early versions of Java. It is also a thread-safe implementation of the Map interface, but its usage is generally discouraged in favor of ConcurrentHashMap.  
   Synchronization: Hashtable uses internal synchronization to ensure thread-safety. Every method is synchronized, which means only one thread can access the Hashtable at a time. This can lead to contention and reduced performance in highly concurrent environments.
## 4. Difference between ArrayList vs Vector(Thread safe)


## 12. what is Singleton 

## 13 what is Synchronization

## 14 what is Serialization

# java 8

## String joiner
## optinal class
## functional interface
## lambda functions
## stream API

## 1 what is  String joiner class (java 8) 


```java 
package com.prep;

import java.util.StringJoiner;

public class SJoiner {

	
	public static void main(String[] args) {
		StringJoiner sj1=new StringJoiner(",","[","]");// 1:delimeter,2:prefix,3:suffix
		
		sj1.add("A").add("B").add("C");
		
		System.out.println(sj1);
		
		StringJoiner sj2=new StringJoiner(":");
		
		sj2.add("P").add("Q");
		
		System.out.println(sj2);
		
		System.out.println(sj1.merge(sj2));
	}
}
```
## 2. what is optional class in java.

## 3 what is functional interface 
An interface that has  only one ***abstract method*** is called functional interface.
But is can have n number of
						***defalt & Static methods***.
```java
@FunctionalInterface
interface MyFunction {
    int apply(int a, int b);
}
```
Available functional interfaces are :
1. Runnable : public abstract void run();
2. Callable : call method();
3. Comaparator : int comapare() & equals()--> this does not count as abstract method bcz its inherited from object class.

### 1. Can one functional interface override another functional inteface.

No, one functional interface cannot directly override another functional interface in Java. 

However, it is possible to extend or refine the behavior of a functional interface by creating a new functional interface that extends or combines existing functional interfaces. This can be done using inheritance or by using default methods to provide additional behavior.

```java
@FunctionalInterface
interface MyFunction {
    int apply(int a, int b);
}

@FunctionalInterface
interface MyExtendedFunction extends MyFunction {
    default int multiply(int a, int b) {
        return a * b;
    }
}
```
### 2. Functional interface introduced in java 8
1. Function<T,R> ---> R apply(T t)
2. Predicate<T> - 	> boolean test(T t) 
3. Supplier<T> -	> T get()
4. Consumer<T> ---	> void accept(T t)



# Misc

## what is Enum

In Java, an enum (short for "enumeration") is a special data type that represents a fixed set of constants. It provides a way to define a collection of named values that are mutually exclusive.

Enums can have methods, constructors, and fields, just like regular classes. Enum constants are implicitly declared as 
``public static final``
```java
public enum DayOfWeek {
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
}
```

Enums can also have additional properties and methods. For example, you can define a method that returns some information or behavior associated with each enum constant:

```java
public enum DayOfWeek {
    // ...

    public boolean isWeekend() {
        return this == SATURDAY || this == SUNDAY;
    }
}
```

## what is join method in java

## pass by value and pass by reference

Technically, Java is always pass by value, because even though a variable might hold a reference to an object, that object reference is a value that represents the object's location in memory. Object references are therefore passed by value. Both reference data types and primitive data types are passed by value.



## what is memory leak

A memory leak in Java refers to a situation where an application unintentionally retains objects in memory, preventing them from being garbage collected and released when they are no longer needed. Over time, this can lead to excessive memory consumption, degraded application performance, and eventually, an OutOfMemoryError.


## how to convert Java to JSON amnaually?
 object mapper class of jackson API 

## RestTemplate

## what are Wrapper Classes 

As java is not complete OOP language to make convert primitive data type to OOP we use Wrapper class.

the wrapper classes are used to convert primitive types into objects and vice versa. The primary purpose of using wrapper classes is to provide additional functionality and methods that are not available for primitive types.

1. Integer: Wraps an int value and provides methods for converting, comparing, and performing arithmetic operations on integers.
2. Boolean: Wraps a boolean value and provides methods for logical operations.
3. Character: Wraps a char value and provides methods for character manipulation.
4. Double: Wraps a double value and provides methods for mathematical operations on floating-point numbers.
5. Float: Wraps a float value and provides methods for floating-point operations.
6. Long: Wraps a long value and provides methods for working with large integer values.
7. Short: Wraps a short value and provides methods for working with short integers.
8. Byte: Wraps a byte value and provides methods for working with byte data.

Wrapper classes are often used in scenarios where objects are required, such as when using collections or generics that can only store objects.

## access modifier

In Java, access modifiers are keywords that are used to control the visibility and accessibility of classes, methods, variables, and constructors within a program. Java provides four different access modifiers:

1. Public: The public access modifier is the most permissive. Public members can be accessed from anywhere, including other classes, packages, and even outside the package.
2. Private: The private access modifier is the most restrictive. Private members can only be accessed within the same class. They are not visible or accessible from other classes or even subclasses.
3. Protected: The protected access modifier allows access from the same class, subclasses within the same package, and subclasses in different packages. It is similar to private but allows subclass access.
4. Default (Package-private): If no access modifier is specified, it is considered as the default access modifier. Members with default access can only be accessed within the same package. They are not accessible outside the package, even by subclasses.


## what is checked exception.

1. checked Exception : Checked exceptions are exceptions that are checked at compile-time by the Java compiler.

Some examples of checked exceptions in Java include IOException, SQLException, and ClassNotFoundException. These exceptions typically represent exceptional conditions that can occur during input/output operations, database access, or class loading, respectively.

```java
public void readFile() throws IOException {
    // Code that may throw IOException
}

public void handleFile() {
    try {
        readFile();
    } catch (IOException e) {
        // Exception handling code
    }
}
```

2. Unchecked exceptions, also known as runtime exceptions, are exceptions that are not checked at compile-time.
```java
public void divide(int a, int b) {
    int result = a / b; // Throws ArithmeticException if b is 0
}
```

## thread scheduling

Scheduling in threads refers to the mechanism by which the operating system determines which threads should execute and for how long. The scheduling algorithm determines the order in which threads are allocated CPU time, allowing multiple threads to run concurrently.

Java provides two main types of thread scheduling:

1. Preemptive Scheduling: Preemptive scheduling is the default scheduling mechanism used by most operating systems. In preemptive scheduling, the operating system can interrupt a running thread and switch to another thread based on its priority and time-slicing. The JVM relies on the operating system's preemptive scheduler to manage thread execution.

2. Cooperative Scheduling: Cooperative scheduling is a scheduling mechanism where threads voluntarily yield control to other threads. In cooperative scheduling, each thread is responsible for explicitly giving up control when it is done or waiting for a certain condition. Cooperative scheduling can be implemented using techniques such as explicit thread yielding or using cooperative constructs like Thread.yield() or Thread.sleep().

## resizing the arraylist and linked list 

## Contigious memory allocation

## coding QA

1. String str="hello world hello"
output :
hello 2
world 1

2. a=23415
b=24

output : 23415

24 is not present in a

2. a=23415
b=34

output : 215



