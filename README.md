# 🐶 GoFetch API documentation v1

Welcome to GoFetch API. Anyone with a GoFetch user account can access GoFetch API, which allows to create delivery jobs and get notified of their progress.

## API endpoints

## "Public APIs" (not that others are private, but you know...)
* [Hello World](endpoints/hello_world.md)
* [Job status webhook](endpoints/job_status_webhook.md)
* [Jobs](endpoints/jobs.md)
* [Sessions](endpoints/sessions.md)

## V1

* [Sign In](endpoints/v1/users/sign_in.md)
* [Calculate a Job's Price](endpoints/v1/jobs/calculate.md)
* [Create a Customer Job](endpoints/v1/my/customer/jobs.md)

## Getting started in the test environment

API requests to test server are sent to

```
http://test.go-fetch.com.au/public_api/v1/
```

1) First, create a user account in the [test web app](http://app.go-fetch.com.au/staging) and add a credit card with a test number `4242 4242 4242 4242`.

2) Next, send [create a session](endpoints/sessions.md#create) request with your GoFetch email and password and get your API authentication token. This only needs to be done once when you setup your API integration, since the authentication token does not change. You can then store your authentication token and use it for all other API requests in the future.

3) Almost there. Check that your authentication works with a [hello world](endpoints/hello_world.md) request.

```bash
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/hello_world
```

4) Finally, send [create a job](endpoints/jobs.md) request and supply your email and authentication token in `X-User-Email` and `X-User-Token` HTTP headers.


## API request haders

Please supply the following headers with your HTTP requests.

| Header | Description |
| --- | --- |
| `X-User-Email: [Your GoFetch email]` | Authentication |
| `X-User-Token: [Your authentication token]` | Authentication |
| `Content-Type: application/json` | Required for POST requests |

## Errors

Error is reported with a non-2xx status code and a single `error` attribute with a text description:

```JSON
{"error": "You need to sign in or sign up before continuing."}
```

## HTTP status codes

GoFetch API returns the following status codes:

| Code | Description |
| --- | --- |
| 2xx Success | Request has succeeded |
| 401 Unauthorized | Authentication error |
| 404 Not Found | Requested resourse not found |
| 422 Unprocessable Entity | Request contains incorrect parameters |

## Working with production server

API requests to production server are sent to

```
https://go-fetch.com.au/public_api/v1/
```

1. Create a live GoFetch user account with the [production web app]
(http://app.go-fetch.com.au/) or the [iOS app](https://itunes.apple.com/au/app/gofetch/id1045358128?mt=8) and add a valid credit card. Your credit card will be charged when your jobs are delivered. If there are multiple credit cards associated with your account, only the first one will be used.

2. Retrieve your production authentication token with [create a session](endpoints/sessions.md#create) request. Store your authentication token securely and use it for all other API requests.

3. Check that your authentication works with a [hello world](endpoints/hello_world.md) request.

4. Congratulations! You are now ready to send your job creation (and other) API requests to the production server.

## Your help is welcome 👍

If you have a question or notice a problem with the API/documentation feel free to submit an issue or a pull request.

