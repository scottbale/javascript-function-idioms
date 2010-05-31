!SLIDE

# Let's make an object #

	@@@ javaScript
    var COINS = new Object();
    COINS.nickel = 5;
    COINS.dime = 10;
    COINS.quarter = 25;
    COINS.isCoin = function(cents){
        return [COINS.NICKEL, COINS.DIME,
         COINS.QUARTER].contains(cents);
    };

!SLIDE

# Let's make an object #

	@@@ javaScript
    var COINS = {};
    COINS.nickel = 5;
    COINS.dime = 10;
    COINS.quarter = 25;
    COINS.isCoin = function(cents){
        return [COINS.NICKEL, COINS.DIME,
         COINS.QUARTER].contains(cents);
    };

!SLIDE

# Let's make an object - JSON #

	@@@ javaScript
    var COINS = {
        NICKEL : 5,
        DIME : 10,
        QUARTER : 25,
        isCoin : function(cents){
            return [COINS.NICKEL, COINS.DIME,
             COINS.QUARTER].contains(cents);
        }
    };

!SLIDE execute

# Iterating an object's properties #

	@@@ javaScript
    var COINS = {
        NICKEL : 5,
        DIME : 10,
        QUARTER : 25,
        isCoin : function(cents){
            return [COINS.NICKEL, COINS.DIME,
             COINS.QUARTER].contains(cents);
        }
    };
    result = '';
    for (var name in COINS){
        result = result + '|' + name
         + ':' + COINS[name];
    }

