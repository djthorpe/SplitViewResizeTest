SplitViewResizeTest
===================

![Logo](https://raw.github.com/djthorpe/SplitViewResizeTest/master/screenshot.png)

Here's some sample code to show how to implement a nice vertical NSSplitView. In your
NIB file, you'll need to:

  - Create an NSSplitView and use a thin divider line.
  - Add two NSImageView objects at the bottom of the left hand NSCustomView within
    the split view. One is a simple "gradient", the other is a "grabber" image.
	You'll find the images in the `resources` folder of this repository.
  - Add constraints so that the "gradient" right hand edge is 15 pixels to the
    right of the parent view and the left hand edge is hard on the left. Ensure
	the image stretches.
  - Your controller object should be wired up to be the delegate for the
    `NSSplitView`.
  - The `ibGrabberView` property of the controller should be connected to the
    grabber `NSView`.
	
The controller has only two methods in it which implement the `NSSplitView`
delegate:

```objc
@interface Controller
-(NSRect)splitView:(NSSplitView* )splitView additionalEffectiveRectOfDividerAtIndex:(NSInteger)dividerIndex;
-(CGFloat)splitView:(NSSplitView* )splitView constrainSplitPosition:(CGFloat)proposedPosition ofSubviewAt:(NSInteger)dividerIndex;
@end
```

The first method adds the "grabber" image to the hotspot location, so that you can
move the divider when hovering over the grabber. The second method ensures that
the grabber is always shown.

If you have multiple `NSSplitView` elements in your UI, you'll obviously need
to change the code somewhat, but this is the simple version.

- David Thorpe, February 2013

