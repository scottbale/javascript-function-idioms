!SLIDE subsection

# Idioms for Inheritance #


!SLIDE execute

# Executable JavaScript #

    @@@ javaScript
    Function.prototype.method
               = function (name, func) {
        if (!this.prototype[name]){
            this.prototype[name] = func;
            return this;
        }
    }

    String.method('trim', function(){
        return this.replace(/^\s+|\s+$/g, '');
    });

    result = '[' + '     neat      '.trim() + ']';

!SLIDE execute

    @@@ javaScript
    var coinReturn = [25,5,10,5];
    coinReturn.each(function(coin){
        result+=coin;
    });

!SLIDE execute

    @@@ javaScript
    Function.prototype.method = function (name, func) {
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

    var coinReturn = [25,5,10,5];
    coinReturn.each(function(coin){
        result+=coin;
    });

!SLIDE execute

    @@@ javaScript
    Array.method('reduce', function(f, value){
        this.each(function(item){
            value = f(item, value);
        });
        return value;
    });

    var coinReturn = [25,5,10,5];

    result = coinReturn.reduce(function(coin, runningTotal){
        return coin + runningTotal;
    }, 0);