---
description: Getting transaction details
---

# Transactions

{% hint style="warning" %}
**Good to know:** link api key should be specified under API\_KEY header&#x20;
{% endhint %}

## Get link payments

{% swagger baseUrl="https://ab.cryptea.me/pay" method="get" path="/{linkname}/payments/{type}" summary="Get link payments made to the link" %}
{% swagger-description %}
{type} - sub, onetime or both
{% endswagger-description %}

{% swagger-parameter in="header" name="API_KEY" %}
key required for secured link
{% endswagger-parameter %}

{% swagger-parameter in="query" name="perPage" type="Number" %}
number of payments per page. Default 10
{% endswagger-parameter %}

{% swagger-response status="200" description="Success" %}
```javascript
{
    "error": false,
    "data": {
        "current_page": 1,
        "data": [
        {
            "id": 1,
            "data": "[]",
            "address": "10340293",
            "token": "matic",
            "amount": "10",
            "amountCrypto": "100",
            "type": "onetime",
            "hash": null,
            "created_at": "2022-09-25 01:32:19"
        }
        ],
        "first_page_url": "",
        "from": 1,
        "last_page": 2,
        "last_page_url": "",
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "",
                "label": "1",
                "active": true
            },
            {
                "url": "",
                "label": "2",
                "active": false
            },
            {
                "url": "",
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "next_page_url": "",
        "path": "",
        "per_page": 10,
        "prev_page_url": null,
        "to": 1,
        "total": 1
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}
```
{
    "error": true,
    "message": "unauthorized"
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Resource not found" %}
```javascript
{
    "error": true,
    "message": ""
}
```
{% endswagger-response %}
{% endswagger %}



## Get active subscriptions

{% swagger method="get" path="/{linkname}/payments/sub/active" baseUrl="https://ab.cryptea.me/pay" summary="Get link active subscriptions, if link supports subscriptions" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="API_KEY" type="string" %}
key required for secured links
{% endswagger-parameter %}

{% swagger-parameter in="query" name="perPage" type="Number" %}
number of items per page. Default 10
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful" %}
```javascript
{
    "error": false,
    "data": {
        "current_page": 1,
        "data": [
        {
            "id": 1,
            "data": "[]",
            "address": "10340293",
            "token": "matic",
            "amount": "10",
            "amountCrypto": "100",
            "type": "onetime",
            "hash": null,
            "created_at": "2022-09-25 01:32:19"
            "expire": null,
        }
        ],
        "first_page_url": "",
        "from": 1,
        "last_page": 2,
        "last_page_url": "",
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "",
                "label": "1",
                "active": true
            },
            {
                "url": "",
                "label": "2",
                "active": false
            },
            {
                "url": "",
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "next_page_url": "",
        "path": "",
        "per_page": 10,
        "prev_page_url": null,
        "to": 1,
        "total": 1
    }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized access" %}
```javascript
{
    "error": true,
    "message": "unauthorized access"
}
```
{% endswagger-response %}
{% endswagger %}



## Get expired subscriptions

{% swagger method="get" path="/{linkname}/payments/sub/expired" baseUrl="https://ab.cryptea.me/pay" summary="Get link expired subscriptions, if link supports subscriptions" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="perPage" type="Number" %}
number of items per page. Default 10
{% endswagger-parameter %}

{% swagger-parameter in="header" name="API_KEY" %}
key required for secured links
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="successfull" %}
```javascript
{
    "error": false,
    "data": {
        "current_page": 1,
        "data": [
        {
            "id": 1,
            "data": "[]",
            "address": "10340293",
            "token": "matic",
            "amount": "10",
            "amountCrypto": "100",
            "type": "onetime",
            "hash": null,
            "created_at": "2022-09-25 01:32:19"
            "expire": null,
        }
        ],
        "first_page_url": "",
        "from": 1,
        "last_page": 2,
        "last_page_url": "",
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "",
                "label": "1",
                "active": true
            },
            {
                "url": "",
                "label": "2",
                "active": false
            },
            {
                "url": "",
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "next_page_url": "",
        "path": "",
        "per_page": 10,
        "prev_page_url": null,
        "to": 1,
        "total": 1
    }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}
```javascript
{
    "error": false,
    "message": "unauthorized access"
}
```
{% endswagger-response %}
{% endswagger %}



## Show payment data

{% swagger method="get" path="{linkname}/{id}" baseUrl="https://ab.cryptea.me/pay" summary="Returns data for payment through id" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="API_KEY" %}
key required for secured links
{% endswagger-parameter %}

{% swagger-parameter in="path" name="id" type="Alphanumeric" required="true" %}
Id of requested payment data
{% endswagger-parameter %}

{% swagger-parameter in="path" name="linkname" type="alphanumeric" required="true" %}
name of link
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Resource found" %}
```javascript
{
    "error": false,
    "data": {
            "id": 1,
            "data": "[]",
            "address": "10340293",
            "token": "matic",
            "amount": "10",
            "amountCrypto": "100",
            "type": "onetime",
            "hash": null,
            "created_at": "2022-09-25 01:32:19"
        }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}
```javascript
{
    "error": true,
    "message": "unauthorized access"
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Not found" %}
```javascript
{
    "error": true,
    "message": "data not found"
}
```
{% endswagger-response %}
{% endswagger %}

