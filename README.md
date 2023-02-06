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
not execute the content of the `if` block.

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

## If-Else Statements

An `if` statement can be followed by an `else` statement. When an `else`
follows an `if`, its content will be executed whenever the conditional clause
of the `if` statement is not true. It should be noted that an `else` statement
is not required to follow an `if` statement, as we have seen in the example
above. But if we were to have an `else` statement, the syntax would look like
this:

```java
if (true) {
    System.out.println("display this message when true");
} else {
    System.out.println("display this message when false");
}
```

Let's modify our program to include an `else` statement! Consider the code below
with the following changes:

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
            } else {
                System.out.println("Oops! Better luck next time!");
            }

        } catch (InputMismatchException exception) {
            System.out.println("Invalid input");
        }
    }
}
```

We can take a look at this again with the debugger and the input of `60` again:

![execute-else-block](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-else-block-execution.PNG)

As we saw previously, when the program stops and evaluates the conditional
clause, it will return `false` since 60 not greater than or equal to 70. But
this time when we choose the step-over action, the next line to be executed
falls into the `else` block instead of continuing to the end of the program! If
we resume the program, we'll see the following output:

```text
Enter a numeric grade from 0 - 100:
60
Oops! Better luck next time!
```

As we can see, the `else` block changes the flow of the program just slightly
when added. It will always fall into the `else` block if the conditional clause
within the `if` statement evaluates to false.

## Else If Statements


An `if` statement can also be followed by an `else if` statement. When an
`else if` statement follows an `if`, the `else if` allows us to specify
another condition whenever the conditional clause of the `if` statement is
not true. It is similar to an `else` in that it is not required to follow
an `if` statement but differs in that it has another conditional clause
attached to it. Let's alter our code to this:

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
            if (grade > 70) {
                System.out.println("Congrats! You passed!");
            } else if (grade == 70) {
                System.out.println("Whew! You just passed!");
            } else {
                System.out.println("Oops! Better luck next time!");
            }

        } catch (InputMismatchException exception) {
            System.out.println("Invalid input");
        }
    }
}
```

Notice we switched the relational operator in the `if` statement's conditional
clause from `>=` to `>` and then added the `else-if` statement with the
conditional clause of `grade == 70`. So now, if the user enters 70, we would
expect the program to execute the `else-if` block.

If we run the program in the debugger, notice that when we step-over the
breakpoint at the `if` statement, the next line of execution this time is
`else if (grade == 70)`:

![next-line-else-if-statement](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-else-if-statement-breakpoint.PNG)

Java will then look at the conditional clause, `grade == 70`. As we can see, the
`grade` variable is storing the value 70; therefore, `70 == 70` will evaluate to
`true`. Let's continue to step-over in the debugger:

![execute-else-if-block](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-else-if-block-executed.PNG)

As we can see, the code then falls into the `else-if` block. If we continue
to step-over, we will then see that the program skips over the `else` block.
This is because a conditional clause had been satisfied by either the `if`
statement's clause or any other `else-if` conditional clauses prior.

When we resume the program, the output in the console will look like this:

```text
Enter a numeric grade from 0 - 100:
70
Whew! You just passed!
```

Note: We can have as many `else-if` statements within an `if/else-if/else` block
of code. Consider this example:

```java
if (grade >= 90) {
    System.out.println("Wow! You got an A!");
} else if (grade >= 80) {
    System.out.println("You got a B!");
} else if (grade >= 70) {
    System.out.println("Congrats! You passed!");
} else {
    System.out.println("Oops! Better luck next time!");
}
```

Take note of the way the conditional clauses are ordered within the `if` and
`else-if` statements. If the user enters a grade of 90 or higher, the program
will execute the statements within the `if` block and **only** the `if` block.
The program will then skip over the `else-if` and `else` statements. If the user
enters a grade between 89 and 80, then the second `else-if` block will then be
executed. If the user enters a grade between 79 and 70, then the third `else-if`
block will be executed. Finally, if the grade is 69 or less, then the `else`
block will be executed.

