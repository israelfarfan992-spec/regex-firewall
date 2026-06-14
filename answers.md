## Task 1

Command:
```bash
grep -Ec '^[0-9]' firewall.log
```

Result:
100000

Explanation:
The ^ anchor matches the beginning of the line and [0-9] matches any digit. Since the header lines start with # and the event lines start with a date, only the firewall events are counted.
## Task 2

Command:
```bash
grep -Ec ' (DROP|REJECT) ' firewall.log
```

Result:
60156

Explanation:
The parentheses create a group and the | operator means OR, so it matches DROP or REJECT. The spaces around the group ensure that only the action field is matched.
```
