---
layout: single
title:  "Perform basic string formatting in C#."
date:   2022-05-20 14:00:00 +0000
categories: C#
permalink: perform-basic-string-formatting
tags:
  - C#
  - Take your first steps with C#
toc: true
---

We use character escape sequences to format literal strings of text to include special characters including tabs and line feeds -- even unicode escape charecters!

We'll learn how to concatenate two strings together, and will use string interpolation to create a literal string template with replaceable parts.

# Character escape sequences

An **character escape sequence** is a special instruction to the runtime that you want to insert a special character that will affect the output of your string.

C# escape character sequences begin with a backslash `\`and then include another character. 

## New line and tab.

Examples are `\n` sequence will add a new line, and a `\t`sequence will add a tab.

```csharp
Console.WriteLine("Hello\nWorld!");
Console.WriteLine("Hello\tWorld!");
```

Output:

```
Hello
World!
Hello   World!
```

## Double-quotation.

If you need to insert a double-quotation mark in a literal string and you don't use the escape character sequence, you will confuse the compiler causing it to terminate the string prematurely.

```csharp
Console.WriteLine("Hello \"World\"!");
```

Output:

```
Hello "World"!
```

## Backslashes.

If you want to use backslashes in your strings you need to use a double backslash `\\`.

```csharp
Console.WriteLine("c:\\source\\repos");
```

Output: 

```
c:\source\repos
```

## Example using new line, double-quotation and tab together.

Code example using all forementioned escape character sequences :

```csharp
Console.WriteLine("Generating invoices for customer \"ABC Corp\" ...\n");
Console.WriteLine("Invoice: 1021\t\tComplete!");
Console.WriteLine("Invoice: 1022\t\tComplete!");
Console.WriteLine("\nOutput Directory:\t");
```

Output: 

```
Generating invoices for customer "ABC Corp" ...

Invoice: 1021		Complete!
Invoice: 1022		Complete!

Output Directory:
```

## Verbatim string literal

A verbatim string literal will keep all whitespace and characters without the need to escape the backslash. To create a verbatim string, use the `@` directive before the literal string.

```csharp
Console.WriteLine(@"   c:\source\repos   
      (this is where your code goes)");
```

Output: 

```
c:\source\repos   
      (this is where your code goes)
```

## Unicode escape characters

You can add encoded characters in literal strings using the `\u` escape sequence, followed by a four-character Unicode (UFT-16).

```csharp
// Kon'nichiwa World
Console.WriteLine("\u3053\u3093\u306B\u3061\u306F World!");
```

Output: 

```
こんにちは World!
```

# String Concatenation

String concatenation is when you combine two or more values into a new value. Unlike addition, the second value is appended to the end of the first value, and so on.

To concatenate two strings together, you use the *string concatenation operator*, which is the plus `+` symbol.

```csharp
string firstName = "Bob";
string message = "Hello " + firstName;
Console.WriteLine(message);
```

Output: 

```
Hello Bob
```

You can perform multiple concatenation operations in the same line of code.

```csharp
string firstName = "Bob";
string greeting = "Hello";
string message = greeting + " " + firstName + "!";
Console.WriteLine(message);
```

Output:

```
Hello Bob!
```

Avoid using an intermediate variable unless you need to.

```csharp
string firstName = "Bob";
string greeting = "Hello";
Console.WriteLine(greeting + " " + firstName + "!");
```

Output:

```csharp
Hello Bob!
```

# String interpolation

String interpolation combines multiple values into a single literal string by using a “template” and one or more *interpolation expressions*. 

An **interpolation expression** is a variable surrounded by an opening and closing curly brace symbol `{}`.

Instead of writing this:

```csharp
string message = greeting + " " + firstName + "!";
```

You can write this:

```csharp
string message = $"{greeting} {firstName}!";
```

Using string interpolation uses fewer keystrokes and helps to write more concise complex operations. Many people find string interpolation syntax cleaner and easier to read.

To interpolate two strings together, you create a literal string and prefix the string with a `$` symbol. The literal string should contain at least one set of curly braces `{}` and inside of those you use the name of a variable.

```csharp
string firstName = "Bob";
string message = $"Hello {firstName}!";
Console.WriteLine(message);
```

Output: 

```
Hello Bob!
```

You can perform several interpolation operations in the same line of code.

```csharp
string firstName = "Bob";
string greeting = "Hello";
string message = $"{greeting} {firstName}!";
Console.WriteLine(message);
```

Output: 

```
Hello Bob!
```

Avoid intermediate variables by adding the interpolation directly in the `Console.WriteLine();` method.

```csharp
string firstName = "Bob";
string greeting = "Hello";
Console.WriteLine($"{greeting} {firstName}!");
```

Output: 

```
Hello Bob!
```

## Combine verbatim literals and string interpolation.

You can use a verbatim literal with string interpolation by prefixing the `@` symbol with the string interpolation `$` symbol.

```csharp
string projectName = "First-Project";
Console.WriteLine($@"C:\Output\{projectName}\Data");
```

Output:
```
C:\Output\First-Project\Data
```