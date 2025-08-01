# Bash read Syntax

**Basic Read Operations**

- `-p` Outputs the prompt string before reading user input.

    ```bash
    read -p "Enter Your name : " name

    echo $name  # Your name will be output
    ```

- `-a` Assigns the provided word sequence to a variable named.


    ```bash
    read -a name        # Expected i Enter : cat dog doll
    
    echo "${name[0]}"  # cat
    echo "${name[1]}"  # dog
    echo "${name[2]}"  # doll

    ```

    ```bash

    read -p "Enter Your Full Name Please : " -a name   # abdelhamed ahmed abdlehmaed

    echo " The First name is  : ${name[0]}"  # abdelhamed
    echo " The Middle name is : ${name[1]}"  # ahmed
    echo " The Last name is   : ${name[2]}"  # abdlehmaed

    ```

- `-s` To secure the critical information, we need to use the “-s” option with the read command

    ``` bash
    read -s -p "Enter Password : " name

    echo "$name"

    ```

- `-n` we are having the functionality to restrict the specific number of characters. For restricting the number of characters, we need to use the `-n` option with the read command.

    ``` bash
    read -n 5 -p "Enter Password : " name

    echo "$name"

    ```


- `-r` To enter Backslach (PATH) Without Facing Errors 

    ``` bash
    read -r -p "Enter Path With / : " path

    echo "$path " 

    ```














---