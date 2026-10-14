# Ring Trail Cam

Built for and submitted to the [Build, Ship, Shape: Amazon Developer Hackathon](https://amazonappdev2026.devpost.com/) (Ring track).

Ring Trail Cam turns your Ring camera into a wildlife trail cam. When Ring reports motion that it did not tag as a person or a vehicle, the app downloads the clip through the Ring API, runs Google's SpeciesNet model on it, and adds the animal to a field journal in your browser. Clips with no animal in them are deleted.

**You need a Ring developer account to run this.** Ring Trail Cam isn't in the Ring Appstore. It runs on your own computer and connects to your camera through a private app that you create in the Ring developer console.

## What you need

- Python 3.11 or newer.
- A Ring developer account and a private app in the [Ring developer console](https://developer.amazon.com/ring/console/apps), with the Cameras and Doorbells scope. Keep the Client ID, Client Secret and HMAC Signature Key that Ring shows when you create the app.
- A Ring camera in the US, with a Ring Protect plan or trial on that Ring account.

## Quick start

```
git clone https://github.com/ella0333/ring-trailcam.git
cd ring-trailcam
python start.py
```

The first run installs what it needs, which takes a few minutes. The dashboard then opens at http://localhost:8000 and walks you through three steps:

1. Enter your app's Client ID, Client Secret and HMAC Signature Key.
2. The app opens a secure tunnel and shows four addresses. Paste them into your app's Account linking settings in the Ring developer console.
3. Open Connect on your app's page in the console, choose Log in with Ring, and sign in with the Ring account that has your camera.

From then on, every motion clip from your camera is checked for animals. The tunnel address changes each time the app starts, so update the addresses in the console when it does. The dashboard shows them under "Ring console addresses".

```
python stop.py
```

To start again with an empty field journal, run `python start.py --fresh`. It keeps your setup.

## More

[HOW-IT-WORKS.md](HOW-IT-WORKS.md) explains the pipeline and the Ring API calls.

MIT licensed.
