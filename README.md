# flutter_redux_dev_tools

[![Build Status](https://travis-ci.org/brianegan/flutter_redux_dev_tools.svg?branch=master)](https://travis-ci.org/brianegan/flutter_redux_dev_tools) [![codecov](https://codecov.io/gh/brianegan/flutter_redux_dev_tools/branch/master/graph/badge.svg)](https://codecov.io/gh/brianegan/flutter_redux_dev_tools)

A Widget you can use to show a [Redux](https://pub.dartlang.org/packages/redux) Time Travel UI. Simply put it in a part of your UI that makes sense (Such as a Dev Tools Drawer), pass it a `DevToolsStore` and you'll be good to go!

Note: This Widget does not work with a normal [Redux](https://pub.dartlang.org/packages/redux) `Store`. It is meant to work with the [redux_dev_tools package](https://pub.dartlang.org/packages/redux_dev_tools), which provides a `DevToolsStore`. The `DevToolsStore` is a drop-in replacement for your Store during Development!

### Demo

A simple Flutter app that allows you to Increment and Decrement a counter.

![A screenshot of the Dev Tools in Action](https://gitlab.com/brianegan/flutter_redux_dev_tools/raw/master/devtools.gif)

### Usage

  1. Create a `main_dev.dart` file
  2. In this file, create a `DevToolsStore` in place of a normal redux `Store`
  3. Create a `ReduxDevTools` widget, passing through the Store. You can place this Widget wherever makes sense in your app! One good suggestion: In a "Dev Tools Drawer." This is generally the `endDrawer` in your Scaffold, and can contain different types of tools for a Dev Build of your app. 

### Example

This example paints only a broad outline of how to use the ReduxDevTools. For a complete example, see the `example` folder.

```dart
int addReducer(int state, action) => state + 1;

// Create a DevToolsStore instead of a normal Store during Development
final store = DevToolsStore<int>(
  addReducer,
  initialState: 0,
);

// Finally, create your app with a Redux Dev Tools
main() { 
  runApp(MaterialApp(
    home: Scaffold(
      endDrawer: ReduxDevTools<int>(store),
    ),
  ));
}
```

## Credits

All of this is inspired by the original [Redux Devtools](https://github.com/gaearon/redux-devtools).

