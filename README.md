# Copyedit

The Web and iOS UI for the CopyEdit App powered by ChatGPT.

For setting up the API check out the following repositories:

[CopyEdit GPT Lambda API](https://github.com/eddietejeda/copyedit-gpt-lambda)
[Langchain Lambda Layer](https://github.com/eddietejeda/aws-langchain-lambda-layer)


## Framework7 CLI Options

Framework7 app created with following options:

```
{
  "cwd": "./copyedit-svelte-app",
  "type": [
    "web",
    "capacitor"
  ],
  "name": "Copyedit",
  "framework": "svelte",
  "template": "tabs",
  "bundler": "vite",
  "cssPreProcessor": false,
  "theming": {
    "customColor": false,
    "color": "#007aff",
    "darkMode": false,
    "iconFonts": true
  },
  "customBuild": false,
  "pkg": "io.framework7.copyedit ",
  "capacitor": {
    "platforms": [
      "android",
      "ios"
    ]
  }
}
```

## Install Dependencies

First of all we need to install dependencies, run in terminal
```
npm install
```

## NPM Scripts

* 🔥 `start` - run development server
* 🔧 `dev` - run development server
* 🔧 `build` - build web app for production
* 📱 `build-capacitor-ios` - build app and copy it to iOS capacitor project
* 📱 `build-capacitor-android` - build app and copy it to Android capacitor project

## Vite

There is a [Vite](https://vitejs.dev) bundler setup. It compiles and bundles all "front-end" resources. You should work only with files located in `/src` folder. Vite config located in `vite.config.js`.
## Capacitor

This project created with Capacitor support. And first thing required before start is to add capacitor platforms, run in terminal:

```
npx cap add android && npx cap add ios
```

Check out [official Capacitor documentation](https://capacitorjs.com) for more examples and usage examples.

## Assets

Assets (icons, splash screens) source images located in `assets-src` folder. To generate your own icons and splash screen images, you will need to replace all assets in this directory with your own images (pay attention to image size and format), and run the following command in the project directory:

```
framework7 assets
```

Or launch UI where you will be able to change icons and splash screens:

```
framework7 assets --ui
```

## Capacitor Assets

Capacitor assets are located in `resources` folder which is intended to be used with `cordova-res` tool. To generate  mobile apps assets run in terminal:

```
sudo gem install cocoapods
cd ./ios/App
pod install
cd ../../
npx cordova-res
npx cap open ios
```

Check out [official cordova-res documentation](https://github.com/ionic-team/cordova-res) for more usage examples.

## Documentation & Resources

* [Framework7 Core Documentation](https://framework7.io/docs/)


* [Framework7 Svelte Documentation](https://framework7.io/svelte/)
* [Framework7 Icons Reference](https://framework7.io/icons/)
* [Community Forum](https://forum.framework7.io)

## Support Framework7

Love Framework7? Support project by donating or pledging on:
- Patreon: https://patreon.com/framework7
- OpenCollective: https://opencollective.com/framework7