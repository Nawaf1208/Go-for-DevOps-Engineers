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

**_25.How to print the length of a character in Go?_**

- `package main`                         

- `import "fmt"`

- `func main() {`
  - `str := "Hello, world!"`
  - `fmt.Println(len(str))`
- `}`

**_26.What would be the output of the following code? Why?_**
- **_`var str string = "cowabunga"`_**
- **_`fmt.Println(str[3])`_**

- 97 Because it prints the ascii code of 'a' which is 97.

**_27.Assuming `var str string = "cowabunga"`, What would be the output of the following lines?_**
- **_`fmt.Println(str[3:5])`_**

- 'ab'

**_28.How to check if a string variable contains the string "ob1"?_**

- `package main`

- `import (`
  - `"fmt"`
  - `"strings"`
- `)`

- `func main() {`
  - `str := "Hello, this is ob1 example"`
  - `substring := "ob1"`

  - `if strings.Contains(str, substring) {`
    - `fmt.Println("String contains 'ob1'")`
  - `} else {`
    - `fmt.Println("String does not contain 'ob1'")`
  - `}`
- `}`

**_29.How to turn the string "Hi There" to "hi there" with the `strings` package?_**

- `package main`

- `import (`
  - `"fmt"`
  - `"strings"`
- `)`

- `func main() {`
  - `original := "Hi There"`
  - `lowercase := strings.ToLower(original)`
  - `fmt.Println(lowercase)`
- `}`

## Conditionals

**_30.Define a variable with value of 5. Write a conditional to check if the value of the variable is bigger than 0 and if it is, print "It's bigger than 0!"_**

- `x := 5`
- `if x > 0 {`
  - `fmt.Print("It's bigger than  0!")`
- `}`

**_31.Define a variable with a random value. If its value bigger than 10 print "yay!". If it's smaller than 10, print "nay!"_**

- `rand.Seed(time.Now().UnixNano())`
- `var x int = rand.Intn(100)`
- `if x > 10 {`
  - `fmt.Print("yay!")`
- `} else {`
  - fmt.Print("nay!")`
- `}`

**_32.What the following code does?_**
- **_`package main`_**
  
- **_`import (`_**
  - **_`"fmt"`_**
  - **_`"math/rand"`_**
  - **_`"time"`_**
- **_`)`_**

- **_`func main() {`_**
  - **_`rand.Seed(time.Now().UnixNano())`_**
  - **_`if randNum := rand.Intn(100); randNum%2 == 0 {`_**
    - **_`fmt.Print("Bingo!")`_**
  - **_`} else {`_**
    - **_`fmt.Print(randNum)`_**
  - **_`}`_**       
- **_`}`_**

- Defines a variable with random value between 0 and 100. If the random value is even, prints "Bingo!" otherwise, prints the random value itself.

## Switch

**_33.Write a switch case to check what day of the week it is. If Sunday print "Here we go". If Monday print "We have just started". For any other day print the day._**

- `package main`

- `import (`
  - `"fmt"`
  - `"time"`
- `)`

- `func main() {`

  - `today := time.Now().Weekday().String()`

  - `switch today {`
  - `case "Sunday":`
    - `fmt.Println("Here we go")`
  - `case "Monday":`
    - `fmt.Println("We have just started")`
  - `default:`
    - `fmt.Println(today)`
	- `}`
- `}`

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
