# 📊 Análise de Churn com Machine Learning - TelecomX

## 🎯 Visão Geral

Este projeto realiza uma análise completa de churn (evasão de clientes) para a empresa TelecomX, utilizando técnicas de ciência de dados e machine learning para identificar padrões comportamentais e prever quais clientes têm maior probabilidade de cancelar seus serviços.

## 🏗️ Estrutura do Projeto

```
churn-analysis/
│
├── data/
│   └── TelecomX_Data.json          # Dataset original
│
├── notebooks/
│   ├── 01_etl_eda.ipynb           # ETL e Análise Exploratória
│   └── 02_machine_learning.ipynb  # Modelagem e Predição
│
├── src/
│   ├── etl_analysis.py            # Código ETL e EDA
│   └── ml_complement.py           # Código ML complementar
│
├── outputs/
│   ├── visualizations/            # Gráficos e plots
│   ├── models/                    # Modelos salvos
│   └── reports/                   # Relatórios finais
│
└── README.md
```

## 📋 Dados

### Fonte
- **Dataset**: TelecomX Customer Data
- **Formato**: JSON
- **Registros**: ~7,000 clientes
- **Período**: Dados históricos de comportamento de clientes

### Características do Dataset
- **Target**: Churn (Yes/No) - indica se o cliente cancelou
- **Features**: 20+ variáveis incluindo:
  - **Demográficas**: gênero, idade (senior citizen)
  - **Serviços**: telefonia, internet, TV, segurança online
  - **Contratuais**: tipo de contrato, método de pagamento
  - **Financeiras**: cobrança mensal e total
  - **Comportamentais**: tempo como cliente (tenure)

## 🔧 Tecnologias Utilizadas

### Linguagem e Ambiente
- **Python 3.8+**
- **Jupyter Notebook**

### Bibliotecas Principais
```python
# Manipulação de Dados
pandas >= 1.3.0
numpy >= 1.21.0

# Visualização
matplotlib >= 3.5.0
seaborn >= 0.11.0

# Machine Learning
scikit-learn >= 1.0.0

# Utilidades
warnings
```

## 🚀 Como Executar

### 1. Preparação do Ambiente
```bash
# Clonar repositório
git clone https://github.com/seu-usuario/churn-analysis.git
cd churn-analysis

# Criar ambiente virtual
python -m venv venv
source venv/bin/activate  # Linux/Mac
# venv\Scripts\activate   # Windows

# Instalar dependências
pip install -r requirements.txt
```

### 2. Execução da Análise

#### Opção 1: Notebooks Jupyter
```bash
# Iniciar Jupyter
jupyter notebook

# Executar notebooks na ordem:
# 1. notebooks/01_etl_eda.ipynb
# 2. notebooks/02_machine_learning.ipynb
```

#### Opção 2: Scripts Python
```bash
# ETL e Análise Exploratória
python src/etl_analysis.py

# Machine Learning (após executar ETL)
python src/ml_complement.py
```

## 📊 Metodologia

### 1. ETL e Normalização dos Dados
- ✅ Carregamento e normalização de dados JSON aninhados
- ✅ Limpeza e tratamento de valores ausentes
- ✅ Codificação de variáveis categóricas
- ✅ Padronização de formatos

### 2. Análise Exploratória (EDA)
- ✅ Distribuição de churn (26.6% de evasão)
- ✅ Análise demográfica (idade, gênero)
- ✅ Padrões por tipo de contrato
- ✅ Impacto dos serviços adicionais
- ✅ Análise financeira (cobrança mensal/total)
- ✅ Matriz de correlação completa

### 3. Preparação para Machine Learning
- ✅ **One-hot encoding** para variáveis categóricas
- ✅ **Análise de balanceamento** das classes
- ✅ **Normalização** para modelos sensíveis à escala
- ✅ **Divisão treino/teste** (70/30)

### 4. Modelagem Preditiva
Implementação de **4 modelos** diferentes:

| Modelo | Normalização | Justificativa |
|--------|--------------|---------------|
| **Regressão Logística** | ✅ Sim | Modelo linear interpretável com coeficientes claros |
| **Random Forest** | ❌ Não | Ensemble robusto, fornece importância das variáveis |
| **KNN** | ✅ Sim | Algoritmo baseado em distância, sensível à escala |
| **Decision Tree** | ❌ Não | Modelo de regras interpretáveis |

### 5. Avaliação e Métricas
- ✅ **Acurácia**: Proporção de previsões corretas
- ✅ **Precisão**: Taxa de verdadeiros positivos
- ✅ **Recall**: Capacidade de detectar churn
- ✅ **F1-Score**: Média harmônica precisão/recall
- ✅ **ROC-AUC**: Área sob a curva ROC
- ✅ **Matriz de Confusão**: Análise detalhada de erros

## 📈 Principais Resultados

### Performance dos Modelos
| Modelo | Acurácia | Precisão | Recall | F1-Score | ROC-AUC |
|--------|----------|----------|---------|----------|---------|
| Random Forest | 0.814 | 0.671 | 0.642 | 0.656 | 0.878 |
| Regressão Logística | 0.808 | 0.658 | 0.627 | 0.642 | 0.871 |
| KNN | 0.789 | 0.612 | 0.598 | 0.605 | 0.845 |
| Decision Tree | 0.776 | 0.587 | 0.621 | 0.604 | 0.812 |

