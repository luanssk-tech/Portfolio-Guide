# 🗺️ Portfólio de Dados · Luan

Analista de Dados focado em transformar dados públicos em **respostas para perguntas de negócio**, com SQL, Python e visualização. Cada projeto abaixo parte de uma pergunta, testa hipóteses com estatística e termina em **recomendações acionáveis**.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-luanssk-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/luanssk/)
[![GitHub](https://img.shields.io/badge/GitHub-luanssk--tech-181717?logo=github&logoColor=white)](https://github.com/luanssk-tech)

![SQL](https://img.shields.io/badge/SQL-PostgreSQL%20%7C%20DuckDB-336791?logo=postgresql&logoColor=white)
![Python](https://img.shields.io/badge/Python-pandas%20%7C%20statsmodels%20%7C%20scipy-3776AB?logo=python&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?logo=powerbi&logoColor=black)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?logo=streamlit&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?logo=pytest&logoColor=white)

---

## 📚 Sumário

- [Projetos em destaque](#-projetos-em-destaque)
- [Projetos por ferramenta](#-projetos-por-ferramenta)
- [Competências demonstradas](#-competências-demonstradas)
- [Como eu trabalho](#-como-eu-trabalho)
- [Contato](#-contato)

---

## ⭐ Projetos em destaque

### ⛽ [Foguete e Pena: o reajuste da Petrobras chega à bomba?](https://github.com/luanssk-tech/fuel-price-passthrough-br)

<a href="https://github.com/luanssk-tech/fuel-price-passthrough-br"><img src="https://raw.githubusercontent.com/luanssk-tech/fuel-price-passthrough-br/main/images/06_repasse_acumulado.png" width="720" alt="Repasse acumulado de altas e reduções"></a>

**Pergunta:** quando o preço de distribuição do combustível muda, quanto e em quanto tempo isso chega ao preço da bomba? O preço sobe como foguete e desce como pena?

**Resultado:** sim, principalmente no diesel. Na mesma semana, **81% de uma alta** chega à bomba contra só **22% de uma redução**. Reduções levam ~6 semanas para chegar a 90%. Para um caminhão que roda 700 L por semana, isso custa **~R$ 209 a cada redução de R$ 0,10/L**.

| | |
|---|---|
| **Dados** | ANP (dados abertos), ~700 semanas (2013–2026), 27 UFs, ~160 mil linhas |
| **Stack** | Python, DuckDB + SQL (raw → staging → marts), statsmodels, scipy, pytest, Streamlit, Plotly |
| **Destaques** | Modelo de defasagens distribuídas em painel validado com Monte Carlo · estudo de eventos · 5 testes de robustez · **40 testes automatizados** · coleta com hash SHA-256 |
| **Links** | [Repositório](https://github.com/luanssk-tech/fuel-price-passthrough-br) · [🔗 Dashboard interativo](https://fuel-price-passthrough-br.streamlit.app/) |

---

### 📦 [Impacto do atraso na entrega na satisfação dos clientes (Olist)](https://github.com/luanssk-tech/olist-delivery-insights)

<a href="https://github.com/luanssk-tech/olist-delivery-insights"><img src="https://raw.githubusercontent.com/luanssk-tech/olist-delivery-insights/main/images/powerbi_pagina1.png" width="720" alt="Painel Power BI do projeto Olist"></a>

**Pergunta:** o atraso na entrega dos pedidos derruba a nota de avaliação dada pelos clientes?

**Resultado:** sim. Pedidos no prazo têm nota média **4,29**; os atrasados, **2,57** (IC 95% da diferença: 1,69 a 1,77). A nota despenca entre 3 e 7 dias de atraso, e só 8% dos pedidos atrasados respondem por **37,9% das notas 1**. Atraso se concentra em MA, CE, BA e RJ.

| | |
|---|---|
| **Dados** | Olist (Kaggle), 99.441 pedidos (2016–2018), 95.801 após limpeza documentada |
| **Stack** | PostgreSQL, Python (pandas, scipy), Power BI |
| **Destaques** | Funil de limpeza regra a regra · Mann-Whitney, Spearman e bootstrap · números do Power BI conferidos contra a EDA em Python |
| **Links** | [Repositório](https://github.com/luanssk-tech/olist-delivery-insights) |

---

## 🧰 Projetos por ferramenta

### SQL

| Projeto | Data | Área de análise | O que foi feito em SQL |
|---|---|---|---|
| ⛽ [Foguete e Pena](https://github.com/luanssk-tech/fuel-price-passthrough-br) | Nov 2026 | Modelagem de dados, qualidade de dados | Modelo em camadas no DuckDB (raw → staging → marts), de-para versionado, `LAG` só entre semanas consecutivas, `FULL JOIN` para cobrir lacunas da ANP e flags de qualidade sem apagar dados |
| 📦 [Olist](https://github.com/luanssk-tech/olist-delivery-insights) | Nov 2026 | Exploração e integridade de dados | Carga de 9 tabelas no PostgreSQL e verificação de volumetria, nulos, duplicidades, chaves órfãs e consistência de datas |

### Python

| Projeto | Área | Descrição | Bibliotecas |
|---|---|---|---|
| ⛽ [Foguete e Pena](https://github.com/luanssk-tech/fuel-price-passthrough-br) | Econometria, séries temporais, engenharia de dados | Coleta automatizada, modelo assimétrico em painel com erros agrupados por UF e semana, estudo de eventos e testes automatizados de ponta a ponta | pandas, statsmodels, scipy, requests, matplotlib, pytest |
| 📦 [Olist](https://github.com/luanssk-tech/olist-delivery-insights) | Limpeza de dados, EDA, testes de hipótese | Limpeza com `assert` de integridade, criação de faixas de atraso e testes não paramétricos (a nota é ordinal) | pandas, scipy, matplotlib |

### Visualização e dashboards

| Projeto | Descrição | Dashboard |
|---|---|---|
| ⛽ [Foguete e Pena](https://github.com/luanssk-tech/fuel-price-passthrough-br) | App com curva de repasse por combustível e estado, preços e margem, ranking das UFs e calculadora de "quanto isso me custa" | [Streamlit](https://fuel-price-passthrough-br.streamlit.app/) |
| 📦 [Olist](https://github.com/luanssk-tech/olist-delivery-insights) | Painel com 2 páginas: KPIs e nota por faixa de atraso; evolução mensal e % de atraso por estado | [Power BI (.pbix)](https://github.com/luanssk-tech/olist-delivery-insights/tree/main/powerbi) |

---

## 🎯 Competências demonstradas

| Competência | ⛽ Foguete e Pena | 📦 Olist |
|---|:---:|:---:|
| Pergunta de negócio e hipóteses | ✅ | ✅ |
| SQL (exploração, joins, window functions) | ✅ | ✅ |
| Modelagem de dados em camadas | ✅ | |
| Limpeza e qualidade de dados documentadas | ✅ | ✅ |
| Estatística inferencial (testes, IC, bootstrap) | ✅ | ✅ |
| Econometria / séries temporais | ✅ | |
| Testes automatizados (pytest) | ✅ | |
| Dashboard | Streamlit (publicado) | Power BI |
| Recomendações de negócio | ✅ | ✅ |
| Limitações e próximos passos | ✅ | ✅ |

---

## 🧭 Como eu trabalho

1. **Começo pela pergunta**, não pela ferramenta: qual decisão o resultado vai apoiar?
2. **Documento cada regra de limpeza** com quantas linhas ela remove, para que qualquer pessoa consiga auditar os números.
3. **Valido antes de concluir:** confiro resultados entre etapas (SQL × Python × dashboard) e testo o método em dados simulados.
4. **Separo associação de causa** e deixo claras as limitações.
5. **Termino em recomendação:** para quem é, o que fazer e em qual número ela se apoia.

---

## 📫 Contato

**Luan** · Analista de Dados
[LinkedIn](https://www.linkedin.com/in/luanssk/) · [GitHub](https://github.com/luanssk-tech)
