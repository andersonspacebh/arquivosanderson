# Landing page — Agendamento de Passaporte Italiano | Cittadini

Cores: off-white `#F7F3EC`, branco `#FFFFFF` e vinho `#6B1E2E` (vinho profundo `#4A1320`), sem dourado. Fonte da marca em tudo: Gilroy Bold (títulos), SemiBold (botões) e Medium (textos). Foto do banner: `originais/hero-coliseu.webp`.

## Pastas

| Pasta | O que tem | Vai para o ar? |
|---|---|---|
| `public/` | A página: `index.html`, `images/`, `fonts/`, favicons | Sim |
| `originais/` | Fotos e logo originais, antes da otimização | Não |
| `ferramentas/` | `servidor.ps1` (servidor local) e `otimizar-imagens.html` (gera as WebP) | Não |
| `vercel.json` | Diz à Vercel para publicar a pasta `public/` e guardar imagens e fontes em cache | Configuração |

## Antes de publicar

1. **Domínio:** no topo do `public/index.html` há 4 linhas com `https://cittadini-passaporte.vercel.app/`. Troque pelo endereço final. Sem isso o WhatsApp não mostra a imagem de prévia.
2. **WhatsApp e Instagram** (@cittadinicidadaniaeuropeia) ficam no bloco `CONFIG`, no topo do `index.html`. O rodapé mostra WhatsApp, Instagram e cidade (o e-mail foi retirado a pedido).

## Publicar na Vercel

- **Pelo site:** crie um projeto novo apontando para esta pasta (via GitHub). Em *Framework Preset* escolha **Other**, sem comando de build. O `vercel.json` já indica a pasta `public`.
- **Pela linha de comando** (precisa de Node): `npx vercel` dentro desta pasta.

## Testar no computador

```powershell
powershell -ExecutionPolicy Bypass -File ferramentas\servidor.ps1 -Port 8766
```

Abra http://localhost:8766/public/index.html

## Trocar ou adicionar fotos

1. Coloque a foto nova em `originais/`.
2. Ajuste a lista `FOTOS` em `ferramentas/otimizar-imagens.html`. Cada linha tem o arquivo, o recorte `[x, y, largura, altura]`, a largura final e o destino.
3. Com o servidor rodando, abra http://localhost:8766/ferramentas/otimizar-imagens.html e clique em **Gerar tudo**. As WebP saem em `public/images/`.

Depoimentos: cada cartão em `index.html` tem a foto, o texto e o nome. Mellissa Rossi está sem foto e aparece com as iniciais "MR".

## Medição

Cada clique em botão do WhatsApp envia `clique_whatsapp` (com o local do botão) para o `dataLayer` do Google Tag Manager. Se o Meta Pixel estiver instalado, envia também o evento `Contact`. Sem essas ferramentas instaladas, nada acontece.
