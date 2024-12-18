grep -E '\b[3-9][0-9]{2,}|\b[1-9][0-9]{3,}\b' filename


grep -E '[5-9][0-9][0-9] ms\.|[1-9][0-9]{3,} ms\.' example.txt


grep -E '\b([5-9][0-9][0-9]|[1-9][0-9]{3,}) ms\.' filename
tc qdisc add dev eth0 root tbf rate 50kbit burst 32kbit latency 200ms


tc qdisc del dev eth0 root
