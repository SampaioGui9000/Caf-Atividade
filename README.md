# Health&Life Analytics — Café, Sono e Saúde

## Sobre o projeto

Este projeto foi desenvolvido como parte de um estudo de **Ciência de Dados**, com o objetivo de analisar a relação entre **consumo de café, qualidade do sono e hábitos de saúde**.

A análise utiliza um dataset sintético com **10.000 registros**, buscando:

* Explorar o perfil dos clientes;
* Investigar a relação entre consumo de café e horas de sono;
* Analisar fatores relacionados à qualidade do sono;
* Criar visualizações para identificar padrões;
* Construir modelos de classificação capazes de prever a `Sleep_Quality`;
* Comparar diferentes algoritmos de Machine Learning;
* Identificar e evitar possíveis problemas de **vazamento de dados (data leakage)**;
* Gerar recomendações que possam apoiar decisões de negócio.

---

## Objetivos

### Objetivo geral

Investigar os fatores relacionados à qualidade do sono e avaliar se hábitos de vida podem ser utilizados para prever a variável `Sleep_Quality`.

### Objetivos específicos

1. Realizar uma análise exploratória dos dados (EDA);
2. Identificar valores nulos, duplicados e possíveis inconsistências;
3. Analisar variáveis numéricas e categóricas;
4. Investigar a relação entre consumo de café e sono;
5. Comparar diferentes grupos de clientes;
6. Criar novas variáveis para melhorar a modelagem;
7. Treinar diferentes modelos de classificação;
8. Avaliar o desempenho dos modelos;
9. Identificar possíveis vazamentos de dados;
10. Selecionar e salvar o modelo de melhor desempenho.

---

## 📊 Dataset

O projeto utiliza o arquivo:

```text
synthetic_coffee_health_10000.csv
```

O dataset possui:

* **10.000 registros**
* **16 variáveis originais**

Entre as principais variáveis estão:

| Variável                  | Descrição                    |
| ------------------------- | ---------------------------- |
| `ID`                      | Identificador do registro    |
| `Age`                     | Idade                        |
| `Gender`                  | Gênero                       |
| `Country`                 | País                         |
| `Coffee_Intake`           | Consumo de café              |
| `Caffeine_mg`             | Consumo estimado de cafeína  |
| `Sleep_Hours`             | Horas de sono                |
| `Sleep_Quality`           | Qualidade do sono            |
| `Stress_Level`            | Nível de estresse            |
| `Health_Issues`           | Problemas de saúde relatados |
| `Occupation`              | Ocupação                     |
| `Smoking`                 | Indicador de tabagismo       |
| `Alcohol_Consumption`     | Consumo de álcool            |
| `BMI`                     | Índice de massa corporal     |
| `Heart_Rate`              | Frequência cardíaca          |
| `Physical_Activity_Hours` | Horas de atividade física    |

> O dataset utilizado no projeto é sintético.

---

## Tecnologias utilizadas

O projeto foi desenvolvido utilizando **Python** e pode ser executado em **Jupyter Notebook** ou **Google Colab**.
### Bibliotecas
```text
pandas
numpy
matplotlib
seaborn
scikit-learn
joblib
```
### Principais ferramentas

* Python
* Jupyter Notebook
* Google Colab
* Git/GitHub
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
---
## Estrutura do projeto

Recomenda-se organizar o repositório da seguinte forma:
```text
HealthLife-Analytics/
│
├── EDA_Coffee_Health.ipynb
├── synthetic_coffee_health_10000.csv
├── README.md
│
└── outputs/
    ├── coffee_health_processed.csv
    └── melhor_modelo_random_forest_balanced.joblib
```
---
## Como executar o projeto

