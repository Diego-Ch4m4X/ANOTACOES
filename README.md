# ANOTAÇÕES

![Licença MIT](https://img.shields.io/badge/license-MIT-green.svg)
![Arquitetura local-first](https://img.shields.io/badge/architecture-local--first-2ea44f)
![Arquivos reais](https://img.shields.io/badge/files-.md%20%7C%20.txt-0969da)
![Preview Markdown](https://img.shields.io/badge/preview-Markdown%20%2B%20Mermaid%20%2B%20KaTeX-0969da)
![Foco desktop](https://img.shields.io/badge/focus-desktop-6f42c1)
![Sem backend obrigatório](https://img.shields.io/badge/backend-n%C3%A3o%20obrigat%C3%B3rio-lightgrey)
![Segurança documentada](https://img.shields.io/badge/security-documented-2ea44f)

**ANOTAÇÕES** é um workspace web **local-first** para organizar uma **pasta real do computador** e editar arquivos **`.txt`** e **`.md`** reais pelo navegador, com árvore lateral, abas, busca, preview Markdown avançado, personalização visual e backup/importação em JSON.

## Abra e teste agora 🚀

Acesse a versão publicada em GitHub Pages:

**https://diego-ch4m4x.github.io/ANOTACOES/**

Clique no link acima, abra a página em **Chrome ou Edge no desktop**, escolha uma pasta raiz do seu computador e teste o fluxo real: criar notas, abrir arquivos `.md`, alternar entre editor e preview, usar abas, buscar conteúdo e personalizar a interface. A proposta é simples: transformar uma pasta comum do seu PC em um ambiente visual de anotações, estudo e documentação.

![Prévia da interface do ANOTAÇÕES](./social-preview.png)

> **Nota de segurança:** este projeto manipula arquivos reais da pasta escolhida pelo usuário. Use com uma pasta de teste na primeira execução e faça backup antes de operações grandes de importação, movimentação, renomeação ou exclusão.

---

## Sumário

- [O que é](#o-que-é)
- [Principais recursos](#principais-recursos)
- [Preview Markdown avançado](#preview-markdown-avançado)
- [Como usar no GitHub Pages](#como-usar-no-github-pages)
- [Como usar localmente](#como-usar-localmente)
- [Compatibilidade](#compatibilidade)
- [Privacidade e armazenamento](#privacidade-e-armazenamento)
- [Segurança e hardening](#segurança-e-hardening)
- [Limitações conhecidas](#limitações-conhecidas)
- [Estrutura do repositório](#estrutura-do-repositório)
- [Licença e atribuições](#licença-e-atribuições)

---

## O que é

O **ANOTAÇÕES** não é apenas um editor de texto dentro do navegador. Ele foi desenhado como um **workspace local-first** para trabalhar em cima de uma **pasta raiz real** escolhida pelo usuário.

Na prática, a aplicação permite:

- escolher uma pasta real do computador;
- listar pastas e arquivos compatíveis em uma árvore lateral;
- criar, abrir, editar, renomear, mover e excluir arquivos `.txt` e `.md`;
- trabalhar com várias notas abertas em abas;
- visualizar Markdown renderizado sem abandonar o fluxo local;
- exportar/importar a estrutura em JSON;
- personalizar cores, fontes, tamanhos e opções de exibição.

A ideia central é manter suas anotações em arquivos simples, portáveis e fáceis de versionar, sem obrigar o uso de banco de dados, login, backend ou formato proprietário.

---

## Principais recursos

### Arquivos e pastas reais

- Seleção manual de **pasta raiz** pelo navegador.
- Suporte a arquivos **`.txt`** e **`.md`**.
- Criação de notas e pastas pela interface.
- Renomeação, exclusão e movimentação por botões, atalhos ou menu contextual.
- Atualização da árvore quando arquivos forem modificados fora da página.
- Persistência de ordem manual da árvore por arquivo auxiliar `.anotacoes-order.json` quando necessário.

### Interface de workspace

- Árvore lateral com pastas e arquivos.
- Menu contextual na árvore.
- Abas múltiplas para arquivos abertos.
- Fixação, reordenação e reabertura de abas fechadas.
- Fechamento individual, fechamento das outras abas e fechamento em lote.
- Barra de abas com navegação lateral e opção de quebra em múltiplas linhas.
- Cabeçalho e árvore recolhíveis.
- Indicadores visuais de estado salvo/não salvo.
- Overlay de sincronização para bloquear a interface durante operações longas na pasta raiz.

### Busca e produtividade

- Busca alternável entre **nome** e **nome + conteúdo**.
- Destaque visual de ocorrências.
- Busca dentro de arquivos `.txt` e `.md` lidos da pasta escolhida.
- Atalhos de teclado para salvar, criar nota, criar pasta, renomear, excluir, alternar Markdown, abrir personalização e abrir informações.
- Autosave opcional.
- Botão de voltar ao topo no preview Markdown.

### Personalização visual

O painel **Personalização** permite ajustar a experiência sem editar código:

- fundo e texto da árvore;
- fonte da árvore;
- tamanho da fonte da árvore;
- cor do ícone de pasta;
- cor e espessura das linhas da árvore;
- fundo e texto do editor/preview;
- fonte e tamanho do editor;
- quebra de linha no editor/preview;
- quebra de abas em múltiplas linhas;
- restauração dos valores padrão.

---

## Preview Markdown avançado

O preview Markdown do `index.html` foi atualizado para funcionar como uma área de leitura técnica, não apenas como renderização básica.

Recursos observados no arquivo atual:

| Recurso | Como é usado no projeto |
|---|---|
| `markdown-it` | Parser Markdown principal. |
| HTML nativo no Markdown | Permitido no parser e sanitizado antes de entrar no DOM. |
| DOMPurify | Sanitização do HTML renderizado. |
| highlight.js | Destaque de sintaxe em blocos de código. |
| KaTeX | Renderização de fórmulas matemáticas. |
| Task lists | Suporte a checklists Markdown. |
| Footnotes | Suporte a notas de rodapé. |
| GitHub Alerts | Suporte visual a `> [!NOTE]`, `> [!TIP]`, `> [!IMPORTANT]`, `> [!WARNING]` e `> [!CAUTION]`. |
| `<details>` / `<summary>` | Acabamento visual para blocos expansíveis HTML dentro do Markdown. |
| Mermaid | Renderização local de diagramas em blocos ````mermaid`. |

### Mermaid no preview

O projeto inclui `libs/mermaid.min.js` e renderiza diagramas Mermaid localmente no preview Markdown. O fluxo atual também contém tratamentos específicos para:

- renderização offline via biblioteca local;
- fallback quando a biblioteca não estiver disponível;
- sanitização do SVG gerado;
- ajuste de tamanho para evitar diagramas gigantes/desproporcionais;
- correções visuais em diagramas de estado;
- preservação de personalizações Mermaid como `classDef`, `fill`, `stroke`, `color`, `font-weight` e `font-style`;
- contraste automático quando o diagrama usa preenchimento personalizado sem cor de texto explícita.

---

## Como usar no GitHub Pages

1. Abra: **https://diego-ch4m4x.github.io/ANOTACOES/**
2. Use **Chrome** ou **Edge** no desktop.
3. Clique em **Escolher pasta raiz**.
4. Autorize uma pasta real do computador.
5. Crie ou abra arquivos `.txt` e `.md`.
6. Use **Ctrl+S** para salvar ou ative o **Autosave**.
7. Use **Atualizar árvore** quando alterar arquivos fora da página.
8. Use **Exportar JSON** antes de alterações grandes ou migrações.

> Dica: para testar com segurança, comece por uma pasta nova ou uma cópia de uma pasta real.

---

## Como usar localmente

Você também pode executar o projeto localmente em `localhost`, o que costuma ser mais previsível para testes.

Arquivos auxiliares incluídos:

- `abrir_html_local_shell.bat`
- `abrir_html_local_py.bat`
- `CMD_Leia_abrir-pagina-localmente.txt`

Fluxo sugerido:

1. mantenha `index.html` e a pasta `libs/` no mesmo diretório;
2. execute um servidor local simples ou use um dos `.bat` auxiliares;
3. abra a página em `http://127.0.0.1:PORTA/index.html`;
4. escolha a pasta raiz pela interface.

Abrir diretamente por `file://` pode funcionar parcialmente, mas não é o modo mais confiável para recursos modernos ligados à File System Access API e carregamento de bibliotecas locais.

---

## Compatibilidade

| Ambiente | Situação |
|---|---|
| Chrome desktop | Recomendado. |
| Edge desktop | Recomendado. |
| Brave | Pode funcionar, mas depende das permissões e políticas do navegador. |
| Firefox | Não é recomendado para o fluxo principal de pasta raiz real. |
| Mobile | Não é o foco do projeto. |

O recurso central depende da **File System Access API**, disponível principalmente em navegadores Chromium no desktop.

---

## Privacidade e armazenamento

O conteúdo principal fica em **arquivos reais** dentro da pasta escolhida pelo usuário.

Além disso, o navegador pode armazenar dados auxiliares para melhorar a experiência:

| Local | Uso provável no projeto |
|---|---|
| Arquivos `.txt` / `.md` | Conteúdo principal das anotações. |
| `.anotacoes-order.json` | Ordem manual da árvore em pastas reais. |
| `localStorage` | Preferências de interface e alguns estados visuais. |
| `sessionStorage` | Estados temporários da sessão. |
| `IndexedDB` | Handles da File System Access API para tentar reativar a pasta raiz em sessões futuras, dependendo das permissões do navegador. |

Pontos importantes:

- a pasta raiz precisa ser autorizada pelo usuário;
- o navegador pode pedir confirmação novamente ao reabrir ou reativar a pasta;
- limpar os dados do site no navegador pode remover preferências, sessão e handles armazenados;
- o app não usa backend obrigatório para armazenar suas notas;
- imagens e mídias externas no Markdown podem ser carregadas pelo navegador quando a CSP e o conteúdo permitirem.

---

## Segurança e hardening

Este repositório inclui documentação específica de segurança em [PENTEST-REPORT.md](./PENTEST-REPORT.md).

Medidas e características relevantes observadas no `index.html` atual:

- **CSP via `<meta http-equiv="Content-Security-Policy">`**;
- `connect-src 'none'`, reduzindo conexões ativas iniciadas por APIs como `fetch`;
- scripts locais carregados de `./libs/`;
- script inline principal protegido por `nonce` e hash na política atual;
- bloqueio de atributos inline de script por `script-src-attr 'none'`;
- sanitização do preview Markdown com DOMPurify;
- renderização Mermaid local com sanitização do SVG resultante;
- dependências de Markdown, KaTeX, Mermaid e highlight.js distribuídas localmente;
- ausência de backend obrigatório.

### Ressalvas técnicas importantes

- A CSP é aplicada por **meta tag**, não por header HTTP real.
- Algumas diretivas de segurança, como `frame-ancestors`, só funcionam adequadamente via header HTTP.
- A integração com pasta real usa permissões sensíveis do navegador e pode solicitar acesso de leitura/escrita.
- O código atual contém persistência de handles da File System Access API em IndexedDB para tentativa de reativação, sujeita às regras do navegador.
- Como a aplicação pode renomear, mover, excluir e sobrescrever arquivos reais, o risco operacional depende da pasta escolhida pelo usuário.

---

## Limitações conhecidas

- Depende de suporte do navegador à **File System Access API**.
- Foi pensado para desktop, não para mobile-first.
- O comportamento pode variar entre navegadores Chromium.
- O acesso à pasta raiz depende de autorização manual do usuário.
- Operações de escrita afetam arquivos reais.
- Alterações feitas fora da aplicação podem exigir **Atualizar árvore**.
- A ordem manual da árvore pode criar `.anotacoes-order.json` dentro da pasta real.
- A CSP por meta tag não substitui todos os controles possíveis de um servidor com headers HTTP.
- O preview permite HTML dentro do Markdown, mas depende de sanitização rigorosa para reduzir risco de XSS.

---

## Estrutura do repositório

```text
.
├─ index.html
├─ social-preview.png
├─ README.md
├─ LICENSE
├─ LICENCAS-E-ATRIBUICOES.md
├─ PENTEST-REPORT.md
├─ CMD_Leia_abrir-pagina-localmente.txt
├─ abrir_html_local_py.bat
├─ abrir_html_local_shell.bat
└─ libs/
   ├─ dompurify.min.js
   ├─ emojis.js
   ├─ github-markdown.css
   ├─ highlight.min.css
   ├─ highlight.min.js
   ├─ katex.min.css
   ├─ katex.min.js
   ├─ markdown-it.min.js
   ├─ markdown-it-footnote.min.js
   ├─ markdown-it-katex.min.js
   ├─ markdown-it-task-lists.min.js
   ├─ mermaid.min.js
   └─ fonts/
      └─ KaTeX_*.ttf / .woff / .woff2
```

---

## Licença e atribuições

O código autoral do projeto está licenciado sob a **MIT License**. Veja [LICENSE](./LICENSE).

As bibliotecas, fontes, estilos e ativos de terceiros distribuídos em `libs/` mantêm suas próprias licenças de origem. Veja o inventário em [LICENCAS-E-ATRIBUICOES.md](./LICENCAS-E-ATRIBUICOES.md).

---

## Fechamento

O **ANOTAÇÕES** é uma proposta prática para quem quer unir a simplicidade de arquivos locais com a ergonomia de uma interface web moderna. Ele funciona como editor, organizador e leitor técnico para `.txt` e `.md`, com um diferencial importante: o conteúdo continua em uma pasta real do seu computador. ✨
