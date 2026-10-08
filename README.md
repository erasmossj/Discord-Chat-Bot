# Discord Chat Bot com Gemini 🤖

Bot de Discord que conversa usando o **Google Gemini** e guarda o histórico recente de cada usuário em um banco de dados, para manter o contexto entre as mensagens.

## Sobre

Projeto pessoal para experimentar aplicações com modelos de linguagem (LLMs) dentro do Discord. O bot responde quando é mencionado ou quando alguém responde a uma mensagem dele, e usa as últimas interações daquele usuário no canal como contexto para a resposta.

> Os comentários e textos explicativos do código foram traduzidos e formatados com ajuda de IA; o código foi escrito por Erasmo da Silva Sá Junior.

## Funcionalidades

- Responde quando o bot é **mencionado** ou quando alguém **responde a uma mensagem dele**.
- Ignora mensagens de outros bots.
- Gera as respostas com o **Google Gemini** (biblioteca `google-genai`), com um *system prompt* configurável.
- Salva usuários e histórico de conversa (mensagem e resposta) com **SQLAlchemy**, separado por usuário e por canal.
- Mantém só as **5 interações mais recentes** de cada usuário em cada canal, apagando as mais antigas.
- Antes de responder, reenvia ao modelo o histórico salvo daquele usuário no canal, para dar contexto.
- Lê as chaves e a URL do banco de um arquivo `.env`, sem nada sensível no código.

## Tecnologias

- [Python](https://www.python.org/)
- [discord.py](https://discordpy.readthedocs.io/)
- [Google Gen AI SDK (`google-genai`)](https://ai.google.dev/)
- [SQLAlchemy](https://www.sqlalchemy.org/)
- [python-dotenv](https://pypi.org/project/python-dotenv/)

## Como rodar

1. Instale as dependências:

   ```bash
   pip install -r requirements.txt
   ```

2. Crie um arquivo `.env` na raiz do projeto:

   ```env
   DISCORD_API_KEY=token_do_seu_bot
   DATABASE_URL=sqlite:///gemini_bot.db   # ou a URL de outro banco suportado pelo SQLAlchemy
   GEMINI_API_KEY=sua_chave_do_gemini
   ```

3. No [Discord Developer Portal](https://discord.com/developers/applications), ative o **Message Content Intent** do bot (o código usa `intents.message_content = True`).

4. Em `app.py`, troque os valores de exemplo `system_prompt = 'System Prompt'` e `model="Gemini-Model"` pelo prompt desejado e por um modelo válido do Gemini.

5. Inicie o bot:

   ```bash
   python app.py
   ```

   Quando aparecer `Online!` no terminal, o bot está conectado.

## Autor

Desenvolvido por **Erasmo da Silva Sá Junior** — [GitHub](https://github.com/erasmossj) · [LinkedIn](https://www.linkedin.com/in/erasmo-junior-883010309/).

## Licença

Distribuído sob a [Licença MIT](./LICENSE).
