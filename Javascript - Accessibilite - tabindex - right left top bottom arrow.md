```
// tabs, left up right down arrows 
function tabIndex() {
    var tabindex = 1; 
    $("[TabIndex='" + tabindex + "']").focus();
    $("[TabIndex='" + tabindex + "']").removeClass("focusIn");
    var tabIndexLength = $("[TabIndex]").length;
    document.onkeydown = checkKey;
    function checkKey(e) {
        e = e || window.event;
        
        if (e.keyCode == '39' || e.keyCode == '40' || (e.keyCode == '9' && !e.shiftKey)) {
            //right arrow, down arrow, tab
            tabindex++;
            $("[TabIndex='" + tabindex + "']").addClass("focusIn");
            //while element exist or it's readonly and tabindex not reached max do
            while (($("[TabIndex='" + tabindex + "']").length == 0 || $("[TabIndex='" + tabindex + "']:not([readonly])").length == 0) && tabindex != (tabIndexLength + 1)) {
                tabindex++;
            }
            if (tabindex == (tabIndexLength + 1)) { tabindex = 1 } //reseting tabindex if finished
            $("[TabIndex]").removeClass("focusIn");
            $("[TabIndex='" + tabindex + "']").focus();
            $("[TabIndex='" + tabindex + "']").addClass("focusIn");
            return false;
        }
        if (e.keyCode == '37' || e.keyCode == '38' || (e.keyCode == '9' && e.shiftKey)) {
            //left arrow, up arrow, shift + tab 
            tabindex--;
            //while element exist or it's readonly and tabindex not reached max do
            while (($("[TabIndex='" + tabindex + "']").length == 0 || $("[TabIndex='" + tabindex + "']:not([readonly])").length == 0) && tabindex >= 1) {
                tabindex--;
            }
            if (tabindex < 1) {
                tabindex = tabIndexLength;
            } //reseting tabindex if finished
            $("[TabIndex]").removeClass("focusIn");
            $("[TabIndex='" + tabindex + "']").focus();
            $("[TabIndex='" + tabindex + "']").addClass("focusIn");
            return false;
        }
    }
    $("*").click(function () {
        $("*").removeClass("focusIn");
    });
}
```
