
# Sintetizador de Pesquisa

Automação que recebe um pedido por áudio ou texto no Telegram, pesquisa o tema na web, sintetiza os principais insights e gera conteúdo pronto (já adaptado ao tom, público e formato) para diferentes redes sociais — sem que o time de marketing precise pesquisar manualmente.

## Objetivo

Agilizar a criação de conteúdo para redes sociais, eliminando o tempo gasto pesquisando um assunto do zero antes de escrever o post.

## Como funciona

1. Funcionário envia um áudio ou texto pelo bot do Telegram, descrevendo o tema, tom e plataforma desejada (LinkedIn, Instagram, Twitter, vídeo, newsletter)
2. Se for áudio, a automação transcreve o conteúdo automaticamente
3. Um agente de IA extrai as informações principais do pedido (tema, plataformas, tom, público-alvo)
4. Pesquisa o tema em tempo real na web (via Tavily) e sintetiza os principais insights em bullets
5. Um agente "Diretor Criativo" define a estratégia editorial ideal para cada plataforma solicitada
6. Redatores especializados (um agente de IA por formato) geram o conteúdo final para LinkedIn, Instagram, Twitter, vídeo e/ou newsletter
7. Os conteúdos gerados são salvos organizados em pastas no Google Drive
8. O funcionário recebe a resposta final de volta no Telegram

## Nodes principais

`Telegram Trigger` · `Google Gemini` (transcrição de áudio) · `Information Extractor` · `Tavily` (pesquisa web) · `Summarization Chain` · `Chain LLM` (agentes redatores por plataforma) · `Google Drive` · `Telegram` (resposta)

---
*Automação construída na plataforma N8N (no-code/low-code), utilizando nodes nativos e lógica visual de fluxo.*
