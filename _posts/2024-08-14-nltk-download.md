---
layout: post
title: "nltk.download"
date: 2024-08-14 15:06:30
categories: ["python"]
---

Was working on some sentences and needed to download the 'punkt' nltk (natural language toolkit) data file but encountered the following issue:



```
[nltk_data] Error loading punkt: <urlopen error [SSL:
[nltk_data]     CERTIFICATE_VERIFY_FAILED] certificate verify failed:
[nltk_data]     unable to get local issuer certificate (_ssl.c:1000)>
```



This seemed to be a ssl issue. So I run this command:



```
sh "/Applications/Python 3.12/Install Certificates.command"
```



Which installed certifi



```
-- pip install --upgrade certifi
Collecting certifi
  Using cached certifi-2024.7.4-py3-none-any.whl.metadata (2.2 kB)
Using cached certifi-2024.7.4-py3-none-any.whl (162 kB)
Installing collected packages: certifi
Successfully installed certifi-2024.7.4
```



Then attempted download of the nltk data files via the terminal:



```
python3 -c ""import nltk;nltk.download('punkt')"
```