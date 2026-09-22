# Agente de Onboarding

Agente de IA que atende novos colaboradores diretamente no Slack, respondendo dúvidas sobre setores, processos, responsáveis e rotinas da empresa a partir de uma base de conhecimento interna.

## Objetivo

Reduzir a carga do RH e dos líderes com perguntas repetitivas dos primeiros dias e dar ao novo colaborador uma resposta imediata, sem precisar descobrir sozinho "com quem falar sobre o quê".

## Como funciona

1. Uma mensagem é enviada no Slack da empresa (o workflow monitora eventos do workspace)
2. Um filtro ignora as mensagens do próprio bot, evitando loops de resposta
3. O agente de IA recebe a pergunta e consulta a base de conhecimento da empresa (um Code Tool com setores, responsáveis, e-mails, atribuições, prazos e dúvidas comuns)
4. Uma memória de conversa, separada por canal, mantém o contexto entre as mensagens
5. A resposta é enviada de volta ao mesmo canal do Slack

## Exemplos de perguntas que o agente responde

- "Com quem falo para solicitar meu contracheque?"
- "Como faço para pedir férias?"
- "Qual o prazo para receber um reembolso?"
- "Como solicito a compra de um equipamento?"
- "Meu e-mail não está funcionando, com quem falo?"

## Tecnologias

- [n8n](https://n8n.io/)
- Slack (Slack Trigger + envio de mensagem)
- Groq (modelo `openai/gpt-oss-120b`)
- AI Agent do n8n com Simple Memory e Code Tool

## Estrutura do workflow

| Nó | Função |
|---|---|
| Slack Trigger | Dispara o fluxo a cada evento do workspace |
| If | Filtra mensagens do próprio bot |
| AI Agent | Interpreta a pergunta e monta a resposta |
| Groq Chat Model | Modelo de linguagem usado pelo agente |
| Simple Memory | Memória de conversa por canal |
| Code Tool | Base de conhecimento da empresa (dados fictícios) |
| Send a message | Envia a resposta ao canal do Slack |

## Como usar

1. Importe o arquivo `agente-onboarding.json` no n8n (**Workflows → Import from File**)
2. Configure as credenciais, que **não estão incluídas** no arquivo por segurança:
   - **Slack API** (nos nós *Slack Trigger* e *Send a message*)
   - **Groq API** (no nó *Groq Chat Model*)
3. No nó **If**, substitua `SEU_ID_DO_BOT_NO_SLACK` pelo ID do usuário do seu bot no Slack
4. Adapte o conteúdo do nó **Code Tool** com as informações reais da sua empresa
5. Ative o workflow

## Observações

- Os dados da empresa (NovaTech Solutions), nomes, e-mails e responsáveis são **fictícios**.
