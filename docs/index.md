# Scraypi (scray-p-i)

Welcome to Scraypi, an easy-to-use RESTful API to scrape websites.

## Routes

* `GET /` - Information about the project in JSON format
* `GET /api/v1/tor` - Scrapes a site and returns JSON over Tor proxy
* `GET /api/v1/proxy` - ~Scrapes a site via an open proxy~
* `GET /api/v1/proxy-v2` - ~Scrapes the site via a private proxy~

## Example

Route: `/api/v1/{{proxy_type}}`
Parameters required: `url`

> Important: Do not forget the http(s) in the URL. The API will not work without it.

Example response:

`GET https://api.scraypi.com/api/v1/tor?url=https://riverside.rocks`

```
{
  "status": "ok",
  "http_status": "200",
  "data": {
    "title": "Riverside Rocks",
    "links": [
      "/services",
      "/gallery.html",
      "mailto:support@riverside.rocks",
      "https://riverside.rocks/matrix",
      "http://rivers256vwq7u32tjsa4l2ve2px7ikmotzwicadjhrjpp246f5iy6qd.onion/"
    ],
    "images": [
      "https://cdn.riverside.rocks/assets/color.svg",
      "https://cdn.riverside.rocks/assets/Logo-OVH.svg",
      "https://cdn.riverside.rocks/assets/ce518a18-CoF-2022_solid+O.svg"
    ],
    "javascript": [
      "https://research.riverside.rocks/js/plausible.js"
    ],
    "meta_tags": {
      "description": "Trust Nobody",
      "image": "https://avatars0.githubusercontent.com/u/59586759?s=460&u=3a65147e9589b116e6724773ea10e9773ac7c682&v=4"
    }
  },
  "headers": [
    "Date: Tue, 06 Sep 2022 01:36:36 GMT",
    "Server: Apache",
    "x-powered-by: Kali Linux (Vangaurd Edition)",
    "x-cease-and-desisted-by: Bisect Hosting",
    "onion-location: http://rivers256vwq7u32tjsa4l2ve2px7ikmotzwicadjhrjpp246f5iy6qd.onion",
    "Vary: Accept-Encoding",
    "Content-Encoding: gzip",
    "Content-Length: 2160",
    "Keep-Alive: timeout=5, max=100",
    "Connection: Keep-Alive",
    "Content-Type: text/html; charset=UTF-8"
  ],
  "raw_text": "\n\nRiverside Rocks\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\nRiverside Rocks\nPrivacy Services | 1.5gbps network avg. | 15TB bandwidth/day | 20k+ Visitors/day\n\nServices List | Gallery | Contact/Report Abuse | Matrix\n\n\n\n\n\n\n\nTor: rivers256vwq7u32tjsa4l2ve2px7ikmotzwicadjhrjpp246f5iy6qd.onion\n\n\n\n\n\n\n\n\n"
}
```

## Which proxy do you need?

* Tor - Blocked on Cloudflare/Akamai sites
* Open Proxy - Blocked on Cloudflare sites
* Private Proxy - Blocked on few sites

## Ratelimiting

There is not ratelimiting at the moment. However, responses are cached for 60 seconds. If you have a use case that needs this value lowered, please contact us.
