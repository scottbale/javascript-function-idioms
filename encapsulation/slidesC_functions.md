!SLIDE subsection

# Functions #

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
.notes function expression can be used anywhere that an expression is expected.
.notes Note the anonymous function expression parameter to the .each() method

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


!SLIDE execute
.notes functions are objects, so they can have their own properties (including other functions!)

# Functions are objects, too #

	@@@ javaScript
    var foo = function(){return false;};
    foo.bar = function(){return true;};
    foo.baz = 3;

    result = foo();

!SLIDE execute

# Functions are objects, too #

	@@@ javaScript
    var foo = function(){return false;};
    foo.bar = function(){return true;};
    foo.baz = 3;

    result = foo.bar();

!SLIDE transition=scrollUp
.notes excerpt from my own unit test runner
.notes example of passing functions as parameters

    @@@ javaScript
    var runTestsRecursive = function(tests){
        for (var prop in tests){
            var aTest = tests[prop];
            if (typeof aTest === 'function'){
                attemptTest(aTest);
            } else if (typeof aTest === 'object'){
                runTestsRecursive(aTest);
            }
        }
    };
    var attemptTest = function(testFunction){
        try {
            testFunction();
        } catch (e) {
            //...some stuff
        }
    };

