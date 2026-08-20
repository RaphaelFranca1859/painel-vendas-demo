# 📊 Painel de Acompanhamento de Vendas

Painel interativo de acompanhamento de vendas para equipes de campo (RCAs), construído como uma **única página HTML autossuficiente** — sem backend, sem build, sem dependências de servidor. Basta abrir o arquivo no navegador.

> ⚠️ **Dados fictícios.** Este repositório usa um conjunto de dados sintético (nomes, códigos e valores de venda inventados) apenas para demonstração. A versão em produção lê planilhas reais exportadas de um sistema de BI interno.

## 🖥️ Demonstração

Abra o arquivo [`index.html`](./index.html) diretamente no navegador, ou acesse a versão publicada via GitHub Pages (se habilitado nas configurações do repositório).

## ✨ Funcionalidades

- **5 visões em abas**: Gerência, Supervisores, RCAs, Zerados (sem venda no dia) e Parcial (formato de envio para WhatsApp).
- **Gráficos dinâmicos** (Chart.js) de necessidade do dia vs. vendido e % da meta batida, por gerência.
- **Filtro por gerência** que recalcula tabela, gráficos e os cards do topo em tempo real.
- **Upload de planilhas** exportadas do sistema de BI (Detalhamento por RCA + Visão Mensal) — parsing client-side de arquivos `.xls`/XML (SpreadsheetML) e HTML tables, sem enviar nada para nenhum servidor.
- **Campos editáveis e persistentes**: Previsão do dia, Meta SKU, Meta Positivação e Positivação manual, salvos no `localStorage` do navegador por dia de referência — sobrevivem a novos uploads de vendas no mesmo dia.
- **Upload em lote da Previsão do dia** via planilha modelo (uma aba por supervisor).
- **Gestão de equipe**: incluir vendedor novo ou excluir temporariamente um RCA do painel, com recômputo automático de todos os agregados.
- **Exportação em imagem** (PNG) de qualquer bloco ou tabela via `html2canvas`, prontos para compartilhar em grupos de WhatsApp.
- **Destaque visual automático** para vendedores sem venda no dia.

## 🛠️ Tecnologias

- HTML + CSS + JavaScript puro (sem framework)
- [Chart.js](https://www.chartjs.org/) — gráficos
- [html2canvas](https://html2canvas.hertzen.com/) — exportação de imagens
- `localStorage` — persistência de edições manuais no navegador

## 📁 Estrutura de dados esperada

O painel espera planilhas exportadas no formato usado pelo BI de origem:

| Arquivo | Conteúdo |
|---|---|
| Detalhamento por RCA | Situação, Supervisor, RCA, metas e vendas do dia, positivação, SKU/PDV |
| Visão Mensal (opcional) | Médias e indicadores do mês por RCA |
| Previsão do dia (opcional) | Uma aba por supervisor, colunas `Vendedor` e `Previsão do Dia` |

Todos os nomes de gerência, supervisor e RCA são lidos dinamicamente dos arquivos — nada é fixo no código.

## 🚀 Como usar

1. Abra `index.html` no navegador (ou publique via GitHub Pages).
2. Clique em **"Carregar dados"** no topo e envie a planilha de Detalhamento do dia (e opcionalmente a Visão Mensal).
3. Edite Previsão, Meta SKU, Meta Positivação e Positivação diretamente nas tabelas — as edições ficam salvas no navegador.
4. Use os filtros de busca em cada aba e o filtro de gerência para recortar a visão.
5. Baixe imagens de qualquer bloco para compartilhar.

## 👤 Autor

Desenvolvido por **Raphael França**.
