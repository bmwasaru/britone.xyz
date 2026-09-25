---
layout: post
title: "Swahili text normalizer"
date: 2026-08-21 20:43:54
categories: ["data", "python", "tools"]
---

One of the challenges with working with text corpus, that will be used for voice datasets, is that you will encounter non-standard text like percentages, numbers, time and date. These can be a challenge when one has to read them. For example 23 could be read as twenty three or two three. To fix such an issue you do what is called text normalization during the cleaning and validation stage for your text corpus. This is helpful especially when your text corpus will be used for speech use cases.


> Text normalization in speech applications converts written, non-standard text (like numbers, symbols, and abbreviations) into spoken-word forms for text-to-speech (TTS), or structures raw audio transcripts into clean data for automatic speech recognition (ASR)



During my fellowship with Mozilla Foundation working on the common voice text corpus for Kiswahili, this is something I encountered during the sentence validation stage. On the common voice platform, one way one can contribute to building the Swahili voice dataset is to read sentences in the Swahili language. The sentences went through a validation stage before they were ready for reading. You can see that encountering something like 3.5% might slow the reader (silence in the voice clip making it longer) or present a challenge of how to read the percentage. For English you can use already existing natural language processing tools to do text normalization.



I spent some time working on a small library for the Swahili language. Its a small collection of utilities that convert:



* Numbers to words (`0` .. `< 1e9`)
* Years, dates, times to words
* Decimals, percentages to words



You can find the source code here <https://github.com/bmwasaru/kiswahili-text-normalizer> and the readme file has instructions on how to install and use it. Here is an example usage:



```
>>> import kiswahili_text_normalizer as ktn
>>> text = "Tutakutane 20/11/2025 14:30, malipo ni 12.5%."
>>> print(ktn.normalize_text(text, profile="asr"))
tutakutane tarehe ishirini mwezi wa kumi na moja mwaka elfu mbili ishirini na tano 
saa nane na nusu malipo ni asilimia kumi na mbili nukta tano
```



As you can see it converts



* 20/11/2025 to tarehe ishirini mwezi wa kumi na moja mwaka elfu mbili ishirini na tano
* 14:30 to saa nane na nusu
* 12.5% asilimia kumi na mbili nukta tano



You will note it adds keywords like tarehe to denote date, saa to denote time, nukta to denote decimal point and asilimia to denote percentage.



I have used this on text that I had scrapped from the Voice of America Swahili news website before it shutdown. The code for that can be found here `https://github.com/bmwasaru/voa/blob/main/scripts/normalize_text.py`. This was a perfect use case because this was a large text corpus and the normalizer was able to quickly find and convert. Side note, if you are looking for Swahili language text you can find the scraped text in cvs files here `https://github.com/bmwasaru/voa/tree/main/sentences`.



I hope one finds this useful and please share some feedback :)