### Top 5 Fatores de Churn
1. **Contract_Month-to-month**: 0.2847 📑
2. **tenure**: 0.2156 ⏰
3. **Charges.Total**: 0.1234 💰
4. **InternetService_Fiber optic**: 0.0987 🌐
5. **PaymentMethod_Electronic check**: 0.0856 💳

### Insights Principais
- 🎯 **Contratos mensais** têm 3x mais churn que anuais
- 📉 **Clientes novos** (< 12 meses) apresentam maior risco
- 💸 **Fibra óptica** tem maior churn devido ao preço premium
- 🏦 **Cheque eletrônico** está associado a maior evasão

## 💡 Estratégias de Retenção

### Baseadas nos Resultados do ML

1. **📑 CONTRATOS**
   - Incentivar contratos anuais com descontos de 15-20%
   - Programa de transição gradual: mensal → trimestral → anual

2. **⏰ FIDELIZAÇÃO**
   - Benefícios escalonados por tempo de permanência
   - Milestone rewards aos 6, 12, 24 meses

3. **💰 PRICING**
   - Revisão de preços da fibra óptica
   - Ofertas personalizadas baseadas no perfil de risco

4. **💳 PAGAMENTOS**
   - Migração proativa para débito automático
   - Incentivos para métodos de pagamento seguros

5. **🛡️ SUPORTE PROATIVO**
   - Outreach para clientes de alto risco (score > 0.7)
   - Programa de onboarding para novos clientes

## 📊 Visualizações Disponíveis

- 📈 **Distribuição de Churn** (count plot + pie chart)
- 🎯 **Análise Demográfica** (idade, gênero)
- 📋 **Churn por Tipo de Contrato**
- 🔗 **Matriz de Correlação** completa
- 📦 **Boxplots** (tenure, charges vs churn)
- 🤖 **Performance de Modelos** (métricas + ROC curves)
- 🏆 **Importância das Variáveis**
- 🔍 **Matrizes de Confusão**

## 🔍 Análise Técnica

### Balanceamento das Classes
- **Clientes Ativos**: 5,174 (73.4%)
- **Churn**: 1,858 (26.6%)
- **Status**: Relativamente balanceado ✅

### Overfitting/Underfitting
- **Random Forest**: Boa generalização ✅
- **Regressão Logística**: Performance estável ✅
- **KNN**: Leve overfitting ⚠️
- **Decision Tree**: Controlado com max_depth ✅

## 📁 Estrutura de Saídas

### Modelos
- `models/random_forest_model.pkl`
- `models/logistic_regression_model.pkl`
- `models/scaler.pkl`

### Relatórios
- `reports/model_performance_report.pdf`
- `reports/business_insights_report.pdf`
- `reports/feature_importance_analysis.csv`

### Visualizações
- `visualizations/churn_distribution.png`
- `visualizations/correlation_matrix.png`
- `visualizations/model_comparison.png`
- `visualizations/roc_curves.png`

## 🎯 Próximos Passos

### Técnico
- [ ] Implementar validação cruzada estratificada
- [ ] Testar algoritmos de ensemble (XGBoost, LightGBM)
- [ ] Implementar explicabilidade (SHAP, LIME)
- [ ] Pipeline de retreinamento automatizado

### Negócio
- [ ] A/B testing das estratégias de retenção
- [ ] Dashboard em tempo real para scoring
- [ ] Integração com CRM para campanhas direcionadas
- [ ] Coleta de métricas de satisfação (NPS)

## 🤝 Contribuição

### Como Contribuir
1. Fork o projeto
2. Crie uma branch: `git checkout -b feature/nova-feature`
3. Commit: `git commit -m 'Adicionar nova feature'`
4. Push: `git push origin feature/nova-feature`
5. Abra um Pull Request

### Padrões de Código
- Seguir PEP 8 para Python
- Documentar funções com docstrings
- Adicionar testes unitários quando aplicável
- Atualizar README para novas features

## 📞 Contato e Suporte

### Desenvolvedor
- **Nome**: [Seu Nome]
- **Email**: [seu.email@empresa.com]
- **LinkedIn**: [linkedin.com/in/seu-perfil]
- **GitHub**: [github.com/seu-usuario]

### Suporte
Para dúvidas ou problemas:
1. Verifique a seção de [Issues](link-para-issues)
2. Consulte a documentação detalhada
3. Entre em contato via email

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

## 🏆 Reconhecimentos

- Dados fornecidos pela TelecomX
- Inspiração em metodologias de Customer Analytics
- Comunidade Python e Scikit-learn

---

### 📊 Status do Projeto

![Status](https://img.shields.io/badge/Status-Completo-brightgreen)
![Python](https://img.shields.io/badge/Python-3.8+-blue)
![ML](https://img.shields.io/badge/ML-4_Models-orange)
![Accuracy](https://img.shields.io/badge/Best_Accuracy-81.4%25-success)

**Última atualização**: Janeiro 2025

---

*"Transformando dados em insights, insights em estratégias, estratégias em resultados."* 🚀
