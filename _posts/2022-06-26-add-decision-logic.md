---
layout: single
title:  "Add decision logic to your code using the if-elseif-else statement in C#"
date:   2022-06-26 12:00:00 +0000
categories: C#
permalink: add-decision-logic
tags:
  - C#
  - Take your first steps with C#
toc: true
---
The C# programming language allows you to build applications that employ decision-making logic. Branching logic enables your programs to perform different instructions based on a set of conditions.

# Using the if statement

The most widely used braching statement is the `if` statement. the `if` statement relies on a Boolean expression that is enclosed in a set of parentheses.  If the express is true, the code executes. If the expression is false, the code is skipped.

## Create a random-number game by using if statements

We’ll use the `Random.Next()` method to simulate rolling three six-sided dice. We’ll evaluate the values to calculate a score. If the score is greater than an arbitrary total, we’ll display a winning message to the user. Otherwise, we’ll display a losing message to the user.

- If any two dice you roll result in the same value, you get two bonus points for rolling double.
- If all three dice you roll result in the same value, you get six bonus points for rolling triples.
- If the sum of the three dice rolls, plus any point bonuses, is 15 or greater, you win the game, otherwise, you lose.

## Step 1 - Write code that generates three random numbers and displays them in output.

```csharp
Random dice = new Random();

int roll1 = dice.Next(1, 7);
int roll2 = dice.Next(1, 7);
int roll3 = dice.Next(1, 7);

int total = roll1 + roll2 + roll3;

Console.WriteLine($"Dice roll: {roll1} + {roll2} + {roll3} = {total}");
```

We create a new instance of the `System.Random` class and store the reference to that object in the `dice`variable. Then, we call the `[Random.Next](http://Random.Next)()`method on the `dice` variable.  We call the `Random.Next` method on the `dice`variable object 3 times, providing the lower and upper bounds to restrict the possible values to mimic a 6 sided dice.  These are stored in varibles `roll1`, `roll2`, `roll3`.

Next, we sum up the the dice rolls and save the value in the `total` variable.

Finally, we display all the values by using string interpolation.

Output:

```
Dice roll: 4 + 5 + 2 = 11
```

## Step 2 - Add an if statement to display different messages based on the value of the total variable.

```csharp
Random dice = new Random();

int roll1 = dice.Next(1, 7);
int roll2 = dice.Next(1, 7);
int roll3 = dice.Next(1, 7);

int total = roll1 + roll2 + roll3;

Console.WriteLine($"Dice roll: {roll1} + {roll2} + {roll3} = {total}");

if (total > 14)
{
    Console.WriteLine("You win!");
}

if (total < 15)
{
    Console.WriteLine("Sorry, you lose.");
}
```

We added two `if` statements to handle the winning and losing scenarios.

The `if` statement is made up of three parts:

- The `if` keyword.
- A *Boolean expression* between parentheses `()`.
- A *code block* defined by curly braces `{}`.

The first Boolean expression `total > 14` is evaluated. If the value of `total` is grater than `14` then the flow of execution will continue into the code defined in the code block `{}`.

However, if the Boolean expression is false, the flow of execution will skip the code block.

The second `if` statement controls the message if the user loses.

## What is a Boolean expression?

A Boolean expression is any code that returns a Boolean value, either `ture`or `false`. 

Here is a simple code example that uses the `string.Contains()`method to evaluate whether one string contains another string:

```csharp
string message = "The quick brown fox jumps over the lazy dog.";
bool result = message.Contains("dog");
Console.WriteLine(result);

if (message.Contains("fox"))
{
    Console.WriteLine("What does the fox say?");
}
```

Because the `message.Contains("fox")` returns a `ture`or `false` value, it qualifies as a Boolean expression and can be used in an `if` statement.

Other simple Boolean expressions can be created by using operators to compare two values. Operators include:

- `==`, the "equals" operator, to test for equality.
- `>`, the "greater than" operator, to test that the value on the left is greater than the value on the right.
- `<`, the "less than" operator, to test that the value on the left is less than the value on the right.
- `>=`, the "greater than or equal to" operator.
- `<=`, the "less than or equal to" operator.

## Step 3 - Add another if statement to implement the doubles bonus

Lets implement the rule “If any two dice you roll result in the same value, you get two bonus points for rolling double.”

