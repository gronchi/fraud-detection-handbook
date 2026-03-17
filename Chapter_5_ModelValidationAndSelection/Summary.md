# Resumo

A seleção de modelos consiste em selecionar o modelo que se espera fornecer os melhores desempenhos preditivos em dados futuros. Para um sistema de detecção de fraude, o melhor modelo pode ser definido como o modelo com os maiores desempenhos esperados de detecção de fraude no próximo bloco de transações.

A estimativa dos desempenhos do modelo em dados futuros é obtida por um procedimento de validação. Este capítulo cobriu diferentes tipos de procedimentos de validação e destacou os benefícios da **estratégia de validação prequencial** para estimar os desempenhos de detecção de fraude de um modelo de predição. A validação prequencial permite fornecer **estimativas precisas dos desempenhos de detecção de fraude em transações futuras, juntamente com intervalos de confiança**.

Os procedimentos de validação são, no entanto, tarefas computacionalmente intensivas. Eles exigem repetir os procedimentos de treinamento muitas vezes para avaliar os desempenhos de modelos de predição com diferentes hiperparâmetros e usando diferentes conjuntos de dados. O tempo de computação do procedimento de validação pode se tornar um gargalo quando os modelos precisam ser atualizados regularmente.

Um desafio fundamental para a seleção de modelos consiste em explorar eficientemente o espaço de hiperparâmetros do modelo a fim de melhor abordar o compromisso entre desempenhos de detecção de fraude e tempos de computação. Este capítulo cobriu a busca aleatória como uma estratégia possível para explorar de forma mais eficiente o espaço de hiperparâmetros do modelo. O próximo capítulo apresentará estratégias alternativas que podem abordar esse compromisso reduzindo o tamanho do conjunto de dados, em particular usando estratégias de subamostragem (Capítulo 6).


