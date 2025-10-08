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

## Story

September 2025 CloudFlare outage on their Cloudflare Dashboard due to repeated calls to their own API - the cause was a useEffect without a dependency.

## What is Dev Proxy?

Dev Proxy is an API simulator that helps you effortlessly test your app beyond the happy path.

![w:1000px](img/proxy.svg)
[What is a proxy?](https://learn.microsoft.com/en-us/microsoft-cloud/dev/dev-proxy/concepts/what-is-proxy)

## Use Cases

- **Simulate API errors** - on internal (ie. localhost) and external (ie. Microsoft Graph).
- **Add latency** to requests to so you can test your UI display loading data messages.
- Fire **rate limits** and **handle throttling** - test with the  `Retry-After` header.

---

- Stand up **mock APIs and data** - for when the backend is not ready yet
- **Intercept OpenAI-compatible requests** to [analyze costs](https://learn.microsoft.com/en-us/microsoft-cloud/dev/dev-proxy/how-to/understand-language-model-usage?tabs=aspire)
- Check if your API is making requests with **least permissions** with `API Center`

## Get Started

[![Get started with Dev Proxy bg right h:300px](https://markdown-videos-api.jorgenkh.no/url?url=https%3A%2F%2Fyoutu.be%2FHVTJlGSxhcw)](https://youtu.be/HVTJlGSxhcw)

## Local Development


- ✅ Dev Proxy will set itself as the system proxy. You can run commands `Invoke-WebRequest` or `curl`.
- ℹ️ Chromium* based browsers (Edge/Chrome) bypass system proxy settings for localhost URLs - you need to exclude localhost URLs from the bypass list.

<sub>*See [documentation](https://learn.microsoft.com/en-us/microsoft-cloud/dev/dev-proxy/how-to/intercept-localhost-requests) for Firefox.</sub>

---

 ⚠️ Save your work beforehand ⚠️
Run this to test localhost

```sh
taskkill /f /im msedge.exe
cd "C:\Program Files (x86)\Microsoft\Edge\Application"
msedge --proxy-bypass-list="<-loopback>" --proxy-server="127.0.0.1:8000"
```

### Usage

![](img/devproxy_intercepted.png)

<sub>How does your application handle
slow responses, rate limits and errors?</sub>

## Dev Proxy Toolkit

![bg right h:300px](https://garrytrinder.gallerycdn.vsassets.io/extensions/garrytrinder/dev-proxy-toolkit/1.5.0/1759321881336/Microsoft.VisualStudio.Services.Icons.Default) [VSCode extension](https://marketplace.visualstudio.com/items?itemName=garrytrinder.dev-proxy-toolkit) is a wrapper to the CLI.

## Config

Open the VSCode command palette `CTRL+SHIFT+P` and 'Dev Proxy Toolkit: Create create configuration file'

Creates `.devproxy/devproxyrc.json`

---

![bg 100%](img/config.png)

## Plugins

💡 Hopefully this gives you some ideas 💡

- `Auth` - Simulates authentication and authorization using API keys or OAuth2.
- `CachingGuidancePlugin` - Shows a warning when Dev Proxy intercepted the same request within the specified period of time.
- `CrudApiPlugin` - Simulates a CRUD API with an in-memory data store.

---

- `EntraMockResponsePlugin` - Mocking auth flow API requests.
- `ExecutionSummaryPlugin` - Creates a summary of the requests that pass through the proxy.
- `MockGeneratorPlugin` - Generate mocks from the request.

---

- `MockRequestPlugin` - test webhooks in your client from dev proxy.
- `RateLimitingPlugin` - Simulates rate-limit behaviors.
- `RewritePlugin` - use rewrite rules - test example.com vs example.local
- `UrlDiscoveryPlugin` - creates a list of requested URLs.
- ... and much more

### Focus Mock and CRUD Plugin

*Return fixed data when your backend is not ready*

- Different data on `nth` request
- Can deliver binary data
- Create a mock CRUD API - mutates in memory and resets on restart.
- Access via `devtunnel` over the internet - have your cloud apps connect to your machine.
- Supports Microsoft Entra
