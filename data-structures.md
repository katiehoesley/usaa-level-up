# Data Structures in Java

## Data types in Java 
**Primitive types** in Java are the most basic data types available within the language. There are 8: 

- boolean
- byte
- char
- short
- int 
- long 
- float 
- double

**Non-primitive data types** in Java include Strings, Classes, Interfaces, and Arrays. 


## Arrays
Arrays are a data structure that can store a fixed-size sequential collection of elements of the same type. Elements can be accessed using indexes.

Standard arrays are statically sized; once *Array* has been initialized with a set of values or a size, it cannot be resized. 

```
//Initialize with a size: 
String[] addresses = new String[10];

//Initialize with values:
int[] evenNumbers = new int[]{2, 4, 6, 8};
```

**Accessing arrays:**

The elements within an array are accessed using the *bracket notatino* where the square brackets take as input the *index* of the element you want to access. 

```
//Get the third address in the ‘addresses’ array
String someAddress = addresses[2]; 

//Get the second number in the ‘evenNumbers’ array 
int someEven = evenNumbers[1]; 
```

**Iterating over arrays:**
An Array can be iterated over using either a normal “for loop” or a “for-each loop”. 

```
//Print all the numbers in the ‘evenNumbers’ array using a normal for-loop

for(int i = 0; i < addresses.length; i++) {
	System.out.println(addresses[i]
}

//Print all the addresses in the ‘addresses’ array using a for-each loop
for(String address : addresses) {
	System.out.println(address)
}
```

## Lists 
A List is a child interface of Collection. It is an ordered collection of objects in which duplicate values can be stored. 

Since List preserves the insertion order, it allows positional access and insertion of elements. List Interface is implemented by ArrayList, LinkedList, Vector and Stack classes.

List is an interface, and the instances of List can be created in the following ways: 

```
List a = new ArrayList(); 
List b = new LinkedList();
List c = new Vector(); 
List d = new Stack(); 
```



## ArrayList 
This class uses dynamic arrays for stories elements, and arrays are sequentially arranged in the memory. It implements the List interface. 

Elements can be added without having to initialize its size. 

An ArrayList can also be instantiated from an existing *Array*.

```
//Instantiate an empty ArrayList
ArrayList<String> addresses = new ArrayList<>();

//Add elements to an ArrayList
addresses.add(“123 Bose St.”);
addresses.add(“189 W. Sennheiser St”);;

//Instantiate and initialize with elements
ArrayList<Integer> evenNumbers = new ArrayList<>(Arrays.asList(2, 4, 8, 6));

//Initialize an ArrayList from an existing Array
String[] products = new String[]{“Magic Vest, “Old Staff”, “Spurious Rock”}; 

ArrayList<String> productList = new ArrayList<>(Arrays.asList(products));
```

Another major advantage to using ArrayList over an Array is that ArrayList class implements both Collections and the List interfaces. This gives you additional functionality over normal arrays and allows you to do things like sort, reverse, and check for membership, which are operations you would usually want to perform on lists. 

```
//Instantiate the ArrayList 

ArrayList<Double> numberList = new ArrayList<>();

numberList.add(0.9);
numberList.add(1.0);
numberList.add(0.3);
numberList.add(0.4); 
```

Now, because ArrayList implements the `sort` method from the List interface, you can simply call the method: 

```
numberList.sort(null)

System.out.println(numberList);
```

and it will output `[0.3, 0.4, 0.9, 1.0]`


## HashMaps
A HashMap is used to store key-value pairs. It implements the Map interface and is not a part of the collection. 

HashMap using the hashing technique to store key-value pairs. The key-value pair is called a **bucket**. Each bucket is stored in an array in the HashMap class. The hashing function works on the key and returns an index at which the bucket is stored. 

There are chances of two keys returning the same index upon hashing. In such cases, the buckets are stored at the same index but are linked, the same as in a Linked List. 

HashMap contains two basic methods: `get` and `put`, to get the value and put the key-value pair in the map. 

