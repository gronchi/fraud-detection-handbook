(Deep_learning)=
# Introdução

Os modelos mais amplamente utilizados para detecção de fraude na indústria ou em competições de aprendizado de máquina {cite}`kaggle2019fraud` são algoritmos de gradient boosting como XGBoost {cite}`chen2016xgboost`, LightGBM {cite}`ke2017lightgbm`, CatBoost {cite}`prokhorenkova2017catboost`, e modelos baseados em árvores como florestas aleatórias {cite}`breiman2001random`. Com o pré-processamento e a engenharia de características corretos, esses modelos fornecem resultados muito convincentes em sistemas de detecção de fraude do mundo real.

Os algoritmos de redes neurais são menos frequentemente considerados em benchmarks de fraude com dados estáticos, pois são mais difíceis de ajustar para alcançar um desempenho preditivo competitivo. No entanto, eles têm muitas vantagens que os tornam essenciais na caixa de ferramentas de um profissional de detecção de fraude.

## Por que usar uma rede neural para detecção de fraude?

Não há razão para assumir que uma rede neural feed-forward multicamada poderia superar florestas aleatórias ou XGBoost em conjuntos de dados estáticos, mas existem vários outros critérios importantes no problema de detecção de fraude além do desempenho de detecção.

### Aprendizado incremental

XGBoost e florestas aleatórias são ambos ensembles de árvores. As árvores de decisão geralmente não são incrementais porque exigem o conjunto de dados completo para calcular divisões ótimas e construir sua estrutura. Modificar uma divisão dado um novo conjunto de dados está longe de ser trivial. Em particular, como é construída hierarquicamente, atualizar uma condição em uma divisão alta de uma árvore torna diretamente a estrutura das subárvores inutilizável. Vale notar que diversas técnicas foram propostas para atualizar árvores de forma incremental, como árvores de Hoeffding {cite}`domingos2000mining`, árvores de Mondrian {cite}`lakshminarayanan2014mondrian`, ou ensembles incrementais de árvores {cite}`sun2018concept`. No entanto, os algoritmos baseados em árvores permanecem em sua maioria usados em um cenário de aprendizado em lote.

O aprendizado incremental é útil para detecção de fraude porque (1) é menos intensivo em recursos, pois os modelos podem ser atualizados frequentemente nos últimos blocos de dados em vez de ter que ser totalmente treinados do zero em todo o conjunto de dados a cada vez, e (2) elimina a necessidade de armazenar dados históricos por muito tempo, evitando assim problemas de regulamentação de dados.

As redes neurais têm a vantagem de serem incrementais por natureza, pois seu treinamento é iterativo e por instância.

### Aprendizado de representação e treinamento de ponta a ponta

Muitos estudos mostraram que, além das características brutas das transações, o uso de engenharia de características especializada (construção de agregados relevantes com base no histórico de transações do titular do cartão) melhora significativamente a taxa de detecção de fraude {cite}`bahnsen2016feature,dal2014learned`.

No entanto, esse processo tem limitações, principalmente a de depender de conhecimento especializado humano dispendioso. Houve tentativas de substituir a agregação manual por meio do aprendizado automático de representações {cite}`fu2016credit,jurgovsky2018sequence,dastidar2020nag`. Esses métodos são principalmente baseados em redes neurais (autoencoders, redes neurais convolucionais, redes de memória de longo e curto prazo).

Além disso, sobre essas representações aprendidas, usar uma rede neural feed-forward em vez de XGBoost ou florestas aleatórias é mais interessante, pois permite treinar todo o modelo (parte de representação + parte de classificação) de uma extremidade à outra.

### Aprendizado federado

O aprendizado federado consiste em compartilhar e treinar um modelo em múltiplos dispositivos, com cada dispositivo mantendo seus dados localmente. A ideia é compartilhar um modelo inicial entre os dispositivos, atualizá-lo localmente e federar frequentemente as atualizações de todos os dispositivos em um modelo global para todos. Em geral, a atualização global é calculada com métodos como a média federada {cite}`konevcny2016federated`, ou seja, por meio de uma média ponderada dos pesos de cada modelo local.

Ao contrário dos modelos baseados em árvores, redes neurais com a mesma arquitetura podem ter seus pesos calculados em média, o que as torna a primeira escolha quando se trata de aprendizado federado.

### Um modelo adicional para empilhamento

Embora as redes neurais possam alcançar um desempenho global próximo ao do XGBoost ou florestas aleatórias, isso não significa que esses diferentes modelos capturam os mesmos padrões de fraude. Em particular, experimentos frequentemente mostram que combinar uma abordagem baseada em árvores e uma rede neural em um ensemble de média simples pode levar, graças à diversidade, a um desempenho geral melhor.

### Mensagem principal

Além do desempenho de detecção, as redes neurais têm diversas vantagens para o problema de detecção de fraude em cartão de crédito: elas podem ser empilhadas a outros modelos, podem ser treinadas de forma incremental, podem ser facilmente federadas, permitem o aprendizado de representação e podem aprender representações e classificação juntos com o treinamento de ponta a ponta.

## Conteúdo do capítulo

Este capítulo cobre técnicas para construir redes neurais para o problema de detecção de fraude. A Seção 2 descreve considerações gerais para projetar um primeiro modelo (rede neural feed-forward totalmente conectada). As próximas seções exploram técnicas de aprendizado profundo mais avançadas para aprender representações úteis a partir dos dados. As Seções 3 e 4 descrevem respectivamente o uso de autoencoders e modelos sequenciais (redes neurais convolucionais, redes de memória de longo e curto prazo e mecanismo de atenção). Por fim, a Seção 5 descreve os resultados de todos os métodos em dados do mundo real, para comparação com os métodos em lote do capítulo 5.
