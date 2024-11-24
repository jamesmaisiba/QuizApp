let currentQuestionIndex = 0;
let score = 0;
const questions = [
    {
        question: "What is the capital of France?",
        options: {
            A: "Berlin",
            B: "Madrid",
            C: "Paris",
            D: "Lisbon"
        },
        correctAnswer: "C"
    },
    {
        question: "Which programming language is known as the language of the web?",
        options: {
            A: "Java",
            B: "Python",
            C: "JavaScript",
            D: "C++"
        },
        correctAnswer: "C"
    },
    {
        question: "What is 5 + 3?",
        options: {
            A: "5",
            B: "8",
            C: "7",
            D: "9"
        },
        correctAnswer: "B"
    }
];

function loadQuestion() {
    const question = questions[currentQuestionIndex];
    document.getElementById('question').innerText = question.question;
    document.getElementById('score').innerText = `Score: ${score}`;
    
    const options = question.options;
    document.querySelectorAll('.answer-btn').forEach((btn, index) => {
        const optionKey = String.fromCharCode(65 + index); // A, B, C, D
        btn.innerText = options[optionKey];
        btn.setAttribute('data-answer', optionKey);
    });
}

function checkAnswer(selectedAnswer) {
    const correctAnswer = questions[currentQuestionIndex].correctAnswer;
    if (selectedAnswer === correctAnswer) {
        score++;
    }
    document.getElementById('score').innerText = `Score: ${score}`;
    document.getElementById('next-btn').style.display = 'block';
}

function nextQuestion() {
    currentQuestionIndex++;
    
    if (currentQuestionIndex < questions.length) {
        loadQuestion();
        document.getElementById('next-btn').style.display = 'none';
    } else {
        alert(`Quiz completed! Your final score is: ${score}`);
    }
}

// Initialize the quiz
window.onload = loadQuestion;
