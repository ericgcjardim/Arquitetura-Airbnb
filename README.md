# Análise da Arquitetura do Airbnb

## Introdução

Este repositório é dedicado à análise da arquitetura do Airbnb, uma das maiores plataformas de acomodações e experiências de viagem do mundo. Para entender melhor as decisões arquiteturais adotadas pela empresa, é fundamental conhecer as características e necessidades do negócio.

## Caracteristicas do Airbnb

### Nicho de Mercado

O Airbnb atua como intermediador em aluguéis de curto prazo, variando de quartos individuais a casas inteiras, além de oferecer experiências de viagem, como passeios e atividades. 

### Número de Clientes

- O Airbnb tem mais de **150 milhões de usuários** em todo o mundo, que juntos já reservaram mais de **1 bilhão de estadias**. 
- Existem mais de 4 milhões de afitriões no Airbnb e mais de 6 milhões de listagens ativas.


### Acessos Simultâneos

- Por sua proporção o Airbnb deve lidar com milhões de acessos simultâneos, especialmente durante as temporadas de férias ou grandes eventos. 

### Requisitos de Segurança

- A plataforma que lida com informações pessoais, reservas e transações financeiras, consequentemente o Airbnb precisa adotar medidas rigorosas de segurança. Catherine Powell, chefe global de hospedagem do Airbnb revelou que os hóspedes da plataforma movimentaram, em 2022, R$ 26 bilhões apenas no Brasil.

### Localização

- O Airbnb opera em por volta de **220 países e regiões** em mais de **100 mil cidades**. Assim, a plataforma precisa lidar com questões como latência, disponibilidade e consistência dos dados, além de múltiplos idiomas, moedas e regulamentações locais.


### Infra de software

- A infra do Airbnb é embasada no modelo de arquitetura de micro-serviços, consistindo de diversos serviços separados por nicho e localidade conectados por APIS.Além disso, a infra da Airbnb também faz isso de duas Hive Clusters e uma Spark Cluster, a razão da utilização da estrtura de clusters se dá pelo alto volume de dados a serem processados e armazenados. segue um breve resumo da organização das clusters:

----- Gold Hive Cluster

  Projetado para execução de trabalhos críticos. Responsável também por armazenar as regras de negócio do sistema.

----- Silver Hive Cluster

  Projetado para ser mais flexível e armazenar processos de menor prioridade. Utilizado principalmente para consulta e análise de dados. Mais caracterizado por um ambiente DEV.

----- Spark Cluster

  Dedicado integralmente para armazenamento e processamento de dados com aprendizado de máquina.


  Além disso, outros fatores interessante da infra da Airbnb incluem a utilização de ferramentas de código open source, sempre contribuindo para comunidade quando possível.

  ## Conclusão

A compreensão destes dados e requisitos é fundamental para entender a arquitetura da Airbnb. À medida que prosseguimos com nossa análise, discutiremos como esses dados influenciam nas decisões arquiteturais da empresa. 




---

**Referencias**
- https://blog.quastor.org/p/airbnbs-architecture
- https://interviewnoodle.com/hotel-booking-system-design-airbnb-1283bbef71ac
- https://www.searchlogistics.com/learn/statistics/airbnb-statistics/
- https://oglobo.globo.com/rio/web-summit-rio/noticia/2023/05/hospedes-do-airbnb-movimentam-r-26-bilhoes-no-brasil-plataforma-calcula-gerar-10-mil-empregos.ghtml
- https://medium.com/airbnb-engineering/data-infrastructure-at-airbnb-8adfb34f169c
