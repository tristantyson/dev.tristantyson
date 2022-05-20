---
layout: single
title:  "Store and retrieve data using literal and variable values in C#."
date:   2022-05-20 13:00:00 +0000
categories: C#
permalink: store-and-retrieve-data
tags:
  - C#
  - Take your first steps with C#
toc: true
---
A literal value is a hard-coded value that never changes.

The string data type is used for alphanumeric words, phrases, or data for presentation. It is not used for calculation.

# Literal data types.
If you want to display a single alphanumeric character on screen, you can create a **char literal** by surrounding it in single-quotes.

```csharp
Console.WriteLine('b');
```

> If you entered `Console.WriteLine('Hello World!');` you would get an error. Using single-quotes is the *character literal* syntax so needs to only contain a single character. This command contains 12 characters so is invalid.
> 

You can display a whole number (no fractions) by using a **int literal**. An `int` literal requires no additional operators like `string` or `char`.

```csharp
Console.WriteLine(123);
```

The term *int* is short for integer.

If you want to print a number that includes a decimal place you can use a **decimal literal**.

To create a decimal literal, append the letter `m` after the number. This is called a *literal suffix*. The literal suffix tells the complier you want to work with a decimal value.

```csharp
Console.WriteLine(12.3m);
```

> You can use a lower-case `m` or upper-case `M` as the literal suffix for a decimal.
> 

If you want to print a value representing either `true` or `false`, you can use a **bool literal**.

```csharp
Console.WriteLine(true);
Console.WriteLine(false);
```

The term *bool* is short for *boolean*. Bool literals represent the idea of truth and falsehood. They're used extensively when adding decision logic to applications.

## Why emphasize data types?
Data types play a central role in C# and are a distinguishing feature of the language compared to other languages. The designers of the C# language believed *enforcing data types* would avoid common software bugs.

## Presentation vs calculation and evaluation.
If you have data that is to be used for presentation or reference purposes you should use a `string` or a `char`.

If you need to perform calculations you should use an `int` or `decimal`.

If you need to preform evaluations of logic you should use a `bool`.

# Declare variables.
A variable is a data item that may change its value during its lifetime. You use variable to store values that you intent to use later in your code. A variable is a friendly label that can be assigned to a computer memory address.

To create a variable, you must first declare the data type of the variable, then give it a name.

```csharp
string firstName;
```

In this case, we’re creating a new variable of the type `string` and the name `firstName`. This variable can only hold string values.

## Variable name rules and conventions.
- Variable names can contain alphanumeric characters and underscore characters. You cannot use special characters such as `#`or `$` which are common in other languages.
- Variable names must begin with an alphanumeric latter or an underscore, not a number.
- Variable names must not be a C# keyboard. For example. you cannot use `decimal decimal;` or `string string;`.
- Variable names are case-sensitive, meaning that `string Value;` and `string value;` are two different variables.
- Variable names should use **camel case**. This is a style of writing that uses a lower-case letter at the beginning of the first word and an upper-case letter at the beginning of each subsequent world. For example `string thisIsCamelCase`.
- Variable names should be descriptive and meaningful.
- Varible names should be one of more entire words appended together.
- Variable names should **not** include the data type of the variable.

# Setting and getting values from variables.
To assign a value to a variable, you use the *assignment operator*, which is a single equals character `=`.

```csharp
string firstName;
firstName = "Bob";
```

This is referend to as “setting the variable”, or simply, a “set” operation.

It is important to notice that the assignment happens from right to left. The C# compiler must first understand the value on the right side of the assignment operator, then it can perform the assignment to the variable on the left side of the assignment operator. if you reverse the order, you confuse the complier.

*Enforcing types* in your variable means you cant assign a value of one data type to a variable declared to hold a different data type. `ints` must hold integers, `strings`must hold strings.

To retrieve a value from a variable you just use the name of the variable.

```csharp
string firstName;
firstName = "Bob";
Console.WriteLine("firstName");
```

You can reuse and reassign values to variables as many times as you want.

```csharp
string firstName;
firstName = "Bob";
Console.WriteLine(firstName);
firstName = "Beth";
Console.WriteLine(firstName);
firstName = "Conrad";
Console.WriteLine(firstName);
firstName = "Grant";
Console.WriteLine(firstName);
```

You must *initialize* a variable before using it. If you have declared a variable but not assigned anything to it, you’ll get an error message when you compile.

It is recommended to assign a value to a variable as soon as you've declared it. You can do both the declaration and setting the value in the same line of code.

```csharp
string firstName = "Bob";
```

# Implicitly typed local variables.
An implicitly typed local variable is created using the `var` keyword. It instructs the compiler to infer the type.

The following code infers a `string` variable.

```csharp
var message = "Hello world!";
```

The complier understands the intent and treats every instance of the variable as an instance of type `string`.

If you later try to change the instance type of an already declared implicitly typed local variable you’ll get an error message when you compile.

You can only use the `var` keyword if the variable is initialized. if you attempt to run `var message;`without setting a value, you will receive an error message.

The `var` keyword has been widely adopted in the C# community.

The reason the `var` keyword is so important, is because when writing advanced code, there might be situations where the data type may not be obvious until it’s declared.

When getting started with C# its recommended to use the actual data type name when declaring variables. This helps to be purposeful as you write code.