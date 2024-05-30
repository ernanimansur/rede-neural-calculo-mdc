<h1 align="center">
  REDE NEURAL PARA CALCULAR O MÁXIMO DIVISOR COMUM
</h1>

<hr>

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=Completo&color=GREEN&style=for-the-badge)

# Sobre

 Projeto desenvolvido na disciplina Tópicos Especiais D - Inteligencia Artificial do curso de graduação em Física. O objetivo é aplicar os conhecimentos teóricos adquiridos em sala de aula.

 O objetivo principal foi desenvolver uma Rede Neural capaz de calcular o Máximo Divisor Comum (MDC) de dois números inteiros diferentes de zero.

# Funcionalidades e Entidades

## Funcionalidades
- ### Criar os dados para o treinamento
  A função create_data gera dados aleatórios no intervalo de 0 a 100 e os salva em um arquivo de texto. Se o parâmetro option é definido como 1, os mesmos dados são gerados para os conjuntos de treinamento, validação e teste. Mas se for definido como 2, são gerados dados diferentes para cada conjunto.

- ### Carregar os dados
  A função load_data carrega os dados do arquivo de texto e os divide em três conjuntos: 50% para treinamento, 25% para validação e 25% para teste.

- ### Previsão de Saída 
  A rede neural pode realizar previsões com base nos dados de entrada fornecidos após ter sido treinada.

## Entidades
- ### Rede Neural
  A arquitetura da rede neural utilizada consiste em uma sequência de camadas que incluem uma camada de Embedding seguida por três camadas LSTM e uma camada densa de saída.

  - **Camada de Embedding**: Camada de entrada que mapeia os números inteiros de entrada (valores entre 0 e 100) para vetores de tamanho 64.
  - **Camadas LSTM**: Três camadas LSTM com 64 unidades cada, configuradas para retornar sequências intercalares.
  - **Camada Densa**: Camada de saída que produz a previsão final.

- ### Compilação do Modelo
  O modelo foi compilado usando o otimizador Adam e a função de perda de erro quadrático médio (mean_squared_error). A métrica de   avaliação utilizada foi a precisão (accuracy).

- ### Treinamento do Modelo
  O modelo foi treinado por aproximadamente 100 épocas com um lote (batch) igual a 200. Os dados de treinamento e validação foram fornecidos durante o treinamento para monitorar o desempenho do modelo ao longo do tempo. Além disso, foi utilizado um callback de Early Stopping para interromper o treinamento se a perda não melhorasse após 10 épocas.

# Resultados

A rede neural foi treinada com um conjunto de dados contendo 1 milhão de exemplos, com valores variando de 1 a 100. Como há apenas 10.000 combinações possíveis dentro deste intervalo, o conjunto de dados pode conter essas combinações repetidas até 100 vezes.

### Primeiro Treinamento (option = 1)
No primeiro treinamento, utilizamos dados repetidos entre os conjuntos. 

![Imagem](img/graph%20dados%20iguais.png)

### Segundo Treinamento (option = 2)
No segundo treinamento, utilizamos dados diferentes para cada conjunto.

![Imagem2](img/graph%20dados%20diferentes.png)

Nos dois treinamentos, a precisão inicial foi de aproximadamente 60%, conforme mostrado nos gráficos. No entanto, quando testamos a rede neural com um conjunto de 10.000 dados contendo todas as combinações possíveis, a rede acertou 9.997 desses dados, resultando em uma precisão de 99,97%. Para um conjunto de 2.500 dados, onde todos os dados não foram usados no treinamento nem na validação, a rede neural acertou 2.098 desses dados, alcançando uma precisão de 83,92%.

Em ambos os treinamentos, pode ter ocorrido overfitting da rede devido à quantidade de dados repetidos. No primeiro treinamento, onde os dados são repetidos entre os conjuntos, a rede neural pode ter memorizado os resultados, o que pode explicar a precisão mais elevada. No segundo treinamento, onde os dados são diferentes para cada conjunto, a rede neural demonstrou uma capacidade significativa de aprendizado, embora ainda haja espaço para melhorias.

# Tecnologias utilizadas

- [Python](https://www.python.org)
- [Jupyter Notebook](https://jupyter.org)
- [NumPy](https://numpy.org)
- [Tensorflow](https://www.tensorflow.org)
- [Keras](https://keras.io)
