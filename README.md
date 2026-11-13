# FileFlow · Intelligent Document Solutions

**Convert. Organize. Simplify.** Sua central inteligente de conversão e gerenciamento de documentos.

Aplicação em arquivo único (`index.html`, HTML + CSS + JavaScript puro, sem framework). Todo o processamento acontece no navegador: nenhum documento é enviado a servidores.

## Ferramentas (16)

| Categoria | Ferramentas |
|---|---|
| Conversão de PDF | PDF para Word (tabelas, colunas, negrito/itálico, OCR) · PDF para JPG · PDF para PNG · Word para PDF |
| Organização de PDF | Juntar · Dividir · Organizar páginas · Girar · Comprimir |
| Conversão de imagens | JPG para PDF · PNG para PDF · PDF para imagem (JPG/PNG/WebP) |
| Segurança e edição | Proteger com senha · Desproteger · Marca d’água · Numerar páginas |

Recursos gerais: pré-visualização antes de baixar, histórico da sessão, encadeamento de operações, arrastar/colar arquivos em qualquer tela, atalhos de teclado (`?`), modo claro/escuro, processamento em segundo plano (Web Worker).

## Publicar no GitHub Pages

1. Envie os arquivos para um repositório.
2. Em **Settings → Pages**, selecione a branch `main` e a pasta `/ (root)`.
3. Edite as tags `og:image` e `twitter:image` no `<head>` do `index.html` com a URL absoluta da imagem, por exemplo `https://SEU-USUARIO.github.io/fileflow/og-image.png`. Isso garante a prévia ao compartilhar o link no WhatsApp e no LinkedIn.

## Testes automáticos

```bash
npm install
npx playwright install chromium
npm run check   # valida a sintaxe do JavaScript do index.html
npm test        # 24 testes ponta a ponta, uma ou mais por ferramenta
```

O workflow `.github/workflows/tests.yml` roda os mesmos testes a cada push e pull request. Os arquivos de exemplo ficam em `tests/fixtures/`.

Sem acesso às CDNs (rede corporativa restrita), os testes podem usar as bibliotecas do `node_modules`:
`LOCAL_LIBS=/caminho/para/node_modules npm test` (instale antes `pdfjs-dist@3.11.174 docx-preview@0.3.3 html2canvas@1.4.1 tesseract.js@5.1.1 @tesseract.js-data/por`).

## Bibliotecas (carregadas sob demanda via CDN)

pdf.js 3.11 · @cantoo/pdf-lib 2.11 (pdf-lib com criptografia) · JSZip 3.10 · docx-preview 0.3 · html2canvas 1.4 · Tesseract.js 5.1 (OCR em português).

## Identidade visual

Logotipos, ícone do app e favicon ficam em `assets/marca/`. Cores principais: `#142B45` · `#2878D0` · `#55B5F5` · `#FFFFFF` · `#F4F7FB` · `#718096`.

Versão `2026.11.13B`.
