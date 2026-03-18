(ML_For_CCFD)=
# Aprendizado de máquina para detecção de fraude em cartão de crédito

A detecção de fraudes em cartões de crédito (CCFD) é como procurar agulhas em um palheiro. Requer encontrar, entre milhões de transações diárias, quais são fraudulentas. Devido à quantidade cada vez maior de dados, agora é quase impossível para um especialista humano detectar padrões significativos a partir dos dados de transação. Por esse motivo, o uso de técnicas de aprendizado de máquina agora é generalizado no campo de detecção de fraudes, onde a extração de informações de grandes conjuntos de dados é necessária {cite}`lucas2020credit,priscilla2019credit,carcillo2018beyond,dal2015adaptive`.

O Aprendizado de Máquina (ML) é o estudo de algoritmos que melhoram automaticamente por meio da experiência {cite}`bontempi2021statistical,friedman2001elements`. O ML está intimamente relacionado aos campos da Estatística, Reconhecimento de Padrões e Mineração de Dados. Ao mesmo tempo, surge como um subcampo da ciência da computação e da inteligência artificial e dá atenção especial à parte algorítmica do processo de extração de conhecimento. O ML desempenha um papel fundamental em muitas disciplinas científicas e suas aplicações fazem parte de nossa vida diária. É usado, por exemplo, para filtrar spam de e-mail, para previsão do tempo, em diagnóstico médico, recomendação de produtos, detecção de rosto, detecção de fraude, etc {cite}`dal2015adaptive,bishop2006pattern`.

A capacidade das técnicas de ML de enfrentar efetivamente os desafios levantados pela CCFD levou a um grande e crescente corpo de pesquisa na última década. Conforme relatado na Fig. 1, milhares de artigos relacionados a este tópico foram publicados entre 2010 e 2020, com cerca de 1500 artigos publicados apenas em 2020.

![alt text](images/ML_CCFD_GoogleScholar_2010_2020.png)
<p style="text-align: center;">
Fig. 1. Número de artigos publicados sobre o tema aprendizado de máquina e detecção de fraude em cartão de crédito entre 2010 e 2020. Fonte: Google Scholar.
</p>

Esta seção tem como objetivo fornecer uma visão geral deste corpo de pesquisa recente, resumindo os principais desafios de pesquisa e os principais conceitos de aprendizado de máquina que podem ser usados para resolvê-los.


## Pesquisas recentes

Para ter uma ideia do estado atual da pesquisa sobre ML para CCFD, pesquisamos no Google Scholar todas as revisões e pesquisas feitas sobre este tópico nos últimos cinco anos. Usando a seguinte pesquisa booleana: `("machine learning" OR "data mining") AND "credit card" AND "fraud detection" AND (review OR survey)` e restringindo o período de pesquisa de 2015 a 2021, identificamos dez revisões/pesquisas que relatamos na tabela a seguir.


| Título | Data| Referência |
|---|---|---|
|Uma pesquisa sobre técnicas de detecção de fraude em cartão de crédito: <br> Perspectiva orientada a dados e técnicas | 2016 | {cite}`zojaji2016survey`|
|Uma pesquisa sobre técnicas de detecção de fraude em cartão de crédito baseadas em aprendizado de máquina e inspiradas na natureza | 2017 | {cite}`adewumi2017survey`|
|Uma pesquisa sobre detecção de fraude em cartão de crédito <br> usando aprendizado de máquina | 2018 | {cite}`popat2018survey`|
|Uma revisão do estado da arte das técnicas de aprendizado de máquina <br> para pesquisa de detecção de fraudes | 2018 | {cite}`sinayobye2018state`|
|Detecção de fraude em cartão de crédito: Estado da arte | 2018 | {cite}`sadgali2018detection`|
|Uma pesquisa sobre diferentes métodos de mineração de dados e aprendizado de máquina <br> para detecção de fraude em cartão de crédito | 2018 | {cite}`patil2018survey`|
|Uma revisão sistemática das abordagens de mineração de dados <br> para detecção de fraude em cartão de crédito | 2018 | {cite}`mekterovic2018systematic`|
|Uma pesquisa abrangente sobre técnicas de aprendizado de máquina <br> e abordagens de autenticação de usuário <br>para detecção de fraude em cartão de crédito | 2019 | {cite}`yousefi2019comprehensive`|
|Detecção de fraude em cartão de crédito: uma revisão sistemática | 2019 | {cite}`priscilla2019credit`|
|Detecção de fraude em cartão de crédito usando aprendizado de máquina: <br> Uma pesquisa | 2020 | {cite}`lucas2020credit`|

