# --- RESULTADOS DO LAB 01 (AULA 03) ---
Mensagem: 'Preciso urgente da segunda via da fatura'
Intenção Predita: [segunda_via]
Vocabulário Filtrado (sem stopwords): ['2a', '2a via', 'aberto', 'acordo', 'acordo pagar', 'alterar', 'alterar endereço', 'app', 'atrasada', 'atualizo', 'atualizo dados', 'boleto', 'cadastramento', 'dados', 'dados residenciais', 'débito', 'débito aberto', 'dívida', 'emitir', 'emitir segunda', 'endereço', 'endereço cadastramento', 'fatura', 'fatura atrasada', 'fazer', 'fazer um', 'gostaria', 'gostaria alterar', 'negociar', 'negociar pagamento', 'no', 'no app', 'onde', 'onde atualizo', 'pagamento', 'pagamento dívida', 'pagar', 'pagar débito', 'posso', 'posso emitir', 'residenciais', 'residenciais no', 'segunda', 'segunda via', 'um', 'um acordo', 'via', 'via boleto', 'via fatura']

#========== PRODUÇÃO DO RELATÓRIO:==============
# 1 - Qual o impacto da remoção de stopwords no tamanho do vocabulário do modelo?
Com a remoção de stopwords o modelo vai filtrar o vocabulário deixando apenas as palavras com real importância, removendo o excesso de palavras genericas

# 2 - O que significa a configuração ngram_range=(1, 2) no TfidfVectorizer?
Ele instrui o modelo para analisar as palavras isoladamente e também analisar as palavras consecutivas em conjunto

# 3 - Como a remoção de palavras genéricas ajuda a evitar classificações incorretas?
Ajuda porque essas palavras aparecem em muitas frases e normalmente não indicam a intenção do usuário
 
 
 
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


  --- RESULTADOS DO LAB 03 (AULA 03) ---
Acuracia via Pipeline: 0.00%

--- Previsões ---
Mensagem: Como solicitar minhas ferias?
Intenção real: solicitar_ferias
Intenção predita: enviar_atestado

Mensagem: Quero agendar meu periodo de ferias
Intenção real: solicitar_ferias
Intenção predita: obter_holerite

# 2 - Qual é a grande vantagem de utilizar o objeto Pipeline no Scikit-Learn?
A principal vantagem do Pipeline é permitir organizar várias etapas do processo de Machine Learning em um único objeto.

# 3 - Por que o Pipeline evita que erros de pré-processamento ocorram entre treino e teste?
O Pipeline deixa tudo organizado e faz o pré-processamento sempre do mesmo jeito.
Ele evita que os dados de teste sejam usados durante o treinamento do modelo.
Assim, diminui os erros e deixa o resultado do modelo mais confiável.

