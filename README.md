# 🚀 HR Analytics: Predição de Rotatividade de Funcionários para Retenção Estratégica

Bem-vindo ao meu projeto de Ciência de Dados, onde abordo um grande desafio em uma corporação multinacional: a rotatividade de funcionários! 🌍 Desenvolvi um modelo preditivo que identifica quais colaboradores têm maior chance de sair da empresa, permitindo decisões estratégicas para reduzir o turnover, aumentar a retenção e melhorar a satisfação dos funcionários. Utilizando o **HR Analytics: Attrition Dataset** do Kaggle, explorei os dados, realizei o pré-processamento, treinei múltiplos modelos de Machine Learning e obtive insights acionáveis. 📊

## 🌟 Visão Geral do Projeto Finalizado

Este projeto foi dividido em notebooks para garantir um fluxo de trabalho claro e eficiente:

* **`EDA_HR.ipynb`**: Foco na Análise Exploratória de Dados (EDA), visualizações e primeiros insights.
* **`Pre_processamento_HR.ipynb`**: Etapas de limpeza, transformação de variáveis (One-Hot Encoding, binarização), normalização e tratamento de desbalanceamento de classes (SMOTE).
* **`Treinamento_Avaliacao_Modelo_HR.ipynb`**: Treinamento, otimização de hiperparâmetros (GridSearchCV) e avaliação detalhada de diversos modelos de Machine Learning (Regressão Logística, Random Forest, KNN, XGBoost) e Deep Learning (Keras).
* **`Melhores_Modelos_HR.ipynb`**: Re-treinamento e salvamento dos dois melhores modelos, seguidos por uma demonstração prática de previsões em exemplos do dataset.

---

## 🔍 O Que Foi Feito (Detalhes por Fase)

### Fase 1: Exploração e Análise de Dados (EDA)
-   **Importação de Bibliotecas e Dataset**: Carreguei ferramentas do Python (Pandas, NumPy, Seaborn, Matplotlib) e o dataset com **35 variáveis** e **1.470 registros**, explorando sua estrutura. 🛠️
-   **Visualização dos Dados**: Converti variáveis categóricas como `'Attrition'`, `'OverTime'` e `'Over18'` para valores numéricos (0/1). Verifiquei dados ausentes (nenhum encontrado!) e identifiquei features com distribuição desigual, como `'MonthlyIncome'` e `'TotalWorkingYears'`. 📈
-   **Remoção de Features Irrelevantes**: Eliminei colunas constantes ou sem informação útil, como `'EmployeeCount'`, `'EmployeeNumber'`, `'Over18'` e `'StandardHours'`, para otimizar a análise. 🗑️
-   **Análise de Padrões de Rotatividade**: Descobri que cerca de **16.12%** dos funcionários saíram da empresa (**237 de 1470 registros**), evidenciando um dataset desbalanceado. Alguns insights:
    * Quem permaneceu é, em geral, mais velho, tem salários mais altos, mora mais perto do trabalho e relata maior satisfação. 👤
    * **Renda Média**: Funcionários que saíram: \$4787.09. Funcionários que ficaram: \$6832.74.
    * **Correlações fortes:** `'TotalWorkingYears'` com `'JobLevel'` e `'MonthlyIncome'`; `'YearsAtCompany'` com `'TotalWorkingYears'` e `'MonthlyIncome'`; `'YearsInCurrentRole'` com `'YearsAtCompany'`. 🔗
    * Funcionários solteiros, representantes de vendas, menos engajados e com menos experiência tendem a sair mais. 🚪
-   **Exploração de Relações**: Visualizei a distribuição de salários por cargo, entre outras métricas chave para entender padrões. 👩‍💼👨‍💼

