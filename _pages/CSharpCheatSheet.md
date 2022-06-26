---
title: "C# Cheat Sheet"
permalink: /CSharpCheatSheet/
layout: single
author_profile: true
toc: true
---
A C# cheat sheet to act as a quick reference with syntax examples.

# Data Types

## Types

| Type | Represents | Range | Default Value |
| --- | --- | --- | --- |
| bool | Boolean value | True or False | False |
| byte | 8-bit unsigned integer | 0 to 255 | 0 |
| char | 16-bit Unicode character | U +0000 to U +ffff | ‘\0’ |
| decimal | 128-bit precise decimal values with 28-29 significant digits | (-7.9 x 1028 to 7.9 x 1028) / 100 to 28 | 0.0M |
| double | 64-bit double-precision floating point type | (+/-)5.0 x 10-324 to (+/-)1.7 x 10308 | 0.0D |
| float | 32-bit single-precision floating point type | -3.4 x 1038 to + 3.4 x 1038 | 0.0F |
| int | 32-bit signed integer type | -2,147,483,648 to 2,147,483,647 | 0 |
| long | 64-bit signed integer type | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | 0L |
| sbyte | 8-bit signed integer type | -128 to 127 | 0 |
| short | 16-bit signed integer type | -32,768 to 32,767 | 0 |
| uint | 32-bit unsigned integer type | 0 to 4,294,967,295 | 0 |
| ulong | 64-bit unsigned integer type | 0 to 18,446,744,073,709,551,615 | 0 |
| ushort | 16-bit unsigned integer type | 0 to 65,535 | 0 |

## Type Conversion

| ToBoolean | Converts a type to a Boolean value, where possible. |
| ToByte | Converts a type to a byte. |
| ToChar | Converts a type to a single Unicode character, where possible. |
| ToDateTime | Converts a type (integer or string type) to date-time structures. |
| ToDecimal | Converts a floating-point or integer type to a decimal type. |
| ToDouble | Converts a type to a double type. |
| ToInt16 | Converts a type to a 16-bit integer. |
| ToInt32 | Converts a type to a 32-bit integer. |
| ToInt64 | Converts a type to a 64-bit integer. |
| ToSbyte | Converts a type to a signed byte type. |
| ToSingle | Converts a type to a small floating-point number. |
| ToString | Converts a type to a string. |
| ToType | Converts a type to a specified type. |
| ToUInt16 | Converts a type to an unsigned int type. |
| ToUInt32 | Converts a type to an unsigned long type. |
| ToUInt64 | Converts a type to an unsigned big integer. |

## Literal data types examples

```csharp
//Literal data types:

	// char literal - requires single quotation operator.
	Console.WriteLine('b');

	// int literal - requires no additional operators.
	Console.WriteLine(123);
	
	// string literal - requires double quotation operators.
	Console.WriteLine("Hello!");

	// decimal literal - requires a literal suffix
	Console.WriteLine(12.3m);

	// boolean literal - requires a true or false value.
	Console.WriteLine(true);
	Console.WriteLine(false);
```

# Variables

## Variable types

| Integral types | sbyte, byte, short, ushort, int, uint, long, ulong, and char |
| --- | --- |
| Floating point types | float and double |
| Decimal types | decimal |
| Boolean types | true or false values, as assigned |
| Nullable types | Nullable data types |

## Defining

```
<type> <name>;
```

## **Initialising**

```
<name> = <value>;
```

## Define and initialise

```
<type> <name> = <value>;
```

## Example

```csharp
// Define variable
string firstName;

// Initialise defined variable
firstName = "Bob";

// Define and initialise variable - best practice.
string firstName = "Bob";

// Implicitly typed local variable - It instructs the compiler to infer the type.
var message = "Hello world!";

```

# String operations

## Character escape sequence

| \\ | \ character |
| --- | --- |
| \' | ‘ character |
| \" | ” character |
| \? | ? character |
| \a | Alert or bell |
| \b | Backspace |
| \f | Form feed |
| \n | Newline |
| \r | Carriage return |
| \t | Horizontal tab |
| \v | Vertical tab |
| \xhh . . . | Hexadecimal number of one or more digits |

## Escape sequence examples

### New line and tab

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

### Double quotation

```csharp
Console.WriteLine("Hello \"World\"!");
```

Output:

```
Hello "World"!
```

### Backslashes

```csharp
Console.WriteLine("c:\\source\\repos");
```

Output: 

```
c:\source\repos
```

### Example using newline, double quote and tab together

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

```csharp
// use the @ directive before the literal string.
Console.WriteLine(@"   c:\source\repos   
      (this is where your code goes)");
```

Output: 

```
c:\source\repos   
      (this is where your code goes)
```

## Unicode escape characters

```csharp
// You can add encoded characters in literal strings using the `\u` escape sequence, followed by a four-character Unicode (UFT-16).

// Kon'nichiwa World
Console.WriteLine("\u3053\u3093\u306B\u3061\u306F World!");
```

Output: 

```
こんにちは World!
```

## String Concatenation

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

Multiple concatenation operations in the same line of code.
```csharp
string firstName = "Bob";
string greeting = "Hello";
Console.WriteLine(greeting + " " + firstName + "!");
```

Output:

```csharp
Hello Bob!
```

## String interpolation

Instead of writing this:

```csharp
string message = greeting + " " + firstName + "!";
```

You can write this:

```csharp
string message = $"{greeting} {firstName}!";
```

Combine 2 variables with string interpolation:

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

```csharp
string projectName = "First-Project";
Console.WriteLine($@"C:\Output\{projectName}\Data");
```

Output: 

```
C:\Output\First-Project\Data
```

# Numeric Operations
Coming next
