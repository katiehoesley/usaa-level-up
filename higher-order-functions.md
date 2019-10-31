<<<<<<< HEAD

# Friday 11/1


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
Have students solve each of these algorithms (pair on some, do one on the board, mix it up) and have them verbally walk through the algorithm to ensure understanding.

- “Make Upper Case”: https://www.codewars.com/kata/57a0556c7cb1f31ab3000ad7
- Swift foxes - given an array of different types of foxes, one of them is a SWIFT fox, write a method that only returns the swift foxes
- Given an array of numbers, return an array of numbers without any duplicates - use this array : [1, 55, 5, 2, 3, 4, 4, 4, 7, 6, 55, 444, 1, 321, 64, 66788, 342, 11, 55, 55, 2]
- “Alternating Case”: https://www.codewars.com/kata/56efc695740d30f963000557
- “Multiply”: https://www.codewars.com/kata/50654ddff44f800200000004

## Streams

Before we jump into HOFs, let’s cover Streams. You’ll need to use streams when you use Map, Filter, Reduce in Java, so it’s important that you understand what they are and how to use them. 

The Streams API was introduced in Java8 and it used to process collections of objects. A stream is a sequence of objects that supports various methods which can be pipelined to produce the desired result.

**FEATURES OF A JAVA STREAM:**

- A stream is not a data structure. It takes input from the Collections, Arrays or I/O channels
- Streams *don’t* change the original data structure, they only provide the result as per the pipelined method
- Each intermediate operation is lazily executed and returns a stream as a result, hence various intermediate operations can be pipelined. Terminal operations mark the end of the stream and return the result.

