# 🎓 Projeto Machine Learning - Predição de Desempenho de Estudantes

Projeto completo de Machine Learning para prever o desempenho acadêmico de estudantes usando técnicas de análise exploratória, pré-processamento e modelagem.

## 📋 Sobre o Projeto

Este projeto implementa um pipeline completo de Machine Learning, desde a análise exploratória dos dados até a criação e avaliação de modelos preditivos. O objetivo é prever a **nota final** (`final_grade`) dos estudantes com base em características como horas de estudo, frequência, notas anteriores, entre outras.

**Dataset:** 2.510 registros de estudantes com 14 variáveis iniciais

## 🚀 Início Rápido

### Pré-requisitos

- Python 3.8+
- pip (gerenciador de pacotes Python)

### Instalação

1. **Clone o repositório:**
```bash
git clone https://github.com/SEU_USUARIO/projeto-Machine.git
cd projeto-Machine
```

2. **Instale as dependências:**
```bash
pip install -r requirements.txt
```

3. **Inicie o Jupyter Notebook:**
```bash
python -m notebook
```

4. **Acesse no navegador:**
```
http://localhost:8888
```

## 📁 Estrutura do Projeto

```
projeto-Machine/
│
├── data/                                    # 📊 Dados
│   ├── students_performance.csv            # Dataset original
│   └── processed/                          # Dados processados
│       ├── students_clean.csv              # Dataset limpo (Etapa 2)
│       ├── X_test.csv                      # Features de teste (Etapa 3)
│       └── y_test.csv                      # Target de teste (Etapa 3)
│
├── models/                                  # 🤖 Modelos Treinados
│   ├── scaler.pkl                          # Scaler da Etapa 2
│   └── modelo_baseline.pkl                # Modelo Baseline (Etapa 3)
│
├── etapa1_EDA/                             # 🔍 Etapa 1: Análise Exploratória
│   ├── notebooks/
│   │   └── 01_EDA.ipynb                   # Notebook completo da EDA
│   └── RELATORIO_ETAPA1_EDA.md            # Relatório detalhado
│
├── etapa2_Preparacao/                      # 🧹 Etapa 2: Pré-Processamento
│   ├── notebooks/
│   │   └── 02_Preprocessamento.ipynb      # Notebook de pré-processamento
│   └── README.md                          # Guia da Etapa 2
│
├── etapa3_Baseline/                        # 🤖 Etapa 3: Modelo Baseline
│   ├── notebooks/
│   │   └── 03_ModeloBaseline.ipynb       # Notebook do modelo baseline
│   ├── GUIA_COMPLETO.md                    # Guia completo de conceitos
│   ├── GUIA_GRAFICOS.md                   # Guia de interpretação de gráficos
│   └── README.md                          # Guia da Etapa 3
│
├── requirements.txt                        # 📦 Dependências
├── README.md                              # 📖 Este arquivo
└── ETRUTURA_PROJETO.md                    # 📋 Estrutura detalhada
```

## 📊 Etapas do Projeto

### ✅ Etapa 1: Análise Exploratória de Dados (EDA)

**Status:** ✅ Completa

**Objetivo:** Entender os dados antes de qualquer modelagem

**Conteúdo:**
- Carregamento e visão geral dos dados
- Análise de qualidade (valores faltantes, outliers)
- Análise univariada (distribuições)
- Análise bivariada (correlações e relações)

**Arquivos:**
- `etapa1_EDA/notebooks/01_EDA.ipynb`
- `etapa1_EDA/RELATORIO_ETAPA1_EDA.md`

---

### ✅ Etapa 2: Pré-Processamento de Dados

**Status:** ✅ Completa

**Objetivo:** Preparar e limpar os dados para modelagem

**Conteúdo:**
- Tratamento de valores faltantes (imputação)
- Tratamento de outliers (capping)
- Codificação de variáveis categóricas (One-Hot Encoding)
- Normalização de variáveis numéricas (StandardScaler)
- Feature Engineering (criação de novas features)

