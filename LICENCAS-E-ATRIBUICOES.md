# Licenças e atribuições

Este documento complementa o [`LICENSE`](./LICENSE).

Ele existe para registrar, de forma prática e objetiva, os **componentes de terceiros distribuídos com o repositório**, suas **licenças de origem** e as observações mais importantes para **redistribuição**.

Em resumo:

- [`LICENSE`](./LICENSE) cobre o **código autoral** do projeto
- este arquivo cobre o **inventário de terceiros** distribuídos com o repositório
- bibliotecas, temas, estilos e ativos de terceiros **mantêm suas licenças originais**
- a licença MIT do projeto **não relicencia automaticamente** arquivos de terceiros

---

## Componentes de terceiros distribuídos

| Componente | Arquivo(s) local(is) | Versão observada | Uso no projeto | Licença informada | Referência pública / origem |
|---|---|---:|---|---|---|
| DOMPurify | `libs/dompurify.min.js` | 3.1.6 | Sanitização do HTML renderizado no preview Markdown | Apache-2.0 / MPL-2.0 | Cure53 / DOMPurify |
| markdown-it | `libs/markdown-it.min.js` | 14.1.0 | Parser Markdown principal | MIT | markdown-it |
| markdown-it-footnote | `libs/markdown-it-footnote.min.js` | 4.0.0 | Suporte a notas de rodapé | MIT | markdown-it-footnote |
| markdown-it-task-lists | `libs/markdown-it-task-lists.min.js` | 2.1.0 | Suporte a task lists | ISC | revin / markdown-it-task-lists |
| markdown-it-katex | `libs/markdown-it-katex.min.js` | não identificado no cabeçalho local | Integração entre Markdown e KaTeX | MIT | waylonflinn / markdown-it-katex |
| KaTeX | `libs/katex.min.js`, `libs/katex.min.css`, `libs/fonts/KaTeX_*` | 0.16.10 | Renderização de fórmulas matemáticas e fontes associadas | MIT | KaTeX |
| highlight.js | `libs/highlight.min.js` | 11.9.0 | Destaque de sintaxe em blocos de código | BSD-3-Clause | highlight.js |
| GitHub Dark theme para highlight.js | `libs/highlight.min.css` | v0.5.0 | Tema visual do syntax highlighting | MIT | GitHub / Primer / highlight theme |
| github-markdown-css | `libs/github-markdown.css` | não identificado no arquivo local | Base visual do preview Markdown | MIT | sindresorhus / github-markdown-css |

---

## Regras práticas de redistribuição

Ao redistribuir este projeto, preserve quando aplicável:

- o arquivo [`LICENSE`](./LICENSE), referente ao **código autoral**
- os avisos e cabeçalhos de licença já presentes nos arquivos minimizados de terceiros
- este inventário, especialmente se a redistribuição incluir `libs/` e ativos relacionados
- as exigências específicas de cada dependência, conforme sua licença de origem

---

## Escopo prático da licença MIT do projeto

De forma prática, a MIT definida em [`LICENSE`](./LICENSE) cobre o **conteúdo autoral deste repositório**, salvo indicação contrária, incluindo por exemplo:

- `index.html`
- `README.md`
- arquivos auxiliares de uso, teste e publicação do repositório
- documentação autoral adicional deste projeto

---

## O que mantém licença própria

As dependências de terceiros distribuídas em `libs/` e seus ativos relacionados **continuam sujeitas às próprias licenças**.

Isso inclui, por exemplo, bibliotecas JavaScript, folhas de estilo, temas visuais e arquivos de fonte. Esses itens **não passam automaticamente a ser MIT** apenas porque o repositório principal usa MIT para o código autoral.

---

## Nota prática sobre o KaTeX

O projeto distribui em conjunto:

- `libs/katex.min.js`
- `libs/katex.min.css`
- arquivos de fonte em `libs/fonts/KaTeX_*`

Esses arquivos foram mantidos juntos para preservar o funcionamento correto da renderização matemática em publicação pública, inclusive em cenários como GitHub Pages, sem exigir ajuste manual de caminhos no CSS.

---

## Resumo objetivo

- **Licença do código autoral:** MIT → [`LICENSE`](./LICENSE)
- **Dependências de terceiros:** mantêm suas licenças originais
- **Função deste arquivo:** inventário, créditos e orientação prática de redistribuição
