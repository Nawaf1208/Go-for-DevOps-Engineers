# Go-for-DevOps-Engineers

![Go](https://img.shields.io/badge/go-%2300ADD8.svg?style=for-the-badge&logo=go&logoColor=white)

![](Go.png)

## Go 101

**_1.What are some characteristics of the Go programming language?_**

- Strong and static typing - the type of the variables can't be changed over time and they have to be defined at compile time
- Simplicity
- Fast compile times
- Built-in concurrency
- Garbage collected
- Platform independent
- Compile to standalone binary - anything you need to run your app will be compiled into one binary. Very useful for version management in run-time.

**_2.True or False? Go is a compiled, statically typed language_**

- True

**_3.Why some functions and packages in Go begin with a Capital letter?_**

- Any exported variable, function, ... begins with a capital letter. In fact when using a package, you can use only the things the package exports for you and others to use.

## Variables & Data Types

**_4.Demonstrate short and regular variable declaration_**

- `package main`

- `import "fmt"`

- `func main() {`
  - `x := 2`
  - `var y int = 2`

  - `fmt.Printf("x: %v. y: %v", x, y)`
- `}`

**_5.True or False?_**
- **_In Go we can redeclare variables_** -> False
- **_Once a variable declared, we must use it_** -> True

**_6.What is the result of the following program?_**
- **_`package main`_**

- **_`import "fmt"`_**

- **_`func main() {`_**
  - **_`var userName`_**
  - **_`userName = "user"`_**
  - **_`fmt.Println(userName)`_**
- **_`}`_**

- Error. The type userName is not defined. It has to be declared or the value assignment should happen at declaration.

- So both `var userName = user` and `var userName string` are valid.

**_6.What is the difference between `var x int = 2` and `x := 2`?_**

- The result is the same, a variable with the value 2.

- With `var x int = 2` we are setting the variable type to integer, while with `x := 2` we are letting Go figure out by itself the type. The result is the same, both styles can't be used in every situation. For example, short declaration can't be used outside of a function.

**_7.What would be the result of executing the following code:_**
- **_`package main`_**

- **_`import "fmt"`_**

- **_`x := 2`_**

- **_`func main() {`_**
  - **_`x = 3`_**
  - **_`fmt.Println(x)`_**
- **_`}`_**

- It will fail with `expected declaration, found x` as outside of a function, every statement should start with a keyword (and short variable declarations won't work).

**_8.Demonstrate a block of variable declarations (at least 3 variables)_**

- **_`package main`_**

- **_`import "fmt"`_**

- **_`var (`_**
  - **_`x bool   = false`_**
  - **_`y int    = 0`_**
  - **_`z string = "false"`_**
- **_`)`_**

- **_`func main() {`_**
  - **_`fmt.Printf("The type of x: %T. The value of x: %v\n", x, x)`_**
  - **_`fmt.Printf("The type of y: %T. The value of y: %v\n", y, y)`_**
  - **_`fmt.Printf("The type of z: %T. The value of z: %v\n", y, y)`_**
- **_`}`_**

**_9.What are package level variables? What would be the reason to use them?_**

- Package level variables are variables that defined at the package level instead of a specific function (like main for example).

- If you have multiple functions in your package that use the same variables, it might make these variables available to the functions by defining them at the package level. This can be in the same file or any file under the same package. For example:

- **_`package main`_**

- **_`var packageLevelVar int = 0`_** 

- **_`func main() {`_**
  - **_`nonPackageLevelVar := 0`_**
- **_`}`_**

## Conversions

**_10.What is the problem with the following block of code? How to fix it?_**
- **_`func main() {`_**
  - **_`var x float32 = 13.5`_**
  - **_`var y int`_**
  - **_`y = x`_**
- **_`}`_**

- Go (Golang) does not support implicit type conversion

**_11.Demonstrate type conversion_**

- **_`package main`_**

- **_`import "fmt"`_**

- **_`func main() {`_**
  - **_`var x int = 2`_**
  - **_`fmt.Println(x)`_**
  - **_`var y float32 = float32(x)`_**
  - **_`fmt.Println(y)`_**
- **_`}`_**

- In Go (Golang), type conversion is the process of converting a value of one data type into another.
  
**_12.The following block of code tries to convert the integer 101 to a string but instead we get "e". Why is that? How to fix it?_**

- **_`package main`_**

- **_`import "fmt"`_**

- **_`func main() {`_**
  - **_`var x int = 101`_**
  - **_`var y string`_**
  - **_`y = string(x)`_**
  - **_`fmt.Println(y)`_**
- **_`}`_**

- It looks what unicode value is set at 101 and uses it for converting the integer to a string. If you want to get "101" you should use the package "strconv" and replace `y = string(x)` with `y = strconv.Itoa(x)`

## Integers

**_13.What is the result of the following program?_**

- **_`package main`_**
 
- **_`import "fmt"`_**
 
- **_`func main() {`_**
  - **_`var x uint`_**
  - **_`x = -3`_**
  - **_`fmt.Println(x)`_**
- **_`}`_**

- Error. When `x` is declared as `uint` it means you can't put any negative values. But because we did put a negative value (`-3`) it will fail to compile it.

**_14.How to print a random integer between 0 and 10?_**

- `package main`

- `import (`
  - `"fmt"`
  - `"math/rand"`
- `)`

- `func main() {`
  - `fmt.Println("A random integer:", rand.Intn(10))`
- `}`

## Constants

**_15.Demonstrate decelaration of constants in the following forms:_**
- **_Single constant_**
- **_Multiple constants in one block_**

- ### Single constant
- `const x int = 2732`

- ### Multiple constants in one block
- `const (`
  - `y = 2017`
  - `z = 2022`
- `)`

**_16.What is wrong with the following code?:_**
- **_`package main`_**

- **_`func main() {`_**
  - **_`var x int = 2`_**
  - **_`var y int = 3`_**
  - **_`const someConst = x + y`_**
- **_`}`_**

- Constants in Go can only be declared using constant expressions. But `x`, `y` are variables hence, their sum is variable.
- `const initializer x + y is not a constant`

**_17.What will be the result of executing the following code?_**
- **_`package main`_**

- **_`import "fmt"`_**

- **_`func main() {`_**
  - **_`const X := 2`_**
  - **_`fmt.Print(X)`_**
- **_`}`_**

- It won't run. Constants cannot be declared using `:=`.

**_18.What will be the result of executing the following code?_**

- **_`package main`_**

- **_`import "fmt"`_**

- **_`const (`_**
  - **_`Const1 = 1`_**
  - **_`Const2 = 1 < 2`_**
  - **_`Const3 = 1 << 10`_**                            
- **_`)`_**

- **_`func main() {`_**
  - **_`fmt.Println(Const1)`_**
  - **_`fmt.Println(Const2)`_**
  - **_`fmt.Println(Const3)`_**
- **_`}`_**

- 1 true 1024
- The 1024 result is because we shifted a 1 bit left 10 places.

## Logical Operators

**_19.What is the output of the following code?_**

- **_`package main`_**

- **_`import "fmt"`_**

- **_`func main() {`_**
  - **_`x := 2017`_**

  - **_`fmt.Println(x > 2022 && x < 3000)`_**
  - **_`fmt.Println(x > 2000 && x < 3000)`_**
  - **_`fmt.Println(x > 2000 && x&2 == 0)`_**          
- **_`}`_**

- false
- true
- false

**_20.What is the output of the following code?_**

- **_`package main`_**
        
- **_`import "fmt"`_**
        
- **_`func main() {`_**
  - **_`x := true`_**

  - **_`fmt.Println(x)`_**
  - **_`fmt.Println(!x)`_**
  - **_`fmt.Println(!x && x)`_**
  - **_`fmt.Println(!x || x)`_**               
- **_`}`_**

- true
- false
- false
- true

## Strings

**_21.Define a variable with the string value of "Hello, World"_**

- `var some_string := "Hello, World"`

**_22.Define a variable that when printed will give this output:_**
- **_`Hello,`_**
- **_`World`_**

- `var some_string := "Hello,\nWorld"`

**_23.How to print "Hello,\nWorld"?_**

- `package main`

- `import "fmt"`
        
- `func main() {`
  - `some_string := Hello,\nWorld`

  - `fmt.Println(some_string)`
- `}`

**_24.What would be the output of the following code?_**
- **_`package main
 
- **_`import "fmt"`_**
 
- **_`func main() {`_**
  - **_`some_string := "There"`_**
                              
  - **_`fmt.Println("Hello", some_string)`_**
- **_`}`_**

- Hello There

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

**_34.Fix the following program to get an input from the user regarding his name and print it
var name string_**

- **_`fmt.Scan(name)`_**

- **_`fmt.Println(name)`_**

- - **_`fmt.Println(name)`_**
 
- `fmt.Scan(name)` changes to `fmt.Scan(&name)`

**_35.Why when asking for user input, we have to specify &?_**

- Because we want to reference the memory address of the variable, this is where the user input will be stored.

**_36.What do we print here?_**
- **_`var age int = 3`_**

- **_`fmt.Println(age)`_**
- **_`fmt.Println(&age)`_**

- The value of `age` variable and then the memory location of `age` variable
