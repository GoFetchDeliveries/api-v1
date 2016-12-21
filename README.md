# GoFetch API v1 documentation

Welcome to GoFetch API. This API allows to create delivery jobs and get notified of their progress.

## Sending requests

Please send requests to `https://go-fetch.com.au/public_api/v1/`.

## Request Headers

| Header | Description |
| --- | --- |
| `X-User-Email: [Your GoFetch email]` | Authentication |
| `X-User-Token: [Your authentication token]` | Authentication |
| `Content-Type: application/json` | Required for POST requests |

## Getting started

Anyone with a GoFetch user account can access GoFetch API.

1. First, create an normal user account using either [GoFetch iOS app](https://itunes.apple.com/au/app/gofetch/id1045358128?mt=8) or the web app [www.go-fetch.com.au/webapp/](https://www.go-fetch.com.au/webapp/).

1. Next, send a [POST sessions](endpoints/sessions.md#create) request with your GoFetch email and password and get your API authentication token. This only needs to be done only once when you setup your API integration, since the authentication token does not change. You can then store your authentication token securely and use it for all other API requests in the future.

1. Finally, supply both your email and authentication token in `X-User-Email` and `X-User-Token` HTTP headers when calling all other GoFetch API endpoits.

#### Test access to API


```bash
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' https://go-fetch.com.au/public_api/v1/hello_world
```

## API endpoints

* [Hello World](endpoints/hello_world.md)
* [Jobs](endpoints/jobs.md)
* [Sessions](endpoints/sessions.md)

