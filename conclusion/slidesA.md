!SLIDE small

# Bad JavaScript - Look Familiar?#

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


