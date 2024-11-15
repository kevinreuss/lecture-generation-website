# Web Caching and Content Delivery Networks (CDNs)

Web caching is a strategy that involves storing copies of web documents in locations closer to the user. It reduces latency and network traffic, leading to faster content delivery. The most common HTTP headers regarding caching are `Cache-Control`, `Expires`, `ETag`, and `Last-Modified`.

```python
# Example of HTTP headers in Python
import requests

response = requests.get('https://example.com')
print(response.headers['Cache-Control'])
print(response.headers['Expires'])
print(response.headers['ETag'])
print(response.headers['Last-Modified'])
```

Content Delivery Networks (CDNs) use web caching as a key strategy. CDNs are distributed networks of servers that efficiently deliver web content to users based on their geographic location. The primary goal of a CDN is to increase web content delivery speed and reliability by distributing the service spatially relative to end-users.

A simple example of CDN usage is linking to jQuery via a CDN in an HTML document.

```html
<!DOCTYPE html>
<html>
<head>
    <!-- jQuery CDN link -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
</head>
<body></body>
</html>
```

In this example, the browser will check its cache for the jQuery file before making a network request. If the file is not in the cache, the request will go to the CDN, which will serve the file from the nearest geographical server.

For both caching and CDNs, it's important to consider the trade-off between data consistency and quicker response times. You can control this balance using `Cache-Control` directives like `no-cache`, `no-store`, `max-age`, or `s-maxage`. 

Remember, performance gains from web caching and CDNs can be significant but should be carefully managed to ensure data accuracy and freshness.