Um conjunto de dez pesquisas em cinco anos pode ser considerado alto. O fato de tantas pesquisas terem sido publicadas em um período tão curto (em particular para as cinco pesquisas publicadas em 2018) reflete a rápida evolução do tópico de ML para CCFD e a necessidade que equipes de pesquisadores independentes sentiram em sintetizar o estado da pesquisa neste campo.

Dado o objetivo comum dessas pesquisas, vale a pena notar que um alto grau de redundância pode ser encontrado em termos de conteúdo. Em particular, todas elas enfatizam um conjunto comum de metodologias e desafios, que apresentamos nas próximas duas seções. Primeiro, cobrimos a metodologia de linha de base, ou seja, o fluxo de trabalho comum que é normalmente seguido em artigos que tratam do uso de técnicas de ML para abordar a CCFD. Em seguida, resumimos os desafios que caracterizam este tópico.

(ML_For_CCFD_Baseline_Methodology)=
## Metodologia de linha de base - Aprendizado supervisionado

Um grande número de técnicas de ML pode ser usado para resolver o problema da CCFD. Isso se reflete diretamente na enorme quantidade de artigos publicados sobre o tema na última década. Apesar desse grande volume de trabalhos de pesquisa, a maioria das abordagens propostas segue uma metodologia de ML de linha de base comum {cite}`patil2018survey,friedman2001elements,bishop2006pattern`, que resumimos na Fig. 2.

![alt text](images/baseline_ML_workflow.png)
<p style="text-align: center;">
Fig. 2. ML para CCFD: Metodologia de linha de base seguida pela maioria das abordagens propostas nas pesquisas recentes sobre o tema.
</p>

Na detecção de fraudes em cartões de crédito, os dados geralmente consistem em dados de transação, coletados, por exemplo, por um processador de pagamentos ou um banco. Os dados da transação podem ser divididos em três grupos {cite}`lucas2020credit,adewumi2017survey,VANVLASSELAER201538`

* Características relacionadas à conta: incluem, por exemplo, o número da conta, a data de abertura da conta, o limite do cartão, a data de validade do cartão, etc.
* Características relacionadas à transação: incluem, por exemplo, o número de referência da transação, o número da conta, o valor da transação, o número do terminal (ou seja, POS), a hora da transação, etc. Do terminal, também se pode obter uma categoria adicional de informações: características relacionadas ao comerciante, como seu código de categoria (restaurante, supermercado, ...) ou sua localização.
* Características relacionadas ao cliente: incluem, por exemplo, o número do cliente, o tipo de cliente (perfil baixo, perfil alto, ...), etc.

Em sua forma mais simples, uma transação de cartão de pagamento consiste em qualquer valor pago a um comerciante por um cliente em um determinado momento. Um conjunto de dados históricos de transações pode ser representado como uma tabela, como ilustrado na Fig. 3. Para detecção de fraudes, também é geralmente assumido que a legitimidade de todas as transações é conhecida (ou seja, se a transação foi genuína ou fraudulenta). Isso geralmente é representado por um rótulo binário, com valor 0 para uma transação genuína e valor 1 para transações fraudulentas.

![alt text](images/tx_table.png)
<p style="text-align: center;">
Fig. 3. Exemplo de dados de transação representados como uma tabela. Cada linha corresponde a uma transação de um cliente para um terminal. A última variável é o rótulo, que indica se a transação foi genuína (0) ou fraudulenta (1).
</p>

