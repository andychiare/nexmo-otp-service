# OTP service via Nexmo Dispatch APIs

This is a Node.js sample project showing how to create an OTP (*One Time Password*) Web service using the [Nexmo Dispatch APIs](https://www.nexmo.com/products/dispatch) as delivery service.

## Setting up the project

To setup the project, ensure you have [Node.js 8.11+](https://nodejs.org) installed and clone this repository. Then run the following command to install the required package dependencies:

```shell
npm install
```

After installing the dependencies, you can run the project by typing:

```shell
npm start
```

A web server listening on port 3000 will be started.

## Using the APIs

The project defines two Web APIs: the first API allows you to create a new OTP, and the second one allows you to verify it.

### Configuring the server

Before using the APIs, you need to set the *Nexmo* parameters needed to send the OTP to the requesting user. You can provide these parameters by setting your configuration data in the `nexmo.json` file.

You also need to store your private key in the `private.key` file.

### Creating the OTP

In order to create a new OTP you should submit a POST request like the following:

```http
POST /otp/123456789 HTTP/1.1
Host: localhost:3000
Content-Type: application/json
cache-control: no-cache
Postman-Token: 759b8a9f-ac82-4e66-afd3-144e039ca23d
{"messengerId": "8192836451", "phoneNumber": "393393423268"}
```

The `123456789` value identifies your request and is up to you providing it.

If the server creates the OTP, you should receive the *201 Created* HTTP status.

### Verifying the OTP

By submitting a GET request like the following, you can verify the OTP received via *Messenger* or SMS:

```http
GET /otp/123456789/63731 HTTP/1.1
Host: localhost:3000
Content-Type: application/json
cache-control: no-cache
```

If the OTP is valid, you will receive a *200 OK* HTTP status.

