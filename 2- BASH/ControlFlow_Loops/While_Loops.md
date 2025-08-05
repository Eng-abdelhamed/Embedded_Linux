# Understanding The `While` loop Syntax and Exambles

The `while` loop in Bash repeats a block of code as long as a specific condition evaluates to `true`. However, in `Bash scripting`, conditions are evaluated based on their exit status:

- **Basic Syntax** :
    ```bash
    #! /bin/bash

    while [ condition ]
    do

        #Block Of Code To Execute As Long as True Condition

    done
    ```

- **Or alternatively**:

    ```bash
    #!/bin/bash
    while [[ condition ]]; do

        #Eceture Block of code
    done
    ```
#


# Nested while Loops in Bash

- `A nested while loop` is a **while loop** placed inside another while loop. This allows you to perform more **complex operations** by iterating over multiple sets of data. The **outer loop will iterate through its conditions**, and for each iteration of the outer loop, the inner loop will execute.
- **Structure of Nested while Loops**:
    ```bash
    while [ condition1 ]
    do
    # Outer loop body

    while [ condition2 ]
    do
        # Inner loop body
    done

    done
    ```
- Here, the **outer loop** will keep iterating as long as condition1 is true, and for each iteration of the outer loop, the inner loop will continue iterating as long as **condition2** is true.


# Common Mistakes

- **Forgetting to Update Loop Variable**: Leads to infinite loops. Debug by checking the condition and using set -x.
```bash
    i=0
    while [[ "$i" -lt 5 ]]; do echo "$i"; done # Error!
```
- **Incorrect Loop Condition**: Off-by-one errors, wrong operators.

```bash
    count=1
    while [[ "$count" -lt 5 ]]; do echo "$count"; count=$((count + 1)); done # Runs 4 times
```

- **Command Substitution in Condition**: Be aware if the command's output changes unexpectedly.

- **Misusing break and continue**: Can lead to incorrect loop behavior.

- **Ignoring Edge Cases**: Consider initial conditions and unexpected variable states.
