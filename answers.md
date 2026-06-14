## Task 1

Command:
```bash
grep -Ec '^[0-9]' firewall.log
```

Result:
100000

Explanation:
The ^ anchor matches the beginning of the line and [0-9] matches any digit. Since the header lines start with # and the event lines start with a date, only the firewall events are counted.
