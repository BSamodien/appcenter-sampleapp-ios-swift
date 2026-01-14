# Claude.md - Project Context for AI Assistant

## Project Overview

This is the **official Microsoft Visual Studio App Center sample application** for iOS, built with Swift. It demonstrates how to integrate and use App Center services including Analytics, Crash Reporting, and Push Notifications.

The app serves as an educational tool with a swipeable interface showcasing each App Center service through dedicated screens.

## Tech Stack

- **Language:** Swift
- **Platform:** iOS 9.0+
- **IDE:** Xcode
- **Dependency Manager:** CocoaPods
- **UI Framework:** UIKit with Storyboards
- **Testing:** XCTest (UI Tests)

### Dependencies (via CocoaPods)

- `AppCenter` - Core SDK
- `AppCenter/Push` - Push notifications
- `VSMobileCenterExtensions` - Testing utilities

## Project Structure

```
appcenter-sampleapp-ios-swift/
├── sampleapp-ios-swift/              # Main app source code
│   ├── AppDelegate.swift             # App entry point & App Center initialization
│   ├── RootViewController.swift      # UIPageViewController for navigation
│   ├── AnalyticsViewController.swift # Analytics demo screen
│   ├── CrashViewController.swift     # Crash reporting demo screen
│   ├── Base.lproj/
│   │   ├── Main.storyboard          # Main UI layouts (7 view controllers)
│   │   └── LaunchScreen.storyboard  # Launch screen
│   ├── Assets.xcassets/             # Images and icons
│   └── Info.plist                   # App configuration
├── sampleapp-ios-swiftUITests/       # UI test target
│   └── sampleapp_ios_swiftUITests.swift
├── sampleapp-ios-swift.xcworkspace/  # Use this for development (CocoaPods)
├── sampleapp-ios-swift.xcodeproj/    # Xcode project file
├── Podfile                           # CocoaPods dependencies
└── DemoCerts.developerprofile        # iOS provisioning profile
```

## Key Files

| File | Purpose |
|------|---------|
| `AppDelegate.swift` | Initializes App Center SDK with Analytics, Crashes, and Push services |
| `RootViewController.swift` | Manages page-based navigation between 7 demo screens |
| `AnalyticsViewController.swift` | Demonstrates tracking custom events and event properties |
| `CrashViewController.swift` | Demonstrates intentional crash generation for testing |
| `Main.storyboard` | Contains all 7 view controller layouts |
| `Podfile` | Defines CocoaPods dependencies |

## App Center Configuration

- **App ID:** `55023a5f-6d10-4333-9562-91fb5ffadb1c`
- **Services Enabled:** Analytics, Crashes, Push
- **Bundle Display Name:** "AMC Sample"

## Development Setup

1. Install dependencies:
   ```bash
   pod install
   ```

2. Open the workspace (not the project file):
   ```bash
   open sampleapp-ios-swift.xcworkspace
   ```

3. Build and run in Xcode

## Architecture

- **Pattern:** MVC (Model-View-Controller)
- **Navigation:** UIPageViewController with horizontal pagination
- **UI:** Storyboard-based with programmatic view controller instantiation

### View Controllers (in order)

1. `welcomeViewController` - Introduction screen
2. `buildViewController` - Build service info
3. `testViewController` - Test service info
4. `distributeViewController` - Distribution service info
5. `CrashViewController` - Crash reporting demo
6. `AnalyticsViewController` - Analytics event tracking demo
7. `pushViewController` - Push notifications info

## Testing

UI tests are located in `sampleapp-ios-swiftUITests/`:

```bash
# Run tests via Xcode or command line
xcodebuild test -workspace sampleapp-ios-swift.xcworkspace \
  -scheme sampleapp-ios-swift \
  -destination 'platform=iOS Simulator,name=iPhone 14'
```

## Code Conventions

- View controllers are instantiated from storyboard using identifiers matching their names
- App Center SDK calls use the `MS` prefix (e.g., `MSCrashes`, `MSAnalytics`)
- Push notification capability is configured in entitlements file

## Common Tasks

### Adding a New Analytics Event
```swift
// In any view controller
MSAnalytics.trackEvent("Event Name")

// With properties
MSAnalytics.trackEvent("Event Name", withProperties: ["key": "value"])
```

### Testing Crash Reporting
The crash button in `CrashViewController` calls `MSCrashes.generateTestCrash()` to simulate a crash for testing purposes.

## External Resources

- [App Center Documentation](https://docs.microsoft.com/en-us/appcenter/)
- [iOS Getting Started Guide](https://docs.microsoft.com/en-us/appcenter/quickstarts/ios/getting-started)
- [App Center SDK for iOS](https://github.com/microsoft/appcenter-sdk-apple)
