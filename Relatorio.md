# HR Analytics: Predição de Rotatividade de Funcionários para Retenção Estratégica

## Introdução

Este projeto tem como objetivo desenvolver um modelo preditivo para identificar quais funcionários possuem maior probabilidade de deixar a empresa. A análise de dados de Recursos Humanos (HR Analytics) é essencial para ajudar na retenção de talentos e na otimização da gestão de pessoas.

## Objetivo

Explorar o conjunto de dados fornecido, entender suas variáveis, identificar padrões e preparar os dados para o treinamento de modelos preditivos. O objetivo final é treinar e avaliar algoritmos como Regressão Logística, Random Forest e Deep Learning para prever a rotatividade de funcionários.

## Tecnologias Utilizadas

- **Linguagem:** Python
- **Bibliotecas:** Pandas, NumPy, Seaborn, Matplotlib, Scikit-learn, TensorFlow
- **Ferramentas:** Jupyter Notebook, Git, GitHub
- **Dataset:** [HR Analytics: Attrition Dataset (Kaggle)](https://www.kaggle.com/pavansubhashht/hr-analytics-attrition-dataset)

## Estrutura do Projeto

```
hr-analytics-turnover/
├── data/                # Conjuntos de dados utilizados na análise
│   ├── raw/
│   │   └── Human_Resources.csv
│   ├── processed/
├── notebooks/           # Notebooks para análise exploratória e modelagem
├── src/                 # Scripts caso precise
├── requirements.txt     # Arquivo com as dependências necessárias
├── README.md            # Resumo do proejto e explicaçoes
├── LICENSE              # Licença de uso do projeto
├── venv/                # Ambiente virtual
├── Relatorio.md         # Relatório do projeto
├── .gitattributes       # Configurações do Git
├── imgs/
└── .idea/                # Configurações do projeto no IDE
```

## Exploração e Análise de Dados

### Características do Dataset

- **Total de registros:** 1470
- **Funcionários que saíram:** 237 (16.12%)
- **Funcionários que permaneceram:** 1233 (83.88%)
- **Média de idade:** 36.9 anos
- **Quantidade de variáveis:** 35 (26 numéricas e 9 categóricas)

### Padrões Identificados

- **Idade:** Funcionários mais velhos têm menor probabilidade de sair.
- **Distância de Casa:** Funcionários que moram longe têm maior tendência de sair.
- **Estado Civil:** Solteiros apresentam maior taxa de rotatividade.
- **Renda Mensal:** Salários mais altos estão associados a menor rotatividade.
- **Número de Empresas Anteriores:** Quem trabalhou em muitas empresas tem maior tendência a sair.
- **Satisfação no Trabalho:** Funcionários insatisfeitos têm maior propensão a deixar a empresa.

### Correlações Significativas

- **TotalWorkingYears** tem forte correlação com **JobLevel** e **MonthlyIncome**.
- **YearsAtCompany** está fortemente correlacionado com **TotalWorkingYears** e **MonthlyIncome**.
- **YearsInCurrentRole** tem forte relação com **YearsAtCompany**.
- **Idade** e **MonthlyIncome** apresentam correlação de 0.5.

O modelo de **Deep Learning** apresentou melhor desempenho e será considerado para implantação.

## Conclusão e impacto no negócio até o momento

Com base neste modelo preditivo, a empresa pode:

- **Identificar perfis de risco** e agir preventivamente para reter talentos.
- **Ajustar políticas salariais** e de benefícios para reduzir a insatisfação.
- **Melhorar a gestão de talentos**, alocando recursos de forma estratégica.
- **Criar programas de retenção** personalizados para grupos vulneráveis.

## Próximos Passos

- Implementação dos algoritmos.

## Como Executar o Projeto

```bash
# Clone o repositório
git clone <seu-repo-url>

# Instale as dependências
pip install -r requirements.txt

# Execute os notebooks no Jupyter Notebook
```

---

📌 **Autor:** Rafael Dutra (Haell)  
📬 **Contato:** [rafaeldutrapro@gmail.com](mailto:rafaeldutrapro@gmail.com)  
🚀 **LinkedIn:** [linkedin.com/in/seu-perfil](https://linkedin.com/in/seu-perfil)
