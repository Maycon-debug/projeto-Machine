# Relatório - Etapa 1: Análise Exploratória de Dados (EDA)

## 📋 Índice

1. [Introdução](#introdução)
2. [Seção 1: Carregamento e Visão Geral dos Dados](#seção-1-carregamento-e-visão-geral-dos-dados)
3. [Seção 2: Análise de Qualidade dos Dados](#seção-2-análise-de-qualidade-dos-dados)
4. [Seção 3: Análise Univariada](#seção-3-análise-univariada)
5. [Seção 4: Análise Bivariada](#seção-4-análise-bivariada)
6. [Conclusões](#conclusões)

---

## Introdução

Este relatório documenta a Análise Exploratória de Dados (EDA) realizada no dataset de desempenho de estudantes. O objetivo é entender as características dos dados, identificar problemas de qualidade e descobrir insights que guiarão as próximas etapas do projeto de Machine Learning.

**Dataset**: `students_performance.csv`  
**Variável Alvo**: `final_grade` (nota final do estudante)  
**Total de Registros**: 2.510 estudantes  
**Total de Variáveis**: 14 colunas

---

## Seção 1: Carregamento e Visão Geral dos Dados

### 1.1 Importação de Bibliotecas

**Código:**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import warnings

%matplotlib inline
```

**Explicação:**

- **pandas**: Manipulação e análise de dados estruturados (DataFrames)
- **numpy**: Operações matemáticas e arrays
- **matplotlib**: Criação de gráficos e visualizações
- **seaborn**: Visualizações estatísticas avançadas
- **warnings**: Suprime avisos desnecessários
- **%matplotlib inline**: Comando mágico do Jupyter para exibir gráficos inline no notebook

**Configurações Aplicadas:**

- Estilo de gráficos: `seaborn-darkgrid` (grade escura para melhor visualização)
- Paleta de cores: `husl` (cores harmoniosas e distintas)
- Exibição completa: Todas as colunas e até 100 linhas visíveis
- Tamanho padrão de figuras: 12x6 polegadas, 100 DPI

### 1.2 Carregamento do Dataset

**Código:**

```python
df = pd.read_csv('../data/students_performance.csv')
print(f"Formato do dataset: {df.shape}")
```

**Resultado:**

- **Formato**: (2510, 14)
- **Linhas**: 2.510 registros (estudantes)
- **Colunas**: 14 variáveis

**Explicação:**

- `pd.read_csv()`: Carrega arquivo CSV em um DataFrame pandas
- `df.shape`: Retorna tupla (linhas, colunas)
- O dataset contém informações sobre características dos estudantes e suas notas finais

### 1.3 Inspeção Inicial dos Dados

**Código:**

```python
df.head(10)  # Primeiras 10 linhas
df.tail(10)  # Últimas 10 linhas
df.info()    # Informações sobre tipos e valores não-nulos
```

**Explicação:**

- **head()**: Visualiza início do dataset para verificar se foi carregado corretamente
- **tail()**: Visualiza final do dataset para detectar problemas no final do arquivo
- **info()**: Mostra:
  - Nome de cada coluna
  - Tipo de dado (int64, float64, object)
  - Quantidade de valores não-nulos
  - Uso de memória

**Informações Obtidas:**

- **Variáveis Numéricas (6)**: age, study_hours_week, attendance_rate, sleep_hours, previous_scores, final_grade
- **Variáveis Categóricas (8)**: student_id, gender, parental_education, extracurricular, tutoring, internet_quality, family_income, health_status
- **Memória**: 274.7+ KB

### 1.4 Identificação de Tipos de Variáveis

**Código:**

```python
numeric_cols = df.select_dtypes(include=[np.number]).columns.tolist()
categorical_cols = df.select_dtypes(include=['object']).columns.tolist()
```

**Explicação:**

- **select_dtypes()**: Filtra colunas por tipo de dado
- **include=[np.number]**: Seleciona apenas tipos numéricos (int, float)
- **include=['object']**: Seleciona apenas strings/objetos (categóricas)
- Essas listas são usadas nas análises subsequentes

**Resultado:**

- **6 variáveis numéricas**: age, study_hours_week, attendance_rate, sleep_hours, previous_scores, final_grade
- **8 variáveis categóricas**: student_id, gender, parental_education, extracurricular, tutoring, internet_quality, family_income, health_status

### 1.5 Estatísticas Descritivas

**Código:**

```python
df[numeric_cols].describe()
```

**Explicação:**

- **describe()**: Calcula estatísticas descritivas para variáveis numéricas
- Retorna uma tabela com:
  - **count**: Quantidade de valores não-nulos
  - **mean**: Média aritmética
  - **std**: Desvio padrão (dispersão dos dados)
  - **min**: Valor mínimo
  - **25%**: Primeiro quartil (Q1)
  - **50%**: Mediana (Q2)
  - **75%**: Terceiro quartil (Q3)
  - **max**: Valor máximo

**Interpretação:**
Essas estatísticas fornecem uma visão geral da distribuição de cada variável numérica, ajudando a identificar:

- Escala dos valores (ex: idade entre 18-25 anos)
- Dispersão (desvio padrão alto indica maior variabilidade)
- Valores extremos (mínimo e máximo)
- Tendência central (média e mediana)

---

## Seção 2: Análise de Qualidade dos Dados

### 2.1 Identificação de Valores Faltantes

**Código:**

```python
missing_values = df.isnull().sum()
missing_percentage = (df.isnull().sum() / len(df)) * 100

missing_df = pd.DataFrame({
    'Valores Faltantes': missing_values,
    'Porcentagem (%)': missing_percentage
})
missing_df = missing_df[missing_df['Valores Faltantes'] > 0]
```

**Explicação:**

- **isnull()**: Identifica valores nulos (NaN) no DataFrame
- **sum()**: Conta total de valores nulos por coluna
- **/ len(df) \* 100**: Calcula porcentagem de valores faltantes
- Filtra apenas colunas com valores faltantes

**Resultados Encontrados:**
| Coluna | Valores Faltantes | Porcentagem (%) |
|--------|-------------------|-----------------|
| study_hours_week | 293 | 11.67% |
| family_income | 278 | 11.08% |
| sleep_hours | 266 | 10.60% |
| attendance_rate | 232 | 9.24% |
| internet_quality | 155 | 6.18% |
| previous_scores | 127 | 5.06% |

**Interpretação:**

- Todas as variáveis têm valores faltantes (entre 5% e 12%)
- `study_hours_week` tem a maior porcentagem de valores faltantes (11.67%)
- Esses valores faltantes precisarão ser tratados na etapa de preparação de dados

### 2.2 Visualização de Valores Faltantes

**Código:**

```python
missing_df['Porcentagem (%)'].plot(kind='barh', color='coral')
plt.title('Porcentagem de Valores Faltantes por Coluna')
plt.xlabel('Porcentagem (%)')
plt.ylabel('Colunas')
```

**Explicação:**

- **plot(kind='barh')**: Cria gráfico de barras horizontais
- Visualização facilita identificação rápida das colunas com mais valores faltantes
- Cores destacam a severidade do problema

**Objetivo:**
Facilitar a visualização e priorização do tratamento de valores faltantes nas próximas etapas.

### 2.3 Identificação de Outliers com Boxplots

**Código:**

```python
for col in numeric_cols:
    df.boxplot(column=col, ax=axes[idx], vert=True)
```

**Explicação:**

- **boxplot()**: Cria diagrama de caixa (boxplot) para cada variável numérica
- **Componentes do Boxplot:**
  - **Linha central**: Mediana (Q2)
  - **Caixa**: Intervalo Interquartil (IQR = Q3 - Q1)
  - **Limites da caixa**: Q1 (inferior) e Q3 (superior)
  - **Whiskers (bigodes)**: Linhas que se estendem até 1.5 × IQR além de Q1 e Q3
  - **Pontos fora dos whiskers**: Outliers (valores atípicos)

**Interpretação:**

- Pontos isolados acima ou abaixo dos whiskers indicam outliers
- Outliers podem ser erros de coleta ou valores legítimos mas raros
- Necessário investigar se são erros ou dados válidos

### 2.4 Análise Quantitativa de Outliers (Método IQR)

**Código:**

```python
Q1 = df[col].quantile(0.25)
Q3 = df[col].quantile(0.75)
IQR = Q3 - Q1
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

outliers = df[(df[col] < lower_bound) | (df[col] > upper_bound)]
```

**Explicação:**

- **Método IQR (Intervalo Interquartil)**:
  - **Q1**: 25% dos dados estão abaixo deste valor
  - **Q3**: 75% dos dados estão abaixo deste valor
  - **IQR**: Diferença entre Q3 e Q1 (contém 50% dos dados centrais)
  - **Limites**: Q1 - 1.5×IQR (inferior) e Q3 + 1.5×IQR (superior)
  - Valores fora desses limites são considerados outliers

**Resultados Encontrados:**
| Variável | Número de Outliers | Porcentagem (%) |
|----------|-------------------|-----------------|
| study_hours_week | 20 | 0.80% |
| attendance_rate | 27 | 1.08% |
| sleep_hours | 24 | 0.96% |
| previous_scores | 21 | 0.84% |
| final_grade | 7 | 0.28% |
| age | 1 | 0.04% |

**Interpretação:**

- Poucos outliers encontrados (< 2% em todas as variáveis)
- `attendance_rate` tem mais outliers (1.08%)
- `final_grade` tem poucos outliers (0.28%), indicando distribuição mais concentrada
- Esses outliers precisarão ser avaliados na etapa de preparação de dados

---

## Seção 3: Análise Univariada

### 3.1 Histogramas para Variáveis Numéricas

**Código:**

```python
axes[idx].hist(df[col].dropna(), bins=30, edgecolor='black', alpha=0.7)
```

**Explicação:**

- **hist()**: Cria histograma (gráfico de frequência)
- **bins=30**: Divide os dados em 30 intervalos
- **dropna()**: Remove valores nulos antes de plotar
- **edgecolor='black'**: Borda preta nas barras para melhor visualização
- **alpha=0.7**: Transparência de 70%

**O que um Histograma Mostra:**

- **Distribuição**: Como os valores estão distribuídos
- **Forma**: Simétrica, assimétrica à direita/esquerda, bimodal
- **Concentração**: Onde a maioria dos valores se concentra
- **Amplitude**: Faixa de valores presente

**Interpretação:**
Cada histograma revela características específicas de cada variável:

- **age**: Distribuição da idade dos estudantes
- **study_hours_week**: Horas de estudo semanais
- **attendance_rate**: Taxa de frequência às aulas
- **sleep_hours**: Horas de sono
- **previous_scores**: Notas anteriores
- **final_grade**: Nota final (variável alvo)

### 3.2 Histogramas com Curva de Densidade (KDE)

**Código:**

```python
sns.histplot(df[col].dropna(), kde=True, bins=30)
```

**Explicação:**

- **histplot()**: Função do Seaborn para histogramas
- **kde=True**: Adiciona Kernel Density Estimation (curva de densidade suavizada)
- A curva KDE ajuda a visualizar a forma da distribuição de forma mais suave

**Vantagens do KDE:**

- Suaviza o histograma, facilitando identificação de padrões
- Mostra a probabilidade de ocorrência de cada valor
- Útil para identificar distribuições normais, assimétricas, etc.

### 3.3 Distribuição de Variáveis Categóricas

**Código:**

```python
value_counts = df[col].value_counts()
value_counts.plot(kind='bar', ax=axes[idx], color='steelblue')
```

**Explicação:**

- **value_counts()**: Conta frequência de cada categoria
- **plot(kind='bar')**: Cria gráfico de barras
- Mostra quantas vezes cada categoria aparece no dataset

**O que Revela:**

- **Balanceamento**: Se as categorias estão balanceadas ou desbalanceadas
- **Categoria dominante**: Qual categoria é mais frequente
- **Raridade**: Categorias com poucas ocorrências
- **Distribuição**: Como os dados estão distribuídos entre categorias

**Variáveis Categóricas Analisadas:**

- **gender**: Gênero dos estudantes
- **parental_education**: Nível educacional dos pais
- **extracurricular**: Participação em atividades extracurriculares
- **tutoring**: Recebe tutoria ou não
- **internet_quality**: Qualidade da internet
- **family_income**: Renda familiar
- **health_status**: Status de saúde

### 3.4 Análise Específica da Variável Alvo (final_grade)

**Código:**

```python
target_variable = 'final_grade'
plt.hist(df[target_variable].dropna(), bins=30)
sns.histplot(df[target_variable].dropna(), kde=True, bins=30)
df[target_variable].describe()
df[target_variable].skew()  # Assimetria
df[target_variable].kurtosis()  # Curtose
```

**Resultados:**

- **Média**: 92.09 pontos
- **Mediana**: 93.31 pontos
- **Desvio Padrão**: 7.45 pontos
- **Mínimo**: 63.24 pontos
- **Máximo**: 101.07 pontos
- **Assimetria (Skewness)**: -0.7647 (assimétrica à esquerda)
- **Curtose (Kurtosis)**: -0.1237 (distribuição platicúrtica)

**Interpretação:**

- **Assimetria Negativa (-0.76)**: A maioria dos estudantes tem notas altas (acima da média)
- **Mediana > Média**: Confirma distribuição assimétrica à esquerda
- **Curtose Negativa**: Distribuição mais "achatada" que a normal, com caudas mais leves
- **Conclusão**: A maioria dos estudantes tem bom desempenho, com poucos casos de notas muito baixas

---

## Seção 4: Análise Bivariada

### 4.1 Matriz de Correlação

**Código:**

```python
correlation_matrix = df[numeric_cols].corr()
sns.heatmap(correlation_matrix, annot=True, fmt='.2f', cmap='coolwarm', center=0)
```

**Explicação:**

- **corr()**: Calcula correlação de Pearson entre todas as variáveis numéricas
- **heatmap()**: Visualiza a matriz de correlação como mapa de calor
- **annot=True**: Mostra os valores de correlação nas células
- **fmt='.2f'**: Formata valores com 2 casas decimais
- **cmap='coolwarm'**: Cores azuis (negativas) e vermelhas (positivas)
- **center=0**: Centraliza a escala de cores em zero

**Interpretação da Correlação:**

- **+1.0**: Correlação positiva perfeita (quando uma aumenta, a outra aumenta)
- **0.0**: Sem correlação linear
- **-1.0**: Correlação negativa perfeita (quando uma aumenta, a outra diminui)
- **|r| > 0.7**: Correlação forte
- **0.3 < |r| < 0.7**: Correlação moderada
- **|r| < 0.3**: Correlação fraca

**O que Revela:**

- Quais variáveis estão relacionadas entre si
- Variáveis altamente correlacionadas podem ser redundantes
- Identifica variáveis preditoras importantes para a variável alvo

### 4.2 Correlações com a Variável Alvo

**Código:**

```python
correlations = correlation_matrix[target_variable].drop(target_variable)
correlations = correlations.sort_values(ascending=False)
correlations.plot(kind='barh', color=['red' if x < 0 else 'green' for x in correlations.values])
```

**Explicação:**

- Extrai apenas as correlações com `final_grade`
- Remove a correlação consigo mesma (sempre 1.0)
- Ordena do maior para o menor
- Visualiza em gráfico de barras horizontais
- Verde para correlações positivas, vermelho para negativas

**Interpretação:**

- **Correlações Positivas**: Variáveis que aumentam quando a nota final aumenta
- **Correlações Negativas**: Variáveis que diminuem quando a nota final aumenta
- **Valores Altos**: Variáveis mais importantes para prever a nota final

**Variáveis Mais Correlacionadas (esperado):**

- `previous_scores`: Provavelmente alta correlação positiva (notas anteriores predizem notas futuras)
- `attendance_rate`: Correlação positiva esperada (maior frequência = melhor nota)
- `study_hours_week`: Correlação positiva esperada (mais estudo = melhor nota)

### 4.3 Scatter Plots (Gráficos de Dispersão)

**Código:**

```python
top_correlated = correlations.abs().sort_values(ascending=False).head(6).index
for col in top_correlated:
    axes[idx].scatter(df[col], df[target_variable], alpha=0.5)
```

**Explicação:**

- **scatter()**: Cria gráfico de dispersão (pontos)
- Mostra relação entre duas variáveis numéricas
- **alpha=0.5**: Transparência para ver sobreposição de pontos
- Foca nas 6 variáveis com maior correlação absoluta

**O que Revela:**

- **Tendência Linear**: Se os pontos formam uma linha (correlação linear)
- **Direção**: Linha sobe (positiva) ou desce (negativa)
- **Força**: Quão próximos os pontos estão da linha
- **Outliers**: Pontos que fogem do padrão geral

**Interpretação:**

- Nuvem de pontos subindo: correlação positiva
- Nuvem de pontos descendo: correlação negativa
- Pontos dispersos: correlação fraca
- Pontos alinhados: correlação forte

### 4.4 Boxplots Comparativos (Variáveis Categóricas vs Variável Alvo)

**Código:**

```python
sns.boxplot(data=df_filtered, x=col, y=target_variable)
```

**Explicação:**

- Compara distribuição de `final_grade` entre diferentes categorias
- Cada categoria tem seu próprio boxplot
- Mostra se há diferença significativa entre grupos

**O que Revela:**

- **Diferença entre grupos**: Se categorias diferentes têm notas diferentes
- **Variabilidade**: Quão dispersas são as notas em cada categoria
- **Outliers por grupo**: Valores atípicos em cada categoria
- **Mediana por grupo**: Qual categoria tem melhor desempenho médio

**Interpretação:**

- Boxplots em alturas diferentes: categoria influencia a nota final
- Boxplots na mesma altura: categoria não influencia significativamente
- Boxplot mais alto: categoria com melhor desempenho
- Boxplot mais baixo: categoria com pior desempenho

**Exemplos de Análises:**

- **final_grade por gender**: Homens vs mulheres têm desempenho diferente?
- **final_grade por tutoring**: Estudantes com tutoria têm melhor nota?
- **final_grade por internet_quality**: Qualidade da internet afeta a nota?
- **final_grade por family_income**: Renda familiar influencia desempenho?

---

## Conclusões

### Principais Descobertas

1. **Estrutura dos Dados:**

   - Dataset com 2.510 estudantes e 14 variáveis
   - 6 variáveis numéricas e 8 categóricas
   - Variável alvo: `final_grade` (nota final)

2. **Qualidade dos Dados:**

   - Valores faltantes presentes em todas as variáveis (5-12%)
   - Poucos outliers encontrados (< 2% em todas as variáveis)
   - Necessário tratamento de valores faltantes na próxima etapa

3. **Distribuição da Variável Alvo:**

   - Média: 92.09 pontos
   - Distribuição assimétrica à esquerda (maioria com notas altas)
   - Poucos casos de notas muito baixas

4. **Relações Identificadas:**
   - Variáveis numéricas mostram correlações com a variável alvo
   - Variáveis categóricas podem influenciar o desempenho
   - Necessário aprofundar análise de correlações específicas

### Próximos Passos

1. **Preparação de Dados:**

   - Tratar valores faltantes (imputação ou remoção)
   - Avaliar e tratar outliers
   - Codificar variáveis categóricas

2. **Feature Engineering:**

   - Criar novas features se necessário
   - Selecionar features mais relevantes
   - Normalizar/escalar variáveis se necessário

3. **Modelagem:**
   - Dividir dados em treino e teste
   - Escolher algoritmos apropriados
   - Treinar e avaliar modelos

---

**Fim do Relatório da Etapa 1 - EDA**
