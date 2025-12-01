<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Novidades do Mundo dos Videogames</title>
    <!-- Meta Tags Open Graph para Facebook e outras redes sociais (ADICIONADAS AQUI) -->
    <!-- LEMBRE-SE DE SUBSTITUIR [SEU_URL_PUBLICO] PELO LINK REAL DEPOIS DA HOSPEDAGEM -->
    <meta property="og:title" content="Central de Notícias de Jogos | Últimas Novidades" />
    <meta property="og:description" content="Mantenha-se atualizado com os maiores lançamentos e notícias da indústria de videogames, com análises geradas por IA." />
    <meta property="og:type" content="website" />
    <meta property="og:url" content="[SEU_URL_PUBLICO]" /> 
    <meta property="og:image" content="https://placehold.co/1200x630/0d1117/ffffff?text=Central+de+Noticias+de+Jogos" />
    <meta property="og:image:width" content="1200" />
    <meta property="og:image:height" content="630" />
    
    <!-- Carrega o Tailwind CSS para estilização moderna e responsiva -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet">
    <style>
        /* Estilos base EGS-inspired */
        body {
            font-family: 'Inter', sans-serif;
            /* Fundo escuro, quase preto (Dark Slate) */
            background-color: #0d1117; 
            min-height: 100vh;
        }
        
        /* Contêiner principal com cor de superfície de loja */
        .store-container {
            background-color: #161b22; 
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
        }

        /* Estilo para preservar formatação do LLM no resumo da notícia */
        .llm-output {
             white-space: pre-wrap;
             color: #c9d1d9; /* Cor de texto mais clara */
             font-size: 1rem;
        }
        
        /* Estilos dos Botões de Tópico */
        .topic-button {
            @apply bg-gray-700 text-gray-100 font-medium py-2 px-4 rounded-full shadow-lg transition duration-200 hover:bg-red-600 hover:text-white hover:shadow-red-500/50 text-sm md:text-base;
        }
        .sub-topic-button {
            @apply bg-gray-600 text-gray-200 font-medium py-2 px-4 rounded-lg transition duration-200 hover:bg-red-500 hover:text-white;
        }

        /* Card de Jogo na secção de Lançamentos (Mantido, mas sobrescrito abaixo) */
        .game-card {
            @apply p-0 overflow-hidden rounded-xl border border-gray-700 bg-gray-800 transition duration-300 transform hover:scale-[1.03] hover:shadow-2xl hover:shadow-red-500/20 cursor-pointer;
        }

        /* Placeholder de imagem para cards menores (Mantido) */
        .card-image-placeholder {
             /* Cor de fundo escura */
            background-color: #1e293b; 
            min-height: 100px;
        }
        
        /* Adiciona estilo para truncar texto com fallback no JS */
        .line-clamp-2 {
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;  
            overflow: hidden;
        }
        
        /* === ESTILOS STEAM-INSPIRED (SOBRESCRITA PARA A SECÇÃO DE LANÇAMENTOS) === */
        .steam-release-list {
            background-color: #1e3040; /* Fundo azul escuro para a lista, mais próximo do Steam */
        }

        .steam-release-item {
            /* Fundo do card: Azul-cinzento escuro típico da Steam */
            @apply flex flex-col md:flex-row p-3 rounded-lg border-b border-[#314a5d] bg-[#2a475e] transition duration-300 transform hover:scale-[1.005] hover:bg-[#385b7c] cursor-pointer shadow-lg;
            min-height: 100px;
            margin-bottom: 0.5rem; /* Espaçamento entre itens */
        }

        .steam-image-placeholder-container {
             /* Simula o tamanho do banner Steam 460x215 */
            width: 100%;
            height: 100%;
            max-width: 150px; /* Largura fixa para a imagem na lista */
            background-color: #1e293b; 
            min-height: 80px;
            @apply rounded-md border border-gray-600;
        }
        .steam-title {
            color: #66c0f4; /* Azul Steam */
            @apply font-semibold;
        }
        .steam-date {
            color: #c7d5e0; /* Cinza claro */
            @apply text-sm;
        }
    </style>
</head>
<body class="p-4 md:p-8">

    <!-- Chosen Palette: Dark Slate / Red Accent -->
    <!-- Application Structure Plan: Dashboard Layout with Thematic Sections. Structure: 1. Header/Search (for user-driven queries). 2. Topic Filters (pre-set, quick access). 3. Featured Card (Detailed AI Summary/Grounding). 4. Releases Grid (Interactive list for drill-down). This structure is chosen because it mimics a modern game store/news portal (high usability) and prioritizes the most important content (the AI-summarized news) while providing clear paths for exploration (filters, detail view). User flow: Search/Filter -> Read Featured Summary -> Click Game in Grid/Summary -> View Detailed Analysis -> Justification: High-density information synthesis best conveyed as stylized text. Releases Grid -> Goal: Organize/Compare -> Viz: Grid of Card Components (HTML/CSS) -> Interaction: Click card to trigger Detail View query -> Justification: Standard, familiar UI pattern for displaying products/upcoming items, easy to scan. Detailed Analysis -> Goal: Explain/Detail -> Viz: Text + Placeholder Image -> Interaction: Back button -> Justification: Provides deep-dive context necessary for a 'report' translation. All uses Chart.js/Plotly.js and NO SVG/Mermaid. -->
    <!-- Visualization & Content Choices: Featured News -> Goal: Inform/Synthesize -> Viz: Large Text Block with Call-to-Action Links (AI-generated text with clickable game titles) -> Interaction: Clickable game titles link to Detail View -> Justification: High-density information synthesis best conveyed as stylized text. Releases Grid -> Goal: Organize/Compare -> Viz: Grid of Card Components (HTML/CSS) -> Interaction: Click card to trigger Detail View query -> Justification: Standard, familiar UI pattern for displaying products/upcoming items, easy to scan. Detailed Analysis -> Goal: Explain/Detail -> Viz: Text + Placeholder Image -> Interaction: Back button -> Justification: Provides deep-dive context necessary for a 'report' translation. All uses Chart.js/Plotly.js and NO SVG/Mermaid. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->

    <div class="max-w-6xl mx-auto store-container rounded-xl p-6 md:p-10 border border-gray-700">

        <!-- CONTAINER PRINCIPAL (Main View) -->
        <div id="mainView">
            
            <!-- CABEÇALHO E FERRAMENTAS DE BUSCA (Mantido no estilo EGS/Dark) -->
            <header class="text-center mb-10">
                <h1 class="text-4xl md:text-5xl font-extrabold text-white mb-4">
                     CENTRAL DE <span class="text-red-500">NOTÍCIAS</span> DE JOGOS
                </h1>
                <p class="text-gray-400 text-lg mb-6">
                    Mantenha-se atualizado com os maiores lançamentos e notícias da indústria.
                </p>

                <!-- Formulário de Consulta -->
                <div class="space-y-4 max-w-2xl mx-auto">
                    <input
                        type="text"
                        id="queryInput"
                        placeholder="Ex: Últimas notícias do PlayStation 5"
                        value="Novidades e lançamentos de jogos mais importantes do momento"
                        class="w-full px-5 py-3 border border-gray-600 bg-gray-800 text-white rounded-lg focus:ring-red-500 focus:border-red-500 shadow-inner transition duration-150"
                    />
                    <button
                        id="searchButton"
                        onclick="fetchGameNews()"
                        class="w-full bg-red-600 hover:bg-red-700 text-white font-bold py-3 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-[1.005] focus:outline-none focus:ring-4 focus:ring-red-500/50 flex items-center justify-center disabled:opacity-50"
                    >
                        Buscar Novidades
                        <svg id="searchIcon" class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
                        <svg id="loadingSpinner" class="w-5 h-5 ml-2 animate-spin text-white hidden" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                            <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                            <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                        </svg>
                    </button>
                </div>
            </header>

            <!-- Tópicos do Momento (Horizontal) -->
            <div class="mb-12">
                <h2 class="text-2xl font-bold text-gray-200 mb-4 border-b border-gray-700 pb-2">🎮 Tópicos em Destaque</h2>
                <div class="flex flex-wrap gap-4 justify-center md:justify-start">
                    <button onclick="setQueryAndFetch('Últimas notícias de PC Gaming')" class="topic-button">💻 PC Gaming</button>
                    <button onclick="toggleConsoleSubMenu()" class="topic-button" id="consolasButton">🕹️ Consolas</button>
                    <button onclick="setQueryAndFetch('Novidades sobre jogos Indie e seus criadores')" class="topic-button">🌟 Jogos Indie</button>
                    <button onclick="setQueryAndFetch('Resultados e notícias de Esports e torneios')" class="topic-button">🏆 Esports</button>
                </div>
                
                <!-- Submenu de Consolas (Vertical/Flexível) -->
                <div id="consoleSubMenu" class="hidden mt-4 pt-4 border-t border-gray-700 mx-auto max-w-3xl">
                    <p class="text-gray-400 mb-3 text-center text-sm">ESCOLHA UMA PLATAFORMA POPULAR:</p>
                    <div class="flex flex-wrap justify-center gap-3">
                        <button onclick="setQueryAndFetch('Últimas notícias da PlayStation 5')" class="sub-topic-button">PlayStation 5</button>
                        <button onclick="setQueryAndFetch('Últimas notícias da Xbox Series X|S')" class="sub-topic-button">Xbox Series X|S</button>
                        <button onclick="setQueryAndFetch('Últimas notícias da Nintendo Switch')" class="sub-topic-button">Nintendo Switch</button>
                        <button onclick="setQueryAndFetch('Últimas notícias da Steam Deck')" class="sub-topic-button">Steam Deck</button>
                    </div>
                </div>
            </div>
            

            <!-- SECÇÃO DE DESTAQUE (Resumo da Notícia Principal - Mantido no estilo EGS/Dark) -->
            <section class="mb-12">
                <h2 class="text-2xl font-bold text-gray-200 mb-4 border-b border-gray-700 pb-2">📰 Notícia Principal & Destaque</h2>
                
                <!-- CARD DE DESTAQUE GRANDE - Fundo Preto total -->
                <div id="results" class="bg-black rounded-xl overflow-hidden shadow-xl border border-gray-700 transition duration-300 hover:shadow-red-500/30">
                    <div id="featuredCardContent" class="min-h-[300px] flex items-center justify-center text-center p-8">
                        <!-- MENSAGEM DE CARREGAMENTO ATUALIZADA AQUI -->
                        <p id="initialMessage" class="text-gray-400 text-lg">Como repórter de videojogos, apresento o resumo das novidades e dos lançamentos mais importantes que marcam o momento no universo dos jogos eletrónicos.</p>
                    </div>
                </div>
                
                <!-- Fonte e Citações para Destaque -->
                <div id="sourcesContainer" class="mt-4 p-4 bg-gray-800 rounded-lg border border-gray-700 hidden">
                    <h3 class="text-lg font-medium text-gray-300 mb-2">Outras Fontes Consultadas:</h3>
                    <ul id="sourcesList" class="space-y-1 text-sm text-gray-400 pl-4 list-disc">
                        <!-- As citações serão inseridas aqui -->
                    </ul>
                </div>
            </section>
            
            <!-- SECÇÃO DE PRÓXIMOS LANÇAMENTOS (GRID DE LISTA - STEAM INSPIRED) -->
            <section class="mb-12">
                <h2 class="text-2xl font-bold text-gray-200 mb-4 border-b border-gray-700 pb-2">📅 Próximos Lançamentos (Top 10)</h2>
                
                <!-- Container da Grid de Lançamentos - Agora usando o estilo de fundo Steam -->
                <div id="releasesContainer" class="steam-release-list grid grid-cols-1 gap-4 p-4 rounded-xl min-h-[150px] items-center justify-center">
                    <p id="releasesMessage" class="col-span-full text-gray-400 text-center">A carregar a lista de lançamentos...</p>
                </div>
            </section>

            <!-- Área de Erro (Oculta por padrão) -->
            <div id="errorContainer" class="mt-8 p-4 bg-red-800 border border-red-600 text-red-200 rounded-lg hidden" role="alert">
                <p class="font-bold">Erro na Busca</p>
                <p id="errorMessage"></p>
            </div>
        </div>
        
        <!-- CONTAINER DE DETALHES DO JOGO (Detail View - Tela de Produto) -->
        <div id="detailView" class="hidden">
            <button onclick="switchView('mainView')" class="mb-8 flex items-center bg-gray-700 hover:bg-gray-600 text-white font-bold py-2 px-4 rounded-lg transition duration-200 shadow-md">
                <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18"></path></svg>
                Voltar para Loja
            </button>
            
            <!-- Detalhes do Jogo -->
            <div class="space-y-8"> 
                <h2 id="gameDetailTitle" class="text-4xl font-extrabold text-white mb-4"></h2>
                
                <!-- Coluna Principal: Imagem e Conteúdo Detalhado -->
                <div class="lg:grid lg:grid-cols-3 lg:gap-8">
                    <!-- Coluna 1 (2/3): Imagem e Resumo Extenso -->
                    <div class="lg:col-span-2">
                        <!-- Container da Imagem com Placeholder SVG (robusto) -->
                        <div id="gameDetailImageContainer" class="w-full mb-6">
                            <!-- Imagem e loading overlay serão inseridos aqui pelo JS -->
                        </div>
                        
                        <!-- Conteúdo do jogo (Story, Gameplay) -->
                        <div id="gameDetailContent" class="p-0 text-gray-300 leading-relaxed min-h-[100px] flex items-center justify-center">
                            <!-- Conteúdo do jogo e loading spinner aqui -->
                        </div>
                    </div>

                    <!-- Coluna 2 (1/3): Deixada vazia aqui, a informação resumida será movida para baixo -->
                    <div class="lg:col-span-1 hidden lg:block">
                        <!-- Espaço intencionalmente vazio para manter o layout no desktop, mas a informação resumida foi movida para a secção de baixo -->
                    </div>
                </div>

                <!-- NOVO LOCAL DA INFORMAÇÃO RESUMIDA (Largura Total abaixo do Conteúdo Principal) -->
                <div class="mt-8 p-6 bg-gray-800 rounded-xl border border-gray-700 shadow-lg">
                    <h3 class="text-xl font-semibold text-gray-200 mb-4 border-b border-gray-700 pb-2">Informação Resumida</h3>
                    
                    <!-- Conteúdo do jogo (Story, Gameplay) -->
                    <div id="gameDetailContentSummary" class="p-0 text-gray-300 leading-relaxed min-h-[100px] flex items-center justify-center">
                        <!-- O conteúdo detalhado resumido será injetado aqui pelo JS -->
                        <p class="text-gray-400 p-6">A carregar detalhes do jogo...</p>
                    </div>
                </div>
            </div>
            
            <!-- Fonte e Citações para Detalhes (Rodapé) -->
            <div id="detailSourcesContainer" class="mt-10 p-4 bg-gray-800 border border-gray-700 rounded-lg hidden">
                <h3 class="text-lg font-medium text-gray-300 mb-2">Fontes Consultadas:</h3>
                <ul id="detailSourcesList" class="space-y-1 text-sm text-gray-400 pl-4 list-disc">
                    <!-- As citações serão inseridas aqui -->
                </div>
            </div>
        </div>
    </div>

    <script>
        // Configurações e Funções do App

        // Variável global para armazenar a chave da API. É deixada vazia para ser preenchida automaticamente.
        const apiKey = ""; 
        
        // O URL da API de Geração de Conteúdo do Gemini com o modelo que suporta grounding (pesquisa).
        const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;

        // Elementos DOM
        const searchButton = document.getElementById('searchButton');
        const queryInput = document.getElementById('queryInput');
        const resultsDiv = document.getElementById('results');
        const initialMessage = document.getElementById('initialMessage');
        const sourcesContainer = document.getElementById('sourcesContainer');
        const sourcesList = document.getElementById('sourcesList');
        const errorContainer = document.getElementById('errorContainer');
        const errorMessage = document.getElementById('errorMessage');
        const loadingSpinner = document.getElementById('loadingSpinner');
        const searchIcon = document.getElementById('searchIcon');
        
        // Elementos para Lançamentos e Views
        const releasesContainer = document.getElementById('releasesContainer');
        const mainView = document.getElementById('mainView');
        const detailView = document.getElementById('detailView');
        const gameDetailTitle = document.getElementById('gameDetailTitle');
        const gameDetailImageContainer = document.getElementById('gameDetailImageContainer');
        const featuredCardContent = document.getElementById('featuredCardContent'); // Novo para o resumo principal
        
        // ELEMENTOS ATUALIZADOS PARA A NOVA ESTRUTURA DE DETALHES
        const gameDetailContent = document.getElementById('gameDetailContent'); // Conteúdo Principal (História/Gameplay)
        const gameDetailContentSummary = document.getElementById('gameDetailContentSummary'); // Conteúdo Resumido (Novo Bloco)
        
        const detailSourcesContainer = document.getElementById('detailSourcesContainer');
        const detailSourcesList = document.getElementById('detailSourcesList');
        
        // Elementos para Tópicos
        const consolasButton = document.getElementById('consolasButton');
        const consoleSubMenu = document.getElementById('consoleSubMenu');

        /**
         * Gera um URL de imagem SVG (placeholder) em linha (Data URI) que é garantido de carregar.
         * @param {string} gameName - O nome do jogo.
         * @returns {string} O Data URI do placeholder SVG.
         */
        function getSvgPlaceholder(gameName) {
            // Limpa e formata o texto para o SVG
            const safeGameName = gameName.toUpperCase().substring(0, 20); // Limita o tamanho
            const text1 = safeGameName;
            const text2 = "ARTE PROMOCIONAL - CARREGANDO DETALHES";
            
            // Define cores (EGS inspired)
            const bgColor = '#1e293b'; 
            const fgColor = '#fca5a5'; // Rosa/Vermelho claro
            const strokeColor = '#4b5563'; 

            const svgContent = `
                <svg width="100%" height="100%" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 338">
                    <rect width="600" height="338" fill="${bgColor}"/>
                    
                    <!-- Borda tracejada para simular um frame -->
                    <rect x="20" y="20" width="560" height="298" stroke="${strokeColor}" stroke-dasharray="8,8" fill="none" stroke-width="2"/>
                    
                    <!-- Texto Principal (Nome do Jogo) -->
                    <text x="300" y="150" font-family="Inter, sans-serif" font-size="36" fill="${fgColor}" text-anchor="middle" alignment-baseline="middle" font-weight="bold">
                        ${text1}
                    </text>
                    
                    <!-- Texto Secundário (Status/Instrução) -->
                    <text x="300" y="195" font-family="Inter, sans-serif" font-size="16" fill="${fgColor}" text-anchor="middle" alignment-baseline="middle">
                        ${text2}
                    </text>
                </svg>
            `.trim().replace(/\s+/g, ' ').replace(/"/g, "'"); // Minifica e substitui aspas para o Data URI

            // Constrói o Data URI
            return `data:image/svg+xml;charset=UTF-8,${encodeURIComponent(svgContent)}`;
        }

        /**
         * Alterna entre a visualização principal e a visualização de detalhes.
         * @param {string} viewId - 'mainView' ou 'detailView'.
         */
        function switchView(viewId) {
            if (viewId === 'mainView') {
                mainView.classList.remove('hidden');
                detailView.classList.add('hidden');
            } else if (viewId === 'detailView') {
                mainView.classList.add('hidden');
                detailView.classList.remove('hidden');
                
                // Limpa o conteúdo de detalhes ao trocar para garantir o estado de carregamento
                gameDetailTitle.textContent = '';
                gameDetailImageContainer.innerHTML = ''; // Limpa o container da imagem
                
                // Limpa e configura spinners para os dois blocos de texto
                gameDetailContent.innerHTML = '<p class="text-gray-400 p-6">A carregar detalhes do jogo...</p>';
                gameDetailContent.classList.add('flex', 'items-center', 'justify-center');
                
                gameDetailContentSummary.innerHTML = '<p class="text-gray-400 p-6">A carregar detalhes do jogo...</p>';
                gameDetailContentSummary.classList.add('flex', 'items-center', 'justify-center');

                detailSourcesContainer.classList.add('hidden');
                detailSourcesList.innerHTML = '';
            }
        }


        /**
         * Realiza chamadas à API com backoff exponencial para lidar com limites de taxa.
         * @param {string} url - O URL da API.
         * @param {object} options - Opções de fetch (método, headers, body).
         * @param {number} retries - Número de tentativas restantes.
         * @returns {Promise<Response>} A resposta do fetch.
         */
        async function fetchWithBackoff(url, options, retries = 5) {
            for (let i = 0; i < retries; i++) {
                try {
                    const response = await fetch(url, options);
                    if (response.ok) {
                        return response;
                    }
                    if (response.status === 429 && i < retries - 1) { // 429 Too Many Requests
                        const delay = Math.pow(2, i) * 1000 + Math.random() * 1000;
                        console.log(`Tentativa ${i + 1} falhou (Status ${response.status}). A tentar novamente em ${delay / 1000}s...`);
                        await new Promise(resolve => setTimeout(resolve, delay));
                        continue;
                    }
                    throw new Error(`API Error: ${response.status} ${response.statusText}`);
                } catch (error) {
                    if (i === retries - 1) {
                        throw error;
                    }
                    const delay = Math.pow(2, i) * 1000 + Math.random() * 1000;
                    console.log(`Tentativa ${i + 1} falhou (${error.message}). A tentar novamente em ${delay / 1000}s...`);
                    await new Promise(resolve => setTimeout(resolve, delay));
                }
            }
            throw new Error("Falha ao realizar a chamada da API após várias tentativas.");
        }


        /**
         * Processa o texto gerado e extrai as fontes de aterramento.
         * @param {object} result - O objeto de resposta da API.
         * @returns {{text: string, sources: Array<{uri: string, title: string}>}} O texto e as fontes.
         */
        function extractContentAndSources(result) {
            const candidate = result.candidates?.[0];

            if (!candidate || !candidate.content?.parts?.[0]?.text) {
                return { text: "Não foi possível gerar um resumo. A resposta da IA estava vazia ou incompleta.", sources: [] };
            }

            const text = candidate.content.parts[0].text;
            let sources = [];
            const groundingMetadata = candidate.groundingMetadata;

            if (groundingMetadata && groundingMetadata.groundingAttributions) {
                sources = groundingMetadata.groundingAttributions
                    .map(attribution => ({
                        uri: attribution.web?.uri,
                        title: attribution.web?.title,
                    }))
                    .filter(source => source.uri && source.title)
                    // Filtra para manter apenas fontes únicas baseadas na URI
                    .filter((value, index, self) => 
                        index === self.findIndex((t) => (
                            t.uri === value.uri
                        ))
                    );
            }

            return { text, sources };
        }
        
        /**
         * Converte a lista Markdown gerada pela IA para HTML no estilo Steam (listas largas).
         * @param {string} markdownText - O texto da lista em Markdown.
         * @returns {string} - A grid de cards formatada em HTML.
         */
        function formatReleasesList(markdownText) {
            // Filtro de segurança: remove asteriscos residuais
            let cleanMarkdown = markdownText.replace(/\*\*/g, '');
            
            // Pega as primeiras 10 linhas que parecem itens de lista
            const lines = cleanMarkdown.split('\n').filter(line => line.trim().startsWith('-')).slice(0, 10); 
            let html = ''; 

            if (lines.length === 0) {
                 return '<p class="col-span-full text-gray-400 text-center p-4">Nenhum lançamento encontrado para os próximos 3 meses.</p>';
            }

            lines.forEach((line, index) => {
                let cleanedLine = line.trim().substring(1).trim(); 
                
                // 1. Extrai o nome do jogo (entre [[...]])
                const nameMatch = cleanedLine.match(/\[\[(.*?)\]\]/);
                const gameName = nameMatch ? nameMatch[1].trim() : 'Jogo Desconhecido';
                
                // 2. Extrai o resto do texto (Plataforma, Data, etc.)
                let details = cleanedLine.replace(/\[\[.*?\]\]/g, '').trim(); 
                
                // Tenta extrair a data/plataforma (texto após o primeiro '- ' se houver)
                const detailMatch = details.match(/-\s*(.*)/);
                const dateAndPlatform = detailMatch ? detailMatch[1].trim() : 'Informação de Lançamento Desconhecida';


                const escapedGameName = gameName.replace(/'/g, "\\'");
                const placeholderText = encodeURIComponent(gameName.toUpperCase().substring(0, 15));
                
                // URL de imagem placeholder no estilo Steam (tamanho 460x215)
                // Usando cor de fundo Dark Blue-Gray e texto Steam Blue
                const imageUrl = `https://placehold.co/460x215/2A475E/66C0F4?text=${index + 1}+-+${placeholderText}`;
                

                // Estrutura do Item de Lista (Steam List Item)
                // Note que aqui removemos o preço e focamos na imagem + detalhes.
                html += `
                    <div class="steam-release-item" onclick="loadGameDetails('${escapedGameName}')">
                        <!-- Imagem / Banner (à esquerda) -->
                        <div class="md:w-1/4 lg:w-1/5 flex-shrink-0 mb-3 md:mb-0 md:mr-4">
                            <img src="${imageUrl}" alt="Banner de ${gameName}" class="steam-image-placeholder-container w-full h-auto rounded-md object-cover">
                        </div>
                        
                        <!-- Detalhes (à direita) -->
                        <div class="flex-grow flex flex-col justify-center">
                            <h3 class="steam-title text-xl mb-1 hover:text-white transition duration-150" title="${gameName}">
                                ${index + 1}. ${gameName}
                            </h3>
                            <p class="steam-date text-sm mb-2">${dateAndPlatform}</p>
                            
                            <!-- Descrição Curta (Garantindo que o layout funcione) -->
                            <p class="text-gray-400 text-xs overflow-hidden line-clamp-2">
                                Um dos títulos mais esperados do ano. Clique para ver a análise e mais informações.
                            </p>
                            <!-- NÃO HÁ PREÇO AQUI -->
                        </div>
                    </div>
                `;
            });
            
            // Remove a mensagem de carregamento se houver conteúdo
            releasesContainer.classList.remove('items-center', 'justify-center');

            return html;
        }


        /**
         * Renderiza o conteúdo (texto) e as fontes da tela principal (Featured Card).
         * @param {string} text - O texto gerado pela IA.
         * @param {Array<object>} sources - A lista de fontes.
         */
        function renderResults(text, sources) {
            let content = text;
            let linkHtml = '';

            // Limpeza de segurança
            content = content.replace(/\*\*/g, ''); 

            // 1. Processamento e Formatação do Texto: Aplica formatação e torna os títulos clicáveis
            const formattedContent = content
                // 1.1. Substitui as quebras de linha por <br>
                .replace(/\n/g, '<br>')
                // 1.2. Aplica formatação e torna os títulos clicáveis, chamando loadGameDetails()
                .replace(/\[\[(.*?)\]\]/g, (match, title) => {
                    const gameName = title.trim();
                    // Escapa aspas simples para segurança na chamada onclick
                    const escapedGameName = gameName.replace(/'/g, "\\'"); 

                    return `
                        <a href="#" 
                           onclick="loadGameDetails('${escapedGameName}'); return false;" 
                           class="text-red-400 hover:text-red-300 hover:underline font-extrabold transition duration-150"
                           title="Ver detalhes de ${gameName}">
                            <span class="uppercase">${gameName}</span>
                        </a>
                    `;
                });

            // Se existirem fontes, destacamos a primeira como principal
            if (sources.length > 0) {
                const primarySource = sources[0];
                linkHtml = `
                    <div class="mb-4 p-4 bg-gray-700 border-l-4 border-red-500 rounded-lg">
                        <p class="text-sm font-semibold text-red-300 mb-1">Fonte Principal da Notícia:</p>
                        <a href="${primarySource.uri}" target="_blank" class="text-red-400 hover:text-red-300 hover:underline font-medium break-words" title="${primarySource.title || primarySource.uri}">
                            ${primarySource.title || primarySource.uri}
                        </a>
                    </div>
                `;
            }

            // --- Estrutura de Destaque com Fundo Preto à Esquerda ---
            const placeholderUrl = `https://placehold.co/400x300/222d3b/93c5fd?text=${encodeURIComponent("DESTAQUE PRINCIPAL")}`;
            
            resultsDiv.innerHTML = `
                <div class="md:grid md:grid-cols-3 min-h-[300px]">
                    <!-- Coluna 1: Imagem/Placeholder (1/3) - AGORA BG-BLACK PURO -->
                    <div class="md:col-span-1 bg-black overflow-hidden relative hidden md:block">
                        <img src="${placeholderUrl}" alt="Imagem de destaque" class="w-full h-full object-cover opacity-70">
                        <!-- Overlay de Destaque -->
                        <div class="absolute inset-0 bg-black/50 flex items-center justify-center p-4">
                            <p class="text-white text-xl font-bold uppercase tracking-widest text-center">NOTÍCIA EM DESTAQUE</p>
                        </div>
                    </div>
        
                    <!-- Coluna 2: Conteúdo do Texto (2/3) -->
                    <div class="md:col-span-2 p-6 md:p-8 space-y-4"> 
                        ${linkHtml}
                        <p class="llm-output">${formattedContent}</p>
                    </div>
                </div>
            `;
            // --- FIM DA ESTRUTURA ---

            
            // Remove as classes de centralização e altura mínima da div de resultados principal
            resultsDiv.classList.remove('flex', 'items-center', 'justify-center');
            featuredCardContent.classList.add('hidden'); // Oculta a mensagem inicial
            
            // Renderiza as fontes remanescentes
            sourcesList.innerHTML = '';
            const otherSources = sources.slice(1); 
            
            if (otherSources.length > 0) {
                sourcesContainer.querySelector('h3').textContent = otherSources.length > 1 ? "Outras Fontes Consultadas:" : "Outra Fonte Consultada:";
                otherSources.forEach(source => {
                    const listItem = document.createElement('li');
                    listItem.innerHTML = `<a href="${source.uri}" target="_blank" class="text-red-400 hover:text-red-300 hover:underline transition duration-150" title="${source.title}">
                                            ${source.title || source.uri}
                                          </a>`;
                    sourcesList.appendChild(listItem);
                });
                sourcesContainer.classList.remove('hidden');
            } else {
                sourcesContainer.classList.add('hidden');
            }
        }
        
        /**
         * Renderiza o conteúdo (texto) e as fontes na tela de detalhes (Produto).
         * @param {string} text - O texto gerado pela IA.
         * @param {Array<object>} sources - A lista de fontes.
         */
        function renderDetailResults(text, sources) {
            
            // O texto é dividido em duas partes: o resumo curto (primeira secção) e o conteúdo principal (restante)
            const parts = text.split(/\[\[História e Contexto\]\]/i);
            const summaryText = parts[0].trim();
            const mainContentText = parts.length > 1 ? `[[História e Contexto]]${parts.slice(1).join('[[História e Contexto]]').trim()}` : '';
            
            // Limpeza de segurança
            const cleanSummary = summaryText.replace(/\*\*/g, ''); 
            const cleanMainContent = mainContentText.replace(/\*\*/g, '');

            // Remove o overlay de carregamento da imagem, mostrando a imagem placeholder final
            const imageOverlay = document.getElementById('imageOverlay');
            if (imageOverlay) {
                imageOverlay.remove();
            }

            // 1. Renderiza o Bloco Resumido (Novo Local)
            const formattedSummary = cleanSummary.replace(/\n/g, '<br>');
            gameDetailContentSummary.innerHTML = `<div class="llm-output">${formattedSummary}</div>`;
            gameDetailContentSummary.classList.remove('flex', 'items-center', 'justify-center');

            // 2. Renderiza o Conteúdo Principal (História/Gameplay)
            const formattedMainContent = cleanMainContent
                .replace(/\n/g, '<br>')
                // Aplica a formatação (destaque para títulos) aos títulos envolvidos em [[...]]
                .replace(/\[\[(.*?)\]\]/g, (match, title) => 
                    `<h3 class="font-bold text-xl text-red-400 mt-4 mb-2">${title.trim().toUpperCase()}</h3>`
                );

            gameDetailContent.innerHTML = `<div class="llm-output">${formattedMainContent}</div>`;
            gameDetailContent.classList.remove('flex', 'items-center', 'justify-center');


            // 3. Renderiza as fontes (Rodapé)
            detailSourcesList.innerHTML = '';
            if (sources.length > 0) {
                sources.forEach(source => {
                    const listItem = document.createElement('li');
                    listItem.innerHTML = `<a href="${source.uri}" target="_blank" class="text-red-400 hover:text-red-300 hover:underline transition duration-150" title="${source.title}">
                                            ${source.title || source.uri}
                                          </a>`;
                    detailSourcesList.appendChild(listItem);
                });
                detailSourcesContainer.classList.remove('hidden');
            } else {
                detailSourcesContainer.classList.add('hidden');
            }
        }


        /**
         * Define a query de busca no input e dispara a busca principal.
         * @param {string} query - A query a ser definida e buscada.
         */
        function setQueryAndFetch(query) {
            queryInput.value = query;
            fetchGameNews();
            // Fecha o submenu de consolas após a seleção
            if (!consoleSubMenu.classList.contains('hidden')) {
                toggleConsoleSubMenu();
            }
        }
        
        /**
         * Alterna a visibilidade do submenu de Consolas.
         */
        function toggleConsoleSubMenu() {
            consoleSubMenu.classList.toggle('hidden');
            consolasButton.classList.toggle('bg-red-600');
            consolasButton.classList.toggle('hover:bg-red-600');
            consolasButton.classList.toggle('bg-gray-700');
            consolasButton.classList.toggle('hover:bg-red-700');
        }

        /**
         * Função principal para buscar notícias e lançamentos de jogos.
         */
        async function fetchGameNews() {
            const userQuery = queryInput.value.trim();
            if (!userQuery) return;
            
            // 1. Configurar o estado de carregamento
            searchButton.disabled = true;
            loadingSpinner.classList.remove('hidden');
            searchIcon.classList.add('hidden');
            errorContainer.classList.add('hidden');
            errorMessage.textContent = '';
            
            // Limpa o conteúdo principal
            resultsDiv.innerHTML = '';
            featuredCardContent.classList.remove('hidden'); // Mostra a área para o spinner
            featuredCardContent.innerHTML = `
                <div class="flex flex-col items-center">
                    <svg class="w-10 h-10 animate-spin text-red-500" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                        <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                        <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                    </svg>
                    <p class="mt-4 text-red-400 text-lg">A buscar notícias e a sintetizar o relatório...</p>
                </div>
            `;
            
            // Limpa o conteúdo de lançamentos
            releasesContainer.innerHTML = '<p id="releasesMessage" class="col-span-full text-gray-400 text-center">A carregar a lista de lançamentos...</p>';
            releasesContainer.classList.add('items-center', 'justify-center');

            try {
                // 2. Chamada da API para o Resumo Principal
                const systemPromptMain = "Você é um repórter de videogame e informação de mercado. Seu objetivo é fornecer uma visão geral concisa e empolgante, em português, das notícias mais importantes sobre o tópico. Inclua análises e previsões sobre os principais jogos mencionados. Para jogos específicos (títulos), use a formatação especial [[Nome do Jogo]] no texto para destacá-los. O resultado deve ser apenas o texto do artigo/resumo, sem títulos ou formatação externa.";
                
                const mainPayload = {
                    contents: [{ parts: [{ text: userQuery }] }],
                    tools: [{ "google_search": {} }],
                    systemInstruction: { parts: [{ text: systemPromptMain }] },
                };

                const mainResponse = await fetchWithBackoff(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(mainPayload)
                });
                
                const mainResult = await mainResponse.json();
                const { text: mainText, sources: mainSources } = extractContentAndSources(mainResult);
                
                // Renderizar o resumo principal e fontes
                renderResults(mainText, mainSources);


                // 3. Chamada da API para a Lista de Lançamentos
                const releasesQuery = `Quais são os 10 jogos mais aguardados para os próximos 3 meses, incluindo o mês, ano e plataforma (PC, PS5, Xbox, Switch)? Retorne APENAS uma lista em Markdown. Para cada jogo, use o formato: - [[Nome do Jogo]] - Plataforma, Data (Ex: Junho 2026).`;

                const releasesPayload = {
                    contents: [{ parts: [{ text: releasesQuery }] }],
                    tools: [{ "google_search": {} }],
                    systemInstruction: { parts: [{ text: "Você é um sistema de catalogação de jogos. Gere apenas uma lista Markdown. Não adicione texto introdutório ou conclusivo." }] },
                };

                const releasesResponse = await fetchWithBackoff(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(releasesPayload)
                });
                
                const releasesResult = await releasesResponse.json();
                const { text: releasesText } = extractContentAndSources(releasesResult);
                
                // Renderizar a lista de lançamentos (Grid de Cards)
                releasesContainer.innerHTML = formatReleasesList(releasesText);

            } catch (error) {
                console.error("Erro no fetchGameNews:", error);
                errorMessage.textContent = `Não foi possível carregar as informações. Por favor, tente novamente. Detalhe: ${error.message}`;
                errorContainer.classList.remove('hidden');
                
                // Restaura o conteúdo principal e a lista com mensagens de erro
                resultsDiv.innerHTML = `<p class="text-red-400 p-8 text-center text-lg">Falha ao obter o resumo das notícias. Verifique a sua conexão ou tente uma busca mais simples.</p>`;
                releasesContainer.innerHTML = `<p class="col-span-full text-red-400 text-center p-4">Falha ao obter a lista de lançamentos.</p>`;
                featuredCardContent.classList.add('hidden');
            } finally {
                // 4. Configurar o estado final
                searchButton.disabled = false;
                loadingSpinner.classList.add('hidden');
                searchIcon.classList.remove('hidden');
            }
        }
        
        /**
         * Função para carregar os detalhes de um jogo específico na Detail View.
         * @param {string} gameName - O nome do jogo.
         */
        async function loadGameDetails(gameName) {
            
            // 1. Mudar para a vista de Detalhes
            switchView('detailView');
            
            // 2. Configurar o estado de carregamento
            gameDetailTitle.textContent = gameName.toUpperCase();
            gameDetailImageContainer.innerHTML = `
                <div id="imageOverlay" class="absolute inset-0 bg-gray-900/90 flex flex-col items-center justify-center text-white p-4">
                    <svg class="w-10 h-10 animate-spin text-red-500" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                        <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                        <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                    </svg>
                    <p class="mt-4 text-red-400">A gerar resumo do jogo...</p>
                </div>
                <img src="${getSvgPlaceholder(gameName)}" alt="Placeholder Art for ${gameName}" class="w-full h-auto object-cover rounded-xl border border-gray-700 shadow-xl" />
            `;
            
            // 3. Chamada da API para os Detalhes do Jogo
            try {
                // Modificado para pedir explicitamente o resumo antes do conteúdo principal
                const detailQuery = `Gere uma análise detalhada e uma descrição do jogo "${gameName}". COMECE com um parágrafo de resumo curto e, em seguida, inclua secções detalhadas sobre [[História e Contexto]] e [[Jogabilidade e Mecânicas]]. Use a formatação [[TITULO]] para os títulos das secções.`;
                
                const detailPayload = {
                    contents: [{ parts: [{ text: detailQuery }] }],
                    tools: [{ "google_search": {} }],
                    systemInstruction: { parts: [{ text: "Você é um analista de jogos. Gere um artigo informativo e detalhado sobre o jogo, em português. O resultado deve ser apenas o texto do artigo/análise, sem títulos ou formatação externa. Certifique-se de que o primeiro parágrafo é um resumo curto e conciso." }] },
                };

                const detailResponse = await fetchWithBackoff(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(detailPayload)
                });
                
                const detailResult = await detailResponse.json();
                const { text: detailText, sources: detailSources } = extractContentAndSources(detailResult);
                
                // Renderizar os detalhes
                renderDetailResults(detailText, detailSources);

            } catch (error) {
                console.error("Erro ao carregar detalhes do jogo:", error);
                
                // Remover o overlay de carregamento
                const imageOverlay = document.getElementById('imageOverlay');
                if (imageOverlay) imageOverlay.remove();

                gameDetailContent.innerHTML = `<p class="text-red-400 p-6">Erro ao carregar os detalhes de ${gameName}. Por favor, tente novamente mais tarde.</p>`;
                gameDetailContent.classList.remove('flex', 'items-center', 'justify-center');
                detailSourcesContainer.classList.add('hidden');
                
                // Também atualiza o resumo
                gameDetailContentSummary.innerHTML = `<p class="text-red-400 p-6">Erro ao carregar o resumo de ${gameName}.</p>`;
                gameDetailContentSummary.classList.remove('flex', 'items-center', 'justify-center');
            }
        }
        
        /**
         * Inicialização: Carrega os dados iniciais ao carregar a página.
         */
        window.onload = function() {
            // Inicia a busca com a query predefinida
            fetchGameNews(); 
        };
    </script>
</body>
</html>
