# curl & wget — Fetch URLs and Test Web Services

## What it does
`curl` sends HTTP requests and prints the response.
`wget` downloads files to disk.
Both are essential for testing APIs and web servers.

## Syntax
```bash
curl https://example.com            # fetch a page
curl -I https://example.com         # headers only (status code)
curl -s https://example.com         # silent — no progress bar
curl -sI localhost | grep -q 200    # quiet check for 200 status

wget https://example.com/file.zip   # download a file to disk
wget -O output.html https://example.com  # save with custom name
```

## My Terminal Output
```bash
rushi@rushi:~$ curl -I https://example.com
HTTP/2 200
content-type: text/html; charset=UTF-8
server: ECS (nyb/1D1E)

rushi@rushi:~$ curl -I localhost
HTTP/1.1 200 OK
Server: nginx/1.18.0
Content-Type: text/html

rushi@rushi:~$ curl -sI localhost | grep "200"
HTTP/1.1 200 OK
```

## curl flags
| Flag | What it does |
|------|-------------|
| `-I` | Fetch headers only — great for status checks |
| `-s` | Silent — suppresses progress output |
| `-o` | Save output to a file |
| `-L` | Follow redirects |
| `-X POST` | Send a POST request |

## Key Points
- `curl -I` is faster for health checks — downloads only headers
- `curl -sI localhost | grep -q 200` is silent — perfect for scripts
- `wget` is simpler for just downloading files to disk
- `curl` is more powerful for API testing with custom headers and methods
- A `200 OK` response means the web server is healthy

## When I use this
Testing if nginx is serving after a config change, checking API
endpoints, downloading files from the command line.
