# Job status webhook

Supply a URL that will be called by GoFetch to notify you when the status of a delivery job changes.

* [Show](#show-the-job-status-webhook)
* [Update](#update-the-job-status-webhook)
* [Remove](#remove-the-job-status-webhook)
* [Test](#test-the-job-status-webhook)

### Webhook URL

GoFetch will send a POST request to your webhook URL with JSON data, for example:


```JSON
{
  "job_id": "b3131f1d-b501-4f48-a31d-af8e6302540b",
  "job_status": "delivered"
}
```

The `job_status` parameter will be one of the following:

| Status | Description |
| --- | --- |
| delivered | The item has been delivered |
| fetcher_approaching_dropoff | Fetcher is within 100 meters from the dropoff location |


## Show the job status webhook

`GET webhooks/job_status`

Returns your job status webhook URL.


### Response

```JSON
{
  "url": "https://website.net/example"
}
```

### cURL example

```shell
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks/job_status
```




## Update the job status webhook

`PUT webhooks/job_status`

If the webhook does not exist, it will create one. Returns empty response.

### Request data


```JSON
{
  "url": "https://website.net/example"
}
```

Save the webhook URL.


### cURL example


```shell
curl -X PUT -d '{"url": "http://webhook42.net/example"}' -H 'Content-Type: application/json' -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks/job_status
```




## Remove the job status webhook


`DELETE webhooks/job_status`

Remove the job_status webhook if you no longer with to receive the notifications.

### cURL example


```shell
curl -X "DELETE" -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks/job_status
```





## Test the job status webhook


`POST webhooks/job_status/test`

Sends a test HTTP request to your webhook URL. This can be useful for debugging your API integration.

### Request data

Supply the *job_id* and *job_status* values that will be sent to your webhook URL. The job does not need to exist, and if it does, this request will not change the status of the job.

```JSON
{
  "job_id": "b3131f1d-b501-4f48-a31d-af8e6302540b",
  "job_status": "fetcher_approaching_dropoff"
}
```

### cURL example

Calls your *job status* webhook with the supplied data.

```shell
curl -d '{"job_id": "b3131f1d-b501-4f48-a31d-af8e6302540b", "job_status": "fetcher_approaching_dropoff"}' -H 'Content-Type: application/json' -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks/job_status/test
```
