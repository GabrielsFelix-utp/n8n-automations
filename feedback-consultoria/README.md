
# Automação Feedback Consultoria

Automação que analisa as respostas de pesquisas de satisfação (NPS) preenchidas pelos clientes após cada consultoria e gera um feedback automático para o consultor sempre que a média do dia fica abaixo da meta.

## Objetivo

Dar ao consultor um retorno rápido e construtivo sobre o atendimento prestado, baseado na percepção real dos clientes, sem depender de um gestor revisar manualmente cada resposta de pesquisa.

## Como funciona

1. **Gatilho diário** (todo dia às 21h)
2. Busca a lista de consultores cadastrados
3. Para cada consultor, filtra as respostas do formulário de satisfação do dia
4. Consolida as avaliações: nota média de satisfação e sugestões de melhoria dos clientes
5. Se a média do dia ficou **abaixo de 7**, um agente de IA analisa os comentários, identifica os principais temas de fricção (agrupados, não listados um a um) e escreve um e-mail de feedback construtivo e motivador para o consultor

## Nodes principais

`Schedule Trigger` · `Google Sheets` (consultores e respostas) · `Split In Batches` (loop por consultor) · `Summarize` · `IF` (condicional de nota) · `AI Agent` (Google Gemini)

---
*Automação construída na plataforma N8N (no-code/low-code), utilizando nodes nativos e lógica visual de fluxo.*
