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

