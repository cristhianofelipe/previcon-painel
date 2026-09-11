# PREVICON — Painel de Carteira (app instalável)

## O que é

Um site estático (PWA) que mostra o painel de rentabilidade da carteira PREVICON.
Qualquer pessoa pode abrir o link no celular e tocar em **"Adicionar à tela inicial"**
para instalar como app, com ícone próprio, sem barra de navegador.

Os dados ficam embutidos no próprio `index.html`, entre os marcadores
`PAINEL_DATA_INICIO` e `PAINEL_DATA_FIM`. Não depende de planilha nem de
nenhum serviço externo — é o mesmo padrão do painel HTML que a rotina
semanal já gera hoje.

## Passo 1 — Criar o repositório no GitHub

1. Crie uma conta em https://github.com (se ainda não tiver).
2. Clique em **New repository**. Nome sugerido: `previcon-painel`.
   Marque como **Public** (obrigatório para o GitHub Pages gratuito).
3. Faça upload dos arquivos desta pasta (`index.html`, `manifest.json`,
   `service-worker.js`, a pasta `icons/`) — pode arrastar tudo na tela
   "uploading an existing file" do próprio GitHub, sem precisar usar linha
   de comando.

## Passo 2 — Ativar o GitHub Pages

1. No repositório, vá em **Settings > Pages**.
2. Em "Source", selecione a branch `main` e a pasta `/ (root)`.
3. Salve. Em 1–2 minutos o GitHub mostra a URL pública, algo como:
   `https://SEU-USUARIO.github.io/previcon-painel/`
4. Esse é o link que qualquer pessoa acessa — no celular, ao abrir esse
   link no Chrome/Safari, aparece a opção de instalar como app.

## Passo 3 — Ligar a atualização semanal

Hoje a tarefa Programada (no projeto "Rentabilidade - Carteira PREVICON")
já processa os extratos e atualiza um painel HTML. Peça a ela para, no
lugar de só isso, também **atualizar este arquivo no GitHub**:

> "Depois de calcular os números da semana, atualize o bloco de dados
> (entre `PAINEL_DATA_INICIO` e `PAINEL_DATA_FIM`) no arquivo `index.html`
> do repositório GitHub `SEU-USUARIO/previcon-painel`, mantendo o mesmo
> formato CSV e atualizando também a variável `PAINEL_ATUALIZADO_EM`.
> Depois, faça commit e push dessa alteração para a branch `main`."

O GitHub Pages redeploya sozinho a cada push (leva menos de um minuto).
Quem já tiver o app instalado vê a atualização automaticamente na próxima
vez que abrir (o app verifica isso sozinho, e também tem um botão
"Verificar atualização").

## Domínio próprio (opcional)

Se quiser um endereço tipo `painel.previcon.mt.gov.br` em vez do
`github.io`, é possível apontar um domínio próprio nas configurações do
GitHub Pages (Settings > Pages > Custom domain) — me avise se quiser
ajuda com isso depois.
