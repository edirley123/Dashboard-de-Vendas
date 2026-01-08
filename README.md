# Desafio Dashboard de Vendas (Excel)

Resumo
-------
Este repositório contém a solução do desafio: um dashboard de vendas criado no Microsoft Excel. O objetivo é transformar dados brutos em visualizações claras que permitam analisar desempenho de vendas e apoiar decisões.

O que está neste repositório
----------------------------
- `base.xlsx` — Base de dados original (dados brutos).
- `dashboard_xbox_finalizado.xlsx` — Arquivo Excel com o dashboard finalizado.
- `README.md` — Este documento, com instruções de reprodução e detalhes do projeto.

Objetivo do Dashboard
---------------------
- Apresentar KPIs essenciais (Receita, Quantidade vendida, Ticket médio, Margem, etc.).
- Visualizar vendas por período, região, produto e canal.
- Permitir filtragem rápida (slicers) e análise exploratória com PivotTables e gráficos interativos.
- Entregar visualizações limpas e acionáveis para suporte à tomada de decisão.

Dados (base.xlsx)
-----------------
- Estrutura esperada (colunas principais):
  - Data (YYYY-MM-DD)
  - PedidoID
  - ClienteID
  - Produto / SKU / Categoria
  - Região / Estado / Cidade
  - Quantidade
  - Preço unitário
  - Receita (Quantidade * Preço)
  - Custo (se disponível)
  - Canal de Venda (loja, e-commerce, parceiro, etc.)
- Observação: caso a estrutura da sua `base.xlsx` seja diferente, faça o mapeamento das colunas antes de seguir.

Como reproduzir o dashboard (passo a passo)
-------------------------------------------
1. Preparar os dados
   - Abra `base.xlsx`.
   - Use o Power Query (Dados → Obter & Transformar) para:
     - Remover colunas desnecessárias.
     - Corrigir tipos (datas, numéricos).
     - Tratar duplicados e valores nulos.
     - Criar colunas calculadas (ex.: Receita = Quantidade * Preço unitário).
   - Carregue a tabela tratada como Tabela do Excel (por exemplo, `tblVendas`).

2. Modelo e medidas (opcional: Power Pivot / Data Model)
   - Se os dados estão em várias tabelas (Produtos, Clientes, Vendas), importe tudo para o Modelo de Dados.
   - Crie medidas com DAX (se usar Power Pivot). Exemplo de medidas:
     - Total Receita = SUM(tblVendas[Receita])
     - Total Quantidade = SUM(tblVendas[Quantidade])
     - Ticket Médio = [Total Receita] / [Total Quantidade]
     - Margem (%) = DIVIDE(SUM(tblVendas[Receita] - tblVendas[Custo]), SUM(tblVendas[Receita]))

3. PivotTables e gráficos
   - Crie PivotTables a partir da tabela/modelo:
     - Vendas por mês/ano (e linha do tempo).
     - Vendas por produto/categoria.
     - Vendas por região/cidade.
     - Top N produtos (use filtros ou Rank em Power Query/DAX).
   - A partir das PivotTables, crie gráficos (colunas, linhas, combo, donut/pie para participação).
   - Use segmentações (slicers) para filtros por período, categoria, região, canal.

4. KPIs e cartões
   - Crie caixas com as principais métricas (Total Receita, Cresc. MoM, Ticket Médio).
   - Use fórmulas ou medidas para calcular variações (% variação mês a mês / ano a ano).
   - Destaque os valores com formatação condicional (cores, setas).

5. Interatividade e polimento
   - Conecte os slicers às PivotTables/Gráficos (Ferramentas -> Relacionar Slicers).
   - Use segmentador de tempo (Timeline) para filtrar por períodos.
   - Ajuste cores, rótulos e títulos para clareza.
   - Proteja células com fórmulas se for necessário enviar o arquivo.
