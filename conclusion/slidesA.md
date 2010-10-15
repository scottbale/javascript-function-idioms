!SLIDE subsection

# The Wrap-Up #

!SLIDE

# jQuery #

    @@@ javaScript
    $('div.clickable').click(function(){
        $(this).attr('class', 'clicked');
    });

!SLIDE transition=scrollUp

# jQuery core.js module #

    @@@ javaScript
    (function() {

        // Define a local copy of jQuery
        var jQuery = function( selector, context ) {
                // The jQuery object is just the
                // init constructor 'enhanced'
                return new jQuery.fn.init(
                           selector, context );
            },

        // ...900+ lines later

        // Expose jQuery to the global object
        window.jQuery = window.$ = jQuery;
    })();

!SLIDE bullets

# Links #

* [Douglas Crockford](http://www.crockford.com/)
* [JavaScript: The Good Parts](http://www.amazon.com/exec/obidos/ASIN/0596517742)
* [The Module Pattern](http://www.adequatelygood.com/2010/3/JavaScript-Module-Pattern-In-Depth)
* slides by [showoff](http://github.com/schacon/showoff)
* [http://github.com/scottbale](http://github.com/scottbale)


