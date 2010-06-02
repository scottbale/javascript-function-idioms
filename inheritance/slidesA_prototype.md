!SLIDE subsection

# Prototype #

!SLIDE bullets incremental transition=fade
.notes blah

# JavaScript Prototypes #

* All objects have a _hidden_ link to a prototype
* If not specified, defaults to the prototype belonging to Object constructor
* All functions have a ".prototype" property, which is used to set the prototype link of any objects
created by calling that function as a constructor

!SLIDE center transition=scrollUp

![astonishment](astonishment.jpg)

!SLIDE execute transition=scrollUp
.notes built-in constructor functions: Object, Array, String, Boolean, Number, Function, RegExp

# built-in constructors #

    @@@ javaScript
    CORE.out(typeof Object);
    CORE.out(typeof Object.prototype);
    CORE.out(typeof Function);
    CORE.out(typeof String);
    CORE.out(typeof Array);
    CORE.out(typeof RegExp);
    CORE.out(typeof Number);

!SLIDE execute
.notes modify Object prototype

# Object prototype #

    @@@ javaScript
    delete Object.prototype.foo;
    var obj = new Object();
    CORE.out(obj.foo);
    Object.prototype.foo = function(){
        return "I am an object.";
    };
    CORE.out(obj.foo());

