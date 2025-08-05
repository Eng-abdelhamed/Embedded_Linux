# Understanding `Case` Statement in Bash 


- The `case statement` in Bash is a **control structure** used to execute different blocks of code based on pattern matching. It is a cleaner and more efficient alternative to multiple `if-elif-else` conditions when handling a fixed set of options.

**Basic Syntax :**

```bash
    case variable in
    pattern1)  
        # Commands to execute if pattern1 matches  
        ;;
    pattern2|pattern3)  
        # Commands to execute if pattern2 or pattern3 matches  
        ;;
    *)  
        # Default case if none of the patterns match  
        ;;
    esac
```

# Pattern Matching In `Case`

- Unlike if conditions, case uses **pattern matching** instead of exact comparisons. Common pattern matching symbols include:

    - `*` → Matches zero or more characters.
    - `?` → Matches exactly one character.
    - `[abc]` → Matches any single character inside the brackets.
    - `[a-z]` → Matches any lowercase letter within the specified range.

#
```bash
    read -p "Enter a letter : " letter

    case $letter in
    a) echo "You entered 'a'";;
    b|c) echo "You entered 'b' or 'c'";;
    [d-f]) echo "You entered a letter between d and f";;
    ?) echo "You entered a single character";;
    *) echo "Unknown input";;
    esac
```
#
# Extended Pattern Matching

- By default, case does not support **complex regex patterns**. However, Bash **allows enabling extended pattern** matching using:
```bash
    shopt -s extglob  # Enable advanced pattern matching    
    export LC_COLLATE=C # to enable case sensitive in REGEX .
```

**Extended pattern matching operators include:**
```bash
    @(pattern1|pattern2|pattern3) → Matches one of the patterns.
    !(pattern) → Matches anything except the specified pattern.
    ?(pattern) → Matches zero or one occurrence.
    *(pattern) → Matches zero or more occurrences.
    +(pattern) → Matches one or more occurrences.
```

**Example:**
```bash
    shopt -s extglob  # Enable advanced pattern matching

    read -p "Enter a filename: " file  

    case $file in
    *.@(jpg|png|gif)) echo "This is an image file";;
    *.@(mp4|mkv|avi)) echo "This is a video file";;
    !(*.*)) echo "This file has no extension";;
    *) echo "Unknown file type";;
    esac
```
#
# Performance Considerations

   -  case is generally faster than multiple if conditions when checking against multiple fixed values. It is faster and more readable compared to multiple if conditions
  - if statements are better suited for complex numerical comparisons or logical evaluations.

**Performance Comparison Example : **

**Using if:**
```bash
    if [ "$var" = "apple" ] || [ "$var" = "banana" ] || [ "$var" = "cherry" ]; then
        echo "Fruit detected"
    fi
```
**Using case:**
```bash
    case $var in
        apple|banana|cherry) echo "Fruit detected";;
    esac
```
**The case version is cleaner and more efficient.**


<?php
// Function to load environment variables from a .env file
function loadEnv($path)
{
    if (!file_exists($path)) {
        return false;
    }

    $lines = file($path, FILE_IGNORE_NEW_LINES | FILE_SKIP_EMPTY_LINES);
    foreach ($lines as $line) {
        if (strpos(trim($line), '#') === 0) {
            continue;
        }

        list($name, $value) = explode('=', $line, 2);
        $name = trim($name);
        $value = trim($value);
        putenv(sprintf('%s=%s', $name, $value));
    }
    return true;
}

// Load environment variables from .env file
loadEnv(__DIR__ . '/file.env');

// Retrieve the database connection details from environment variables
$dbHost = getenv('DB_HOST');
$dbUser = getenv('DB_USER');
$dbPassword = getenv('DB_PASSWORD');
$dbName = getenv('DB_NAME');

?>

ON a multi-node setup, remember to provide the IP address of the database server in the .env file.

