#Fuseki

Based heavily on Crush & Lovely's iOS boilerplate project Amaro, but tailored for our workflow.

## Gimme gimme

Change to your projects directory, download the setup file and run:

$ ruby setup

TODO DOC:

Open project and changed scheme to shared.
Setup hockeyapp
Setup slack intergration

### Foundation
* A local git repository for the application is created (and committed to a few times through the initialization process).
* A sane `.gitignore` file is included.
* A `Certificates` directory is included with a readme file about what to include so that other developers can test and release the app.
* Sensible defaults for build options, warnings, and the like.
    * Build configurations are split into xcconfig files for modularity and consistency. We're using [jspahrsummers/xcconfigs](https://github.com/jspahrsummers/xcconfigs) as our base.
    * There are separate staging, production, and distribution schemes, and corresponding preprocessor macros. No more fiddling with variables here and there to switch your target environment.
* Automatic ways to easily distinguish between builds of the app:
    * Ad-hoc and development builds have their bundle id suffixed with ".adhoc" or ".dev" so that they can co-exist on devices with other builds.
    * Ad-hoc and development builds' icons are badged with an 🅢 for staging environments and a 🅟 for production environments. The bundle names (but not the display names) are also changed to easily distinguish them in places where it may otherwise be difficult.
* The build number of the app is incremented on every ad-hoc and distribution build. This ensures that external distribution services can reliably distinguish builds, even if the version number itself doesn't change.
* [CocoaPods](http://cocoapods.org) are integrated from the get-go.
* A barebones settings bundle is included with an "Acknowledgements" section that includes licenses for all your pods. It's automatically updated after each `pod install`.
* Identifiers from storyboards and asset catalogs are pulled out into constants, much like [objc-codegenutils](https://github.com/puls/objc-codegenutils).

