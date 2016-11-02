# Dynamic Information Syndication
动态信息聚合  **0.0.2**  
Dynamic Information Syndication standard based on [RSS](https://cyber.harvard.edu/rss/rss.html) and [Atom](https://tools.ietf.org/html/rfc4287).  
The specification might change in the future.  


<!-- toc orderedList:0 -->

- [Dynamic Information Syndication](#dynamic-information-syndication)
	- [Introduction](#introduction)
	- [DIS](#dis)
	- [Feed](#feed)
		- [Types of the feed](#types-of-the-feed)
	- [Tags](#tags)
	- [One-Hour Rule](#one-hour-rule)
	- [Example](#example)
	- [Common Site API](#common-site-api)

<!-- tocstop -->


---

## Introduction  

ALL **DIS** (dynamic information syndication) should conform **JSON** specification.  

<strike> DIS document should have a mandatory field called `version` that specify the version of DIS that the document conforms to. </strike> **will be defined in the future.**  

## DIS   
| Element  | Description | Example |  
|---|---|---|
| **title** | The name of the DIS service | UIUC CS411 course tracker |
| **updated** | The update date of this DIS | Sat Oct 15 2016 15:11:55 GMT-0500 (CDT) |
| link | Thr URL to the HTML website | https://courses.illinois.edu/schedule/2016/fall/CS/411 |  
| description | Phrase or sentence describing the channel | Track the open/close status of UIUC CS411 |  
| image | image of this DIS | |  
| author | author of this DIS | |  
| feeds | Array of **feed** ||

*bold means required*

## Feed
| Element | Description | Example |
|---|---|---|
| **id** | global unique identifier within the DIS | hSy7812 |
| **updated** | Indicate when the feed was updated | Sat Oct 15 2016 15:11:55 GMT-0500 (CDT) |
| **type** | type of the feed | 'text' & 'article' |
| **content** | content of the feed | |

### Types of the feed
* type: **article**    
content:    

| Element | Description | Example |  
|---|---|---|
| title | title of the article | 为什么我这么帅? |
| link | link that this article should refer to | |
| html | html content | |
| markdown | markdown content | |  
only one of `html` and `markdown` can be defined.  

* type: **text**    
content:  

| Element | Description | Example |    
|---|---|---|  
| text | the content of the feed | |   
| photos | array of photo urls | |   
| videos | array of video urls | |  

## Tags   
tags are got from `description`, `html`, `markdown`, `text`.  
tags should be defined as `#tag{content}`  

## One-Hour Rule  
You can't remove a feed from your dis document until after 60 minutes.

## Example  
```json
{
  "title": "UIUC CS411",
  "link": "https://courses.illinois.edu/schedule/2016/fall/CS/411",
  "updated": "Sat Oct 15 2016 15:38:49 GMT-0500 (CDT)",
  "description": "#tag{UIUC}, #tag{courses}, #tag{CS411}",
  "feeds": [
    {
      "id": "h123hj23",
      "updated": "Sat Oct 15 2016 15:38:49 GMT-0500 (CDT)",
      "type": "text",
      "content": {
        "text": "CS411 course opened https://courses.illinois.edu/schedule/2016/fall/CS/411"
      }
    }
  ]
}
```

## Common Site API
**(not required but recommended)**  

`count`  
Get `<= count` number of feeds    
`-1` means get all,  
`0` means get 0.

`page`  
eg: `?page=0&count=5` get 0~4 (inclusive) feeds  
eg: `?page=1&count=5` get 5~9 (inclusive) feeds  

eg:  
`newty.com/dis/uiuc-cs411?count=10&page=0`  