Dois estágios podem ser distinguidos no projeto de um sistema de detecção de fraudes baseado em ML. O primeiro estágio consiste em construir um modelo de predição a partir de um conjunto de dados históricos rotulados (Fig. 2, parte superior). Este processo é chamado de *aprendizado supervisionado*, uma vez que o rótulo das transações (genuínas ou fraudulentas) é conhecido. No segundo estágio, o modelo de predição obtido do processo de aprendizado supervisionado é usado para prever o rótulo de novas transações (Fig. 2, parte inferior).

Formalmente, um modelo de predição é uma função paramétrica com parâmetros $\theta$, também chamada de *hipótese*, que recebe uma entrada $x$ de um domínio de entrada $\mathcal{X}\subset \mathbb{R}^n$ e produz uma predição $\hat{y}=h(x,\theta)$ sobre um domínio de saída $\mathcal{Y} \subset \mathbb{R}$ {cite}`carcillo2018beyond,dal2015adaptive`:

$$
h(x,\theta): \mathcal{X} \rightarrow \mathcal{Y}
$$

O domínio de entrada $\mathcal{X}$ geralmente difere do espaço de dados brutos de transação por dois motivos. Primeiro, por razões matemáticas, a maioria dos algoritmos de aprendizado supervisionado exige que o domínio de entrada seja de valor real, ou seja, $\mathcal{X} \subset \mathbb{R}^n$, o que requer a transformação de características de transação que não são números reais (como timestamps, variáveis ​​categóricas, etc.). Em segundo lugar, geralmente é benéfico enriquecer os dados da transação com outras variáveis ​​que podem melhorar o desempenho de detecção do modelo de predição. Este processo é conhecido como *engenharia de recursos* (também conhecida como *transformação de recursos*, *extração de recursos* ou *pré-processamento de dados*).

Para detecção de fraudes, o domínio de saída $\mathcal{Y}$ geralmente é a classe prevista para uma determinada entrada $x$, ou seja, $\mathcal{Y}=\{0,1\}$. Dado que a classe de saída é binária, esses modelos de predição também são chamados de *classificadores binários*. Alternativamente, a saída também pode ser expressa como uma probabilidade de fraude, com $\mathcal{Y}=[0,1]$, ou mais geralmente como uma pontuação de risco, com $\mathcal{Y} = \mathbb{R}$, onde valores mais altos expressam riscos maiores de fraude.

O treinamento (ou construção) de um modelo de predição $h(x,\theta)$ consiste em encontrar os parâmetros $\theta$ que fornecem o melhor desempenho. O desempenho de um modelo de predição é avaliado usando uma função de perda, que compara o rótulo verdadeiro $y$ com o rótulo previsto $\hat{y}=h(x,\theta)$ para uma entrada $x$. Em problemas de classificação binária, uma função de perda comum é a função de perda zero/um $L_{0/1}$, que atribui uma perda igual a um no caso de predição errada e zero caso contrário:

$$
\begin{align}
L_{0/1}: \mathcal{Y} \times \mathcal{Y} &\rightarrow& \{0,1\} \\
y,\hat{y} &= &
\begin{cases}
    1,& \text{if } y \ne \hat{y}\\
    0,& \text{if } y=\hat{y}
\end{cases}
\end{align}
$$

```{note}
A função de perda zero/um é uma função de perda padrão para problemas de classificação binária. No entanto, não é adequada para problemas de detecção de fraude em cartão de crédito, devido ao alto desequilíbrio de classes (muito mais transações genuínas do que fraudulentas). Estimar o desempenho de um sistema de detecção de fraudes é um problema não trivial, que será abordado em profundidade no [Capítulo 4](Performance_Metrics).
```

Para obter uma estimativa justa do desempenho de um modelo de predição, uma prática metodológica importante, conhecida como *validação*, é avaliar o desempenho de um modelo de predição em dados que não foram usados ​​para treinamento. Isso é alcançado dividindo o conjunto de dados, antes do treinamento, em um *conjunto de treinamento* e um *conjunto de validação*. O conjunto de treinamento é usado para o treinamento do modelo de predição (ou seja, para encontrar os parâmetros $\theta$ que minimizam a perda no conjunto de treinamento). Uma vez que os parâmetros $\theta$ foram fixados, a perda é estimada com o conjunto de validação, o que dá uma estimativa melhor do desempenho que o modelo de predição deve ter em transações futuras (e não vistas).


