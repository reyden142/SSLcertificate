# SSL Certificate for **create-react-app**

## Overview
An **SSL certificate** (Secure Sockets Layer certificate) is a digital certificate that authenticates the identity of a website and enables an encrypted connection between the web server and the browser. It secures data transmitted over the internet, such as login credentials, credit card information, and other sensitive data.

When a website has an SSL certificate:
- The URL starts with **"https://"** instead of "http://".
- A padlock symbol appears in the browser’s address bar, indicating a secure connection.

In this guide, we'll show you how to set up SSL certificates for a **Create React App** project.

## Step 1: Create a React Application
To get started, first create a new React app using `create-react-app`:

```bash
npx create-react-app name-of-the-folder
```
Replace `name-of-the-folder` with your desired folder name.

## Step 2: Install mkcert
To generate locally trusted SSL certificates, we’ll use **mkcert**. Install it on your Windows system using Chocolatey (a package manager for Windows):
```bash
choco install mkcert
```
After installation, you’ll need to install the local Certificate Authority (CA) by running:
```bash
mkcert -install
```

## Step 3: Generate SSL Certificates
Now, create the SSL certificates for your development environment:
```bash
# Create a folder to store the certificates
mkdir -p .cert

# Generate the certificates for localhost (or replace with your desired domain/IP)
mkcert -key-file ./.cert/key.pem -cert-file ./.cert/cert.pem "localhost"
```
You can replace `"localhost"` with any domain or IP address (e.g., `192.168.1.25`, `www.example.com`).

## Step 4: Configure SSL in package.json
Next, update your `package.json` file to tell your React app to use the generated SSL certificates:
```json
"scripts": {
    "start": "set HTTPS=true&&set SSL_CRT_FILE=./.cert/cert.pem&&set SSL_KEY_FILE=./cert/key.pem&&react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  }
```
This will enable SSL when starting the development server.

## Alternative: Use .env File
As an alternative to updating `package.json`, you can configure SSL in a `.env` file for a cleaner approach. Simply add the following to your `.env` file:
```bash
HTTPS=true
SSL_CRT_FILE=./.cert/cert.pem
SSL_KEY_FILE=./.cert/key.pem
```

## Conclusion
Now, when you start your React app using `npm start`, it will run over **HTTPS** using the certificates you created. The browser will display the secure padlock symbol, indicating that the connection is secure.
