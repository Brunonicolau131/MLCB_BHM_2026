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

# 1 - Avaliem os resultados e verifiquem se os resultados foram corretos ou incorretos. Coloque a resposta no arquivo do relatório do laboratório
             --- RESULTADOS DO LAB 02 ---
          
    Mensagem de Teste: 'Gostaria de devolver o produto que comprei'
    Intenção Predita: troca_devolucao

      -- Distribuição de Probabilidades por Classe ---
      
              Classe [duvida_frete]: 27.99%
              Classe [rastrear_pedido]: 24.54%
              Classe [troca_devolucao]: 47.46%
# 2 - Detectado algum erro, qual seria a maneira mais correta de melhorar o resultado do algoritmo?
    Não a erro.

    
# 3 - Detalhe a função do Naive Bayes no algorítmo.
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


# LAB 04 - AULA 02 (MLCB): DESAFIO NLU PARA AGÊNCIA DE VIAGENS
--- DATASET ---
                                         mensagem          intencao
0       Quero comprar uma passagem para São Paulo  comprar_passagem
1          Gostaria de comprar uma passagem aérea  comprar_passagem
2   Preciso reservar um voo para o Rio de Janeiro  comprar_passagem
3       Quero adquirir uma passagem para Salvador  comprar_passagem
4                    Quero cancelar minha reserva  cancelar_reserva
5                 Preciso cancelar minha passagem  cancelar_reserva
6                  Como faço para cancelar o voo?  cancelar_reserva
7     Gostaria de cancelar minha reserva de hotel  cancelar_reserva
8                    Quero falar com um atendente   falar_atendente
9                Preciso conversar com uma pessoa   falar_atendente
10            Gostaria de falar com o atendimento   falar_atendente
11          Pode me encaminhar para um atendente?   falar_atendente

--- RESULTADOS DO TESTE ---
Mensagem: 'Gostaria de falar com o atendimento'
Intenção real: [falar_atendente]
Intenção predita: [falar_atendente]

Mensagem: 'Preciso reservar um voo para o Rio de Janeiro'
Intenção real: [comprar_passagem]
Intenção predita: [falar_atendente]

Mensagem: 'Como faço para cancelar o voo?'
Intenção real: [cancelar_reserva]
Intenção predita: [cancelar_reserva]

--- RESULTADOS DO LAB 04 ---
Mensagem: 'Gostaria de adquirir um voo para Recife' ==> Intenção Predita: [comprar_passagem]
Mensagem: 'Preciso desistir da minha reserva' ==> Intenção Predita: [cancelar_reserva]
Mensagem: 'Quero conversar com alguém do atendimento' ==> Intenção Predita: [falar_atendente]

# justificativa técnica
Escolhi o TF-IDF para transformar as frases em números e a Regressão Logística para identificar cada intenção.
Nos testes, o modelo conseguiu classificar as novas frases de forma adequada.
Como estou trabalhando com poucas frases, alguns resultados podem acabar não sendo perfeitos.
Para melhorar o modelo, seria interessante adicionar mais exemplos ao dataset.

  
