# VoolerGROUP API reference
Last update March 22nd, 2017.

This reference explains how to use the voolerGROUP API in your own applications and identifies the different types of events.


## voolerGROUP
**VoolerGROUP** is cloudbased, mobileready WebRTC solution for different use cases. VoolerGROUP is based on **rooms** and **roles**. VoolerGROUP takes care about configuration models, keys, tokens, sessions and other variables behind the scenes.

To build your own client application based on voolerGROUP, you can simply embed room in your website. Embedding is not suitable for iOS.

In more advance needs, we offer also more powerful REST API, please ask.

## Definitions

In this chapter we are defining basic concepts of voolerGROUP. In the middle of voolerGROUP there is **room** which is like a normal, physical meeting room which gathers different **users** together. 
- every **user** have always one **role**
- every **room** can have different **features**
- every *room* is owned by **organization**
- **client** is something you are building

Key concepts are *rooms*, *roles* and *features*. As said above, *rooms* are gathering users together, so all *users* inside the same *room* are connected together. The way *users* are connecting together is managed by *role*.

- *role* is **owner** if he/she owns current *room* and is logged in voolerGROUP. *Owner* is highest user level.
- if *user* is **allowed** publish own camera and/or microphone to other *users*, *user* role is **publisher**
- if *user* can only view and follow other *users*, his/her *role* is **viewer**. *Viewer* is the lowest role and usually you can join *room* as viewer (default)

*User roles* are provided by voolerGROUP by API.

*Rooms* have different *features*. *Features* can be like following ones:
* recording ability (always on, triggered, none)
* screensharing
* max amount of publishers
* max amount of viewers
* accessible only by certain role(s)
* authentication method like PIN-code or password
* chat (open, moderated, none)
* UI elements like logo, background, colors etc. for *room*

Every *room* has own, unique name which is managed by ***organization***. Naming format for *room* is   **`organization-roomname`** in common environment.

We also offer solution where you don't need to define organization as it is already defined other ways, for example in subdomain or similar. You can build your application based `organization.vooler.tv/roomname` as a base scheme for example.


## Using iframe embeds

Easiest (and quickest) way to use voolerGROUP is the iframe API which lets you embed voolerGROUP on your website. This guide explains how to use the iframe API. 

Simpliest usage of inline frame is something like following one:

```html
<iframe id="voolerGROUP" width="640" height="640" src="https://baseurl.tld/ORGANIZATION-ROOMNAME" frameborder="0"></iframe>
```

Above example will embed *room* called **ORGANIZATION-ROOMNAME** to your application or webpage with *role* **VIEWER**. Height and width are both 640px and there are no borders.

If you need information for how to use HTML iframe tag, please visit [W3Schools](http://www.w3schools.com/tags/tag_iframe.asp).

If you wish to embed *room* called **ORGANIZATION-ROOMNAME** with *role* as a **PUBLISHER**, you can use following inline code in your *client*:

```html
<iframe id="voolerGROUP" width="640" height="640" src="https://baseurl.tld/OWNER-ROOMNAME?role=owner" frameborder="0"></iframe>
```

You can notice that we added only one query string `?role=owner` to address line. With this single query string you defined upper role for user. When you are embedding voolerGROUP with simple iframe, voolerGROUP is taking care about all UI elements like predefined color scheme, logos etc. for organization.

You can also embed voolerGROUP backend if you wish as a similar way or You can use voolerGROUP's backend as a separate service. VoolerGROUP will maintain all necessary things for You, you just need to create room(s) and possible password for publishers.

#### Advanced iframe embedding

If you need more control for iframe embedding, you can use different parameters for more customized usage. You can use for example following features:

- embed whitelabeled (remove header elements)
- hide chat
- possibility to have each publisher in own frame
- possibility to have shared screen in own frame
- define aspect ratio of videos (fixed 1:1, 16:9, 4:3 or flexible)
- ...

We can offer whitelabeled iOS and Android applications which can be branded as needed.

#### Examples

Default embed with two users, width 100%. Fixed ratio 1:1. Menu and branding visible: 
![Default](https://raw.githubusercontent.com/webaitio/API/master/screenshots/branded__two_publishers_default.png "Default embed")

Embed with two users, width 100%. Fixed ratio 1:1. Only background color visible: 
![Colored bg](https://raw.githubusercontent.com/webaitio/API/master/screenshots/branded__two_publishers__background_color_set.png "Background color only")

Embed with two users, width 100%. Fixed ratio 1:1. Fully unbranded: 
![Whitelabel](https://raw.githubusercontent.com/webaitio/API/master/screenshots/whitelabel__two_publishers__fixed_ratio.png "Whitelabel")

Embed with one user only, width 100%. Wide ratio. Fully unbranded: 
![Whitelabel wide](https://raw.githubusercontent.com/webaitio/API/master/screenshots/whitelabel__one_publisher__wide.png "Whitelabel wide")

## System requirements

##### Bandwidth:
- Video: 300 kbps per stream (recommended lowest level) - 1000 kbps per stream (recommended)
- Audio: 50 kbps per stream (recommended lowest level) - 100 kbps per stream (recommended)

Quality of video and audio will automatically change depending on bandwidth.  

##### Video resolutions — browsers:
- 1280 x 720
- 640 x 480 (default, recommended resolution)
- 320 x 240

##### Video resolutions — mobile (iOS/Android):
- Customizable

##### Additional recommendations:
Headsets with microphone for improved sound quality and privacy **OR** USB echo-canceling speakers for meeting room environments.

##### Supported browsers (desktop and Android):
- Google Chrome (latest release version)
- Google Chrome for Android (latest release version)
- Firefox (latest release version)
- Firefox for Android (latest release version)
- Opera (latest release version)

##### Supported iOS-hardware (iOS-app only):
- iPad 4, iPad mini 2, iPad Air or newer versions
- iPad Pro
- iPhone 5 or newer
- minimum supported iOS version is 9 or higher

VoolerGROUP is not currently supporting iOS without native application (except: webcast mode).

##### Common requirements and features:
- Port 443 must be open on the client network
- VoolerGROUP is based on VP8 video format (the WebRTC standard)
- Internet Explorer or Edge **IS NOT** currently supported
##
