<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Quiz de Adestramento de Cães</title>
<style>
    body {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        background: linear-gradient(to bottom, #fff8f0, #fefefe);
        margin: 0;
        padding: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
    }
    .quiz-container {
        background: white;
        padding: 20px;
        border-radius: 16px;
        box-shadow: 0px 6px 20px rgba(0,0,0,0.15);
        max-width: 500px;
        width: 100%;
        text-align: center;
        animation: fadeIn 0.6s ease-in-out;
    }
    .quiz-header img {
        width: 100%;
        border-radius: 12px;
        margin-bottom: 15px;
    }
    h1, h2 {
        color: #333;
    }
    p {
        color: #555;
    }
    .progress-bar {
        background: #e0e0e0;
        border-radius: 20px;
        overflow: hidden;
        margin: 20px 0;
        height: 12px;
    }
    .progress {
        background: linear-gradient(90deg, #ff914d, #ffb347);
        height: 100%;
        width: 0%;
        transition: width 0.3s ease;
    }
    button, .option {
        background-color: #ff914d;
        color: white;
        border: none;
        padding: 12px 18px;
        border-radius: 10px;
        font-size: 16px;
        cursor: pointer;
        margin-top: 12px;
        width: 100%;
        transition: all 0.3s;
    }
    button:hover, .option:hover {
        background-color: #e67a32;
        transform: scale(1.03);
    }
    .option {
        display: block;
        background: #f7f7f7;
        color: #333;
        border: 1px solid #ddd;
        margin: 8px 0;
        text-align: center;
    }
    .option:hover {
        background: #ffe8d4;
        border-color: #ff914d;
        color: #222;
    }
    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(20px); }
        to { opacity: 1; transform: translateY(0); }
    }
</style>
</head>
<body>

<div class="quiz-container" id="quiz">
    <div class="quiz-header">
        <img src="https://images.unsplash.com/photo-1620331311523-d27a0c93450b?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80" alt="Cachorro fofo">
        <h1>🐾 Quiz de Adestramento de Cães</h1>
        <p>Descubra em menos de 1 minuto como melhorar o comportamento do seu cão!</p>
        <button onclick="startQuiz()">Começar Agora</button>
    </div>
</div>

<script>
const questions = [
    {
        question: "Qual o maior desafio com seu cão hoje?",
        options: ["Puxa muito a guia", "Late demais", "Não obedece comandos", "Ansiedade quando fica sozinho", "Outro"]
    },
    {
        question: "Quanto tempo por dia você dedica ao treino?",
        options: ["Menos de 10 minutos", "Entre 10 e 20 minutos", "Mais de 20 minutos", "Não treino todos os dias"]
    },
    {
        question: "Seu cão já passou por algum adestramento?",
        options: ["Nunca", "Sim, mas não funcionou", "Sim, e funcionou", "Estou treinando sozinho"]
    },
    {
        question: "Qual o porte e idade do seu cão?",
        options: ["Filhote pequeno (até 10kg)", "Filhote médio/grande", "Adulto pequeno (até 10kg)", "Adulto médio/grande", "Sênior (mais de 7 anos)"]
    },
    {
        question: "Se tivesse um método simples e comprovado para resolver o problema, começaria quando?",
        options: ["Hoje mesmo", "Essa semana", "No próximo mês", "Ainda não sei"]
    }
];

let currentQuestion = 0;
let answers = [];

function startQuiz() {
    currentQuestion = 0;
    answers = [];
    showQuestion();
}

function showQuestion() {
    const quizDiv = document.getElementById("quiz");
    const q = questions[currentQuestion];

    quizDiv.innerHTML = `
        <div class="progress-bar">
            <div class="progress" style="width:${((currentQuestion)/questions.length)*100}%"></div>
        </div>
        <h2>${q.question}</h2>
    `;
    q.options.forEach(option => {
        quizDiv.innerHTML += `<div class='option' onclick="selectOption('${option}')">${option}</div>`;
    });
}

function selectOption(option) {
    answers.push(option);
    currentQuestion++;
    if (currentQuestion < questions.length) {
        showQuestion();
    } else {
        showResult();
    }
}

function showResult() {
    const quizDiv = document.getElementById("quiz");
    quizDiv.innerHTML = `
        <div class="progress-bar">
            <div class="progress" style="width:100%"></div>
        </div>
        <h2>🐕 Seu Resultado:</h2>
        <p>Seu cão pode começar a melhorar em poucos dias com um método simples e prático, exigindo apenas alguns minutos por dia.</p>
        <p>🎯 Nosso curso online já ajudou centenas de tutores a transformar a relação com seus cães.</p>
        <a href="https://pay.kiwify.com.br/kVPazKf?afid=2ZYY0a2m" target="_blank">
            <button>🚀 Adestre já o seu cão</button>
        </a>
        <img src="https://images.unsplash.com/photo-1601979031059-3e1c77fc5d3a?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80" 
             alt="Cão feliz adestrado" style="width:100%; border-radius:12px; margin-top:20px;">
    `;
}
</script>

</body>
</html>
