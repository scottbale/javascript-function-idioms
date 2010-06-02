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

# Object prototype #

    @@@ javaScript
    delete Object.prototype.foo;
    var obj = new Object();
    CORE.out(obj.foo);
    Object.prototype.foo = function(){
        return "I am an object.";
    };
    CORE.out(obj.foo());

!SLIDE

# Pseudoclassical Inheritance #

    @@@ javaScript
    var Core = function(){
        this.name = "abstract core";
    };
    Core.prototype.out = function(output){
        alert(this.name + ": " + output);
    };
    Core.prototype.require = function(import){
        this.out("require: " + import);
    };

    var core = new Core();
    core.out("foo");
    core.require("jQuery.core.js");

!SLIDE smaller transition=scrollUp

    @@@ javaScript
    var Core = function(){
        this.name = "abstract core";
    };
    Core.prototype.out = function(output){
        alert(this.name + ": " + output);
    };
    Core.prototype.require = function(import){
        this.out("require: " + import);
    };
    var ShowoffCore = function(){
        this.name = "Showoff";
    };
    ShowoffCore.prototype = new Core();
    ShowoffCore.prototype.out = function(output){
        result = result || '';
        result = result + '<p>' + output + '</p>';
    };

    var core = new ShowoffCore();
    core.out("foo");
    core.require("jQuery.core.js");

!SLIDE bullets incremental

# Key Point #

* An object's hidden prototype link can *only* be set by the new operator

!SLIDE

# Functional Inheritance #

    @@@ javaScript
    var factory = function(o){
        var F = function(){};
        F.prototype = o;
        return new F();
    };

!SLIDE smaller transition=scrollUp

    @@@ javaScript
    var factory = function(o){
        var F = function(){};
        F.prototype = o;
        return new F();
    };
    var core = factory({
        out : function(output){
            alert(this.name + ": " + output);
        },
        require : function(import){
            this.out("require: " + import);
        }
    });
    var showoffCore = factory({
        out: function(output){
            result = result || '';
            result = result + '<p>' + output + '</p>';
        }
    });
    core.out("foo");
    showoffCore.out("foo");


