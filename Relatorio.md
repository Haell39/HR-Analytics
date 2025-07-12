# HR Analytics: Predição de Rotatividade de Funcionários para Retenção Estratégica

## Introdução
Este projeto tem como objetivo desenvolver um modelo preditivo para identificar quais funcionários possuem maior probabilidade de deixar a empresa (churn ou turnover). A análise de dados de Recursos Humanos (HR Analytics) é essencial para ajudar na retenção de talentos e na otimização da gestão de pessoas, permitindo decisões estratégicas que reduzam a rotatividade, aumentando a retenção e satisfação dos funcionários.

## Objetivo
A fase inicial focou em explorar o conjunto de dados, entender suas variáveis, identificar padrões e realizar a limpeza necessária para preparar os dados para o treinamento de modelos preditivos. O objetivo final foi treinar e avaliar algoritmos de Machine Learning, como Regressão Logística, Random Forest, KNN, XGBoost e um modelo de Deep Learning (Keras), para prever a rotatividade de funcionários. 

## Tecnologias Utilizadas

- **Linguagem:** Python  
- **Bibliotecas:** Pandas, NumPy, Seaborn, Matplotlib, Scikit-learn, TensorFlow (Keras), imbalanced-learn, XGBoost, Joblib  
- **Ferramentas:** Jupyter Notebook, Git, GitHub  
- **Dataset:** HR Analytics: Attrition Dataset (Kaggle) 

## Estrutura do Projeto
```
hr-analytics-turnover/
├── data/                # Conjuntos de dados utilizados na análise
│   ├── raw/             # Dados originais
│   │   └── Human_Resources.csv
│   ├── processed/       # Dados pré-processados (treino e teste)
│   └── models/          # Modelos de ML treinados e salvos
├── notebooks/           # Notebooks para análise exploratória, pré-processamento e modelagem
│   ├── EDA_HR.ipynb
│   ├── Pre_processamento_HR.ipynb
│   ├── Treinamento_Avaliacao_Modelo_HR.ipynb
│   └── Treinamento_e_Previsao_Melhores_Modelos_HR.ipynb
├── src/                 # Scripts auxiliares (se houver necessidade futura)
├── requirements.txt     # Arquivo com as dependências necessárias
├── README.md            # Resumo do projeto e explicações
├── LICENSE              # Licença de uso do projeto
├── venv/                # Ambiente virtual
├── Relatorio.md         # Relatório do projeto
├── .gitattributes       # Configurações do Git
├── imgs/                # Imagens geradas (gráficos, matrizes de confusão)
└── .idea/               # Configurações do projeto no IDE (opcional)
```

## Exploração e Análise de Dados (EDA)

### Características do Dataset
O conjunto de dados possui 1470 registros e 35 variáveis. Após a limpeza e transformação, foram identificadas 50 features numéricas para o modelo. 

- **Total de registros:** 1470 
- **Funcionários que saíram (Churn):** 237 (16.12%) 
- **Funcionários que permaneceram:** 1233 (83.88%) 
- **Média de idade:** 36.9 anos 
- **Quantidade de variáveis:** 35 (26 numéricas e 9 categóricas antes do One-Hot Encoding).

### Padrões e Insights Iniciais

- **Renda Mensal:** A renda mensal média de funcionários que saíram é de aproximadamente $4787,09, enquanto a de funcionários que permaneceram é de aproximadamente $6832,74, indicando que salários mais altos estão associados a menor rotatividade.  
- **Envolvimento no Trabalho (JobInvolvement), Satisfação no Trabalho (JobSatisfaction), Satisfação no Relacionamento (RelationshipSatisfaction) e Equilíbrio entre Vida Pessoal e Profissional (WorkLifeBalance):** Estas variáveis possuem um impacto na tendência de permanência, onde maior satisfação e equilíbrio geralmente resultam em menor rotatividade. 
- **Horas Extras (OverTime):** Funcionários que não trabalham horas extras têm menor probabilidade de churn. Isso pode ocorrer porque o excesso de trabalho pode levar à insatisfação e ao esgotamento.
- **Estado Civil (MaritalStatus_Single):** Funcionários solteiros apresentam maior taxa de rotatividade.
- **TotalWorkingYears, JobLevel, YearsInCurrentRole, Age, YearsWithCurrManager, StockOptionLevel, YearsAtCompany, PercentSalaryHike:** Todas essas variáveis apresentaram correlações significativas com a rotatividade. 

## Pré-processamento de Dados

As etapas de pré-processamento incluíram:

- **Transformação de Variáveis Binárias:** As colunas 'Attrition', 'OverTime' e 'Over18' foram convertidas para representações numéricas (0 e 1).
- **Remoção de Colunas Constantes/Irrelevantes:** 'EmployeeCount', 'EmployeeNumber', 'Over18' e 'StandardHours' foram removidas por serem constantes ou não informativas. 
- **One-Hot Encoding:** Variáveis categóricas como 'BusinessTravel', 'Department', 'EducationField', 'Gender', 'JobRole' e 'MaritalStatus' foram transformadas em representações numéricas usando One-Hot Encoding. 
- **Normalização:** As features numéricas foram normalizadas usando MinMaxScaler para garantir que todas estivessem na mesma escala, o que é importante para o desempenho de alguns modelos.  
- **Balanceamento de Classes:** Devido ao desbalanceamento da variável alvo ('Attrition'), a técnica SMOTE (Synthetic Minority Over-sampling Technique) foi aplicada para equalizar o número de amostras nas classes 'Ficou' e 'Saiu', resultando em 1233 registros para cada classe.  
- **Divisão Treino/Teste:** Os dados foram divididos em conjuntos de treino (75%) e teste (25%) de forma estratificada para manter a proporção das classes.

