````
clearTimeout($.data(this, "scrollCheck"));
$.data(this, "scrollCheck", setTimeout(function () {
  alert("end of scrolling");
}, 250));
