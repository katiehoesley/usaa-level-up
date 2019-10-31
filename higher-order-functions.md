
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

Write a basic algorithm that checks whether a word is a palindrome!

Write a basic algorithm that takes in two numbers as arguments and returns the product of those two numbers multiplied together. 

- “Multiply”: https://www.codewars.com/kata/50654ddff44f800200000004


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

- “Alternating Case” [map?]: https://www.codewars.com/kata/56efc695740d30f963000557


## Useful Resources! 
- [Fun Fun Functions HOFs Part I](https://www.youtube.com/watch?v=BMUiFMZr7vk&feature=youtu.be)
- [Fun Fun Functions HOFs Part II](https://www.youtube.com/watch?v=bCqtb-Z5YGQ&feature=youtu.be)
- [Fun Fun Functions HOFs Part III](https://www.youtube.com/watch?v=Wl98eZpkp-c&feature=youtu.be)



