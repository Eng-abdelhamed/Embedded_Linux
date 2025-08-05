# Understanding the For Loops In Bash

- Basix Syntax  in Bash  >> **`for...in...do...done`** 
 - `for (( ... )); do ... done` : Similar to for loops in other **programming languages (like C).**


```bash
#!/bin/bash
#  Basic Syntax
for variable in list_of_items
do

    echo " The Variables : $variable " 

done

```
- C Prog Lang Sytle 

```bash
#!/bin/bash

for ((init ; Condition ; Incremetn or Decremet))
do
    echo "Counter Value : $variable"

done
```


---
## 1.2 Iterating over a Whitespace-Separated List (in for...in):

```bash
#!/bin/bash

for lang in English Arabic Spanish do

echo " The Language are : $lang " 

done
```
---
## 1.3 Iterating over Elements in an Array (in for...in):
```bash
#!/bin/bash

Names=("Abdelhamed" "Ahmed" "mohamed")

for name in "${Names[@]}" 
do
echo " $name"

done
```

-  `${array_name[@]}` treats each element as a separate word.
 - `${array_name[*]}` treats all elements as one word, with elements        separated by the first character of the IFS variable (usually a space). It's generally safer to use [@] for iterating.

---
## 1.4 Iterating over the Output of a Command (in for...in):

- Assume We have a File include names we want to iterate over the names


```bash

for names in $(cat myFileNames.txt); do

echo " The Names inside the files is : "${names}"
done

```
---
## 1.5. Comparison with while Loops

   -  Use for when you know the number of iterations beforehand or when you have a specific list of items to process.
   -  Use while when the number of iterations is unknown and depends on a condition that might change during the loop's execution.
