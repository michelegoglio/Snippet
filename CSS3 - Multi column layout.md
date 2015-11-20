#CSS3 Multi-column Properties

* column-count
* column-gap
* column-rule-style
* column-rule-width
* column-rule-color
* column-rule
* column-span
* column-width

#CSS3 Create Multiple Columns

The column-count property specifies the number of columns an element should be divided into.

##FOR EXAMPLE:
````
<!DOCTYPE html>
    <html>
        <head>
            <style type="text/css"> 
                .newspaper {
                    -webkit-column-count: 3;
                    -moz-column-count: 3; 
                    column-count: 3;
                    text-align:justify;
                    color:#AA3344;
                }
            </style>
        </head>
        <body>
            <div class="newspaper">
            CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,CSS Global Forum, CSS Global Forum,
            </div>
        </body>
    </html>
````

#CSS3 Specify the Gap Between Columns
The column-gap property specifies the gap between the columns.
The following example specifies a 40 pixels gap between the columns:

##FOR EXAMPLE:
````
<!DOCTYPE html>
    <html>
        <head>
            <style type="text/css"> 
                .newspaper {
                    -webkit-column-count: 3; 
                    -moz-column-count: 3; 
                    column-count: 3;
                    -webkit-column-gap: 40px;
                    -moz-column-gap: 40px;
                    column-gap: 40px;
                    color:#CC1100;
                }
            </style>
        </head>
        <body>
            <div class="newspaper">
            CSS Global Forum, CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,
            </div>
        </body>
    </html>
````

#CSS3 Column Rules
The column-rule-style property specifies the style of the rule between columns:

##FOR EXAMPLE:
````
<!DOCTYPE html>
    <html>
        <head>
            <style type="text/css"> 
                .newspaper {
                    -webkit-column-count: 3; 
                    -moz-column-count: 3;
                    column-count: 3;
                    -webkit-column-gap: 40px;
                    -moz-column-gap: 40px;
                    column-gap: 40px;
                    -webkit-column-rule-style: solid;
                    -moz-column-rule-style: solid;
                    column-rule-style: solid;
                    color:#ABCDEF;
                }
            </style>
        </head>
        <body>
            <div class="newspaper">
            CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,
            </div>
        </body>
    </html>
````

The column-rule-width property specifies the width of the rule between columns:

##FOR EXAMPLE:
```` 
<!DOCTYPE html>
    <html>
        <head>
            <style type="text/css"> 
                .newspaper {
                    -webkit-column-count: 3;
                    -moz-column-count: 3;
                    column-count: 3;
                    -webkit-column-gap: 40px;
                    -moz-column-gap: 40px;
                    column-gap: 40px;
                    -webkit-column-rule-style: solid;
                    -moz-column-rule-style: solid;
                    column-rule-style: solid;
                    -webkit-column-rule-width: 1px;
                    -moz-column-rule-width: 1px;
                    column-rule-width: 1px;
                    color:#00AB11;
                }
            </style>
        </head>
        <body>
            <div class="newspaper">
            CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,
            </div>
        </body>
    </html>
````

##EXAMPLE:
````
<!DOCTYPE html>
    <html>
        <head>
            <style type="text/css"> 
            .newspaper {
                -webkit-column-count: 3;
                -moz-column-count: 3;
                column-count: 3;
                -webkit-column-gap: 40px;
                -moz-column-gap: 40px;
                column-gap: 40px;
                -webkit-column-rule-style: solid;
                -moz-column-rule-style: solid;
                column-rule-style: solid;
                -webkit-column-rule-width: 1px;
                -moz-column-rule-width: 1px;
                column-rule-width: 1px;
                -webkit-column-rule-color: lightblue; 
                -moz-column-rule-color: lightblue; 
                column-rule-color:#EE9999;
            }
            </style>
        </head>
        <body>
            <div class="newspaper">
            CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,
            </div>
        </body>
    </html>
````

##EXAMPLE:
````
<!DOCTYPE html>
    <html>
        <head>
            <style type="text/css"> 
            .newspaper {
                -webkit-column-count: 4; 
                -moz-column-count: 4;
                column-count: 4;
                -webkit-column-gap: 40px;
                -moz-column-gap: 40px;
                column-gap: 40px;
                -webkit-column-rule: 1px solid lightblue;
                -moz-column-rule: 1px solid lightblue;
                column-rule: 1px solid lightblue;
            }
            </style>
    </head>
    <body>
        <div class="newspaper">
            CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,
        </div>
    </body>
</html>
````

##FOR EXAMPLE:
````
<!DOCTYPE html>
    <html>
        <head>
            <style type="text/css"> 
            .newspaper {
                -webkit-column-count: 4; 
                -moz-column-count: 4;
                column-count: 4;
                -webkit-column-gap: 40px;
                -moz-column-gap: 40px;
                column-gap: 40px;
                -webkit-column-rule: 1px solid lightblue;
                -moz-column-rule: 1px solid lightblue;
                column-rule: 1px solid lightblue;
            }
            </style>
        </head>
        <body>
            <div class="newspaper">
            CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,CSS Global Forum,
            </div>
        </body>
    </html>
````
