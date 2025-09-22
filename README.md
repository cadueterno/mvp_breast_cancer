
# MVP - Machine Learning para Diagnóstico de Câncer de Mama

## Objetivo
Desenvolver um modelo de aprendizado supervisionado para classificar tumores como **malignos** ou **benignos**, utilizando características obtidas de exames médicos.

## Dataset
- **Nome:** Breast Cancer Wisconsin (Diagnostic)
- **Origem:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29)
- **Tamanho:** ~50 KB
- **Características:** 569 amostras e 30 variáveis explicativas.

## Tecnologias
- Python 3.10
- Pandas, NumPy, Scikit-learn
- Matplotlib, Seaborn

## Como rodar o notebook
1. Clone este repositório:
   ```bash
   git clone https://github.com/SEU_USUARIO/mvp_breast_cancer.git
   ```
2. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```
3. Abra no Google Colab ou Jupyter Notebook e execute todas as células.

## Estrutura do projeto
```
mvp_breast_cancer/
│
├── notebook_mvp.ipynb      # Notebook completo
├── README.md                # Documentação do projeto
└── requirements.txt         # Lista de dependências
```

## Conclusões
O modelo Random Forest otimizado atingiu **98% de acurácia** na base de teste, sendo escolhido como a melhor solução inicial para este problema.

---
**Autor:** Carlos Eduardo Silva dos Santos  
**Disciplina:** Privacidade e Segurança Cibernética  
**Professor:** Dr. André Serrano