```{note}
Cuidado especial deve ser tomado na prática ao dividir o conjunto de dados em conjuntos de treinamento e validação, devido à natureza sequencial das transações de cartão de crédito e ao atraso no relato de fraudes. Essas questões serão abordadas em detalhes no [Capítulo 5](Model_Validation_And_Selection).
```

O procedimento de aprendizado supervisionado normalmente consiste em treinar um conjunto de modelos de predição e estimar seus desempenhos usando o conjunto de validação. No final do procedimento, o modelo que se presume fornecer o melhor desempenho (ou seja, a menor perda no conjunto de validação) é selecionado e usado para fornecer previsões sobre novas transações (consulte a Fig. 2).

Existe uma vasta gama de métodos para projetar e treinar modelos de predição. Isso explica em parte a grande literatura de pesquisa sobre ML para CCFD, onde os artigos geralmente se concentram em um ou dois métodos de predição. A pesquisa de Priscilla et al. em 2019 {cite}`priscilla2019credit` fornece uma boa visão geral dos métodos de aprendizado de máquina que foram considerados para o problema da CCFD. A pesquisa deles cobriu cerca de cem artigos de pesquisa, identificando para cada artigo quais técnicas de ML foram usadas, veja a Fig. 4.

![alt text](images/ReviewMLforCCFD_2019_Table.png)
<p style="text-align: center;">
Fig. 4. Frequência de uso de técnicas de ML na CCFD. Fonte: Priscilla et al., 2019 {cite}`priscilla2019credit`. As referências fornecidas na tabela estão em {cite}`priscilla2019credit`.
</p>

A classificação das técnicas de aprendizado em categorias de 'alto nível' não é um exercício simples, pois muitas vezes existem conexões metodológicas, algorítmicas ou históricas entre elas. Priscilla et al. optaram por dividir as abordagens em quatro grupos: aprendizado supervisionado, aprendizado não supervisionado, aprendizado de conjunto e aprendizado profundo. Pode-se argumentar que o aprendizado de conjunto e o aprendizado profundo fazem parte do aprendizado supervisionado, uma vez que exigem que os rótulos sejam conhecidos. Além disso, o aprendizado profundo e as redes neurais podem ser considerados parte da mesma categoria.

Cobrir todas as técnicas de ML está fora do escopo deste livro. Em vez disso, nosso objetivo é fornecer uma estrutura de referência e reproduzível para a CCFD. Decidimos, com base em nossos trabalhos de pesquisa, cobrir cinco tipos de métodos: regressão logística (LR), árvores de decisão (DT), florestas aleatórias (RF), Boosting e redes neurais/aprendizado profundo (NN/DL). LR e DT foram escolhidos devido à sua simplicidade e interpretabilidade. RF e Boosting foram escolhidos por serem atualmente considerados o estado da arte em termos de desempenho. Os métodos NN/DL foram escolhidos por fornecerem direções de pesquisa promissoras.

(ML_For_CCFD_Challenges)=
## Visão geral dos desafios

A CCFD com ML é um problema notoriamente difícil. Resumimos abaixo os desafios comumente destacados nas revisões sobre o tópico {cite}`lucas2020credit,priscilla2019credit,mekterovic2018systematic,adewumi2017survey,zojaji2016survey`.

**Desequilíbrio de classes**: os dados da transação contêm muito mais transações legítimas do que fraudulentas: a porcentagem de transações fraudulentas em um conjunto de dados do mundo real é normalmente bem inferior a 1%. Aprender com dados desequilibrados é uma tarefa difícil, pois a maioria dos algoritmos de aprendizado não lida bem com grandes diferenças entre as classes. Lidar com o desequilíbrio de classes requer o uso de estratégias de aprendizado adicionais, como amostragem ou ponderação de perdas, um tópico conhecido como *aprendizagem desbalanceada*.

