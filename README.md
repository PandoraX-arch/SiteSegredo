# 🔒 Secret Vault

Um cofre digital elegante para compartilhar mensagens sigilosas com limite de visualizações e proteção anti-compartilhamento.

## Funcionalidades

- **Senha de acesso** — só quem tem a senha pode ver a mensagem
- **Limite de visualizações** — configurável (padrão: 3 vezes)
- **Fingerprinting de dispositivo** — detecta se o link foi compartilhado com outro dispositivo e bloqueia o acesso
- **Registro de acessos** — log completo com horário, ID e status de cada entrada
- **Design elegante** — tema escuro com detalhes em dourado, tipografia serifada, animações cinematográficas

## Configuração

Edite o arquivo `src/config.js`:

```js
export const CONFIG = {
  password: 'sua-senha',           // Senha para acessar o cofre
  secretTitle: 'Para Você',        // Título exibido após o acesso
  secretMessage: 'Sua mensagem…',  // A mensagem secreta
  maxViews: 3,                     // Número máximo de visualizações
  sender: 'Anônimo',               // Nome do remetente
}
```

## Como rodar

```bash
npm install
npm run dev
```

## Deploy

```bash
npm run build
```

A pasta `dist/` estará pronta para deploy em Vercel, Netlify, GitHub Pages, etc.

## Como funciona a proteção

1. Na primeira vez que alguém acessa com a senha correta, o app registra um **fingerprint** do dispositivo (user agent, resolução, fuso horário, idioma, etc.)
2. Se alguém tentar acessar de um **dispositivo diferente**, o acesso é bloqueado imediatamente
3. Cada visualização é registrada no histórico local
4. Ao atingir o limite de visualizações, o cofre é bloqueado permanentemente

> **Nota:** os dados são armazenados no `localStorage` do navegador — não há servidor, tudo é local.

## Stack

- React 18 + Vite
- CSS customizado (sem frameworks)
- Fontes: Cormorant Garamond + IBM Plex Mono (Google Fonts)