**Arquivos:**
- `etapa2_Preparacao/notebooks/02_Preprocessamento.ipynb`
- `etapa2_Preparacao/README.md`

**Outputs:**
- `data/processed/students_clean.csv` - Dataset limpo
- `models/scaler.pkl` - Scaler salvo para uso futuro

---

### ✅ Etapa 3: Modelo Baseline

**Status:** ✅ Completa

**Objetivo:** Criar e avaliar o primeiro modelo de Machine Learning

**Conteúdo:**
- Divisão de dados (60% treino, 20% validação, 20% teste)
- Treinamento de Regressão Linear
- Cálculo de métricas (MSE, RMSE, MAE, R²)
- Análise de overfitting
- Identificação de features importantes
- Visualizações de desempenho

**Arquivos:**
- `etapa3_Baseline/notebooks/03_ModeloBaseline.ipynb`
- `etapa3_Baseline/GUIA_COMPLETO.md` - Guia completo de conceitos
- `etapa3_Baseline/GUIA_GRAFICOS.md` - Guia de interpretação de gráficos
- `etapa3_Baseline/README.md` - Guia da Etapa 3

**Outputs:**
- `models/modelo_baseline.pkl` - Modelo treinado
- `data/processed/X_test.csv` e `y_test.csv` - Dados de teste (guardados para Etapa 5)

**Métricas Esperadas:**
- R² > 0.65 (modelo explica mais de 65% da variação)
- RMSE < 5 pontos (erro médio aceitável)
- Diferença Treino vs Validação < 0.10 (sem overfitting)

---

### 🔄 Próximas Etapas

- **Etapa 4:** Modelos Avançados (Random Forest, XGBoost, etc.)
- **Etapa 5:** Avaliação Final e Comparação de Modelos

## 🛠️ Tecnologias Utilizadas

- **Python 3.8+**
- **Pandas** - Manipulação de dados
- **NumPy** - Computação numérica
- **Matplotlib/Seaborn** - Visualizações
- **Scikit-learn** - Machine Learning
- **Jupyter Notebook** - Ambiente de desenvolvimento

## 📚 Documentação

Cada etapa possui documentação completa:

- **Relatórios:** Explicam cada código, tabela e gráfico
- **Guias:** Conceitos teóricos e práticos
- **READMEs:** Instruções específicas de cada etapa

## 📖 Como Usar

### Para Estudantes/Aprendizes

1. **Comece pela Etapa 1:**
   - Leia o relatório da Etapa 1
   - Execute o notebook `01_EDA.ipynb`
   - Entenda os dados antes de prosseguir

2. **Continue com Etapa 2:**
   - Execute o notebook `02_Preprocessamento.ipynb`
   - Veja como os dados são preparados

3. **Finalize com Etapa 3:**
   - **IMPORTANTE:** Leia `GUIA_COMPLETO.md` primeiro!
   - Execute o notebook `03_ModeloBaseline.ipynb`
   - Consulte `GUIA_GRAFICOS.md` para interpretar os gráficos

### Para Desenvolvedores

- Cada etapa é independente e pode ser executada separadamente
- Os dados processados são salvos para uso nas próximas etapas
- Os modelos são salvos em `.pkl` para reutilização

## 📊 Resultados Principais

### Etapa 3 - Modelo Baseline

- **R² Validação:** ~0.69 (69% da variação explicada)
- **RMSE:** ~4.2 pontos
- **MAE:** ~3.2 pontos
- **Overfitting:** Não detectado (diferença < 2%)

## 🤝 Contribuindo

Este é um projeto educacional. Sinta-se livre para:
- Fazer fork do projeto
- Criar branches para novas features
- Abrir issues para reportar bugs ou sugerir melhorias
- Enviar pull requests

## 📝 Licença

Este projeto é de código aberto e está disponível para fins educacionais.

## 👤 Autor

[Seu Nome]

## 🙏 Agradecimentos

- Dataset: Students Performance Dataset
- Comunidade de Machine Learning

---

**Última atualização:** Etapa 3 completa ✅

**Status do projeto:** 🚧 Em desenvolvimento (Etapas 4 e 5 pendentes)
