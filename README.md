
<!-- intelligence-quiz/index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Discover Your Intelligence Type</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <div class="container">
    <h1>Discover Your Intelligence Type</h1>
    <p>Take this quiz to learn which type of intelligence is strongest in you.</p>
    <a href="quiz.html" class="start-button">Start Quiz</a>
  </div>
</body>
</html>

<!-- intelligence-quiz/quiz.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Multiple Intelligences Quiz</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <div class="container">
    <h1>Multiple Intelligences Quiz</h1>
    <form id="quiz-form"></form>
    <button id="submit-btn">See My Results</button>
  </div>
  <script src="quiz.js"></script>
</body>
</html>

<!-- intelligence-quiz/results.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Your Results</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <div class="container">
    <h1>Your Intelligence Results</h1>
    <div id="results-display"></div>
    <a href="index.html" class="restart-button">Retake Quiz</a>
  </div>
  <script src="results.js"></script>
</body>
</html>

/* intelligence-quiz/styles.css */
body {
  font-family: Arial, sans-serif;
  background: #f0f4f8;
  color: #333;
  margin: 0;
  padding: 0;
}
.container {
  max-width: 700px;
  margin: 50px auto;
  padding: 20px;
  background: #fff;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
}
h1 {
  text-align: center;
  color: #222;
}
button, .start-button, .restart-button {
  display: block;
  margin: 20px auto;
  padding: 12px 20px;
  background: #0077cc;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  text-decoration: none;
  text-align: center;
}
button:hover, .start-button:hover, .restart-button:hover {
  background: #005fa3;
}

/* intelligence-quiz/quiz.js */
const questions = {
  Linguistic: [
    "I enjoy writing stories, poems, or journaling.",
    "I’m good at explaining things clearly and effectively.",
    "I love reading books and expanding my vocabulary.",
    "I often find myself playing with words or making puns.",
    "I remember what I read or hear better than what I see.",
    "I do well in language arts or English classes."
  ],
  "Logical-Mathematical": [
    "I enjoy solving puzzles and logical problems.",
    "I excel at math and science subjects.",
    "I like to analyze situations and find patterns.",
    "I question how things work and why.",
    "I often find myself organizing or categorizing things.",
    "I can do calculations in my head easily."
  ],
  Spatial: [
    "I enjoy drawing, painting, or designing.",
    "I can easily visualize how things look in my mind.",
    "I like working with maps, charts, or diagrams.",
    "I enjoy building with blocks, Legos, or modeling kits.",
    "I have a strong sense of direction.",
    "I often think in images rather than words."
  ],
  Musical: [
    "I frequently listen to or think about music.",
    "I can pick up rhythms or beats quickly.",
    "I enjoy singing, playing an instrument, or composing music.",
    "I remember melodies and lyrics easily.",
    "I notice when music is off-key or out of rhythm.",
    "I’m sensitive to sounds in my environment."
  ],
  "Bodily-Kinesthetic": [
    "I learn best through hands-on activities.",
    "I’m good at sports, dancing, or physical coordination.",
    "I enjoy moving around rather than sitting still.",
    "I express myself through body language or gestures.",
    "I often tap my foot or fidget when I think.",
    "I use my hands when talking or explaining things."
  ],
  Interpersonal: [
    "I enjoy group activities and social interactions.",
    "I can sense how others are feeling.",
    "I often mediate conflicts between friends.",
    "I prefer to work with others rather than alone.",
    "I am a good listener and communicator.",
    "I enjoy teaching or helping others learn."
  ],
  Intrapersonal: [
    "I spend time thinking about my thoughts and emotions.",
    "I set personal goals and reflect on my progress.",
    "I understand what motivates me.",
    "I am comfortable being alone and working independently.",
    "I know my strengths and weaknesses.",
    "I often think about the meaning of life and who I am."
  ],
  Naturalistic: [
    "I enjoy being outdoors and observing nature.",
    "I’m interested in animals, plants, and the environment.",
    "I notice patterns and changes in the weather or seasons.",
    "I care deeply about the Earth and sustainability.",
    "I like categorizing or collecting things in nature.",
    "I’m drawn to careers involving biology or conservation."
  ]
};

const form = document.getElementById("quiz-form");
let qIndex = 0;

for (const [type, items] of Object.entries(questions)) {
  const header = document.createElement("h2");
  header.textContent = `${type} Intelligence`;
  form.appendChild(header);

  items.forEach((q, i) => {
    const div = document.createElement("div");
    div.innerHTML = `
      <label>${q}</label><br/>
      <select name="${type}" required>
        <option value="">Choose</option>
        <option value="1">1 - Strongly Disagree</option>
        <option value="2">2 - Disagree</option>
        <option value="3">3 - Neutral</option>
        <option value="4">4 - Agree</option>
        <option value="5">5 - Strongly Agree</option>
      </select>
    `;
    form.appendChild(div);
  });
}

document.getElementById("submit-btn").addEventListener("click", function () {
  const results = {};
  const selects = document.querySelectorAll("form select");

  selects.forEach((select) => {
    const type = select.name;
    const score = parseInt(select.value);
    if (!results[type]) results[type] = 0;
    results[type] += score;
  });

  localStorage.setItem("quizResults", JSON.stringify(results));
  window.location.href = "results.html";
});

/* intelligence-quiz/results.js */
const display = document.getElementById("results-display");
const results = JSON.parse(localStorage.getItem("quizResults"));

if (results) {
  let sorted = Object.entries(results).sort((a, b) => b[1] - a[1]);
  const [topType, topScore] = sorted[0];
  display.innerHTML = `<h2>Your Dominant Intelligence: ${topType}</h2><p>Score: ${topScore}</p>`;

  sorted.slice(1).forEach(([type, score]) => {
    const p = document.createElement("p");
    p.textContent = `${type}: ${score}`;
    display.appendChild(p);
  });
} else {
  display.innerHTML = "<p>No results found. Please take the quiz first.</p>";
}
