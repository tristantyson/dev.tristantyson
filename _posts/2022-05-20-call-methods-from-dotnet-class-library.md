---
layout: single
title:  "Call methods from the .NET Class Library using C#"
date:   2022-05-20 16:00:00 +0000
categories: C#
permalink: call-methods-dotnet-class-library
tags:
  - C#
  - Take your first steps with C#
toc: true
---
The C# programming language is supplemented by a large library of functionality that enables you to create desktop or web applications, access data in files or on the internet, perform advanced mathematical operations, and much more. Understanding how to navigate this library of functionality is a critical skill that will help you build feature-rich applications more quickly.

# The .NET Class Library

## What is the .Net Class Library?

The **.NET Class Library** is a collection of classes containing methods. These methods are created by Microsoft and are available for use in your application.

A class is a container for methods. Developers keep related methods together in a single class. Example, any methods that can send or receive information from a command-line window are collected into the `System.Console` class in the .NET Class Library.

In many cases theses classes and methods enable you to build specific a type of application.  One of the larger subsets of classes and methods enable you to create dynamic applications. There are several families of classes that enable you to build native desktop applications. Another subset of classes and methods enable you to access a database.

There are other classes with methods that are more general purpose in nature. They can allow you to read or write to files, perform trigonometry or calculus, make calls to retrieve data from across the internet, you could use these classes and their methods, whether you're building a web, desktop, mobile, or cloud application.

Having this library is a huge time saver for you as a software developer.  It saves you having to start from scratch with each new application you want to build.

## Even data types are part of the .NET Class Library.

The C# data types already learned are actually part of the .NET Class Library, too. C# masks the true identity of the data types we’ve used in order to simplify your work. Behind the scenes the data types are implemented just like every other class in the .NET class library. This means that there are helpful methods that are built in and available on your variables.

## What is a namespace?

Think of a namespace as the last name, surname or “family name” for a type. A class contains the code that implements a type. Classes are organised into a namespace to prevent naming collisions. After all, when there are thousands of classes, its possible that there might be a need or reuse a class name. The namespace helps to make sure no two classes have the same *full* name,

## How to find what you need in the .NET Class Library.

There is likely a small subset of classes you’ll use throughout your tenure developing with C#. While working on projects you’ll become familiar with some parts of the .NET Class Library and less familiar with others. No one knows its all.

You’ll likely use blogs, articles, or forums where others have needed to do similar kinds of things you want to do. Third-party sources will give you clues and even provide same sample code to try.

You’ll likely spend a lot of time reading Microsoft documentation for a specific method to understand exactly what they do, how they work, what are their limitations, under what conditions they raise exceptions, and how to mitigate those problems. Documentation is the source of truth, the documentation team works closely with the .NET class Library software developers to ensure its accuracy.

# Calling different kinds of methods in the .NET Class Library.

We’ve been calling methods since our first lines of code when using the `Console.WriteLine()` method. Not all classes and methods are implemented the same way.

## How to call methods in the .NET Class Library.

From the previous experience with the `Console.WriteLine()` method, you should already know the basics:

- Start by typing the class name, `Console`.
- Add the member access operator, the `.` symbol.
- Add the method’s name, `WriteLine`.
- Add the method invocation operator, which is a set of parentheses `()`.
- Finally, add the value you want the `Console.WriteLine()` method to print as an input parameter between the opening and closing parentheses (for example, `"Hello World!"`)

Optionally, depending on how the developers designed and implemented the given method, you may also need to:

- Pass additional values as input parameters.
- Accept a return value.

## Calling different kinds of methods in the .NET Class Library.

The following code simulates a dice roll by generating a random number and printing it to the console.

```csharp
Random dice = new Random();
int roll = dice.Next(1, 7);
Console.WriteLine(roll);
```

Running the code multiple times, numbers from 1 to 6 are displayed in the console output.

The first line of code creates a new instance of the `System.Random` class in the .NET Class Library and stores the reference to the new object in a variable named `dice`.

The second line of the code calls the `dice` objects `Next()` method passing in two parameters the minimum and maximum value of the random number. The `Next()` method returns the value, which we save into a variable named `roll`.

The third line of code calls the `WriteLine()` method to print the value of `roll` to the console.

## Stateful verses stateless methods.

In computing, **state** describes the condition of the execution environment at a specific moment in time. As code executes line by line, values are stored in variables. At any moment during execution, the current state of the application is the collection of all values stored in memory.

Some methods don't rely on the current state of the application to work properly. In other words, **stateless methods** are implemented so that they can work without referencing or changing any values already stored in memory. Stateless methods are also know as **static methods**.

Example, the `Console.WriteLine()` method doesn't rely on any value stored in memory. It performs its function and finishes without impacting the state of the application in any way.

Other methods, however, must have access to the state of the application to work properly. In other words, **stateful methods** are built in such a way that they rely on values stored in memory by previous lines of code that have already executed. Or they modify the state of the application by updating values or storing new values in memory. They're also know as **instance methods**.

Stateful (instance) methods keep track of their state in *fields*, which are variables defined on the class. Each new instance of the class gets its own copy of those fields in which to store state.

A single class can support both stateful and stateless methods. However, when you call stateful methods, you must first create an *instance* of the class so that the method can access state.

## Creating an instance of a class.

An instance of a class is called an *object*. To create a new instance of a class, you use the `new`operator. Consider the following line of code that creates a new instance of the `Random` class to create a new object called `dice`:

```csharp
Random dice = new Random();
```

The `new` operator does several important  things:

- It first requests an address in the computers memory large enough to store a new object based on the `Random` class.
- It creates the new object, and stores it at the memory address.
- It returns the memory address so that it can be saved in the dice variable.

From that point on, when the `dice` variable is referenced, the .NET Runtime performs a lookup behind the scenes to give the illusion that you're working directly with the object itself.

## How can you determine whether you need to create an instance of a class before calling its methods?

Consult the documentation

Attempt to access the method directly from the class itself. 

```csharp
int result = Random.Next();
```

Output:

```
(1,14): error CS0120: An object reference is required for the non-static field, method, or property 'Random.Next()'
```

# Work with return values and input parameters.