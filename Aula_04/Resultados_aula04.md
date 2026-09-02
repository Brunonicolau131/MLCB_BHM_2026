# Atividade 1: Código Semi-Pronto - (Versão 1 — KNN com Fallback e 10 Testes Digitados)
Instruções:
1 - Complete os trechos marcados com # TODO para montar a pipeline usando KNN ($K=3$).

2 - O loop deve solicitar obrigatoriamente 10 entradas manuais via input().

3 - Em caso de confiança abaixo do limiar (50%), acione o Fallback direcionando o cliente para a equipe humana.



# ATIVIDADE 1: CHATBOT VERSÃO 1 (KNN)

import numpy as np  
import pandas as pd

from sklearn.feature_extraction.text import TfidfVectorizer

from sklearn.neighbors import KNeighborsClassifier

from sklearn.pipeline import Pipeline

from sklearn.metrics import classification_report, confusion_matrix

from sklearn.model_selection import train_test_split

df = pd.read_csv('dataset_moveis_100.csv')

X_train, X_test, y_train, y_test = train_test_split(
    df['texto'],
    df['intencao'],
    test_size=0.30,
    random_state=42,
    stratify=df['intencao']
)

pipeline_knn = Pipeline([
    ('vectorizer', TfidfVectorizer(ngram_range=(1, 2))),
    ('classifier', KNeighborsClassifier(
        n_neighbors=3,
        metric='cosine'
    ))
])

pipeline_knn.fit(X_train, y_train)

y_pred = pipeline_knn.predict(X_test)

print("\n=== RELATÓRIO DE CLASSIFICAÇÃO ===")
print(classification_report(y_test, y_pred))

print("\n=== MATRIZ DE CONFUSÃO ===")
print(confusion_matrix(y_test, y_pred))


# TESTES DO CHATBOT


LIMIAR_CONFIANCA = 0.50

print("\n=== INICIANDO BATERIA DE TESTES (10 INPUTS OBRIGATÓRIOS) ===")

for i in range(1, 11):
    print(f"\n[Teste {i}/10]")
    
    # TODO 4: Solicitar frase do usuário
    frase = input("Digite a frase do cliente: ").strip()
    
    # TODO 5: Extrair probabilidades e classe prevista
    probs = pipeline_knn.predict_proba([frase])[0]

    maior_prob = np.max(probs)

    intencao = pipeline_knn.predict([frase])[0]
    
    # TODO 6: Regra de decisão
    if maior_prob >= LIMIAR_CONFIANCA:
        print(
            f"Intenção prevista: {intencao} | "
            f"Confiança: {maior_prob * 100:.1f}%"
        )
    
    else:
        print(
            f"FALLBACK - Confiança baixa: "
            f"{maior_prob * 100:.1f}%"
        )
        print(
            "Não consegui entender sua solicitação. "
            "Encaminhando para atendimento humano."
        )
 # Resultado terminal


 === RELATÓRIO DE CLASSIFICAÇÃO ===
                    precision    recall  f1-score   support

logistica_entregas       1.00      1.00      1.00         6
       reclamacoes       1.00      1.00      1.00         6
           suporte       1.00      1.00      1.00         6
 trocas_devolucoes       1.00      1.00      1.00         6
            vendas       1.00      1.00      1.00         6

          accuracy                           1.00        30
         macro avg       1.00      1.00      1.00        30
      weighted avg       1.00      1.00      1.00        30


=== MATRIZ DE CONFUSÃO ===
[[6 0 0 0 0]
 [0 6 0 0 0]
 [0 0 6 0 0]
 [0 0 0 6 0]
 [0 0 0 0 6]]

=== INICIANDO BATERIA DE TESTES (10 INPUTS OBRIGATÓRIOS) ===

[Teste 1/10]
Digite a frase do cliente: oi amor 
Intenção prevista: suporte | Confiança: 100.0%

[Teste 2/10]
Digite a frase do cliente: qual o maior numero de 100
Intenção prevista: logistica_entregas | Confiança: 66.7%

