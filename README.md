# 🍺 Otimização de Estoque e Previsão de Demanda (Cerveja)

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-0.24+-orange.svg)
![Pandas](https://img.shields.io/badge/Pandas-1.2+-green.svg)

## 📌 O Problema de Negócio
No setor de bebidas, a gestão eficiente de estoque é crucial. O excesso de inventário gera custos de armazenagem e risco de vencimento, enquanto a falta (ruptura/stockout) resulta em perda direta de receita e insatisfação do cliente. 

O objetivo deste projeto é prever a demanda diária de consumo de cerveja na cidade de São Paulo, permitindo que a cadeia de suprimentos e a logística ajustem seus estoques de forma proativa com base na previsão climática e no calendário.

## 📊 Principais Descobertas (Visão de Negócios)
Durante a Análise Exploratória de Dados (EDA), desmistificamos alguns sensos comuns do mercado:

1. **O Calor Dita as Regras:** A temperatura máxima diária apresentou uma forte correlação positiva (0.64) com o volume de vendas.
2. **O Peso do Lazer:** Os finais de semana elevam drasticamente o piso de vendas. Os 25% piores dias de venda nos fins de semana ainda superam a maioria dos dias úteis.
3. **O Mito da Chuva:** Ao contrário do esperado, a chuva tem um impacto quase negligenciável nas vendas (correlação de apenas -0.19). Um fim de semana chuvoso ainda gera muito mais receita do que uma terça-feira ensolarada.
4. **Sazonalidade:** O pico de demanda ocorre em Janeiro (alta temporada), enquanto o período de Maio a Julho exige atenção da equipe comercial para evitar ociosidade, marcando o vale de consumo do ano.

## 🤖 Modelagem Preditiva e Machine Learning
Para prever o volume diário em milhares de litros, testamos abordagens de diferentes complexidades:
*   **Regressão Linear Múltipla** (Modelo Baseline interpretável)
*   **Random Forest Regressor** (Modelo Ensemble não-linear)

**O Resultado:** A simplicidade venceu a complexidade. Devido ao tamanho da base de dados (1 ano de operação / 365 registros), modelos complexos como Random Forest sofreram de *overfitting* ao tentar encontrar padrões muito específicos. A **Regressão Linear Múltipla** apresentou a melhor capacidade de generalização para novos dados.

*   **R²:** 0.74 (O modelo consegue explicar 74% da variação na demanda).
*   **Erro Absoluto Médio (MAE):** ~1.98 mil litros. 
> *O que significa ?  O modelo consegue prever a demanda logística de um dia futuro errando, para mais ou para menos, menos de 2 mil litros, garantindo alta eficiência na alocação de caminhões e produção diária.*

## 📂 Estrutura do Projeto
A arquitetura do projeto segue as melhores práticas de Engenharia de Dados e reprodutibilidade:

```text
cerveja-brasil-demanda-mercado/
│
├── data/
│   ├── processed/         # Dados limpos e prontos para modelagem
│   └── raw/               # Dados originais imutáveis
│
├── notebooks/
│   ├── 01_limpeza_sao_paulo.ipynb
│   ├── 02_analise_demanda.ipynb
│   └── 03_modelagem_preditiva.ipynb
│
├── reports/
│   └── figures/           # Gráficos gerados automaticamente pelos scripts
│
├── src/                   # Scripts modulares Python
│
├── .gitignore             # Arquivos ignorados pelo Git
├── PLANEJAMENTO.md        # Documentação de escopo e etapas do projeto
├── requirements.txt       # Dependências de ambiente (reprodutibilidade)
└── README.md              # Este arquivo
```

## 🚀 Como Executar
1. Clone este repositório: `git clone https://github.com/planezio27-ai/cerveja-brasil-demanda-mercado.git`
2. Crie e ative um ambiente virtual.
3. Instale as dependências: `pip install -r requirements.txt`
4. Execute os notebooks sequencialmente na pasta `notebooks/`.

---
*Projeto desenvolvido como parte de um portfólio de Ciência de Dados orientada a negócios. Conecte-se comigo no www.linkedin.com/in/gianluca-planezio-97844a192*
