# Basic Data Types

# Integer types

| Type    | bits    | Notes     |
|---------|---------|-----------|
| Long    | 64      | From -2<sup>63</sup> to 2<sup>63</sup> -1|
| Int     | 32      | From -2<sup>31</sup> to 2<sup>31</sup> -1|
| Short   | 16      | From -32768 to 32767|
| Byte    | 8       | From -128 to 127|

- Now let us see how to declare int data types
```kotlin
var a : Int = 12
println(a)
```
Output: 12

```kotlin
val b : Long = 132432
println(b)
```
Output: 132432

# Var vs Val:

var is like general variable and it's known as a mutable variable in kotlin and can be assigned multiple times.
val is like Final variable and it's known as immutable in kotlin and can be initialized only single time.

```kotlin
var c: Byte = 123
println(c)
c = 113
println(c)
```
Expected Output:
```
123
113
```
Same way:

```kotlin
val d: Long = 1234567
println(d)
d = 765467
println(d)
```
Expected Output:
```
Val cannot be reassigned
```
# Unsigned Integers
Kotlin provieds following types of unsigned integers

- ```UByte``` : an unsigned 8-bit integer ranges from 0 to 255.
- ```UShort```: an unsigned 16-bit integer ranges from o to 65535.
- ```UInt```: an unsigned 32-bit integer, ranges from 0 to 2<sup>32</sup>-1
- ```ULong```: an unsigned 64-bit integer, ranges from 0 to 2<sup>64</sup> -1

Unsigned types support most of the operations of their signed counterparts.
```kotlin
fun main(){
    val a:UByte =12u
    val b:UShort = 234u
    val c:UInt = 2554u
    val d:ULong = 12345657545u
	println(a)
    println(b)
    println(c)
    println(d)
}
```
Output:
```
12
234
2554
12345657545
```
If you try to pass the signed number to unsigned variable it throws an exception:
```kotlin
fun main(){
    val c:UInt = -2554u
    println(c)
}
```
The output would looks like this:
```
Unresolved reference. None of the following candidates is applicable because of receiver type mismatch: public inline operator fun BigDecimal.unaryMinus(): BigDecimal defined in kotlin public inline operator fun BigInteger.unaryMinus(): BigInteger defined in kotlin
```

Type cast from unsigned to signed and back to unsigned:
```kotlin
fun main(){
    val c:UInt = 2554u
    val d:Int = c.toInt()
    val e:UInt = c.toUInt()
    println(d)
    println(e)
}
``` 
Output:
```
2554
2554
```
Type cast from signed to unsigned to signed:
```kotlin
fun main(){
    val c:Int = -2554
    val d:UInt = c.toUInt()
    val e:Int = c.toInt()
    println(d)
    println(e)
}
```
Output:
```
4294964742
-2554
```

# Floating point data types


| Type    | bits    | Notes     |
|---------|---------|-----------|
| Double  | 64      | 16 - 17 significant digits |
| Float   | 32      | 6 - 7 significant digits   |

```kotlin
val d: Double = 123.45678
println(d)
```
output: ```123.45678```
```kotlin
val f: Float = 123.45
println(f)
```
output: ```123.45```
# Literal Constants
There are the following kinds of literal constants for integral values:

- Decimals: ```123```
- Longs are tagged by a capital L: ```123L```
- Hexadecimals: ```0x0F```
- Binaries: ```0b00001011```
Kotlin also supports a conventional notation for floating-point numbers:

- Doubles by default: ```123.5```, ```123.5e10```

- Floats are tagged by f or F: ```123.5f```

You can use underscores to make number constants more readable:
```
val oneMillion = 1_000_000
val creditCardNumber = 1234_5678_9012_3456L
val socialSecurityNumber = 999_99_9999L
val hexBytes = 0xFF_EC_DE_5E
val bytes = 0b11010010_01101001_10010100_10010010
```
# Boolean
| Type    | bits    | Notes     |
|---------|---------|-----------|
| Boolean | 8       | True or false. Operations include: ```||``` - lazy disjunction, ```&& -``` lazy conjunction, ! - negation |
```kotlin
val myTrue: Boolean = true
val myFalse: Boolean = false
println(myTrue || myFalse)
println(myTrue && myFalse)
println(!myTrue)
```
output:
```
true
false
false
```
# Characters
Characters are represented by the type ```Char```. Character literals go in single quotes: ```'1'```.

