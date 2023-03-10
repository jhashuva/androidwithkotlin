# Lists

- Lists are ordered collections of elements.
- List elements can be acessed programitically through their indices 
- Elements can occur more than once in a list.

An example of a list is a sentence: it's a group of words, their order is important, and they can repeat.

## Immutable list 
Declare a list using immutable list  using listOf()

```
val countries = listOf("India","Us","South Africa","UK")
println(countries)
```
Output: ```[India,Us,South Africa,UK]```

## Mutable list
 Lists can be changed using ```mutableListOf()```
 
```
val myList = mutableListOf("stand","hardrive","camera")
myList.remove("stand")

```
Output: ```kotlin.Boolean = true```

With a list defined with ```val```, you can't change which list the variable refers to, but you can still change the contents of the list. 

# Arrays

- Arrays store multiple items.
- Array elements can be accessed programmatically through their indices.
- Array elements are mutable.
- Array size is fixed.

## Array using ```arrayOf()```

An array of strings can be created using arrayOf()

```
val colors = arrayOf("red","green","yellow")
println(java.util.Arrays.toString(colors))
```

Output: ```[red,green,yellow]```


With an array defined with ```val```, you can't change which array the variable refers to, but you can still change the contents of the array.

## Arrays with mixed or single types

An array can contain different types

```
val mix = arrayOf("hats",2)
```

An array also contain just one type(integers in this case)

```
val numbers = intArrayOf(1,2,3)
```

## Combining arrays

Use the + operator

```
val number1 = intArrayOf(1,2,3)
val number2 = intArrayOf(4,5,6)
val combined = numbers2+numbers
println(Arrays.toString(combined))
```
Output: ```[4, 5, 6, 1, 2, 3]```



