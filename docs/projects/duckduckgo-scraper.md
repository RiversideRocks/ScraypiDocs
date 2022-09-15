# Create a DuckDuckGo Scraper with Scraypi

Tired of using complex code to extract data from a website? Scraypi is here to help. In this tutorial, you will learn how to scrape DuckDuckGo's search results.

First, select a search term. For this demo, we'll use "servers". The easiest DuckDuckGo site to scrape is their HTML only results. That url structure will look something like this:

```
https://html.duckduckgo.com/html/?q=servers
```

Open this link in your browser to make sure valid results appear. Next, let's add this to the Scraypi API. DuckDuckGo doesn't often block IPs, but to be safe, we will use a shared proxy to scrape.

Since this url we need to scrape has url parameters, we need to encode it in base64 to 