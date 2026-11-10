# Voz do Riacho

Enquete popular informal sobre preferências para a Administração Regional do Riacho Fundo I (RA XVII), Distrito Federal.

Site publicado: https://voz-riacho-fundo-enquete.flutedpitch3.chatgpt.site

## Recursos

- 11 nomes com o mesmo destaque visual.
- Confirmação antes de registrar o voto.
- Votos persistidos em Cloudflare D1 e resultados com percentuais.
- Compartilhamento pelo WhatsApp ou pela função de compartilhamento do dispositivo.
- Layout responsivo e controles acessíveis por teclado.
- Sem solicitação de nome, telefone ou CPF.

O bloqueio de repetição usa um identificador aleatório em cookie e limita a participação por navegador. Não assegura um voto por pessoa. A enquete não é uma eleição oficial nem uma pesquisa representativa da população.

## Desenvolvimento

Requer Node.js 24 ou superior; não há dependências externas para instalar.

```sh
npm run dev
```

A prévia usa SQLite local em `.sites-runtime/preview.sqlite`. O servidor escuta na porta 4173. O cookie de participação tem o atributo `Secure`; use uma prévia HTTPS para testar a votação no navegador.

## Build e hospedagem

```sh
npm run build
```

A entrada do Worker é gerada em `dist/server/index.js`. A configuração do site existente está em `.openai/hosting.json`. O ambiente de produção precisa de um banco D1 com binding `DB`; aplique `drizzle/0000_votes.sql` antes de receber votos. O build e o repositório não contêm votos de produção.

Este projeto requer um servidor Cloudflare Worker e D1; GitHub Pages sozinho não executa as APIs de votação. Publicar o código no GitHub não substitui a hospedagem atual.

## Estrutura

- `worker/index.js`: página, estilos, código do navegador e APIs.
- `drizzle/`: migração do banco de dados.
- `scripts/build.mjs`: montagem do Worker.
- `scripts/preview.mjs`: servidor de desenvolvimento com SQLite.

As fontes DM Sans e Manrope são carregadas do Google Fonts, com alternativas locais quando indisponíveis.
