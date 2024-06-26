---
title: "The character garbled problem encountered by Lexus playing CD"
date: "2021-06-15"
slug: "the-character-garbled-problem-encountered-by-lexus-playing-cd"
categories: 
  - "network"
tags: 
  - "cd"
  - "chinese"
  - "lexus"
image: "images/IMG_20230415_152142-scaled-e1681543616554-jpg-1.webp"
---

> I recently encountered a tricky problem when burning a CD. On the Lexus car CD player, the Chinese music label cannot be read. Looking back now, this problem may be unsolvable at the moment. Here is just a record of the solution process:  
>   

![](images/IMG_20230415_150947-1024x584.webp)



## Burning program selection.
Before choosing to burn a CD, I searched for various burning tutorials in detail. The main difference is the choice of burning software. I have chosen Nero, Brunatonce and ImgBurn successively. Of the three, the first is old-fashioned paid software, and the second and third are free software. But Brunatonce has not been updated for more than ten years because of the developer, and the latest version stays at 0.99.5 in 2004. Although it can be used in XP compatibility mode on Windows 11, it still encounters inexplicable errors. In addition, it is said that among the three, Brunatonce is the software with the best low-speed recording effect, but since the current CD recorder has no low-speed recording, the starting point is above 10x, so it is of little significance. It is mainly recommended to use ImgBurn here. Although the program has not been updated for a long time, the developers have been answering questions online at http://forum.imgburn.com. Any questions can be answered in a short time.

##  Choose the recording method. 
That is, the existing audio assets and the burning goals that need to be achieved. There are three main ways of distinguishing:

- **a. Choice of audio CD and music CD**. Among them, audio CD refers to the lossless analog audio format \*.cda reversed through the WAV format, which is non-digital music, and all CD records purchased by default are in this format. Music CD is a digital music format, and generally supports compressed music formats such as mp3/wma/aac. As far as 2022 is concerned, burning CDs generally pursues the former, and the effect of the latter will not be much better than listening to music via Bluetooth.
- **b. Selection of audio CD resources**. There are generally three music formats that can be burned as audio CDs: WAV, FLAC, and APE. And the music file of the same format has the difference of full track and split track, that is, a single CD is a whole file of about 400-700MB, or more than 10 single files of about 30-50MB. If it is downloaded from Ziyuan.com, most of the files are whole tracks, but on platforms such as QQ Music, only single tracks can be downloaded, and the entire CD cannot be downloaded as a file. It is generally recommended to choose the whole track file to burn. On the one hand, there is no need to worry about the insufficient capacity of the CD. On the other hand, the whole track file usually comes with a CUE file, or the format of ape can also be directly extracted from the CUE file through foobar2000. When burning a combination of self-selected songs, the main thing to be calculated is the CD capacity, which generally should not exceed 750MB.
- **c. Audio CD-TEXT production**. As mentioned above, audio CD is an analog music format launched in 1982. At that time, CDs were the same as song tapes, and it was impossible to record song information. However, in 1995, Sony and Philips launched the CD-TEXT standard, which can embed CD-related track information at the beginning of the CD file. After that, Jeff Arnold developed the CUE Sheet file on the basis of CD-TEXT in 1997, and it has been followed by almost all Mainstream player support. Of course, this is the problem, whether it is the CD-TEXT standard_.cdt file, or follow-up_.cue files, in the Windows 95 era in the 1990s, almost never considered supporting Chinese natively. The former \*.cdt file only supports ASCII (English letters), 8859 (English and European letters), MS-JIS (some Japanese characters) three character encodings, while the latter CUE only supports ANSI character encodings. Among them, the ANSI encoding is the most pitted. This encoding is automatically recognized as ASCII in North America, automatically converted to GB2312 in mainland China, and automatically converted to Shfit-JIS in Japan. That is, if an ANSI-encoded CUE file is made on a Windows computer set to the Chinese environment, it will be garbled when opened on a Windows computer under the English environment.

_The biggest problem I encountered this time is that the Lexus CD player does not support the GB2312 mode ANSI in mainland China, so if the current cue file recording method is used, it will inevitably be garbled when encountering Chinese. Unless the cdt file editing mode is adopted, there are almost no ready-made cdt file editors on the Internet. Even though NERO can write cd-text files, it still uses the \*.nra files developed by NERO to convert, and the actual test has no effect . The only way I can find out is to use Sony’s official cdt editor released in 1995 to edit, but if you want to insert Chinese, you can only edit in Windows 95 in the MS-JIS Japanese environment, with the help of 2500 A Chinese character commonly used in Japanese is realized. This method is a bit too frustrating. When I was discussing with the developer of ImgBrun, he also suggested that I should give up._

## Burning process ideas.
When I found garbled characters in the first recording, I searched all the information about CUE files in the Chinese circle, and came to three conclusions:

- a. CUE must use ANSI format;
- b. ANSI codes are different in different regions (as above "2.");
- c. When the burned CD is played on the computer, unless a special plug-in is used, the effect of Chinese CD-TEXT cannot be seen generally. For example, in Foobar2000, it is displayed as garbled characters.

When burning for the second time, I chose to install a hyper-v virtual machine to test the cue file encoding problem in the English Windows 11 environment, and found three problems:

- a. Chinese ANSI-encoded files are displayed as garbled characters in the English environment (as above "2.");
- b. The UTF-8 encoding opened in Notepad on Windows 11 is not the same as the UTF-8 encoding opened in Windows XP Notepad. UTF-8 in XP corresponds to UTF-16 LE in Windows 11. It is more obvious in ImgBurn, only the cue file converted to UTF-16LE can be loaded normally in ImgBurn in English environment, otherwise it will be displayed as garbled characters.
- c. Although the CUE file encoded with UTF-16 LE can be recognized by ImgBurn, it is impossible to successfully engrave the CUE file with this encoding, because the CUE file itself only supports ANSI encoding, even if you choose to recognize UTF-16 in ImgBurn After LE encodes the file to force the output of ANSI, it is also displayed as garbled characters.

## Summary.

CDs are a thing of the past. Nowadays, whether it is U disk, mobile phone Bluetooth or CarPlay, HiCar, CarLife and other connection modes, they are many times more convenient and easier to use than CDs. As a technology that can be called outdated, it is very difficult to seek technical support now. What is rare is that in the process of solving the problem, I still encountered a lot of useful information on the Internet. For example, I searched on Japanese websites and found hundreds of pages of discussions on how CD-TEXT supports Japanese in 2002. I saw developer 20 on ImgBurn. Year after year, I have been silently giving support to niche users. On the official websites of GNU and SONY, the links to technical documents from nearly 30 years ago are still well preserved. In comparison, it is really difficult to search for useful information on the Chinese Internet. Not to mention whether the links on the web pages 20 years ago can be opened normally, the normal search information is not right. No reason was found. For example, in many Chinese technical documents about CUE, it is shown that CD-text files support 8 languages, but which 8 languages are supported specifically, whether they contain Chinese codes, there is no place to find information, and the source of this statement is found through English searches. It is a technical manuscript on GNU, which is basically copied from the original text, but the technical manuscript on GNU gives an accurate source of evidence, that is, the official document on SONY DADC, from which it is found that the so-called 8 languages, except Japanese, other All are English, German, French and other European languages, excluding Chinese. Just stopped thinking about it.
