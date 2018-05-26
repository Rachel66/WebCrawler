# requests-crawler

A simple web crawler, mainly targets for link validation test.

## Features

- based on [requests-html][requests-html], **full JavaScript support!**
- support requests frequency limitation, e.g. rps/rpm
- support crawl with headers and cookies
- include & exclude mechanism
- group visited urls by HTTP status code
- display url's referers and hyper links

## Installation/Upgrade

```bash
$ pip install -U git+https://github.com/debugtalk/WebCrawler.git
```

Only **Python 3.6** is supported.

To ensure the installation or upgrade is successful, you can execute command `requests_crawler -V` to see if you can get the correct version number.

```bash
$ requests_crawler -V
0.5.2
```

## Usage

```text
$ requests_crawler -h
usage: requests_crawler [-h] [-V] [--log-level LOG_LEVEL]
                        [--seed SEED]
                        [--include [INCLUDE [INCLUDE ...]]]
                        [--exclude [EXCLUDE [EXCLUDE ...]]]
                        [--headers [HEADERS [HEADERS ...]]]
                        [--cookies [COOKIES [COOKIES ...]]]
                        [--workers WORKERS]
                        [--requests-limit REQUESTS_LIMIT]
                        [--interval-limit INTERVAL_LIMIT]

A web crawler for testing website links validation, based on requests-html.

optional arguments:
  -h, --help            show this help message and exit
  -V, --version         show version
  --log-level LOG_LEVEL
                        Specify logging level, default is INFO.
  --seed SEED           Specify crawl seed url
  --include [INCLUDE [INCLUDE ...]]
                        Urls include the snippets will be crawled recursively.
  --exclude [EXCLUDE [EXCLUDE ...]]
                        Urls include the snippets will be skipped.
  --headers [HEADERS [HEADERS ...]]
                        Specify headers, e.g. 'User-Agent:iOS/10.3'
  --cookies [COOKIES [COOKIES ...]]
                        Specify cookies, e.g. 'lang=en country:us'
  --workers WORKERS     Specify concurrent workers number.
  --requests-limit REQUESTS_LIMIT
                        Specify requests limit for crawler, default rps.
  --interval-limit INTERVAL_LIMIT
                        Specify limit interval, default 1 second.
```

## Examples

Basic usage.

```bash
$ requests_crawler --seed http://debugtalk.com
```

Crawl with headers and cookies.

```text
$ requests_crawler --seeds http://debugtalk.com --headers User-Agent:iOS/10.3 --cookies lang:en country:us
```

Crawl with extra hosts, e.g. `httprunner.org` will also be crawled recursively.

```text
$ requests_crawler --seeds http://debugtalk.com --include httprunner.org
```

Skip excluded url snippets, e.g. urls include `httprunner` will be skipped.

```text
$ requests_crawler --seeds http://debugtalk.com --exclude httprunner
```

Crawl with 30 rps limitation.

```text
$ requests_crawler --seeds http://debugtalk.com --requests-limit 30
```

Crawl with 500 rpm limitation.

```text
$ requests_crawler --seeds http://debugtalk.com --requests-limit 500 --interval-limit 60
```

<!-- ## Logs && Report -->


[requests-html]: https://github.com/kennethreitz/requests-html