**Desvio de conceito**: os padrões de transação e fraude mudam com o tempo. Por um lado, os hábitos de consumo dos usuários de cartão de crédito são diferentes durante a semana, fins de semana, períodos de férias e, de modo mais geral, evoluem com o tempo. Por outro lado, os fraudadores adotam novas técnicas à medida que as antigas se tornam obsoletas. Essas mudanças dependentes do tempo nas distribuições de transações e fraudes são chamadas de *desvio de conceito*. O desvio de conceito requer o projeto de estratégias de aprendizado que possam lidar com mudanças temporais nas distribuições estatísticas, um tópico conhecido como *aprendizado online*. O problema do desvio de conceito é acentuado na prática pelos feedbacks atrasados (consulte a seção {ref}`Fraud_Detection_System`).

**Requisitos de tempo quase real**: os sistemas de detecção de fraude devem ser capazes de detectar rapidamente transações fraudulentas. Dado o volume potencialmente alto de dados de transação (milhões de transações por dia), podem ser necessários tempos de classificação tão baixos quanto dezenas de milissegundos. Este desafio está intimamente relacionado à *paralelização* e *escalabilidade* dos sistemas de detecção de fraude.

**Recursos categóricos**: os dados transacionais geralmente contêm vários recursos *categóricos*, como o ID de um cliente, um terminal, o tipo de cartão e assim por diante. Os recursos categóricos não são bem tratados pelos algoritmos de aprendizado de máquina e devem ser transformados em recursos numéricos. As estratégias comuns para transformar recursos categóricos incluem agregação de recursos, transformação baseada em grafos ou abordagens de aprendizado profundo, como incorporação de recursos.

**Modelagem sequencial**: cada terminal e/ou cliente gera um fluxo de dados sequenciais com características únicas. Um desafio importante da detecção de fraudes consiste em modelar esses fluxos para caracterizar melhor seus comportamentos esperados e detectar quando ocorrem comportamentos anormais. A modelagem pode ser feita agregando recursos ao longo do tempo (por exemplo, acompanhando a frequência média ou os valores de transação de um cliente) ou contando com modelos de predição sequencial (como modelos ocultos de Markov ou redes neurais recorrentes, por exemplo).

**Sobreposição de classes**: os dois últimos desafios podem ser associados ao desafio mais geral de sobreposição entre as duas classes. Apenas com informações brutas sobre uma transação, distinguir entre uma transação fraudulenta ou genuína é quase impossível. Esse problema é comumente resolvido usando técnicas de engenharia de recursos, que adicionam informações contextuais às informações de pagamento brutas.

**Medidas de desempenho**: as medidas padrão para sistemas de classificação, como o erro médio de classificação incorreta ou a AUC ROC, não são adequadas para problemas de detecção devido ao problema de desequilíbrio de classes e à complexa estrutura de custos da detecção de fraudes. Um sistema de detecção de fraudes deve ser capaz de maximizar a detecção de transações fraudulentas e, ao mesmo tempo, minimizar o número de fraudes previstas incorretamente (falsos positivos). Muitas vezes, é necessário considerar várias medidas para avaliar o desempenho geral de um sistema de detecção de fraudes. Apesar de seu papel central no projeto de um sistema de detecção de fraudes, atualmente não há consenso sobre qual conjunto de medidas de desempenho deve ser usado.

**Falta de conjuntos de dados públicos**: por razões óbvias de confidencialidade, as transações de cartão de crédito do mundo real não podem ser compartilhadas publicamente. Existe apenas um conjunto de dados compartilhado publicamente, que foi disponibilizado no Kaggle {cite}`Kaggle2016` por nossa equipe em 2016. Apesar de suas limitações (apenas dois dias de dados e recursos ofuscados), o conjunto de dados tem sido amplamente utilizado na literatura de pesquisa e é um dos mais votados e baixados no Kaggle. A escassez de conjuntos de dados para detecção de fraudes também é verdadeira com dados simulados: ainda não há simuladores ou conjuntos de dados simulados de referência disponíveis. Como resultado, a maioria dos trabalhos de pesquisa não pode ser reproduzida, tornando impossível a comparação de diferentes técnicas por pesquisadores independentes.