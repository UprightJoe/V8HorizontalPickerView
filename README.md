V8HorizontalPickerView
======================
by Shawn Veader (@veader) of [V8 Logic](http://v8logic.com) / [V8 Labs, LLC](http://v8labs.com)

Original design by [Buck Sharp](http://bucksharp.tumblr.com/), the designer on f/stats.

Fork created by Travis Hanna (Github:UprightJoe)

Fork Information
================
To date, the following modifications have been made 
to Shawn Veader's original work:

- [CocoaPods](http://cocoapods.org) support was added via a podspec file 
- An awakeFromNib method was added to improve storyboard support
- `horizontalPickerView:viewForElementAtIndex:`	 and `horizontalPickerView:titleForElementAtIndex:` have been moved
  from the delegate protocol *(V8HorizontalPickerViewDelegate)* to the data source protocol
  *(V8HorizontalPickerViewDataSource)*.  __This is potentially a breaking change__ if you were using the 
  original version of this component and have a scenario where your delegate and dataSource are not the same 
  object.  However, this seems to be more consistent with the stated intent of the original author which was 
  to mimic UITableView.
- This readme file has been modified as appropriate.

How to use V8HorizontalPickerView
---------------------------------
Add the `V8HorizontalPickerView` header and implementation files (.h and .m)
along with the protocol header file to your app source and include them in
your project. (A podspec file has been provided for your convenience if your project uses CocoaPods.)

Implement the necessary delegate and data source protocol methods.
Instantiate and add the picker view to your view and wire up the delegate
and data source. That's it!

This control was modeled after the standard Apple controls such as `UITableView`.

Data Source Protocol
----------------
    - (NSInteger)numberOfElementsInHorizontalPickerView:(V8HorizontalPickerView *)picker;
    - (NSString *)horizontalPickerView:(V8HorizontalPickerView *)picker titleForElementAtIndex:(NSInteger)index;
    - (UIView *)  horizontalPickerView:(V8HorizontalPickerView *)picker  viewForElementAtIndex:(NSInteger)index;


Delegate Source Protocol
-------------------
    - (void)horizontalPickerView:(V8HorizontalPickerView *)picker didSelectElementAtIndex:(NSInteger)index;
    - (NSInteger) horizontalPickerView:(V8HorizontalPickerView *)picker widthForElementAtIndex:(NSInteger)index;

The protocol requires the width method to be implemented and for either the
title or view *ForElementAtIndex: method to be implemented. (ie: you don't
need both)

Using Views for Elements
------------------------
If you are going to implement the

    -horizontalPickerView:viewForElementAtIndex:

data source method, make sure your view conforms to the 
`V8HorizontalPickerElementState` protocol.

License
-------
See LICENSE file.
This work is published under the zlib/libpng license.