# pio.js
---

**Easily monitize any web site that has images. Brought to you by the good folks at [print.io](http://www.print.io).**

*Note -- This github is for documentation/issues/feature requests only. Source code is closed source.*

For an example, click the shopping cart on [hellopics.com](http://www.hellopics.com).

## pio.js Features/Rationale

The widget does not pollute any of the embedded page's CSS/JS. All of the JS is placed under the `PIO` namespace. 

`pio.js` is pure javascript and weighs in at 4kb. Zero 3rd party JS files are used. In other words, this file does not include/need jquery, lodash, zepto, or any other lib. You will not have JS clash issues when you use this.


## Getting Started

In order to get started with the widget, you need to get an api key. This can be obtained by filling out [the contact form on print.io](http://print.io/contacts).

## Embedding and Configuring the Widget

We recommend you place the code for embedding and configuring side by side. 


####Bare Minimum Example
Here we are going to embed the script to use http/https, depending on the page its embedded in, and then configure the widget using the `PIO.config(options)` call.

````html
<!-- this points to the print.io CDN, which supports both http/https -->
<script src=”//az412349.vo.msecnd.net/widget-assets/pio.latest.js” />
<script>
PIO.config({
  // required -- api key
  recipeId:””
});
</script>

````

##API

###PIO.config(options)
Configures the widget for future calls to `PIO.open(options)`. Note that options can be passed in to both `PIO.config()`, `PIO.options()` or just one of them. See the section Config/Open Options API below for more details.

###PIO.open(options)
Opens the widget. Note that one can pass in preset items/images.

###PIO.close()
Closes the widget.

###PIO.getCart()
Returns the user's current cart.

###PIO.getNumItems()
Returns the current number of items in the user's cart. It is recommended that this be used in conjunction with the options `fns.onCartChange()` callback-- `PIO.getNumItems()` is great for getting a pre-launched cart's items count wereas `fns.onCartChange()` is great for changing based on the user's live usage of the cart.



##Config/Open Options API

**Important** These options can be passed in to either the `PIO.config(options)` function or the `PIO.open(options)` function. It is recommended that one pass in items like `images` or `items` to `PIO.open(options)` and pass in items like the `recipeId` and `fns` callback functions to `PIO.config(options)`.

````html
<script src=”//az412349.vo.msecnd.net/widget-assets/pio.latest.js” />
<script>
PIO.config({
            
    //REQUIRED
    // apikey / recipeId
    recipeId: '',


    //optional
    //predefined images -- should be an array of strings that are absolute urls
    images: [],

    //optional
    //predefined items
    // an item should have the form
    // { productId:0, sku:'', templateName:'', images:[] }
    items: [],

    //optional
    //turn widget functionality on/off
    canUseUpload: true,
    canBuyOtherProducts: true,
    canUseMap: true,
    goToCustomize: false,

    //optional
    //go straight to a page in the widget
    goTo: '',

    //optional
    //an orderid-- would make the widget go straight to an orderid/review
    orderId: null,

    //optional
    //use back button wisely
    usePushState: false,

    //optional
    //whether or not to fade out the page's background
    fadeBackground: true,

    //all optional
    //pass in user preferences
    countryCode: '',
    currencyCode: '',
    languageCode: '',

    //all optional
    fns: {
        //callback for when the widget cart/order changes
        onCartChange: function (cart) {

        },
        //callback on widget close
        onClose: function () {

        },
        //callback on widget open
        onOpen: function () {

        }
    },


    //optional
    // url of widget (can be staging or live)
    url: 'http://staging.api.print.io/widget/'
});
</script>

````

Copyright 2012-2013 Breakout Commerce LLC
