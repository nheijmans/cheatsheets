## Cheatsheet: iptables

#### insert a rule on position 3
``` iptables -I INPUT 3 -i eth0 -p tcp —dport 22 -j ACCEPT```

#### append a rule to the chain
``` iptables -A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT```

#### delete a rule based on NUMBER
``` iptables -D INPUT 4```

#### delete ALL rules
``` iptables —flush```

#### view INPUT/OUTPUT rules
``` iptables -L```

#### view NAT rules
``` iptables -t nat -L```

#### view ALL rules with NUMBER
``` iptables -L -n --line-numbers```

#### save iptables rules
``` iptables-save > iptables.txt ```

#### restore iptables rules
``` iptables-restore < iptables.txt```

#### redirect traffic coming on a port to a different port (replace the variables with your values)
``` iptables -t nat -A PREROUTING -i eth0 -p tcp --dport $srcPortNumber -j REDIRECT --to-port $dstPortNumber ```

#### redirect access on a port to a different ip with same port
``` iptables -t nat -A PREROUTING -p tcp --dport 1111 -j DNAT --to-destination 2.2.2.2:1111 ```

#### log with the LOG option, then block/forward etc.

#### Additional reading
https://www.thegeekstuff.com/2011/01/iptables-fundamentals

