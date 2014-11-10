# HLSpriteKit

![License MIT](https://go-shields.herokuapp.com/license-MIT-blue.png)
[![Badge w/ Version](https://cocoapod-badges.herokuapp.com/v/HLSpriteKit/badge.png)](http://cocoadocs.org/docsets/HLSpriteKit)
[![Badge w/ Platform](https://cocoapod-badges.herokuapp.com/p/HLSpriteKit/badge.svg)](http://cocoadocs.org/docsets/HLSpriteKit)

SpriteKit scene and node subclasses, plus various utilities.

## Included

### HLGestureTarget

A gesture target handles gestures from `UIGestureRecognizers`.  It can be attached to any `SKNode` using the class category `SKNode+HLGestureTarget`.

The use pattern is this: The `SKScene` knows about its view, and so it is the `UIGestureHandlerDelegate`. It manages a collection of shared gesture recognizers, which it attaches to and detaches from its view as appropriate. When a certain gesture is recognized by a gesture recognizer, the scene figures out which node or nodes are the target of the gesture, and it forwards the gestures to those nodes using the `HLGestureTarget` interface.

Here's the point: The scene can effectively use `UIGestureRecognizer`s rather than `touchesBegan`, and the gesture handling code can be encapsulated within node subclassses (rather than dumped into the bloated scene).

### HLLayoutManager

A layout manager provides a single method (`layout`) to lay out a nodes.  It can be attached to any `SKNode` using the class category `SKNode+HLLayoutManager`.

The only layout manager currently provided in `HLSpriteKit` is `HLTableLayoutManager`, for table-like layouts, but more are planned.

Putting layout code in a third-party object (rather than in the `SKScene` or `SKNode` subclass) allows for easier re-use of common layout math.

### Custom SKNode Subclasses

* `HLGridNode`. Organizes content into a grid of same-size squares, with visual formatting and interaction options.

* `HLLabelButtonNode`.  A simple `SKLabelNode` displayed over an `SKSpriteNode`, but with extra sizing and alignment options.  In particular, it can size the sprite node to the text, and it can do baseline alignment so that the full font size (including descender) is vertically centered in the background; the math for the calculation is provided for all `SKLabelNode`s in a category `SKLabelNode+HLLabelNodeAdditions`.

* `HLMenuNode`. An interface and model of a hierarchical menu of buttons. The interface is a simple vertical stack of buttons, for now, but it provides a few layout and animation features.

* `HLMessageNode`. Shows a text message over a solid or textured background, with some animation options.

* `HLScrollNode`. Provides support for scrolling and scaling its content with pan and pinch gestures. The interface is deliberately analagous to `UIScrollView`.

* `HLToolbarNode`. A horizontal toolbar of squares, with various visual formatting, sizing, and animation options.

* `HLTiledNode`. Behaves like an `SKSpriteNode` that tiles its texture to fit a specified size.

### HLScene

HLScene contains functionality useful to many scenes, including but not limited to:

* loading scene assets in a background thread
* a shared gesture recognition system and an `HLGestureTarget`-aware gesture delegate implementation
* modal presentation of a node above the scene
* registration of nodes for common scene-related behaviors (e.g. resizing when the scene resizes; not encoding when the scene encodes; etc)

## Development

`HLSpriteKit` is under active development, and so includes other experimental classes and functions which seem general enough for reuse.  For instance, a generic `SKTexture` store and `SKEmitterNode` store are included, but it's not clear they are useful.

## Installation

`HLSpriteKit` is available via [CocoaPods](http://cocoapods.org):

    pod 'HLSpriteKit'
