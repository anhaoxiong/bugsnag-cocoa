
We love people filing issues and sending pull requests!

How to contribute
-----------------

-   [Fork](https://help.github.com/articles/fork-a-repo) the [notifier on github](https://github.com/bugsnag/bugsnag-cocoa)
-   Commit and push until you are happy with your contribution
-   Test your changes
-   [Make a pull request](https://help.github.com/articles/using-pull-requests)
-   Thanks!

Running the tests
-----------------

Run the tests using the default SDK (iOS 11.2) by using:

    make test e2e

Alternately, you can specify an iOS SDK:

    make SDK=iphonesimulator11.3 test

Or test on OS X:

    make BUILD_OSX=1 test

If you are interested in cleaner formatting, run `make bootstrap` to install
[xcpretty](https://github.com/supermarin/xcpretty) as an output formatter.


Releasing a new version
-----------------------

## Release Checklist
Please follow the testing instructions in [the platforms release checklist](https://github.com/bugsnag/platforms-release-checklist/blob/master/README.md), and any additional steps directly below.

- On a throttled network, is the request timeout reasonable, and the main thread not blocked by any visible UI freeze? (Throttling can be achieved by setting both endpoints to "https://httpstat.us/200?sleep=5000")
- Please ensure that release builds are run on a physical device with an ad-hoc archive. (For release builds, select Edit Scheme, change the Build Configuration to Release, and uncheck Debug Executable)
- Run the static analyzer (Product -> Analyze in Xcode) to ensure that no problems are introduced.

### CocoaPods

If you're a member of the core team, you can release the cocoa pod as follows:

### One time setup

* Install Cocoapods

    ```
    gem install cocoapods
    ```

* Register

    ```
    pod trunk register notifiers@bugsnag.com 'Bugsnag Notifiers' --description='your name'
    ```

* Click the link in the email that got sent to support

### Every time

* Update the CHANGELOG. Update the README.md if appropriate.
* Update the version number, tag, and push by running `make VERSION=[number] release`
* Create a new release https://github.com/bugsnag/bugsnag-cocoa/releases/new
* Select the tag you just pushed
* Set the title to the tag (v5.x.x)
* Copy the changelog entries into the release notes
* Click "Publish Release"
* Update the setup guides for Objective-C and Swift on docs.bugsnag.com with any
  new content
* Make releases to downstream libraries, if appropriate (generally for bug
  fixes)
