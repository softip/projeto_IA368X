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
Este projeto utiliza algoritmos de Machine Learn para tentar identificar os fatores associados à morte por a COVID-19 em comparação com mortes decorridas de outras causas.

Neste trabalho foram utilizados dados anonimizados de pacientes com COVID-19 do estado do Ceará, que foram disponibilizados publicamente pela [IntegraSUS/CE](https://github.com/integrasus/api-covid-ce).

Este dataset possui 1.873.583 de registros de pacientes do estado do Ceará acompanhados com sintomas de COVID-19. O dataset possui 43 features (colunas), sendo algumas relevantes para este trabalho, como por exemplo a relação de comorbidades do paciente. Apesar de possuir muitos registros, o dataset apresenta aproximadamente 97% de informações faltantes em relação às comorbidades e outros fatores de risco. Mais informações sobre esse dataset podem ser obtidas no [notebook de análise exploratória](https://github.com/softip/projeto_IA368X/blob/main/notebooks/E2_An%C3%A1lise_Explorat%C3%B3ria.ipynb).

Além dos dados do IntegraSUS/CE foram utilizados dados demográficos dos municípios onde os pacientes residem, esses dados foram obtidos do [portal do IBGE](https://www.ibge.gov.br/cidades-e-estados/ce.html). Esse dataset possui informações demográficas, como área do município, população, renda, número de matrícula e índice de desenvolvimento Humano Municipal - IDHM. Esse dataset foi utilizado para verificar se fatores sociais podem estar associados às mortes por COVID-19.

Os datasets utilizados neste notebook são resultados das etapas de pré-processamento: limpeza de dados e transformação de dados. Para compreender melhor como os dados foram tratados é possível acessar os notebooks de preparação dos dados [Dataset1:RandomForest](https://github.com/softip/projeto_IA368X/blob/main/notebooks/Tratamentode_Dados_para_ML_random_florest.ipynb) e [Dataset2:Regression COX](https://github.com/softip/projeto_IA368X/blob/main/notebooks/Tratamentode_Dados_para_ML_Cox.ipynb).

Este trabalho apresenta a aplicação de dois algoritmos de Machine Learning. O primeiro utiliza o algoritmo de florestas aleatórias (Random Forest) para classificar as mortes em decorrência de COVID-19 ou por outras causas. O Random Forest, assim como outros algoritmos baseados em árvores de decisão possibilitam o estudo de como a classificação foi realizada, de forma a compreender quais características ou fatores contribuem mais para o evento, nesse caso a morte por COVID-19.

O segundo algoritmo utilizado é o Regression COX, que faz parte da família de algoritmos de análise de sobrevivência. O modelo criado tem o objetivo de prever quais características (fatores) contribuem para a morte devido a COVID-19.

# Vídeos do Projeto
# Vídeo da Proposta

[Link para vídeo de apresentação da proposta do projeto.](https://youtu.be/59DZYWyoovo)

# Vídeo da Apresentação Final

[Link para vídeo de apresentação final do projeto.](https://youtu.be/PZiL9D5mvsE)

# Slides do Projeto Final

[Slides da Apresentação](https://drive.google.com/file/d/1w8w3I-188_QzMqYMKmWJ2pcuUQfWYXaU/view?usp=sharing)

# Introdução e Referenciais de Teóricos

# Contextualização do projeto

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
*  anemia falciforme; 
*  câncer e 
*  obesidade mórbida (IMC≥40).

O PNI define 14 grupos prioritários para vacinação, sendo eles: Trabalhadores de Saúde; Pessoas de 80 anos e mais; Pessoas de 75 a 79 anos; Pessoas de 70 a 74 anos; Pessoas de 65 a 69 anos; Pessoas de 60 a 64 anos; População indígena aldeado em terras demarcadas aldeada; Povos e comunidades tradicionais ribeirinhas e quilombolas; Grupo com comorbidades*; Trabalhadores da educação; Pessoas com deficiência permanente severa; Forças de Segurança e Salvamento; Funcionários do sistema de privação de liberdade; População privada de liberdade. Além disso, estima-se que serão necessárias 104.265.535 (cento e quatro milhões, duzentos e sessenta e cinco mil, quinhentos e trinta e cinco) doses, para vacinar uma população de 49.650.255 (quarenta e nove milhões, seiscentos e cinquenta mil, duzentos e cinquenta e cinco) pessoas dos grupos de Trabalhadores da saúde, pessoas com 60 anos ou mais e o Grupo com comorbidades.

Com o surgimento de novas linhagens do vírus de maior transmissibilidade, pesquisadores brasileiros já apontaram uma piora na situação epidemiológica das regiões acometidas por essas variantes. Entretanto, diferentemente do que tem sido apontado, Freitas e colaboradores sugerem uma mudança no padrão de mortalidade da doença, já que jovens entre 20-39 anos têm sido a população mais acometida com uma taxa de letalidade maior em 2,7 vezes [9]. Assim, a ampla capacidade de mutacidade do Sars-CoV-2, bem como a mudança de foco de infecção do vírus reiteram mais do que nunca o início de ações como: maiores estudos sobre a eficácia das vacinas disponíveis no país, compartilhamento mais eficiente de dados e informações referentes à pandemia além de um maior engajamento por parte dos envolvidos na produção de conhecimento sobre o assunto no Brasil [10].

# Motivação

Diante do problema apresentado na seção anterior, a motivação para este trabalho consiste na identificação de fatores associados ao óbito por COVID-19 em comparação aos óbitos por outras causas, no intuito de priorizar subgrupos para imunização ou em outros cenários aplicáveis.

# Perguntas de Pesquisa

- Qual perfil da população Brasileira está mais suscetível ao óbito por meio de infecção por COVID-19?
- Quais características implicam em maior mortalidade por COVID-19?

# Objetivos do Projeto

O objetivo deste trabalho é estabelecer um perfil da população que seja mais suscetível à óbito por COVID-19, utilizando algoritmos de Machine Learn e dados demográficos do estado do Ceará para propor subgrupos de prioridade para imunização.

# Metodologia
Inicialmente, foram realizadas etapas de pré-processamento utilizando limpeza e transformação de dados. O estudo foi do tipo observacional com tratamento de dados utilizando algoritmos de Machine Learn como  florestas aleatórias (Random Forest) e Regression COX. 

O Random Forest baseia-se em árvores de decisão o qual possibilita o estudo da classificação entre óbitos por COVID-19 ou por outras causas, além de compreender quais características ou fatores são mais suscetíveis ao óbito pela doença. Já o  Regression COX é um modelo de análise estatística de sobrevivência. Neste estudo foi utilizado com o objetivo de prever quais características (fatores) contribuem para o óbito por COVID-19.

# Ferramentas
A análise exploratória dos dados será realizada utilizando o notebook do Google Colab. A linguagem utilizada para processamento dos dados será o Python com as bibliotecas Pandas e NumPy. Para visualização dos dados será utilizada as bibliotecas Matplotlib e Seaborn.

A biblioteca Scikit Learn será utilizada para construção de modelos de Machine Learning. O objetivo é utilizar algoritmos supervisionados para prever os óbitos por Covid-19, dadas as características/comorbidades dos pacientes. Uma vez que o modelo esteja concluído, será extraído as características mais importantes, que levam os pacientes a óbito.

# Base de Dados e Evolução

# Bases Estudadas e Adotadas
Para responder às perguntas de pesquisa será utilizada uma base de dados fornecida pelo Governo do Estado do Ceará. A base possui o registro dos infectados por COVID-19, apresentando suas comorbidades e o desfecho da infecção.

| Base de Dados | Endereço na Web | Resumo descritivo |
|---------------|-----------------|-------------------|
| api-covid-ce  | [api-covid-ce](https://github.com/integrasus/api-covid-ce) | Este repositório trata da disponibilização da API pública do IntegraSUS sobre dados relacionados ao boletim epidemiológico covid-19 do estado do Ceará.|

# Qual o esquema/dicionário desse banco (o formato é livre)?

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
Para pré-processamento foram realizadas limpeza e transformação de dados, utilizando dois algoritmos de machine learning: florestas aleatórias (Random Forest) e Regression COX.  Os dados foram tratados e estão disponíveis para  acesso nos links: Dataset1:RandomForest e Dataset2:Regression COX.
 
# Apresente aqui uma Análise Exploratória (inicial) sobre esta base.
[Notebook de análise exploratória.](https://github.com/softip/projeto_IA368X/blob/main/notebooks/E2_An%C3%A1lise_Explorat%C3%B3ria.ipynb)

# Integração entre Bases e Análise Exploratória
Descreva etapas de integração de fontes de dados e apresente a seguir uma análise exploratória que envolva ambas.

Na etapa de análise exploratória foram utilizados os seguintes ferramentas:

* Estatística descritiva e gráficos;
* Análise correlação e gráficos de dispersão;

[Os resultados de análise exploratória está descrita no notebook de análise exploratória.](https://github.com/softip/projeto_IA368X/blob/main/notebooks/E2_An%C3%A1lise_Explorat%C3%B3ria.ipynb)

# Análises Realizadas
As análises realizadas estão dividas nas seguintes etapas:

1. Pré-processamento
2. Análise Exploratória
3. Machine Learning
4. Conclusão
 
Na primeira etapa (análise exploratória) foram realizadas análise de dados para conhecer os dados, verificar quais dados estavam faltantes, realizar estatísticas descritivas, desenvolvimento de gráficos com intuito de melhorar a visualização destes dados. entre outros.

Na segunda etapa (pré-processamento) foram realizadas a limpeza e transformação de dados, realizando a remoção ou imputação de dados faltantes. Também foram selecionados os features e o subconjunto de dados de interesse, além de realizar a junção dos diferentes datasets.

Na terceira etapa (machine learning) foram realizadas análises de dados utilizando  dois modelos (algoritmos) de machine learning: florestas aleatórias (Random Forest) e Regression COX.

Na quarta etapa (conclusão) foi realizada a interpretação dos resultados.

# Ferramentas
A análise exploratória dos dados será realizada utilizando o notebook do Google Colab. A linguagem utilizada para processamento dos dados será o Python com as bibliotecas Pandas e NumPy. Para visualização dos dados será utilizada as bibliotecas Matplotlib e Seaborn. A biblioteca Scikit Learn será utilizada para construção de modelos de Machine Learning. 

# Resultados

O principal resultado obtido neste estudo foi de que do número total de óbitos (21.963), 96,8% foram confirmados positivos para COVID-19, em sua maioria homens (55,9%). A faixa etária que mais se contaminou possuía entre 30 e 40 anos e eram do sexo feminino. Apesar de grande parte da população do Ceará possuir entre 10 e 19 anos, a grande maioria dos óbitos acontece entre os 75 e 80 anos. Pode-se observar também que em 93,2% dos casos positivos para COVID-19 a internação não foi necessária. Demograficamente, a cidade com maior número de óbitos é Fortaleza (capital do Ceará), seguida por Caucaia (16,3km) e Maracanaú (23,4km).

Como resultados podemos observar que cerca de 45% dos óbitos pela doença no estado do Ceará foram pacientes que não possuíam comorbidade nenhuma e 31% dos pacientes possuíam pelo menos uma comorbidade. A maioria dos óbitos por COVID-19 eram de pacientes com problemas cardiovasculares e diabetes. Dados da secretaria de saúde do Distrito Federal (DF) exemplificam esse fato: dos mais de 300 mil infectados, em abril de 2021, pouco mais de 17 mil eram portadores de comorbidades, totalizando 17,2% dos casos. A grande maioria desses pacientes (56,6%) são cardiopatas, seguido de pacientes obesos (7,3%) e imunossuprimidos (5,6%). Além disso, no DF dentre os mais de 5 mil mortos pela COVID-19, 85,1% tinham outras doenças que agravaram o quadro da infecção [6]. 

O mesmo pode ser observado em estudos realizados pela Caixa de Previdência e Assistência aos Servidores da Fundação Nacional de Saúde (CAPESESP) que avaliou 600 pessoas em 2020, acometidas ou não pelo Sars-CoV-2. Esse estudo revelou que a taxa de mortalidade por COVID-19 de pessoas diabéticas é 10% maior que a taxa de mortalidade entre pessoas saudáveis, devido a vulnerabilidade do paciente diabético em lidar com o quadro infeccioso do vírus [7]. O mesmo é pontuado por Marinho e colaboradores, que apontaram a desregulação imunológica e a inflamação metabólica do paciente diabético como pontos chave capazes de reduzir a habilidade do organismo em desenvolver cura contra a doença, justificando a maior taxa de mortalidade associada à essa população [8].

Além disso, pode-se perceber que a taxa de letalidade da doença para casos mais graves (onde o paciente foi pra UTI) é maior, mais de 66% dos casos evoluiu para óbito. Diferente é observado em casos mais leves, onde mais de 67% evoluem recuperados. 

# Discussão

# Trabalhos Futuros

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