```csharp
Random dice = new Random();

int roll1 = dice.Next(1, 7);
int roll2 = dice.Next(1, 7);
int roll3 = dice.Next(1, 7);

int total = roll1 + roll2 + roll3;

Console.WriteLine($"Dice roll: {roll1} + {roll2} + {roll3} = {total}");

if ((roll1 == roll2) || (roll2 == roll3) || (roll1 == roll3))
{
    Console.WriteLine("You rolled doubles! +2 bonus to total!");
    total += 2;
}

if (total >= 15)
{
    Console.WriteLine("You win!");
}

if (total < 15)
{
    Console.WriteLine("Sorry, you lose.");
}
```

Here we combine 2 Boolean expressions to create one large Boolean express in a single line of code. This type of code is sometimes called a *compound condition*. We have one outer set of parentheses that combines three inner sets of parentheses separated by two pipe characters.

Twi pipe characters `||` is the **logical OR** operator, which basically says “either the expression to my left OR the expression to my right must be true for the ENTIRE Boolean expression to be true”. If bother expressions are false, the entire Boolean expression is false.

First, we evaluate `(roll1 == roll2)`. If that's true, the entire expression is true. If it's false, we evaluate `(roll2 == roll3)`. If that's true, the entire expression is true. If it's false, we evaluate `(roll1 == roll3)`. If that's true, the entire expression is true. If all three are false, the entire expression is false.

If the compound Boolean expression is true, we execute the following code block. This time, there are two lines of code. The first line of code prints a message to the user. The second line of code increments the value of `total` by `2`.

Finally, we also changed the check to see if the user won to use the `>=` operator. That scenario more closely resembles the requirement we created as we began, but it should function identically to what we wrote previously.

## Step 4 - Add another if statement to implement the triples bonus

Next, let's add another new rule: "If all three dice you roll result in the same value, you get six bonus points for rolling triples.”

```csharp
Random dice = new Random();

int roll1 = dice.Next(1, 7);
int roll2 = dice.Next(1, 7);
int roll3 = dice.Next(1, 7);

int total = roll1 + roll2 + roll3;

Console.WriteLine($"Dice roll: {roll1} + {roll2} + {roll3} = {total}");

if ((roll1 == roll2) || (roll2 == roll3) || (roll1 == roll3))
{
    Console.WriteLine("You rolled doubles! +2 bonus to total!");
    total += 2;
}

if ((roll1 == roll2) && (roll2 == roll3)) 
{
    Console.WriteLine("You rolled triples! +6 bonus to total!");
    total += 6;
}

if (total >= 15)
{
    Console.WriteLine("You win!");
}

if (total < 15)
{
    Console.WriteLine("Sorry, you lose.");
}
```

Here, we combine two Boolean expressions to create one compound Boolean expression in a single line of code. We have one outer set of parentheses that combines two inner sets of parentheses separated by two ampersand characters.

Two ampersand characters `&&` is the **logical AND** operator, which basically says "only if both expressions are true, then the entire expression is true". In this case, if `roll1` is equal to `roll2`, and `roll2` is equal to `roll3`, so `roll1` must be equal to `roll3` and the user rolled triples.

If you run the code, you might see output like this example:

Output

```
Dice roll: 3 + 6 + 1 = 10
Sorry, you lose.

```

Or like this example:

Output

```
Dice roll: 1 + 4 + 4 = 9
You rolled doubles! +2 bonus to total!
Sorry, you lose.

```

Or like this example:

Output

```
Dice roll: 5 + 6 + 4 = 15
You win!

```

Or, if you're lucky, you'll see this output:

Output

```
Dice roll: 6 + 6 + 6 = 18
You rolled doubles! +2 bonus to total!
You rolled triples! +6 bonus to total!
You win!

```

But wait, should we really reward the player for getting both a triple bonus and a double bonus? After all, a triple implies that they also rolled a double. Ideally, this bonus doesn't *stack*. They should be two separate bonuses. We have our first bug in logic.

# Use the ‘else’ and ‘else if’ statement

## Combine the win or lose checking into one statement.

Instead of performing two checks to display the "You win!" or "Sorry, you lose" message, we'll use the `else` keyword.

