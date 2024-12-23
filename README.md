grep -E '\b[3-9][0-9]{2,}|\b[1-9][0-9]{3,}\b' filename


grep -E '[5-9][0-9][0-9] ms\.|[1-9][0-9]{3,} ms\.' example.txt


grep -E '\b([5-9][0-9][0-9]|[1-9][0-9]{3,}) ms\.' filename
tc qdisc add dev eth0 root tbf rate 50kbit burst 32kbit latency 200ms


tc qdisc del dev eth0 root

#!/bin/bash
USER="sidadm"

echo "Диалоговые процессы (DIA): $(ps -u $USER | grep -i 'DIA' | wc -l)"
echo "Фоновые процессы (BTC): $(ps -u $USER | grep -i 'BTC' | wc -l)"
echo "Обновляющие процессы (UPD): $(ps -u $USER | grep -i 'UPD' | wc -l)"

