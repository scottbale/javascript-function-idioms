!SLIDE subsection

# Inheritance Idioms #

!SLIDE execute

# Pseudoclassical Inheritance #

    @@@ javaScript
    // a constructor aka pseudo-class
    var FreeACM = function() {
        this.coinReturn = [];
    };
    FreeACM.prototype.purchase = function(price) {
        return true;
    };

    var acm = new FreeACM();
    CORE.out(acm.purchase(85));

!SLIDE execute transition=scrollUp

# "Subclass" #

    @@@ javaScript
    var FreeACM = function() {
        this.coinReturn = [];
    };
    FreeACM.prototype.purchase = function(price) {
        return true;
    };

    var PayACM = function() {};
    PayACM.prototype = new FreeACM();
    PayACM.prototype.purchase = function(price) {
        return this.coinReturn.length != 0;
    }

    var acm = new PayACM();
    CORE.out(acm.purchase(85));

!SLIDE transition=scrollUp

# Prototype.js #

    @@@ javaScript
    var FreeACM = Class.create({
      initialize: function() {
        this.coinReturn = [];
      },
      purchase: function(price) {
        return true;
      }
    });

    var PayACM = Class.create(FreeACM, {
      purchase: function(price) {
        return this.coinReturn.length != 0;
      }
    });


!SLIDE bullets

# Key Point #

* An object's hidden prototype link can *only* be set by using the new operator

!SLIDE

# Prototypal Inheritance #

    @@@ javaScript
    function(o){
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

!SLIDE execute transition=scrollUp

    @@@ javaScript
    var freeACM = {
        coinReturn : [],
        purchase : function(price) {
            return true;
        }
    }
    var payACM = Object.create(freeACM);
    payACM.purchase = function(price) {
        return this.coinReturn.length != 0;
    }

    CORE.out(freeACM.purchase(85));
    CORE.out(payACM.purchase(85));

!SLIDE

# Functional Inheritance #
## Combine prototypal inheritance with encapsulation ##

    @@@ javaScript
    var constructor = function(prototype){
        var a, b; // secret stuff

        var publicMethod = function(){
            // accesses secret stuff
        };

        var obj = Object.create(prototype);
        obj.publicMethod = publicMethod;
        return obj;
    };



