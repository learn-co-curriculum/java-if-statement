# If Statement

## Learning Goals

- Learn about conditionals.
- Learn how to use the `if` statement.

## The `if` Statement in Java

In Java, code will run sequentially unless specified otherwise. We have seen in
the "Exception Handling" lesson how code could jump around if the code comes
across an exception. But even then, all our code so far would still be
considered "unconditional". This means that the code is written in a sequential
manner without any logic applied. Wouldn't it be great if we could say "If this
is true... do this thing first"? Well, it turns out, we can! Statements and
logic like that are called **conditionals** where we interrupt the flow of the
program with some logic.

Consider a program where we want to alert a student if he or she passed a test:


```java
import java.util.InputMismatchException;
import java.util.Scanner;

public class GradeExample {
    public static void main (String[] args) {
        Scanner scanner = new Scanner(System.in);

        try {
            // Prompt the user to enter a numeric grade from 0 to 100
            System.out.println("Enter a numeric grade from 0 - 100:");
            int grade = scanner.nextInt();

            // A passing grade is a 70 or higher
            if (grade >= 70) {
                System.out.println("Congrats! You passed!");
            }

        } catch (InputMismatchException exception) {
            System.out.println("Invalid input");
        }
    }
}
```

Let's break down the statement:

```java
if (grade >= 70) {
```

The `if` statement allows us to specify a "condition". In Java, an `if`
statement is immediately followed by an open parenthesis `(`, what we call a
"conditional clause" and a close parenthesis `)`. The **conditional clause** is
any expression that can evaluate to either "true" or "false".

In this case, either the `grade` is greater than or equal to 70, or it's not.
If it's greater than or equal to 70, then the program will execute the
content of the `if` block. If the grade is less than 70, then the program will
not execute the content of the `if` block. Consider the following flowchart:

![flowchart](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/if-conditional-flowchart.png)

Let's take a look at this control flow by running this program in the
debugger. We'll put a breakpoint at the `if` statement and enter in the grade
`90`:

![if-statement-breakpoint](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-if-statement-breakpoint.PNG)

As we can see in the debug console, the user entered 90 in as the input. If we
take a look at the conditional clause, `grade >= 70` is equivalent to
`90 >= 70`, which evaluates to `true`. Let's step-over to the next statement and
see what happens in the execution:

![execute-if-block](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-if-block-execution.PNG)

As we predicted, the execution falls into the `if` block! Let's run this again,
but this time, we'll have the user enter `60` instead:

![if-statement-breakpoint-again](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-if-statement-breakpoint-2.PNG)

When the user enters in 60, and we look at the conditional clause,
`grade >= 70`, we can see that this is now equivalent to `60 >= 70`, which is
`false`. Let's see what happens this time when we step-over to the next
statement:

![ignore-if-block](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-end-program.PNG)

Since the grade entered was less than 70, the program does not execute the
content of the `if` block and continues on with the program. In this case, there
is nothing after the `if` statement, so it will jump to the end of the program.
If we look at the console, we'll notice nothing was printed after prompting the
user for a grade:

```text
Enter a numeric grade from 0 - 100:
60
```

## Syntax of an `if` Statement

An `if` statement can contain multiple statements inside it. Therefore, an `if`
statement can be followed by an open curly brace `{` if it is meant to indicate
the conditional execution of more than one statement. As always, the open curly
brace `{` must then be matched with a close curly brace`}`:

```java
if (grade >= 70) {
    // as many statements here that I need for my program
}
```

Note that if we only have one conditional statement, we can omit the matching
curly braces:

```java
if (grade >= 70)
    System.out.println("Congrats! You passed!");
```

This notation is not recommended, as it makes it very easy to accidentally
expand or reduce the scope of an `if` statement.
