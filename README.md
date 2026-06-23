# DuckFlix TV

APK de TV da DuckFlix — um "embrulho" WebView que abre **https://duckflix-nine.vercel.app**
em tela cheia, navegável pelo controle remoto. Funciona em **Fire TV / Fire Stick**,
**Android TV / Google TV** e celulares/tablets Android.

O conteúdo é o site (atualiza sozinho no Vercel). O APK quase nunca precisa mudar.

## Como o APK é gerado (automático, sem instalar nada)

Todo `push` na branch `main` dispara o GitHub Actions, que compila o APK na nuvem e
publica em **Releases**. O link de download **fixo** (sempre o mais novo) é:

```
https://github.com/henryksgroup-collab/duckflix-tv/releases/latest/download/duckflix-tv.apk
```

## Instalar pelo Downloader (AFTVnews)

1. Abra o app **Downloader** no Fire TV / Android TV.
2. No campo de URL, digite o link acima (ou o código curto gerado em aftv.news).
3. **Go** → baixa → **Install**.

## Instalar pelo NTDown

1. Registre o APK acima no NTDown para receber um **código numérico**.
2. Na TV, abra o **NTDown**, digite o código → instala.

## Atualizar o app

- Só dá `push` em `main` (ou roda o workflow "Build DuckFlix TV APK" manualmente).
  Sai um novo Release e o link `latest` passa a apontar pra ele.
- Como o app é um WebView do site, o de-para de conteúdo/UX acontece no Vercel —
  reinstalar o APK só é necessário se mudar algo no embrulho nativo.

## O que o embrulho faz

- Tela cheia + esconde a barra do sistema (imersivo).
- `localStorage` ligado → login, device-id e persistência funcionam igual ao navegador.
- Autoplay e **vídeo em tela cheia** (custom view) — o player do site abre fullscreen.
- Botão **Voltar** do controle volta no histórico; segura a saída acidental.
- **Pop-up de anúncio bloqueado**: `target=_blank`/`window.open` não abrem nova janela.

Editar a URL do app: `app/src/main/java/com/duckflix/tv/MainActivity.java` (`APP_URL`).
