# Why Use Shell Scripts?

- **Automate daily backups** to save time and ensure consistency  
- **Install and patch software** across multiple servers efficiently  
- **Monitor system health** at regular intervals without manual checks  
- **Raise alarms and send notifications** when thresholds are crossed  
- **Troubleshoot issues and perform audits** quickly using scripted commands  

---

## 1 - Variables in Bash

- Bash is a dynamically typed language. Variables are treated as strings by default but can behave like numbers in arithmetic operations.  
- Variables allow you to **store and reuse** data across a script.
- They make scripts **dynamic**, **flexible**, and **reusable**.
- A variable is accessed using a **`$`** before its name.
- Variable names can only contain **letters, digits, or underscores (`_`)**.
- Variable names are **case-sensitive**.

---

##  Types of Variables in Bash

### 1. **Local Variables**

- Defined **within a function** and accessible **only inside** that function.

#### Example:
```bash
my_function() {
  local var="I am local"
  echo $var
}
```

---

### 2. **Global Variables**

- Default type in Bash (declared outside a function).
- Accessible **throughout the script**.

#### Example:
```bash
var="Ahmed"
echo $var   # Output: Ahmed
```

---

### 3. **Environment Variables**

- Used to **pass information** from the shell to programs.
- Available to all subprocesses of the shell.

#### Example:
```bash
export PATH=$PATH:/custom/path
echo $PATH
```

> ⚠️ **Note:** Do not use a `$` when assigning the variable name in `export`.  
> ✅ Correct: `export PATH=$PATH:/custom/path`  
> ❌ Incorrect: `export $PATH=...`

---

# Declaring Variables and Data Types Using `declare`

The `declare` command in Bash provides enhanced control over variables and their data types.

## Common `declare` Options and Examples

### 1. **String (default)**

```bash
declare var="Abdelhamed"
echo "Hello, $var"  # Output: Hello, Abdelhamed
```

---

### 2. **Integer**

```bash
declare -i num=42
echo $((num + 10))  # Output: 52
```

---

### 3. **Indexed Array**

```bash
declare -a names=("Abdo" "Ahmed" "Omar")
echo ${names[0]}  # Output: Abdo
```

> ✅ **Note:** Don't use commas between elements.

---

### 4. **Associative Array** (Bash 4.0+)

```bash
declare -A colors
colors[apple]="red"
colors[banana]="yellow"
echo ${colors[apple]}  # Output: red
```

---

### 5. **Readonly Variable**

```bash
declare -r pi=3.14
echo $pi  # Output: 3.14
# pi=3.15  → This will give an error since it's readonly.
```

---

### 6. **Exported Variable**

```bash
declare -x USERNAME="admin"
echo $USERNAME  # Output: admin
```

This makes the variable available to child processes.

---

### 7. **Trace/Debug Variable Assignment**

```bash
declare -t myvar="test"
# This enables a trace whenever the variable is assigned (for debugging)
```

---

### 8. **Lowercase / Uppercase Conversion**

```bash
declare -l small="HELLO"
echo $small  # Output: hello

declare -u big="hello"
echo $big    # Output: HELLO
```

---

## Summary Table of `declare` Options

| Option | Description                        |
|--------|------------------------------------|
| `-i`   | Integer                            |
| `-a`   | Indexed array                      |
| `-A`   | Associative array                  |
| `-r`   | Read-only                          |
| `-x`   | Export (like environment variable) |
| `-t`   | Trace/debug on assignment          |
| `-l`   | Convert value to lowercase         |
| `-u`   | Convert value to uppercase         |

---


`echo` is a built-in command used to display messages, variables, and outputs in Bash.

---

### 📌 Common Options for `echo`

| Option | Description | Example | Output |
|--------|-------------|---------|--------|
| `-n`   | Do not print the trailing newline | `echo -n "Hello"` | `Hello` |
| `-e`   | Enable interpretation of backslash escapes | `echo -e "Line1\nLine2"` | Line1<br>Line2 |
| `-E`   | Disable escape characters (default) | `echo -E "Hello\nWorld"` | `Hello\nWorld` |

---

### 🔠 Backslash Escape Sequences with `-e`

| Sequence | Description | Example | Output |
|----------|-------------|---------|--------|
| `\n`     | New line     | `echo -e "A\nB"`     | A <br> B |
| `\t`     | Horizontal tab | `echo -e "A\tB"`   | A  B |
| `\r`     | Carriage return | `echo -e "123\rABC"` | ABC |
| `\\`     | Backslash     | `echo -e "\\"`     | \ |
| `\"`     | Double quote  | `echo -e "\"Hi\""` | "Hi" |
| `\a`     | Alert (bell) | `echo -e "\a"` | 🔔 (sound) |
| `\b`     | Backspace     | `echo -e "123\b4"` | 124 |
| `\c`     | Suppress further output | `echo -e "Hi\cBye"` | Hi |

---

### 🧪 Examples

#### ➤ Display with no newline

```bash
echo -n "Loading..."
sleep 1
echo "Done!"
```

#### ➤ Colored Output (ANSI Escape Sequences)

```bash
echo -e "\e[31mError:\e[0m Something went wrong"
echo -e "\e[32mSuccess:\e[0m Everything is fine"
```

> ✅ `\e[31m` = red, `\e[32m` = green, `\e[0m` resets the color

#### ➤ Write to a file

```bash
echo "Backup completed" > log.txt       # overwrite
echo "New entry" >> log.txt             # append
```

#### ➤ Combine with commands

```bash
echo "Current user is: $(whoami)"
```

---

### ⚠️ Notes

- `echo` behavior may vary slightly between shells (`bash`, `dash`, `sh`, etc.).
- For advanced formatting, use `printf` instead of `echo`.

---



```bash
string="HelloWorld"

echo ${string:0:5}  # Hello
echo ${string:5}    # World
echo ${string}      # HelloWorld
echo ${string:-1:0} # HelloWorld
```

> Prepared with ❤️ for Bash learners.
