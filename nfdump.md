## Cheatsheet: nfdump
#### top 10 source ips sorted on flows
```nfdump -s srcip -r capturefile```

#### top 10 source ips sorted on bytes 
```nfdump -s srcip/bytes -r capturefile```

#### export nfdump captures to one csv file
```time nfdump -R /path/to/files -o csv > output.csv```

#### search netflow for connections from src host to any destination host in the list []
```nfdump -R netflow/subdir/ -A proto,dstip,dstport -O tstart -o 'fmt:%ts %te %da %pr/%dp %pkt %byt' \
‘src host $src and dst host in [$dst1 $dst2]'
```

