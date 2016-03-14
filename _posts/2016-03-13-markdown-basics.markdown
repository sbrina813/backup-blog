---
layout: post
title:  "Markdown basics"
date:   2016-03-12
categories: front_end
---

## Markdown Basics 

>Extract from markdownPreview plugin cheatsheet of sublime and [Jianshu](http://www.jianshu.com/p/2accf6447311)

#### Text basics

```
# Big title (h1)
## Middle title (h2)
### Smaller title (h3)
#### h4
##### h5
###### h6
```

# Big title (h1)
## Middle title (h2)
### Smaller title (h3)
#### h4
##### h5
###### h6

```
 *italic* 
 _italic_
 **bold**
 __bold__
`important`
 % and `%`
[^note-id]
 `[ TOC ]` 
```

 *italic* 
 _italic_
 **bold**
 __bold__
`important`
 % and `%`
[^note-id]
 `[ TOC ]`

#### Separation line

```
****
----
____
```

****
----
____


#### Indentation

```
> Here is some indented text
>> even more indented
```

> Here is some indented text
>> even more indented

#### Example lists

```
- bullet list 1
 - bullet list 2
    - sub item 1
    - sub item 2

 - bullet list 3
 + bullet list 4
 * bullet list 5
```

- bullet list 1
 - bullet list 2
    - sub item 1
    - sub item 2

 - bullet list 3
 + bullet list 4
 * bullet list 5

 #### Links

```
[example inline link](http://lmgtfy.com/)
[another one with a title](http://lmgtfy.com/ "Hello, world")

[reference 1][ref1] or [reference 2 with title][ref2]
References are usually placed at the bottom of the document.
```

[example inline link](http://lmgtfy.com/)
[another one with a title](http://lmgtfy.com/ "Hello, world")
[reference 1][ref1] or [reference 2 with title][ref2]
References are usually placed at the bottom of the document.

#### Images

```
![revolunet logo](http://www.revolunet.com/static/parisjs8/img/logo-revolunet-carre.jpg "revolunet logo")
![revolunet logo][revolunet-logo]
```

![revolunet logo](http://www.revolunet.com/static/parisjs8/img/logo-revolunet-carre.jpg "revolunet logo")
![revolunet logo][revolunet-logo]


#### Code

'with tab indentation' or '4 spaces'
```
    <script>
        document.location = 'http://lmgtfy.com/?q=markdown+cheat+sheet';
    </script>
```


    <script>
        document.location = 'http://lmgtfy.com/?q=markdown+cheat+sheet';
    </script>


- ```js   
- ```python

#### Emoji

```
:+1: :heart: :beer: :smile:
```

![emoji cheatsheet](http://www.emoji-cheat-sheet.com/)
:+1: :heart: :beer: :smile:

#### Tables

```
| Year | Temperature (low) | Temperature (high) |  
| ---- | ----------------- | -------------------|  
| 1900 |               -10 |                 25 |  
| 1910 |               -15 |                 30 |  
| 1920 |               -10 |                 32 |  
```

| Year | Temperature (low) | Temperature (high) |  
| ---- | ----------------- | -------------------|  
| 1900 |               -10 |                 25 |  
| 1910 |               -15 |                 30 |  
| 1920 |               -10 |                 32 |  


```

|| *Year* || *Temperature (low)* || *Temperature (high)* ||  
||   1900 ||                 -10 ||                   25 ||  
||   1910 ||                 -15 ||                   30 ||  
||   1920 ||                 -10 ||                   32 ||  

```


|| *Year* || *Temperature (low)* || *Temperature (high)* ||  
||   1900 ||                 -10 ||                   25 ||  
||   1910 ||                 -15 ||                   30 ||  
||   1920 ||                 -10 ||                   32 ||  




































