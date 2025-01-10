
#!/bin/bash

# Function to execute commands with options to repeat, proceed, or exit
execute_commands() {
    # Array with commands
    local commands=("ls -l" "pwd" "echo 'Hello, World!'")

    # Iterate over the array
    for command in "${commands[@]}"; do
        while true; do
            echo "Executing command: $command"
            eval "$command"
            
            # Prompt the user for the next action
            echo "The command has been executed. What would you like to do?"
            echo "1. Repeat"
            echo "2. Proceed to the next"
            echo "3. Exit"
            read -rp "Enter the number of your choice: " action

            case $action in
                1) 
                    # Repeat the command
                    echo "Repeating the command: $command"
                    ;;
                2)
                    # Proceed to the next command
                    echo "Moving to the next command."
                    break
                    ;;
                3)
                    # Exit the script
                    echo "Exiting."
                    return 0
                    ;;
                *)
                    echo "Invalid input. Please try again."
                    ;;
            esac
        done
    done

    echo "All commands have been executed."
}

# Call the function
execute_commands
