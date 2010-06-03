!SLIDE subsection

# Whirlwind Overview - Objects #
                     
!SLIDE
.notes When a function is a property of an object it is called a 'method'

# Let's make an object #

	@@@ javaScript
    var COINS = new Object();
    COINS.nickel = 5;
    COINS.dime = 10;
    COINS.quarter = 25;
    COINS.isCoin = function(cents){
        return [this.NICKEL, this.DIME,
         this.QUARTER].contains(cents);
    };

!SLIDE

# Let's make an object - JSON #

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

!SLIDE execute
.notes JS objects are associative arrays - name->value pairs
.notes accessing property using dot "." notation = refinement

# Accessing object properties #

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
!SLIDE execute

# Accessing object properties #
.notes accessing property using brackets [] with String literal

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

    result = COINS["NICKEL"];

!SLIDE execute

# Iterating an object's properties #
.notes 'for in' loop

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
    for (var name in COINS){
        CORE.out(name + ':' + COINS[name]);
    }

!SLIDE execute

## Cleaner Iteration - hasOwnProperty() and typeof ##
.notes 'for in' loop using 'hasOwnProperty' built-in function, and filtering out functions

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
    for (var name in COINS){
        if (COINS.hasOwnProperty(name)
         && typeof COINS[name] !== 'function'){
            CORE.out(name + ':' + COINS[name]);
        }
    }

