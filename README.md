# healthcare

## Glossary
* `Xcode` - IDE for developing software for iOS, macOS, iPadOS, watchOS, tvOS. 
* `npx` - It is used to run Node.js packages and executables that are installed locally or published on npm without the need to install them globally. One of the main benefits of `npx` over `npm` is that it allows you to quickly and easily try out new packages without cluttering up your global package registry or having to worry about version conflicts.

## Folder Structure
* The index.js file is typically the entry point of your app, and it registers the main component using the AppRegistry.registerComponent method. AppRegistry is a module that is responsible for registering the main component of your application and starting the app's runtime.
* ios - Overall, the ios folder in a React Native project is where you'll go to build and run your app on an iOS device or simulator. Contains Xcode project and source code for iOS version of the app.
* * ConsultantApp.xcodeproj - Xcode project file. Contains all the resources, configuration files, source code files, and other files necessary to build an application or software project in Xcode.
* * Podfile - Used by CocoaPods (dependency manager for iOS and macOS projects). Include external libraries and frameworks that the project requires.
* * ConsultantApp
* * * AppDelegate.m - Main entry point for app's iOS code. Initializes react native bridge and sets up root view controller for the app. 
* * * Info.plist - App configuration. Bundle identifier, version number, and minimum required iOS version.
* * * LaunchScreen.storyboard - Visual layout of app's user interface. 
* * ConsultantApp.xcodeproj
* * * project.pbxproj - Main project file. Automatically generated by Xcode and should not be edited manually.
* android -
* * `gradlew` is a script that is used to execute Gradle commands in a React Native project without having to install Gradle on your machine. In order to run the gradlew script, it needs to have execute permission. 
* * `build.gradle` is a file in a Gradle-based Android project that contains configuration settings and dependencies for building the app. The file is written in the Groovy programming language and is used by Gradle to build and manage the project. The build.gradle file contains two sections: buildscript and allprojects. In the buildscript section, you can specify the repositories where Gradle should look for the required dependencies, the classpath for the Gradle plugins, and any other build system settings. In the allprojects section, you can specify the repositories where Gradle should look for the required dependencies for the project modules. 
* * In `settings.gradle`, you can specify the modules that make up the project, their names, and their locations within the project directory structure. You can also define dependencies between modules, such as which modules depend on which other modules. The settings.gradle file is used by Gradle to generate the project's build configuration. It is processed before the build.gradle files, which contain the actual build configurations and tasks.

## Development
### Environment Setup
1. Install Node.js and the React Native CLI (Command Line Interface) on your computer. You can follow the instructions on the official Node.js website to install Node.js, and then install the React Native CLI using the following command: `npm install -g react-native-cli`
2. If you are using macOS or Windows, follow the steps for both Android and iOS setup - https://reactnative.dev/docs/environment-setup. Refer to steps under `React Native CLI Quickstart`. DO NOT skip any of the steps.

### Project Installation 
1. Clone the project from Github.
2. You need to run `npm install` when you first clone or download a new project that has a package.json file. This command installs all the dependencies listed in the package.json file into a local node_modules folder. You may also need to run `npm install` if new dependencies are added to the project. For example, if a new package is added to the package.json file, you need to run `npm install` to download and install the new package and its dependencies. It's a good practice to run `npm install` whenever you pull or clone a new version of a project, or when someone else has added new dependencies to the project.

### Running 
1. For iOS Simulator https://reactnative.dev/docs/environment-setup?platform=ios&guide=native#running-your-react-native-application 
2. For Android Emulator https://reactnative.dev/docs/environment-setup?platform=android&guide=native&os=macos#running-your-react-native-application  

Navigate to your project directory and start the development server by running the following command: `npx react-native start`. This will start the Metro bundler, which is a tool that helps to bundle and serve your app's JavaScript code. Let Metro Bundler run in its own terminal. Open a new terminal inside your React Native project folder. Run `npx react-native run-android` for Android and `npx react-native run-ios` for iOS.

## Debugging
Use ChatGPT for debugging questions, it has been working well.

### Android
If facing any issues with running Android Emulator or running app, first load `android` folder into Android Studio. If the `android` folder doesn't build there, then it won't build anywhere. Some common issues -
* Kotlin version mismatch - ensure the system installed version (use `kotlin -version` for finding installed version) matches with the `kotlinVersion` defined in `build.gradle`. From `android` directory path, run `./gradlew clean` for clean-up and `./gradlew assembleDebug` for rebuilding the project.
* Gradle `compile` vs `implementation` issue - Some React Native packages might throw errors when building Android version of the project or running Android Emulator. You should always use `implementation` rather than `compile`for dependencies, as `compile` is now deprecated or removed in the case of Gradle 7+. `react-native-upi-payment` is a known case as of now, to fix it, update the `node_modules/react-native-upi-payment/android/build.gradle`. This has to be done manually, as `node_modules` isn't committed to repo. 
### iOS