(Resource: https://www.geeksforgeeks.org/stream-in-java/)


## Lambdas
So, what is a lambda? 

A lambda in Java is Java’s first step into functional programming. A Java lambda expression is thus a function whcih can be created without belonging to any class. They’re commonly used to implement simple even listeners/callbacks, or in functional programming with the Java Streams API.

Lambdas in Java are functions that are not bound to any object. This allows you to pass them around to different parts of your code. 

**Concise Lambdas:**

```
List<String> words = new ArrayList<>(Arrays.asList("foo bar", "foo bar baz", "hello world"));

words.forEach(word -> System.out.println(word));
```

*Notes on syntax:* 

- You can write a lambda with no parenthases around a parameter if there is only ONE parameter. If there are more, you must use parenthases. 

- If you only have one statement in the lambda, then you do NOT need to use curly braces. 

**Expanded Lambdas:**

- The above syntax is extremely concise, but when you need to do more work inside your lambda, you can use expanded syntax. 

- The code example in the “concise lambdas” section could be rewritten in a more verbose fashion like this: 

```
List<String> words = new ArrayList<>(Arrays.asList("foo bar", "foo bar baz", "hello world"));

words.forEach((String word) -> {
    // you could write additional code here
    System.out.println(word);
});
```



#Higher Order Functions 

Higher order functions are a language agnostic concept where a function takes in another function as an argument, or returns a function as its result. The most commonly used HOFs are map, filter, and reduce.

These methods all allow us to iterate over an array without using a for-loop. 

**Why would you want to iterate WITHOUT using a for-loop if these HOFs are basically for-loops under the hood?**


## Map: Array.map()

The `map` method invokes a function for each element of an array. It allows each element to be transformed and pushed into a new array. 

The `map` method creates a new array that is the same size as the original array. This new array is the return value, and it does NOT mutate the original array. 

It applies a function to each element of the original array and pushed that return value into the new array.

The HOFs are easier and more intuitively used in JavaScript, so I’ll give examples in JS and then in Java to help nail down the concept. 

```
const numbers = [1, 2, 3, 4]; 

const squares = numbers.map((number) => number * number)

console.log(squares)
```

Java example: 

```
    public static void main(String args[]) {
       List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);
       List<Integer> squares = numbers.stream()
                                      .map( i -> i*i)
                                      .collect(Collectors.toList());
       System.out.println("original list of numbers : " + numbers);
       System.out.println("transformed list of integers using Map in Java 8 : "
                                   + squares);

    }
```

#### TASK: Use .map() to take an array of strings and turn them all to upper case

## Filter: Array.filter()
The `filter` method invokes a function for each element of an array, but allows each element to be filtered out of a new array. 

The `filter` method creates a new array that is NOT larger than the original array. 

It applies a function to each element of the original array. 

It pushes the element into the new array if the function returns true. 

The function passed to the `filter` method is called a ‘predicate’ becuase its value will be true or false. 


Javascript 

```
const numbers = [1, 2, 3, 4]

const oddNumbers = numbers.filter(function(number) {
	return element %2 !==0
})

OR 

const oddNumbers = numbers.filter(number => number %2 !==0)
```

Java8
```
public static void main(String[] args) {
    List<String> numbers = Arrays.asList("1", "2", "3", "4", "5", "6");
    System.out.println("original list: " + numbers);
    List<Integer> even = numbers.stream()
                                .map(s -> Integer.valueOf(s))
                                .filter(number -> number % 2 == 0)
                                .collect(Collectors.toList());
    System.out.println("processed list, only even numbers: " + even);
}
```

#### TASK: Use .filter() to take an array of numbers and return only numbers greater than 5

## Reduce: Array.reduce()
It’s fairly common to need to perform operations where a stream reduces to a single value. For example: maximum, minimum, sum, product, etc. Reducing is the repeated process of combining elements. 

The `reduce` method has a lot to offer and can be thought of as a Swiss Army knife. The use of `reduce` is best described through examples: summing all of the numbers in an array and multiplying all of the numbers in an array. 

```
const numbers = [1, 2, 3, 4]

let result = 0;

for(let number of numbers) {
	result = result + num
}
```

- So, the initial value of `result` is 0 
- We can abstract this common task with the `reduce` method!

```
const numbers = [1, 2, 3, 4]

const sum = numbers.reduce((result, number) => {
	return result + number; 
}, 0)

console.log(sum)
```

Java8 Example: 

```
public static void main(String[] args) 
    { 
        //creating a list of Strings 
        List<String> words = Arrays.asList("GFG", "Geeks", "for", 
                                           "GeeksQuiz", "GeeksforGeeks"); 
        // The lambda expression passed to 
        // reduce() method takes two Strings 
        // and returns the longer String. 
        // The result of the reduce() method is 
        // an Optional because the list on which 
        // reduce() is called may be empty. 
        Optional<String> longestString = words.stream() 
                                   .reduce((word1, word2) 
                             -> word1.length() > word2.length() 
                                           ? word1 : word2); 
        // Displaying the longest String 
        longestString.ifPresent(System.out::println); 
} 
```

#### TASK: Use .reduce() to combine an array of individual letter strings into one string

## Check for Understanding:

Which HOF would you use to make an array of strings all upper case?

- “Make Upper Case” [map]: https://www.codewars.com/kata/57a0556c7cb1f31ab3000ad7

Which HOF would you use to eliminate items from an array that don’t match a certain criteria? [filter]

- Swift foxes - given an array of different types of foxes, one of them is a “swift fox”, write a method that only returns the swift foxes


Which HOF would you use to eliminate all duplicates from an array? [filter]

- Another good filter is return an array without duplicates 


Which HOF would you use to add up all elements in an array and return the total? [reduce]


**More Complicated Examples:**

- Next reduce one that’s more complicated: given a bunch of addresses return an array of the unique zip codes 


## Useful Resources! 
- [Fun Fun Functions HOFs Part I](https://www.youtube.com/watch?v=BMUiFMZr7vk&feature=youtu.be)
- [Fun Fun Functions HOFs Part II](https://www.youtube.com/watch?v=bCqtb-Z5YGQ&feature=youtu.be)
- [Fun Fun Functions HOFs Part III](https://www.youtube.com/watch?v=Wl98eZpkp-c&feature=youtu.be)


## When done: Solve shopping cart in Java
*Don’t open these if you are a student looking ahead - this is meant to be done in class, timed!*

- https://github.com/gSchool/shopping-cart-interview-jest
- Rubric: https://github.com/gSchool/shopping-cart-interview-jest/blob/master/README.md

## When done: Pair on 4 level 8 CodeWars algorithms
- https://www.codewars.com/kata/5772da22b89313a4d50012f7
- https://www.codewars.com/kata/5168bb5dfe9a00b126000018
- https://www.codewars.com/kata/565f5825379664a26b00007c
- https://www.codewars.com/kata/58f8a3a27a5c28d92e000144

## When done: Pair on Reverse Polish Calculator


=======
# Friday 11/1


>>>>>>> 6ef4fbab2a213db059714053353a718dd40b46d1
