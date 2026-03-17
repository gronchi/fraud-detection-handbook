(Credit_Card_Fraud_Scenarios)=
# Cenários de fraude de cartão de crédito

As perdas financeiras mundiais causadas por atividades fraudulentas com cartões de crédito valem dezenas de bilhões de dólares. Um em cada dez americanos já foi vítima de fraude de cartão de crédito (valor médio de US$ 399), de acordo com o Statistic Brain Research Institute {cite}`StatisticBrain2018`. De acordo com o último relatório do Banco Central Europeu (BCE) {cite}`ECB2020`, o nível total de perdas por fraude com cartões totalizou 1,8 bilhão de euros em 2018 na Área Única de Pagamentos em Euros (SEPA).

Existe uma grande variedade de cenários que podem levar um fraudador a realizar com sucesso pagamentos fraudulentos com um cartão de crédito. Atualmente, não existe uma taxonomia definitiva sobre os tipos de fraude com cartão de crédito, embora certos padrões sejam conhecidos por ocorrer com mais frequência do que outros. Deve-se notar também que a detecção de fraudes é um jogo de gato e rato, onde os padrões fraudulentos mudam com o tempo. À medida que a tecnologia evolui, tanto em termos de prevenção de fraudes quanto de facilidade de uso dos sistemas de pagamento, o mesmo acontece com as técnicas dos fraudadores. Eles se adaptam, passando dos alvos antigos (e agora corrigidos) para a vulnerabilidade das novas tecnologias. Eles também se beneficiam das constantes mudanças no volume e nas características das transações genuínas.

## Fraudes com cartão presente vs. com cartão não presente

É útil distinguir dois cenários de transação. O primeiro, chamado de cenários com *cartão presente* (CP), refere-se a cenários em que um cartão físico é necessário, como transações em uma loja (também conhecida como ponto de venda - POS) ou transações em um caixa eletrônico (por exemplo, em um caixa eletrônico - ATM). O segundo, chamado de cenários com *cartão não presente* (CNP), refere-se a cenários em que um cartão físico não precisa ser usado, o que engloba pagamentos realizados na Internet, por telefone ou por correio.

Essa distinção é importante, pois as técnicas usadas para comprometer um cartão variam, dependendo se uma cópia física do cartão precisa ser produzida ou não. Mais importante, os fraudadores estão recentemente mais propensos a explorar as deficiências dos cenários CNP do que os de CP, provavelmente porque os cenários de CP existem há mais de duas décadas e se tornaram bastante robustos a ataques de fraude, principalmente graças à tecnologia EMV (Europay Mastercard e Visa, ou seja, cartões com chip). Outra razão é que considerações simples sobre barreiras físicas muitas vezes podem ajudar a prevenir fraudes de CP. Conforme declarado no relatório Nilson de 2019, os cenários CNP foram responsáveis por 54% de todas as perdas por fraude no ano de 2018, embora representem menos de 15% de todo o volume de compras em todo o mundo (CNP + POS + ATM) {cite}`NilsonReport2019`. A proporção de fraude CNP é ainda maior na Europa e foi relatada como sendo responsável por 79% de todas as transações de cartões emitidos na SEPA no relatório de 2020 sobre fraude com cartões do Banco Central Europeu {cite}`ECB2020`, conforme relatado na figura abaixo.

![alt text](./images/SEPA_FraudVolumePerType.png)
<p style="text-align: center;">
Fig. 1. Evolução do valor total da fraude com cartões emitidos na SEPA. <br>As fraudes com cartão não presente representam a maioria das fraudes relatadas.
</p>

### Fraudes com cartão presente

As fraudes com cartão presente ocorrem quando um fraudador consegue realizar uma transação fraudulenta bem-sucedida usando um cartão de pagamento físico, seja em um caixa eletrônico ou em um POS. Nesse cenário, os cenários de fraude são geralmente categorizados como *cartões perdidos ou roubados*, *cartões falsificados* e *cartão não recebido*.

**Cartão perdido ou roubado**: O cartão pertence a um cliente legítimo e cai nas mãos de um fraudador após uma perda ou roubo. Este é o tipo mais comum de fraude no cenário de fraude com cartão presente e permite que um fraudador faça transações, desde que o cartão não seja bloqueado pelo seu proprietário legítimo. Nesse cenário, o fraudador geralmente tenta gastar o máximo possível e o mais rápido possível.

**Cartão falsificado**: Um cartão falso é produzido por um fraudador, imprimindo as informações de um cartão. Tais informações são geralmente obtidas por *clonagem* do cartão do cliente legítimo, sem que ele perceba. Como os proprietários legítimos não sabem da existência de uma cópia de seu cartão, a origem da fraude pode ser mais difícil de identificar, pois o fraudador pode esperar muito tempo antes de usar o cartão falso. O uso crescente da tecnologia chip e PIN (também conhecida como EMV) reduziu esse tipo de fraude.

**Cartão não recebido**: O cartão foi interceptado por um fraudador na caixa de correio de um cliente legítimo. Isso pode acontecer se um cliente solicitar um novo cartão, que é interceptado, ou if um fraudador consegue solicitar um novo cartão sem o conhecimento do cliente legítimo (por exemplo, acessando fraudulentamente sua conta bancária) e o entrega em um endereço diferente. No primeiro caso, os clientes podem avisar rapidamente o banco que o cartão não foi recebido e bloqueá-lo. O último caso pode ser mais difícil de detectar, pois o cliente não sabe que um novo cartão foi solicitado.

As estatísticas sobre a proporção desses tipos de fraude em cenários com cartão presente foram relatadas pelo Banco Central Europeu para 2018, consulte o gráfico abaixo {cite}`ECB2020`.

![alt text](./images/SEPA_FraudType_CardPresent.png)
<p style="text-align: center;">
Fig. 2. Evolução e detalhamento do valor da fraude com cartão presente por categoria na SEPA.
</p>

As principais categorias de fraudes são *perdidos e roubados* e *cartões falsificados*, enquanto os cenários de *cartão não recebido* representam uma proporção muito pequena das perdas por fraude. É importante notar que essas proporções de fraude são aproximadamente as mesmas, quer os pagamentos tenham sido feitos em um caixa eletrônico ou em um POS, e que, no geral, o valor das fraudes em ambientes com cartão presente tende a diminuir.

### Fraudes com cartão não presente

O cartão não presente refere-se à categoria geral de fraudes realizadas remotamente, seja por correio, telefone ou na Internet, usando apenas algumas das informações presentes em um cartão.

No geral, há menos estatísticas disponíveis sobre a causa de tais fraudes. Por exemplo, ao contrário das fraudes com cartão presente, o Banco Central Europeu exige apenas que os operadores de esquemas de pagamento com cartão relatem as perdas totais por fraude CNP.

Sabe-se, no entanto, que a maioria das fraudes CNP é uma consequência direta de credenciais de pagamento obtidas ilegalmente (por exemplo, números de cartão), seja de violações de dados ou, às vezes, diretamente dos titulares dos cartões (por exemplo, via phishing, mensagens de texto fraudulentas). Também é importante notar que tais credenciais geralmente não são usadas diretamente, mas sim colocadas à venda em mercados clandestinos da web (a *dark web*) e posteriormente usadas por grupos criminosos. Os criminosos que roubam dados geralmente são um grupo diferente dos criminosos que perpetram fraudes {cite}`ECB2020,NilsonReport2019`.

Os dados geralmente envolvidos em fraudes com cartão não presente incluem o número do cartão, a data de validade do cartão, o código de segurança do cartão e as informações de cobrança pessoal (como o endereço do titular do cartão).