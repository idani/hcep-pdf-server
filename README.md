# hcep-pdf-server

This forked from https://github.com/uyamazak/hcep-pdf-server


Simple and fast PDF rendering server using Headless Chrome & Express & Puppeteer.

Headless Chrome
<https://developers.google.com/web/updates/2017/04/headless-chrome>

Express
<http://expressjs.com/>

Puppeteer
<https://github.com/GoogleChrome/puppeteer>


## Getting Started

### Caution
Since this product is supposed to be used within local network (like Kubernetes, Google Kubernetes Engine), error control and security measures are minimum, please accept only reliable requests. It does not assume direct disclosure to the outside.


### Clone
git clone this repository.


### (optionary) Add fonts
If you convert pages in Japanese, Chinese or languages other than English, you will need to install each font files. Also, you can use WEB fonts, but since it takes a long time for requesting and downloading them, we recommend that install the font files in the server.


```
cp AnyFonts.ttf ./fonts/
```


### Build image

```
 docker-compose build
```

### Run

Below example, run with 80 port.

```
 docker-compose up -d

```

## Example

### Get request with url parameter

```
curl "http://localhost?url=http://example.com" -o hcep-pdf-get.pdf
```

### Get request with url parameter

```
curl "http://localhost/screenshot?url=http://example.com" -o hcep-pdf-get.pdf
```


### POST request with html parameter

```
curl -sS http://localhost:8000 -v -d html=hcep-pdf-ok -o hcep-pdf-post.pdf
```

Please note that because the page does not have a URL, when sending html in POST method, you can not use a relative path.

So, you need to include external files with domain.

Bad, not working

```
<link href="/static/style.css" rel="stylesheet">
```

OK

```
<link href="http://example.com/static/style.css" rel="stylesheet">
```

## Customize PDF options
You can customize PDF with options. Read the puppeteer API's docs.

<https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md#pagepdfoptions>


## Author
uyamazak: https://github.com/uyamazak/

blog: http://uyamazak.hatenablog.com/
