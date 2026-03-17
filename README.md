# Aprendizado de Máquina Reprodutível para Detecção de Fraude de Cartão de Crédito - Manual Prático

## Acesso antecipado

Versão preliminar disponível em [https://gronchi.github.io/fraud-detection-handbook/Foreword](https://gronchi.github.io/fraud-detection-handbook/Foreword).

## Motivações

O aprendizado de máquina para detecção de fraudes em cartões de crédito (ML para CCFD) tornou-se um campo de pesquisa ativo. Isso é ilustrado pela [quantidade notável de publicações sobre o tópico na última década](https://gronchi.github.io/fraud-detection-handbook/Chapter_2_Background/MachineLearningForFraudDetection).

Não há dúvida de que a integração de técnicas de aprendizado de máquina em sistemas de detecção de fraude de cartão de pagamento melhorou muito sua capacidade de detectar fraudes com mais eficiência. Ao mesmo tempo, um grande problema neste novo campo de pesquisa é a falta de reprodutibilidade. Não existem benchmarks ou metodologias reconhecidas para comparar e avaliar as técnicas propostas.

Este livro tem como objetivo dar um primeiro passo nessa direção. Todas as técnicas e resultados fornecidos neste livro são reproduzíveis. As seções que incluem código são notebooks Jupyter, que podem ser executados localmente ou na nuvem usando [Google Colab](https://colab.research.google.com/) ou [Binder](https://mybinder.org/).

O público-alvo são estudantes ou profissionais interessados no problema específico de detecção de fraudes em cartões de crédito do ponto de vista prático. De modo mais geral, acreditamos que o livro também seja de interesse para profissionais de dados e cientistas de dados que lidam com problemas de aprendizado de máquina que envolvem dados sequenciais e/ou problemas de classificação desbalanceada.

Sumário provisório:

* Capítulo 1: Visão geral do livro
* Capítulo 2: Contexto
* Capítulo 3: Começando
* Capítulo 4: Métricas de desempenho
* Capítulo 5: Seleção de modelo
* Capítulo 6: Aprendizagem desbalanceada
* Capítulo 7: Aprendizagem profunda
* Capítulo 8: Interpretabilidade*

(*): Ainda não publicado.

## Rascunho atual

A escrita do livro está em andamento. Fornecemos através deste repositório Github um acesso antecipado ao livro. Em janeiro de 2022, os primeiros sete capítulos foram disponibilizados.

A versão online do rascunho atual deste livro está disponível [aqui](https://gronchi.github.io/fraud-detection-handbook/).

Qualquer comentário ou sugestão é bem-vindo. Recomendamos o uso de issues do Github para iniciar uma discussão sobre um tópico e o uso de pull requests para corrigir erros de digitação.


## Compilando o livro

Para ler e/ou executar este livro em seu computador, você precisará clonar este repositório e compilar o livro.

Este livro é um Jupyter book. Portanto, você precisará primeiro [instalar o Jupyter Book](https://jupyterbook.org/intro.html#install-jupyter-book).

A compilação foi testada com as seguintes versões de pacotes:

```
sphinxcontrib-bibtex==2.2.1
Sphinx==4.2.0
jupyter-book==0.11.2
```

Feito isso, este é um processo de duas etapas:

1. Clone este repositório:

```
git clone https://github.com/Fraud-Detection-Handbook/fraud-detection-handbook
```

2. Compile o livro

```
jupyter-book build fraud-detection-handbook
```

O livro estará disponível localmente em `fraud-detection-handbook/_build/html/index.html`.

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

Este livro é o resultado de dez anos de colaboração entre o [Machine Learning Group, Université Libre de Bruxelles, Bélgica](http://mlg.ulb.ac.be) e [Worldline](https://worldline.com).

* ULB-MLG, Investigador Principal: Gianluca Bontempi
* Worldline, Gerente de P&D: Frédéric Oblé

Gostaríamos de agradecer a todos os colegas que trabalharam neste tópico durante esta colaboração: Olivier Caelen (ULB-MLG/Worldline), Fabrizio Carcillo (ULB-MLG), Guillaume Coter (Worldline), Andrea Dal Pozzolo (ULB-MLG), Jacopo De Stefani (ULB-MLG), Rémy Fabry (Worldline), Liyun He-Guelton (Worldline), Gian Marco Paldino (ULB-MLG), Théo Verhelst (ULB-MLG).

A colaboração foi possível graças ao [Innoviris](https://innoviris.brussels), o Instituto de Pesquisa e Inovação da Região de Bruxelas, através de uma série de bolsas que começaram em 2012 e terminaram em 2021.

* 2018 a 2021. *DefeatFraud: Avaliação e validação de engenharia de features profundas e soluções de aprendizado para detecção de fraudes*. Programa Innoviris Team Up.
* 2015 a 2018. *BruFence: Aprendizado de máquina escalável para automatizar sistemas de defesa*. Programa Innoviris Bridge.
* 2012 a 2015. *Aprendizado de máquina adaptativo em tempo real para detecção de fraudes em cartões de crédito*. Programa Innoviris Doctiris.

A colaboração continua no contexto do projeto [Data Engineering for Data Science (DEDS)](https://deds.ulb.ac.be/) - no âmbito do programa Horizon 2020 - Marie Skłodowska-Curie Innovative Training Networks (H2020-MSCA-ITN-2020).