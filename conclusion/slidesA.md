!SLIDE subsection

# Conclusion #

!SLIDE small

# Look Familiar?#

	@@@ html
    <html><head><LINK REL=stylesheet HREF="/irj/portalapps/com.sap.portal.design.portaldesigndata/themes/portal/mon_sap_ebp_theme/prtl_std/prtl_std_nn7.css?7.1.5.0.1">

    <script language="JavaScript">
    function clearEntries() {
        document.logonForm.longUid.value="";
        document.logonForm.password.value="";
    }

    function setFocusToFirstField() {
            myform = document.logonForm;
            for(i=0; i<myform.length; i++) {
                    elem = myform.elements[i];
                    if(elem.readOnly==false && elem.type=="text") {
                            elem.focus();
                            break;
                    }
            }
    }


!SLIDE small transition=scrollUp

	@@@ HTML
    function addTenantPrefix()
    {

    return true;
    }

    </script>
    <body>
    <table valign="middle" align="center" border="0" cellspacing="0" style="margin-top:10">
    <tr>
     <td colspan="2" valign="Top" height="24" class="welcome">
       <!-- Welcome<br> -->

       <!-- Yasaswy Bhupalam EBPP Canada French Changes. Commenting the below hard coded Text. Mar-01-2009 -->
      <!--Welcome -->
            Welcome<br>
      <!-- End changes-->

     </td>
    </tr> </table> </body></html

!SLIDE transition=fade

# jQuery core.js module #

    @@@ javaScript
    (function() {

        // Define a local copy of jQuery
        var jQuery = function( selector, context ) {
                // The jQuery object is just the
                // init constructor 'enhanced'
                return new jQuery.fn.init(
                           selector, context );
            },

        // ...900+ lines later

        // Expose jQuery to the global object
        window.jQuery = window.$ = jQuery;
    })();

!SLIDE bullets

# Credits/Links #

* [Douglas Crockford](http://www.crockford.com/)
* [JavaScript: The Good Parts](http://www.amazon.com/exec/obidos/ASIN/0596517742)
* [The Module Pattern](http://www.adequatelygood.com/2010/3/JavaScript-Module-Pattern-In-Depth)
* [jQuery](http://github.com/jquery)
* slides by [showoff](http://github.com/schacon/showoff)
* [http://github.com/scottbale](http://github.com/scottbale)


