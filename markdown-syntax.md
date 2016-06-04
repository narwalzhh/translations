#Standard Markdown

##Strong and Emphasize
```
*emphasize* **strong** ***emphasize and strong***
_emphasize_ __strong__ ___emphasize and strong___
```

*emphasize* **strong** ***emphasize and strong***
_emphasize_ __strong__ ___emphasize and strong___

##Link and Email
Inlines:
```
An [example](http://url.com/ "title")
```

[百度链接](http://www.baidu.com "百度")

Reference-style lables (titles are options)
```
An [example] [id].Then,anywhere else
in the doc, define in link:
    
    [id]: http://example.com/ "title"
```

[这是百度链接][002]
[002]: http://www.baidu.com" "百度"

Email
```
An email <example@example.com> link.
```

<zhanghui921313@gmail.com>

##Images
Inline (titles are options)
```
![alt text](/path/img.jpg "Title")
```

![图片在哪里](/path/img.jpg "图片")

Reference-style
```
![alt text][id]
[id]: /url/to/img.jpg "titile"
```

![图片在这里][007]
[007]: /url/to/img.jpg "这就是图片"


##Headers
```
setext-sytle
Header 1
======
Header 2
------
```

Header1 
======
Header 2
------

atx-style(closing # is optional)
```
#Header1#
##Header2##
######Header6######
```

#Header1#
##Header2##
######Header6######

##Lists
Ordered, without paragraphs
```
1. foo
2. bar
```

1. foo
2. bar

Unordered, with paragraphs
```
*   A list item
    with multiple paragraphs
*   Bar
```

*   A list item
    with multiple paragraphs
*   Bar

You can nest them
```
*   Abacus
    *   answer
*   Bubbles
    1.  bunk
    2.  bupkins
        *   belittler
    3.  burper
*   Cunning
```

*   Abacus
    *   answer
*   Bubbles
    1.  bunk
    2.  bupkins
        *   belittler
    3.  burper
*   Cunning

##Blockquotes
```
> Email-style angle brackets
> are used from blockquotes
> > And, they can be nested.
> ### Headers in blockquotes
> 
> * you can quto a list
> * Etc.
```

> Email-style angle brackets
> are used from blockquotes
> > And, they can be nested.
> ### Headers in blockquotes
> 
> * you can quto a list
> * Etc.

##Inline Code
```
`<code>` spans are delimited
by backticks.
you can include literal backticks
like ```this```.
```

`variables`

```
public class Tmp {
    public static void main() {
        System.out.println("hello world !");
    }    
}
```

##Block code
Indent every line of a code block by at least 4 spaces or 1 tab
```
This is a normal paragraph.
    This is a preformatted
    code block.
```

##Horizontal Rules
Three or more dashes or asterisks
```
---
* * * 
- - - - 
```

---
* * * 
- - - - 

##Hard Line Breaks
End a line with two or more spaces
```
Roses are red,   
Violets are blue.  
```

Roses are red,  
Violets are blue.  

##Delete lines
```
~~delete line~~
```

~~delete line~~ 