### Fase 2: Pré-processamento de Dados
-   **Transformação de Variáveis Categóricas**: Utilizei One-Hot Encoding para converter colunas como `BusinessTravel`, `Department`, `EducationField`, `Gender`, `JobRole` e `MaritalStatus` em um formato numérico adequado para os modelos.
-   **Normalização de Features**: Apliquei `MinMaxScaler` para escalar as features numéricas, garantindo que todas as variáveis contribuíssem igualmente para o treinamento dos modelos.
-   **Balanceamento de Classes (SMOTE)**: Para lidar com o desbalanceamento significativo na variável alvo (`Attrition`), utilizei a técnica SMOTE, resultando em um conjunto de dados balanceado para o treinamento.
-   **Divisão Treino/Teste**: O dataset foi dividido em conjuntos de treino (75%) e teste (25%) com estratificação para manter a proporção das classes.

### Fase 3: Modelagem e Avaliação
-   Treinei e otimizei múltiplos modelos de Machine Learning: **Regressão Logística, Random Forest, K-Nearest Neighbors (KNN), XGBoost Classifier e um modelo de Deep Learning (Keras)**.
-   Utilizei `GridSearchCV` para otimização de hiperparâmetros com validação cruzada (`StratifiedKFold`) e `F1-Score` como métrica principal, dada a importância de balancear precisão e recall na predição de rotatividade.
-   **Resultados de Destaque:**
    * **XGBoost Classifier:** Melhor desempenho geral (F1-Score: 0.9264).
    * **Random Forest Classifier:** Segundo melhor desempenho (F1-Score: 0.9215).
    * Ambos os modelos demonstraram alta capacidade preditiva para identificar funcionários em risco de rotatividade.

### Fase 4: Salvando e Demonstrando Modelos (Exemplos Aléatórios)
-   Os dois melhores modelos (XGBoost e Random Forest) foram re-treinados com seus melhores parâmetros e **salvos** (`.pkl`) na pasta `data/models/`.
-   Um notebook dedicado (`Treinamento_e_Previsao_Melhores_Modelos_HR.ipynb`) foi criado para carregar esses modelos salvos e demonstrar sua capacidade de fazer previsões em exemplos aleatórios do conjunto de teste, comparando-as com os valores reais.

---

## 📸 Alguns Gráficos da EDA!
<h3>Histórico de Treinamento do Modelo Keras (Acurácia e Loss)</h3>
<img src="imgs/img.png" alt="Distribuição de Várias Features Numéricas" width="700" /> <br>
*Acurácia do modelo de Deep Learning.*

<h3>Boxplot de Salário Mensal por Cargo</h3>
<img src="imgs/graph1.png" alt="Distribuição de Salário Mensal por Cargo" width="700" /> <br>
*Visualização da variação salarial entre os diferentes cargos.*

<h3>Heatmap de Correlação entre Atributos</h3>
<img src="imgs/graph2.png" alt="Mapa de Calor de Correlação" width="700" /> <br>
*Mapa de calor mostrando a correlação entre as variáveis numéricas do dataset.*

<h3>Impacto das Horas Extras na Rotatividade de Funcionários</h3>
<img src="imgs/img2.png" alt="Mapa de Calor de Correlação" width="700" /> <br>
*Relação entre a realização de horas extras e a rotatividade de funcionários*

---

## 🚀 Como Explorar Este Projeto na sua máquina
1.  **Clone o repositório:**
    ```bash
    git clone <seu-repo-url>
    cd hr-analytics-turnover
    ```
2.  **Crie e ative o ambiente virtual (recomendado):**
    ```bash
    python -m venv venv
    # No Windows:
    .\venv\Scripts\activate
    # No macOS/Linux:
    source venv/bin/activate
    ```
3.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Execute os notebooks na sequência no Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```
    * Comece por `EDA_HR.ipynb` para as análises iniciais.
    * Prossiga para `Pre_processamento_HR.ipynb` para as etapas de preparação dos dados.
    * Continue com `Treinamento_Avaliacao_Modelo_HR.ipynb` para ver o treinamento e avaliação de todos os modelos.
    * Finalize com `Treinamento_e_Previsao_Melhores_Modelos_HR.ipynb` para o re-treinamento, salvamento e demonstração dos modelos finalistas.

---

## 🤝 Contato Profissional
Email: rafaeldutrapro@gmail.com <br>
LinkedIn: [linkedin.com/in/rafaelsantoshome](https://www.linkedin.com/in/rafaelsantoshome/)
