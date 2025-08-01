# Command Line Arguments 

- When running a **Bash script**, the input arguments are stored in special    variables:


- `$@` all the input Arguments
- `$#` The numbers of the Arguments 
- `$0` The Command Itself

    - **Exmable :**
        ```bash
            ./examble arg1 arg2 arg3

        ```
        - Here when using `$@`  it will return `arg1, arg2, and arg3`
        - When using `$#` return `3`
        - When using `$0` return `./examble`

---
## 2.2. Positional Parameters


 - **Arguments** passed to a script are processed in the same order in which they’re sent. The indexing of the **arguments** starts at one, and the first argument can be accessed inside the script using `$1`.
 freestar

 - Similarly, the s**econd argument** can be accessed using `$2`, and so on. The positional parameters refer to the representation of arguments based on their position in the command line.

As an example, let’s consider the userReg-positional-parameter.sh script, which prints positional parameter values corresponding to **Username, Age, and Full Name** in that order:

```bash 
    echo "The First Arguments : $#1"
    echo "The Sec Arguments   : $#2"
    echo "The THird Arguments : $#3"