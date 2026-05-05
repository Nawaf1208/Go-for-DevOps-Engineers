# Go-for-DevOps-Engineers

![Go](https://img.shields.io/badge/go-%2300ADD8.svg?style=for-the-badge&logo=go&logoColor=white)

![](Go.png)

## Go 101

<details>
<summary><b><i>1.What are some characteristics of the Go programming language?</i></b>
</summary>

$\color{green}{\text{Answer}}$

- Strong and static typing - the type of the variables can't be changed over time and they have to be defined at compile time
- Simplicity
- Fast compile times
- Built-in concurrency
- Garbage collected
- Platform independent
- Compile to standalone binary - anything you need to run your app will be compiled into one binary. Very useful for version management in run-time.

</details>

<details>
<summary><b><i>2.True or False? Go is a compiled, statically typed language</i></b>
</summary>

$\color{green}{\text{Answer}}$

True

</details>

<details>
<summary><b><i>3.Why some functions and packages in Go begin with a Capital letter?</i></b>
</summary>

$\color{green}{\text{Answer}}$

Any exported variable, function, ... begins with a capital letter. In fact when using a package, you can use only the things the package exports for you and others to use.

</details>

## Variables & Data Types

<details>
<summary><b><i>4.Demonstrate short and regular variable declaration</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
  package main

  import "fmt"

  func main() {
  	x := 2
  	var y int = 2

  	fmt.Printf("x: %v. y: %v", x, y)
  }
```

</details>

<details>
<summary><b><i>5.True or False?</i></b></summary>

$\color{green}{\text{Answer}}$

- <b><i>In Go we can redeclare variables</i></b> -> False
- <b><i>Once a variable declared, we must use it</i></b> -> True

</details>

<details>
<summary><b><i>6.What is the result of the following program?</i></b>
	
```Go
package main

import "fmt"

func main() {
	var userName
	userName = "user"
	fmt.Println(userName)
}
```
</summary>

$\color{green}{\text{Answer}}$

- Error. The type userName is not defined. It has to be declared or the value assignment should happen at declaration.

- So both `var userName = user` and `var userName string` are valid.

</details>

<details>
<summary><b><i>6.What is the difference between `var x int = 2` and `x := 2`?</i></b></summary>

$\color{green}{\text{Answer}}$

- The result is the same, a variable with the value 2.

- With `var x int = 2` we are setting the variable type to integer, while with `x := 2` we are letting Go figure out by itself the type. The result is the same, both styles can't be used in every situation. For example, short declaration can't be used outside of a function.

</details>

<details>
<summary><b><i>7.What would be the result of executing the following code:</i></b>

```Go
package main

import "fmt"

x := 2

func main() {
	x = 3
	fmt.Println(x)
}
```

</summary>

$\color{green}{\text{Answer}}$

- It will fail with `expected declaration, found x` as outside of a function, every statement should start with a keyword (and short variable declarations won't work).

</details>

<details>
<summary><b><i>8.Demonstrate a block of variable declarations (at least 3 variables)</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
package main

import "fmt"

var (
	x bool = false
	y int = 0
	z string = "false"
)

func main() {
	fmt.Printf("The type of x: %T. The value of x: %v\n", x, x)
	fmt.Printf("The type of y: %T. The value of y: %v\n", y, y)
  	fmt.Printf("The type of z: %T. The value of z: %v\n", y, y)
}

```

</details>

<details>
<summary><b><i>9.What are package level variables? What would be the reason to use them?</i></b></summary>

$\color{green}{\text{Answer}}$

- Package level variables are variables that defined at the package level instead of a specific function (like main for example).

- If you have multiple functions in your package that use the same variables, it might make these variables available to the functions by defining them at the package level. This can be in the same file or any file under the same package. For example:

```Go
package main

var packageLevelVar int = 0 

func main() {
	nonPackageLevelVar := 0
}
```

</details>

## Conversions

<details>
<summary><b><i>10.What is the problem with the following block of code? How to fix it?
	
```Go
func main() {
	var x float32 = 13.5
	var y int
	y = x
}
```
</i></b></summary>

$\color{green}{\text{Answer}}$

- Go (Golang) does not support implicit type conversion

</details>

<details>
<summary><b><i>11.Demonstrate type conversion

```Go
package main`_**

import "fmt"

func main() {
	var x int = 2
	fmt.Println(x)
  	var y float32 = float32(x)
  	fmt.Println(y)
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

- In Go (Golang), type conversion is the process of converting a value of one data type into another.

</details>

<details>
<summary><b><i>12.The following block of code tries to convert the integer 101 to a string but instead we get "e". Why is that? How to fix it?

```Go
package main

import "fmt"

func main() {
	var x int = 101
  	var y string
  	y = string(x)
  	fmt.Println(y)
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

- It looks what unicode value is set at 101 and uses it for converting the integer to a string. If you want to get "101" you should use the package "strconv" and replace `y = string(x)` with `y = strconv.Itoa(x)`

</details>

## Integers

<details>
<summary><b><i>13.What is the result of the following program?

```Go
package main
 
import "fmt"

func main() {
	var x uint
	x = -3
  	fmt.Println(x)
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

- Error. When `x` is declared as `uint` it means you can't put any negative values. But because we did put a negative value (`-3`) it will fail to compile it.

</details>

<details>
<summary><b><i>14.How to print a random integer between 0 and 10?</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
package main

import (
	"fmt"
  	"math/rand"
)

func main() {
	fmt.Println("A random integer:", rand.Intn(10))
}
```

</details>

## Constants

<details>
<summary><b><i>15.Demonstrate decelaration of constants in the following forms:

- Single constant
- Multiple constants in one block

</i></b></summary>

$\color{green}{\text{Answer}}$

- ### Single constant
```Go
const x int = 2732
```

- ### Multiple constants in one block
```Go
const (
	y = 2017
  	z = 2022
)
```

</details>

<details>
<summary><b><i>16.What is wrong with the following code?

```Go
package main

func main() {
	var x int = 2
	var y int = 3
  	const someConst = x + y
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

- Constants in Go can only be declared using constant expressions. But `x`, `y` are variables hence, their sum is variable.
- `const initializer x + y is not a constant`

</details>

<details>
<summary><b><i>17.What will be the result of executing the following code?

```Go
package main

import "fmt"

func main() {
	const X := 2
	fmt.Print(X)
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

- It won't run. Constants cannot be declared using `:=`.

</details>

<details>
<summary><b><i>18.What will be the result of executing the following code?

```Go
package main

import "fmt"

const (
	Const1 = 1
  	Const2 = 1 < 2
  	Const3 = 1 << 10                           
)

func main() {
	fmt.Println(Const1)
  	fmt.Println(Const2)
  	fmt.Println(Const3)
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

- 1 true 1024
- The 1024 result is because we shifted a 1 bit left 10 places.

</details>

## Logical Operators

<details>
<summary><b><i>19.What is the output of the following code?

```Go
package main

import "fmt"

func main() {

x := 2017

	fmt.Println(x > 2022 && x < 3000)
  	fmt.Println(x > 2000 && x < 3000)
  	fmt.Println(x > 2000 && x&2 == 0)         
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

- false
- true
- false

</details>

<details>
<summary><b><i>20.What is the output of the following code?

```Go
package main
        
import "fmt"
        
func main() {
	x := true

	fmt.Println(x)
  	fmt.Println(!x)
  	fmt.Println(!x && x)
  	fmt.Println(!x || x)               
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

- true
- false
- false
- true

</details>

## Strings

<details>
<summary><b><i>21.Define a variable with the string value of "Hello, World"</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
var some_string := "Hello, World"
```

</details>

<details>
<summary><b><i>22.Define a variable that when printed will give this output:
	
```Go
Hello,
```
  
```Go
World
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
var some_string := "Hello,\nWorld"
```

</details>

<details>
<summary><b><i>23.How to print "Hello,\nWorld"?</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
package main

import "fmt"
        
func main() {
	some_string := Hello,\nWorld

	fmt.Println(some_string)
}
```

</details>

<details>
<summary><b><i>24.What would be the output of the following code?

```Go
package main
 
import "fmt"
 
func main() {
	some_string := "There"
                              
	fmt.Println("Hello", some_string)
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
Hello There
```

</details>

<details>
<summary><b><i>25.How to print the length of a character in Go?</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
package main                       

import "fmt"

func main() {
	str := "Hello, world!"
  	fmt.Println(len(str))
}
```

</details>

<details>
<summary><b><i>26.What would be the output of the following code? Why?
```Go
var str string = "cowabunga"
fmt.Println(str[3])`_**
```
</i></b></summary>

$\color{green}{\text{Answer}}$

97 Because it prints the ascii code of 'a' which is 97.

</details>

<details>
<summary><b><i>27.Assuming `var str string = "cowabunga"`, What would be the output of the following lines?
```Go
fmt.Println(str[3:5])
```
</i></b></summary>

$\color{green}{\text{Answer}}$

`ab`

</details>

<details>
<summary><b><i>28.How to check if a string variable contains the string "ob1"?</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
package main

import (
	"fmt"
	"strings"
)

func main() {
	str := "Hello, this is ob1 example"
  	substring := "ob1"

  	if strings.Contains(str, substring) {
		fmt.Println("String contains 'ob1'")
  	} else {
    	fmt.Println("String does not contain 'ob1'")
  	}
}
```

</details>

<details> 
<summary><b><i>29.How to turn the string "Hi There" to "hi there" with the `strings` package?</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
package main

import (
	"fmt"
  	"strings"
)

func main() {
	original := "Hi There"
  	lowercase := strings.ToLower(original)
  	fmt.Println(lowercase)
}
```

</details>

## Conditionals

<details> 
<summary><b><i>30.Define a variable with value of 5. Write a conditional to check if the value of the variable is bigger than 0 and if it is, print "It's bigger than 0!"</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
x := 5
if x > 0 {
	fmt.Print("It's bigger than  0!")
}
```

</details>

<details> 
<summary><b><i>31.Define a variable with a random value. If its value bigger than 10 print "yay!". If it's smaller than 10, print "nay!"</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
rand.Seed(time.Now().UnixNano())
var x int = rand.Intn(100)
if x > 10 {
	fmt.Print("yay!")
} else {
  	fmt.Print("nay!")
}
```

</details>

<details> 
<summary><b><i>32.What the following code does?
	
```Go
package main
  
import (
	"fmt"
  	"math/rand"
  	"time"
)

func main() {
	rand.Seed(time.Now().UnixNano())
  	if randNum := rand.Intn(100); randNum%2 == 0 {
    	fmt.Print("Bingo!")
  	} else {
    	fmt.Print(randNum)
  	}
}
```
  
</i></b></summary>

$\color{green}{\text{Answer}}$

Defines a variable with random value between 0 and 100. If the random value is even, prints "Bingo!" otherwise, prints the random value itself.

</details>

## Switch

<details> 
<summary><b><i>33.Write a switch case to check what day of the week it is. If Sunday print "Here we go". If Monday print "We have just started". For any other day print the day.</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
package main

import (
	"fmt"
  	"time"
)

func main() {

	today := time.Now().Weekday().String()

  	switch today {
  	case "Sunday":
		fmt.Println("Here we go")
  	case "Monday":
    	fmt.Println("We have just started")
  	default:
    	fmt.Println(today)
	}
}
```

</details>

## User Input

<details> 
<summary><b><i>34.Fix the following program to get an input from the user regarding his name and print it var name string</i></b>

```Go
fmt.Scan(name)
fmt.Println(name)
	fmt.Println(name)
```
</summary>

$\color{green}{\text{Answer}}$

`fmt.Scan(name)` changes to `fmt.Scan(&name)`
</details>

<details> 
<summary><b><i>35.Why when asking for user input, we have to specify &?</i></b>
</summary>

$\color{green}{\text{Answer}}$

Because we want to reference the memory address of the variable, this is where the user input will be stored.

</details>

<details> 
<summary><b><i>36.What do we print here?</i></b>
	
```Go
var age int = 3
```

</summary>

$\color{green}{\text{Answer}}$
	
```Go
fmt.Println(age)
fmt.Println(&age)
```

The value of `age` variable and then the memory location of `age` variable

</details>

## Arrays & Slices

<details> 
<summary><b><i>37.Define an array of integers of size 4 without value (no items).</i></b>
</summary>

$\color{green}{\text{Answer}}$

```Go
var x [4]int
```
	
</details>

<details>
<summary><b><i>38.Define an array of the following colors: red, green and blue.</i></b>
</summary>

$\color{green}{\text{Answer}}$

```Go
var rgb = [3]string{"red", "green", "blue"}
```
	
</details>

<details>
<summary><b><i>39.You defined the following array and printed it. What was the output? 

``` Go
var numbers = [10]int{}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
[0 0 0 0 0 0 0 0 0 0]
```

</details>

<details>
<summary><b><i>40.Define an array of integers of size 10. All the values should be zeros except first one which should be 5 and the last one which should be 100.</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
var arr = [10]int{5, 9: 100}
```

</details>

<details>
<summary><b><i>41.What would be the result of the following code?

```Go
var arr = [...]int{1, 2, 3, 4}
var anotherArr = [4]int{1, 2, 3, 4}
fmt.Println(arr == anotherArr)
```

</i></b></summary>

$\color{green}{\text{Answer}}$

The result of comparison is true.

</details>

<details>
<summary><b><i>42.Assuming there is a defined array called 
	
```Go
arr
```

Print its length.</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
fmt.Println(len(arr))
```

</details>

<details>
<summary><b><i>43.True or False? An array of type [1]int is the same type as an array of [2]int.</i></b></summary>

$\color{green}{\text{Answer}}$

False. Go treats the array size as being part of the type itself. So [1]int type != [2]int type.

</details>

<details>
<summary><b><i>44.True or False? If var x := 2, then var y [x]int is an array of size 2.</i></b></summary>

$\color{green}{\text{Answer}}$

False. It's not possible to use variable to define an array of certain size. As the size of an array is part of its type and types must be resolved at compile time, not runtime.

</details>

<details>
<summary><b><i>45.Demonstrate defining the following slices:
- without values (with nil)
- with two values
</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
var slice []
```

```Go
int var slice = []int{1, 2}
```

</details>

<details>
<summary><b><i>46.Append to a slice called b the number 7.</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
b = append(b, 7)
```

</details>

<details>
<summary><b><i>47.Given that 

```Go
var slice = []int{2, 0, 1, 7}
```

What would be the result of 

```Go
slice = append(slice, 2, 0, 2, 2)
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
[2 0 1 7 2 0 2 2]
```

</details>

<details>
<summary><b><i>48.How to compare two slices?</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
package main

import (
    "fmt"
    "reflect"
)

func main() {
    x := []int {2, 0, 1, 7}
    y := []int {2, 0, 2, 2}

    fmt.Println(reflect.DeepEqual(x, y))
}
```

</details>

<details>
<summary><b><i>49.Why in Go you need assign the value returned from append function as opposed of other programming languages like Python, where you don't need to do it?</i></b></summary>

$\color{green}{\text{Answer}}$

Because in Go when you pass a something to a function, it copies it. So when we append something to a slice it appends it to a copy of it. So in order to change the original slice, we need to assign the returned copy back into the original slice.

</details>

<details>
<summary><b><i>50.How create a slice of capacity (not size) of 20?</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
slice := make([]int, 20)
```

</details>

<details>
<summary><b><i>51.How create a slice of size 3 ad capacity of 10?</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
slice := make([]int, 3, 20)
```

</details>

<details>
<summary><b><i>52.What's the use case for defining in advance the capacity of a slice?</i></b></summary>

$\color{green}{\text{Answer}}$

It's more efficent to set the size once for a slice rather than increase its capacity every times new items added to it.

</details>

<details>
<summary><b><i>53.What's the value of slice after running the following code? Why?

```Go
slice := make([]int, 3)
slice = append(slice, 41)
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
[0 0 0 41]
```

</details>

<details>
<summary><b><i>54.True or False? When specifying the capacity of a slice, it's always best to specify a capacity that is bigger than the slice size.</i></b></summary>

$\color{green}{\text{Answer}}$

True. Otherwise it will cause compile-time error or run-time error, depends on how you defined it.

</details>

<details>
<summary><b><i>55.Given 

```Go
slice := []int{1, 2, 3, 4, 5}
```

What would be the result of the following expressions:

```Go
slice[:]
```

```Go
slice[2:]
```

```Go
slice[:1]
```

```Go
slice[2:4]
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
[1 2 3 4 5]
```

```Go
[3 4 5]
```

```Go
[1]
```

```Go
[3 4]
```

</details>

<details>
<summary><b><i>56.What's the output of the following program?

```Go
slice := []int{1, 2, 3}
anotherSlice := slice[1:]
slice[1] = 999
anotherslice[1] = 5
fmt.Println("slice:", slice)
fmt.Println("slice:", anotherSlice)
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
[10 999 3]
[999 5]
```

The expalantion is that slicing a slice isn't creating a copy of the data but rather creates another variable that shares the very same memory.

</details>

<details>
<summary><b><i>57.How to create an independant slice of a slice?</i></b></summary>

$\color{green}{\text{Answer}}$

When creating a slice of a slice, it will create variable that shares the same memory. To create a slice that is indepdant of the original slice, you can use the built-in function `copy`

```Go
slice := []int{1, 2, 3}
destSlice = make([]int, 3)
numOfElements := copy(slice, destSlice)
```

</details>

## Loops

<details>
<summary><b><i>58.Define a simple for loop with following components:
	
- variable `i` initialized to 0
- expression where the variable should be smaller than 50
- at the end of each iteration the variable value should be incremented by 1
- In the loop itself, the value of variable `i` should be added to a variable called `sum` (initialize the variable before the loop with value of 0)

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
sum := 0
for i := 0; i < 50; i++ {
    sum += i
}
```

</details>

<details>
<summary><b><i>59.Implement infinite loop.</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
for {
    fmt.Print("forever!")
}
```

</details>

<details>
<summary><b><i>60.What's the difference between the following two loops?

```Go
for {
    fmt.Print("forever!")
}
```

```Go
for true {
    fmt.Print("forever!")
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

From result perspective, there is no difference. Both are infinite loops.

</details>

## Maps

<details>
<summary><b><i>61.Define the following map variables:
- an empty map where all keys are of string type, as well as the values
- an empty map where all the keys are of string type and the values are of int type
- A map with string type keys and int array values (non empty map, populate it with data)
- Empty map with int type keys and string type values of size 100
</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
var someMap = map[string]string
```

```Go
anotherMap := map[string]int{}
```

```Go
nonEmptyMap := map[string][]int{
  "someKey": []int{1, 2, 3},
  "anotherKey": []int{4, 5, 6},
}
```

```Go
someMap := make(map[int][]string, 100)
```

</details>

<details>
<summary><b><i>62.True or False? All keys in a single map, should have the same data type.</i></b></summary>

$\color{green}{\text{Answer}}$

True. This is also true for the all the values in a single map.

</details>

<details>
<summary><b><i>63.How to check the number of key-value pairs in a map?</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
len(someMap)
```

</details>

<details>
<summary><b><i>64.True or False? To compare maps, one can use "==" this way 
	
`someMap == anotherMap` 

</i></b></summary>

$\color{green}{\text{Answer}}$

False.

</details>

<details>
<summary><b><i>65.What's the output of the following code?

```Go
someMap := map[string]int{}
someMap["x"] = 41
fmt.Println(someMap["y"])
```

</i></b></summary>

$\color{green}{\text{Answer}}$

0

</details>

<details>
<summary><b><i>66.What's the output of the following code?

```Go
someMap := map[string]int{
  "x": 41,
}
value, exists := someMap["x"]
fmt.Println(value, exists)
value, exists = someMap["y"]
fmt.Println(value, exists)
```

</i></b></summary>

$\color{green}{\text{Answer}}$

41 true 0 false

</details>

<details>
<summary><b><i>67.Remove from the following map the key-value pair of "y"

```Go
someMap := map[string]int{
  "x": 41,
  "y": 303,
  "z": 56,
}
```

$\color{green}{\text{Answer}}$

```Go
delete(someMap, "y")
```

</details>

## Functions

<details>
<summary><b><i>68.Define a function that prints "Hello World"</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
func PrintHelloWorld() {
    fmt.Println("Hello World")
}
```

</details>

<details>
<summary><b><i>69.What the following code does?

```Go
func add(x int, y int) int {
    return x + y
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

add is a function that takes two parameters (two integers) and returns their sum.

</details>

<details>
<summary><b><i>70.Which of the following functions will work just fine?

```Go
func add(x int, y int) int {
    return x + y
}
```

```Go
func add(x, y int) int {
    return x + y
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

Both. If two or more parameters share the same type, you can specify it only once.

</details>

<details>
<summary><b><i>71.True or False? A function in Go can return either zero or one values, but not more than that</i></b></summary>

$\color{green}{\text{Answer}}$

False. A fucntion in Go can return multiple values

</details>

<details>
<summary><b><i>72.Write code that will execute the following function in a valid way

```Go
func swap(x, y string) (string, string) {
    return y, x
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
x, y = swap("and roll", "rock")
fmt.Println(a, b)
```

</details>

<details>
<summary><b><i>73.What is the result of the following code?

```Go
func process(num int) (x int) {
    x = num + 10
    var z = num - x
    x = z + x
    return
}

func main() {
  fmt.Println(process(10))
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

10

</details>

## Defer

<details>
<summary><b><i>74.What will be the output of the following code? Why?

```Go
package main

import "fmt"

func main() {
    defer fmt.Println("1")

    fmt.Println("2")
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
2
1
```

2 is printed before 1 due to the defer statement. The `defer` statement defers the execution of the function (`fmt.Println("1")`) until the surrounding fucntion (which is `main()`) returns.

</details>

<details>
<summary><b><i>75.True or False? The arguments of a deferred functions are evaluated but the function itself isn't called until the surrounding function returns.</i></b></summary>

$\color{green}{\text{Answer}}$

True.

</details>

<details>
<summary><b><i>76.What will be the output of the following code? Why?

```Go
package main

import "fmt"

func main() {
    fmt.Println("100")

    for i := 0; i < 10; i++ {
      defer fmt.Println(i)
    }

    fmt.Println("200")
  }
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
100
200
9
8
7
6
5
4
3
2
1
0
```

Deferred functions are executed in a last-in-first-out order, this is why it prints it from 9 to 0 instead of from 0 to 9.

</details>

## Packages

<details>
<summary><b><i>77.How do you export a variable or a function in Go for other packages to use?</i></b></summary>

$\color{green}{\text{Answer}}$

Capitalize the first letter of what you would like to export.

</details>

<details>
<summary><b><i>78.What are different levels of scope of variables?</i></b></summary>

$\color{green}{\text{Answer}}$

- Local
- Package
- Global

</details>

## Generics

<details>
<summary><b><i>79.How can you define your custom generic type in Golang?</i></b></summary>

$\color{green}{\text{Answer}}$

By creating an interface.

```Go
package main

type C interface {
	int | int32 | string
}
```

</details>

<details>
<summary><b><i>80.Why can we send both int and string to following function?

```Go
package main

import "fmt"

type C interface {
  int | int32 | string
}

func show[T C](input T) {
	fmt.Println(input)
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

Because we created show function as a generic function. Therefore it can get types that we have in C.

</details>

<details>
<summary><b><i>81.Change this function to accept any type in Golang.

```Go
package main

import "log"

func do_log(input string) {
	log.Print(input)
}
```

</i></b></summary>

$\color{green}{\text{Answer}}$

```Go
Use any keyword.

package main

import "log"

func do_log(input any) {
	log.Print(input)
}
```

</details>
