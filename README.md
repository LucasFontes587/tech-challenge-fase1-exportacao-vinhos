# 🍷 Tech Challenge — Fase 1 | Pós Tech Data Analytics FIAP

> Análise estratégica das exportações de vinhos brasileiros para apoio à tomada de decisão de investimento.

---

## 📌 Contexto

Este projeto foi desenvolvido como **Tech Challenge da Fase 1** da Pós-Graduação em **Data Analytics** da FIAP (Pós Tech), em parceria com a Alura.

O desafio simula um cenário real: atuando como Analistas de Dados de uma grande vinícola, o objetivo foi analisar o histórico de exportações de vinhos do Brasil (dados da **Embrapa**) nos últimos **15 anos (2009–2023)** para identificar padrões, oportunidades e riscos — e fundamentar a alocação estratégica de capital.

**Perguntas centrais do projeto:**
1. Como evoluiu o faturamento das exportações ao longo do tempo?
2. Quem são os maiores clientes e qual o valor agregado de cada mercado?
3. Qual a estratégia recomendada para o futuro?

---

## 🗂️ Base de Dados

- **Fonte:** Embrapa — dados de exportação vitivinícola do Rio Grande do Sul
- **Arquivo:** `Exportacao.csv`
- **Período:** 2009 a 2023
- **Granularidade:** Volume (Kg) e Valor (US$) por país de destino, por ano

### Desafio estrutural dos dados
O CSV original apresentava os anos distribuídos em colunas (formato "largo"), com colunas duplicadas misturando Quantidade (Kg) e Valor (US$). A limpeza exigiu:
- Identificação de colunas duplicadas (sufixo `.1` para colunas de valor)
- Uso do `melt` para transformar colunas em linhas (formato "longo")
- Merge das bases de quantidade e valor
- Filtro dos últimos 15 anos e remoção de registros sem exportação

---

## 🔍 Metodologia

A abordagem foi **quantitativa e exploratória**, estruturada em etapas:

1. **Extração e Limpeza** — reestruturação do dataset do formato largo para longo, merge das bases de quantidade e valor, conversão Kg → Litros e cálculo do preço médio por litro
2. **Panorama Geral** — análise da série temporal de faturamento, volume, variação anual (%) e preço médio por litro
3. **Análise por País** — ranking dos Top 15 mercados por faturamento, com colormap de valor agregado (US$/L)
4. **Análise Detalhada** — drill-down individual por país (ex: Paraguai) com gráfico de eixo duplo (volume + faturamento)
5. **Segmentação de Mercados** — classificação dos destinos em 3 segmentos por preço médio:
   - 🔵 **Econômico** — abaixo de US$ 1,50/L
   - 🟡 **Médio** — entre US$ 1,50 e US$ 3,00/L
   - 🟢 **Premium** — acima de US$ 3,00/L
6. **Conclusões e Recomendações** — relatório executivo gerado programaticamente com as métricas consolidadas

---

## 📊 Principais Resultados

| Indicador | Valor |
|-----------|-------|
| Faturamento Total (15 anos) | ~US$ 93M |
| Volume Total | ~55M litros |
| Preço Médio Global | ~US$ 1,70/L |
| Países atendidos | 121+ |
| Participação do Paraguai | ~28,5% do faturamento |

### Mercados por valor agregado (US$/L)
| País | Valor Agregado | Segmento |
|------|---------------|----------|
| Japão | US$ 7,93 | 🟢 Premium |
| China | US$ 5,10 | 🟢 Premium |
| Reino Unido | US$ 4,15 | 🟢 Premium |
| EUA | US$ 2,81 | 🟡 Médio |
| Paraguai | US$ 1,63 | 🔵 Econômico |

---

## 🧭 Recomendações Estratégicas

- **Mercado interno**: maior potencial imediato — consumo per capita de apenas 1,66 L/hab vs. 40 L/hab na Europa
- **China**: market share crescendo +4.104%, classe média em expansão e relação BRICS favorável — maior ROI de longo prazo
- **Reino Unido**: 2º maior importador global com 96,7% de dependência de importações — forte oportunidade pós-Brexit
- **Japão**: monitorar como mercado de médio prazo (3–5 anos) — retração pós-pandemia reversível com alto valor agregado
- **Rússia**: excluída no curto-médio prazo por barreiras geopolíticas e sanções

---

## 🛠️ Tecnologias Utilizadas

| Categoria | Ferramentas |
|-----------|------------|
| Linguagem | Python 3 |
| Manipulação de dados | Pandas, NumPy |
| Visualização | Plotly Express, Plotly Graph Objects, Matplotlib, Seaborn |
| Ambiente | Google Colab |
| Versionamento | Git / GitHub |

---

## 📁 Estrutura do Repositório

```
├── Análise_de_importações_de_vinho_postech.ipynb   # Notebook principal
├── Exportacao.csv                                   # Base de dados (Embrapa)
└── README.md
```

---

## 👥 Equipe

> *Adicione os nomes e links do LinkedIn dos integrantes do grupo aqui*

| Nome | LinkedIn |
|------|----------|
| Lucas Fontes Culatrelli | [🔗 Perfil](#) |
| Integrante 2 | [🔗 Perfil](#) |
| Integrante 3 | [🔗 Perfil](#) |

---

## 📚 Referências

- Embrapa Uva e Vinho — Base de dados de exportações vitivinícolas do RS
- OIV — Organisation Internationale de la Vigne et du Vin (Relatório 2024)
- ComexStat / MDIC — Dados complementares de comércio exterior brasileiro

---

> Projeto desenvolvido para fins acadêmicos na **Pós Tech Data Analytics — FIAP + Alura**
