# Prefácio


Fraude de cartões de pagamento é um grande desafio para empresários, emissores de cartões de pagamento e empresas de serviços transacionais, causando perdas financeiras substanciais e crescentes a cada ano. De acordo com o Relatório Nilson de 2019, as perdas mundiais com fraudes de cartão aumentaram de 9,84 bilhões de dólares em 2011 para 27,85 bilhões de dólares em 2018, e estão projetadas para ultrapassar 40 bilhões de dólares em 2027 {cite}`NilsonReport2019`.

A detecção de padrões de fraude em transações com cartões de pagamento é conhecida por ser um problema muito difícil. Com a quantidade cada vez maior de dados gerados pelas transações com cartões de pagamento, tornou-se impossível para um analista humano detectar padrões fraudulentos em conjuntos de dados de transações, muitas vezes caracterizados por um grande número de amostras, muitas dimensões e atualizações online. Como resultado, o desenvolvimento de técnicas de detecção de fraude em cartões de pagamento tem se concentrado cada vez mais na última década em abordagens baseadas em técnicas de aprendizado de máquina (ML), que automatizam o processo de identificação de padrões fraudulentos a partir de grandes volumes de dados {cite}`priscilla2019credit,carcillo2019combining,sadgali2018detection,dal2015adaptive`.

A integração de técnicas de ML em sistemas de detecção de fraude de cartões de pagamento melhorou muito sua capacidade de detectar fraudes de forma mais eficiente e auxiliar os intermediários de processamento de pagamentos na identificação de transações ilícitas. Embora nos últimos anos o número de transações fraudulentas tenha continuado a aumentar, a porcentagem de perdas devido a fraudes começou a diminuir em 2016, uma tendência inversa que está associada à crescente adoção de soluções de ML {cite}`NilsonReport2019`. Além de ajudar a economizar dinheiro, a implementação de sistemas de detecção de fraude baseados em ML está se tornando hoje uma obrigação para instituições e empresas ganharem a confiança de seus clientes.

Uma questão amplamente reconhecida e recorrente neste novo campo de ML para detecção de fraude em cartões é a falta de reprodutibilidade da maioria dos trabalhos de pesquisa publicados sobre o tema {cite}`lucas2020credit,priscilla2019credit,patil2018survey,zojaji2016survey`. Por um lado, há uma falta de disponibilidade de dados de transações de cartões de pagamento, que não podem ser compartilhados publicamente por razões de confidencialidade. Por outro lado, os autores não se esforçam o suficiente para fornecer seu código and tornar seus resultados reproduzíveis.

Este livro tem como objetivo dar um primeiro passo na direção da reprodutibilidade na avaliação comparativa de técnicas de detecção de fraude em cartões de pagamento. Devido à grande quantidade de pesquisas publicadas no domínio, não foi possível revisar e implementar exaustivamente todas as técnicas existentes. Em vez disso, optamos por focar em algumas das técnicas que nos pareceram mais essenciais, com base em nossa colaboração de 10 anos com nosso parceiro industrial Worldline.

Algumas das técnicas apresentadas, como as que lidam com o desequilíbrio de classes ou conjuntos de modelos, são amplamente reconhecidas como partes essenciais do projeto de um sistema de detecção de fraude de cartão de crédito. Além disso, cobrimos tópicos menos documentados que acreditamos merecer mais atenção. Isso inclui, em particular, aspectos de design do processo de modelagem, como a escolha de métricas de desempenho e estratégias de validação, e estratégias promissoras de pré-processamento e aprendizado, como embeddings de features e redes neurais em geral.

Embora o livro se concentre na fraude de cartões de pagamento, acreditamos que a maioria das técnicas e discussões apresentadas neste livro podem ser úteis para outros profissionais que trabalham no tópico mais amplo de detecção de fraudes.