[Teste 3/10]
Digite a frase do cliente: quero pagar meus debitos 
Intenção prevista: reclamacoes | Confiança: 66.7%

[Teste 4/10]
Digite a frase do cliente: quero saber quando sera a entrega do meu produto
Intenção prevista: logistica_entregas | Confiança: 100.0%

[Teste 5/10]
Digite a frase do cliente: produto veio com defeito 
Intenção prevista: trocas_devolucoes | Confiança: 66.7%

[Teste 6/10]
Digite a frase do cliente: a minha vida ta muito estranha queria uma namorada 
Intenção prevista: reclamacoes | Confiança: 100.0%

[Teste 7/10]
Digite a frase do cliente: o palmeiras nao tem mundial
Intenção prevista: reclamacoes | Confiança: 66.7%

[Teste 8/10]
Digite a frase do cliente: a lua esta cheia 
Intenção prevista: logistica_entregas | Confiança: 66.7%

[Teste 9/10]
Digite a frase do cliente: boa tarde!
FALLBACK - Confiança baixa: 33.3%
Não consegui entender sua solicitação. Encaminhando para atendimento humano.

[Teste 10/10]
Digite a frase do cliente: se ta de palhaçada com minha cara
Intenção prevista: reclamacoes | Confiança: 100.0%





# ATIVIDADE 2: CHATBOT VERSÃO 2 ((Versão 2 — Decision Tree e 8 Testes Digitados))


import numpy as np
import pandas as pd

from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.tree import DecisionTreeClassifier
from sklearn.pipeline import Pipeline
from sklearn.metrics import classification_report, confusion_matrix
from sklearn.model_selection import train_test_split



df = pd.read_csv('dataset_moveis_100.csv')



X_train, X_test, y_train, y_test = train_test_split(
    df['texto'],
    df['intencao'],
    test_size=0.30,
    random_state=42,
    stratify=df['intencao']
)



pipeline_dt = Pipeline([
    ('vectorizer', TfidfVectorizer(ngram_range=(1, 2))),
    ('classifier', DecisionTreeClassifier(random_state=42))
])


pipeline_dt.fit(X_train, y_train)


y_pred = pipeline_dt.predict(X_test)


print("=" * 60)
print("=== AVALIAÇÃO DO MODELO - DECISION TREE ===")
print("=" * 60)

print("\n=== MATRIZ DE CONFUSÃO ===")
print(confusion_matrix(y_test, y_pred))

print("\n=== RELATÓRIO DE CLASSIFICAÇÃO ===")
print(classification_report(y_test, y_pred))



LIMIAR_CONFIANCA = 0.50


print("\n" + "=" * 60)
print("=== INICIANDO BATERIA DE TESTES (8 INPUTS OBRIGATÓRIOS) ===")
print("=" * 60)


for i in range(1, 9):

    print(f"\n[Teste {i}/8]")

    # Solicita a frase digitada pelo usuário
    frase = input("Digite a frase do cliente: ").strip()

    # Obtém as probabilidades das classes
    probs = pipeline_dt.predict_proba([frase])[0]

    # Obtém a maior probabilidade
    maior_prob = np.max(probs)

    # Obtém a intenção prevista
    intencao = pipeline_dt.predict([frase])[0]

    # Regra de decisão utilizando limiar de 50%
    if maior_prob >= LIMIAR_CONFIANCA:

        print(
            f"Intenção prevista: {intencao} | "
            f"Confiança: {maior_prob * 100:.1f}%"
        )

    else:

        print(
            f"Confiança baixa: {maior_prob * 100:.1f}%"
        )

        print(
            "Desculpe, não entendi sua solicitação. "
            "Encaminhando você para um atendente humano..."
        )


print("\n" + "=" * 60)
print("=== FINAL DOS 8 TESTES ===")
print("=" * 60)


 # Resultado terminal


=== MATRIZ DE CONFUSÃO ===
[[4 0 0 0 2]
 [1 2 0 3 0]
 [0 0 6 0 0]
 [0 0 0 5 1]
 [0 0 0 0 6]]

=== RELATÓRIO DE CLASSIFICAÇÃO ===
                    precision    recall  f1-score   support

