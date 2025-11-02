# Mini-jeux-b-b-
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pendu - Spécial Malo 👶</title>
<style>
    body {
        font-family: 'Arial', sans-serif;
        background: linear-gradient(to bottom, #b3e5fc, #e1f5fe);
        margin: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .container {
        background: white;
        padding: 30px;
        border-radius: 10px;
        box-shadow: 0 4px 10px rgba(0,0,0,0.3);
        width: 90%;
        max-width: 500px;
        text-align: center;
    }
    h1 {
        color: #0277bd;
    }
    #wordDisplay {
        font-size: 2em;
        letter-spacing: 10px;
        margin: 20px 0;
    }
    #lettersUsed {
        margin-top: 10px;
        font-size: 1.1em;
    }
    button {
        background: #0288d1;
        color: white;
        border: none;
        padding: 10px 20px;
        border-radius: 5px;
        cursor: pointer;
        font-size: 1em;
    }
    button:hover {
        background: #01579b;
    }
    input {
        padding: 8px;
        font-size: 1em;
        margin: 10px;
        width: 60%;
    }
    #pendu {
        font-family: monospace;
        white-space: pre;
        margin-top: 20px;
    }
    #babyResult {
        margin-top: 20px;
        background: #f1f8e9;
        padding: 15px;
        border-radius: 8px;
        display: none;
        font-size: 1.1em;
        animation: fadeIn 2s ease;
    }
    #babyResult img {
        margin-top: 15px;
        border-radius: 10px;
        width: 80%;
        max-width: 300px;
    }
    @keyframes fadeIn {
        from {opacity: 0;}
        to {opacity: 1;}
    }
</style>
</head>
<body>
<div class="container">
    <h1>🪢 Jeu du Pendu - Spécial bébé 👶</h1>

    <div id="game">
        <p>Devine le mot caché !</p>
        <div id="wordDisplay">_ _ _ _</div>
        <input type="text" id="letterInput" maxlength="1" placeholder="Lettre...">
        <button id="guessBtn">Proposer</button>
        <div id="lettersUsed"></div>
        <div id="pendu"></div>
        <div id="message"></div>

        <div id="babyResult">
            <h3>💞 Résultat 💞</h3>
            <p><strong>Prénom :</strong> Malo<br>
            <strong>Taille :</strong> 50 cm<br>
            <strong>Poids :</strong> 3,2 kilos<br>
            <strong>Né le :</strong> 23/02/2026</p>
            <img src="https://helene-douay.fr/wp-content/uploads/2020/04/b%C3%A9b%C3%A9-1-mois-photo-naturel-7.jpg" alt="Photo du bébé">
        </div>

        <button id="restartBtn" style="display:none;">Rejouer 🔁</button>
    </div>
</div>

<script>
const secretWord = "malo"; // Mot défini
let displayWord = Array(secretWord.length).fill("_");
let lettersUsed = [];
let errors = 0;
const maxErrors = 6;

const wordDisplay = document.getElementById('wordDisplay');
const letterInput = document.getElementById('letterInput');
const guessBtn = document.getElementById('guessBtn');
const lettersUsedDiv = document.getElementById('lettersUsed');
const penduDiv = document.getElementById('pendu');
const messageDiv = document.getElementById('message');
const restartBtn = document.getElementById('restartBtn');
const babyResult = document.getElementById('babyResult');

const penduStages = [
    `
    
    
      
      
    ========`,
    `
      
      |
      |
      |
    ========`,
    `
  +---+
      |
      |
      |
    ========`,
    `
  +---+
  |   |
      |
      |
    ========`,
    `
  +---+
  |   |
  O   |
      |
    ========`,
    `
  +---+
  |   |
  O   |
 /|\\  |
      |
    ========`,
    `
  +---+
  |   |
  O   |
 /|\\  |
 / \\  |
    ========`
];

guessBtn.addEventListener('click', guessLetter);
letterInput.addEventListener('keypress', e => { if(e.key === "Enter") guessLetter(); });

function guessLetter() {
    const letter = letterInput.value.toLowerCase();
    if(!letter.match(/[a-zàâçéèêëîïôûùüÿñæœ]/i)) {
        alert("Merci d’entrer une lettre valide !");
        letterInput.value = "";
        return;
    }
    if(lettersUsed.includes(letter)) {
        alert("Lettre déjà utilisée !");
        letterInput.value = "";
        return;
    }

    lettersUsed.push(letter);

    if(secretWord.includes(letter)) {
        for(let i=0;i<secretWord.length;i++){
            if(secretWord[i] === letter) displayWord[i] = letter;
        }
    } else {
        errors++;
    }

    updateDisplay();
    letterInput.value = "";

    if(!displayWord.includes("_")) {
        messageDiv.textContent = "🎉 Bravo ! Tu as trouvé MALO !";
        endGame();
    } else if(errors >= maxErrors) {
        messageDiv.textContent = "💀 Perdu ! Le mot était : MALO";
        endGame();
    }
}

function updateDisplay() {
    wordDisplay.textContent = displayWord.join(" ");
    lettersUsedDiv.textContent = "Lettres utilisées : " + lettersUsed.join(", ");
    penduDiv.textContent = penduStages[errors];
}

function endGame() {
    guessBtn.disabled = true;
    letterInput.disabled = true;
    restartBtn.style.display = "inline-block";

    // Afficher le résultat bébé après 2 secondes
    setTimeout(() => {
        babyResult.style.display = "block";
    }, 2000);
}

restartBtn.addEventListener('click', () => {
    displayWord = Array(secretWord.length).fill("_");
    lettersUsed = [];
    errors = 0;
    guessBtn.disabled = false;
    letterInput.disabled = false;
    restartBtn.style.display = "none";
    messageDiv.textContent = "";
    babyResult.style.display = "none";
    updateDisplay();
});

updateDisplay();
</script>
</body>
</html>

[googlef635895ff3dbf79d (3).html](https://github.com/user-attachments/files/23291046/googlef635895ff3dbf79d.3.html)