Com a reprodutibilidade dos experimentos como um dos principais impulsionadores deste livro, a escolha de um formato Jupyter Book pareceu mais adequada do que um formato de livro impresso tradicional. Em particular, todas as seções deste livro que incluem código são notebooks Jupyter, que podem ser executados de forma independente no computador do leitor, clonando o repositório do livro, ou online usando o Google Colab ou o Binder. Além disso, a natureza de código aberto do livro - totalmente disponível em um repositório público do Github - permite que os leitores abram discussões sobre o conteúdo do livro por meio de issues do Github ou proponham alterações ou melhorias com pull requests.

## Licença

O código nos notebooks é lançado sob uma [licença GNU GPL v3.0](https://www.gnu.org/licenses/gpl-3.0.en.html). A prosa e as imagens são lançadas sob uma [licença CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).


Se você deseja citar este livro, pode usar o seguinte:

<pre>
@book{leborgne2022fraud,
title={Reproducible Machine Learning for Credit Card Fraud Detection - Practical Handbook},
author={Le Borgne, Yann-A{\"e}l and Siblini, Wissam and Lebichot, Bertrand and Bontempi, Gianluca},
url={https://github.com/Fraud-Detection-Handbook/fraud-detection-handbook},
year={2022},
publisher={Universit{\'e} Libre de Bruxelles}
}
</pre>

## Autores

* [Yann-Aël Le Borgne](https://yannael.github.io/) (Autor de contato - yann-ael.le.borgne@ulb.be) - [Machine Learning Group - Université Libre de Bruxelles, Bélgica](http://mlg.ulb.ac.be).
* [Wissam Siblini](https://www.linkedin.com/in/wissam-siblini) - [Machine Learning Research - Worldline Labs](https://worldline.com)
* [Bertrand Lebichot](https://b-lebichot.github.io/) - [Interdisciplinary Centre for Security, Reliability and Trust  - Université du Luxembourg, Luxemburgo](https://wwwfr.uni.lu/snt)
* [Gianluca Bontempi](https://mlg.ulb.ac.be/wordpress/members-2/gianluca-bontempi/) - [Machine Learning Group - Université Libre de Bruxelles, Bélgica](http://mlg.ulb.ac.be)

## Agradecimentos

Este livro é o resultado de dez anos de colaboração entre o [Machine Learning Group,  Université Libre de Bruxelles, Bélgica](http://mlg.ulb.ac.be) e [Worldline](https://worldline.com)

* ULB-MLG, Pesquisador Principal: Gianluca Bontempi
* Worldline, Gerente de P&D: Frédéric Oblé

Gostaríamos de agradecer a todos os colegas que trabalharam neste tema durante esta colaboração: Olivier Caelen (ULB-MLG/Worldline), Fabrizio Carcillo (ULB-MLG), Guillaume Coter (Worldline), Andrea Dal Pozzolo (ULB-MLG), Jacopo De Stefani (ULB-MLG), Rémy Fabry (Worldline), Liyun He-Guelton (Worldline), Gian Marco Paldino (ULB-MLG), Théo Verhelst (ULB-MLG).

A colaboração tornou-se possível graças à [Innoviris](https://innoviris.brussels), o Instituto de Pesquisa e Inovação da Região de Bruxelas, por meio de uma série de subsídios que tiveram início em 2012 e foram concluídos em 2021.

* 2018 a 2021. *DefeatFraud: Assessment and validation of deep feature engineering and learning solutions for fraud detection*. Innoviris Team Up Programme. 
* 2015 a 2018. *BruFence: Scalable machine learning for automating defense system*. Innoviris Bridge Programme.
* 2012 a 2015. *Adaptive real-time machine learning for credit card fraud detection*. Innoviris Doctiris Programme. 

A colaboração prossegue no contexto do [projeto Data Engineering for Data Science (DEDS)](https://deds.ulb.ac.be/) — sob a estrutura do Horizon 2020 - Marie Skłodowska-Curie Innovative Training Networks (H2020-MSCA-ITN-2020).