<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Auxiliar de Estudos</title>
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 24 24%22 fill=%22none%22 stroke=%22currentColor%22 stroke-width=%222%22 stroke-linecap=%22round%22 stroke-linejoin=%22round%22 class=%22feather feather-book-open%22><path d=%22M2 2h10v20H2zM22 2h-10v20h10z%22/></svg>">
    <style>
        body {
            background-color: #f4f4f4;
            color: #333;
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow-y: scroll;
        }
        .container {
            width: 90%;
            max-width: 1200px;
            margin: auto;
            padding-top: 20px;
        }
        .header {
            text-align: center;
            margin-bottom: 20px;
        }
        .search-bar {
            margin-bottom: 20px;
            text-align: center;
        }
        .search-bar input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }
        .categories {
            margin-bottom: 20px;
            text-align: center;
        }
        .categories button {
            padding: 10px 15px;
            margin-bottom: 10px;
            border: none;
            border-radius: 5px;
            background-color: #1E90FF;
            color: white;
            font-size: 16px;
            cursor: pointer;
        }
        .categories button:hover {
            background-color: #1C7ECD;
        }
        .resource-list {
            list-style-type: none;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .resource-item {
            width: 100%;
            margin: 10px 0;
            padding: 10px;
            background-color: #fff;
            border: 1px solid #ddd;
            border-radius: 5px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        .resource-item a {
            color: #1E90FF;
            text-decoration: none;
            font-size: 18px;
            display: block;
            margin-bottom: 10px;
        }
        .resource-item a:hover {
            text-decoration: underline;
        }
        .resource-item p {
            margin: 0;
        }

        @media (min-width: 768px) {
            .resource-list {
                flex-direction: row;
                flex-wrap: wrap;
                justify-content: space-around;
            }
            .resource-item {
                width: 45%;
            }
        }

        @media (min-width: 1200px) {
            .resource-item {
                width: 30%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>Auxiliar de Estudos</h1>
            <p>Encontre materiais de estudo para melhorar seu aprendizado</p>
        </div>
        <div class="search-bar">
            <input type="text" id="searchInput" placeholder="Buscar recursos...">
        </div>
        <div class="categories">
            <button onclick="filterCategory('todos')">Todos</button>
            <button onclick="filterCategory('videos')">Vídeos</button>
            <button onclick="filterCategory('artigos')">Artigos</button>
            <button onclick="filterCategory('livros')">Livros</button>
            <button onclick="filterCategory('exercicios')">Exercícios</button>
        </div>
        <ul class="resource-list" id="resourceList">
            <li class="resource-item" data-category="videos">
                <a href="https://example.com/video1" target="_blank">Vídeo 1</a>
                <p>Descrição do Vídeo 1</p>
            </li>
            <li class="resource-item" data-category="artigos">
                <a href="https://example.com/artigo1" target="_blank">Artigo 1</a>
                <p>Descrição do Artigo 1</p>
            </li>
            <li class="resource-item" data-category="livros">
                <a href="https://example.com/livro1" target="_blank">Livro 1</a>
                <p>Descrição do Livro 1</p>
            </li>
            <li class="resource-item" data-category="exercicios">
                <a href="https://example.com/exercicio1" target="_blank">Exercício 1</a>
                <p>Descrição do Exercício 1</p>
            </li>
        </ul>
    </div>
    <script>
        const searchInput = document.getElementById('searchInput');
        const resourceList = document.getElementById('resourceList');
        searchInput.addEventListener('keyup', function() {
            const filter = searchInput.value.toLowerCase();
            const resources = resourceList.getElementsByTagName('li');
            for (let i = 0; i < resources.length; i++) {
                const a = resources[i].getElementsByTagName('a')[0];
                if (a.innerHTML.toLowerCase().indexOf(filter) > -1) {
                    resources[i].style.display = '';
                } else {
                    resources[i].style.display = 'none';
                }
            }
        });

        function filterCategory(category) {
            const resources = resourceList.getElementsByTagName('li');
            for (let i = 0; i < resources.length; i++) {
                const resourceCategory = resources[i].dataset.category;
                if (resourceCategory === category || category === 'todos') {
                    resources[i].style.display = '';
                } else {
                    resources[i].style.display = 'none';
                }
            }
        }
    </script>
</body>
</html>
