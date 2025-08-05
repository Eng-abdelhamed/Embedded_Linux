# Understanding the Control Flow If Condiiton



- **examble For The Structure of the If Condition syntax in BASH**
    ```bash
    #!/bin/bash
    if [ condition ]; then
        #execute block of code
    elif [ condition ]; then
        #execute block of code
    else
        # execute block of code
    fi
    ```
 - Spaces around [ and ] are required, otherwise the script will fail.


|    Operators | Description|
|--------|---------------|
`=`      | **strings are equal**
`!=`     | **Strings are not equal**
`-z`     | **Strings are Empty**
`-n`     | **Strings are not Empty**


- ***Syntax for String comparison***

```bash
#!/bin/bash
if [ $string1 = $string2 ]; then
    echo " Strings Are Eqaul "
elif [ $string1 != $string2 ]; then
    echo " Strings are Not Equal "
fi
````


```bash
#!/bin/bash
if [ -z $var ]; then
    echo " Var is empty "
elif [ -n $var ]; then
    echo "Var is not empty"
fi
```


## 1.2 Numeric Comparison work wih `[]`  and not with Strings

|    Operators | Description|
|--------|---------------|
`-eq`     | **equal**
`-ne`     | **not equal**
`-gt`     | **greater than**
`-ls`     | **less than**
`-ge`     | **greater than or equal**
`-le`     | **less than or equal**

- **Examble**

```bash
#!/bin/bash
if [ $num1 -eq $num2 ]; then
    echo "the Numbers Are equal " 
elif [ $num1 -ne $num2 ]; then
    echo " The numbers not equal " 
fi

```

## 1.3 Conditional Operators for String Matching

|    Operators | Description|
|--------|---------------|
`[[ "abcd" = *ab* ]]`     | **check if `abcd` contain `ab`**
`[[ "abc" =  ab[cd] ]]`     | **check if the third char of `abcd ` is `c` or  `d`**
`[[ "abc" < "bcd" ]]`     | **check if `abc` is come before  `bcd` lexiographicalyy**
`[[ "abc" > "vfg" ]]`     | **check if `abc` is come after   `vfg` lexiographicalyy**








