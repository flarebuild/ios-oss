package(default_visibility = ["//visibility:public"])

load(
    "@build_bazel_rules_swift//swift:swift.bzl",
    "swift_library",
)

load(
    "@build_bazel_rules_apple//apple:ios.bzl",
    "ios_application",
)

swift_library(
    name = "Sources",
    module_name = "Kickstarter_Framework",
    srcs = glob([
        "AppDelegate.swift",
        "DataSources/*.swift",
        "Library/*.swift",
        "ViewModels/*.swift",
        "Views/*.swift",
        "Views/**/*.swift",
    ], exclude = [
        "**/*Tests.swift",
        "DataSources/*Test.swift",
        "Library/MockQualtricsPropertiesType.swift",
        "Library/MockQualtricsResultType.swift",
    ]),
    data = glob([
        "Views/Storyboards/*.xib",
        "Views/Storyboards/*.storyboard",
    ]),
    deps = [
        "//:Alamofire",
        "//:AlamofireImage",
        "//:AppCenter",
        "//:AppCenterAnalytics",
        "//:AppCenterCrashes",
        "//:AppCenterDistribute",
        "//:Argo",
        "//:Crashlytics",
        "//:Curry",
        "//:Fabric",
        "//:FBSDKCoreKit",
        "//:FBSDKLoginKit",
        "//:KsApi",
        "//:Library",
        "//:Optimizely",
        "//:Prelude_UIKit",
        "//:Prelude",
        "//:Qualtrics",
        "//:ReactiveExtensions",
        "//:ReactiveSwift",
        "//:Runes",
        "//:Stripe",
    ],
)

ios_application(
    name = "Release",
    resources = glob([
        "Assets.xcassets/*",
        "Assets.xcassets/**/*",
        "Assets.xcassets/**/**/*",
    ], exclude = [
        "Assets.xcassets/app-icon-beta.appiconset/*",
        "Assets.xcassets/app-icon-debug.appiconset/*",
    ]),
    entitlements = "Release.entitlements",
    strings = glob([
        "Locales/**/*.strings",
    ]),
    bundle_id = "com.kickstarter.kickstarter",
    bundle_name = "Kickstarter",
    families = [
        "iphone",
        "ipad",
    ],
    infoplists = ["Info.plist"],
    minimum_os_version = "12.4",
    deps = [
        ":Sources",
    ],
)
