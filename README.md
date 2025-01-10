#!/bin/bash

# Function to execute commands with options to repeat, proceed, or exit
execute_commands() {
    # Array with commands
    local commands=("ls -l" "pwd" "echo 'Hello, World!'")

    # Iterate over the array
    for ((i = 0; i < ${#commands[@]}; i++)); do
        local command="${commands[i]}"
        while true; do
            echo "Executing command: $command"
            eval "$command"
            
            # Check if there's a next command
            local next_command="None"
            if ((i + 1 < ${#commands[@]})); then
                next_command="${commands[i + 1]}"
            fi

            # Prompt the user for the next action
            echo "The command has been executed. What would you like to do?"
            echo "1. Repeat the command: $command"
            echo "2. Proceed to the next command: $next_command"
            echo "3. Exit"
            read -rp "Enter the number of your choice: " action

            case $action in
                1) 
                    # Repeat the current command
                    echo "Repeating the command: $command"
                    ;;
                2)
                    # Proceed to the next command
                    if [ "$next_command" != "None" ]; then
                        echo "Moving to the next command: $next_command"
                        break
                    else
                        echo "No next command. All commands executed."
                        return 0
                    fi
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
