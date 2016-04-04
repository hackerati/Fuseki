#Fuseki

Based on Crush & Lovely's iOS boilerplate.

## Gimme gimme
Change to your projects directory, run this line in your terminal, and follow the prompts:

```sh
ruby -e "$(curl -fsSL https://raw.github.com/thehackerati/Fuseki/master/tiramisu)"
```

## Details and Requirements
The bootstrap assumes:

* You are using Xcode 7 or later.
* You have version 0.34.1 or later of the [CocoaPods gem](http://cocoapods.org/#install) installed.
* You are on OS 10.9 or later
* You are targetting iOS 8.0, at minimum (and thus will be compiling against at least the iOS 8.0 SDK).
    * As of [October 2015](https://developer.apple.com/support/appstore/), 91% of iOS devices are on iOS 8 or later.

### Foundation
* A well-chosen class prefix is enforced (or may be omitted entirely... [the times, they are a-changin'](http://inessential.com/2014/07/24/prefixes_considered_passe))
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

### Logging, Error Reporting, Testing
* [CocoaLumberjack](https://github.com/CocoaLumberjack/CocoaLumberjack) is configured for logging. A [custom formatter](https://github.com/crushlovely/Sidecar/blob/master/Sidecar/CRLMethodLogFormatter.h) is used by default to include the class and method name in log messages.
* [Specta](https://github.com/specta/specta) and [Expecta](https://github.com/specta/expecta) are included to allow for the creation of [Rspec](http://rspec.info)-like tests. Xcode integration for testing is fully configured; add your tests to the Specs target and hit Cmd+U.

### Utility Belt
* [AFNetworking](https://github.com/AFNetworking/AFNetworking)
* [libextobjc](https://github.com/jspahrsummers/libextobjc)'s [scope](https://github.com/jspahrsummers/libextobjc/blob/master/extobjc/EXTScope.h) and [keypath checking](https://github.com/jspahrsummers/libextobjc/blob/master/extobjc/EXTKeyPathCoding.h) modules.
* [Asterism](https://github.com/robb/Asterism), a fast, simple and flexible library for manipulating collections.
* [Sidecar](https://github.com/crushlovely/Sidecar), Crush's homegrown library. Features commonly needed functionality, such as creating UIColors from hex, playing short sound effects, and performing blocks on the main thread.

### More...
Additionally, the Podfile notes a few other libraries that you may find useful:

* [FormatterKit](https://github.com/mattt/FormatterKit), for all your string-formatting needs.
* [PromiseKit](https://github.com/mxcl/PromiseKit/blob/master/LICENSE), a promises/futures library similar to [Promises/A+](http://promises-aplus.github.io/promises-spec/), and related wrappers for core libraries.
* [Mantle](https://github.com/Mantle/Mantle), a project from the GitHub folks to make simpler, safer model classes.
* [SSKeychain](https://github.com/soffes/sskeychain), a friendly wrapper around the Keychain API.
* [DateTools](https://github.com/MatthewYork/DateTools), if you find yourself needing to do a lot of datetime math.


Here are some specific tips:

* Making a change to a build setting? Make it once in your project's `.xcconfig` file, so that it will propagate to all configurations.
* Adding an external library? If there's a podspec for it, bring it in via Cocoapods. If there's not, consider writing one and submitting it upstream. Use git submodules as a last resort; version and dependency management with them is a pain in the ass.
    * There should almost never be a reason to check in third-party projects wholesale. If you need to modify someone else's code, fork the repo and include the fork in your Podfile with a direct [`:git` reference](http://guides.cocoapods.org/syntax/podfile.html#pod).
* Use CocoaLumberjack's `DDLog` variants instead of `NSLog`. It's faster, provides more information, is more configurable, and understands log levels. All of that with the same familiar syntax. Retrain your fingers.
* Need to define different settings in staging and production? Check out the [ProjectName-Environment.h](CrushBootstrap/Other-Sources/CrushBootstrap-Environment.h) file in Other Sources. It defines macros to test the type of build that is currently taking place.
