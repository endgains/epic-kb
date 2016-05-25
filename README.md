# epic-kb
Example of a knowledge base repository
<html>
<head>
<style>
{
	margin: 0;
	border: 0;
	padding: 0;
}
* {
	box-sizing: border-box;
}
p {
	font-family: Arial, Times New Roman, sans-serif;
	font-size: 1rem;
	line-height: 1.5;
}
h2 {
	font-size: 1.5rem;
	font-family: Arial, Tohoma, sans-serif;
	line-height: 1.6;
}
td {font-family: arial, sans-serif; font-size: 8pt; width: 50mm}
.formfield {font-size: 8pt; width: 50mm}
.banner {color: #000000; background: #ff8100}
.note {color: #000000; background: #dddddd}
.table_main {width: 50%; margin-bottom: 5mm}
.table_sub {margin-bottom: 2mm; margin-top: 2mm; margin-left: 2mm; margin-right: 2mm}
.table_note {color: #000000; background: #dddddd}
.table_skip {background: #dddddd}
select {
    padding: 8px 10px;
    border: none;
    background-color: white;
	width: 50mm;
	font-size: 110%;
}
select:hover {
    background-color: #ffe6e6;
}
input [type="button"] {font-size: 1rem; width: 20mm}
</style>
<script src="https://code.jquery.com/jquery-2.2.3.min.js"></script>
<link href='https://fonts.googleapis.com/css?family=Open+Sans:400,700' rel='stylesheet' type='text/css'>
<link rel="stylesheet" href="style.css"></input>
</head>
<body>
<h2>Knowledge Base Page Example</h2>
<table>
<tr><td class='banner'>Choose</td><td class='banner'>Question</td></tr>
<tr><td><span class='A'></span></td><td><span class='Q'></span></td></tr>
<tr><td><span class='A'></span></td><td><span class='Q'></span></td></tr>
<tr><td><span class='A'></span></td><td><span class='Q'></span></td></tr>
<tr><td><span class='A'></span></td><td><span class='Q'></span></td></tr>
<tr><td><button onClick='showAnswer()'>Show answer</button></td><td><span id='finalAnswer'></span></td></tr>
</table>
<script>
questions = $(".Q").toArray()
answers = $(".A").toArray()

// Collate questions to ask
function questionChanger(level){

	// Initially clear final answer span
	$('#finalAnswer').html("");
	
	// Sart questions
	if (level == 0){
		questions[level].innerHTML = "Do you exercise?";
		var exercise = "<select id='exerciseAnswer' class='formfield' onChange='questionChanger("+(level+1)+")'>";
			exercise += "<option value=''>Choose</option>";
			exercise += "<option value='yes'>Yes</option>";
			exercise += "<option value='no'>No</option>";
			exercise += "</select>";
		answers[level].innerHTML = exercise;
	}
	else if (level == 1){
		if ($('#exerciseAnswer').val() == "yes") {
			questions[level].innerHTML = "What are your fitness goals?"
				var goals = "<select id='goalsAnswer' class='formfield' onChange='questionChanger("+(level+1)+")'>";
				goals += "<option value=''>Choose</option>";
				goals += "<option value='weightLoss'>Weight loss</option>";
				goals += "<option value='strength'>Strength</option>";
				goals += "<option value='mass'>Mass</option>";
				goals += "</select>";
			answers[level].innerHTML = goals;
		}
		else if ($('#exerciseAnswer').val() == "no") {
			questions[level].innerHTML = "Are you considering exercise?"
				var consider = "<select id='considerAnswer' class='formfield' onChange='questionChanger("+(level+1)+")'>";
				consider += "<option value=''>Choose</option>";
				consider += "<option value='yes'>Yes</option>";
				consider += "<option value='no'>No</option>";
				consider += "</select>";
			answers[level].innerHTML = consider;
		}
	}
	else if (level == 2){
			questions[level].innerHTML = "Question #3"
			answers[level].innerHTML = "<select id='Q3' class='formfield' onChange='questionChanger("+(level+1)+")'><option value='none'>Neither</option><option value='a'>Show answer #4a</option><option value='b'>Show answer #4b</option></input>"
	}
	else if (level == 3){
		if ($('#Q3').val() == "a"){
			questions[level].innerHTML = "Question #4 (a) (Shows if user selected 'a')"
			answers[level].innerHTML = "<input type='checkbox' id='Q4a'>"
		}
		else if ($('#Q3').val() == "b"){
			questions[level].innerHTML = "Question #4 (b) (Shows if user selected 'b')"
			answers[level].innerHTML = "<input type='checkbox' id='Q4b'>"
		}
		else{
			questions[level].innerHTML = ""
			answers[level].innerHTML = ""
		}
	}
}
function showAnswer(){
var content = ""
if($('#Q1').prop('checked')){
content = "<h3>Stop point selected</h3>"
content += "<p>What the user should do if they checked question 2.</p>"
content += "<p>As this is a stop point no other instructions show</p>"
}
else{
content += "<h3>Standard instructions for everyone</h3>"
content += "<p>Some standard instructions</p>"
if($('#Q0').prop('checked')){
content += "<h3>Question #1 checked</h3>"
content += "<p>What to do if question #1 is checked</p>"
}
if ($('#Q3').val() == "a"){
content += "<h3>'A' selected at question 3</h3>"
content += "<p>What the user should do if they selected 'A' at question 3</p>"
if($('#Q4a').prop('checked')){
content += "<h3>'4a' selected at question 4</h3>"
content += "<p>What the user should do if they checked question 4a</p>"
}
}
if ($('#Q3').val() == "b"){
content += "<h3>'B' selected at question 3</h3>"
content += "<p>What the user should do if they selected 'B' at question 3</p>"
if($('#Q4b').prop('checked')){
content += "<h3>'4b' selected at question 4</h3>"
content += "<p>What the user should do if they checked question 4b</p>"
}
}
}
$('#finalAnswer').html(content)
}
questionChanger(0)
</script>
</body>
</html>
