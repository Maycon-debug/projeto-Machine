# 📁 Estrutura Detalhada do Projeto

## Organização por Etapas

O projeto está organizado em pastas separadas para cada etapa do pipeline de Machine Learning, facilitando a navegação e manutenção do código.

## 📂 Estrutura Completa

```
projeto-Machine/
│
├── data/                                    # 📊 Dados do Projeto
│   └── students_performance.csv            # Dataset principal (2.510 registros)
│
├── etapa1_EDA/                              # 🔍 Etapa 1: Análise Exploratória
│   ├── notebooks/
│   │   └── 01_EDA.ipynb                    # Notebook completo da EDA
│   └── RELATORIO_ETAPA1_EDA.md             # Relatório detalhado explicando cada código
│
├── etapa2_Preparacao/                       # 🧹 Etapa 2: Preparação de Dados
│   └── notebooks/                          # Notebooks da etapa 2 (a criar)
│       └── (notebooks serão criados aqui)
│
├── etapa3_FeatureEngineering/              # 🔧 Etapa 3: Feature Engineering (futuro)
│   └── notebooks/
│
├── etapa4_Modelagem/                        # 🤖 Etapa 4: Modelagem (futuro)
│   └── notebooks/
│
├── etapa5_Avaliacao/                        # 📈 Etapa 5: Avaliação (futuro)
│   └── notebooks/
│
├── requirements.txt                         # 📦 Dependências do projeto
├── README.md                                # 📖 Documentação principal
└── ETRUTURA_PROJETO.md                     # 📋 Este arquivo
```

## 📋 Descrição das Etapas

### Etapa 1: Análise Exploratória de Dados (EDA) ✅

**Status:** Completa

**Conteúdo:**

- Notebook com todas as análises exploratórias
- Relatório completo explicando cada código e tabela
- Visualizações e estatísticas descritivas

**Arquivos:**

- `etapa1_EDA/notebooks/01_EDA.ipynb`
- `etapa1_EDA/RELATORIO_ETAPA1_EDA.md`

### Etapa 2: Preparação e Limpeza de Dados 🔄

**Status:** Em preparação

**Conteúdo:**

- Tratamento de valores faltantes
- Tratamento de outliers
- Codificação de variáveis categóricas
- Normalização/escala de variáveis

**Arquivos:**

- `etapa2_Preparacao/notebooks/` (a criar)

### Etapas Futuras 📅

- **Etapa 3:** Feature Engineering
- **Etapa 4:** Modelagem (treinamento de modelos)
- **Etapa 5:** Avaliação e Otimização

## 🎯 Convenções de Nomenclatura

### Notebooks

- Formato: `NN_NomeDaEtapa.ipynb`
- Exemplo: `01_EDA.ipynb`, `02_Preparacao.ipynb`

### Relatórios

- Formato: `RELATORIO_ETAPAN_Nome.md`
- Exemplo: `RELATORIO_ETAPA1_EDA.md`

### Pastas

- Formato: `etapaN_Nome`
- Exemplo: `etapa1_EDA`, `etapa2_Preparacao`

## 📝 Notas Importantes

1. **Caminhos Relativos:** Os notebooks usam caminhos relativos para acessar o dataset:

   - De `etapa1_EDA/notebooks/`: `../../data/students_performance.csv`
   - De `etapa2_Preparacao/notebooks/`: `../../data/students_performance.csv`

2. **Dados Intermediários:** Dados processados podem ser salvos em:

   - `data/processed/` (a criar quando necessário)

3. **Modelos:** Modelos treinados podem ser salvos em:

   - `models/` (a criar na etapa 4)

4. **Resultados:** Gráficos e resultados podem ser salvos em:
   - `results/` (a criar quando necessário)

## 🔄 Fluxo de Trabalho

```
1. EDA (etapa1_EDA/)
   ↓
2. Preparação (etapa2_Preparacao/)
   ↓
3. Feature Engineering (etapa3_FeatureEngineering/)
   ↓
4. Modelagem (etapa4_Modelagem/)
   ↓
5. Avaliação (etapa5_Avaliacao/)
```

Cada etapa utiliza os resultados da etapa anterior.

---

**Última atualização:** Estrutura criada e Etapa 1 completa ✅
