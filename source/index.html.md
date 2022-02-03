---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - java
  - python
  - swift
  - go
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the YO2 Retail API
---

# Introduction

Welcome to the `YO2-Retail` API! You can use our API to access any `YO2-Retail` API endpoints, which can get information on various products, payments, and cash transactions performed by the customer.

We have language bindings in Shell, Java, Python, Swift, Go, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Retail Reader API

## Get Payment Transaction Details

```java
import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Response response = client.target(
  "https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?fromdate=2022-01-01&todate=2022-02-03&page=0&rows=100")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Bearer [token]")
  .get();
System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body: "+ response.readEntity(String.class));
```

```python
import requests

headers = {
  'Authorization': 'Bearer [token]'
}

response = requests.get(
  'https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?fromdate=2022-01-01&todate=2022-02-03&page=0&rows=100',
  headers=headers
)

print(response.status_code)
print(response.headers)
print(response.text)
```

```shell
curl "https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?fromdate=2022-01-01&todate=2022-02-03&page=0&rows=100" \
  -H "Authorization: [token]" -H "Content-Type: application/json" -H "Accept: application/json"
```

```swift
import Foundation

let url = URL(string: "https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?fromdate=2022-01-01&todate=2022-02-03&page=0&rows=100")!
var request = URLRequest(url: url)
request.addValue("Bearer [token]", forHTTPHeaderField: "Authorization")

let task = URLSession.shared.dataTask(with: request) {data, response, error in
  if let response = response {
    print(response)

    if let data = data, let body = String(data: data, encoding: .utf8) {
      print(body)
    }
  } else {
    print(error ?? "Unknown error")
  }
}

task.resume()
```

```go
package main

import (
	"fmt"
	"io/ioutil"
	"net/http"
)

func main() {
	client := &http.Client{}

	req, _ := http.NewRequest(
    "GET",
    "https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?fromdate=2022-01-01&todate=2022-02-03&page=0&rows=100",
    nil,
  )

	req.Header.Add("Authorization", "Bearer [token]")

	resp, err := client.Do(req)

	if err != nil {
		fmt.Println("Errored when sending request to the server")
		fmt.Println(err)
		return
	}

	defer resp.Body.Close()
	resp_body, _ := ioutil.ReadAll(resp.Body)

	fmt.Println(resp.Status)
	fmt.Println(resp.Header)
	fmt.Println(string(resp_body))
}
```

```javascript
const request = new XMLHttpRequest();

request.open(
  "GET",
  "https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?fromdate=2022-01-01&todate=2022-02-03&page=0&rows=100"
);
request.setRequestHeader("Authorization", "Bearer [token]");

request.onreadystatechange = function () {
  if (this.readyState === 4) {
    console.log("Status:", this.status);
    console.log("Headers:", this.getAllResponseHeaders());
    console.log("Body:", this.responseText);
  }
};

request.send();
```

> The above command returns JSON structured like this:

