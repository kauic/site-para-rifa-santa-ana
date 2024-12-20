<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Marcação de Pontos</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Marcação de Pontos</h1>
        <form id="pointForm">
            <label for="name">Nome do Marcador:</label>
            <input type="text" id="name" required placeholder="Digite o nome do marcador">
            
            <label for="points">Pontuação (1 a 300):</label>
            <input type="number" id="points" required min="1" max="300" placeholder="Digite a pontuação">
            
            <button type="submit">Registrar Pontuação</button>
        </form>

        <h2>Lista de Pontuações</h2>
        <ul id="scoreList"></ul>
    </div>
    <script src="scripts.js"></script>
</body>
</html>
/* Estilização básica */
body {
    font-family: Arial, sans-serif;
    background-color: #f8f9fa;
    margin: 0;
    padding: 0;
}

.container {
    max-width: 600px;
    margin: 50px auto;
    padding: 20px;
    background: #ffffff;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

h1, h2 {
    text-align: center;
    color: #333;
}

form {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

input, button {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 16px;
}

button {
    background-color: #28a745;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: bold;
}

button:hover {
    background-color: #218838;
}

#scoreList {
    list-style: none;
    padding: 0;
    margin-top: 20px;
}

#scoreList li {
    padding: 10px;
    margin: 10px 0;
    background-color: #e9ecef;
    border-radius: 5px;
}
// Captura o formulário e a lista
const form = document.getElementById('pointForm');
const scoreList = document.getElementById('scoreList');

// Lida com o envio do formulário
form.addEventListener('submit', function(event) {
    event.preventDefault();

    const name = document.getElementById('name').value.trim();
    const points = parseInt(document.getElementById('points').value);

    // Valida os dados
    if (!name || isNaN(points) || points < 1 || points > 300) {
        alert('Por favor, insira um nome válido e uma pontuação entre 1 e 300.');
        return;
    }

    // Adiciona um novo item na lista
    const listItem = document.createElement('li');
    listItem.textContent = `${name}: ${points} pontos`;
    scoreList.appendChild(listItem);

    // Limpa o formulário
    form.reset();
});
