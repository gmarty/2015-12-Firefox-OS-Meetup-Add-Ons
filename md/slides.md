# Firefox OS Add-ons:<br>Hands-on Session
## Firefox OS London December 2015

---

[@g_marty](https://twitter.com/g_marty) - Guillaume Marty

I am <img src="img/French.svg" style="height: .8em; vertical-align: middle;" alt="French" title="French"> and living in the <img src="img/UK.svg" style="height: .8em; vertical-align: middle;" alt="UK" title="UK">

I work at <img src="img/Mozilla.svg" style="height: .8em; vertical-align: middle; margin-bottom: 21px;" alt="Mozilla" title="Mozilla"> on <img src="img/Firefox-OS.svg" style="height: 1.7em; vertical-align: middle; margin-bottom: 21px;" alt="Firefox OS" title="Firefox OS">

---

## What are add-ons all about?

Note:
Since the beginning of Firefox OS, it's been really easy to edit the code and
make live changes.
Add-ons allow to persist these changes and easily custom and adapt any aspect
of the OS. It works on both websites and apps.
That's a completely unique feature in the world of mobile OSes.

---

## WebExtensions

Note:
Long-term plan to update all flavours of Firefox.
New extension model based on the specification implemented in Chrome and Opera.
That will help interoperability.

---

## Inside an add-on

![WebExtension](img/webextension.svg)

---

## manifest.json

```json
{
  "manifest_version": 1,
  "name": "Add-on Example",
  "description": "Firefox OS add-on example",
  "version": "1.0",
  "author": "Guillaume Marty",
  "content_scripts": [
    {
      "matches": ["app://system.gaiamobile.org/index.html"],
      "css": ["css/style.css"],
      "js": ["js/index.js"]
    }
  ],
  "icons": { "128": "/icons/128.png" }
}
```

---

## update.webapp

```json
{
  "name": "Add-on Example",
  "description": "Firefox OS add-on example",
  "developer": {
   "name": "Guillaume Marty"
  },
  "package_path": "extension.zip",
  "icons": { "128": "/icons/128.png" }
}
```

Note:
It's still a bit experimental and some aspect may change.
Specifically the icons property in update.webapp may go away.
But we recommend to specify it.

---

## Life of an add-on

1. Development
2. [Publish online]
3. Install
4. Enable / Disable

Note:
If you use the WebIDE, not need to put it online.
Add-ons are activated by default when installed from the Marketplace.
But they must be enabled in the Settings app when installed from WebIDE, each
time a new version is flashed.

---

## Coding considerations

* <div>`window` is proxied</div> <!-- .element: class="fragment" data-fragment-index="1" -->
* <div>The `DOM` may or may not be loaded</div> <!-- .element: class="fragment" data-fragment-index="2" -->
* <div>Avoid multiple injections</div> <!-- .element: class="fragment" data-fragment-index="3" -->
* <div>Listen to `onenabledstatechange` event</div> <!-- .element: class="fragment" data-fragment-index="4" -->

Note:
An add-on code can read window properties but the global variables are not
visible outside the add-on.
Make sure that your add-on works whether the DOM is loaded already or not.
navigator.mozApps.mgmt.addEventListener('enabledstatechange', fn) can be used to
initialise an add-on at install or clean it at deinstall.

---

## Warning

|Product|Version|Date|
|---------------|---|----------------------|
|Firefox OS     |2.5|2015/08/27 or later|
|Firefox Desktop|44 |2015/09/30 or later|

Note:
The implementation is still experimental and may be unstable.

---

## Warning

* Not compatible with simulators in WebIDE
* Please use the mulet

---

## Use cases

Note:
Micro features.
Fix bugs/features on websites.
There is no limit to the customability of your phone.

---

## Marketplace

![MDN](img/marketplace.png)

---

## In the future

* More features, more stable, less bugs
* Support API of WebExtensions in Chrome

Note:
There may be compatible with other flavours of Firefox.

---

## Documentation

---

[developer.mozilla.org/en-US/Firefox_OS/Add-ons](https://developer.mozilla.org/en-US/Firefox_OS/Add-ons)

![MDN](img/mdn.png)

---

[developer.chrome.com/extensions](https://developer.chrome.com/extensions)

![Google Chrome Developers](img/google-chrome.png)

---

## Forums

* [Dev FxOS forum](https://groups.google.com/forum/#!forum/mozilla.dev.fxos)
* [Discourse](https://discourse.mozilla-community.org/c/add-ons/)

---

## Thank you!
