<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="stylesheet" href="style.css">
</head>
<body bgcolor="white">
<body>
<div class="panel">
<h1>Loki Quiz App</h1>
<div class="question" id="ques"></div>
<div class="options" id="opt"></div>
<button onclick="checkAns()" id="btn">SUBMIT</button>
<div id="score"></div>
<script src="script.js"></script>
</div>

</body>
</html>

<style>
body{
          background-image: url('https://igimages.gumlet.io/tamil/home/lokeshkanagaraj-27102022.jpg?w=376&dpr=2.6');
          background-repeat: no-repeat;
          background-attachment: fixed;
          background-size: cover;
        }body {
background-color: rgb(250, 250, 250);
}
.panel {
margin-top: 8%;
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
color: rgb(255, 255, 255);
}
.question {
font-size: 40px;

margin-bottom: 20px;
}
.options {
font-size: 20px;
display: grid;
background-color:rgb(10, 10, 10);
grid-template-columns: repeat(2, 1fr);
grid-gap: 20px;
margin-top: 10px;
margin-bottom: 20px;
position: fixed;
top: 40%;
left: 40%;
}
button {
margin-right: 75px;
margin-top: 17%;
font-size: 20px;
padding: 10px 20px;
background-color: #ffffff;
color: rgb(0, 0, 0);
border: none;
cursor: pointer;
}
#score {
font-size: 30px;
color: rgb(255, 255, 255);
}
</style>
<script>
const Questions = [{
q: "Which is the first Movie of Lokesh Kanagaraj?",
a: [{ text: "Leo", isCorrect: false },
{ text: "Vikram", isCorrect: false },
{ text: "Managaram", isCorrect: true },
{ text: "Kaithi", isCorrect: false }
]
},
{
q: "Where Lokesh Kanagaraj was Born in ?" ,
a: [{ text: "Chennai", isCorrect: false},
{ text: "Coimbatore", isCorrect: true },

{ text: "Tuticorin", isCorrect: false },
{ text: "Madurai", isCorrect: false }
]
},
{
q: "What is the first 100 Crore Movie of Loki",
a: [{ text: "Beast", isCorrect: false },
{ text: "Vikram", isCorrect: false },
{ text: "Kaithi", isCorrect: true },
{ text: "kolamavu Kokila", isCorrect: false }
]
},
{
q: "What is Loki's First short Film",
a: [{ text: "Hello", isCorrect: false },
{ text: "Dhruva", isCorrect: false },
{ text: "Kalam", isCorrect: true },
{ text: "Kadhal", isCorrect: false }
]
},
{
q: "What is his first Job?",
a: [{ text: "Police Officer", isCorrect: false },
{ text: "Bank Clerk", isCorrect: false },
{ text: "Bank Manager", isCorrect: true },
{ text: "Driver", isCorrect: false }
]
},
{
q: "Which college did Loki studied?",
a: [{ text: "Bannari Amman College", isCorrect: false },
{ text: "Karpagam College", isCorrect: false },
{ text: "Psg College", isCorrect: true },
{ text: "Hindhusthan College", isCorrect: false }
]
},
{
q: "Who is the favourite actor of Loki?",
a: [{ text: "Kamal", isCorrect: true},
{ text: "Rajini", isCorrect: false },
{ text: "Ajith", isCorrect: false },
{ text: "Vijay", isCorrect: false }
]
},
{
q: "Will SuperStar will be in LCU",
a: [{ text: "False", isCorrect: true},
{ text: "True", isCorrect: false },
]
},
{
q: "Whether loki get Married?",
a: [{ text: "Yes", isCorrect: true},
{ text: "No", isCorrect: false },
]
},
{
q: "Will Leo Comes in LCU?",
a: [{ text: "Yes", isCorrect: true},
{ text: "No", isCorrect: false },
]
},
]
let currQuestion = 0
let score = 0
function loadQues() {

const question = document.getElementById("ques")
const opt = document.getElementById("opt")
question.textContent = Questions[currQuestion].q;
opt.innerHTML = ""
for (let i = 0; i < Questions[currQuestion].a.length; i++) {
const choicesdiv = document.createElement("div");
const choice = document.createElement("input");
const choiceLabel = document.createElement("label");
choice.type = "radio";
choice.name = "answer";
choice.value = i;
choiceLabel.textContent = Questions[currQuestion].a[i].text;
choicesdiv.appendChild(choice);
choicesdiv.appendChild(choiceLabel);
opt.appendChild(choicesdiv);
}
}
loadQues();
function loadScore() {
const totalScore = document.getElementById("score")
totalScore.textContent = `You scored ${score} out of ${Questions.length}`
}

function nextQuestion() {
if (currQuestion < Questions.length - 1) {
currQuestion++;
loadQues();
} else {
document.getElementById("opt").remove()
document.getElementById("ques").remove()
document.getElementById("btn").remove()
loadScore();
}
}
function checkAns() {

const selectedAns =
parseInt(document.querySelector('input[name="answer"]:checked').value);
if (Questions[currQuestion].a[selectedAns].isCorrect) {
score++;
console.log("Correct")
nextQuestion();
} else {
nextQuestion();
}
}
</script>
</body>
</html>
