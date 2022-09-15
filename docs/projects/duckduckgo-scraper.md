# Create a DuckDuckGo Scraper with Scraypi

Tired of using complex code to extract data from a website? Scraypi is here to help. In this tutorial, you will learn how to scrape DuckDuckGo's search results.

First, select a search term. For this demo, we'll use "servers". The easiest DuckDuckGo site to scrape is their HTML only results. That url structure will look something like this:

```
https://html.duckduckgo.com/html/?q=servers
```

Open this link in your browser to make sure valid results appear. Next, let's add this to the Scraypi API. DuckDuckGo doesn't often block IPs, but to be safe, we will use a shared proxy to scrape.

Since this url we need to scrape has url parameters, we need to encode it in base64. You can write this into your code or simply find a website online that does this task:

```
aHR0cHM6Ly9odG1sLmR1Y2tkdWNrZ28uY29tL2h0bWwvP3E9c2VydmVycw==
```

It's time to add this to the API. The API request with a shared proxy should look like this:

```
https://api.scraypi.com/api/v1/proxy?url=aHR0cHM6Ly9odG1sLmR1Y2tkdWNrZ28uY29tL2h0bWwvP3E9c2VydmVycw==&type=shared&encoded=true
```

Adding the `encoded` parameter is very important: it signals to the API that the link is being sent encoded in base64. Send the request, and voilà:

![](https://i.imgur.com/BxibVOl.png)

No complex code, no wasting time. Just an easy API request. All links that have been scraped from the page are found under data --> links. Enjoy!