#Bootstrap

###Containers
define how much space a grid system should use. They can be of two types: .container has di erent widths for different types of devices whereas .container-fluid expands to  t the width of the device.

You can choose a  uid container if you are not fond of a  xed layout. To do this, you use the class .container-fluid. A  uid container has no  xed width; its width will always be the width of thedevice.

a column de ned for extra smaller devices will work in all types of devices.

###Rows
Rows have the negative margins so that they are not pushed by the padding of the container.

###Bootstrap forces tables to fit the width of the parent element by applying a width of 100%. But this has an issue. A multi-column table will get squeezed on smaller devices and may not be readable.Bootstrap has another class to remedy this: .table-responsive.

###Helper ClassesBootstrap provides various helper classes that can be useful in certain situations in dealing with grids. These classes are:} .clearfix: Normally used to clear  oats, adding this class to any column will make it shift to a new row automatically, to help you correct problems that occur with uneven column heights.

O setting columns: You don’t have to occupy all 12 of the virtual columns. You can use o set classes like .col-xs-offset-* or .col-md-offset-* to leave a particular number of virtual Bootstrap columns to the left of any column (kind of like invisible place holders).} Reordering: Use classes like .col-md-push-* and .col-md-pull-* to shift a column to the right or left, respectively.

###The Bootstrap Modal 
 a lightweight multi-purpose JavaScript popup that is customizable and respon- sive. It can be used to display alert popups, videos, and images in a website. Websites built with Bootstrap can use the modal to showcase (for example) terms and conditions (as part of a signup process), videos (similar to a standard light box), or even social media widgets.
 
 To trigger the modal, you’ll need to include a link or a button. The markup for the trigger element might look like this:`<a href="#" class="btn btn-lg btn-success" data-toggle="modal" data-target="#basic- Modal">Click to open Modal</a>`

The modal is one of the best plugins o ered by Bootstrap 3. For a novice designer, it is one of the best ways to load content inside a popup screen without writing any JavaScript.

###ScrollSpyScrollSpy is an interesting JavaScript module added to the Bootstrap library. It is basically a combination of navigation menu and contents below. Its role is to update the active item in the navigation bar as you scroll down the content area. To use the ScrollSpy feature you have to add data-spy="scroll" and data-target="#top-navigation" attribute to the body element. Here #top-navigation is the id of my navigation bar. Make sure the links in the navigation bar are internal links.