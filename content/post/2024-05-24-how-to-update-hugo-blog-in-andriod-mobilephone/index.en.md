---
title: "How to Update a Hugo Blog on an Android Phone"
date: "2024-05-24"
slug: "How-to-Update-a-Hugo-Blog-on-an-Android-Phone"
categories: 
  - "network"
tags:   
  - "Hugo"
  - "Blog"
  - "Android"
Image: "hugo.png"
---

It is well-known that the process of publishing a blog has always been cumbersome due to the absence of backend solutions in static blog programs like HUGO, HEXO, and Jekyll. Previously, I used various methods to update my blog, but all of them required a PC.

 ## PC Method

 ### VSCODE+Github
 My initial approach was to edit in VSCODE, generate static files in the Public directory locally using the Hugo command, and then submit them to Github Pages for direct publication. Later, I found the Hugo generation process too cumbersome, so I switched to editing and directly submitting to Github, then using Github Actions to generate blog files and publish them to Github Pages.

 Since all images on this site are hosted on Github, and due to the well-known issues with the speed of accessing Github Pages, I eventually abandoned the Github Actions + Github Pages solution in favor of automatic deployment through Vercel or Cloudflare Pages.
 

 ### Obsidian+Github
Obsidian is an excellent note-taking software with a very large plugin library. With Obsidian + quickadd plugin + Git plugin, it's very convenient to directly submit blog posts to Github from Obsidian. However, the issue is that Obsidian can only publish article content and cannot modify other site settings. Managing the Posts directory of Hugo directly with Obsidian feels odd, and unless a dedicated blog repository is created, there's a constant risk of confusing note content with blog content during the management process.

### Joplin+Github
Joplin is also a very good open-source note-taking software. Although Joplin has fewer plugins, there is one that can directly publish to Github Pages, called Pages Publisher [Pages Publisher](https://github.com/ylc395/joplin-plugin-pages-publisher). However, this plugin is used by fewer people and currently only offers a very basic blog theme.

Nevertheless, all these methods inevitably require the use of a PC.



## Mobile Method

### Github Code
Github repositories allow for direct creation and modification of files. However, the inconvenience with this method is that direct access to Github from within China is not always reliable. The worst scenario is editing halfway through, only to have the page reset due to network issues. Github Codespaces faces the same issue.

![codespaces](codespaces.png)

### StackEdit
Stackedit is an excellent online Markdown editor that can be privately deployed and linked to Github repositories, with information stored in browser Cookies. I've tried editing simple information on my phone through Stackedit and submitting updates to Github. The main drawback of this method is that it cannot submit images, making it suitable only for situations where no images are needed or when using a third-party image library.

![stackedit](stackedit.jpg)

> Having suffered significant setbacks with image libraries since 2008, and upon cleaning up my Wordpress blog in 2018, I found that nearly 500 out of 900 images on the site had been lost due to issues with external image libraries. Even self-built image libraries have left me lacking confidence. Managing them separately always feels prone to problems.

### Weblog App
Weblog is an Android app that supports managing Hugo and HEXO blogs on mobile devices. It includes built-in Hugo and Hexo environments and Git, allowing for convenient blog setup, static file generation, and webpage previews on the phone. It can easily publish to Github via Git. However, due to Hexo's lower efficiency, it is recommended to use it with Hugo. The main issue with this solution is that it only supports creating MD files and does not allow uploading photos within the app. To upload photos, one must use the Android's native file manager or a third-party file management tool.

![weblog](weblog2.jpg)


### Code-server
Code-server is a VSCode-like program that can be deployed online, allowing for direct cloning of Github repositories to create blog files through a browser and submit them via Git. This solution essentially serves as a substitute for Github Codespaces. For use within Mainland China, it is recommended to set it up on a VPS in Japan, South Korea, Hong Kong, or Taiwan. Operating through a mobile browser is generally problem-free. Thanks to online deployment, it's convenient to continue writing on multiple devices. The difference lies only in server performance and connection speed. This blog post was written collaboratively on an Android phone and tablet.

![code-server](codeserver.jpg)


### Mgit App
Mgit is an Android Git application that easily pulls Github repositories to the local device, allowing for blog writing with a third-party Markdown editor. Many people use Obsidian as their blog editor and sync between their phone and computer using Mgit. The downside is that Mgit seems to have not been updated for a long time, and I encountered an issue on my Vivo X100 phone where I couldn't edit files directly within Mgit.

![mgit](weblog.jpg)

### Termux
I have not personally tried this method, but I've seen many recommendations for setting up a Linux environment within the Android system. However, if the sole purpose is to update a blog, this approach might be overkill.