### 1. Clone o repositório
```bash
git clone URL_DO_SEU_REPOSITORIO
```
### 2. Acesse a pasta
```bash
cd HealthLife-Analytics
```
### 3. Instale as dependências
```bash
pip install pandas numpy matplotlib seaborn scikit-learn joblib jupyter
```
### 4. Execute o notebook
Com Jupyter:
```bash
jupyter notebook
```
Depois, abra:
```text
EDA_Coffee_Health.ipynb
```
Também é possível fazer o upload do notebook e do dataset no **Google Colab**.
> O arquivo `synthetic_coffee_health_10000.csv` deve estar no mesmo diretório do notebook para que o carregamento dos dados funcione corretamente.
---
# Etapa 1 — Análise Exploratória de Dados (EDA)
A primeira etapa consiste na exploração e preparação inicial dos dados.
Foram realizadas análises de:
* Dimensões do dataset;
* Tipos das variáveis;
* Valores nulos;
* Registros duplicados;
* Estatísticas descritivas;
* Distribuição das variáveis numéricas;
* Distribuição das variáveis categóricas;
* Correlação entre variáveis;
* Qualidade do sono;
* Consumo de café;
* Hábitos relacionados à saúde.

### Tratamento de valores nulos
A variável `Health_Issues` apresentou valores nulos.
A análise indicou que esses valores representam clientes que **não reportaram problemas de saúde**. Por isso, os valores foram convertidos para a categoria:
```text
None
```
Após o tratamento:
```text
Nulos restantes: 0
Duplicadas: 0
```
---
# Etapa 2 — Visualização e análise de insights
Foram desenvolvidas visualizações para investigar principalmente a relação entre:
* Consumo de café × horas de sono;
* Consumo de café × qualidade do sono;
* Qualidade do sono × horas dormidas;
* Qualidade do sono × nível de estresse;
* Qualidade do sono × ocupação;
* Qualidade do sono × problemas de saúde;
* Consumo de café × gênero;
* Sono × diferentes grupos de clientes.

Também foram utilizadas segmentações para comparar diferentes perfis de consumidores.
---
# Principais descobertas

A análise exploratória encontrou alguns padrões relevantes nesta base:

### Consumo de café e sono

Os clientes pertencentes ao quartil de maior consumo de café dormem, em média, **0,59 hora a menos por noite** do que aqueles pertencentes ao quartil de menor consumo.

```text
Menor consumo: 6,92 horas
Maior consumo: 6,33 horas
Diferença:     0,59 hora
```

### ☕ Alto consumo de café

Entre os clientes que consomem **5 ou mais xícaras por dia**, a proporção classificada como `Poor` em qualidade do sono foi:

```text
17,8%
```

Enquanto entre aqueles que consomem menos de 2 xícaras:

```text
6,6%
```

Isso indica uma associação relevante entre maior consumo de café e maior proporção de baixa qualidade de sono nesta base.

### 💼 Ocupação

A categoria `Office` apresentou a maior proporção de clientes classificados com qualidade de sono `Poor`:

```text
10,6%
```
### 🚬 Tabagismo
Nesta base, a proporção de qualidade de sono `Poor` foi:

```text
Fumantes:       8,8%
Não-fumantes:   9,8%
```
Portanto, os dados analisados **não sustentam a conclusão de que fumantes apresentam maior proporção de sono `Poor`**.

### ⚠️ Data Leakage
Um dos principais pontos da análise foi a identificação de possível **vazamento de dados**.

As variáveis `Stress_Level` e principalmente `Sleep_Hours` possuem uma relação muito forte com `Sleep_Quality`.

Foram testados três cenários:

| Modelo | Features                                  |  Acurácia |
| ------ | ----------------------------------------- | --------: |
| A      | Com `Stress_Level` e `Sleep_Hours`        |     99,1% |
| B      | Sem `Stress_Level`, mas com `Sleep_Hours` |     98,7% |
| C      | Sem `Stress_Level` e `Sleep_Hours`        | **76,5%** |

O modelo C foi escolhido como cenário final por representar uma situação mais realista: prever a qualidade do sono utilizando **hábitos e características do cliente**, sem utilizar diretamente as horas de sono como variável de entrada.

# 🤖 Etapa 3 — Modelo Preditivo

A variável alvo utilizada foi:

```text
Sleep_Quality
```
As classes existentes são:

```text
Excellent
Fair
Good
Poor
```
## Pré-processamento

Também foram criadas novas features:
### `Caffeine_per_Cup`

### `Has_Health_Issue`
Indicador que identifica se o cliente possui algum problema de saúde relatado.

## Divisão dos dados

Os dados foram divididos em:
80% → Treinamento
20% → Teste
Resultado:
# Modelos utilizados

Foram treinados e comparados três algoritmos principais:
1. **Logistic Regression**
2. **Random Forest**
3. **Decision Tree**

