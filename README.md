# GoFetch API v1 documentation

Welcome to GoFetch API. This API allows to create delivery jobs and get notified of their progress.

## API endpoints

* [Hello World](endpoints/hello_world.md)
* [Jobs](endpoints/jobs.md)
* [Sessions](endpoints/sessions.md)

Test URL: `http://test.go-fetch.com.au/public_api/v1`

Production URL: `https://go-fetch.com.au/public_api/v1`


## Getting started

Anyone with a GoFetch user account can access GoFetch API. Here is how to setup your API account on GoFetch staging environment and submit delivery jobs to test your API integration.

1. First, create a user account in the staging [web app](http://www.go-fetch.com.au/webappstaging) and add a card with a test number `4242 4242 4242 4242`.

1. Next, send a [POST sessions](endpoints/sessions.md#create) request with your GoFetch email and password and get your API authentication token. This only needs to be done once when you setup your API integration, since the authentication token does not change. You can then store your authentication token securely and use it for all other API requests in the future.

1. Check that your authentication works with a `hello_world` request.

```bash
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1
```

1. Finally, supply both your email and authentication token in `X-User-Email` and `X-User-Token` HTTP headers when calling all other GoFetch API endpoints.

#### Test access to the API


## API request haders

| Header | Description |
| --- | --- |
| `X-User-Email: [Your GoFetch email]` | Authentication |
| `X-User-Token: [Your authentication token]` | Authentication |
| `Content-Type: application/json` | Required for POST requests |

## Errors

Error responses contains a single `error` attribute with a text description:

```JSON
{"error": "You need to sign in or sign up before continuing."}
```

## HTTP status codes

GoFetch API returns the following status codes:

| Code | Description |
| --- | --- |
| 2xx Success | Request has succeeded |
| 401 Unauthorized | Authentication error |
| 422 Unprocessable Entity | Request contains incorrect parameters |

## Feedback is welcome

If you have a question or notice a problem with the API or this documentation feel free to submit an issue or a pull request.

