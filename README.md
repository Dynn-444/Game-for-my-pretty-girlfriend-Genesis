<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Juego Romántico para Génesis</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #E8DAEF;
            color: #391848;
            text-align: center;
            padding: 20px;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            text-align: left;
        }
        .question {
            margin: 20px 0;
            padding: 20px;
            background-color: #ffcccc;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .question h2 {
            color: #391848;
        }
        .options label {
            display: block;
            margin: 10px 0;
        }
        .options button {
            background-color: #ff9999;
            border: none;
            padding: 10px 20px;
            margin-top: 10px;
            border-radius: 5px;
            cursor: pointer;
            color: #391848;
        }
        .options button:hover {
            background-color: #ff6666;
        }
        #result {
            margin-top: 20px;
            font-size: 1.2em;
        }
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Juego Romántico para Génesis</h1>

        <div class="question">
            <h2>¿Cuál es mi cumpleaños?</h2>
            <div class="options">
                <label>
                    <input type="radio" name="question1" value="7 de noviembre del 2006"> 7 de noviembre del 2006
                </label>
                <label>
                    <input type="radio" name="question1" value="7 de diciembre del 2006"> 7 de diciembre del 2006
                </label>
            </div>
            <button onclick="checkAnswer(1, '7 de noviembre del 2006'); showNextQuestion()">Comprobar Respuesta</button>
        </div>

        <div class="question hidden">
            <h2>¿Cuáles son los nombres de mis gatas?</h2>
            <div class="options">
                <label>
                    <input type="radio" name="question2" value="Luna y Zazha"> Luna y Zazha
                </label>
                <label>
                    <input type="radio" name="question2" value="Sol y Estrella"> Sol y Estrella
                </label>
            </div>
            <button onclick="checkAnswer(2, 'Luna y Zazha'); showNextQuestion()">Comprobar Respuesta</button>
        </div>

        <div class="question hidden">
            <h2>¿Qué carrera estoy estudiando?</h2>
            <div class="options">
                <label>
                    <input type="radio" name="question3" value="Comercio exterior"> Comercio exterior
                </label>
                <label>
                    <input type="radio" name="question3" value="Ingeniería informática"> Ingeniería informática
                </label>
            </div>
            <button onclick="checkAnswer(3, 'Comercio exterior'); showNextQuestion()">Comprobar Respuesta</button>
        </div>

        <div class="question hidden">
            <h2>¿Cuál es el nombre de mi mejor amiga?</h2>
            <div class="options">
                <label>
                    <input type="radio" name="question4" value="Marylinn"> Marylinn
                </label>
                <label>
                    <input type="radio" name="question4" value="Ana"> Ana
                </label>
            </div>
            <button onclick="checkAnswer(4, 'Marylinn'); showNextQuestion()">Comprobar Respuesta</button>
        </div>

        <div id="result"></div>

        <div id="specialImage" class="hidden">
            <h2>¡Lo has logrado!</h2>
            <p>Aquí tienes una imagen especial:</p>
            <img src="https://i.imgur.com/dzrcstO.jpeg" alt="Imagen especial" style="max-width: 100%; border-radius: 10px;">
        </div>
    </div>

    <script>
        function checkAnswer(question, correctOption) {
            const selectedOption = document.querySelector(`input[name="question${question}"]:checked`);
            const result = document.getElementById('result');
            if (selectedOption && selectedOption.value === correctOption) {
                result.innerHTML += `<p>Pregunta ${question}: ¡Correcto!</p>`;
                checkAllAnswers();
            } else {
                result.innerHTML += `<p>Pregunta ${question}: Incorrecto. La respuesta correcta es ${correctOption}.</p>`;
            }
        }

        function showNextQuestion() {
            const currentQuestion = document.querySelector('.question:not(.answered)');
            if (currentQuestion) {
                currentQuestion.classList.add('answered');
                const nextQuestion = currentQuestion.nextElementSibling;
                if (nextQuestion) {
                    nextQuestion.classList.remove('hidden');
                }
            }
        }

        function checkAllAnswers() {
            const allQuestions = document.querySelectorAll('.question');
            let allCorrect = true;
            allQuestions.forEach(question => {
                if (!question.classList.contains('answered')) {
                    allCorrect = false;
                }
            });

            if (allCorrect) {
                const specialImage = document.getElementById('specialImage');
                specialImage.classList.remove('hidden');
            }
        }
    </script>
</body>
</html>
