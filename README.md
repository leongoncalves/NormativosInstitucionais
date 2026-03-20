<img width="1879" height="923" alt="image" src="https://github.com/user-attachments/assets/a6e1426b-612a-4e66-a8f3-007342dbafce" />

# 📋 Repositório de Normativos Institucionais

Página estática em HTML/CSS/JS para consulta centralizada de atos normativos institucionais, com controle de vigência, identificação de normas revogadas e filtros de busca.

* Página exemplificativa, devendo ser adaptada ao contexto e a necessidade. Funções de busca já implementadas.
---

## Por que esta página existe

Órgãos públicos publicam portarias, resoluções e instruções normativas ao longo dos anos. Com o tempo, algumas normas são revogadas ou parcialmente alteradas — mas quem acessa diretamente um documento não tem como saber disso. Não há aviso, não há link para o substituto, não há indicação de que aquela norma não vale mais.

Isso gera um risco real: servidores e cidadãos podem aplicar normas sem validade jurídica em procedimentos administrativos sem perceber.

Esta página resolve esse problema ao reunir **todos os atos normativos em um único lugar**, com status de vigência explícito e referência ao normativo que substituiu cada norma revogada.

A iniciativa decorre de recomendação da **AUDIN — Unidade de Auditoria Interna do IFTO**, formulada em nota de auditoria com fundamento no princípio da eficiência e da segurança jurídica (art. 37 da Constituição Federal e art. 2º da Lei nº 9.784/1999) e nas diretrizes de transparência ativa da Lei de Acesso à Informação (art. 8º da Lei nº 12.527/2011).

---

## O que a página faz

- Lista **todos os atos normativos** — inclusive os já revogados
- Exibe o **status de vigência** de cada norma de forma clara e visual:
  - 🟢 Em vigor
  - 🔴 Revogada — com link para o ato revogador e para a norma substituta
  - 🟡 Alterada parcialmente — com referência ao artigo e ao ato que o alterou
- Permite **busca por texto livre** (número, título, ementa, palavras-chave)
- Oferece **filtros** por tipo de ato, status de vigência e ano
- Exibe **metadados completos** de cada norma: número, tipo, ementa, data de expedição e data de entrada em vigor
- Mostra **estatísticas dinâmicas** (total, em vigor, revogados, tipos distintos) que se atualizam ao filtrar
- Permite **ordenação por coluna** (data, tipo, título)

---

## Estrutura de cada normativo

| Campo | Descrição |
|---|---|
| Data | Data de expedição do ato |
| Tipo | Portaria, Resolução, Instrução Normativa, Orientação Prática, Deliberação etc. |
| Número | Identificador único do ato (ex: `MGI/MF/CGU n. 103/2025`) |
| Título | Nome completo do ato, com link para o documento |
| Ementa | Descrição resumida do objeto da norma |
| Vigência | Data de entrada em vigor |
| Status | Em vigor / Revogada / Alterada parcialmente |
| Revogada por | Link para o ato que revogou ou alterou a norma |

---

## Tecnologia

Página única, sem dependências externas nem back-end. Tudo funciona offline.

```
normativos.html   ← arquivo único, autossuficiente
```

- **HTML5** semântico
- **CSS** puro com variáveis customizadas (suporte a modo escuro automático via `prefers-color-scheme`)
- **JavaScript** vanilla — busca, filtros e ordenação em tempo real, sem bibliotecas
- Fontes carregadas via Google Fonts: `Syne` (display), `Crimson Pro` (corpo), `JetBrains Mono` (metadados e labels)

Para publicar: basta abrir o arquivo `normativos.html` em qualquer navegador, ou hospedar como GitHub Pages, servidor web institucional ou intranet.

---

## Como adicionar novos normativos

Cada normativo é uma linha `<tr>` no `<tbody>` da tabela. Os atributos `data-*` controlam os filtros:

```html
<tr
  data-tipo="portaria"       <!-- portaria | resolucao | instrucao | orientacao | deliberacao -->
  data-status="vigor"        <!-- vigor | revogado | parcial -->
  data-ano="2025"
  data-search="termos para busca livre em minúsculas">

  <td class="td-data">29/dez/25</td>
  <td class="td-tipo"><span class="tipo-pill tipo-portaria">Portaria</span></td>
  <td class="td-titulo">
    <div class="doc-numero">MGI/MF/CGU n. 103/2025</div>
    <a href="URL_DO_DOCUMENTO" class="doc-link">Título completo do ato</a>
  </td>
  <td class="td-ementa">Texto da ementa.</td>
  <td class="td-vigencia">29/12/2025</td>
  <td class="td-status">
    <span class="status-badge badge-vigor">● Em vigor</span>
    <!-- para revogadas, adicionar: -->
    <!-- <div class="revogado-por">Revogada pela <a href="#">Portaria n. xxx</a></div> -->
  </td>
</tr>
```

Para normas **revogadas**, usar `data-status="revogado"` e a classe `revogado` na `<tr>`, e preencher o `<div class="revogado-por">` com link para o ato revogador.

Para normas **parcialmente alteradas**, usar `data-status="parcial"` e o badge `badge-parcial`, indicando qual artigo foi alterado e por qual ato.

---

## Contexto institucional

| | |
|---|---|
| **Instituição** | Instituto Federal de Educação, Ciência e Tecnologia do Tocantins — IFTO |
| **Unidade responsável** | AUDIN — Unidade de Auditoria Interna |
| **Auditora-chefe** | Rosana Sara da Silva Brito |
| **Auditor** | Leonardo Gonçalves Pereira |
| **Fundamento** | Nota de Auditoria AUDIN/IFTO — Achado 2: Ausência de repositório centralizado de atos normativos com controle de vigência |
| **Base legal** | Art. 37 da CF/88 · Art. 2º da Lei nº 9.784/1999 · Art. 8º da Lei nº 12.527/2011 |

---

## Licença

Uso institucional — IFTO. Pode ser adaptado livremente por outras unidades do sistema federal de ensino ou órgãos públicos.
