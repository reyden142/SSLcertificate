# SSL Certificate
How to create an SSL certificate for **create-react-app**

## Overview
An SSL certificate (Secure Sockets Layer certificate) is a digital certificate that authenticates the identity of a website and enables an encrypted connection between a web server and a browser. SSL is used to secure data that is transmitted over the internet, such as login credentials, credit card details, or any other sensitive information.

When a website has an SSL certificate, its URL starts with **"https://"** instead of "http://", and a padlock symbol is displayed in the browser’s address bar, indicating that the connection is secure.

## React Environment
```bash
npx create-react-app name-of-the-folder
```

## Install mkcert
To install mkcert on Windows using Chocolatey (a package manager for Windows), you can run the following command in your command line:
```bash
choco install mkcert
```
To install the local CA (Certificate Authority), run:
```bash
mkcert -install
```

## How to create a certificate
```bash
//create a certficate folder
mkdir -p .cert
//create the actual certificates in the folder 
mkcert -key-file ./.cert/key.pem -cert-file ./.cert/cert.pem "localhost"
```
You can change the "localhost" to any IP address or website (e.g. 192.168.1.25 or www.example.com)

## Update the package.json file
```json
"scripts": {
    "start": "set HTTPS=true&&set SSL_CRT_FILE=./.cert/cert.pem&&set SSL_KEY_FILE=./cert/key.pem&&react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  }
```

## Alternative for package.json
You can update your .env file
```bash
HTTPS=true
SSL_CRT_FILE=./.cert/cert.pem
SSL_KEY_FILE=./.cert/key.pem
```