```json
[
  {
    "source": "S02",
    "sourcedesc": "GIFT",
    "purpose": "P200",
    "status": 0,
    "transactionrefno": "005222478403624711",
    "transactiondate": "2022-01-24T08:06:10.129",
    "transactiontype": "SD",
    "agentlocationid": 784101,
    "agentlocationname": "AL WAHDA",
    "agentrefno": "6574575544",
    "amountinsettlmentccy": 500,
    "amountintoccy": 500,
    "createdby": "786000750",
    "createdon": "2022-01-24T08:06:10.128",
    "customeraddress": "ALWAHDA STREET 1",
    "customercategory": 2,
    "customerfirstname": "SFC ALWAHDA",
    "customeridname": "SFC ALWAHDA",
    "customeridno": "32423487",
    "customeridtype": "5",
    "customeridvalidthru": "2023-07-31T06:43:28",
    "customerlastname": "",
    "customermiddlename": "",
    "customermobileno": "",
    "customerno": "7",
    "customerremarks": "142345",
    "exchangerate": 1,
    "fromccycode": "AED",
    "toccycode": "AED",
    "invoicenumber": "78410022000000000365",
    "issuedon": "2022-01-24T08:06:10.128",
    "merchantid": "056592",
    "merchantname": "SFC",
    "transactionamount": 500,
    "totalcharges": 0,
    "totaltransactionamount": 500,
    "totalvatamount": 0,
    "othercharges": 0,
    "paymentmode": "CS",
    "productgroupname": "CASH COLLECTION",
    "productid": "5",
    "productname": "CASH COLLECTION",
    "purposedesc": "AIR TRANSPORT",
    "ratesessionid": "123123",
    "serviceid": "967382",
    "servicename": "string",
    "serviceproviderid": "784100",
    "serviceprovidername": "ABC",
    "settlementccy": "AED"
  },
  {
    "source": "S02",
    "sourcedesc": "GIFT",
    "purpose": "P200",
    "status": 0,
    "transactionrefno": "005222478407250521",
    "transactiondate": "2022-01-24T08:06:51.39",
    "transactiontype": "SD",
    "agentlocationid": 784101,
    "agentlocationname": "AL WAHDA",
    "agentrefno": "6574575544",
    "amountinsettlmentccy": 500,
    "amountintoccy": 500,
    "createdby": "786000750",
    "createdon": "2022-01-24T08:06:51.39",
    "customeraddress": "ALWAHDA STREET 1",
    "customercategory": 2,
    "customerfirstname": "SFC ALWAHDA",
    "customeridname": "SFC ALWAHDA",
    "customeridno": "32423487",
    "customeridtype": "5",
    "customeridvalidthru": "2023-07-31T06:43:28",
    "customerlastname": "",
    "customermiddlename": "",
    "customermobileno": "",
    "customerno": "7",
    "customerremarks": "142345",
    "exchangerate": 1,
    "fromccycode": "AED",
    "toccycode": "AED",
    "invoicenumber": "78410022000000000367",
    "issuedon": "2022-01-24T08:06:51.39",
    "merchantid": "056592",
    "merchantname": "SFC",
    "transactionamount": 500,
    "totalcharges": 0,
    "totaltransactionamount": 500,
    "totalvatamount": 0,
    "othercharges": 0,
    "paymentmode": "CS",
    "productgroupname": "CASH COLLECTION",
    "productid": "5",
    "productname": "CASH COLLECTION",
    "purposedesc": "AIR TRANSPORT",
    "ratesessionid": "123123",
    "serviceid": "967382",
    "servicename": "string",
    "serviceproviderid": "784100",
    "serviceprovidername": "ABC",
    "settlementccy": "AED"
  }
]
```

This endpoint retrieves all payment transaction details.

### HTTP Request

`GET https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails`

### Query Parameters

| Parameter | Required | Description                                                            |
| --------- | -------- | ---------------------------------------------------------------------- |
| fromdate  | No       | If set, the result will be filtered by the starting date.              |
| todate    | No       | If set, the result will be filtered by the end date.                   |
| rows      | No       | Limit the number of records being displayed per page. Default to 1000. |
| txnrefno  | No       | If set, result will be filtered by the transaction ref number.         |

<aside class="warning">
Remember — you must replace `[token]` with your API key you got when you subscribe to our API plan.
</aside>

## Get a Specific Transaction Ref.No

```java
import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Response response = client.target(
  "https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?txnrefno=005222478403624711")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Bearer [token]")
  .get();
System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body: "+ response.readEntity(String.class));
```

```python
import requests

headers = {
  'Authorization': 'Bearer [token]'
}

response = requests.get(
  'https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?txnrefno=005222478403624711',
  headers=headers
)

print(response.status_code)
print(response.headers)
print(response.text)
```

```shell
curl "https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?txnrefno=005222478403624711" \
  -H "Authorization: [token]" -H "Content-Type: application/json" -H "Accept: application/json"
```

