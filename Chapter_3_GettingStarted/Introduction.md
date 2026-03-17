# Introdução


A melhor maneira de ter uma ideia dos desafios subjacentes ao projeto de um sistema de detecção de fraudes em cartões de crédito (FDS) é projetando um. Este capítulo apresenta uma implementação de um FDS de linha de base e cobre as principais etapas que precisam ser consideradas.

A [Seção 3.2](Transaction_data_Simulator) descreve primeiro um simulador simples para dados de transações de cartões de pagamento. Embora simplista, o simulador fornece um cenário suficientemente desafiador para abordar um problema típico de detecção de fraudes. Em particular, o simulador permitirá gerar conjuntos de dados que i) são altamente desbalanceados (baixa proporção de transações fraudulentas), ii) contêm variáveis ​​numéricas e categóricas (com características categóricas que possuem um número muito alto de valores possíveis) e iii) apresentam cenários de fraude dependentes do tempo.

A [Seção 3.3](Baseline_Feature_Transformation) e a [seção 3.4](Baseline_FDS) abordam as duas etapas principais de um processo de modelagem preditiva padrão: transformação de recursos e modelagem preditiva. Essas seções fornecerão algumas estratégias de linha de base para realizar transformações de recursos significativas e construir um primeiro modelo preditivo cuja precisão servirá como referência no resto do livro.

Finalmente, na [seção 3.5](Baseline_FDS_RealWorldData), aplicamos essa metodologia de linha de base (transformação de recursos e modelagem preditiva) a um conjunto de dados do mundo real de transações com cartão e ilustramos sua capacidade de detectar transações fraudulentas de forma eficaz.