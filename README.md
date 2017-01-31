# VoolerGROUP API reference
This API reference is under construction, last updated January 31st, 2017.

This guide explains how to use the voolerGROUP API in your own applications and identifies the different types of events.

### What is voolerGROUP?
-----------------------
**VoolerGROUP** is cloudbased, mobileready WebRTC solution for different use cases. VoolerGROUP is based on **rooms** and **roles**. VoolerGROUP takes care about configuration models, keys, tokens, sessions and other variables behind the scenes. VoolerGROUP is build on top of TokBox WebRTC SDK.

To build your own application based on voolerGROUP, you can choose from two different ways:
- **<API Reference for iframe embeds>** (not suitable for iOS)
- **<API Reference for JSON>** (advanced way)

In some cases, you can also combine power from both API.

### Definitions
---------------
In this chapter we are defining basic concepts of voolerGROUP.

- in the heart of voolerGROUP there is **room** which is like a normal, physical meeting room which gathers different **users** together
- every **user** have always one **role**
- every **room** can have different **features**
- **client** is something you are building

So we are playing quite much around *rooms*, *roles* and *features*. As said above, *rooms* are gathering users together, so all *users* inside the same *room* are connected together. The way *users* are connecting together is managed by *role*.

- *role* is **owner** if he/she owns current *room* and is logged in voolerGROUP. *Owner* is highest user level.
- if *user* is **allowed** publish own camera and/or microphone to other *users*, *user* role is **publisher**
- if *user* can only view and follow other *users*, his/her *role* is **viewer**. *Viewer* is the lowest role and usually you can join *room* as viewer (default)

*User roles* are provided by voolerGROUP by API.

*Rooms* have different *features*. *Features* can be like following ones:
* recording ability (always on, triggered, none)
* screensharing
* max amount of publishers
* max amount of viewers
* accessible only by certain role
* authentication method like PIN-code or password
* chat (open, moderated, none)
* UI elements like logo, background, colors etc. for *room*

Every *room* has own, unique name which is managed by *owner*. Naming format for *room* is always  **owner**-**roomname**. 

### Building your client based on iframe Embeds
----------------------------------------------
Easiest way to embed voolerGROUP is the iframe API which lets you embed voolerGROUP on your website. This guide explains how to use the iframe API. 

Simpliest usage of inline frame is something like following one:

```html
<iframe id="voolerGROUP" type="text/html" width="640" height="640"
src="http://webaitio.tv/etusivu/OWNER-ROOMNAME" frameborder="0"></iframe>
```

Above example will embed *room* called **OWNER-ROOMNAME** to you webpage with *role* **VIEWER**. Height and width are both 640px and there is no borders.

If you need information for how to use HTML iframe tag, please visit [W3Schools](http://www.w3schools.com/tags/tag_iframe.asp).

If you wish to join *room* called **OWNER-ROOMNAME** with your *role* as a **PUBLISHER**, you can use following inline code in your *client*:

```html
<iframe id="voolerGROUP" type="text/html" width="640" height="640"
src="http://webaitio.tv/etusivu/OWNER-ROOMNAME?role=owner" frameborder="0"></iframe>
```

You can notice that we added a following query string:
```
?role=owner
```

This was an example usage of parameters.

### Building JSON based client
-----------------------------
Our JSON API endpoints give external *clients* access to voolerGROUP data and outputs necessary data for your use.

```
Base URL: https://webaitio.to/etusivu/OWNER-ROOMNAME
```

|METHOD |ENDPOINT                       |USAGE                                          |RETURNS            |
|------ |--------                       |-----                                          |-------            |
|GET    |?data=json                     |Get full JSON                                  |full room data     |
|GET    |?data=json&password={123}      |Get full JSON if *room* is password protected  |full room data     |
|GET    |?data=json&password={WRONG}    |Password is wrong                              |Wrong password     |

### Revision history
-------------------
##### January 31, 2017
First public release

##### January 29, 2017
Initial version of voolerGROUP API

