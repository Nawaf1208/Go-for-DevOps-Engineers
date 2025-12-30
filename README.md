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
