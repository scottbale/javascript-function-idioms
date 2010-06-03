!SLIDE subsection

# Inheritance Idioms #

!SLIDE

# Pseudoclassical Inheritance #

    @@@ javaScript
    // a constructor aka pseudo-class
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

!SLIDE transition=scrollUp

    @@@ javaScript
    var Core = function(){this.name = "abstract core";};Core.prototype.out = function(output){alert(this.name + ": " + output);};Core.prototype.require = function(import){this.out("require: " + import);};
    var ShowoffCore = function(){
        this.name = "Showoff";
    };
    ShowoffCore.prototype = new Core();
    ShowoffCore.prototype.out=function(output){
        result = result || '';
        result = result+'<p>'+output+'</p>';
    };

    var core = new ShowoffCore();
    core.out("foo");
    core.require("jQuery.core.js");

!SLIDE bullets

# Key Point #

* An object's hidden prototype link can *only* be set by using the new operator

!SLIDE

# Prototypal Inheritance #

    @@@ javaScript
    var factory = function(o){
        var F = function(){};
        F.prototype = o;
        return new F();
    };

!SLIDE

# Prototypal Inheritance #

    @@@ javaScript
    Object.create = function(o){
        var F = function(){};
        F.prototype = o;
        return new F();
    };
!SLIDE

# Prototypal Inheritance #

    @@@ javaScript
    Object.create = function(o){
        var F = function(){};
        F.prototype = o;
        return new F();
    };
    Object.mixin = function(obj,mixin){
        for (name in mixin){
            if (mixin.hasOwnProperty(name)){
                obj[name] = mixin[name];
            }
        }
        return obj;
    };

!SLIDE transition=scrollUp

    @@@ javaScript
    var coreProto = {
        name : 'core',
        out : function(output){
            alert(this.name + ": " + output);
        },
        require : function(import){
            this.out("require: " + import);
        }
    }
    var showoffProto = Object.create(coreProto);
    showoffProto.name = 'showoff';
    showoffProto.out = function(output){
        result = result || '';
        result = result + '<p>' + this.name;
        result = result + ":" + output+'</p>';
    }

    var showoff1 = Object.create(showoffProto);
    showoff1.require("jQuery.js");

!SLIDE transition=scrollUp

    @@@ javaScript
    var coreProto = {
        name : 'core',
        out : function(output){
            alert(this.name + ": " + output);
        },
        require : function(import){
            this.out("require: " + import);
        }
    }
    var showoffProto =
    Object.mixin(Object.create(coreProto), {
        name : 'showoff',
        out : function(output){
            result=result || '';
            result=result+'<p>'+this.name;
            result=result+":"+output+'</p>';
        }
    });
    var showoff1 = Object.create(showoffProto);
    showoff1.require("jQuery.js");

!SLIDE

# Functional Inheritance #
## Combine prototypal inheritance with encapsulation ##

    @@@ javaScript
    var constructor = function(prototype){
        var a, b; // secret stuff

        var publicMethod = function(){
            // accesses secret stuff
        };

        return Object.mixin(
          Object.create(prototype),
          {'publicMethod':publicMethod}
          );
    };



