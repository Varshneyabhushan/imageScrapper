# ImageScrapper

[![Install now.](https://developer.chrome.com/webstore/images/ChromeWebStore_BadgeWBorder_v2_206x58.png)
](https://chrome.google.com/webstore/detail/imagescrapper/iobhdbbomjpihclcfdcedekcigollffc)


## About

Image scrapper is a chrome extension that can be used to exctract image URLs out of any web page and download them in bulk.


# Features

1. This can also be used to download files of other type (example : pdf)
2. We can also choose to upload the images directly to google photos (takes up memory from google drive quota )
3. Ability to pause downloads or download images in the deserved order.
4. Save the list of URLs to chrome's local storage to download later.
5. Import and export configurations.

# How to use

1. Study the web page you want to get images from , and do the configuration accordingly in settings page.see [How to Configure](/README.md#how-to-configure) for details.
![demo_1](/tiles/demo_1.png)
2. click the accept button in the notifications.<br>
![demo_2](/tiles/demo_2.png)
3. Wait till the application fetches the URLs and click the download button. Content page should not be closed util all the images are fetched.

# How to Configure

1. url : Match pattern that matches to deserved URLs.
2. name : address of the [DOM element](https://developer.mozilla.org/en-US/docs/Web/API/Element) in the document that contains title of the album
3. path : address of the DOM elements which have URLs of pictures you want to fetch
4. next : address of the element that has link to the document containing next set of pictures. Leave it blank if there are no more pictures to be fetched.

## Syntax

Just like xpath , address should be like location path.The location path consists of steps.Each step is either in form `X` or `X=X` or `X=X=X`

* `    id=x    ` --> get elements of id = x
* `childNodes=x` --> get xth childNode
* `   class=x  ` --> get elements of classname = x
* ` class=x=y  ` --> get yth element of class = x 
* `    tag=x   ` --> get elements of tagname = x
* `   tag=x=y  ` --> get yth element of tagname = x
* `     ?=x    ` --> get attribute value of name = x
* `  navigate  ` --> get document after navigating the address obtained

## Example

In javascript , `class=gallery=0/tag=input=0/?=value` translates to 

```
document.getElementsByclassName('gallery')[0].getElementsByTagName(‘input’)[0].value
```

Configuration that was shown in the demonstration is 
```
{
  "https://www.unsplash.com/search/photos/*":{
    "1":"https://www.unsplash.com/search/photos/*",
    "2":"tag=input=0/?=value",
    "3":"class=_1pn7R/tag=a=0/?=href/navigate/class=_2yFK- IEpfq=0/tag=img=0/?=src",
    "4":"",
    "5":"https://www.unsplash.com/search"
    }
}
```


