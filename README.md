# SiaUs-iOS

Main purpose of this repository is to show you how to work with Sia `us` framework on simple demo project. `Us.Framework` is compiled version of `us` project written in `go` (https://github.com/lukechampine/us) and it is alternative and low level API for `Sia` (decentralized cloud storage platform).

This demo iOS app works with Sia `host address` and `contract data` (string of 192 characters) you can prepare on your personal Sia node and use them to upload selected photo from your iPhone's photo library directly to the host. After doing so, it will locally store the `.usa` file which is required in order to download the photo later.

TLDR: You can upload and download photos on the Sia platform! Yay!

# Prerequisites

This project was created with Xcode 10.2 and doesn't have any pods or dependencies. All you need is in the project already and works out of the box. It should serve as inspiration for you.

What you will definitely need are the `host address` and `contract data` mentioned earlier (follow instructions HERE).

If you are new to Sia and you got to this repo accidentally, make sure to check the tutorial which this readme is second part of: https://medium.com/p/6c7077da6c18

# Updating and importing `Us.Framework`

You don't need to do it right now because the framework version in this project has all features this demo needs. But if you are going to build more advanced apps and require the framework to expose more of the `us` functions, you will need to know how you update it, compile and import new framework version into your project.

You can find detailed instructions for the compilation of the framework HERE. Once done, all you need to do is to open `SiaUs-iOS / SiaUs / Frameworks` folder and replace `Us.Framework`. Alternatively, you can just delete old one and drag the new version in the Xcode directly. You will need to do this each time you compile the framework unless you make some script to automate this for you.

# Running the app

Next step is to open the project `SiaUs-iOS / SiaUs.xcodeproj`, build it and run it in simulator.

Once launched, just enter the `host address` and `contract data`. As writing 192 characters is quite difficult, you can use any of these two options:

- open `Constants.swift` and change value of `testContract` to your 192 characters long string (return it to nil if you want to stop pre-filling it after launch)
- use the `Scan Contract (QR Code)` button in the app, for example to scan QR code with the contract data you generated on your computer

Now all you need to do is write name of the file. Whatever you choose, it will be used as a name of the selected photo and `.png` automatically added to it.

Then you can select any photo from your library (if you run on actual iPhone, else it will show you default library with few images of nature that come with the simulator) and touch `Upload` button. For average photo this can take some time (see in the video), so be patient, but no worries. The app ignores any touches during the upload/download. Also it remembers your previously filled values after restart.

# Troubleshooting

I don't expect issues with the app but can imagine some issues coming from your Sia node. For example, insufficient funding as each upload and download costs you something in SC for the host's bandwidth. Just let me know if you run into issues and I will update the repo as neccessary.
