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
## Task 3

Command:
```bash
grep -Ec ' 11\.' firewall.log
```

Result:
33217

Explanation:
The pattern matches a space followed by 11\. so the dot is treated as a literal character instead of a wildcard. This counts events whose source IP address begins with 11.
```
## Task 4

Command:
```bash
grep -Ec ' [0-9]{7}$' firewall.log
```

Result:
2343

Explanation:
The pattern [0-9]{7} matches exactly seven digits, and the $ anchor ensures that the match is at the end of the line. This counts packets whose size field has seven digits.
```
## Task 5

Command:
```bash
grep -E '^[0-9]' firewall.log | sed -E 's/^([0-9]{4}-[0-9]{2}-[0-9]{2}) ([0-9]{2}:[0-9]{2}:[0-9]{2}) ([A-Z]+) ([A-Z]+).*/\1 \3 \4/' | head -5
```

Result:
```text
2018-05-25 FORWARD TCP
2018-02-22 FORWARD UDP
2018-03-20 REJECT UDP
2018-11-08 REJECT TCP
2018-07-24 REJECT TCP
```

Explanation:
The grep command removes header lines by matching lines that start with a digit. The sed command uses capture groups to keep the date, action, and protocol, then rebuilds the output with backreferences.
