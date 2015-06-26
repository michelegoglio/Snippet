````
<input class="datepicker" id="depart">
<input class="datepicker" id="return">
var dp1 = [];
var dp2 = [];
$("#depart").datepicker({
    numberOfMonths: 2,
    dateFormat: "m/dd/yy",
    onSelect: function (d) {
        dp1 = [];
        dp1.push(d);
    },
    beforeShowDay: function (date) {
        dmy = (date.getMonth() + 1) + "/" + date.getDate() + "/" + date.getFullYear();
        if ($.inArray(dmy, dp2) >= 0) {
            return [true, "foo"];
        } else {
            return [true, ""];
        }
    }    
});
$("#return").datepicker({
    numberOfMonths: 2,
    dateFormat: "m/dd/yy",
    onSelect: function (d) {
        dp2 = [];
        dp2.push(d);
    },
    beforeShowDay: function (date) {
        dmy = (date.getMonth() + 1) + "/" + date.getDate() + "/" + date.getFullYear();
        if ($.inArray(dmy, dp1) >= 0) {
            return [true, "foo"];
        } else {
            return [true, ""];
        }
    }
});
