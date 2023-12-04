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

### Parte 3
A arquitetura do sistema do Airbnb é um exemplo complexo de design de sistemas, que abrange desde a escolha da tecnologia até a gestão de requisitos funcionais e não funcionais. 


### Requisitos e Design do Sistema
- **Requisitos Funcionais**: Incluem a necessidade dos hotéis de se cadastrarem facilmente, atualizarem e visualizarem reservas. Para os usuários, é crucial poder pesquisar e reservar hotéis, além de visualizar suas reservas​​.
- **Requisitos Não Funcionais**: Envolvem baixa latência para acesso por usuários e hotéis, disponibilidade constante sem ponto único de falha e consistência para usuários e hotéis​​.
- **Trade-offs de Design**: A arquitetura foi projetada priorizando disponibilidade, seguida de consistência e latência. Por enfatizar a disponibilidade e consistência, há um trade-off inevitável com a latência, implicando tempos maiores para completar tarefas​​.

### Tecnologias Adotadas
- **Infraestrutura na Nuvem**: O Airbnb depende fortemente de serviços de computação na nuvem, especificamente da Amazon Web Services (AWS). A AWS fornece uma infraestrutura escalável e confiável, além de uma gama de ferramentas para gerenciar o aplicativo​​.
- **Backend e Frontend**: O backend do aplicativo é construído com uma combinação de Ruby on Rails e Node.js, enquanto o frontend é desenvolvido em React Native. Essa combinação de tecnologias facilita uma experiência de usuário contínua em diferentes plataformas​​.
- **Arquitetura de Microserviços**: O Airbnb adota uma abordagem de microserviços, dividindo a aplicação em serviços menores e independentes que se comunicam através de APIs. Isso permite que a plataforma escale sua aplicação de forma mais eficiente, pois cada serviço pode ser escalado independentemente conforme necessário​​.
- **Gateway de API**: No centro da arquitetura está o Gateway de API, que é o ponto de entrada único para todas as solicitações do cliente. Ele é responsável por rotear solicitações para o serviço apropriado e gerenciar autenticação e autorização​​.

### Serviços Específicos
- **Serviços-chave**: Incluem o Serviço de Usuário para autenticação e informações de perfil, o Serviço de Busca para lidar com consultas e retornar resultados, o Serviço de Reservas para gerir todo o processo de reserva, o Serviço de Mensagens para mensagens em tempo real entre hóspedes e anfitriões, o Serviço de Avaliação para o sistema de avaliações e o Serviço de Notificação para notificações por push, email e outros tipos​​.

Essas escolhas tecnológicas e de design refletem a necessidade do Airbnb de operar em grande escala, atendendo a uma base de usuários global com diferentes requisitos e expectativas. A arquitetura do sistema é, portanto, uma combinação cuidadosa de confiabilidade, escalabilidade e eficiência, permitindo que a plataforma ofereça uma experiência de usuário fluida e intuitiva.

## Parte 4

### Descrição das Tecnologias

#### 1. **Amazon Web Services (AWS)**
   - **Serviços Relevantes da AWS**: 
     - **EC2 (Elastic Compute Cloud)**: Fornece capacidade de computação escalável.
     - **RDS (Relational Database Service)**: Usado para gerenciamento de bases de dados.
     - **S3 (Simple Storage Service)**: Armazenamento de objetos para armazenar e recuperar grandes quantidades de dados.

#### 2. **Ruby on Rails & Node.js**
   - **Backend**: O backend do Airbnb é uma combinação de Ruby on Rails e Node.js. Ruby on Rails é utilizado por sua eficiência no desenvolvimento rápido e Node.js por sua performance em operações I/O não bloqueantes.

#### 3. **React Native**
   - **Frontend**: React Native é utilizado para desenvolver a interface do usuário. Permite uma experiência de usuário consistente em várias plataformas (iOS, Android, Web).

#### 5. **Gateway de API**
   - **Roteamento de Solicitações**: Atua como o ponto de entrada para as solicitações dos clientes, roteando-as para o serviço apropriado e gerenciando autenticação e autorização.
Ele determina para qual microserviço uma determinada solicitação deve ser enviada, baseando-se em vários fatores como o tipo de solicitação, os parâmetros incluídos, e as políticas de roteamento configuradas.

   - **Balanceamento de Carga**: responsável por balancear a carga de solicitações entre diferentes instâncias de um serviço, ajudando a manter a performance e a disponibilidade.

   - **Autenticação e Autorização**: Antes de encaminhar as solicitações, o Gateway verifica a identidade do solicitante e se ele tem permissão para acessar o recurso desejado.
Isso envolve a verificação de tokens de acesso, credenciais de usuário e possivelmente outros mecanismos de segurança.

## Tecnologias de Processamento e Armazenamento de Dados

### 1. Apache Spark Streaming Cluster
- **Utilização**: Processamento de dados em tempo real.
- **Benefício**: Permite análise e processamento de fluxos de dados contínuos para insights rápidos e tomada de decisões.

### 2. Hadoop Cluster
- **Utilização**: Processamento de big data.
- **Benefício**: Armazenamento e processamento de grandes conjuntos de dados, suportando análise e mineração em larga escala.

### 3. Kafka
- **Utilização**: Plataforma de streaming de eventos.
- **Benefício**: Gerencia fluxos de dados em tempo real, garantindo comunicação rápida e confiável entre diferentes partes da arquitetura.

### 4. Cassandra Cluster
- **Utilização**: Banco de dados NoSQL distribuído.
- **Benefício**: Gerencia grandes volumes de dados, com alta disponibilidade e escalabilidade, adequado para cenários de intensa leitura e escrita.

### 5. Redis Cluster
- **Utilização**: Armazenamento de dados em memória.
- **Benefício**: Usado para caching e armazenamento de estruturas de dados, acelerando operações que exigem acesso rápido.

### 6. Elasticsearch Cluster
- **Utilização**: Busca e análise de dados em tempo real.
- **Benefício**: Oferece recursos de pesquisa eficientes e poderosos, melhorando a experiência do usuário.

![alt text](http://url/to/img.png)

### Modelo Híbrido: Unificação e Consolidação
O Airbnb está evoluindo sua arquitetura para um modelo híbrido que combina micro e macroserviços. Essa abordagem busca equilibrar a granularidade dos serviços e melhorar a colaboração entre equipes.
- **Unificação de APIs**: Concentra-se em criar pontos claros de acesso a dados ou funcionalidades.
- **Consolidação de Serviços**: Visa criar blocos de serviço onde cada bloco encapsula uma coleção de microserviços, facilitando o gerenciamento e a manutenção.
- **Serviço de Agregação de Dados**:  Este serviço atua como um intermediário entre o backend interno e os blocos de serviço. É responsável por coletar e distribuir dados para os vários microserviços.
- **Blocos de Serviço**: Cada bloco encapsula um conjunto de microserviços relacionados, promovendo organização e eficiência.
![alt text](./arq2.png)
---

**Referencias**
- https://blog.quastor.org/p/airbnbs-architecture
- https://interviewnoodle.com/hotel-booking-system-design-airbnb-1283bbef71ac
- https://www.searchlogistics.com/learn/statistics/airbnb-statistics/
- https://oglobo.globo.com/rio/web-summit-rio/noticia/2023/05/hospedes-do-airbnb-movimentam-r-26-bilhoes-no-brasil-plataforma-calcula-gerar-10-mil-empregos.ghtml
- https://medium.com/airbnb-engineering/data-infrastructure-at-airbnb-8adfb34f169c
- https://aws.amazon.com/pt/solutions/case-studies/innovators/airbnb/

