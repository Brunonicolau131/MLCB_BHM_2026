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
