# About Functions

- Generally a function is a block of code that can perform specific task.
- Function breaks large program  into smaller modular chunks.
- Declare using the ```fun``` keyword.
- Can take arguments with either named or default arguments.

```kotlin
fun printHello() {
    println("Hello World")
}
```

You can call the above function by ```printHello()```


# Unit returning functions

A function that does not return any useful value, its return type is Unit.

```kotlin
function printHello(name: String?): Unit {
    println("Hi There!")
}
```

```Unit``` is a type with only one value: ```Unit```

## Unit returning functions

- The ```Unit``` return type decleration is optional.

```kotlin
fun printHello(name: String?): Unit{
    println('Hi there!')
}
```
Which is equivalent to:

```kotlin
fun printHello(name: String?){
    println("Hi there!")
}
```

# Function Arguments

Functions may have different types of arguments.

- Default parameters
- Required parameters
- Named arguments

## Default paramenters

Default values provides a fallback if no parameter value is passed.

```kotlin
fun drive(speed: Strring = "fast") {
    println("driving $speed")
}
```

```kotlin
drive()  # driving fast
drive("slow") #driving slow
drive(speed = "turtle-like") #driving turtle-like
```

## Required parameters

If no default is specified for a parameter, the corresponding argument is required.

```kotlin
fun tempToday(day: String, temp: Int) {
    println("Today is $day and it's $temp degrees")
}
```

## Default versus requred paramenters

Functions can have a mix of default and required parameters.

```kotlin
fun reformat(str: String, divideByCamelHumps: Boolean, wordSeprator: Char, 
            normalizedCase: Boolean = true){
    println('$str $divdeByCamelHUmps $wordSeprator $normalizedCase')
```

Pass in required arguments

```kotlin
reformat("Today is a day like no other day", false,'-')
```

## Named arguments

To improve readability, use named arguments for required arguments.

```kotlin
reformat(str, divideByCamelHumps = false, wordSeparator = '_')
```


It's considered good style to put default arguments after positional arguments, that way caller only have to specify the required arguments.

# Compact functions

## Single-expression functions

Compact functions, or single-expression functions, make your code more concise and readable.

```kotlin
fun double(x: Int): Int{
    x * 2
}
```

Short form of above function

```kotlin
fun double(x: Int):Int = x*2    #compact version

```

# Lambdas and higher-order functions

- Kotlin functions can be stored in variables and data structures.

- They can be passed as arguments to, and returned from, other higher-order functions.

- You can use higher-order functions to create new "built-in" functions.

## Lambda functions

- A lambda is an expression that makes a function that has no name.

```
var dirtyLevel = 20
val waterFilter = {level: Int -> level/2}
println(waterFilter(dirtyLevel))
```

Output: ```10```

## Syntax for function types

- Kotlin's syntax for function types is closely related to its syntax for lambdas.
- Declare a variable that holds a function.

```kotlin
var waterFilter: (Int) -> Int = {level -> level/2}
```

Here ```waterFilter``` is Variable name

## Higher-order functions

Higher-order functions take functions as parameters, or return a function.

```
fun encodeMsg(msg: String, encode: (String)->String): String{
    return encode(msg)

} 
```

The body of the code calls the function that was passed as the second argument, and passes  the first argument along to it.

To call this function, pass it a string and function.

```kotlin
val enc1: (String) -> String = { input -> input.toUpperCase()}
println(encodeMsg("abc", enc1))
```

Using a function type seperates its implementation from its usage.

## Passing a function reference

Use the ```::``` operator to pass a named function as an argument to another function.

```kotlin
fun enc2(input:String): String = input.reversed()
encodeMesage("abc",::enc2)
```

The ```::``` operator lets kotlin know that you are passing the function reference as an argument, and not trying to call the function.

## Last parameter call syntax

Kotlin prefers that any parameter that takes a function is  the last parameter.

```kotlin
encodeMessage("acronym", {input -> input.toUpperCase() })
```

You can pass a lambda as a function parameter without putting it inside the parentheses.

```kotlin
encodeMsg("acronym") { input-> input.toUpperCase() }
```

## Using higher-order functions

Many kotlin built-in functions are defined using last parameter call syntax.

```kotlin
inline fun repeat(times: Int, action: (Int)->Unit)
repeat(3){
    print("Hello")
}
```

# List filters

## List filters

Get part of a list based on some condition.


|red| red-orange | dark red | orange | bright orange | saffron | 
|---|-------------|----------|--------|---------------|---------|


                 Apply filter() on list 
                    Condition: element contains "red"
                    
                    
|red| red-orange | dark red |  
|---|-------------|----------|
                
## Iterating through lists

If a function literal has only one parameter, you can omit its decleration and the "->". The parameter is implicitly declared under the name ```it```.

```
val ints = listOf(1,2,3)
ints.filter{ it>0}
```

Filter iterates through a collection, where ```it``` is the value of the element during the iteration. This is equivalent to:

```kotlin
ints.filter{ n: Int -> n > 0} 
// OR
ints.filter{ n-> n>0}
```
## List filters

The filter condition in culry braces {} tests each item as the filter loops through.
If the expression returns ```true```, the item is included.

```kotlin
val books = listOf("nature","biology","birds")
println(books.filter{ it[0]=='b'})
```

Output:
```
[biology, birds]
```

## Eager and lazy filters

Evaluation of expressions in lists.

- Eager: Occurs regardless of whether the result is ever used.
- Lazy: Occurs only if  necessary at runtime.

Lazy evaluation of lists is useful if you don't need the entire result, or if the list is exceptionally large and multiple copies wouldn't fit into RAM.

### Eager filters

Filters are eager by default. A new list is created each time you use a filter.

```kotlin
val instruments = listOf("viola","cello","violin")
val eager = instruments.filter{ it[0]=='v' }
println()
```

Output: ```eager:[viola, violin]```

### Lazy filters

Sequences are data strucutres that use lazy evalution, and can be used with filters to make them lazy.

```kotlin
val instruments = listOf("viola","cello","violin")
val filtered = instruments.asSequence().filter{ it[0]=='v' }
println("filtered: "+ filtered)
```

## Sequences -> lists

Sequences can be turned back into lists using toList().

```kotlin
val filtered = instruments.asSequence().filter{ it[0]=='v'}
val newList = filtered.toList()
println("new list:"+ newList)
```
Output:
```new list: [viola, violin]```


## Other list transformations

- map() performs the same transform on every item and returns the list.
    
```
val numbers= setOf(1, 2, 3)
println(numbers.map { it * 3})
```
Output:
```
[3, 6, 9]
```

- ```flatten()``` returns a single list of all the elements of nested collections.
```
val numberSets = listOf(setOf(1,2,3), setOf(4,5), setOf(1,2))
println(numberSets.flatten())
```

Output:
```
[1, 2, 3, 4, 5, 1, 2]
```