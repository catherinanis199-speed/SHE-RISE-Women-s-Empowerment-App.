<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SHE RISE - Learning Hub</title>

<style>
* { box-sizing: border-box; }

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #fff5fa;
  color: #39243b;
}

header {
  background: #922c78;
  color: white;
  padding: 22px;
  text-align: center;
}

header h1 { margin: 0; font-size: 30px; }

nav {
  background: #70205f;
  padding: 15px;
  text-align: center;
}

nav a {
  color: white;
  text-decoration: none;
  margin: 10px;
}

.hero {
  text-align: center;
  padding: 45px 15px;
  background: linear-gradient(135deg,#f8c6e3,#e7c7ff);
}

.hero h2 { font-size: 30px; }

button {
  background: #922c78;
  color: white;
  border: none;
  padding: 12px 20px;
  border-radius: 20px;
  cursor: pointer;
  margin: 5px;
}

button:hover { background: #70205f; }

section { padding: 30px 18px; text-align: center; }

h2 { color: #922c78; }

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit,minmax(210px,1fr));
  gap: 18px;
  max-width: 950px;
  margin: auto;
}

.card {
  background: white;
  padding: 25px;
  border-radius: 15px;
  box-shadow: 0 3px 12px #00000015;
}

.emoji { font-size: 40px; }

#lessonArea {
  display: none;
  max-width: 750px;
  margin: 25px auto;
  background: white;
  padding: 25px;
  border-radius: 15px;
  text-align: left;
  box-shadow: 0 3px 12px #00000015;
}

#lessonArea h2 { text-align: center; }

.lesson {
  background: #fff0f8;
  padding: 15px;
  border-radius: 10px;
  margin: 12px 0;
}

#quizArea {
  background: #f9e9f5;
  padding: 20px;
  border-radius: 12px;
  margin-top: 20px;
}

footer {
  background: #70205f;
  color: white;
  text-align: center;
  padding: 20px;
}
</style>
</head>

<body>

<header>
  <h1>🌸 SHE RISE</h1>
  <p>Dream Big. Learn More. Rise Together.</p>
</header>

<nav>
  <a href="#home">Home</a>
  <a href="#learning">Learning Hub</a>
  <a href="#about">About</a>
</nav>

<div class="hero" id="home">
  <h2>Welcome to SHE RISE!</h2>
  <p>Learn new skills, discover opportunities and build your future.</p>
  <button onclick="document.getElementById('learning').scrollIntoView()">Start Learning</button>
</div>

<section id="learning">
  <h2>🌸 Learning Hub</h2>
  <p>Choose a subject and start your free learning journey!</p>

  <div class="cards">

    <div class="card">
      <div class="emoji">💻</div>
      <h3>Computer Skills</h3>
      <p>Learn HTML, CSS, Python and Java basics.</p>
      <button onclick="openSubject('computer')">Start Learning</button>
    </div>

    <div class="card">
      <div class="emoji">🗣️</div>
      <h3>English Skills</h3>
      <p>Improve grammar and communication.</p>
      <button onclick="openSubject('english')">Start Learning</button>
    </div>

    <div class="card">
      <div class="emoji">💰</div>
      <h3>Financial Education</h3>
      <p>Understand budgeting and saving.</p>
      <button onclick="openSubject('finance')">Start Learning</button>
    </div>

    <div class="card">
      <div class="emoji">🎯</div>
      <h3>Career Development</h3>
      <p>Prepare for interviews and jobs.</p>
      <button onclick="openSubject('career')">Start Learning</button>
    </div>

  </div>

  <div id="lessonArea">
    <h2 id="subjectTitle"></h2>
    <p id="subjectIntro"></p>
    <div id="lessons"></div>
    <div id="quizArea">
      <h3>📝 Practice Quiz</h3>
      <p id="question"></p>
      <div id="answers"></div>
      <p id="result"></p>
    </div>
    <button onclick="closeSubject()">Back to Subjects</button>
  </div>
</section>

<section id="about">
  <h2>Our Mission</h2>
  <p>To help every woman learn, grow, become confident and independent.</p>
</section>

<footer>
  <p>© 2026 SHE RISE | Together We Rise 🌸</p>
</footer>

<script>