You may follow along with this by either using the IntelliJ debugger, as we have
throughout this lesson, or you can use the browser-based Java visualizer
[here](https://pythontutor.com/java.html#code=public%20class%20GradeExample%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%0A%20%20%20%20%20%20//%20Change%20this%20hardcoded%20value%20and%20watch%20the%20code%20be%20executed%0A%20%20%20%20%20%20int%20grade%20%3D%2090%3B%0A%20%20%20%20%20%20%0A%20%20%20%20%20%20if%20%28grade%20%3E%3D%2090%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Wow!%20You%20got%20an%20A!%22%29%3B%0A%20%20%20%20%20%20%7D%20else%20if%20%28grade%20%3E%3D%2080%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20System.out.println%28%22You%20got%20a%20B!%22%29%3B%0A%20%20%20%20%20%20%7D%20else%20if%20%28grade%20%3E%3D%2070%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Congrats!%20You%20passed!%22%29%3B%0A%20%20%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Oops!%20Better%20luck%20next%20time!%22%29%3B%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%7D&cumulative=false&heapPrimitives=nevernest&mode=edit&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false)
to see the flow of how this program is executed.

## Nested Conditionals

Since `if` statements can contain multiple statements inside their `if` block,
they can also contain other `if` statements. This is called
**nested conditionals**. Consider the following changes to the program we have
been working with:

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
                if (grade >= 90) {
                    System.out.println("Wow! You got an A!");
                    System.out.println("Great job!");
                } else {
                    System.out.println("Great job!");
                }
            }

        } catch (InputMismatchException exception) {
            System.out.println("Invalid input");
        }
    }
}
```

In the example above, we want to further customize the greeting message for
students that pass their test. We want to give an extra congratulations to
those students who receive a score of 90 and up; so we check to see if their
grade is greater than or equal to a 90 and display a message if that is the
case. If not, we simply tell congratulate them on passing their test and let
them know they did a great job.

Let's take a look at what happens when the user enters 85 for a grade in the
debugger:

![if-statement-breakpoint](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-if-statement-breakpoint-3.PNG)

We will first compare the value in the variable `grade` with the passing grade
of 70 in the first `if` statement. Since `grade` is storing the value of 85, we
will evaluate `85 >= 70` to be `true`. As we have seen previously, the code will
then enter the `if` block.

Let's step-over two more times until we reach the line `if (grade >= 90)`:

![inner-if-statement](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-if-statement-breakpoint-4.PNG)

At this point, we encounter another `if` statement! Just like the previous outer
`if` statement, Java will evaluate the conditional clause. This conditional
clause is `grade >= 90`. In this case, `85 >= 90` will evaluate to `false`,
causing the execution to skip on down to the `else` statement within this inner
`if-else` block:

![else-block-execution](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-else-block-execution-2.PNG)

If we resume the program, we'll see that when the user enters 85, the output in
the console looks like this:

```text
Enter a numeric grade from 0 - 100:
85
Congrats! You passed!
Great job!
```

Now let's take a look at what happens when the user enters 90 instead for a
grade in the debugger:

![if-statement-breakpoint](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-if-statement-breakpoint-5.PNG)

Just as before, we will evaluate the conditional clause of the outer `if`
statement to be `90 >= 70`. This will return `true` so we expect to fall into
the outer `if` block. Let's step-over two more times until we reach the line
`if (grade >= 90)` again:

![inner-if-statement](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-if-statement-breakpoint-6.PNG)

Like before, the code will evaluate the conditional clause of this inner `if`
statement. But unlike the previous input, when we evaluate `grade >= 90`, which
is equivalent to `90 >= 90` in this case, it will result in a `true`. So instead
of skipping down to the `else` block like we did above, this time, we will enter
into the inner `if` block:

![if-block-execution](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-if-block-execution-2.PNG)

If we resume the program, we'll see that when the user enters 90, the output in
the console looks like this:

```text
Enter a numeric grade from 0 - 100:
90
Congrats! You passed!
Wow! You got an A!
Great job!
```

Now, we may have noticed that no matter if the value of `grade` is considered an
`A` or not, as long as it is passing, we tell the user "Great job!" Can we modify
the code in the previous example to remove the duplicated line of code between
the case where the student's grade is greater than or equal to 90 and the case
where the student's grade is less than 90 but greater than or equal to 70?

The answer is yes! Consider the following code below that removes the duplicated
line:

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
                if (grade >= 90) {
                    System.out.println("Wow! You got an A!");
                }
                System.out.println("Great job!");
            }

        } catch (InputMismatchException exception) {
            System.out.println("Invalid input");
        }
    }
}
```

In this case, the `else` block was unnecessary since "Great job!" would be
printed to the console regardless as long as the grade is considered a passing
grade.

Let's do knowledge check based off of the code above!

<details>
  <summary>What do we expect to be printed <i>after</i> the user enters in 60 for the grade?</summary>

  <p>Answer:<br></p>

  <p>Nothing. There will be no lines printed after the user enters in 60 for a grade since there is no else statement after the <code>if (grade >= 70)</code></p>

</details>

<details>
  <summary>What do we expect to be printed <i>after</i> the user enters in 70 for the grade?</summary>

  <p>Answer:<br></p>

  <p><code>Congrats! You passed!</code><br><code>Great job!</code></p>

</details>

<details>
  <summary>What do we expect to be printed <i>after</i> the user enters in 92 for the grade?</summary>

  <p>Answer:<br></p>

  <p><code>Congrats! You passed!</code><br><code>Wow! You got an A!</code><br><code>Great job!</code></p>

</details>
