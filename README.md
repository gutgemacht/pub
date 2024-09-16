reassign_params() {
    for i in {27..2}; do
        # Calculate the source variable number
        source_var_num=$((i - 2))
        
        # Reassign the variables
        eval "param${i}=\"\${param${source_var_num}}\""
    done
}
