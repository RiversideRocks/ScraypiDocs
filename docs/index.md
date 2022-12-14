# Scraypi (scray-p-i)

Welcome to Scraypi, an easy-to-use and free RESTful API to scrape websites.

## Routes

* `GET /` - Information about the project in JSON format
* `GET /api/v1/tor` - Scrapes a site and returns JSON over Tor proxy
* `GET /api/v1/proxy` - Scrapes a site via an open proxy or shared proxy

## Example

Route: `/api/v1/{{proxy_type}}`
Parameters required: `url` (url of website to scrape)
Parameters required if using proxy endpoint: `type` (either shared or open, default: open)

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

### Tor
* Often blocked on Cloudflare/Akamai sites
* IPv6 and IPv4
* Geolocated mostly in Europe and the United States
* Mostly datacenter IPs

Additional information: IPs are rotated every ten minutes.

### Open Proxy
* Often blocked on Cloudflare sites
* IPv4 only
* **HTTP only**
* Geolocation varies
* Blend of datacenter and residential IPs

### Shared Proxy
* Blocked on fewer sites (works well with Cloudflare)
* IPv4 and IPv6 (?)
* Geolocation varies
* Blend of datacenter IPs

Additional information: IPs are rotated hourly.

All requests use fake user agents.

### Private Proxy
* Coming Soon

Currently all of these routes experience the same cache time, but in the future, harsher cache
times may be imposed to reduce load on private proxies.

## Ratelimiting

There is not ratelimiting at the moment. However, responses are cached for 60 seconds. To see if your request has been ratelimited, check the `X-Cache` header. If it read "MISS", it has bypassed the cache. If it reads "HIT", it has temporary hit our cache server. If you have a use case that needs this value lowered, please contact us.

## Terms of Use

This is a free service. We require the following while using this service:

* Do not use this site/service to harass others
* Don't abuse the API (don't send exessive requests and traffic)
* Don't use this site/service to DDoS websites
* Don't use this site/service to scrape/access illegal websites

Before use, consider reading up on the legality of web scraping in your country. Our website is operated from the United States of America where [said practice is legal](https://techcrunch.com/2022/04/18/web-scraping-legal-court/).

## Donations

This is a free project. At the moment I don't have plans to add paid tiers. If you would like to donate, our Bitcoin and Monero wallets can be found [here](https://riverside.rocks/services).

## Credits

Our backend uses [Python](https://python.org), [Beautiful Soup](https://beautiful-soup-4.readthedocs.io/en/latest/), [Varnish](https://varnish-cache.org/), [Caddy](https://caddyserver.com) and [Tor](https://www.torproject.org).

This project is managed by [Riverside Rocks](https://riverside.rocks).