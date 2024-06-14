# GoLang Learning
Here are some resources to get you started with learning GoLang:

## Online Courses:
Go: The complete developers guide(GoLang): https://www.udemy.com/course/go-the-complete-developers-guide/
(Consider enrolling in a free trial before purchasing)
## Websites:
Go by example: https://gobyexample.com/
## Books:
The Go Programming language by Alan A. A. Donovan and Brian Kernighan
## Practice Platforms:
GoPhercises: https://gophercises.com/
## Additional Course (Optional):
Building Modern Web Applications with Go: https://www.udemy.com/course/building-modern-web-applications-with-go/

## Should you learn a framework?

Whether or not you need to learn a framework when starting with Go depends on your goals:

#### Learning the Basics:
If you're just getting started with Go, it might be beneficial to focus on learning the core language concepts and the Go standard library first. This will give you a solid foundation before diving into frameworks.
#### Building Simple Applications:
For simple command-line tools or small applications, you might not necessarily need a framework. The Go standard library can provide most of the functionality you'll need.
#### Building Web Applications: 
If you're interested in building web applications with Go, then learning a web framework like Gin or Echo can be very helpful. These frameworks will streamline the development process and provide essential features for web development.

After Basics.
Following this : https://www.youtube.com/playlist?list=PL5dTjWUk_cPYztKD7WxVFluHvpBNM28N9

<details>
<summary>Import Functionality</summary>

This lesson introduces a basic component of Go program, i.e., packages.

We'll cover the following:

- Packages
- Package dependencies
- Import keyword
- Visibility
- Visibility rule

## Packages

A library, module, or namespace in any other language is called a package. Packages are a way to structure code. A program is constructed as a package which may use facilities from other packages. A package is often abbreviated as ‘pkg’.

Every Go file belongs to only one package whereas one package can comprise many different Go files. Hence, the filename(s) and the package name are generally not the same. The package to which the code-file belongs must be indicated on the first line. A package name is written in lowercase letters. For example, if your code-file belongs to a package called main, do the following:

```go
package main
```

A standalone executable belongs to main. Each Go application contains one main.

An application can consist of different packages. But even if you use only package main, you don’t have to stuff all code in 1 big file. You can make a number of smaller files, each having package main as the 1st line of code. If you compile a source file with a package name other than main, e.g., pack1, the object file is stored in pack1.a.

## Package dependencies

To build a program, the packages, and the files within them must be compiled in the correct order. Package dependencies determine the order in which to build the packages. Within a package, the source files must all be compiled together. The package is compiled as a unit, and by convention, each directory contains one package. If a package is changed and recompiled, all the client programs that use this package must be recompiled too!

## Import keyword

A Go program is created by linking set of packages together, with the import keyword. For example, if you want to import a package say fmt, then you do:

```go
package main
import "fmt"
```

`import "fmt"` tells Go that this program needs functions, or other elements from the package fmt, which implements a functionality for formatted IO. The package names are enclosed within " "(double quotes).

Import loads the public declarations from the compiled package; it does not insert the source code. If multiple packages are needed, they can each be imported by a separate statement. For example, if you want to import two packages, fmt and os in one code file, there are some following ways to do so:

```go
import "fmt"
import "os"
```

or you can do:

```go
import "fmt"; import "os"
```

Go has provided us with a shorter and more elegant way of importing multiple packages known as factoring the keyword. It is stated as:

```go
import (
  "fmt"
  "os"
)
```

Factoring means calling a keyword once on multiple instances. You may have noticed that we imported two packages using a single import keyword. It is also applicable to keywords like const, var, and type.

## Visibility

Packages contain all other code objects apart from the blank identifier (_). Also, identifiers of code-objects in a package have to be unique which means that there can be no naming conflicts. However, the same identifier can be used in different packages. The package name qualifies a package to be different.

## Visibility rule

Packages expose their code objects to code outside of the package according to the following rule enforced by the compiler:

When the identifier (of a constant, variable, type, function, struct field, …) starts with an uppercase letter, like, Group1, then the ‘object’ with this identifier is visible in code outside the package (thus available to client-programs, or ‘importers’ of the package), and it is said to be exported (like public identifiers/variables in OO languages). Identifiers that start with a lowercase letter are not visible outside the package, but they are visible and usable in the whole package (like private identifiers/variables).

Note: Capital letters can come from the entire Unicode-range, like Greek; not only ASCII letters are allowed.

Importing a package gives access only to the exported objects in that package. Suppose we have an instance of a variable or a function called Object (starts with O so it is exported) in a package pack1. When pack1 is imported in the current package, Object can be called with the usual dot-notation from OO-languages:

```go
pack1.Object
```

Packages also serve as namespaces and can help us avoid name-conflicts. For example, variables with the same name in two packages are differentiated by their package name, like pack1.Object and pack2.Object.

A package can also be given another name called an alias. If you name a package then its alias will be used throughout the code, rather than its original name. For example:

```go
import fm "fmt"
```

Now in the code, whenever you want to use fmt, use its alias:fm (not fmt).

Note: Go has a motto known as “No unnecessary code!”. So importing a package which is not used in the rest of the code is a build-error.

</details>



<details>
<summary>Overview of Functions</summary>

This lesson explains how to write a simple function in Go.

We'll cover the following:

- Functions
- Hello World 🌍
- Comments
- Naming things in Go

## Functions

The simplest function declaration has the format:

```go
func functionName()
```

Between the mandatory parentheses ( ) no, one, or more parameters (separated by ,) can be given as input to the function. After the name of each parameter variable must come its type.

The main function as a starting point is required (usually the first function), otherwise the build-error: undefined: main.main occurs. The main function has no parameters and no return type (in contrary to the C-family) otherwise, you get the build-error: func main must have no arguments and no return values. When the program executes, after initializations the first function called (the entry-point of the application) will be the main.main() (like in C). The program exits immediately and successfully when main.main returns.

The code or body in functions is enclosed between braces { }. The first { must be on the same line as the declaration otherwise you get the error: syntax error: unexpected semicolon or newline before { ). The last } is positioned after the function-code in the column beneath the function. The syntax is as follows:

```go
func func_Name(param1 type1, param2 type2, ...){
  ...
}
```

If the function is returning an object of type type1, we follow the syntax as:

```go
func func_Name(param1 type1, param2 type2, ...) type1 {
  ...
}
```

or:

```go
func func_Name(param1 type1, param2 type2, ...) ret1 type1 {
  ...
}
```

where ret1 is a variable of type type1 to be returned. So a general function returning multiple variables looks like:

```go
func func_Name(param1 type1, param2 type2, ...) (ret1 type1, ret2 type2, ...) {
...
}
```

Smaller functions can be written on one line like:

```go
func Sum(a, b int) int { return a + b }
```

Let’s create the main function now as an entry point.

```go
package main
import "fmt"

func main(){
}
```

## Naming things in Go

Clean, readable code and simplicity are major goals of Go development. Therefore, the names of things in Go should be short, concise, and evocative. Long names with mixed caps and underscores which are often seen e.g., in Java or Python code, sometimes hinder readability. Names should not contain an indication of the package. A method or function which returns an object is named as a noun, no Get… is needed. To change an object, use SetName. If necessary, Go uses MixedCaps or mixedCaps rather than underscores to write multiword names.

</details>
