# shadow-cljs expo test

Consider this a pre-alpha Work in Progress. The goal here is to use `react-native` entirely without their packager running since that just gets in the way and makes things significantly more complicated. It is far from user-friendly but it works.

For this demo you'll need to have an actual Android or iOS device with the Expo app installed. The emulator does not work yet.

First clone and install `shadow-cljs`.

```
git clone https://github.com/shadow-cljs/expo-test.git
cd expo-test
npm install
```

We could technically use the folder created by `create-react-native-app` as the project root but I kinda wanted to isolate what it generates from the actual files required by `shadow-cljs` for demo purposes. So instead the actual `react-native` project is generated into a sub-directory "DemoApp".

```
npx create-react-native-app DemoApp
```

This takes a while but should eventually end in `Happy hacking!`. Do not run ANY of the printed instructions.

Instead just run `shadow-cljs` to compile our demo app.

```
# run one of these depending on which device you have available
npx shadow-cljs watch ios
npx shadow-cljs watch android

# or run both
npx shadow-cljs watch ios android
```

Once this finishes compiling you should be able to load the App in Expo.

It currently does not generate the QRCode you'd usually get from the CRNA tools but you can easily generate one online. I used https://www.qr-code-generator.com/.

Just generate a QRCode for the URL:

```
# for iOS
exp://<insert-your-ip-here>:18000
# for Android
exp://<insert-your-ip-here>:18001
```

`shadow-cljs` should have printed your IP on startup.

```
shadow-cljs - Using IP "192.168.1.13" from Interface "Intel(R) Ethernet Connection (2) I219-V"
```

So this would be

```
exp://192.168.1.13:18000
```

When you have the QRCode generated just scan it with the Expo App. It should load and show some text.

Live-Reload is enabled and should just work.