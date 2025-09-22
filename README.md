
# MVP - Machine Learning para Diagnóstico de Câncer de Mama

## Objetivo
A etapa de avaliação tem como objetivo analisar o desempenho dos modelos treinados em dados não vistos, ou seja, a base de teste. Isso garante que o modelo não apenas decorou os exemplos do treino, mas generalizou bem para novos casos.

Neste projeto, os modelos foram treinados com 70% dos dados e avaliados em 30% de dados reservados exclusivamente para teste.

## Dataset
- **Nome:** Breast Cancer Wisconsin (Diagnostic)
- **Origem:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29)
- **Tamanho:** ~50 KB
- **Características:** 569 amostras e 30 variáveis explicativas.

## Tecnologias
- Python 3.10
- Pandas, NumPy, Scikit-learn
- Matplotlib, Seaborn

## Escolha das Métricas de Avaliação
| **Métrica**                | **Por que usar**                                                                                                               |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Accuracy (Acurácia)**    | Mede a proporção de previsões corretas sobre o total de casos. Útil quando as classes estão balanceadas.                       |
| **Precision (Precisão)**   | Mede a qualidade das previsões **positivas**. Importante para evitar falsos positivos, que podem gerar alarmes desnecessários. |
| **Recall (Sensibilidade)** | Mede a capacidade do modelo em detectar **casos realmente malignos**. Essencial em diagnósticos médicos.                       |
| **F1-Score**               | Média harmônica entre *Precision* e *Recall*. Ideal quando precisamos equilibrar falsos positivos e falsos negativos.          |
| **Matriz de Confusão**     | Mostra o desempenho detalhado, evidenciando onde ocorrem erros de classificação.                                               |


## Estrutura do projeto
```
mvp_breast_cancer/
│
├── notebook_mvp.ipynb      # Notebook completo
├── README.md                # Documentação do projeto
└── requirements.txt         # Lista de dependências
```

## Treinamento Final do Modelo
Após comparar três modelos iniciais (Logistic Regression, Decision Tree, Random Forest), o Random Forest apresentou o melhor desempenho e foi selecionado para otimização com GridSearchCV.

Código usado para treino final:
final_model = grid.best_estimator_
final_model.fit(X_train_scaled, y_train)

## Teste com a Base de Teste
O modelo final foi avaliado usando o 30% de dados reservados para teste, que não participaram do treino.

y_pred_final = final_model.predict(X_test_scaled)

from sklearn.metrics import classification_report, confusion_matrix

print(classification_report(y_test, y_pred_final))
sns.heatmap(confusion_matrix(y_test, y_pred_final), annot=True, fmt='d', cmap='Blues')
plt.xlabel("Previsto")
plt.ylabel("Real")
plt.show()

## Resultados Obtidos
## Relatório de Classificação:
| Métrica                 | Valor             |
| ----------------------- | ----------------- |
| **Accuracy**            | **0.982** (98,2%) |
| **Precision (Maligno)** | **0.97**          |
| **Recall (Maligno)**    | **0.98**          |
| **F1-Score (Maligno)**  | **0.98**          |
| **F1-Score Geral**      | **0.98**          |

## Matriz de Confusão:
| **Real \ Previsto** | **Benigno (0)** | **Maligno (1)** |
| ------------------- | --------------- | --------------- |
| **Benigno (0)**     | 107             | 2               |
| **Maligno (1)**     | 1               | 61              |

## Os Resultados Fazem Sentido?
Sim, os resultados fazem sentido porque:

1. A acurácia está alta (98,2%), mas não é a única métrica analisada.
2. Recall alto (98%) indica que o modelo identifica quase todos os tumores malignos, essencial em saúde.
3. O número de falsos negativos é muito baixo (apenas 1 caso), mostrando boa capacidade de detecção.
4. O modelo não apresentou overfitting, pois a performance no treino foi similar ao teste.

💡 Apesar do excelente desempenho, em ambientes reais de saúde, modelos como este devem ser usados apenas como suporte ao diagnóstico, nunca como decisão final.

## Conclusões da Avaliação
O Random Forest otimizado se mostrou altamente eficaz na classificação de tumores de mama.
Mesmo com métricas excelentes, o único falso negativo exige atenção: em diagnósticos médicos, Recall deve ser maximizado.
Melhorias futuras:
Coletar mais dados clínicos para treinar o modelo.
Explorar Redes Neurais Profundas (Deep Learning) para aumentar Recall.
Aplicar técnicas de balanceamento como SMOTE, caso classes fiquem desbalanceadas em bases futuras.
Implementar um ensemble híbrido, combinando Random Forest com outros modelos.

## Resumo Final
O modelo atingiu:
1. 98,2% de acurácia,
2. 98% de Recall,
3. e apenas 1 falso negativo, mostrando grande potencial para ser aplicado como ferramenta auxiliar na detecção de câncer de mama, apoiando profissionais da saúde na tomada de decisões críticas.

---
**Autor:** Carlos Eduardo Silva dos Santos  
**Disciplina:** Privacidade e Segurança Cibernética  
**Professor:** Dr. André Serrano
