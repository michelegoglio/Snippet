````
<!DOCTYPE html>
<html>
<head>
<title></title>
<style>
	textarea{
		border:solid 2px #ccc;
		clear:both;
		display:block;
		margin:20px 0;
		height:500px;
		width:600px;
		padding:2px;
	}
</style>
</head>
<body>

<textarea id="HTMLToValidate"></textarea>
<a id='validationHTML' href='javascript:void(0)'>Validation</a>
<br/><br/>
<div id='errorMsg'></div>
<div id='errorMsgBeginTags'></div>
<div id='errorMsgEndTags'></div>

<script src="jquery-3.1.1.min.js"></script>
<script>
$(document).ready(function(){
	var arrayHTMLTagBegin = ['<h1>','<h2>','<h3>','<h4>','<h5>','<h6>','<div>','<p>','<table>','<ol>','<ul>','<li>','<span>','<tr>','<td>','<tbody>','<th>'];
	var arrayHTMLTagEnd = ['</h1>','</h2>','</h3>','</h4>','</h5>','</h6>','</div>','</p>','</table>','</ol>','</ul>','</li>','</span>','</tr>','</td>','</tbody>','</th>'];

	var arraySequenceBeginingTable = ['<table><tr><td>','<table>','<tr><td>','begin'];
	var arraySequenceEndingTable = ['</td></tr></table>','</table>','</td></tr>','end'];
	var arraySequenceBeginingUnorderedList = ['<ul><li>','<ul>','<li>','begin'];
	var arraySequenceEndingUnorderedList = ['</li></ul>','</ul>','</li>','end'];
	var arraySequenceBeginingOrderedList = ['<ol><li>','<ol>','<li>','begin'];
	var arraySequenceEndingOrderedList = ['</li>/<ol>','</ol>','</li>','end'];

    var arraySequence = {
    	arraySequenceBeginingTable:arraySequenceBeginingTable,
    	arraySequenceEndingTable:arraySequenceEndingTable, 
    	arraySequenceBeginingUnorderedList:arraySequenceBeginingUnorderedList,
    	arraySequenceEndingUnorderedList:arraySequenceEndingUnorderedList,
    	arraySequenceBeginingOrderedList:arraySequenceBeginingOrderedList,
    	arraySequenceEndingOrderedList:arraySequenceEndingOrderedList
    }

	var validationHTML = $('#validationHTML');
	var HTMLToValidate = $('#HTMLToValidate');

	validationHTML.click(function(e) {
	    e.preventDefault();
	    var temporaryHTMLToValidate = HTMLToValidate.val();
		var equalBeginEndTag = verifyEQualBeginEndTag(temporaryHTMLToValidate, arrayHTMLTagBegin, arrayHTMLTagEnd);

		var sequenceTags = verifySequenceTags(temporaryHTMLToValidate,arraySequence);
	});

	function verifySequenceTags(str,arraySequence){
		$('#errorMsg').empty();
		var msg = '';
		$.each( arraySequence, function( key, value ) {
			var keySequence = key;
			var arraySequenceToTest = value;
			var sequence = arraySequenceToTest[0];
			var sequenceReference = arraySequenceToTest[1];
			var sequenceStringSearch = arraySequenceToTest[2];
			var sequenceSearchWay = arraySequenceToTest[3];
			var arrayIndex = [];
			
			var arraySequenceToFix =[];
			cr=0;

			// creation d'un tableau d'index de positionnement pour chaque sequence de reference existante dans la string de depart
			var stringMatch = new RegExp(sequenceReference, 'g'), match;
			while (match = stringMatch.exec(str)) {
				arrayIndex.push(match.index);
			}
			for(i=0; i<arrayIndex.length; i++){
				// test si la sequence est une sequence de depart ou de fin pour pouvoir calculer la string a extraire 
				if(sequenceSearchWay == 'begin'){
					substringSequence = str.substring(arrayIndex[i],arrayIndex[i] + sequenceReference.length + sequenceStringSearch.length);
				} else if(sequenceSearchWay == 'end'){
					substringSequence = str.substring(arrayIndex[i] - sequenceStringSearch.length, arrayIndex[i] + sequenceReference.length);
				}
			
				if(substringSequence != sequence){
					// calcul du nombrede fois que la sequence n'est pas respectée
					cr++;
				}
			}
			if(cr > 0){
				msg += 'La sequence ' + sequence + 'n\'est pas respectée ' + cr + 'fois';
			}
		});
		$('#errorMsg').text(msg);	
		
	}
	function verifyEQualBeginEndTag(str,arrayHTMLTagBegin,arrayHTMLTagEnd) {
		var arrayContentBeginTag = [];
		var arrayContentEndTag = [];
		var msgMissingBeginTags = '';
		var msgMissingEndTags = '';
		var msgMissingTags = '';
	    for (var i = 0; i != arrayHTMLTagBegin.length; i++) {
	       var substringTagBegin = arrayHTMLTagBegin[i];
	       var contentBeginTag = str.split(substringTagBegin).length - 1;
	       arrayContentBeginTag.push(contentBeginTag);
	    }
	    for (var i = 0; i != arrayHTMLTagEnd.length; i++) {
	       var substringTagEnd = arrayHTMLTagEnd[i];
	       var contentEndTag = str.split(substringTagEnd).length - 1;
	       arrayContentEndTag.push(contentEndTag);
	    }	

	    // si les tableaux n'ont pas de html, ne passe pas dans la fonction pour les tester
		var forTest =0;
	    for (var i = 0; i != arrayContentBeginTag.length; i++){
	    	arrayContentBeginTag[i] !== 0 && forTest !==1 ? forTest = 1 : '';
	    }   
	    for (var i = 0; i != arrayContentEndTag.length; i++){
	    	arrayContentEndTag[i] !== 0 && forTest !==1 ? forTest = 1 : '';
	    }   
    
	    //comparaison des 2 arrays de debut et de fin pour voir si le nombre d'éléments est le même
	    if(forTest === 1) {
		    var arrayTagToFix = compareArrays(arrayContentBeginTag, arrayContentEndTag);
	 		$('#errorMsgBeginTags').empty();
	 		$('#errorMsg').empty();
	 		$('#errorMsgEndTags').empty();

			var arrayTagToFixBegin = arrayTagToFix.arrayTagToFixBegin;
			if(arrayTagToFixBegin.length > 0){
				var arrayTagNumberToFixBegin = arrayTagToFix.arrayTagNumberToFixBegin;
			 	for(i=0; i<arrayTagToFixBegin.length; i++){
		 			msgMissingBeginTags += arrayTagNumberToFixBegin[i] + ' ' + arrayHTMLTagBegin[arrayTagToFixBegin[i]];
		 			if(i<arrayTagToFixBegin.length - 1){
			 				msgMissingBeginTags += ', ';
					}
			    }
			    $('#errorMsgBeginTags').text('HTML tags de début manquants :' + msgMissingBeginTags);
			}

		    var arrayTagToFixEnd = arrayTagToFix.arrayTagToFixEnd;
		    if(arrayTagToFixEnd.length > 0){
			    var arrayTagNumberToFixEnd = arrayTagToFix.arrayTagNumberToFixEnd;
		 		for(i=0; i<arrayTagToFixEnd.length; i++){
		 			msgMissingEndTags += arrayTagNumberToFixEnd[i] + ' ' + arrayHTMLTagEnd[arrayTagToFixEnd[i]];
		 			if(i<arrayTagToFixEnd.length - 1){
		 				msgMissingEndTags += ', ';
					}
		 		}
				$('#errorMsgEndTags').text('HTML tags de fin manquants :' + msgMissingEndTags);
			}

			// affichage message info lorsque le nombre de tags entrants et sortants est identique
			if(arrayTagToFixEnd.length === 0 && arrayTagToFixBegin.length === 0){
				$('#errorMsgBeginTags').empty();
				$('#errorMsgEndTags').empty();
				$('#errorMsg').text('pas d\'erreurs HTML');
			}

	    } else {
	    	// affichage message info lorsqu'aucun tag HTML n'est trouvé dans la string à tester
			$('#errorMsgBeginTags').empty();
			$('#errorMsgEndTags').empty();	    	
			$('#errorMsg').text('pas de tags HTML à tester');
	    }
	}

	function compareArrays(arrayA,arrayB) {
		var arrayTagToFix = [];
		var arrayTagToFixBegin = [];
		var arrayTagToFixEnd = [];
		var arrayTagNumberToFixBegin = [];
		var arrayTagNumberToFixEnd = [];
		var arrayNumber = 0;

	    for (j = 0; j < arrayA.length; j++){
	        if (arrayA[j] !== arrayB[j]) {
	        	//creation d'arrays pour nombre de tags début/fin non égaux;
	        	if(arrayA[j] > arrayB[j]){
	        		arrayTagToFixEnd.push(j);
	        		arrayNumber = arrayA[j] -  arrayB[j];
	        		arrayTagNumberToFixEnd.push(arrayNumber);
	        	} else {
	        		arrayTagToFixBegin.push(j);
	        		arrayNumber = arrayB[j] - arrayA[j];
	        		arrayTagNumberToFixBegin.push(arrayNumber);	
	        	}
	        } 
	    }
	    var arrayTagToFix = {
	    	arrayTagToFixBegin:arrayTagToFixBegin,
	    	arrayTagNumberToFixBegin:arrayTagNumberToFixBegin, 
	    	arrayTagToFixEnd:arrayTagToFixEnd, 
	    	arrayTagNumberToFixEnd:arrayTagNumberToFixEnd
	    }
	    return arrayTagToFix;
	}
}); 


</script>
</body>

</html>
````
