 # LAB 02 - AULA 03 (MLCB): Matriz de Confusão e Métricas

--- RESULTADOS DO LAB 02 (AULA 03) ---

--- Relatório de Classificação ---
                     precision    recall  f1-score   support

horario_atendimento       0.50      1.00      0.67         1
        localizacao       0.00      0.00      0.00         1
    troca_devolucao       0.00      0.00      0.00         1

           accuracy                           0.33         3
          macro avg       0.17      0.33      0.22         3
       weighted avg       0.17      0.33      0.22         3

--- Matriz de Confusão ---
[[1 0 0]
 [1 0 0]
 [0 1 0]]


# 1 - O que representam as métricas Precision, Recall e F1-Score no relatório?

  precision e quando buscamos uma precisão entre os dados inseridos, ou seja com base nas mensagem e interações qual a que a corresponde com precisão.  
  recall indica quem realmente pertence a uma determinada interação.

  f1- Score combina os dois anteriores tirando uma metrica.

# 2 - Como interpretar a diagonal principal da Matriz de Confusão?

  --- Matriz de Confusão ---
  [[1 0 0]
  [1 0 0]
  [0 1 0]]

  com base nessa matriz apresentada podemos acompanhar quantos acertos foram feitos ou seja caba coluna representa uma interação que com diz com a mensagem apresentada.

# 3 - Por que a acurácia isolada pode ser enganosa quando temos classes desbalanceadas?

  pois ele apresenta uma proporção de previsão, que se a mais itens em um dos lados não haverá proporção assim causando esse engano.
