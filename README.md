# Porsche Sales Intelligence Dashboard

Dashboard interativo de análise de vendas Porsche, com design inspirado no site oficial da [Porsche Brasil](https://www.porsche.com/brazil/pt/).

---

## Visão Geral

Ferramenta de business intelligence para explorar **100 registros de vendas sanitizadas** de veículos Porsche.  
Permite filtrar, visualizar KPIs, gráficos e insights de modelos populares por cidade e estado.

**Arquivo principal:** [`porsche_sales_dashboard.html`](./porsche_sales_dashboard.html)

---

## Como usar

1. Abra o arquivo `porsche_sales_dashboard.html` em qualquer navegador moderno (Chrome, Firefox, Edge, Safari).
2. Não é necessário servidor — funciona 100% offline (dados embutidos no HTML).
3. Use os filtros no topo e clique em **Aplicar Filtros** para atualizar todos os painéis.

> **Requisito:** conexão com a internet na primeira carga (para carregar Chart.js e a fonte Inter via CDN).

---

## Filtros disponíveis

| Filtro              | Descrição                                      |
|---------------------|------------------------------------------------|
| **Modelo da Porsche** | Ex.: 911 Turbo S, Taycan 4S, Cayenne Coupe…  |
| **Model Year**        | Anos de 2020 a 2026                          |
| **City**              | Cidades dos EUA presentes na base            |
| **Pay Method**        | Wire Transfer, Credit Card, Financing, etc.  |

Botões:
- **Aplicar Filtros** — atualiza KPIs, gráficos, insights e tabela
- **Limpar** — restaura a visão completa (100 registros)

---

## KPIs e indicadores

| KPI                        | O que mostra                                      |
|----------------------------|---------------------------------------------------|
| **Total de Vendas**        | Quantidade de registros no filtro atual           |
| **Receita Total**          | Soma de `SalesPriceSanitized` (USD)               |
| **Ticket Médio**           | Receita ÷ número de vendas                        |
| **Ano de Modelo + Vendido**| Model Year com maior volume de vendas             |

---

## Gráficos e insights

### 1. Vendas por Estado (State)
Gráfico de barras com a quantidade de veículos vendidos por estado.  
**Destaque nos dados:** CA (16) e TX (14) lideram o ranking.

### 2. Top Modelos
Ranking horizontal dos 10 modelos mais vendidos no filtro atual.  
Modelos com maior frequência geral: Macan Electric, Macan T, Panamera, Taycan 4S, Cayenne E-Hybrid, Cayenne Coupe.

### 3. Vendas por Ano de Modelo
Linha temporal da distribuição de Model Year.  
**Pico:** 2024 (29 unidades).

### 4. Principais Modelos por Cidade
Lista das cidades com mais vendas e os modelos mais populares em cada uma — responde diretamente à pergunta de negócio:

> *“Quero insight de carros populares de vendas com base nos dados em cada cidade”*

### 5. Tabela detalhada
Listagem completa com:
- ID da venda
- Modelo e ano
- Preço
- Cidade / Estado
- Método de pagamento
- Status de entrega (com pills coloridas)

---

## Fonte de dados

| Item                    | Valor                                      |
|-------------------------|--------------------------------------------|
| Arquivo original        | `Porsche_Sales_Sanitized.xlsx`             |
| Planilha principal      | `Sanitized Sales`                          |
| Total de registros      | 100                                        |
| Receita total (bruta)   | ~ US$ 12,8 milhões                         |
| Datas inválidas         | 24 registros com `SaleDateSanitized = INVALID` |
| Modelos únicos          | 40                                         |
| Estados únicos          | 33                                         |
| Cidades únicas          | 79                                         |

Colunas utilizadas:
- `PorscheModelSanitized`
- `ModelYearSanitized`
- `SalesPriceSanitized`
- `CitySanitized`
- `StateSanitized`
- `PayMethodSanitized`
- `DeliveryStatusSanitized`
- `sale_id`

---

## Design (UI/UX)

Inspirado no site oficial da Porsche Brasil:

- **Paleta:** fundo preto (`#0A0A0A`), cards `#1A1A1A`, acento vermelho Porsche `#D5001C`
- **Tipografia:** Inter (sans-serif moderna e legível)
- **Layout:** sticky header, cards com borda sutil, hierarquia clara
- **Responsivo:** adapta-se a desktop, tablet e mobile
- **Microinterações:** hover nos filtros, linhas da tabela e botões

---

## Estrutura de arquivos

```
artifacts/
├── porsche_sales_dashboard.html   ← Dashboard completo (abrir no browser)
├── sales_data.json                ← Dados extraídos em JSON (referência)
└── README.md                      ← Este arquivo
```

---

## Tecnologias

- HTML5 + CSS3 (puro)
- JavaScript (vanilla)
- [Chart.js 4.4](https://www.chartjs.org/) — gráficos
- Google Fonts (Inter)

Nenhuma dependência de build ou framework. Abra e use.

---

## Perguntas de negócio respondidas

| Pergunta                                              | Onde encontrar no dashboard                  |
|-------------------------------------------------------|----------------------------------------------|
| Quais os principais modelos vendidos por cidade?      | Card **Principais Modelos por Cidade**       |
| Qual o ano de modelo que mais saiu?                   | KPI **Ano de Modelo + Vendido** + gráfico de linha |
| Insight de carros populares por cidade                | Card de insights + tabela filtrável          |
| Quantidade de vendas por state                        | Gráfico **Vendas por Estado**                |

---

## Observações

- Os dados são **sanitizados** (nomes, datas e valores já tratados).
- Alguns registros possuem data de venda marcada como `INVALID` — não impactam os KPIs de volume e receita.
- Status de entrega incluem variações (Delivered, In Transit, Pending, Cancelled, etc.) e são normalizados visualmente por cores.

---

*Porsche Sales Intelligence · Design inspirado em porsche.com/brazil*
