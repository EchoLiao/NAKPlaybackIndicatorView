[![Build Status](https://travis-ci.org/yujinakayama/NAPlaybackIndicatorView.png?branch=master)](https://travis-ci.org/yujinakayama/NAPlaybackIndicatorView)

# ![Icon](Documentation/icon.png) NAPlaybackIndicatorView

**NAPlaybackIndicatorView** is a view that mimics the music playback indicator in the Music.app on iOS 7.

It has three vertical bars and they oscillate randomly.

It requires iOS 7 or later.

## Installation

~~NAPlaybackIndicatorView is available through [CocoaPods](http://cocoapods.org)~~ **Not yet available**,
to install it simply add the following line to your `Podfile`:

```ruby
pod 'NAPlaybackIndicatorView'
```

Then run `pod install`.

## Basic Usage

Here's a basic example:

```objective-c
NAPlaybackIndicatorView *indicator = [[NAPlaybackIndicatorView alloc] initWithFrame:frame];

// Initially the `state` property is NAPlaybackIndicatorViewStateStopped
// and the `hidesWhenStopped` property is YES.
// Thus, the view is hidden at this time.

// The view appears and the bars start animation.
indicator.state = NAPlaybackIndicatorViewStatePlaying;

// The bars stop animation and become idle.
indicator.state = NAPlaybackIndicatorViewStatePaused;

// The view becomes hidden.
indicator.state = NAPlaybackIndicatorViewStateStopped;
```

You can use NAPlaybackIndicatorView in both code and Storyboard, and also with both Auto Layout and frame-based layout.

### Code with Auto Layout

```objective-c
NAPlaybackIndicatorView *indicator = [[NAPlaybackIndicatorView alloc] initWithFrame:CGRectZero];
indicator.translatesAutoresizingMaskIntoConstraints = NO;
[self.view addSubview:indicator];

// Then, add some positioning layout constraints.
// Note that normally you don't need to add sizing constraints
// since NAPlaybackIndicatorView has an intrinsic content size.
// It will be automatically resized to fit its content.
```

### Code with Frame-Based Layout

```objective-c
NAPlaybackIndicatorView *indicator = [[NAPlaybackIndicatorView alloc] initWithFrame:CGRectZero];
[indicator sizeToFit]; // Resize itself to fit its content.
[self.view addSubview:indicator];
```

### Storyboard with Auto Layout

1. Put a `UIView` on your view.
2. Set its custom class to `NAPlaybackIndicatorView`.
3. In the **Size Inspector** (⌥⌘5), set the **Intrinsic Size** to **Placeholder** and set the width to 13 and the height to 12. Note that this is just for convenience of the appearance on the Storyboard, and the placeholder size won't be used at runtime.
4. Add some positioning layout constraints.

### Storyboard with Frame-Based Layout

1. Put a `UIView` on your view.
2. Set its custom class to `NAPlaybackIndicatorView`.
3. In the **Size Inspector** (⌥⌘5), set the width to 13 and the height to 12. In fact, the content width is 12 points on Retina device, and 13 points on non-Retina device.

## Customization

### Color

The color of the bars can be changed by setting `tintColor` property (`UIView`) of the view or its ancestor view.

### Size

Normally the view can be automatically resized to fit its content by:

* Omitting sizing constraints in Auto Layout, since it has an intrinsic content size.
* Calling `sizeToFit` in frame-based layout.

Or if you explicitly specify size, the bars will be placed in the center of the view.

## Class Reference

NAPlaybackIndicatorView's reference is available [here](http://yujinakayama.me/NAPlaybackIndicatorView/).

## License

Copyright (c) 2014 Yuji Nakayama

See the [LICENSE.txt](LICENSE.txt) for details.
