package(default_visibility = ["//visibility:public"])

load(
    "@build_bazel_rules_apple//apple/internal:apple_framework_import.bzl",
    "apple_dynamic_framework_import",
)

load(
    "@build_bazel_rules_swift//swift:swift.bzl",
    "swift_library",
)

apple_dynamic_framework_import(
    name = "Alamofire",
    framework_imports = glob(["Carthage/Build/iOS/Alamofire.framework/**"]),
)

apple_dynamic_framework_import(
    name = "AlamofireImage",
    framework_imports = glob(["Carthage/Build/iOS/AlamofireImage.framework/**"]),
)

apple_dynamic_framework_import(
    name = "AppCenter",
    framework_imports = glob(["Carthage/Build/iOS/AppCenter.framework/**"]),
)

apple_dynamic_framework_import(
    name = "AppCenterAnalytics",
    framework_imports = glob(["Carthage/Build/iOS/AppCenterAnalytics.framework/**"]),
)

apple_dynamic_framework_import(
    name = "AppCenterCrashes",
    framework_imports = glob(["Carthage/Build/iOS/AppCenterCrashes.framework/**"]),
)

apple_dynamic_framework_import(
    name = "AppCenterDistribute",
    framework_imports = glob(["Carthage/Build/iOS/AppCenterDistribute.framework/**"]),
)

apple_dynamic_framework_import(
    name = "Argo",
    framework_imports = glob(["Carthage/Build/iOS/Argo.framework/**"]),
)

apple_dynamic_framework_import(
    name = "Crashlytics",
    framework_imports = glob(["Frameworks/Fabric/Crashlytics.framework/**"]),
)

apple_dynamic_framework_import(
    name = "Curry",
    framework_imports = glob(["Carthage/Build/iOS/Curry.framework/**"]),
)

apple_dynamic_framework_import(
    name = "Fabric",
    framework_imports = glob(["Frameworks/Fabric/Fabric.framework/**"]),
)

apple_dynamic_framework_import(
    name = "FBSDKCoreKit",
    framework_imports = glob(["Carthage/Build/iOS/FBSDKCoreKit.framework/**"]),
)

apple_dynamic_framework_import(
    name = "FBSDKLoginKit",
    framework_imports = glob(["Carthage/Build/iOS/FBSDKLoginKit.framework/**"]),
)

apple_dynamic_framework_import(
    name = "Optimizely",
    framework_imports = glob(["Carthage/Build/iOS/Optimizely.framework/**"]),
)

apple_dynamic_framework_import(
    name = "Prelude_UIKit",
    framework_imports = glob(["Carthage/Build/iOS/Prelude_UIKit.framework/**"]),
)

apple_dynamic_framework_import(
    name = "Prelude",
    framework_imports = glob(["Carthage/Build/iOS/Prelude.framework/**"]),
)

apple_dynamic_framework_import(
    name = "Qualtrics",
    framework_imports = glob(["Carthage/Build/iOS/Qualtrics.framework/**"]),
)

apple_dynamic_framework_import(
    name = "ReactiveExtensions",
    framework_imports = glob(["Carthage/Build/iOS/ReactiveExtensions.framework/**"]),
)

apple_dynamic_framework_import(
    name = "ReactiveSwift",
    framework_imports = glob(["Carthage/Build/iOS/ReactiveSwift.framework/**"]),
)

apple_dynamic_framework_import(
    name = "Runes",
    framework_imports = glob(["Carthage/Build/iOS/Runes.framework/**"]),
)

apple_dynamic_framework_import(
    name = "Stripe",
    framework_imports = glob(["Carthage/Build/iOS/Stripe.framework/**"]),
)

swift_library(
    name = "KsApi",
    srcs = glob([
        "KsApi/*.swift",
        "KsApi/**/*.swift",
        "KsApi/**/**/*.swift",
        "Library/EnvironmentType.swift",
        "Frameworks/native-secrets/ios/Secrets.swift",
    ], exclude = [
        "KsApi/*Tests.swift",
        "KsApi/**/*Tests.swift",
        "KsApi/**/**/*Tests.swift",
        "KsApi/models/RootCategoriesEnvelope.swift",
    ]),
    deps = [
        "//:Argo",
        "//:Curry",
        "//:Prelude",
        "//:ReactiveExtensions",
        "//:ReactiveSwift",
        "//:Runes",
    ],
)

swift_library(
    name = "Library",
    srcs = glob([
        "Library/*.swift",
        "Library/**/*.swift",
    ], exclude = [
        "Library/*Tests.swift",
        "Library/EnvironmentType.swift",
        "Library/**/*Test.swift",
        "Library/**/*Tests.swift",
        "Library/MockPushRegistration.swift",
        "Library/TestHelpers/*.swift",
        "Library/Tracking/MockTrackingClient.swift",
    ]),
    deps = [
        "//:Argo",
        "//:Crashlytics",
        "//:Curry",
        "//:Fabric",
        "//:FBSDKCoreKit",
        "//:FBSDKLoginKit",
        "//:KsApi",
        "//:Prelude_UIKit",
        "//:Prelude",
        "//:ReactiveExtensions",
        "//:ReactiveSwift",
        "//:Runes",
    ],
)
