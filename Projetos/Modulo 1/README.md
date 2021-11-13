# Projeto Módulo 1 - BootCamp Data Science Aplicada da Alura

![imagem](https://startupsaude.com/wp-content/uploads/2020/08/datasus-logo_display.png)

## O projeto

Olá! Este é meu primeiro projeto no BootCamp Data Science Aplicada, da Alura. Também é meu primeiro projeto mais formal no ramo da programação! Estou muito feliz de estar participando do curso e aprendendo sobre esta área que tanto me atrai. O projeto está no arquivo [Projeto_Modulo_1.ipynb](https://github.com/arturcgs/BootcampDataScienceAplicada3/blob/main/Projetos/Modulo%201/Projeto_Modulo_1.ipynb), espero q você possa aprender algo com ele.

## Os dados

Os dados analisados foram retiados do [tabnet](https://datasus.saude.gov.br/informacoes-de-saude-tabnet/), sistema do DATASUS que disponibiliza dados de saúde do Brasil. Comparei o número de internações e custo dessas internações entre o escopo Público e o Não Público.

Para a separação entre estes escopos, foi utilizado o filtro de Naturezas Jurídicas, no próprio tabnet. No escopo Público, foram selecionadas todas as entidades de admnistração pública. Já no Não Público, foram selecionadas todas as outras entidades, sendo elas empresariais, sem fim lucrativo, pessoas físicas e instituições extraterritoriais.

O filtro por ano/mes atendimento foi selecionado, para usarmos dados que correspondessem melhor a data em que os procedimentos foram realizados. Por isso, não incluí os dados de 2021, posto que, como ainda há atendimentos que não foram processados, eles não são tão confiáveis. Utilizei dados a partir de 2015, pois antes disso, havia dados faltando.

## Como foi feito

Após a importação e limpeza dos bancos de dados utilizados, foram feitos gráficos comparando os valores desejados.

## Conclusão

A análise realizada é somente inicial e incapaz de gerar conclusões concretas. Com isso em mente, parece haver uma relação entre a renda per capita de um estado e sua proporção de internações públicas e não públicas. Além disso, os gastos por internação pública tendem a ser menores do que por internação não pública.

Muito obrigado por ver meu projeto!
