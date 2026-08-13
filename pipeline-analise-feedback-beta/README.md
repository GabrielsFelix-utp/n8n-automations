
# Pipeline de Análise com IA (BETA)

> Primeira versão desenvolvida deste tipo de automação — mantida no repositório como registro de evolução técnica.

Automação que analisa feedbacks recebidos por e-mail sobre uma versão do sistema, identifica sentimento e categoria (bug, reclamação, sugestão ou elogio) e encaminha um resumo automático para o canal certo no Slack, além de gerar um briefing diário para o CEO.

## Objetivo

Dar aos desenvolvedores e à liderança uma visão organizada e resumida dos feedbacks recebidos, sem precisar ler e-mail por e-mail manualmente para entender o que precisa de atenção.

## Como funciona

1. **Gatilho por e-mail** (Gmail) sempre que um novo feedback chega
2. Extrai as informações principais do feedback (cliente, ponto principal)
3. Um agente de IA analisa o **sentimento** (positivo/negativo) e a **categoria** (bug, reclamação, sugestão, elogio)
4. Feedbacks marcados como urgentes disparam um alerta imediato no Slack
5. Cada categoria é encaminhada para o canal correspondente no Slack, já resumida
6. Reclamações e elogios recebem uma resposta automática por e-mail ao cliente
7. Todo feedback é registrado em uma planilha
8. **Gatilho semanal**: um segundo fluxo consulta os feedbacks do dia e gera um briefing executivo em HTML (total de feedbacks, sentimentos, categorias, casos urgentes e recomendação) enviado por e-mail

## Nodes principais

`Gmail Trigger` · `Information Extractor` · `Sentiment Analysis` · `Text Classifier` · `Slack` · `Gmail` (resposta automática) · `Google Sheets` · `Schedule Trigger` · `Basic LLM Chain` (briefing executivo)

---
*Automação construída na plataforma N8N (no-code/low-code), utilizando nodes nativos e lógica visual de fluxo.*
