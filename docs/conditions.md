
Kotiln features several ways to implement conditional logic:
- if/Else statements
- When statements
- For Loops
- While loops

# if/Else statements

```kotlin
val a = 10
val b = 20

if(a>b){
    println("a is great")
} else {
    println("b is great")
}
```
Output: ```b is great```

## If statement with multiple cases
```
val books = 10
if (books == 0){
    println('No books')
} else if (books < 20){
    println('few books')
} else {
    println("More books")
}
```
Output: ```few books```

## Ranges in if/else statments


- Data types containing a span of comparable values (e.g. integers from 1 to 100 inclusive)
- Ranges are bounded
- Objects within a range can be mutable or immutable.

```kotlin
val numberOfEmployees = 50
if (numberOfEmployees in 1..100) {
    println("numberOfEmployees")
}
```
Output: ```50```

## when statement
```
when(results)
    0 -> println("No Results")
    in 1..39 -> println("Got Results")
    else -> println("That's a lot of results")
```
Output: ```That's a lot of results```

Note: As well as a when statement, you can also define a ```when``` expression that provides a return value.

## for Loops

```
val pets = arrayOf("dog","cat","rabbit")
for (element in pets){
    print(element + " ")
}
```
Output: ```dog cat rabbit```

You don't need to define an iterator variable and increment it for each pass.


## for loops: elements and indexes

```
for((index, element) in pets.withIndex()){
    println("Item at $index is $element\n")
}
```
Output: ```
Item at 0 is dog
Item at 1 is cat
Item at 2 is robbit```

## for loops: step sizes and ranges

```
for(i in 1..5) print(i)
```
Output: ```12345```

```for(i in 5 downTo 1) print(i)```
Output: ```54321```

```for(i in 3..6 step 2) print(i)```
Output: ```35```

```for(i in 'd'..'g') print(i)```
Output: ```defg```

## while loops

```
var chairs = 0
while(chairs<50){
    chairs++
}
println("There are $chairs chairs available\n")
```

Output: ```There are 50 chairs available```

```
do {
    chairs--
} while(chairs>50)
println("$chairs chairs available")
```
Output: ```49 chairs available```

## repeat loops

```
repeat(3){
    print("Hey")
}
```
Output: ```HeyHeyHey```

