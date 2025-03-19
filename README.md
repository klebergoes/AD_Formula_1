# Análise de Performance dos Pilotos Ativos da Fórmula 1

## Sumário

[Desafio / Problema](#Desafio-/-Problema)

[Tecnologias Utilizadas](#Tecnologias-Utilizadas)

[Estrutura do Projeto](#Estrutura-do-Projeto)

[Conjunto de Dados](#Conjunto-de-Dados)

[Metodologia](#Metodologia)

[Como Executar](#Como-Executar)

[Resultados](#Resultados)


## Desafio / Problema

Uma renomada empresa está interessada em investir no patrocínio de um piloto de Fórmula 1 e, para tomar uma decisão estratégica, busca selecionar aquele que tenha apresentado a melhor performance em corridas. Com o objetivo de ajudar na escolha do piloto ideal, fui consultado para fornecer uma análise detalhada e embasada em dados históricos do Campeonato Mundial de Fórmula 1. Para isso, utilizarei abordagens analíticas tanto descritivas quanto de série temporal, a fim de explorar e interpretar o desempenho de pilotos ao longo de várias temporadas. Através dessa análise, pretendo identificar padrões de consistência e evolução no desempenho dos pilotos, permitindo assim sugerir o mais adequado para representar a marca no mundo da Fórmula 1, com base em dados concretos e insights valiosos.

A base de dados da Fórmula 1 contém um total de 859 pilotos cadastrados, mas nem todos estão ativos na categoria atualmente. Para garantir que a análise seja focada nos competidores relevantes, considerarei apenas os pilotos confirmados para a temporada 2025. A seguir, estão as equipes e seus respectivos pilotos:

-	Alpine - Pierre Gasly e Jack Doohan;
-	Aston Martin - Fernando Alonso e Lance Stroll;
-	Ferrari - Charles Leclerc e Lewis Hamilton;
-	Haas - Esteban Ocon e Oliver Bearman;
-	Sauber/Audi - Nico Hulkenberg  e Gabriel Bortoleto; 
-	McLaren - Lando Norris e Oscar Piastri;
-	Mercedes - George Russel e Andrea Kimi Antonelli;
-	RB - Yuki Tsunoda e Isack Hadjar;
-	Red Bull - Max Verstappen e Liam Lawson;
-	Williams - Alexander Albon e Carlos Sainz.


## Tecnologias Utilizadas
-   Linguagem: Python;
-   Bibliotecas: Pandas, Matplotlib, Seaborn, NumPy, Kagglehub, Os, Json e Warnings;
-   Ferramentas: Google Colab.


## Estrutura do Projeto

-   README.md: Documentação do projeto;
-   Projeto_Formula_1.ipynb: Notebook usado na análise.


## Conjunto de Dados

-   Fonte: Repositório Kaggle;
-   Dataset: muhammadehsan02/formula-1-world-championship-history-1950-2024;
-   Formato: API;
-   Tabelas / Colunas utilizadas:
    -   Driver_Details: Inclui informações abrangentes sobre os pilotos, como detalhes pessoais, estatísticas de carreira e conquistas:
        -   driverId: Identificador exclusivo para o motorista:
            -   Tipo de Dado: Inteiro.
        -   driverRef: Nome de referência para o driver:
            -   Tipo de Dado: String.
    -   Race_Results: Fornece resultados detalhados de cada corrida, incluindo posições finais, pontos ganhos e outras métricas importantes:
        -   resultId: Identificador para o resultado da corrida:
            -   Tipo de Dado: Inteiro.
        -   driverId: Identificador exclusivo para o motorista:
            -   Tipo de Dado: Inteiro.
        -   raceId: Identificador para a corrida:
            -   Tipo de Dado: Inteiro.
        -   positionOrder: Ordem de finalização com relação a outros pilotos:
            -   Tipo de Dado: Inteiro.
        -   points: Pontos concedidos para a corrida:
            -   Tipo de Dado: Float.
    -   Race_Schedule: Lista todas as corridas realizadas de 1950 a 2024, juntamente com detalhes como data, local e nome da corrida:
        -   raceId: Identificador para a corrida:
            -   Tipo de Dado: Inteiro.
        -   date: Data da corrida:
            -   Tipo de Dado: String.


## Metodologia

-   Importação pacotes e configuração para consumo de API: Importação dos pacotes necessários para execução do projeto, além da configuração do ambiente para armazenar as credenciais de acesso ao Kaggle, garantindo a autenticação e a integração com a API para extração de dados;
-   Coleta de Dados: Extração dos dados necessários por meio da integração com a API do Kaggle, acessando e obtendo os conjuntos de dados diretamente do repositório online para análise;
-   Transformação dos dados: Preparo dos dados para análise;
-   Exploração dos dados: Realização de análise exploratória com o uso de estatísticas descritivas, análise temporal e visualizações gráficas, com o objetivo de identificar padrões, tendências, sazonalidades e outliers nos dados;
-   Conclusão: Elaboração de um relatório final detalhado, apresentando a análise realizada e justificando a escolha do piloto mais adequado para ser patrocinado, com base nos critérios de desempenho e outros fatores relevantes identificados ao longo da análise.


## Como Executar

-   Acesse o Google Colab e faça login com suas credenciais;
-   No menu superior, vá até Arquivo > Abrir Notebook;
-   Na janela que se abrir, clique na aba GitHub;
-   Preencha os seguintes campos:
    -   Usuário ou organização: klebergoes;
    -   Repositório: klebergoes/AD_Formula_1.
-   Selecione o notebook Projeto_Formula_1.ipynb.


## Resultados

### Triagem dos pilotos

Dos 20 pilotos escalados para a temporada de 2025, 16 possuem histórico de corrida. A análise será feita com base nos pilotos com maior índice de vitórias (aproveitamento), que é a quantidade de corridas que o piloto participou dividida pela quantidade de vezes que ficou em primeiro lugar:

*Inserir imagem da Triagem dos pilotos*

Vamos manter o estudo apenas nos pilotos que estão liderando o ranking de índice de vitórias: 

Hamilton com (30.23%) e Max Verstappen com (30.96%).

Vamos entender quem possui o melhor desempenho em seus históricos de corrida.


### Medidas Separatrizes e de Tendencia Central

Análise detalhada para verificar a presença de outliers, examinar a distribuição dos dados e identificar a localização do valor central, que representa o ponto de concentração principal dos dados:

*Inserir imagem da Medidas Separatrizes e de Tendencia Central*

Perceba que não temos outlier, a média de pontos na história de Max Verstappen é levemente mais alta que a de Hamilton.

Hamilton possui uma média de 13.63 pontos, enquanto Max Verstappen tem uma média de 13.93 pontos.

Embora os valores mínimo e máximo de ambos os pilotos sejam iguais e não apresentem outliers, a mediana de Max Verstappen (15.0) está 2 pontos acima de Hamilton (13.0), indicando uma maior consistência em pontuações mais altas.

Max Verstappen leva vantagem com relação à média de pontos.


### Medidas de Dispersão ou Variabilidade

Avaliação da dispersão das pontuações em relação à média aritmética, com o objetivo de compreender o grau de variabilidade dos dados. Quanto maior o valor da dispersão, maior a dispersão dos pontos em torno da média, indicando uma maior heterogeneidade nos resultados:

*Inserir imagem da Medidas de Dispersão ou Variabilidade*

Hamilton possui um desvio padrão de 8.87 pontos, enquanto Max Verstappen tem um desvio padrão de 9.59 pontos.

O desvio padrão indica o grau de dispersão dos pontos em relação à média, ou seja, quanto maior esse valor, maior a variação nos resultados.

Os números mostram que as pontuações de Hamilton apresentam menor variação em comparação às de Max Verstappen, sugerindo que suas corridas são mais regulares e previsíveis.

Por outro lado, a maior variação nos pontos de Max Verstappen indica que ele teve desempenhos mais oscilantes, com corridas de pontuações altas, mas também baixas.

Isso reforça que Hamilton mantém uma performance mais uniforme ao longo das corridas, refletindo um desvio padrão menor.


### Série temporal

Análise detalhada para identificar se existe uma tendência consistente na evolução da média das pontuações ao longo do tempo, considerando possíveis padrões ou variações significativas:

*Inserir imagem da Medidas de Série temporal*

Ao avaliar a evolução das corridas ao longo dos anos para os dois pilotos, percebe-se que ambos apresentaram crescimento na média de pontos. No entanto, Hamilton começou a ter uma queda em sua performance a partir do período de 2019-2020.

Max Verstappen se destaca no período de 2023-2024, com uma média de pontuação nunca antes alcançada por Hamilton.

Considerando que Hamilton tem praticamente o dobro de tempo de participação na Fórmula 1 em comparação com Max Verstappen, esperava-se que sua performance fosse melhor, devido à experiência adquirida.


### Conclusão

Ao analisar as Medidas Separatrizes e de Tendência Central, observa-se que Max Verstappen apresenta uma média de pontuação ligeiramente superior à de Hamilton. No entanto, seu desvio padrão também é um pouco maior, indicando uma maior dispersão dos pontos ao redor da média, ou seja, suas pontuações variam mais entre as corridas.

A análise de série temporal revela uma tendência de desempenho distinta entre os dois pilotos ao longo dos anos. Quando Max Verstappen iniciou sua trajetória na Fórmula 1 (2015-2016), Hamilton já era um competidor consolidado, com uma média de 19 pontos por corrida, enquanto Verstappen, ainda em fase de adaptação, possuía uma média inicial de 6 pontos.

Entretanto, a evolução de Verstappen ao longo dos anos foi notável. Entre 2021 e 2022, sua média saltou para 19 pontos, enquanto a de Hamilton caiu para 14, marcando uma inversão na liderança do desempenho. No intervalo de 2023 e 2024, Verstappen atingiu um patamar impressionante, superando todas as marcas previamente registradas por Hamilton e consolidando-se como um dos pilotos mais dominantes da categoria.

Essa trajetória evidencia que Verstappen demonstrou um aprimoramento técnico e estratégico ao longo dos anos, reforçando um desenvolvimento consistente durante as temporadas.

Existem, obviamente, outros fatores que podem ter influenciado a queda de desempenho de Hamilton, como o carro, as estratégias de equipe, fatores psicológicos e físicos, entre outros. Como este estudo tem fins didáticos, não será aprofundado.


### Contato

-   Autor: Kleber Goes da Silva
-	E-mail: kleber-goes@hotmail.com
-	LinkedIn: in/kleber-goes-02091990
