# Learnyourintelligencetype.github.io
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
    <form id="quiz-form">
      <!-- Questions injected via JavaScript -->
    </form>
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
