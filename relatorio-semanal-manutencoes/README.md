
# Relatório Semanal de Manutenções

Automação que consulta a planilha de manutenções da empresa, avalia o status de cada equipamento (no prazo, em risco ou atrasado) e envia um briefing executivo por e-mail ao gestor toda semana — sem necessidade de abrir a planilha manualmente.

## Objetivo

Dar ao gestor uma visão rápida (30 segundos de leitura) de quais manutenções estão atrasadas, quais estão perto do prazo e quais estão indo bem, sem precisar revisar linha por linha da planilha.

## Como funciona

1. **Gatilho semanal** (toda terça-feira, 8h)
2. Busca os dados da planilha de manutenções no Google Sheets
3. Calcula automaticamente quantos dias faltam (ou passaram) do prazo de cada reparo
4. Classifica cada equipamento como **atrasado**, **em risco** (prazo próximo) ou **no prazo**
5. Um agente de IA analisa o conjunto de dados e escreve um resumo executivo, priorizando atrasos críticos
6. O relatório é enviado automaticamente por e-mail (Outlook) ao gestor responsável

## Nodes principais

`Schedule Trigger` · `Google Sheets` · `Set` (tratamento de dados) · `Aggregate` · `AI Agent` (Google Gemini) · `Microsoft Outlook`

---
*Automação construída na plataforma N8N (no-code/low-code), utilizando nodes nativos e lógica visual de fluxo.*
