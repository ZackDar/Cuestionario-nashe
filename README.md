<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cuestionario nashe</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background-color: #f4f4f4;
    }
    .quiz-container {
      max-width: 600px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    .question {
      font-weight: bold;
      margin-top: 20px;
    }
    .options {
      margin: 10px 0;
    }
    .options label {
      display: block;
      margin-bottom: 8px;
      cursor: pointer;
    }
    button {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 16px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    .result {
      margin-top: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="quiz-container">
    <h2>Cuestionario de prueba</h2>

    <div id="quiz"></div>

    <button onclick="submitQuiz()">Enviar</button>

    <div class="result" id="result"></div>
  </div>

  <script>
    // Cuestionario nashe
    const questions = [
      {
        question: "¿Quien fue el ministro de la propaganda del regimen nazi?",
        options: ["Hermann Göring", "Joseph Goebbels", "Heinrich Himmler", " Albert Speer"],
        answer: 1
      },
      {
        question: "¿Qué fue el nazismo?",
        options: ["Un movimiento socialista democrático", "Un régimen comunista", "Una ideología ultranacionalista, racista y totalitaria", "Un sistema monárquico liberal"],
        answer: 2
      },
      {
        question: "¿Cuando se  firmo el tratado de versalles?",
        options: ["1919", "1945", "1929", "1939"],
        answer: 0
      },
      {
        question: "¿Bauty es un gordo puto?",
        options: ["si", "obvio", "reeee", "si encima alto gay"],
        answer: 3
      },
      {
        question: "¿Quién escribió 'Cien años de soledad'?",
        options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Julio Cortázar", "Pablo Neruda"],
        answer: 1
      }
    ];

    const quizContainer = document.getElementById("quiz");

    function loadQuiz() {
      questions.forEach((q, index) => {
        const questionDiv = document.createElement("div");

        questionDiv.innerHTML = `
          <div class="question">${index + 1}. ${q.question}</div>
          <div class="options">
            ${q.options.map((opt, i) => `
              <label>
                <input type="radio" name="question${index}" value="${i}">
                ${opt}
              </label>
            `).join("")}
          </div>
        `;

        quizContainer.appendChild(questionDiv);
      });
    }

    function submitQuiz() {
      let score = 0;

      questions.forEach((q, index) => {
        const selected = document.querySelector(`input[name="question${index}"]:checked`);
        if (selected && parseInt(selected.value) === q.answer) {
          score++;
        }
      });

      const resultDiv = document.getElementById("result");
      resultDiv.textContent = `Obtuviste ${score} de ${questions.length} respuestas correctas.`;
    }

    loadQuiz();
  </script>
</body>
</html>
