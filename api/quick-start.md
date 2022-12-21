# 🚀 Quick Start

## Get your Link API key

Your API requests can be authenticated using API key. Any request to a secured link that doesn't include an API key in the header will return unsuccessful.&#x20;

You can generate an API key from your Dashboard, select the link you want, once taken to the overview page of that link, select API/SDK and generate key, This would generate the key and secure the link API for requests.&#x20;

{% hint style="danger" %}
You will not be able to view this key again once you close this window, so be sure to record it, Clicking the generate button would generate a new key invalidating older keys.
{% endhint %}



## Make your first request

To make your first request, send an authenticated request to the pay/{linkname}. This will bring back a link to be used for payment based on link data or provided data

{% hint style="info" %}
**Good to know:** link API key should be specified under API\_KEY header&#x20;
{% endhint %}

{% swagger baseUrl="https://ab.cryptea.me/pay" method="post" path="/{linkName}" summary="Initializes a new payment." %}
{% swagger-description %}
Parameters in body is most likely predefined by link data specified during link creation
{% endswagger-description %}

{% swagger-parameter in="body" name="callback_url" required="false" type="string" %}
Url to redirect to after payment
{% endswagger-parameter %}

{% swagger-parameter in="body" name="amount" required="false" type="number" %}
Amount in (USD) to be paid in crypto
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" required="false" type="json" %}
data to be embedded in payment data
{% endswagger-parameter %}

{% swagger-parameter in="header" name="API_KEY" type="string" %}
key required for secured link api
{% endswagger-parameter %}

{% swagger-response status="200" description="Operation Successful" %}
```javascript
{
   "error": false,
   "message": "successful",
   "url": "generated link"
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}
```javascript
{
    "error": true,
    "message": "unauthorized"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Bad request" %}
```javascript
{
    "error": true,
    "message": "error message"
}
```
{% endswagger-response %}
{% endswagger %}
