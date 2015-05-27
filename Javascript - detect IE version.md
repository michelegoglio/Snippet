````
    var isIE = false;
    if (navigator.userAgent.indexOf('MSIE') != -1){
        var detectIEregexp = /MSIE (\d+\.\d+);/ //test for MSIE x.x
    }   else { // if no "MSIE" string in userAgent
        var detectIEregexp = /Trident.*rv[ :]*(\d+\.\d+)/ //test for rv:x.x or rv x.x where Trident string exists

        if (detectIEregexp.test(navigator.userAgent)){ //if some form of IE
            var ieversion=new Number(RegExp.$1); // capture x.x portion and store as a number
            if (ieversion<=11) {
                //egal ou inferieur a ie11"
                isIE = true;
            }
        }
    }
````
