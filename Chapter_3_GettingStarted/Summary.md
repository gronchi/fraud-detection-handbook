(Summary_Performance_Metrics)=
# Resumo

Este capítulo ilustrou que o design de um sistema de detecção de fraude de *linha de base* pode ser alcançado usando estratégias simples de pré-processamento e classificadores padrão de aprendizado de máquina. Em particular, conseguimos obter desempenhos de detecção de fraude bem acima dos de um classificador aleatório.

O capítulo, no entanto, apenas arranhrou a superfície de como abordar um problema de detecção de fraude. Como veremos, um grande número de técnicas mais avançadas pode ser utilizado para melhorar os desempenhos. Os desempenhos podem ser abordados em termos de acurácias de detecção de fraude, mas também em termos de requisitos computacionais (memória/tempos de execução). Este último é, na prática, importante durante o treinamento, pois os sistemas de detecção de fraude precisam lidar com grandes volumes de dados (muito maiores do que os utilizados neste exemplo de linha de base) e também durante a inferência para processamento em tempo real ou quase em tempo real. Em geral, deve-se considerar cuidadosamente os compromissos entre acurácia e requisitos computacionais.

Os capítulos avançados cobrirão em detalhes os possíveis caminhos que podem ser explorados para melhorar a abordagem de linha de base proposta.

Antes disso, o foco dos próximos dois capítulos abordará mais especificamente a metodologia experimental, ou seja, quais medidas de desempenho devem ser utilizadas e como estas podem ser estimadas. Essas questões são fundamentais para encontrar uma forma objetiva de comparar os desempenhos de diferentes sistemas de detecção de fraude e identificar o de melhor desempenho.
