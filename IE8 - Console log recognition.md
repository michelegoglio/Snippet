````
//Console.log Fallback for Internet Explorer
if (!window.console) {
	window.console = new function () {
		this.log = function (str) { /* do nothing */ };
		this.dir = function (str) { /* do nothing */ };
	};
} 
````

ou
````
if (!window.console){ console = {log: function() {}} };
````
ou
````
if (typeof console === "undefined") {
    this.console = { log: function () { } };
}
````
