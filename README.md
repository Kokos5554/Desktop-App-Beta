> You're currently viewing the README file for v2.20, which is not out yet. v2.20 is planned to be released on __December 1st__.
# FalixNodes Beta
![image](https://i.imgur.com/nHUmzBG.png)
The FalixNodes application was built for users to have a quicker access to their FalixNodes client, panel, servers, and VPS(s) all through one place. We also include our help center in there if needed.

### Requirements
[Git](https://git-scm.com/downloads)

[Node](https://nodejs.org/en/download/)(v12 or up)

### Building
Clone project:
```
git clone https://github.com/FalixNodes-Software/Desktop-App
```
Change directory:
```
cd Desktop-App
```
Install packages:
```
npm install electron@9.0.5
npm install electron-builder
```
*Electron 9.0.5 is recommended for FalixNodes Software, as certain things broke in newer versions*

Run Build command:
```
npm run build
```
When building, it will build a setup file for your operating system, so if you're on Windows, it will create a EXE file; or if you're on Linux, it will create an AppImage and a Snap file; or if you're on macOS, it will create a DMG file.

### Setting up Auto Update
If you're forking the project and want to create something similar, but also want auto updating, here's how. Electron Builder is required for this, which is why it's used in v2.20 of FalixNodes Software. From personal experience, this appears to mostly work on Windows only.

There are some requirements in this:
 - A [GitHub token](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token)
 - [`electron-builder`](https://www.npmjs.com/package/electron-builder) package
 
 You need to change a few things in `package.json` so that Electron Builder knows where to publish updates, we recommend GitHub as provider.
 What you need to change, is the build area of the `package.json` file, example:
 ```
   "build": {
    "publish": [
      {
        "provider": "github",
        "owner": "UsernameOrOrangization",
        "repo": "repo-name",
        "token": "GITHUBTOKEN"
      }
    ]
  }
  ```
 
 GitHub token is required so that Electron Builder has permission to create new releases in the repo.
 
 Once you're ready to publish an update, make the version number in `package.json` has been raised to a newer number. Then run the publish command:
 ```
 npm run publish
 ```
 When running the publish command, Electron Builder will start building setup files for your operating system, create a new release under the name of the version number(x.x.x), and then upload setup files to the new release. By default, Electron Builder will create a new release as a draft, giving you time to add a changelog and such to the release. You'll need to set it to publish and you're done!
 
 Once the release is set to publish on GitHub, the app will detect it, starting downloading, then install it.
