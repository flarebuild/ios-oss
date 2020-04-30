# How to build Kickstarter iOS App in 11 seconds with Bazel :racing_car:


## Prepare Environment

###### Install [Bazelisk](https://github.com/bazelbuild/bazeliskhttps://github.com/bazelbuild/bazelisk) `1.4.0` as a Bazel through [Homebrew](https://brew.sh):

```bash
brew install bazelisk@1.4.0
ln -s /user/local/Cellar/bazelisk/1.4.0/bin/bazelisk /user/local/bin/bazel
```


## Welcome to your Bazel experience :four_leaf_clover:

### Quick Start

###### 1. Clone Kickstarter iOS repository and install tools and dependencies.

```bash
git clone git@github.com:kickstarter/ios-oss.git && \
make bootstrap
```

###### 2. Create a new `WORKSPACE` file with base dependencies.

###### 3. Create `BUILD` files.

###### 4. Update some env values in your main target's `Info.plist` file:
```
CFBundlePackageType: $(PRODUCT_BUNDLE_PACKAGE_TYPE) -> APPL
...
```

###### 5. Add a new `.bazelversion` and specify exact version of Bazel which will be used. Additionally add a new `.bazelrc` with predefined build flags for iOS build.

###### 6.1. Fetch and Compile core Bazel’s dependencies:

```bash
bazel build @build_bazel_rules_swift//examples/xplatform/hello_world
```

###### 6.2. Fetch external Bazel’s dependencies:

```bash
bazel fetch //Kickstarter:Release
```

###### 6.3. Build project with Bazel:

```bash
bazel build //Kickstarter:Release \
--spawn_strategy=local \
--apple_platform_type=ios \
--cpu=ios_x86_64
```

###### 7. Build Kickstarter iOS App with Bazel completed successfully :tada:

###### 8. Install Tulsi `0.20200219.88` – Xcode Project Generator For Bazel: <https://github.com/bazelbuild/tulsi#building-and-installing>.

###### 9. Remove `Kickstarter.xcodeproj`.

###### 10. Create a new `Kickstarter.tulsiproj` and save it on the same level with `WORKSPACE` file.

###### 11. Add `BUILD` files associated with the project as a Packages to the created Tulsi's project.

###### 12. Next, you have to select one or more targets that you want to build in Xcode, for example `Release` - `ios_application` and `Sources`(`Kickstarter_Framework`) – `swift_library`.

###### 13. Select one or more `Source Targets` with a Recursive strategy (Optional). This allows you to select a working set from your full source tree that best matches the portion of the project that you're likely to edit. Save a new Config with the `Default` name.

###### 14. Generate a new Xcode Project with Tulsi and save it on the same level with `WORKSPACE` and `Kickstarter.tulsiproj` files.

#### Finally, build and run Kickstarter app with Bazel in Xcode :champagne:



### iOS Build Benchmarks :male-scientist:

MacBook Pro (13-inch, 2018), macOS Catalina 10.15.3
Xcode 11.4, Carthage 0.34

swift --version
Apple Swift version 5.2 (swiftlang-1103.0.32.1 clang-1103.0.32.29)
Target: x86_64-apple-darwin19.3.0

###### 1. Cold Build with Xcode's original build system.
###### Build time: `124.3s`

###### 2. Cold Build with Bazel without Remote Cache.
###### Elapsed time: `269.938s`

```bash
INFO: Analyzed target //Kickstarter-iOS:Release (0 packages loaded, 1990 targets configured).
INFO: Found 1 target...
Target //Kickstarter-iOS:Release up-to-date:
  bazel-bin/Kickstarter-iOS/Release.ipa
INFO: Elapsed time: 269.938s, Critical Path: 267.86s
INFO: 87 processes: 87 local.
INFO: Build completed successfully, 122 total actions
```

###### 3. Cold Build with Bazel + Upload Actions and Outputs to Remote Cache.
###### Elapsed time: `271.675s`

```bash

```

###### 4. Cold Build with Bazel + Retrieve Actions and Outputs from Remote Cache.
###### Elapsed time: `11.400s` :boom:

```bash

```

#### Result: Overall speedup from original Xcode build system to Bazel build with Remote Cache is `x11` :crystal_ball:
