# Custom Splash Screen

A Flutter package to custom splash screen: change logo icon, logo animation, and splash screen background color. (Custom from animated splash screen)

<img src="https://raw.githubusercontent.com/tranhuycong/custom_splash/master/example/assets/splash-animation-zoom-out.2019-09-09%2011_18_24.gif" width="230" height="440" alt="ProgressDialog Demo" />

### Using the package

[Get the library](https://github.com/tranhuycong/custom_splash)


### Things to do
<ol>
<li> Get a logo for your app</li>
<li> Prepare what to execute while the splash screen is shown (initializing your db, shared preferences, firebase...etc) </li>
<li> Screen to be shown after splash screen and background process </li>
<li> Duration of Splash Screen  </li>
</ol>

Import the package
```dart
import 'package:custom_splash/custom_splash.dart';
```

## Show splash screen for some duration
```dart
  type: CustomSplashType.StaticDuration
```

Inside your **main** function, use *home* as **SplashScreen(_)**, the parameters are as follows:
> **imagePath**: Path to your app-logo/image

> **backGroundColor**(not require - default: white): background's color (Colors.deepOrange or Color(0xfffc6042))

> **animationEffect**(not require -  default: **'fade-in'**): change animation of logo. There are: **'fade-in'**, **'zoom-in'**, **'zoom-out'**, **'top-down'**.

<img src="https://raw.githubusercontent.com/tranhuycong/custom_splash/master/example/assets/splash-animation-top-down.2019-09-09%2011_12_06.gif" width="230" height="440" alt="ProgressDialog Demo" />

> **logoSize**(not require -  default: 250): custom size of logo

> **home**: Screen to be shown after splash

> **duration**: duration of splash screen in milliseconds

> **type**
```dart
runApp(MaterialApp(
    home: CustomSplash(
        imagePath: 'assets/flutter_icon.png',
        backGroundColor: Colors.deepOrange,
        animationEffect: 'zoom-in',
        logoSize: 200,
        home: MyApp(),
        customFunction: duringSplash,
        duration: 2500,
        type: CustomSplashType.StaticDuration,
        outputAndHome: op,
    ),
));
```

## Execute a function in background and based on the value from that function navigate to different screen

```dart
  type: CustomSplashType.BackgroundProcess
```
> Create an object of  **Function** that gets executed while splash screen is shown
```dart
Function duringSplash = () {
  //Write your code here
  ...
  return value;
};
```

> Create routes according to your function return value
```dart
  //setup the return value correctly for proper navigation
  Map<dynamic, Widget> returnValueAndHomeScreen = {1: Home(), 2: HomeSt()};

```


Inside your **main** function, use *home* as **SplashScreen(_)**, the parameters are as follows:
> imagePath: Path to your app-logo/image
> home: Screen to be shown after splash
> customFunction: the function you have written above
> duration: duration of splash screen in milliseconds
> type
> output value of customFunction and home screen to navigate(Map function)

```dart
runApp(MaterialApp(
    home: CustomSplash(
        imagePath: 'assets/flutter_icon.png',
        backGroundColor: Colors.deepOrange,
        animationEffect: 'zoom-in',
        logoSize: 200,
        home: MyApp(),
        customFunction: duringSplash,
        duration: 2500,
        type: CustomSplashType.StaticDuration,
        outputAndHome: op,
    ),
));
```
