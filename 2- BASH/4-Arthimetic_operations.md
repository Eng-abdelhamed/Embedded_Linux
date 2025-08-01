# Arthimetic Operations In Bash

- Bash supports various arithmetic operations, which can be performed using different methods such as `expr, let, (( )), and bc.` This document provides an overview of arithmetic operations in Bash and their usage.

## 1 - Arithmetic Methods in Bash

## 1.1 - Using `expr`
**expr** is one of the oldest methods to perform arithmetic operations in Bash. It requires spaces between numbers and operators.



```bash
#!/bin/bash

A=5
B=3

# Adding
expr $A + $B

# Difference
expr $A - $B

# Divison
expr $A / $B

# For Multiplication use `\*` instead of `*` For Avoiding the Wildcard 
expr $A \* $B

result=$(expr $A + $B)
echo $result  # Output = 8
```

## 1.2 - Using `let`

- let allows direct arithmetic evaluation. --> No need for **spaces between operators and numbers**.


```bash
#! /bin/bash
A=4
b=2
let result=a+b
echo $result #output is 6
```

## 1.3 - Using (( ))  The most Recommended Way

- The `(( ))` syntax provides the cleanest way to perform arithmetic calculations in Bash.

```bash
#! /bin/bash
A=4
B=2
result=$((A+B))   #Output is 6
```
- you may also using programming c Typo

```bash
echo $((A--))
echo $((++A))
echo $((A++))
echo $((A++))
```

## 1.4 Using bc (for Floating-Point Calculations)


- The `bc` command is used for floating-point calculations, as Bash does not support them natively.
- `expr` and `"double parentheses"` only return decimal output, they do not support floating values.
- For this we use another utility called `bc`, it referred to as Basic Calculator.
- It works in an `interactive mode` and also you can input to another command as well
- `bc -l` is used when You Want Floating numbers , `"scale =2 ; $a / $b"` this scale that floating point at least 2 numbers after `.`

```bash
#!/bin/bash
A=4
B=3
result=$(echo $A / $B | bc -l) # output = 1.333333

# Scaling the Floating point
result=$(echo "scale=2;$A / $B" | bc)  # output = 1.33


```

## 1.5 Supported Arthimetic operations

- Addition example: $((a + b))
- Subtraction example: $((a - b))
- Multiplication example: $((a * b))
- Integer Division examlpe: $((a / b)) Performs integer division
- Floating-Point Division example: echo "$a / $b" | bc -l Returns decimal result
- Modulus example: $((a % b)) Returns remainder
- Exponentiation example: $((a ** b)) Computes power