## Modelagem Preditiva

Foram treinados e avaliados diversos modelos de Machine Learning e Deep Learning. A otimização de hiperparâmetros foi realizada usando GridSearchCV com validação cruzada estratificada (5-Fold) e `scoring='f1'` para garantir um bom desempenho em ambas as classes.

### Modelos e Desempenho no Conjunto de Teste:

| Modelo                   | Acurácia | Precisão | Recall | F1-Score | Melhores Parâmetros (Otimizados) |
|--------------------------|----------|----------|--------|----------|----------------------------------|
| Regressão Logística      | 0.8136   | 0.7969   | 0.8409 | 0.8183   | {'C': 10, 'solver': 'liblinear'} |
| Random Forest Classifier | 0.9238   | 0.9485   | 0.8961 | 0.9215   | {'max_depth': None, 'min_samples_leaf': 1, 'min_samples_split': 2, 'n_estimators': 200} |
| K-Nearest Neighbors (KNN)| 0.8979   | 0.8302   | 1.0000 | 0.9072   | {'metric': 'manhattan', 'n_neighbors': 3, 'weights': 'distance'} |
| XGBoost Classifier       | 0.9287   | 0.9552   | 0.8994 | 0.9264   | {'colsample_bytree': 0.7, 'learning_rate': 0.05, 'max_depth': 5, 'n_estimators': 200, 'subsample': 0.9} |
| Deep Learning (Keras)    | 0.9157   | 0.8926   | 0.9448 | 0.9180   | (Arquitetura: Dense(64) -> Dropout(0.3) -> Dense(32) -> Dropout(0.3) -> Dense(1, sigmoid), otimizador Adam, loss binary_crossentropy) |

### Melhores Modelos Identificados
Com base no F1-Score, que é uma métrica balanceada para classes, os dois modelos com melhor desempenho foram:

- **XGBoost Classifier** (F1-Score: 0.9264)  
- **Random Forest Classifier** (F1-Score: 0.9215)

Estes modelos serão salvos e utilizados para futuras previsões.

## Conclusão e Impacto no Negócio

Este projeto demonstrou a capacidade de prever a rotatividade de funcionários com alta precisão utilizando modelos de Machine Learning. Com base nos modelos preditivos (especialmente XGBoost e Random Forest), a empresa pode:

- **Identificar perfis de risco:** A equipe de RH pode focar proativamente em funcionários com alta probabilidade de sair, intervindo antes que seja tarde.  
- **Ajustar políticas:** Implementar políticas que incentivem o equilíbrio entre trabalho e vida pessoal, limitar horas extras e promover um ambiente de trabalho saudável, como sugerido pela análise de 'OverTime'. 
- **Melhorar a satisfação:** Focar em fatores como renda mensal, satisfação no trabalho e envolvimento, que demonstraram impacto na retenção. 
- **Criar programas de retenção personalizados:** Desenvolver estratégias direcionadas para grupos vulneráveis, como funcionários solteiros ou com alta distância de casa.

Ao transformar esses insights em ações estratégicas, a corporação pode reduzir a rotatividade, aumentar a retenção e, consequentemente, melhorar a satisfação e produtividade dos funcionários.

## Próximos Passos

- Manutenção e monitoramento contínuo dos modelos em um ambiente de produção para garantir que continuem precisos com novos dados.  
- Exploração de técnicas avançadas para interpretabilidade de modelos (e.g., SHAP, LIME) para entender melhor os fatores que levam à rotatividade.  
- Considerar a coleta de dados adicionais sobre clima organizacional, feedback de funcionários e desempenho de gerentes para enriquecer o modelo.

## Como Executar o Projeto

```bash
# 1. Clone o repositório
git clone <seu-repo-url>
cd hr-analytics-turnover

# 2. Crie e ative o ambiente virtual (opcional, mas recomendado)
python -m venv venv

# No Windows:
.\venv\Scripts\activate

# No macOS/Linux:
source venv/bin/activate

# 3. Instale as dependências
pip install -r requirements.txt

# 4. Execute os notebooks na sequência no Jupyter Notebook
# Inicie pelo 'EDA_HR.ipynb', depois 'Pre_processamento_HR.ipynb',
# e finalmente 'Treinamento_Avaliacao_Modelo_HR.ipynb'
# e 'Treinamento_e_Previsao_Melhores_Modelos_HR.ipynb'
jupyter notebook
```

---

📌 **Autor:** Rafael Dutra (Haell)  
📬 **Contato:** rafaeldutrapro@gmail.com  
🚀 **LinkedIn:** [linkedin.com/in/seu-perfil](https://linkedin.com/in/seu-perfil)
