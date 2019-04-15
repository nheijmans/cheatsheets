## Cheatsheet: Wireshark/tshark
### General
#### get unique mac addresses with belonging IP’s 
``` tshark -r capture.pcap -Y 'ip.src >= iprange and ip.src <= iprange’  -T fields  -e eth.src -e ip.src | sort | uniq -c ```

#### get the hostname
``` tshark -r capture.pcap -Y 'dns' -T fields -e ip.host | head ```

#### scope to frames
```tshark -r capture.pcap -Y 'frame.number > X && frame.number < Y ```

### HTTP
#### get all URL’s requested by a system filtered on IP address
``` tshark -r capture.pcap -Y 'http and ip.src == ipaddr or ip.dst == ipaddr' -T fields -e ip.src -e ip.dst -e http.request.full_uri -e http.referer -e http.response.code -e http.content_type | less ```


### SMB
#### filter out all files occuring in the pcap
```tshark -n -r capture.pcap -Y '(smb.cmd == 0xa2 && (smb.fid == 0)) && (ip.addr == 10.3.58.7 && ip.addr == 10.3.58.6)' -T fields -e frame.time -e ip.src -e ip.dst -e smb.path -e smb.file | head ```

### SSL
#### filter out ssl handshake ciphers
```tshark -n -r capture.pcap -Y 'ssl.handshake.type == 1' -T fields -e ip.src -e ssl.record.version -e ssl.handshake.ciphersuite > ssl_by_ip.txt```

#### extract the ssl handshake
```tshark -n -r capture.pcap -Y 'ssl.handshake.certificate' -T fields -E separator=\| -E aggregator=\| -e x509ce.dNSName -e x509sat.teletexString -e x509sat.uTF8String -e x509sat.universalString -e x509sat.IA5String | tr -s \| '\n' | sort | uniq -c | sort -nr > ssl_handshake_output.txt```
