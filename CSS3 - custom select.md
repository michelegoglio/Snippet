````
<label>
  text label
  <select>
    <option selected> Select Box </option>
    <option>Short Option</option>
    <option>This Is A Longer Option</option>
  </select>
</label>

select {
  font-size:18px;
  padding:3px;
  margin: 0;
  max-height: 300px;
  min-width: 100px;
  background: #fff;
  color: #0071B3;
  border:0;
  border-bottom: 3px solid #0071B3;
  line-height: 22px;
  outline:none;
  display: inline-block;
  padding: 5px 20px 5px 5px;
  -webkit-appearance:none;
  -moz-appearance:none;
  appearance:none;
  cursor:pointer;
}

/* Targetting Webkit browsers only. FF will show the dropdown arrow with so much padding. */
@media screen and (-webkit-min-device-pixel-ratio:0) {
  select {padding-right:18px}
}

label {
  position:relative;
}
label:after {
  content:'>';
  font:18px "Consolas", monospace;
  color: #0071B3;
  -webkit-transform:rotate(90deg);
  -moz-transform:rotate(90deg);
  -ms-transform:rotate(90deg);
  transform:rotate(90deg);
  right:8px; 
  top:0;
  padding:0 0 2px;
  position:absolute;
  pointer-events:none;
}
label:before {
  content: '';
  right: 6px;
  top: 0px;
  width: 20px;
  height: 20px;
  background: #f8f8f8;
  position: absolute;
  pointer-events: none;
  display: block;
}
````
