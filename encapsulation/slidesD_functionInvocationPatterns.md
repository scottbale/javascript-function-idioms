!SLIDE subsection

# Function Invocation Patterns #

!SLIDE transition=fade
.notes 'this' keyword a lot different in JavaScript than in Java

# What is 'this'? #

	@@@ javaScript
    function(){
        return this.foo;
    }

!SLIDE bullets left transition=scrollUp
.notes it turns out, the object bound to 'this' keyword depends on how the function is invoked

# Four function invocation patterns #

* function
* method
* constructor
* apply

!SLIDE

# 'this' detector function #

    @@@ javaScript
    var thisDetector = function (){
        if (this === thisDetector){
            result = '\'this\' is me!';
        } else {
            result = '\'this\' is ' + this;
        }
    };

!SLIDE execute
.notes 'object Window' is the global object in the browser

# Function invocation pattern #

    @@@ javaScript
    var thisDetector = function (){
        if (this === thisDetector){
            result = '\'this\' is me!';
        } else {
            result = '\'this\' is ' + this;
        }
    };
    thisDetector();

!SLIDE execute
.notes 'object Window' is the global object in the browser

# Function invocation pattern #

    @@@ javaScript
    var containingFunction = function(){

        var thisDetector = function (){
            if (this === thisDetector){
                result = '\'this\' is me!';
            } else {
                result = '\'this\' is ' + this;
            }
        };
        thisDetector();
    }();

!SLIDE execute
.notes what do you think will be outputted?

# Method invocation pattern #

    @@@ javaScript
    var thisDetector = function (){
        if (this === thisDetector){
            result = '\'this\' is me!';
        } else {
            result = '\'this\' is ' + this;
        }
    };
    var testObject = {
        testMe:thisDetector,
        toString:function(){return "testObject"}
    };
    testObject.testMe();

!SLIDE execute

# Constructor invocation pattern #
.notes we will cover prototype in more detail later
.notes this pattern is typified by the use of the 'new' keyword

    @@@ javaScript
    var thisDetector = function (){
        if (this === thisDetector){
            result = '\'this\' is me!';
        } else {
            result = '\'this\' is ' + this;
        }
    };
    thisDetector.prototype.toString = function(){
        return "newly constructed object";
    };
    new thisDetector();

!SLIDE execute
.notes there are always two implicit hidden additional parameters in a function invocation: context for 'this, and arguments array
.notes 'apply()' method allows making these additional parameters explicit

# 'apply()' invocation pattern #
.notes 'apply' is a method available to functions (functions are objects)
.notes so, we're calling a method on a function which invokes it, rather than directly invoking the function

    @@@ javaScript
    var thisDetector = function (){
        if (this === thisDetector){
            result = '\'this\' is me!';
        } else {
            result = '\'this\' is ' + this;
        }
    };

    thisDetector.apply(thisDetector, []);

!SLIDE execute

# Apply different context #

    @@@ javaScript
    var thisDetector = function (){
        if (this === thisDetector){
            result = '\'this\' is me!';
        } else {
            result = '\'this\' is ' + this;
        }
    };

    thisDetector.apply(
      {toString:function(){return 'foo';}}, []);


!SLIDE execute
.notes example of specifying arguments - note there are no args in signature, but function sees three args anyway!

# 'apply()' with arguments #

    @@@ javaScript
    var argCounter = function (){
        result = arguments.length;
    };

    argCounter.apply({}, [false, 3, {}]);




