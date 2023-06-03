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

## 2. What is marker interface

No methods: A marker interface does not define any methods. It is empty and serves as a tag or label for the implementing classes.
Some common examples of marker interfaces in Java include 
1. Serializable
2. Cloneable

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

## 4. Difference between ArrayList vs Vector(Thread safe)


## 12. what is Singleton 

## 13 what is Synchronization

## 14 what is Serialization

# java 8

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

## pass by value and pass by reference

Technically, Java is always pass by value, because even though a variable might hold a reference to an object, that object reference is a value that represents the object's location in memory. Object references are therefore passed by value. Both reference data types and primitive data types are passed by value.



## what is memory leak

A memory leak in Java refers to a situation where an application unintentionally retains objects in memory, preventing them from being garbage collected and released when they are no longer needed. Over time, this can lead to excessive memory consumption, degraded application performance, and eventually, an OutOfMemoryError.




