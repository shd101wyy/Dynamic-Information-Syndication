# Dynamic Information Syndication
动态信息聚合  **0.0.1**  
Dynamic Information Syndication standard based on [RSS](https://cyber.harvard.edu/rss/rss.html) and [Atom](https://tools.ietf.org/html/rfc4287).  
The specification might change in the future.  


<!-- toc orderedList:0 -->

- [Dynamic Information Syndication](#dynamic-information-syndication)
	- [Introduction](#introduction)
	- [channel elements](#channel-elements)
	- [Feed](#feed)
	- [One-Hour Rule](#one-hour-rule)
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
| **updated** | The update date of this DIS | Sat Oct 15 2016 15:11:55 GMT-0500 (CDT) |
| link | Thr URL to the HTML website | https://courses.illinois.edu/schedule/2016/fall/CS/411 |  
| description | Phrase or sentence describing the channel | Track the open/close status of UIUC CS411 |  
| image | image of this DIS | |  
| author | author of this DIS | |  
| feeds | Array of **feed** ||
| tags | tags of this DIS. no space and case insensitive ||

*bold means required*

## Feed
| Element | Description | Example |
|---|---|---|
| **id** | global unique identifier within the DIS | hSy7812 |
| **updated** | Indicate when the feed was updated | Sat Oct 15 2016 15:11:55 GMT-0500 (CDT) |
| author | the author of the feed | shd101wyy |
| image | image related to author | |    
| link | link attached to title | https://github.com/shd101wyy |
| title | The title of feed | UIUC CS411 |  
| text | the content of feed | The class is opened |  
| photos | array of photo urls | |  
| videos | array of video urls | |  
| <strike>markdown</strike> | markdown content | |   
| html | html content | |  
| <strike>categories</strike> | category of this feed | ['bilibili', '一人之下'] |
| tags | tags of this feed. no space and case insensitive | |

`feeds` should be sorted by `updated`, from most recent to least recent.  

## One-Hour Rule  
You can't remove a feed from your dis document until after 60 minutes.

## Example  
```json
{
  "title": "UIUC CS411",
  "link": "https://courses.illinois.edu/schedule/2016/fall/CS/411",
	"updated": "Sat Oct 15 2016 15:38:49 GMT-0500 (CDT)",
	"tags": ["UIUC", "courses", "CS411"],
  "feeds": [
    {
      "title": "CS411",
      "id": "h123hj23",
      "updated": "Sat Oct 15 2016 15:38:49 GMT-0500 (CDT)",
      "author": "shd101wyy",
      "text": "CS411 course opened https://courses.illinois.edu/schedule/2016/fall/CS/411"  
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
