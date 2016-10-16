# Dynamic Information Syndication
**0.0.1**  
Dynamic Information Syndication standard based on RSS.  
The specification might change in the future.  


<!-- toc orderedList:0 -->

- [Dynamic Information Syndication](#dynamic-information-syndication)
	- [Introduction](#introduction)
	- [channel elements](#channel-elements)
	- [Item](#item)
	- [Example](#example)
	- [Common Site API](#common-site-api)

<!-- tocstop -->


---

## Introduction  

ALL **DIS** (dynamic information syndication) should conform **JSON** specification.  

<strike> DIS document should have a mandatory field called `version` that specify the version of DIS that the document conforms to. </strike> **will be defined in the future.**  

## channel elements   
| Element  | Description | Example |  
|---|---|---|
| **title** | The name of the DIS service | UIUC CS411 course tracker |
| link | Thr URL to the HTML website | https://courses.illinois.edu/schedule/2016/fall/CS/411 |  
| description | Phrase or sentence describing the channel | Track the open/close status of UIUC CS411 |  
| **pubDate** | The publish date of this DIS | Sat Oct 15 2016 15:11:55 GMT-0500 (CDT) |
| items | Array of **Item** ||  

*bold means required*

## Item
| Element | Description | Example |
|---|---|---|
| title | The title of item | UIUC CS411 |  
| pubDate | Indicate when the item was published | Sat Oct 15 2016 15:11:55 GMT-0500 (CDT) |
| id | the unique id of the item | 1ha789 |
| author | the author of the item | shd101wyy |
| image | image related to author | |    
| link | link related to author | https://github.com/shd101wyy |
| text | the content of item | The class is opened |  
| photos | array of photo urls | |  
| videos | array of video urls | |  
| markdown | markdown content | |   

## Example  
```json
{
  "title": "UIUC CS411",
  "link": "https://courses.illinois.edu/schedule/2016/fall/CS/411",
  "items": [
    {
      "title": "CS411",
      "pubDate": "Sat Oct 15 2016 15:38:49 GMT-0500 (CDT)",
      "author": "shd101wyy",
      "id": "5hjasd8",
      "text": "CS411 course opened https://courses.illinois.edu/schedule/2016/fall/CS/411"  
    }
  ]
}
```

## Common Site API
**(not required but recommended)**  

`count`  
Get `<= count` number of items    
`-1` means get all,  
`0` means get 0.

`page`  
eg: `?page=0&count=5` get 0~4 (inclusive) items  
eg: `?page=1&count=5` get 5~9 (inclusive) items  

eg:  
`newty.com/dis/uiuc-cs411?count=10&page=0`  