```csharp
Random dice = new Random();

int roll1 = dice.Next(1, 7);
int roll2 = dice.Next(1, 7);
int roll3 = dice.Next(1, 7);

int total = roll1 + roll2 + roll3;

Console.WriteLine($"Dice roll: {roll1} + {roll2} + {roll3} = {total}");

if ((roll1 == roll2) || (roll2 == roll3) || (roll1 == roll3))
{
    Console.WriteLine("You rolled doubles!  +2 bonus to total!");
    total += 2;
}

if ((roll1 == roll2) && (roll2 == roll3))
{
    Console.WriteLine("You rolled triples!  +6 bonus to total!");
    total += 6;
}

if (total >= 15)
{
    Console.WriteLine("You win!");
}
else 
{
    Console.WriteLine("Sorry, you lose.");
}
```

Here, if `total >= 15` is false, the code block after the `else` keyword will execute. Because these two options are related opposites, this scenario is a perfect example of when to use the `else` keyword.

## Use nesting to remove the double or triple stacking bonus.

In the previous code, we saw how we introduced a subtle logic bug into our application. Let's fix bug that by using nesting.

Nesting allows us to place code blocks inside of code blocks. In this case, we'll nest `if` and `else` statements (the check for triples) inside of another `if` statement (the check for doubles) to prevent them both from happening.

We'll nest the check for triples inside of the check for doubles.

```csharp
int roll1 = 6;
int roll2 = 6;
int roll3 = 6;

int total = roll1 + roll2 + roll3;

Console.WriteLine($"Dice roll: {roll1} + {roll2} + {roll3} = {total}");

if ((roll1 == roll2) || (roll2 == roll3) || (roll1 == roll3))
{
    if ((roll1 == roll2) && (roll2 == roll3))
    {
        Console.WriteLine("You rolled triples!  +6 bonus to total!");
        total += 6;
    }
    else
    {
        Console.WriteLine("You rolled doubles!  +2 bonus to total!");
        total += 2;
    }
}

if (total >= 15)
{
    Console.WriteLine("You win!");
}
else 
{
    Console.WriteLine("Sorry, you lose.");
}
```

To test the code without running the application dozens of times, you can temporarily hard-code the values of the three `roll` variables by adding the following code before the line where `total` is declared and initialized.

To test that double work:

```csharp
roll1 = 6;
roll2 = 6;
roll3 = 5;
```

Output:

```
Dice roll: 6 + 6 + 5 = 17
You rolled doubles!  +2 bonus to total!
You win!
```

To test that triples work:

```csharp
roll1 = 6;
roll2 = 6;
roll3 = 6;
```

Output:

```
Dice roll: 6 + 6 + 6 = 18
You rolled triples!  +6 bonus to total!
You win!
```

## ****Use if, else, and else if statements to give a prize instead of a win-lose message****

To make the game more fun, let's change the game from win-or-lose to award fictitious prizes for each score. We'll offer four prizes. The player should win only one prize:

- If the player scores greater or equal to 16, they'll win a new car.
- If the player scores greater or equal to 10, they'll win a new laptop.
- If the player scores exactly 7, they'll win a trip.
- Otherwise, the player wins a kitten.

```csharp
Random dice = new Random();

int roll1 = dice.Next(1, 7);
int roll2 = dice.Next(1, 7);
int roll3 = dice.Next(1, 7);

int total = roll1 + roll2 + roll3;

Console.WriteLine($"Dice roll: {roll1} + {roll2} + {roll3} = {total}");

if ((roll1 == roll2) || (roll2 == roll3) || (roll1 == roll3))
{
    if ((roll1 == roll2) && (roll2 == roll3))
    {
        Console.WriteLine("You rolled triples!  +6 bonus to total!");
        total += 6;
    }
    else
    {
        Console.WriteLine("You rolled doubles!  +2 bonus to total!");
        total += 2;
    }
}

if (total >= 16)
{
    Console.WriteLine("You win a new car!");
}
else if (total >= 10)
{
    Console.WriteLine("You win a new laptop!");
}
else if (total == 7)
{
    Console.WriteLine("You win a trip for two!");
}
else
{
    Console.WriteLine("You win a kitten!");
}
```

You can use `if`, `else`, and `else if` statements to create multiple exclusive conditions as Boolean expressions. In other words, when you want only one outcome to happen, but you have several possible conditions and results, use as many `else if` statements as you want. If none of the `if` and `else if` statements apply, the final `else` code block will be executed. The `else` is optional, but it must come last.