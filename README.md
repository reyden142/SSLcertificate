# SSLcertificate
How to create an SSL certificate for create-react-app 

## React Environment
```bash
npx create-react-app name-of-the-folder
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
