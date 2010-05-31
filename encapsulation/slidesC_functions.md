!SLIDE execute

# Function Statement #

	@@@ javaScript
    var coinReturn = [25, 25, 10];
    var coins = [];

    function isSufficientFunds(purchasePrice){
        var funds = 0;
        coinReturn.each(function(coin){
            funds+=coin;
        });
        return (funds >= purchasePrice);
    }

    result = isSufficientFunds(60);

!SLIDE execute

# Function Expression #

	@@@ javaScript
    var coinReturn = [10, 5, 25];
    var coins = [];

    var isSufficientFunds = function(purPrice){
        var funds = 0;
        coinReturn.each(function(coin){
            funds+=coin;
        });
        return (funds >= purPrice);
    };

    result = isSufficientFunds(75);


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

!SLIDE execute

# Cleaner Iteration #

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
        if (COINS.hasOwnProperty(name)
         && typeof COINS[name] !== 'function'){
            result = result + '|' + name
             + ':' + COINS[name];
        }
    }

