# Local HTTP Lab

A beginner lab to understand how a web client communicates
with a local HTTP server.

## Requirements
- Ubuntu
- Python 3
- curl

## Project files
- site/index.html: the web page
- evidence/http-results.txt: observed test results
- README.md: instructions

## Start the server
Run these commands separately:

```bash
cd ~/local-http-lab
python3 -m http.server 8000 --bind 127.0.0.1 --directory site
```

Keep this terminal open. The server serves files from `site`
and listens on the local address, port 8000.

## Test
Open a second Ubuntu terminal.

Existing page:
```bash
curl -i http://127.0.0.1:8000/index.html
```
Expected: HTTP 200 OK and the page HTML.

Missing page:
```bash
curl -i http://127.0.0.1:8000/missing.html
```
Expected: HTTP 404 File not found.

Stop the server with Ctrl+C in the server terminal.
Then request the existing page again:
```bash
curl -i http://127.0.0.1:8000/index.html
```
Expected: curl error (7), failed to connect.

## What I learned
- A server is a program that receives requests and sends responses.
- HTTP 404 means the server responded but did not find the page.
- A connection failure is different from an HTTP response.
- Stopping the server does not delete the HTML file.

## Scope
This is a local learning lab, not a production hosting setup.
