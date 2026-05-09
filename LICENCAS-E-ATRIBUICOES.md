# Licenças e atribuições

Este documento complementa o arquivo [`LICENSE`](./LICENSE).

Ele registra, de forma prática, os **componentes de terceiros distribuídos com o repositório**, seus usos dentro do projeto e observações relevantes para redistribuição.

Em resumo:

- [`LICENSE`](./LICENSE) cobre o **código autoral** do projeto;
- este arquivo cobre o **inventário de bibliotecas, estilos, fontes e ativos de terceiros**;
- dependências de terceiros **mantêm suas próprias licenças**;
- a licença MIT do projeto **não relicencia automaticamente** arquivos de terceiros.

---

## Componentes de terceiros distribuídos

| Componente | Arquivo(s) local(is) | Versão observada | Uso no projeto | Licença informada / esperada | Observação |
|---|---|---:|---|---|---|
| DOMPurify | `libs/dompurify.min.js` | 3.1.6 | Sanitização do HTML renderizado no preview Markdown e do SVG gerado por Mermaid | Apache-2.0 / MPL-2.0 | O cabeçalho local informa a licença. |
| markdown-it | `libs/markdown-it.min.js` | 14.1.0 | Parser Markdown principal | MIT | O cabeçalho local informa a licença. |
| markdown-it-footnote | `libs/markdown-it-footnote.min.js` | 4.0.0 | Suporte a notas de rodapé | MIT | O cabeçalho local informa a licença. |
| markdown-it-task-lists | `libs/markdown-it-task-lists.min.js` | 2.1.0 | Suporte a task lists/checklists | ISC | O cabeçalho local informa a licença. |
| markdown-it-katex | `libs/markdown-it-katex.min.js` | não identificada no cabeçalho local | Integração entre Markdown e KaTeX | MIT | Manter a referência do projeto original ao redistribuir. |
| KaTeX | `libs/katex.min.js`, `libs/katex.min.css`, `libs/fonts/KaTeX_*` | 0.16.10 | Renderização de fórmulas matemáticas e fontes associadas | MIT | Os arquivos de fonte fazem parte do funcionamento correto do CSS do KaTeX. |
| highlight.js | `libs/highlight.min.js` | 11.9.0 | Destaque de sintaxe em blocos de código | BSD-3-Clause | O cabeçalho local informa a licença. |
| Tema GitHub Dark para highlight.js | `libs/highlight.min.css` | 0.5.0 | Tema visual para syntax highlighting | MIT | O cabeçalho local informa a licença. |
| github-markdown-css | `libs/github-markdown.css` | não identificada no cabeçalho local | Base visual do preview Markdown | MIT | Manter a referência do projeto original ao redistribuir. |
| Mermaid | `libs/mermaid.min.js` | 10.9.3 | Renderização local de diagramas Mermaid no preview Markdown | MIT | O arquivo minificado não traz cabeçalho de licença completo; preservar a atribuição do projeto Mermaid. |
| Mapa local de emojis | `libs/emojis.js` | arquivo local do projeto | Dicionário offline de shortcodes de emoji | verificar origem antes de redistribuição isolada | O arquivo funciona como fallback/local map para evitar dependência remota no app. |
| Prévia social | `social-preview.png` | ativo do repositório | Imagem de preview do projeto | autoral do projeto, salvo indicação contrária | Usada no README e metadados sociais. |

---

## Arquivos autorais do projeto

A licença MIT definida em [`LICENSE`](./LICENSE) cobre o conteúdo autoral deste repositório, salvo indicação contrária, incluindo:

- `index.html`;
- `README.md`;
- `PENTEST-REPORT.md`;
- `LICENCAS-E-ATRIBUICOES.md`;
- `CMD_Leia_abrir-pagina-localmente.txt`;
- `abrir_html_local_py.bat`;
- `abrir_html_local_shell.bat`;
- demais textos, scripts auxiliares e documentação autoral do repositório.

---

## Observações sobre bibliotecas locais

O projeto distribui as dependências em `./libs/` para reduzir dependência de CDN e permitir uma experiência mais previsível em GitHub Pages ou execução local.

Isso inclui:

- parser Markdown;
- sanitizador HTML;
- renderizador matemático;
- renderizador de diagramas;
- tema visual de Markdown;
- syntax highlighting;
- fontes do KaTeX.

Ao atualizar qualquer biblioteca, revise também:

1. licença do novo arquivo;
2. cabeçalho mantido no arquivo minificado;
3. compatibilidade com a CSP atual;
4. caminhos relativos de CSS, JS e fontes;
5. impacto no preview Markdown, KaTeX e Mermaid.

---

## Nota prática sobre KaTeX

O projeto distribui em conjunto:

- `libs/katex.min.js`;
- `libs/katex.min.css`;
- `libs/fonts/KaTeX_*`.

Esses arquivos devem permanecer juntos, porque o CSS do KaTeX referencia as fontes por caminho relativo. Remover ou mover a pasta `fonts/` pode quebrar a renderização matemática.

---

## Nota prática sobre Mermaid

O projeto distribui `libs/mermaid.min.js` para renderizar diagramas Mermaid dentro do preview Markdown sem depender de CDN.

Ao redistribuir ou atualizar essa biblioteca:

- preserve a atribuição ao projeto Mermaid;
- confirme a licença da versão usada;
- teste diagramas reais no preview;
- valide se o SVG gerado continua compatível com DOMPurify e com a CSP do projeto.

---

## Regras práticas de redistribuição

Ao redistribuir este projeto, preserve quando aplicável:

- o arquivo [`LICENSE`](./LICENSE), referente ao código autoral;
- este inventário de licenças e atribuições;
- os cabeçalhos de licença existentes nos arquivos de terceiros;
- a estrutura `libs/`, especialmente quando o funcionamento offline/local depender dela;
- as exigências específicas de cada dependência de terceiros.

---

## Resumo objetivo

- **Código autoral:** MIT, conforme [`LICENSE`](./LICENSE).
- **Dependências de terceiros:** mantêm suas licenças originais.
- **Função deste arquivo:** inventário, créditos, cautelas de redistribuição e rastreabilidade das bibliotecas locais.
