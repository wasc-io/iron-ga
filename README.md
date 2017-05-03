# iron-ga

`iron-ga` is a Polymer Element for [Google Analytics Web Tracking](https://developers.google.com/analytics/devguides/collection/analyticsjs/), supports page and event tracking.

The element supports anonymizing the users IP, as required by the EU Dataprotection Law

### Installation

```sh
bower install iron-ga --save
```


#### Initialise

```html
<link rel="import" href="bower_components/iron-ga/iron-ga.html">

<iron-ga code="UA-XXXXX-Y"></iron-ga>
```

If you are using regular anchor links and not push-state links you are ready to go!

If you have a Single Page Application that uses push-state, eg with `page.js` or `<app-router>` you will need to signal to the `iron-ga` element that the page has changed.

The Page Change events are handled using iron-signals so you do not need to do any dom finding to trigger a page track.

#### Anonymize
````html
<link rel="import" href="bower/components/iron-ga/iron-ga.html">
<iron-ga code="UA-XXXXXX-Y" anonymize="true"></iron-ga>
````

#### Track a page Change

```javascript
    this.fire('iron-signal', {name: 'track-page', data: { path: "/about.html" } });
```

#### Track an Event

```javascript
    this.fire('iron-signal', {name: 'track-event',data: {category: "messages",action: "send_text_message",label: "group",value: 1}});
```

#### User id attribution

To use [Google Analytics user id attribution](https://developers.google.com/analytics/devguides/collection/analyticsjs/user-id) set the user id property on the element:

```javascript
    document.querySelector("iron-ga").userId = loggedInUserId;
```
