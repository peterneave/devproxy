---
marp: true
theme: uncover
headingDivider: 3
paginate: true
style: |
  section::after {
    /* Layout of pagination content */
    box-sizing: border-box;
    text-align: right;
    width: 120px;
    height: 120px;
    line-height: 120px;
    padding: 20px;
  }
---


<!--
_class:
 - lead
 - invert
-->

# DevProxy

Dev Proxy is an API simulator that helps you effortlessly test your app beyond the happy path.

<!--fit-->
<!-- _paginate: skip -->

## Foreword
<!-- _paginate: skip -->

📝 Contribute on [![w:48](img/github-mark.svg) GitHub](https://github.com/peterneave/devproxy)

🔗 View Online [neave.dev/devproxy](https://neave.dev/devproxy)

⬇️ Download [PowerPoint](https://neave.dev/devproxy/devproxy.pptx) and [PDF](https://neave.dev/devproxy/devproxy.pdf)

## What is Dev Proxy?

Dev Proxy is an API simulator that helps you effortlessly test your app beyond the happy path.

![w:1000px](img/proxy.png)

---

- Create API errors - on internal (ie. localhost) and external (ie. Microsoft Graph).
- Fire rate limits
- Add latency
- Stand up mock APIs

## Get Started

[![Get started with Dev Proxy h:300px](https://markdown-videos-api.jorgenkh.no/url?url=https%3A%2F%2Fyoutu.be%2FHVTJlGSxhcw)](https://youtu.be/HVTJlGSxhcw)

## Local Development

Chromium based browsers will not send localhost to the proxy.

```sh
taskkill /f /im msedge.exe
```

```sh
"msedge.exe" --proxy-bypass-list="<-loopback>" --proxy-server="127.0.0.1:8000"
```

See [documentation](
https://learn.microsoft.com/en-us/microsoft-cloud/dev/dev-proxy/how-to/intercept-localhost-requests) for more information

## Dev Proxy Toolkit

![bg left h:400px](https://garrytrinder.gallerycdn.vsassets.io/extensions/garrytrinder/dev-proxy-toolkit/1.5.0/1759321881336/Microsoft.VisualStudio.Services.Icons.Default)
[Dev Proxy Toolkit](https://marketplace.visualstudio.com/items?itemName=garrytrinder.dev-proxy-toolkit)

## Config

`CTRL+SHIFT+P` - `Create create configuration file`

`.devproxy/devproxyrc.json`

---

![bg 100%](img/config.png)

### Example

![](img/devproxy_intercepted.png)

## Plugins