### Resultados

| Modelo              | Acurácia Treino | Acurácia Teste |
| ------------------- | --------------: | -------------: |
| Logistic Regression |           72,7% |          71,9% |
| Random Forest       |       **78,1%** |      **76,5%** |
| Decision Tree       |           79,1% |          74,4% |

O **Random Forest** apresentou a melhor acurácia no conjunto de teste entre os modelos avaliados inicialmente.

# ⚖️ Balanceamento das classes

Também foram avaliadas versões com:

Essa abordagem busca dar maior peso às classes menos representadas durante o treinamento.
As versões balanceadas foram avaliadas utilizando métricas como:
* Acurácia;
* F1-macro;
* Matriz de confusão;
* Relatório de classificação.
A avaliação por F1-macro é importante porque considera o desempenho individual das diferentes classes, evitando que apenas a classe majoritária determine a avaliação do modelo.

# Métricas de avaliação
Os modelos foram avaliados utilizando:

### Acurácia
Mede a proporção de previsões corretas.

### Matriz de confusão
Permite observar os acertos e erros de classificação para cada classe.

### Classification Report
Apresenta métricas como:
* Precision;
* Recall;
* F1-score;
* Support.

### F1-macro
Calcula a média do F1-score entre as classes, dando o mesmo peso para cada uma delas.

# Arquivos gerados
Durante o projeto são gerados arquivos relacionados ao processamento dos dados e ao modelo final.

### Dataset processado
Esse arquivo contém os dados após as etapas de preparação utilizadas no projeto.

### Modelo
O melhor modelo avaliado é salvo utilizando `joblib`.

Exemplo:

# Recomendações para o negócio
Os resultados podem apoiar estratégias relacionadas a bem-estar e comportamento dos clientes.
### 1. Monitoramento do consumo de café
Clientes com consumo elevado apresentaram maior proporção de classificação `Poor` para qualidade do sono nesta base.
Uma empresa poderia utilizar essa informação para desenvolver campanhas educativas sobre consumo consciente de cafeína.

### 2. Segmentação de clientes
As análises permitem identificar grupos com diferentes padrões de:
* Consumo de café;
* Sono;
* Estresse;
* Atividade física;
* Ocupação;
* Problemas de saúde.
Esses grupos podem ser utilizados para estratégias de comunicação e campanhas segmentadas.

### 3. Uso do modelo preditivo
O modelo final pode ser utilizado como uma ferramenta de apoio para identificar clientes com maior probabilidade de apresentar determinada classificação de qualidade do sono.
Entretanto, o modelo **não deve ser utilizado como diagnóstico médico**.

### 4. Importância da qualidade dos dados
A identificação de `Stress_Level` e `Sleep_Hours` como potenciais fontes de vazamento demonstra a importância de analisar as variáveis antes de treinar modelos preditivos.
Modelos com desempenho muito alto nem sempre representam modelos melhores ou mais úteis para o negócio.

# Limitações
Este projeto possui algumas limitações importantes:
* O dataset é sintético;
* As associações encontradas não devem ser interpretadas automaticamente como relações de causa e efeito;
* O modelo apresenta desempenho moderado quando as variáveis diretamente relacionadas ao sono são removidas;
* Os resultados dependem das características específicas desta base;
* O modelo não deve ser utilizado para diagnóstico ou decisões médicas.

# Conclusão
A análise demonstrou uma associação entre maior consumo de café e indicadores menos favoráveis de sono nesta base de dados.
Além da análise exploratória, o projeto demonstrou a importância de identificar **data leakage** antes de avaliar um modelo de Machine Learning.
Embora modelos contendo `Sleep_Hours` apresentem acurácia próxima de 99%, essa abordagem não representa um cenário preditivo adequado quando o objetivo é estimar a qualidade do sono a partir de hábitos de vida.
Após a remoção das variáveis que poderiam causar vazamento, o **Random Forest alcançou 76,5% de acurácia no conjunto de teste**, apresentando o melhor desempenho entre os modelos principais avaliados.

## Projeto
**Health&Life Analytics — Café, Sono e Saúde**
Projeto desenvolvido para estudo de:

## Licença
Este projeto foi desenvolvido para fins acadêmicos e educacionais.
