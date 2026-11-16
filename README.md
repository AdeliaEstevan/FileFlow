# FileFlow · Intelligent Document Solutions

**Convert. Organize. Simplify.** Sua central inteligente de conversão e gerenciamento de documentos.

Aplicação em arquivo único (`index.html`, HTML + CSS + JavaScript puro, sem framework). Todo o processamento acontece no navegador: nenhum documento é enviado a servidores.

## Ferramentas (17)

| Categoria | Ferramentas |
|---|---|
| Conversão de PDF | PDF para Word (imagens, listas, tabelas, colunas, negrito/itálico, remoção de cabeçalhos/rodapés, OCR) · PDF para JPG · PDF para PNG · Word para PDF (pesquisável) |
| Organização de PDF | Juntar · Dividir · Organizar páginas · Girar · Comprimir |
| Conversão de imagens | JPG para PDF · PNG para PDF · PDF para imagem (JPG/PNG/WebP) |
| Segurança e edição | Proteger com senha · Desproteger · Assinar PDF (desenhar, digitar ou imagem) · Marca d’água · Numerar páginas |

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
npm test        # 29 testes × 3 navegadores (Chromium, Firefox e WebKit/Safari)
npx playwright test --project=firefox   # apenas um navegador
```

O workflow `.github/workflows/tests.yml` roda os mesmos testes a cada push e pull request, em paralelo nos três navegadores. Os arquivos de exemplo ficam em `tests/fixtures/`.

Diferenças entre navegadores já tratadas no código:
- Safari não gera imagens WebP pelo canvas: a opção aparece desabilitada, com aviso.
- Safari limita a área de cada canvas (~16,7 milhões de pixels) e o Chrome/Firefox, a altura (32.767 px): renderizações grandes são reduzidas ou feitas em blocos.
- Sem `OffscreenCanvas` no worker (Safari antigo), a compressão roda no thread principal.
- Em aba oculta o processamento continua (não depende de `requestAnimationFrame`).

Sem acesso às CDNs (rede corporativa restrita), os testes podem usar as bibliotecas do `node_modules`:
`LOCAL_LIBS=/caminho/para/node_modules npm test` (instale antes `jszip@3.10.1`, `pdfjs-dist@3.11.174 docx-preview@0.3.3 html2canvas@1.4.1 tesseract.js@5.1.1 @tesseract.js-data/por`).

## Bibliotecas (carregadas sob demanda via CDN)

pdf.js 3.11 · @cantoo/pdf-lib 2.11 (pdf-lib com criptografia) · JSZip 3.10 · docx-preview 0.3 · html2canvas 1.4 · Tesseract.js 5.1 (OCR em português).

## Identidade visual

Logotipos, ícone do app e favicon ficam em `assets/marca/`. Cores principais: `#142B45` · `#2878D0` · `#55B5F5` · `#FFFFFF` · `#F4F7FB` · `#718096`.

Versão `2026.11.16A`.
