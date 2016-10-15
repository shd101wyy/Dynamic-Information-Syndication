# Dynamic-Information-Syndication
**0.0.1**  
Dynamic Information Syndication standard based on RSS.  
The specification might change in the future.  


<!-- toc orderedList:0 -->

- [Dynamic-Information-Syndication](#dynamic-information-syndication)
	- [Introduction](#introduction)
	- [Required channel elements](#required-channel-elements)
	- [Item](#item)
	- [Common site api specification](#common-site-api-specification)
	- [Example](#example)

<!-- tocstop -->


---

## Introduction  

ALL **DIS** (dynamic information syndication) should conform **JSON** specification.  

<strike> DIS document should have a mandatory field called `version` that specify the version of DIS that the document conforms to. </strike> **will be defined in the future.**  

## Required channel elements   
| Element  | Description | Example |  
|---|---|---|
| title | The name of the DIS service | zhihu.com feeds |
| link | Thr URL to the HTML website | https://www.zhihu.com |  
| description | Phrase or sentence describing the channel | The latest feeds from Zhihu |  
| items | Array of **Item** ||

## Item
| Element | Description | Example |
|---|---|---|
| title | The title of item | How to be more clever? |  
| pubDate | Indicate when the item was published | Sat Oct 15 2016 15:11:55 GMT-0500 (CDT) |
| id | the unique id of the item | 1ha789 |
| author | the author of the item | zhihu admin |
| link | link related to author | https://www.zhihu.com/shd101wyy |
| text | the content of item | How to be more clever, this is a good question |  
| photos | array of photo urls | |


## Common site api specification
* `/website.com/dis`  
return dis information
* `/website/com/dis/get`    
get all items  
  * `/website.com/dis/get?count=10&config={}`  
  get 10 items with config    
  * `/wesite.com/dist/get?pubDate=1476564368038&config={}`  
  get date newer than pubDate

## Example  
```json
{
  "title": "UIUC Course Explorer",
  "link": "https://courses.illinois.edu/",
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