To declare and instantiate a HashMap with keys that are strings and values that are integers, do this: 

```
HashMap<String, Integer> numbers = new HashMap<>();
```

Notice that the types are only needed in the declaration. They are not needed in the call to construct the new HashMap because the types are inferred. 

You will use this HashMap to look up the integer corresponding to the English word for a given number, so add some items as follows: 

```
numbers.put(“zero”, 0); 
numbers.put(“one”, 1);
numbers.put(“two”, 2);
```
Now, the integer corresponding to the number “one” can now be looked up with: 

`Integer num = numbers.get(“one”);`


## Enums 
**What is an enum?:** An enum is a special Java type used to define collections and constants. 

An enum is a special “class” that represents a group of constants (unchangeable variables, like `final` variables). 

You should use an `enum` when you have a hard-coded list of values that will remain consistent. This allows you to avoid strings, which are brittle and will not trigger compile errors for typos.

To create an enum, use the `enum` keyword (instead of class or interfact), and separate the constants with a comma. Note that they should be in uppercase letters: 

```
enum Level {
	LOW,
	MEDIUM,
	HIGH
}
```

To access `enum` constants, use the dot syntax: 

```
Level myLevel = Level.MEDIUM;
```

You can also have an `enum` inside a class:

```
public class MyClass {
	enum Level {
		LOW,
		MEDIUM,
		HIGH
	}

	public static void main(String[] args) {
		Level myLevel = Level.MEDIUM;
		System.out.println(myLevel)
	}

}

```

**When to use an enum:** You should use an enum when you have a hard-coded list of values that will remain constant. This allows you to avoid strings, which are brittle and iwll not trigger compile errors for typos. 

Enums have a `.values()` method, which returns an array of all enum constants. This method is useful when you want to loop through all the constants of an enum, or (for some reason) see all of the values in the enum.

```
for (Level myLevel : Level.values()) {
	System.out.println(myLevel)
}
```

and your output would be: 

```
LOW
MEDIUM
HIGH
```

####Try this:
Create an enum named `Role` for the `User` class with the values `OWNER, ADMIN, USER`

```
class User {
    //declare your enum here
}
```

## Interfaces
An interface is a reference type in Java. But... what does that mean?

An interface defines behavior that can be shared among several classes. The classes that share this behavior are said to ***implement*** the interface.  Another wayt o describe an interface is to say it is a contract to which a class must agree. 

An interface is 100% abstract class and has only abstract methods. 

A Class can implement any number of interfaces.

Interfaces look a LOT like classes. In their most common form, they contian no fields, and the methods they include never have implementations, this is left to the classes to implement.

So - most interfaces are collections of method signatures and these defined the common behavior that classes can share. 

(Method signature: method name + parameter list

```
public void setMapReference(int xCoordinate, int yCoordinate) {
	//method code 
}
```
In the above method, the methid signature is `setMapReference(int, int)`

)

To use an interface in your class, append the word ‘implements’ after your class name followed by the interface name.

`class Dog implements Pet`


## Checks for Understanding! 

**Question:** Which of the data structures we’ve discusses are the best option for holding an indeterminate number of elements? 
**Answer:** ArrayList


**Question:** What is the data structure assigned to the variable `accounts` in the following code snippet? 

```
int balance = 0;

for(int i = 0; i < accounts.length; i++) {
  balance += accounts[i];
}
```
**Answer:** `int[]` 

Since the snippet uses accounts.length instead of accounts.size() and bracket notation instead of accounts.get(i), you can conclude that accounts is an Array. Additionally, the values of those elements are being added to the variable balance which is an int. Therefore, accounts must be an int[].


**Now, let’s implement some of what we’ve learned to write some basic algorithms!**

Write a basic algorithm that checks whether a word is a palindrome!

Write a basic algorithm that takes in two numbers as arguments and returns the product of those two numbers multiplied together. 

- “Multiply”: https://www.codewars.com/kata/50654ddff44f800200000004