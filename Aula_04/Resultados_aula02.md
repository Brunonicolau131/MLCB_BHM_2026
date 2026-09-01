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
