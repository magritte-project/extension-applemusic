# extension-applemusic

A Magritte extension which adds Apple Music as a content source and playback engine

[![Test](https://github.com/magritte-project/extension-applemusic/actions/workflows/test.yml/badge.svg)](https://github.com/magritte-project/extension-applemusic/actions/workflows/test.yml)

## Installation

### For Developers

The Magritte project uses [`asdf`](https://asdf-vm.com/) to manage tooling. Follow the Getting
Started directions to install `asdf` on your machine. Once you've installed `asdf`, you can
bootstrap your development environment:

```sh
$ ./bootstrap
```

Bootstrapping the development environment creates a `.env` file. Edit the entries the `.env` file to
be suitable for your local working environment.

Once your development environment is bootstrapped and you've filled in `.env`, you can start the
extension server:

```sh
$ pnpm dev
```

After the extension server has started, you can import the extension into your local Magritte
instance:

- Sign in to an administrator account
- Click the **User** menu in the top right corner
- Select **Settings**
- Select **Manage Extensions** in the **Admin** section
- Click the **+ Import Extension** button
- Enter your the extension’s development server URL, `http://localhost:9292/`

After an extension has been imported, any user can install it from Settings → Extensions in the user
menu.

## Configuration

The Apple Music extension reads its configuration from the environment, or from a `.env` file in the
current directory if one is present.

| Key             | Type   | Required | Description                                                  |
| --------------- | ------ | -------- | ------------------------------------------------------------ |
| TEAM_ID         | string | Yes      | ID of the team the Apple Music key was generated under       |
| APP_ID          | string | Yes      | ID of the app the Apple Music key is associated with         |
| KEY_ID          | string | Yes      | ID of the key on the Apple developer portal                  |
| KEY_SECRET      | string | Yes      | Contents of the key used to authenticate with Apple Music    |
| VITE_STOREFRONT | string | No       | Storefront that your Apple Music account is registered under |

The `KEY_SECRET` value may be in either JWK or PKCS8 format.

## Deployment

This extension can be built for deployment by running `pnpm build`. This will produce an express.js
server under `dist/`. It can be invoked with `node dist/server.js`.