const subjects = {

computer: {
 title: "💻 Computer Skills",
 intro: "Start your journey into the world of technology!",
 lessons: [
  {
   name: "Lesson 1: What is HTML?",
   text: "HTML stands for HyperText Markup Language. It is used to create the structure of websites.",
   example: "<h1>Hello World</h1> creates a large heading."
  },
  {
   name: "Lesson 2: What is CSS?",
   text: "CSS stands for Cascading Style Sheets. It controls the colours, fonts and layout of websites.",
   example: "h1 { color: purple; } makes a heading purple."
  },
  {
   name: "Lesson 3: What is Python?",
   text: "Python is a beginner-friendly programming language used for websites, automation and data analysis.",
   example: "print('Hello World') displays Hello World."
  }
 ],
 quiz: {
  q: "Which language is used to create the structure of a website?",
  a: ["HTML","CSS","Python"],
  correct: 0
 }
},

english: {
 title: "🗣️ English Skills",
 intro: "Improve your English one lesson at a time!",
 lessons: [
  {
   name: "Lesson 1: Nouns",
   text: "A noun is a naming word. It names a person, place, animal or thing.",
   example: "Examples: Woman, Bengaluru, book and school."
  },
  {
   name: "Lesson 2: Verbs",
   text: "A verb is an action word.",
   example: "Examples: Read, write, walk and learn."
  },
  {
   name: "Lesson 3: Simple Sentences",
   text: "A sentence is a group of words that expresses a complete thought.",
   example: "Example: She is learning English."
  }
 ],
 quiz: {
  q: "Which of these is a verb?",
  a: ["Book","Running","School"],
  correct: 1
 }
},

finance: {
 title: "💰 Financial Education",
 intro: "Learn how to manage your money wisely!",
 lessons: [
  {
   name: "Lesson 1: What is Saving?",
   text: "Saving means keeping some of your money for future needs.",
   example: "If you receive ₹1000 and save ₹200, you keep ₹200 for later."
  },
  {
   name: "Lesson 2: Budgeting",
   text: "A budget is a plan for how you will spend and save your money.",
   example: "Divide your money between needs, savings and wants."
  },
  {
   name: "Lesson 3: Needs and Wants",
   text: "Needs are essential things. Wants are things you would like to have.",
   example: "Food is a need. A new luxury handbag is usually a want."
  }
 ],
 quiz: {
  q: "What does saving mean?",
  a: ["Spending everything","Keeping money for later","Borrowing money"],
  correct: 1
 }
},

career: {
 title: "🎯 Career Development",
 intro: "Build confidence and prepare for your career!",
 lessons: [
  {
   name: "Lesson 1: Resume Basics",
   text: "A resume is a document that presents your education, skills and experience.",
   example: "Include your name, education, skills and projects."
  },
  {
   name: "Lesson 2: Interview Skills",
   text: "Prepare for common questions and practise speaking clearly.",
   example: "Practise answering: Tell me about yourself."
  },
  {
   name: "Lesson 3: Communication",
   text: "Good communication means sharing your ideas clearly and listening carefully.",
   example: "Speak politely, confidently and clearly."
  }
 ],
 quiz: {
  q: "What is a resume mainly used for?",
  a: ["Applying for jobs","Ordering food","Playing games"],
  correct: 0
 }
}

};

function openSubject(id) {
 const s = subjects[id];

 document.getElementById("lessonArea").style.display = "block";
 document.getElementById("subjectTitle").innerText = s.title;
 document.getElementById("subjectIntro").innerText = s.intro;

 const lessonBox = document.getElementById("lessons");
 lessonBox.innerHTML = "";

 s.lessons.forEach(function(lesson) {
  lessonBox.innerHTML += `
   <div class="lesson">
    <h3>${lesson.name}</h3>
    <p>${lesson.text}</p>
    <strong>Example:</strong>
    <p>${lesson.example}</p>
   </div>
  `;
 });

 document.getElementById("question").innerText = s.quiz.q;
 document.getElementById("result").innerText = "";

 const answerBox = document.getElementById("answers");
 answerBox.innerHTML = "";

 s.quiz.a.forEach(function(answer,index) {
  const button = document.createElement("button");
  button.innerText = answer;
  button.onclick = function() {
   checkAnswer(index,id);
  };
  answerBox.appendChild(button);
 });

 document.getElementById("lessonArea").scrollIntoView({
  behavior: "smooth"
 });
}

function checkAnswer(index,id) {
 const q = subjects[id].quiz;
 const result = document.getElementById("result");

 if(index === q.correct) {
  result.innerText = "🎉 Correct answer! Excellent work!";
  result.style.color = "green";
 } else {
  result.innerText = "Not quite! Try again. You can do it!";
  result.style.color = "red";
 }
}

function closeSubject() {
 document.getElementById("lessonArea").style.display = "none";
 document.getElementById("learning").scrollIntoView();
}

</script>

</body>
</html>
