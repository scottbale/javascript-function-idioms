!SLIDE subsection

# Encapsulation Idioms #

!SLIDE bullets incremental transition=fade
.notes blah

# Why Encapsulation? #

* No linker, only a single global object
* No native namespacing or visibility modifiers
* Anything can modify most anything

!SLIDE small transition=scrollUp
.notes typical HTML, many imports

    @@@ HTML
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>foo</title>
    <script type="text/javascript" src="/js/jquery-1.4.min.js"></script>
    <script type="text/javascript" src="/js/jquery.cycle.all.js"></script>
    <script type="text/javascript" src="/js/jquery-print.js"></script>
    <script type="text/javascript" src="/js/jquery.batchImageLoad.js"></script>
    <script type="text/javascript" src="/js/jquery.doubletap-0.1.js"></script>
    <script type="text/javascript" src="/js/fg.menu.js"></script>
    <script type="text/javascript" src="/js/showoff.js"></script>
    <script type="text/javascript" src="/js/jTypeWriter.js"> </script>
    <script type="text/javascript" src="/js/sh_main.min.js"></script>
    <script type="text/javascript" src="/js/core.js"></script>
    <script type="text/javascript" src="/js/showoffcore.js"></script>
    ...

!SLIDE bullets left incremental transition=scrollUp
.notes blah

# Encapsulation Techniques #

* simple namespacing
* private state with function closures
* Module pattern combines these two

!SLIDE

# Namespacing #
## Avoid global vars ##

	@@@ javaScript
    var COINS = {
        NICKEL : 5,
        DIME : 10,
        QUARTER : 25,
        isCoin : function(cents){
            return [this.NICKEL, this.DIME,
             this.QUARTER].contains(cents);
        }
    };

    result = COINS.NICKEL;

!SLIDE
.notes closure, capture lexical scope, free variables

# Function Closures #

	@@@ javaScript
    var coinReturn = [25, 25, 10];

    function isSufficientFunds(purchasePrice){
        var funds = 0;
        coinReturn.each(function(coin){
            funds+=coin;
        });
        return (funds >= purchasePrice);
    }

!SLIDE transition=scrollUp
.notes closure can persist beyond the life of the containing (outer) function

	@@@ javaScript

	var func = function(){
        var coinReturn = [25, 25, 10];

        function isSufficientFunds(purchasePrice){
            var funds = 0;
            coinReturn.each(function(coin){
                funds+=coin;
            });
            return (funds >= purchasePrice);
        }
        return isSufficientFunds;
    }();

    CORE.out(func(20));
    CORE.out(func.coinReturn);

!SLIDE smaller transition=scrollUp
.notes accomplishes both: namespacing, private state
.notes doesn't completely prevent tampering, but can preserve invariants

# A Module #

    @@@ javaScript
    var ACM = function(){
        var coinReturn = [];
        var coins = [];

        var doPurchase = function(purchasePrice){
            if (ifSufficientFunds(purchasePrice)){
                // ...
            }
        };
        //...
        return {
            deposit : function(coin){
                coinReturn.push(coin);
            },
            purchase : function(purchasePriceInCents){
                return doPurchase(purchasePriceInCents);
            }
            //...
        };
    }();

!SLIDE
.notes canonical example of module

# The Module Pattern #

    @@@ javaScript
    var MODULE = function(){
        var private state = //...

        var privateMethod = function(arg){
            // ...
        };

        return {
            publicMethod : function(arg){
                privateMethod(arg);
            },
        };
    }();

!SLIDE transition=scrollUp
.notes import another module - theoretically there's a runtime advantage

# Slight Variation #

    @@@ javaScript
    var MODULE = function(anotherModule){
        var private state = //...

        var privateMethod = function(arg){
            anotherModule.doSomething();
            // ...
        };

        return {
            publicMethod : function(arg){
                privateMethod(arg);
            },
        };
    }(ANOTHER_MODULE);

!SLIDE transition=scrollUp
.notes import another module - theoretically there's a runtime advantage

# Another Variation #

    @@@ javaScript
    (function(module){
        var private state = //...

        var privateMethod = function(arg){
            // ...
        };

        module.publicMethod = function(arg){
            privateMethod(arg);
        };
    }(ANOTHER_MODULE));

!SLIDE bullets incremental
.notes unlike other languages, there is no nesting of scope in blocks, only in function bodies

# Key Point #

* Functions are the <i>only</i> means of nesting scope
