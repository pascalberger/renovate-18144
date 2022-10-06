Reproduction for https://github.com/renovatebot/renovate/issues/18144

## Current behavior

Renovate fails during lookup of the Repology dependency:

```
WARN: Repology lookup failed with unexpected error
{
  "packageName": "debian_11/ca-certificates",
  "err": {
    "name": "HTTPError",
    "code": "ERR_NON_2XX_3XX_RESPONSE",
    "timings": {
      "start": 1665051008270,
      "socket": 1665051008270,
      "lookup": 1665051008458,
      "connect": 1665051008458,
      "secureConnect": 1665051008656,
      "upload": 1665051008656,
      "response": 1665051008819,
      "end": 1665051008819,
      "phases": {
        "wait": 0,
        "dns": 188,
        "tcp": 0,
        "tls": 198,
        "request": 0,
        "firstByte": 163,
        "download": 0,
        "total": 549
      }
    },
    "message": "Response code 403 (Forbidden)",
    "stack": "HTTPError: Response code 403 (Forbidden)\n    at Request.<anonymous> (/home/ubuntu/renovateapp/node_modules/got/dist/source/as-promise/index.js:118:42)\n    at runMicrotasks (<anonymous>)\n    at processTicksAndRejections (node:internal/process/task_queues:96:5)",
    "options": {
      "headers": {
        "user-agent": "Renovate Bot (GitHub App 2740)",
        "accept": "application/json",
        "accept-encoding": "gzip, deflate, br"
      },
      "url": "https://repology.org/api/v1/project/ca-certificates",
      "hostType": "repology",
      "username": "",
      "password": "",
      "method": "GET",
      "http2": false
    },
    "response": {
      "statusCode": 403,
      "statusMessage": "Forbidden",
      "body": "<html>\r\n<head><title>403 Forbidden</title></head>\r\n<body>\r\n<center><h1>403 Forbidden</h1></center>\r\n<hr><center>nginx</center>\r\n</body>\r\n</html>\r\n",
      "headers": {
        "server": "nginx",
        "date": "Thu, 06 Oct 2022 10:10:10 GMT",
        "content-type": "text/html",
        "content-length": "146",
        "connection": "close"
      },
      "httpVersion": "1.1"
    }
  }
}
```

Opening https://repology.org/api/v1/project/ca-certificates from the browser works.

This behavior started October 5th 2022.

## Expected behavior

Renovate should be able to lookup Repology dependencies.
