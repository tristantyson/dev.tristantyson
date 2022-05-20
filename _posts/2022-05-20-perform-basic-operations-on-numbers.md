---
layout: single
title:  "Perform basic operations on numbers in C#"
date:   2022-05-20 15:00:00 +0000
categories: C#
permalink: perform-basic-ops-on-numbers
tags:
  - C#
  - Take your first steps with C#
toc: true
---
We'll perform basic string and numeric operations on data. As we go on, the compiler will perform different tasks depending on the data types of the values around the given operator. 

# Simple addition and implicit data conversion.

## Add two numeric values

To add two numbers together you need to use the *addition operator* which is the `+` symbol. This is the same operator what is used in string concatenation. The reuse of one symbol for multiple purposes is sometimes called *overloading the operator* and happens frequently in C#.

```csharp
int firstNumber = 12;
int secondNumber = 7;
Console.WriteLine(firstNumber + secondNumber);
```

Output:

```
19
```

## Mix data types to force implicit type conversion

What happens when you try and mix `string` and `int` values with the `+` operator?

```csharp
string firstName = "Bob";
int widgetsSold = 7;
Console.WriteLine(firstName + " sold " + widgetsSold + " widgets.");
```

Output:

```
Bob sold 7 widgets.
```

In this example the compiler understands what we want to use the `+` symbol to concatenate the two operands. It decides this because the `+` symbol is surrounded by operands of `string` and `int`data types. It attempts to implicitly convert the `int` variable into a `string` temporarily so it can process the concatenation. The compiler does this automatically but ideally you would be explicit about your intentions.

## Adding numbers and concatenating strings

Look at the following code:

```csharp
string firstName = "Bob";
int widgetsSold = 7;
Console.WriteLine(firstName + " sold " + widgetsSold + 7 + " widgets.");
```

Output:

```
Bob sold 77 widgets.
```

Instead of adding the `int` variable to the literal `int` `7`, the complier treats everything as a string and concatenates it all together.

To let the complier know your intentions of adding the `int` variable to the literal `int`, you can use the parentheses symbol `()`.

```csharp
string firstName = "Bob";
int widgetsSold = 7;
Console.WriteLine(firstName + " sold " + (widgetsSold + 7) + " widgets.");
```

Output:

```
Bob sold 14 widgets.
```

In this case, the parentheses symbols form the *order of operations* operator, just like in a mathematical formula. This means the inner-most parentheses are resolved first, resulting in the addition of the `int` variable `widgetsSold` and the value `7`. Once this is resolved, the compiler moves forward in the order of operations and implicitly converts the result to a string so it can be concatenated with the rest of the message.

<aside>
💡 You would ideally avoid performing both a calculation and a concatenation in a single line of code. This example is to help you understand how the compiler deals with operators.

</aside>

# Math operators

## Addition, subtraction, multiplication, and division with integers.

```csharp
int sum = 7 + 5;
int difference = 7 - 5;
int product = 7 * 5;
int quotient = 7 / 5;

Console.WriteLine("Sum: " + sum);
Console.WriteLine("Difference: " + difference);
Console.WriteLine("Product: " + product);
Console.WriteLine("Quotient: " + quotient);
```

Output:

```
Sum: 12
Difference: 2
Product: 35
Quotient: 1
```

The above code demonstrates:

- `+` is the addition operator.
- `-` is the subtraction operator.
- `*` is the multiplication operator.
- `/` is the division operator.

The results from the division operation example is incorrect. This is because the variable is defined as an `int`, which are unable to represent a decimal value.

## Perform division using literal decimal data.

To see division working properly, we need to use a data type that supports fractional digits after the decimal point, like `decimal`.

```csharp
decimal decimalQuotient = 7.0m / 5;
Console.WriteLine("Decimal quotient: " + decimalQuotient);
```

Output:

```
Decimal quotient: 1.4
```

In order for this to work, the quotient must be of type `decimal` **and** either the dividend *or* divisor must be of type `decimal`(*or* both).

Working examples:

```csharp
decimal decimalQuotient = 7 / 5.0m;
decimal decimalQuotient = 7.0m / 5.0m;
```

Non working examples:

```csharp
int decimalQuotient = 7 / 5.0m;
int decimalQuotient = 7.0m / 5;
int decimalQuotient = 7.0m / 5.0m;
decimal decimalQuotient = 7 / 5;
```

## Perform division using literal decimal data

