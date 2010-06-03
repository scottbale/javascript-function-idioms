!SLIDE subsection

# Prototype #

!SLIDE bullets incremental transition=fade
.notes blah

# JavaScript Prototypes #

* All objects have a _hidden_ link to a prototype
* If not specified, defaults to the prototype belonging to Object constructor
* All functions have a ".prototype" property, which is used to set the prototype link of any objects
created by calling that function as a constructor

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

# prototype #
## changes to prototype inherited by all instances ##

    @@@ javaScript
    delete Object.prototype.foo;
    
    var obj = new Object();

    CORE.out(obj.foo);

    Object.prototype.foo = function(){
        return "I am an object.";
    };
    CORE.out(obj.foo());

!SLIDE execute
.notes adding to obj does not affect obj's prototype

# prototype #
## modifying 'obj' does not affect prototype ##

    @@@ javaScript
    Object.prototype.foo = 2112;

    var obj = new Object();
    CORE.out(obj.foo);

    obj.foo = 42;
    CORE.out(obj.foo);
    CORE.out(Object.prototype.foo);

    delete Object.prototype.foo;
    CORE.out(obj.foo);

!SLIDE

# Extending the Language #

    @@@ javaScript
    Function.prototype.method
                   = function (name, func) {
        if (!this.prototype[name]){
            this.prototype[name] = func;
            return this;
        }
    };
    Array.method('each', function(f, index){
        for (var i=0; i<this.length; i++){
            f(this[i], i);
        }
    });

    [2,3,5].each(function(item){CORE.out(item);});