Special characters start from an escaping backslash ```\```. The following escape sequences are supported: ```\t```, ```\b```, ```\n```, ```\r```, ```\```, ```\"```, ```\\``` and ```\$```.

To encode any other character, use the Unicode escape sequence syntax: ```\uFF00```.
```kotlin
val aChar: Char = 'a'

println(aChar)
println('\n') //prints an extra newline character
println('\uFF00')
```
output:
```
a


＀
```
# Strings
- Strings are any sequence of characters enclosed by double quotes.
```kotlin
val s1: String = "Hello World"
println(s1)
```
Output: Hello World

- String literals can contain escape characters.
```kotlin
val s2: String = "Hello World\n"
println(s1)
```
Output: Hello World

- Or any arbitrary text delimited by a triple quote ```(""")```
```kotlin
val s3: String = """
       
        Arbitary text
"""
println(s3)
```
Output:
```

Arbitary text

```
## String concatenation
```kotlin
val cats = 3
val dogs = 5

"I have $cats cats"+" and $dogs dogs"
```
Output: ```I have 3 cats and 5 dogs```

## String templates
- A template expression starts with a dollar sign ($) and can be a simple value:
```kotlin
val f = 12
println("f = $f")
```
Output: ```f = 12```
```kotlin
val s = "androidwithkotlin.xyz"
println("$s.length is ${s.length}")
```
Output: ```androidwithkotlin.xyz.length is 21 ```

## String template expressions

```kotlin
val books = 12
val pens = 3

"I have ${books + pens} items with me."
```
Output: ```I have 15 items with me.```


# Type checking and Type Casting

```kotlin
val b: Byte = 1 
val i: Int = b //Gives you error
val i1: Int = b.toInt()
```

| Method    | to type   |
|-----------|-----------|
| ```toByte()```| Byte  |
|  ```toInt()```| Int   |
| ```toShort()```| Short|
| ```toLong()``` | Long |
|```toFloat()``` | Float |
| ```toDouble()```| Double |
| ```toChar()``` | Char |

```
val l = 1L + 3 // Long + Int => Long
```
 
 # Null Safety
 
 - In kotlin, variables cannot be null by default.
 - You can explicitly assiagn a variable to null using the safe call operator.
 - Allow null-pointer exceptions using the !! operator.
 - You can test for null using the elvis (?:) operator.
 
 ### Variables cannot be null
 
 - In kotlin, ```null``` variables are not allowed by default.
 
 ```kotlin
var numberOfColors: Int = null
```
 
 Output: ```error: null can not be a value of a non-null value```
 
 # Safe call operator
 
 The safe call operator (?), after the type indicates that a variable can be ```null```.
 
Declare an ```Int?``` as nullable.

```kotlin
var numberOfColors: Int?= null
```

NOTE: In general, do not set a variable to null as it may have unwanted consequences.

## Testing for null

Check whether the ```numberOfColors``` variable is not ```null```. Then decrement that variable.

```kotlin
var numberOfColors = 6
if (numberOfColors != null) {
    numberOfCOlors = numberOfColors.desc()   
}
```

Now we can see the kotlin way of writing it, using the safe call operator.

```kotlin
var numberOfColors = 6
numberOfColors = numberOfColors?.desc()
```
# The !! Operator

We use the ```!!``` operator when we sure variable won't null. Use ```!!``` to force the variable into non-null type. Then we call methods/properties on it. 

```kotlin
val len = s!!.length
```

The above mentioned statement will throw null point exception if s is null.

Warning: Because ```!!``` will throws an exception, it should only be used when it would be exceptional to hold null value.

# Elvis operator

Chain null tests with the ?: operator.
```kotlin
numberOfBooks = numberOfBooks?.desc()?:0
```

The ?: operator is sometimes called the "Elvis operator," because it's like a smiley on its side with a pompadour hairstyle, like Elvis Presley styled his hair.

Medium article on kotlin basic data types: [https://medium.com/@joshuaudayagiri/introduction-to-kotlin-data-types-6de7bc4f70d4](https://medium.com/@joshuaudayagiri/introduction-to-kotlin-data-types-6de7bc4f70d4)