logistica_entregas       0.80      0.67      0.73         6
       reclamacoes       1.00      0.33      0.50         6
           suporte       1.00      1.00      1.00         6
 trocas_devolucoes       0.62      0.83      0.71         6
            vendas       0.67      1.00      0.80         6

          accuracy                           0.77        30
         macro avg       0.82      0.77      0.75        30
      weighted avg       0.82      0.77      0.75        30



[Teste 1/8]
Digite a frase do cliente: oi amor
Intenção prevista: suporte | Confiança: 100.0%

[Teste 2/8]
Digite a frase do cliente: qual o maior numero de 100
Intenção prevista: vendas | Confiança: 100.0%

[Teste 3/8]
Digite a frase do cliente: quero pagar meus debitos
Intenção prevista: vendas | Confiança: 100.0%

[Teste 4/8]
Digite a frase do cliente: quero saber quando sera a entrega do meu produto
Intenção prevista: logistica_entregas | Confiança: 100.0%

[Teste 5/8]
Digite a frase do cliente: o palmeiras nao tem mundial
Intenção prevista: trocas_devolucoes | Confiança: 100.0%

[Teste 6/8]
Digite a frase do cliente: a lua esta cheia
Intenção prevista: trocas_devolucoes | Confiança: 100.0%

[Teste 7/8]
Digite a frase do cliente: boa tarde!
Intenção prevista: trocas_devolucoes | Confiança: 100.0%

[Teste 8/8]
Digite a frase do cliente: se ta de palhaçada com minha cara
Intenção prevista: vendas | Confiança: 100.0%



# Atividade 3: Relatório Comparativo de Modelos

# Relatório de Avaliação NLU - SAC Móveis Residenciais
## 1. Tabela Comparativa de Métricas (Dados de Teste)

ATIVIDADE 1: 

=== MATRIZ DE CONFUSÃO ===
[[6 0 0 0 0]
 [0 6 0 0 0]
 [0 0 6 0 0]
 [0 0 0 6 0]
 [0 0 0 0 6]]

ATIVIDADE 2: 

=== MATRIZ DE CONFUSÃO ===
[[4 0 0 0 2]
 [1 2 0 3 0]
 [0 0 6 0 0]
 [0 0 0 5 1]
 [0 0 0 0 6]]


------------ KNN (K=3) ------------
Acurácia Geral: 100%
F1-Score: 100%
Principais Erros na Matriz: não mostrou erro nas 30 frases dp database, foi reconhecido como se todas as frases fossem compatíveis. 

------------ Decision Tree ------------
Acurácia Geral: 76,67%
F1-Score: 75%
Principais Erros na Matriz: houve confusão entre trocas_devolucoes, reclamacoes e logistica_entregas.


 ## 2. Análise dos Testes de Entrada (`input()`)

 **Comportamento do KNN (10 testes):** [Como o KNN reagiu às variações das frases digitadas e ao fallback?]

 houve uma resposta ate que considerável, boa parte dos inputs teve uma porcentagem de confiança adequada, so o FALLBACK que deixou a desejar porem com uma melhora no database ja seria o suficiente para corrigir. 


 **Comportamento da Decision Tree (8 testes):** [Como a Árvore de Decisão se comportou em comparação ao KNN?]

Teve um péssimo desempenho pois deu confiança a todos os inputs e não apresentou nenhum fallback ao contrario do knn que teve um melhor desempenho 


## 3. Veredito Final

**Melhor modelo para este projeto:** [KNN ou Decision Tree]
KNN pois ele apresentou melhor desenpenho.

**Justificativa técnica:** [Explique a escolha com base nas métricas estatísticas e no comportamento do fallback]

O KNN apresentou os melhores resultados, alcançando 100% de acurácia e 100% de F1-Score, enquanto a Decision Tree obteve aproximadamente 76,67% de acurácia e 75% de F1-Score. A matriz de confusão do KNN também não apresentou erros, enquanto a Decision Tree confundiu diferentes classes, e em relação ao fallback o knn foi o unico que apresentou a ultilização do mesmo.
