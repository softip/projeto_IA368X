# Estudo de fatores associados a mortes devido a COVID-19
# Study of factors associated with deaths due to COVID-19

# Apresentação

O presente projeto foi originado no contexto das atividades da disciplina de pós-graduação [*Ciência e Visualização de Dados em Saúde*](https://github.com/datasci4health/home), oferecida no primeiro semestre de 2021, na Unicamp.

|Nome  | RA | Especialização|
|--|--|--|
| Ana Carolina Furiozo Arantes  | 228122  | Saúde|
| Ivan Paulino Pereira  | 262125  | Computação|
| Kleber Marcelo da Silva Rezende  | 232154  | Computação|
| Marília Santoro Cardoso  | 207705  | Saúde|


# Descrição Resumida do Projeto
Este projeto utiliza algoritmos de Machine Learn para tentar identificar os fatores associados à morte por COVID-19 em comparação com mortes decorridas de outras causas.

Neste trabalho foram utilizados dados anonimizados de pacientes com COVID-19 do estado do Ceará, que foram disponibilizados publicamente pelo [IntegraSUS/CE](https://github.com/integrasus/api-covid-ce).

Este dataset possui 1.873.583 de registros de pacientes do estado do Ceará acompanhados com sintomas de COVID-19. O dataset possui 43 features (colunas), sendo algumas relevantes para este trabalho, como por exemplo a relação de comorbidades do paciente. Apesar de possuir muitos registros, o dataset apresenta aproximadamente 97% de informações faltantes em relação às comorbidades e outros fatores de risco. Mais informações sobre esse dataset podem ser obtidas no [notebook de análise exploratória](https://github.com/softip/projeto_IA368X/blob/main/notebooks/E2_An%C3%A1lise_Explorat%C3%B3ria.ipynb).

Além dos dados do IntegraSUS/CE foram utilizados dados demográficos dos municípios onde os pacientes residem, esses dados foram obtidos do [portal do IBGE](https://www.ibge.gov.br/cidades-e-estados/ce.html). Esse dataset possui informações demográficas, como área do município, população, renda, número de matrícula e Índice de Desenvolvimento Humano Municipal - IDHM. Esse dataset foi utilizado para verificar se fatores sociais podem estar associados às mortes por COVID-19.

Os datasets utilizados no [notebook final](https://github.com/softip/projeto_IA368X/blob/main/notebooks/E3_Entrega_Final_(Modelos).ipynb) são resultados das etapas de pré-processamento: limpeza de dados e transformação de dados. 

Para compreender melhor como os dados foram tratados é possível acessar os notebooks de preparação dos dados [Dataset1:RandomForest](https://github.com/softip/projeto_IA368X/blob/main/notebooks/Tratamentode_Dados_para_ML_random_florest.ipynb) e [Dataset2:Regression COX](https://github.com/softip/projeto_IA368X/blob/main/notebooks/Tratamentode_Dados_para_ML_Cox.ipynb).

O primeiro notebook utiliza o algoritmo de florestas aleatórias (Random Forest) para classificar as mortes em decorrência de COVID-19 ou por outras causas. O Random Forest, assim como outros algoritmos baseados em árvores de decisão possibilitam o estudo de como a classificação foi realizada, de forma a compreender quais características ou fatores contribuem mais para o evento, nesse caso a morte por COVID-19.

O segundo algoritmo utilizado é o Regression COX, que faz parte da família de algoritmos de análise de sobrevivência. O modelo criado tem o objetivo de prever quais características (fatores) contribuem para a morte devido a COVID-19.

# Vídeos do Projeto
## Vídeo da Proposta

[Link para vídeo de apresentação da proposta do projeto.](https://youtu.be/59DZYWyoovo)

## Vídeo da Apresentação Final

[Link para vídeo de apresentação final do projeto.](https://youtu.be/PZiL9D5mvsE)

## Slides do Proposta
[Slides da Apresentação](https://drive.google.com/file/d/1UVw2a4cfNNw-17ogSW_DAaoE-lfuQ9Z-/view?usp=sharing)

## Slides do Projeto Final
[Slides da Apresentação](https://drive.google.com/file/d/1w8w3I-188_QzMqYMKmWJ2pcuUQfWYXaU/view?usp=sharing)

# Introdução e Referenciais de Teóricos

O novo coronavírus (SARS-CoV-2), vírus causador da doença COVID-19, foi identificado pela primeira vez na cidade de Wuhan, localizada na China, em dezembro de 2019 [1]. Rapidamente, o vírus se disseminou mundialmente, o que levou a Organização Mundial de Saúde (OMS) a declarar que a epidemia da COVID-19 constituía uma Emergência de Saúde Pública de Importância Internacional, em 30 de janeiro de 2020 e, em 11 de março de 2020, uma pandemia [1, 2].

O primeiro registro no Brasil ocorreu em 26 de fevereiro de 2020 e o primeiro óbito em 20 de março do mesmo ano. Com a ascensão dos números de óbitos, a pandemia tem se apresentado como um dos maiores desafios sanitários mundial deste século [1–3]. Atualmente, a população brasileira totaliza cerca de 500 mil mortes pela doença, além de aproximadamente 18 milhões de casos confirmados [4].

A alta taxa de letalidade se dá devido sua alta transmissibilidade. A transmissão do vírus ocorre através de gotículas contaminadas de secreções da orofaringe de uma pessoa infectada, por contato com objetos e superfícies contaminadas, ou por via fecal-oral. Além disso, a transmissão é intensificada pelo elevado tempo de incubação (cerca de 5-6 dias, variando de 0 a 24 dias), e devido a pessoas assintomáticas, pré-sintomáticas ou com sintomas leves poderem espalhar a doença [2].

O SARS-CoV-2 foi nomeado como síndrome respiratória aguda grave coronavírus-2 devido à sua alta homologia (aproximadamente 80%) com SARS-CoV, que causou a síndrome do desconforto respiratório agudo e alta mortalidade durante 2002–2003. O vírus SARS-CoV-2 afeta principalmente o sistema respiratório. Além de envolver sintomas relacionados à infecção do trato respiratório inferior, incluindo febre, tosse seca e dispneia, cefaleia, tontura, fraqueza generalizada, vômito e diarreia [5].

Um número de mortes de pacientes com doenças graves continuou a aumentar em todo o mundo. Estudos epidemiológicos têm mostrado que a mortalidade acomete mais pessoas idosas e portadoras de doenças crônicas subjacentes, que requerem hospitalização, cuidados intensivos e uso de ventiladores mecânicos [2, 5].

# Caracterização do problema
Em 16/12/2020 o governo brasileiro lançou o Plano Nacional de Imunização - PNI. O plano apresenta a caracterização dos grupos de risco para agravamento e óbito pela COVID-19. De acordo com o PNI, os principais fatores de risco associados a progressão para formas graves da doença e ao óbito são:

* idade superior a 60 anos; 
* diabetes mellitus; 
* doença pulmonar obstrutiva crônica (DPOC); 
* doença renal; 
* doenças cardiovasculares e cerebrovasculares; 
* hipertensão arterial grave; 
* indivíduos transplantados de órgãos sólidos;
* anemia falciforme; 
* câncer e 
* obesidade mórbida (IMC≥40).

O PNI define 14 grupos prioritários para vacinação, sendo eles: Trabalhadores de Saúde; Pessoas de 80 anos e mais; Pessoas de 75 a 79 anos; Pessoas de 70 a 74 anos; Pessoas de 65 a 69 anos; Pessoas de 60 a 64 anos; População indígena aldeado em terras demarcadas aldeada; Povos e comunidades tradicionais ribeirinhas e quilombolas; Grupo com comorbidades*; Trabalhadores da educação; Pessoas com deficiência permanente severa; Forças de Segurança e Salvamento; Funcionários do sistema de privação de liberdade; População privada de liberdade. Além disso, estima-se que serão necessárias 104.265.535 (cento e quatro milhões, duzentos e sessenta e cinco mil, quinhentos e trinta e cinco) doses, para vacinar uma população de 49.650.255 (quarenta e nove milhões, seiscentos e cinquenta mil, duzentos e cinquenta e cinco) pessoas dos grupos de Trabalhadores da saúde, pessoas com 60 anos ou mais e o Grupo com comorbidades.

Com o surgimento de novas linhagens do vírus de maior transmissibilidade, pesquisadores brasileiros já apontaram uma piora na situação epidemiológica das regiões acometidas por essas variantes. Entretanto, diferentemente do que tem sido apontado, Freitas e colaboradores sugerem uma mudança no padrão de mortalidade da doença, já que jovens entre 20-39 anos têm sido a população mais acometida com uma taxa de letalidade maior em 2,7 vezes [9]. Assim, a ampla capacidade de mutacidade do Sars-CoV-2, bem como a mudança de foco de infecção do vírus reiteram mais do que nunca o início de ações como: maiores estudos sobre a eficácia das vacinas disponíveis no país, compartilhamento mais eficiente de dados e informações referentes à pandemia além de um maior engajamento por parte dos envolvidos na produção de conhecimento sobre o assunto no Brasil [10].

# Motivação

Diante do problema apresentado na seção anterior, a motivação para este trabalho consiste na identificação de fatores associados ao óbito por COVID-19 em comparação aos óbitos por outras causas, no intuito de permitir a priorização de subgrupos para imunização ou em outros cenários aplicáveis.

# Perguntas de Pesquisa

- Qual perfil da população Brasileira está mais suscetível ao óbito por meio de infecção por COVID-19?
- Quais características implicam em maior mortalidade por COVID-19?

# Objetivos do Projeto

O objetivo deste trabalho é estabelecer um perfil da população que seja mais suscetível à óbito por COVID-19, utilizando algoritmos de Machine Learn e dados demográficos do estado do Ceará para propor subgrupos de prioridade para imunização.

# Metodologia
O estudo foi do tipo observacional e empregando processo de KDD, que  é composto por cinco fases, sendo elas: seleção de dados, pré-processamento, transformação, mineração e interpretação/avaliação.  

Na primeira etapa, após definir as perguntas de pesquisa, foi realizada a busca por fontes de dados que pudessem ser utilizadas para fornecer as respostas desejadas. Após realizar a seleção dos dados foi realizada a análise exploratória dos dados para conhecer os dados, tentar identificar padrões e encontrar insights. Além disso, foi realizada as estatísticas descritivas, o desenvolvimento de gráficos com intuito de melhorar a visualização destes dados e foi verificado quais dados estavam faltantes.
Na segunda etapa (pré-processamento) foi realizada a remoção ou imputação de dados faltantes. Os tipos dos campos foram alterados conforme o domínio do dado e registros duplicados foram excluídos. 

Na terceira etapa (transformação) o conjunto de dados do IntegraSUS foi fundido com o conjunto de dados do IBGE, foi criada uma nova coluna "tempo de vida" utilizada na regressão de COX. Essa nova feature foi obtida subtraindo a data de início dos sintomas (início da observação) da data de morte do paciente (término da observação). Para os pacientes que não faleceram, a data da extração do conjunto de dados no GitHub do IntegraSUS,  foi utilizada como a data do término da observação. 

Por fim, as features categorias foram transformadas em dummies. Um dummies é uma feature que representa se uma caracteristica está presente ou não, por exemplo, a coluna sexo pode possuir dois valores "Masculino" e "Feminino", quando a coluna é transformada em dummies são criadas duas colunas com os titulos "Masculino" e "Feminino". Se um paciente é do sexo masculino, então a coluna "Masculino" vai receber o valor 1,  representando sim, e a coluna "Feminino" vai receber o valor 0, representando "Não". Esse processo é necessário para o correto funcionamento de alguns algoritmos de aprendizagem de máquina, como é o caso da regressão COX. Após as transformações um conjunto de features de interesses foi selecionada e dois novos conjuntos de dados foram criados para serem utilizados na próxima etapa do KDD.

Na quarta etapa foi realizada a mineração de dados. Nesta etapa foram criados dois modelos, um de classificação utilizando o algoritmo de florestas aleatórias (Random Forest) e um de regressão utilizando o algoritmo  Regression COX.

O Random Forest é um algoritmo de aprendizagem de máquina utilizado para realizar classificação e regressão. O algoritmo cria diversas árvores de decisão, escolhendo aleatoriamente as features que serão utilizadas em cada árvore. O resultado da classificação é realizado considerando os votos de cada árvore da floresta na predição realizada.

A Regressão de COX, que é uma análise de sobrevivência. A análise de sobrevivência é um conjunto de abordagens estatísticas usadas para descobrir o tempo que um evento de interesse (geralmente chamado de morte) leva para ocorrer leva. Essa abordagem é frequentemente utilizada em dados de saúde, para prever fatores associados à morte e tratamento com maior probabilidade de sobrevivência.


# Ferramentas
A análise exploratória dos dados foi realizada utilizando o notebook do Google Colab. A linguagem utilizada para processamento dos dados foi o Python com as bibliotecas Pandas e NumPy. Para visualização dos dados foram utilizadas as bibliotecas Matplotlib e Seaborn.

A biblioteca Scikit Learn foi utilizada para construção de modelos de Machine Learning. O objetivo foi utilizar algoritmos supervisionados para prever os óbitos por Covid-19, dadas as características/comorbidades dos pacientes.

# Bases Estudadas e Adotadas
Para responder às perguntas de pesquisa foi utilizada uma base de dados fornecida pelo Governo do Estado do Ceará. A base possui o registro dos infectados por COVID-19, apresentando suas comorbidades e o desfecho da infecção.

| Base de Dados | Endereço na Web | Resumo descritivo |
|---------------|-----------------|-------------------|
| api-covid-ce  | [api-covid-ce](https://github.com/integrasus/api-covid-ce) | Este repositório trata da disponibilização da API pública do IntegraSUS sobre dados relacionados ao boletim epidemiológico covid-19 do estado do Ceará.|
|   IBGE-CE     | [IBGE-CE](https://www.ibge.gov.br/cidades-e-estados/ce.html) | API pública do IBGE com dados populacionais do estado do Ceará.|

# Dicionário de dados

A tabela abaixo apresenta o dicionário de dados do conjunto.
Nome da coluna/campo             |Descrição                                            |Tipo
---------------------------------|-----------------------------------------------------|---------------
bairroPaciente     		 		 |Bairro de residência do paciente                     |Textual
classificacaoEstadoSivep 		 |Resultado do exame     					           |Categórico
codigoMunicipioPaciente  		 |Código do município fornecido pelo IBGE              |Numérico
codigoPaciente     	     		 |Código identificador do paciente                     |Numérico
comorbidadeAsmaSivep             |Indicador de asma                                    |Categórico
comorbidadeCardiovascularSivep   |Indicador de problemas cardiovasculares              |Categórico
comorbidadeDiabetesSivep         |Indicador de diabetes                                |Categórico
comorbidadeHematologiaSivep      |Indicador de hematologia                             |Categórico
comorbidadeImunodeficienciaSivep |Indicador de Imunodeficiência                        |Categórico
comorbidadeNeurologiaSivep       |Indicador de morbidade neurológica                   |Categórico
comorbidadeObesidadeSivep        |Indicador de obesidade                               |Categórico
comorbidadePneumopatiaSivep      |Indicador de pneumonia                               |Categórico
comorbidadePuerperaSivep         |Indicador de morbidade puerperal (parto precoce)     |Categórico
comorbidadeRenalSivep            |Indicador de morbidade renal                         |Categórico
comorbidadeSindromeDownSivep     |indicador de síndrome de Down                        |Categórico
comorbidadeHiv                   |indicador de HIV                                     |Categórico
comorbidadeNeoplasias            |indicador de neoplasias                              |Categórico
tipoTesteExame                   |Tipo de exame realizado (Teste rápido, RT PCR, ELISA, Quimioluminescência, Eletroquimioluminescência)     |Categórico
racaCorPaciente                  |Raça/Cor do paciente                                 |Categórico
dataNotificacaoObito             |Data na qual o óbito foi notificado                  |Data
cnesNotificacaoEsus              |Código do Cadastro Nacional de Estabelecimentos de Saúde no qual o caso foi notificado no sistema E     |Numérico
municipioNotificacaoEsus         |Município que notificou o caso no E                  |Numérico
dataEntradaUtisSvep              |Data de entrada na UTI                               |Data
dataEvolucaoCasoSivep            |Data do diagnóstico de evolução                      |Data
dataInicioSintomas               |Data de início dos sintomas                          |Data
dataInternacaoSivep              |Data de internação do paciente                       |Data
dataNotificacao                  |Data de notificação do exame                         |Data
dataObito                        |Data do óbito     |Data
dataResultadoExame               |Data do resultado do exame                           |Data
dataSaidaUtisSvep                |Data de saída da UTI                                 |Data
dataSolicitacaoExame             |Data de solicitação de exame                         |Data
estadoPaciente                   |Estado de residência do paciente                     |Categórico
evolucaoCasoSivep                |Diagnóstico de evolução do caso (Cura ou óbito)      |Categórico
idSivep                          |Identificador do paciente no Sistema de Vigilância da Saúde     |Numérico
idadePaciente                    |Idade do paciente em anos                            |Numérico
municipioPaciente                |Município de residência do paciente                  |Textual
obitoConfirmado                  |Confirmação de óbito                                 |Booleano
paisPaciente                     |País de residência do paciente                       |Categórico
resultadoFinalExame              |Resultado do exame final                             |Categórico
sexoPaciente                     |Sexo do paciente                                     |Categórico

# O que descobriu sobre esse banco?
O banco de dados do IntegraSUS/CE possui muitos registros (1.873.583) de pacientes do estado do Ceará com sintomas de COVID-19, apresentando 43 features (colunas), sendo algumas relevantes para este trabalho, como por exemplo a relação de comorbidades do paciente. Porém, cerca de 97% do dataset possui informações faltantes em relação às comorbidades e outros fatores de risco.
 
# Quais as transformações e tratamentos (e.g., dados faltantes e limpeza) feitos?
Para o pré-processamento foram realizadas limpeza e transformação de dados, utilizando dois algoritmos de machine learning: florestas aleatórias (Random Forest) e Regression COX.  Os dados foram tratados e estão disponíveis para  acesso nos links: [Dataset1:RandomForest](https://github.com/softip/projeto_IA368X/blob/main/notebooks/Tratamentode_Dados_para_ML_random_florest.ipynb) e [Dataset2:Regression COX](https://github.com/softip/projeto_IA368X/blob/main/notebooks/Tratamentode_Dados_para_ML_Cox.ipynb).

# Análise Exploratória de Dados.
[Notebook de análise exploratória.](https://github.com/softip/projeto_IA368X/blob/main/notebooks/E2_An%C3%A1lise_Explorat%C3%B3ria.ipynb)

O conjunto de dados do IntegraSUS, utilizado neste trabalho, possui muitos dados faltantes, principalmente os dados relacionados as comorbidades que são de interesse de estudo. Cerca de 99% dos dados faltantes estavam relacionados as comorbidades, uma hipótese para a falta de dados relacionados as comorbidades é de que essas informações são coletadas apenas quando o paciente é internado ou busca por atendimento em uma unidade de saúde. A figura abaixo apresenta que a maior parte dos dados faltantes são de pessoas que não foram internadas.

![alt text](https://catalogos.ifs.ifsuldeminas.edu.br/temp/grafico1.png)

O número total de óbitos do dataset (21.963), 96,8% foram confirmados positivos para COVID-19, em sua maioria homens (55,9%). A faixa etária que mais se contaminou possuía entre 30 e 40 anos e eram do sexo feminino. Apesar de grande parte da população do Ceará possuir entre 10 e 19 anos, a grande maioria dos óbitos acontece entre os 75 e 80 anos. Pode-se observar também que em 93,2% dos casos positivos para COVID-19 a internação não foi necessária. Demograficamente, a cidade com maior número de óbitos é Fortaleza (capital do Ceará), seguida por Caucaia (16,3 km de distância da capital) e Maracanaú (23,4 km de distância da capital), conforme pode ser visto na figura abaixo:

![alt text](https://catalogos.ifs.ifsuldeminas.edu.br/temp/grafico2.png)

Como resultados podemos observar que cerca de 45% dos óbitos pela doença no estado do Ceará foram pacientes que não possuíam comorbidade nenhuma e 31% dos pacientes possuíam pelo menos uma comorbidade. 

![alt text](https://catalogos.ifs.ifsuldeminas.edu.br/temp/grafico3.png)

A maioria dos óbitos por COVID-19 eram de pacientes com problemas cardiovasculares e diabetes. Dados da secretaria de saúde do Distrito Federal (DF) exemplificam esse fato: dos mais de 300 mil infectados, em abril de 2021, pouco mais de 17 mil eram portadores de comorbidades, totalizando 5,6% dos casos. A grande maioria desses pacientes (56,6%) são cardiopatas, seguido de pacientes obesos (7,3%) e imunossuprimidos (5,6%). Além disso, no DF dentre os mais de 5 mil mortos pela COVID-19, 85,1% tinham outras doenças que agravaram o quadro da infecção [6]. 

![alt text](https://catalogos.ifs.ifsuldeminas.edu.br/temp/grafico4.png)

O mesmo pode ser observado em estudos realizados pela Caixa de Previdência e Assistência aos Servidores da Fundação Nacional de Saúde (CAPESESP) que avaliou 600 pessoas em 2020, acometidas ou não pelo Sars-CoV-2. Esse estudo revelou que a taxa de mortalidade por COVID-19 de pessoas diabéticas é 10% maior que a taxa de mortalidade entre pessoas saudáveis, devido a vulnerabilidade do paciente diabético em lidar com o quadro infeccioso do vírus [7]. O mesmo é pontuado por Marinho e colaboradores, que apontaram a desregulação imunológica e a inflamação metabólica do paciente diabético como pontos chave capazes de reduzir a habilidade do organismo em desenvolver cura contra a doença, justificando a maior taxa de mortalidade associada à essa população [8].

O número de mortes também é maior entre os homens, cerca de 55% dos óbitos e internações são relacionadas ao gênero masculino.

![alt text](https://catalogos.ifs.ifsuldeminas.edu.br/temp/grafico8.png)

No que tange aos óbitos por raça/cor, observa-se que 83.4% dos óbitos estão relacionados as declarados como Pardos, 13% relacionados aos Branco 2% relacionados aos declarados Preto. De acordo, o IPECE, cem 2019, 65,5% da população ceraense se declaram como pardos, 34,3% como brancos e 3,1% como negros. Observa-se que o número de mortos é maior entre pardos e negros.

![alt text](https://catalogos.ifs.ifsuldeminas.edu.br/temp/grafico9.png)

Além disso, pode-se perceber que a taxa de letalidade da doença para casos mais graves (onde o paciente foi pra UTI) é maior, mais de 66% dos casos evoluiu para óbito. Diferente do observado em casos mais leves, onde mais de 67% evoluem para recuperados. 

![alt text](https://catalogos.ifs.ifsuldeminas.edu.br/temp/grafico8.png)

Mais informações sobre as análise exploratória realizada pode ser acessado no noteboo:
[Os resultados de análise exploratória estão descritos no notebook de análise exploratória.](https://github.com/softip/projeto_IA368X/blob/main/notebooks/E2_An%C3%A1lise_Explorat%C3%B3ria.ipynb)


# Resultados

O algoritmo random forest foi utilizado para prever se o óbito de um paciente foi devido a Covid ou se teve outras causas, ao  final da simulação foi verificado quais características estavam mais associadas às mortes por Covid.

O modelo de floresta aleatória apresentou acurácia de 87.4% e sensibilidade para detectar as mortes causadas por Covid de 96.2%. No entanto, o modelo apresentou uma especificidade muito baixa, ou seja, ele possui baixa capacidade de prever os casos negativos. Esse problema pode ter ocorrido devido a quantidade menor e desproporcional de registros de mortes devido a outras causas. Além disso, os fatores associados à morte por Covid também têm influenciado mortes por outras causas, o que faz o modelo possuir uma baixa especificidade.

O modelo de florestas aleatórias apresentou que os fatores mais associados à morte devido a Covid são: a idade, raça/cor, o sexo, e as comorbidades cardiovasculares e diabetes, como mostrado na figura abaixo. Essas características são as mesmas já observadas na análise exploratória.

![alt text](https://catalogos.ifs.ifsuldeminas.edu.br/temp/grafico6.png)

A regressão de COX foi utilizada para prever como diversas características colaboram para a redução do tempo de vida de um paciente infectado por Covid, ou seja, como essas características estão associadas à morte por Covid. Para interpretar o resultado da correlação de COX é necessário interpretar o Hazard Ratio (exp(coef)), ou a razão de risco, onde:

* HR = 1: Sem efeito
* HR < 1: Redução do risco de morte
* HR > 1: Aumento do risco de morte

Além disso, de avaliar a razão de risco (HR) faz-se necessário avaliar também a probabilidade do evento ser ao acaso (p-value). Após executar a regressão de COX e considerando um p-value < 0.05, verificamos que o fator idade entre 0 e 59 anos, a escolaridade e as puérpera possuem maior chances de sobrevivência, enquanto a idade maior que 60 anos, e as comorbidades de obesidade, neurológicas, renais e diabetes contribuem para o aumento das chances de morte. A figura abaixo apresenta como os fatores estão associados às chances de morte e sobrevivência devido a Covid. 

![alt text](https://catalogos.ifs.ifsuldeminas.edu.br/temp/grafico7.png)

Entre as comorbidades a obesidade é a que oferece maior risco de morte, aumentando as chances em 48%, seguidas das comorbidades neurológica com 20%, renal 17% e diabetes 7%. Verifica-se aqui que o fator cardiovascular apresentou uma pequena razão de risco e não foi considerado, pois seu p-valor foi de 0.34, essa informação é diferente do que foi observada na análise exploratória, onde o fator cardiovascular era maior entre todas as outras comorbidades presentes nas vítimas de Covid. 

Um fato interessante é que o fator escolarização entre 6 a 14 anos apresentou uma redução das chances de morte devido a covid de 6%.

# Discussão

As análises realizadas comprovaram que a idade superior a 60 anos contribui muito para o aumento do risco de morte. Além disso, algumas comorbidades não apresentam impacto elevado como se acreditava ao realizar a análise exploratória, como é o caso da comorbidade cardiovascular e do diabetes que apresentou aumento no risco de morte de 7%.

Além disso, a condição de puérpera, considerada anteriormente como uma comorbidade e fator de risco, se mostrou como um fator que colabora para a redução do risco de morte. E a educação (escolaridade) se mostrou importante, mais uma vez, colaborando com a redução do risco de morte.

Aproveitamos para pedir desculpas, pois na apresentação do trabalho a Regressão de COX apresentou uma falha. O fator idade foi considerado sem efeito, pois no conjunto de dados a característica idade era uma única coluna com valores numéricos discretos. Ocorre que as idades menores que 60 anos colaboram para a redução do risco de morte, enquanto que as idades maiores que 60 anos colaboram com o aumento do risco de morte, uma vez que havia uma única coluna com todas as idades, uma faixa etária anula a outra. Ao perceber o erro dividimos as idades em faixas etárias de 10 anos, após criamos uma coluna para cada faixa etária e preenchemos com 1 a coluna correspondente à faixa etária do paciente, as demais foram preenchidas com 0. Aproveitamos e realizamos o mesmo processo para as colunas sexo e raça.

# Trabalhos Futuros

O que poderia ser melhorado se houvesse mais tempo?

* Obtenção de mais informações de outros bancos de dados abrangendo mais regiões.
* Testar outras formas de tratamentos de dados para investigar as alterações obtidas nos resultados


# Referências Bibliográficas

1. Oliveira WK de, Duarte E, França GVA de, Garcia LP (2020) Como o Brasil pode deter a COVID-19. Epidemiol e Serviços Saúde 29:e2020044
2. Aquino EML, Silveira IH, Pescarini JM, et al (2020) Medidas de distanciamento social no controle da pandemia de COVID-19: potenciais impactos e desafios no Brasil. Cien Saude Colet 25:2423–2446
3. Werneck GL, Carvalho MS (2020) A pandemia de COVID-19 no Brasil: crônica de uma crise sanitária anunciada. Cad Saude Publica 36:1–4
4. World Health Organization (2021) Brazil: WHO Coronavirus Deseases (COVID-19) Dashboard.
5. Yuki K, Fujiogi M, Koutsogiannaki S (2020) COVID-19 pathophysiology: A review. Clin Immunol 215:108427
6. Covid-19: pacientes com comorbidades representam 85,1% dos mortos pela doença no DF. https://www.correiobraziliense.com.br/cidades-df/2021/03/4911911-covid-19-pacientes-com-comorbidades-representam-851--dos-mortos-pela-doenca-no-df.html. Accessed 12 Apr 2021
7. Diabéticos com Covid-19 têm 57% mais chances de morrer do que pacientes saudáveis, diz pesquisa – Jovem Pan. https://jovempan.com.br/programas/jornal-da-manha/diabeticos-com-covid-19-tem-57-mais-chances-de-morrer-do-que-pacientes-saudaveis-diz-pesquisa.html?amp. Accessed 12 Apr 2021
8. Marinho FP, Castro TM, Cristina A, Silvério P (2021) Inter-relação entre COVID-19 e diabetes mellitus: uma revisão sistemática. 2021:1–14
9. Ricardo A, Freitas R, Beckedorff OA, Góes LP De, Siqueira AM, Castro DB De, Fernandes C, Rocha D, Lemos Q, Barros ENC (2021) A emergência da nova variante P.1 do SARS-CoV-2 no Amazonas (Brasil) foi temporalmente associada a uma mudança no perfil da mortalidade devido a COVID-19, segundo sexo e idade. https://doi.org/https://doi.org/10.1590/SciELOPreprints.2030
10.	Maria F, Marquitti D, Coutinho RM, et al (2021) Carta à Comunidade Científica : o Brasil frente às novas variantes de SARSCoV- 2. 
11.	Brasil. Ministério da Saúde. Secretaria de Ciência, Tecnologia e Insumos Estratégicos. Departamento de Ciência e Tecnologia. (2014) Diretrizes Metodológicas: elaboração de revisão sistemática e metanálise de estudos observacionais comparativos sobre fatores de riscos e prognósticos. Brasília: Ministério da Saúde, 2014. 132 p.
12.	https://www.ipece.ce.gov.br/2020/12/22/cresce-numero-de-pessoas-que-se-declararam-de-cor-preta-enquanto-brancos-e-pardos-caem-no-ceara-em-2019-com-relacao-a-2013/