If you want to perform division on two variables of type `int` but do not want the result truncated, you must perform a **data type cast** from `int` to `decimal`.

Casting is one type of data conversion that instructs the compiler to temporarily treat a value as if it were a different data type.

To cast `int` to `decical` , you need to add the *cast operator* before the value. The cast operator is the name of the data type you want to cast surrounded by parenthesis, in front of the value to cast it. in this case it would be `(decial)` before the variable.

```csharp
int first = 7;
int second = 5;
decimal quotient = (decimal)first / (decimal)second;
Console.WriteLine(quotient);
```

Output:

```
1.4
```

<aside>
💡 We’ve seen three uses, or overloads, for the parenthesis operator: method invocation, order of operations, and casting

</aside>

## Determine the remainder after int division.

The remainder operator `%` tells you the remainder of the `int` division. 

```csharp
Console.WriteLine("Modulus of 200 / 5 : " + (200 % 5));
Console.WriteLine("Modulus of 7 / 5 : " + (7 % 5));
```

Output:

```
Modulus of 200 / 5 : 0
Modulus of 7 / 5 : 2
```

## Order or operations.

In math, PEMDAS is an acronym that helps students remember the order in which multiple operations are performed. The order is:

- Parenthesis (what ever is inside the parenthesis is performed first).
- Exponents.
- Multiplication and division (from left to right).
- Addition and Subtraction (from left to right).

C# follows the same order as PEMDAS except for exponents.

See the below example:

```csharp
int value1 = 3 + 4 * 5;
int value2 = (3 + 4) * 5;
Console.WriteLine(value1);
Console.WriteLine(value2);
```

Output:

```
23
35
```

Notice the difference when performing the same operation in a different order.

# Increment and decrement values.

Frequently, you’ll need to increment and decrement values, especially when you work with any looping logic or code that interacts with a data structure, which houses multiple element of data.

The `+=` operator adds and assigns the value on the right of the operator to the value on the left of the operator.

```csharp
int value = 0;
value = value + 5;
value += 5;
```

In the above example, lines two and three perform the same.

The `++` operator increments the value of the variable by 1.

```csharp
int value = 0;
value = value + 1;
value++;
```

In the above example, lines 2 and 3 perform the same.

The same techniques can be used for subtraction, multiplication and more.

<aside>
💡 Operators like `+=`, `-=`, `*=`, `++`, and `--` are known as *compound assignment operators* because they compound some operation in addition to assigning the result to the variable. The `+=` operator is specifically termed the *addition assignment* operator.

</aside>

Code to increase and decrease a value using different methods.

```csharp
int value = 1;

value = value + 1;
Console.WriteLine("First increment: " + value);

value += 1;
Console.WriteLine("Second increment: " + value);

value++;
Console.WriteLine("Third increment: " + value);

value = value - 1;
Console.WriteLine("First decrement: " + value);

value -= 1;
Console.WriteLine("Second decrement: " + value);

value--;
Console.WriteLine("Third decrement: " + value);
```

Output:

```
First increment: 2
Second increment: 3
Third increment: 4
First decrement: 3
Second decrement: 2
Third decrement: 1
```

## Positioning the increment and decrement operators

Depending on their position, the increment and decrement operators perform their operations before or after they retrieve their value. If you use the operator before the value `++value`, then the increment will happen *before* the value is retrieved. Likewise, `value++` will increment the value *after* the value has been retrieved.

```csharp
int value = 1;
value++;
Console.WriteLine("First: " + value);
Console.WriteLine("Second: " + value++);
Console.WriteLine("Third: " + value);
Console.WriteLine("Fourth: " + (++value));
```

Output:

```
First: 2
Second: 2
Third: 3
Fourth: 4
```

Notice the line:

```csharp
Console.WriteLine("Second: " + value++);
```

The operator is *after* the value. So the value is received and used in the string interpolation operation, *then* the value is incremented.

The next line of code confirms the value was in fact, incremented.

```csharp
Console.WriteLine("Third: " + value);
```

This is in contrast to the last fine of code where the operation is placed before the value. meaning that the value is first increased then retrieved for use in the string interpolation operation

.

```csharp
Console.WriteLine("Fourth: " + (++value));
```

While not strictly necessary, we added parenthesis around the expression `(++value)` to improve readability. Seeing so many `+` operators doesn't read very well when reviewing code at a later date. These decisions are purely for stylistic purposes but  bare in mind you will write code once and read it many times, so you should always prioritize readability where you can.