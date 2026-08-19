# LAB 01 - AULA 02 (MLCB): Classificador de Intenções

  
  # 1 - Avaliem os resultados e verifiquem se os resultados foram corretos ou incorretos. Coloque a resposta no arquivo do relatório do laboratório
      
            --- RESULTADOS DO LAB 01 ---
      Mensagem: 'Quero consultar quanto dinheiro tenho' ==> Intenção Predita: [fazer_pix]
      Mensagem: 'Pode me ajudar a fazer um pix?' ==> Intenção Predita: [fazer_pix]
      Mensagem: 'Gostaria de cancelar meu cartão de crédito' ==> Intenção Predita: [cancelar_conta]

      Os resultados foram incorretos, a primeira mensagem a "intenção Predita:" deveria ser consultar_saldo, e como visto a cima nao foi oque obtivemos.
      

  # 2 - Detectado algum erro, qual seria a maneira mais correta de melhorar o resultado do algoritmo?

      Para corrigir seria necessário adicionar uma frase parecida ou ate mesmo a própria frase no dataset assim obtendo o seguinte resultado:

            --- RESULTADOS DO LAB 01 ---
      Mensagem: 'Quero consultar quanto dinheiro tenho' ==> Intenção Predita: [consultar_saldo]
      Mensagem: 'Pode me ajudar a fazer um pix?' ==> Intenção Predita: [fazer_pix]
      Mensagem: 'Gostaria de cancelar meu cartão de crédito' ==> Intenção Predita: [cancelar_conta]



  # 3 - Detalhe a função do LogisticRegression no algorítmo.

      o logisticRegression realiza a verificação de onde a frase se encaixa ou seja:

      modelo = LogisticRegression()    -      atribuímos o LogistcRegression()

      modelo.fit(X_train_vec, y_train)    -        catalogamos os dataset que possuímos para realizar uma base de comparação com as futuras frases

      predicoes = modelo.predict(novas_frases_vec)    -      após elas serem vetorizadas e realizado a opreção para saber qual a intanção da frase.


# LAB 02 - AULA 02 (MLCB): Naive Bayes e Probabilidades

             --- RESULTADOS DO LAB 02 ---
          
    Mensagem de Teste: 'Gostaria de devolver o produto que comprei'
    Intenção Predita: troca_devolucao

      -- Distribuição de Probabilidades por Classe ---
      
              Classe [duvida_frete]: 27.99%
              Classe [rastrear_pedido]: 24.54%
              Classe [troca_devolucao]: 47.46%

  # Detalhe a função do Naive Bayes no algoritmo:
    Naive Bayes analisa a mensagem e verifica com qual categoria ela mais se parece.
    Depois, ele calcula as probabilidades e escolhe a intenção mais provável como resposta



# LAB 03 - AULA 02 (MLCB): Preencha os blocos TODO

  # 1 - Qual foi a acurácia obtida pelo modelo no conjunto de teste e por que, em um dataset tão pequeno (9 exemplos), essa métrica pode ser enganosa?
    
    Acurácia do Modelo: 0.00%
    
    0% porque não temos tanto exemplos a serem usados para treinar o modelo.
    Sim o dataset pequeno como esse pode apresentar uma métrica enganosa.

    
  # 2 - Como o modelo de Árvore de Decisão (DecisionTreeClassifier) toma a decisão de separar as intenções do usuário?
      Com base no dataset, criando divisões de treino que permitem com base no vector se a frase apresentada ela e ou nao verdadeira assim criando a     arvore de decisões com base nas palavras e conjuntos de palavras apresentadas.

  # 3 - Qual é o risco de utilizar uma Árvore de Decisão sem limite de profundidade (max_depth) em datasets de texto maiores?
      um maior volume de processamento, e dependendo do tipo de frase, como o uma arvore de decisão, só foca em captar a intenção de uma determinada frase o inicio da frase, já e mais do que o suficiente para poder saber qual a sua intenção, assim sendo necessário o uso do max_depth 
  
