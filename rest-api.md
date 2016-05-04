---
layout: page
title: REST API
permalink: /rest-api/
---

## Getting started

### Making requests

The ChartBlocks API is hosted at [https://api.chartblocks.com/v1/](https://api.chartblocks.com/v1/). The API is 
REST based, providing access to chart, set, data and user information.

To generate charts on-the-fly, please see the Image API.

### SDK's

To get you up and running with the API as quickly as possible we've implemented 
an [SDK for PHP](https://github.com/ChartBlocks/php-rest-sdk). Other languages 
will be available shortly.

### Authorization

The majority of API calls must be made as an authorized user. An ACCESS_TOKEN and
SECRET_KEY can be generated from your ChartBlocks profile page. Together these 
are used to sign requests.

## Authorizing a request

We'd suggest using one our pre-built SDKs if you're new to development, but to
authenticate requests in your own clients, please read on.

Your SECRET_KEY is never sent in the request, only the ACCESS_TOKEN. The 
SECRET_KEY is used to generate a SIGNATURE which both authenticates the request
as coming from you, and mitigates man in the middle attacks.

The signature is sent in your HTTP request using the **Authorization** header in the format:

{% highlight js %}
'Authorization: BASIC ' . base64_encode($ACCESS_TOKEN . ':' . $SIGNATURE);
{% endhighlight %}

### Generating a signature

This snippet of psuedo code describes how to generate a signature. It should be
possible to implement this in your language of choice.

{% highlight js %}
var key1 = sha1(body);
var key2 = key1 . SECRET_KEY;
var key3 = sha1(key2);
var signature = base64_encode(key3);
{% endhighlight %}

The **body** variable is your request body. For a GET request this would be your 
query parameters in the format:

> param1=val&param2=val

For POST, PUT and PATCH requests this would be your request body, normally a
JSON document, i.e.:

{% highlight json %}
{
  "name": "My Chart",
  "isPublic": true
}
{% endhighlight %}

The SECRET_KEY is obtained along with the ACCESS_TOKEN from the profile page
of your ChartBlocks account.


### Item tokens

Charts and datasets can are assigned a token, allowing people without a 
ChartBlocks account to view *private* items providing they know the token.

To request a chart or set with a token, pass the given token as a GET
parameter of **t**, i.e.

> https://api.chartblocks.com/v1/chart/541fdd38c9a61d68707f9d86**?t=c9ea94ad**


## Chart config

The chart config object can end up rather large, and contains enough parameters
to warrant its own documentation page. Please reference the [Chart Config](/chart-config)
documentation separately for more information on how to format your config 
object.

## Resources 
{% for group in site.data.rest.apidoc.groups %}
  {% include rest/group.html group = group %}
{% endfor %}
