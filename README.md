grep -E '\b[3-9][0-9]{2,}|\b[1-9][0-9]{3,}\b' filename


grep -E '[5-9][0-9][0-9] ms\.|[1-9][0-9]{3,} ms\.' example.txt


grep -E '\b([5-9][0-9][0-9]|[1-9][0-9]{3,}) ms\.' filename
