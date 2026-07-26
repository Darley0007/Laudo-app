# Laudo — Andamento Processual

## Como publicar no Netlify

**Passo importante:** o app usa a API da Anthropic para analisar os documentos.
No ambiente original (artifact do Claude) a chave era injetada automaticamente,
mas fora dali isso não existe — por isso incluí uma Netlify Function
(`netlify/functions/analyze.js`) que guarda a chave no servidor com segurança.

1. Suba esta pasta para um repositório no GitHub (ou arraste a pasta direto
   no painel do Netlify, em "Deploy manually").
2. No Netlify: **Add new site → Import an existing project**, aponte para o
   repositório. Build command e publish directory já estão configurados no
   `netlify.toml` (`npm run build` / `dist`).
3. Em **Site settings → Environment variables**, adicione:
   - `ANTHROPIC_API_KEY` = sua chave da API da Anthropic (console.anthropic.com)
4. Faça o deploy. Pronto — o app estará no ar.

## Rodar localmente (opcional)

```
npm install
npm run dev
```

Para testar a function localmente, use a Netlify CLI:
```
npm install -g netlify-cli
netlify dev
```
