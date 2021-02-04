# Basic DNS Server with dynamic updates

## Starting
```
docker-compose up
```

## Making queries
```
# Basic Query:
dig @localhost www0.example.local

# www is a CAME pointing to www0
dig @localhost www.example.local

# Look ma - recursive DNS
dig @localhost moodle.org
```

## Making updates
You'll need nsupdate (or rndc)

```
# Basic Query:
dig @localhost www0.example.local

# To update:
nsupdate -l -k etc/bind/rndc.conf

# From nsupdate:
update delete www0.example.local A
update add www0.example.local 5 A 127.0.1.1
send
quit

# Query again:
dig @localhost www0.example.local
dig @localhost www.example.local
```