```swift
import Foundation

let url = URL(string: "https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?txnrefno=005222478403624711")!
var request = URLRequest(url: url)
request.addValue("Bearer [token]", forHTTPHeaderField: "Authorization")

let task = URLSession.shared.dataTask(with: request) {data, response, error in
  if let response = response {
    print(response)

    if let data = data, let body = String(data: data, encoding: .utf8) {
      print(body)
    }
  } else {
    print(error ?? "Unknown error")
  }
}

task.resume()
```

```go
package main

import (
	"fmt"
	"io/ioutil"
	"net/http"
)

func main() {
	client := &http.Client{}

	req, _ := http.NewRequest(
    "GET",
    "https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?txnrefno=005222478403624711",
    nil,
  )

	req.Header.Add("Authorization", "Bearer [token]")

	resp, err := client.Do(req)

	if err != nil {
		fmt.Println("Errored when sending request to the server")
		fmt.Println(err)
		return
	}

	defer resp.Body.Close()
	resp_body, _ := ioutil.ReadAll(resp.Body)

	fmt.Println(resp.Status)
	fmt.Println(resp.Header)
	fmt.Println(string(resp_body))
}
```

```javascript
const request = new XMLHttpRequest();

request.open(
  "GET",
  "https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?txnrefno=005222478403624711"
);
request.setRequestHeader("Authorization", "Bearer [token]");

request.onreadystatechange = function () {
  if (this.readyState === 4) {
    console.log("Status:", this.status);
    console.log("Headers:", this.getAllResponseHeaders());
    console.log("Body:", this.responseText);
  }
};

request.send();
```

> The above command returns JSON structured like this:

```json
[
  {
    "source": "S02",
    "sourcedesc": "GIFT",
    "purpose": "P200",
    "status": 0,
    "transactionrefno": "005222478403624711",
    "transactiondate": "2022-01-24T08:06:10.129",
    "transactiontype": "SD",
    "agentlocationid": 784101,
    "agentlocationname": "AL WAHDA",
    "agentrefno": "6574575544",
    "amountinsettlmentccy": 500,
    "amountintoccy": 500,
    "createdby": "786000750",
    "createdon": "2022-01-24T08:06:10.128",
    "customeraddress": "ALWAHDA STREET 1",
    "customercategory": 2,
    "customerfirstname": "SFC ALWAHDA",
    "customeridname": "SFC ALWAHDA",
    "customeridno": "32423487",
    "customeridtype": "5",
    "customeridvalidthru": "2023-07-31T06:43:28",
    "customerlastname": "",
    "customermiddlename": "",
    "customermobileno": "",
    "customerno": "7",
    "customerremarks": "142345",
    "exchangerate": 1,
    "fromccycode": "AED",
    "toccycode": "AED",
    "invoicenumber": "78410022000000000365",
    "issuedon": "2022-01-24T08:06:10.128",
    "merchantid": "056592",
    "merchantname": "SFC",
    "transactionamount": 500,
    "totalcharges": 0,
    "totaltransactionamount": 500,
    "totalvatamount": 0,
    "othercharges": 0,
    "paymentmode": "CS",
    "productgroupname": "CASH COLLECTION",
    "productid": "5",
    "productname": "CASH COLLECTION",
    "purposedesc": "AIR TRANSPORT",
    "ratesessionid": "123123",
    "serviceid": "967382",
    "servicename": "string",
    "serviceproviderid": "784100",
    "serviceprovidername": "ABC",
    "settlementccy": "AED"
  }
]
```

This endpoint retrieves a specific transaction based on given transaction reference number.

### HTTP Request

`GET https://yo2rdev.luluone.com/retail-reader/yo2/getPaymentTransactionDetails?txnrefno=<txnrefno>`

### URL Parameters

| Parameter | Description                 |
| --------- | --------------------------- |
| txnrefno  | The transaction ref number. |

<aside class="warning">Remember — you must replace `[token]` with your API key you got when you subscribe to our API plan.</aside>
