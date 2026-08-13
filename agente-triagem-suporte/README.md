
# Agente de Triagem de Suporte

Agente de IA que recebe tickets de suporte via formulário, classifica automaticamente o tipo de problema, define prioridade com base no plano do cliente, tenta resolver o caso diretamente e organiza o acompanhamento em um quadro no Trello.

## Objetivo

Reduzir o tempo de primeira resposta ao cliente e organizar o fluxo de atendimento entre o que é resolvido automaticamente e o que precisa de atendimento manual da equipe.

## Como funciona

1. Cliente preenche um formulário com nome, e-mail, empresa, assunto e mensagem
2. O agente consulta a base de clientes para verificar o plano contratado (Enterprise/Corporate recebem prioridade elevada)
3. Classifica o ticket em categorias (bug, feature request, billing, account, how-to, performance) e define a prioridade (crítica, alta, média, baixa)
4. Sempre que possível, **gera uma solução prática e direta** para o cliente, com passos claros — não apenas um "vamos analisar e retornar"
5. Cria um card no Trello e o move entre listas, permitindo que a equipe acompanhe visualmente o que está com o agente automático e o que passou para atendimento manual
6. Encaminha o ticket à equipe responsável (engenharia, produto, financeiro ou customer success) e responde ao cliente por e-mail com protocolo de atendimento

## Nodes principais

`Form Trigger` · `Guardrails` · `AI Agent` (Google Gemini) · `Google Sheets` (consulta de plano) · `Structured Output Parser` · `Trello` (criação e movimentação de cards) · `IF` · `Gmail`

---
*Automação construída na plataforma N8N (no-code/low-code), utilizando nodes nativos e lógica visual de fluxo.*
