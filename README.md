# Proof of Existence

An online service to prove the existence of documents

## Instructions

### Setup

#### Mac OS X

- Install brew: https://brew.sh/
- brew install git (will trigger installation of Xcode, do it!)
- Follow guide https://treehouse.github.io/installation-guides/mac/node-mac.html
- Ready!

```sh
git clone git@github.com:poexio/proofofexistence.git
cd proofofexistence
```

### Installation

```sh
npm install
```

#### Configuration

```sh
node setup.js
```

Edit `.env` for environment variables. All values are **required**.

* `PORT` - The local port to run the app on.
* `HOST` - The host or domain name.
* `HOST_SCHEME` - e.g, `http` or `https`
* `HOST_PORT` - e.g., `80` or `443`
* `DB_PATH` - Path to the LevelDB directory.
* `DOCUMENT_PRICE` - Document certification price in satoshis.
* `SIGN_PRICE` - Document signing price in satoshis.
* `BLOCKCYPHER_TOKEN` - BlockCypher API token.
* `BITCOIN_HD_PRIVATE_KEY` - HD wallet private key for generating addresses.
* `BITCOIN_HD_PUBLIC_KEY` - HD wallet public key for receiving payments.
* `MAGIC_NUMBER` - Token for some private API routes.
* `MAIL_FROM` - Name/email to send as.
* `MAIL_TO` - Email address to send notifications to.
* `GMAIL_USER` - GMail account for sending notifications.
* `GMAIL_PASS` - Gmail password for sending notifications.

Any environment variables that are set when the app is run will override the
values in the `.env` file.

### Building

```sh
npm run build
```

### Running

```sh
npm run watch
```

The app will be listening at http://localhost:3003/.

### Testing

To run the app in test mode, create a `.env.test` file with the desired
configuration.

You must use a **Testnet3 wallet** for the public and private keys. It is
recommended to change the database path to a `/tmp` location.

Run the app in test mode with:

```sh
NODE_ENV=test npm run watch
```

### Production

Build the app:

```sh
npm run build
```

The production app is run with:

```sh
NODE_ENV=production npm run serve
```

To clean up:

```sh
npm run clean
```

### Deployment

```sh
ssh ubuntu@poex.io
cd /home/ubuntu/poex/
git pull origin master
npm install
npm run build
sudo service poex_prod restart
```

### News

The `/news` route should be handled by [poexio/poex-news]. This can be
configured in Nginx with a directive like:

```
location /news {
        alias /home/ubuntu/news/_site;
        error_page 404 /news/404.html;
}
```

## License

© Copyright 2017 PoEx Limited, all rights reserved.<br />
© Copyright 2015-2017 Smart Contract Solutions Inc., all rights reserved.

[poexio/poex-news]: https://github.com/poexio/poex-news
