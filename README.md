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
    #hint {
        margin-top: 20px;
        padding: 10px;
        background: #fff3cd;
        border: 1px solid #ffecb5;
        border-radius: 8px;
        color: #795548;
        font-weight: bold;
        display: none;
        animation: fadeIn 1s ease-in-out;
    }
    @keyframes fadeIn {
        from {o
