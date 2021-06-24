# Projeto: Estudo de fatores associados a mortes devido a COVID-19
# Project: Study of factors associated with deaths due to COVID-19

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

Neste trabalho foram utilizados dados anonimizados de pacientes com COVID-19 do estado do Ceará, que foram disponibilizados publicamente pela IntegraSUS/CE.

Este dataset possui 1.873.583 de registros de pacientes do estado do Ceará acompanhados com sintomas de COVID-19. O dataset possui 43 features (colunas), sendo algumas relevantes para este trabalho, como por exemplo a relação de comorbidades do paciente. Apesar de possuir muitos registros, o dataset apresenta aproximadamente 97% de informações faltantes em relação às comorbidades e outros fatores de risco. Mais informações sobre esse dataset podem ser obtidas no notebook de análise exploratória.

Além dos dados do IntegraSUS/CE foram utilizados dados demográficos dos municípios onde os pacientes residem, esses dados foram obtidos do portal do IBGE. Esse dataset possui informações demográficas, como área do município, população, renda, número de matrícula e índice de desenvolvimento Humano Municipal - IDHM. Esse dataset foi utilizado para verificar se fatores sociais podem estar associados às mortes por COVID-19.

Os datasets utilizados neste notebook são resultados das etapas de pré-processamento: limpeza de dados e transformação de dados. Para compreender melhor como os dados foram tratados é possível acessar os notebooks de preparação dos dados Dataset1:RandomForest e Dataset2:Regression COX

Este trabalho apresenta a aplicação de dois algoritmos de Machine Learning. O primeiro utiliza o algoritmo de florestas aleatórias (Random Forest) para classificar as mortes em decorrência de COVID-19 ou por outras causas. O Random Forest, assim como outros algoritmos baseados em árvores de decisão possibilitam o estudo de como a classificação foi realizada, de forma a compreender quais características ou fatores contribuem mais para o evento, nesse caso a morte por COVID-19.

O segundo algoritmo utilizado é o Regression COX, que faz parte da família de algoritmos de análise de sobrevivência. O modelo criado tem o objetivo de prever quais características (fatores) contribuem para a morte devido a COVID-19.

# Vídeos do Projeto
# Vídeo da Proposta

[Link para vídeo de apresentação da proposta do projeto.](https://youtu.be/59DZYWyoovo)

# Vídeo da Apresentação Final

[Link para vídeo de apresentação final do projeto.](https://youtu.be/PZiL9D5mvsE)

# Perguntas de Pesquisa

- Qual perfil da população Brasileira está mais suscetível ao óbito por meio de infecção por COVID-19?
- Quais características implicam em maior mortalidade por COVID-19?

# Bases de Dados
Para responder às perguntas de pesquisa será utilizada uma base de dados fornecida pelo Governo do Estado do Ceará. A base possui o registro dos infectados por COVID-19, apresentando suas comorbidades e o desfecho da infecção. Os dados foram obtidos do repositório no GitHub: https://github.com/integrasus/api-covid-ce.

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


# Metodologia
Em 2014, o Ministério da Saúde apresentou uma publicação [11], onde se relatou uma técnica de identificação de palavras-chave pesquisáveis que representassem uma questão de pesquisa clínica, por meio de uma estrutura conhecida pelo acrônimo PICOT, onde cada letra representa um componente da questão: P (população de interesse), I (intervenção de interesse), C (comparador), O (desfecho - outcome) e T (período de seguimento - timeframe). Dentro da mesma publicação, menciona-se o fato de que tal estrutura também costuma ser chamada pelo acrônimo PECO, onde a letra E se refere a Exposição a ser considerada, como, por exemplo, fator de risco ou fator prognóstico.

Neste projeto nossa população de interesse (P) é representada por indivíduos que foram notificados como possíveis portadores do Coronavírus. Desta forma, pode-se dizer que nossa Unidade de Estudo é o indivíduo com suspeita de COVID-19. A amostra selecionada consiste de uma base de dados composta por cerca de 1.685.731 registros de notificações no estado do Ceará. 

Trata-se de uma amostra de conveniência já que é a que dispomos até o presente momento. A intervenção de interesse (I) ou, nosso caso, o fator de exposição seria a influência das comorbidades e/ou outras características no aumento de casos de óbitos. Desta forma, o comparador (C) é dado pelo grupo de pessoas sem comorbidades que evoluíram para óbito - desfecho (O). O período de seguimento (T) consiste no intervalo que se inicia em 01-01-2020 e vai até o presente momento.

O estudo será do tipo Observacional, já que não teremos capacidade de controlar as variáveis de interesse da situação existente. Além disso, já que estamos lidando com uma janela temporal fixa, pode-se dizer que este estudo também é Transversal.

A partir da análise dos dados, espera-se encontrar correlações positivas (ou negativas) que nos permitam apresentar associações, por meio de um estudo descritivo. Pretende-se utilizar a técnica de Caso-Controle Retrospectivo, a fim de se identificar quais comorbidades contribuíram, em maior grau, para os casos de óbito.

# Ferramentas
A análise exploratória dos dados será realizada utilizando o notebook do Google Colab. A linguagem utilizada para processamento dos dados será o Python com as bibliotecas Pandas e NumPy. Para visualização dos dados será utilizada as bibliotecas Matplotlib e Seaborn.

A biblioteca Scikit Learn será utilizada para construção de modelos de Machine Learning. O objetivo é utilizar algoritmos supervisionados para prever os óbitos por Covid-19, dadas as características/comorbidades dos pacientes. Uma vez que o modelo esteja concluído, será extraído as características mais importantes, que levam os pacientes a óbito.


# Cronograma
<div dir="ltr" align="left"><table border="1" sytle="border: 1px solid #000"><colgroup><col><col width="8"><col width="8"><col width="8"><col width="8"><col width="8"><col width="8"><col width="8"><col width="8"><col width="8"><col width="8"><col width="8"><col width="8"><col width="8"></colgroup><tbody><tr><td colspan="14" style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">Cronograma</p></td></tr><tr><td style="border: 1px solid #000"><br></td><td colspan="4" style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">Abril</p></td><td colspan="4"><p dir="ltr" style="text-align: center;">Maio</p></td><td colspan="5" style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">Junho</p></td></tr><tr><td style="border: 1px solid #000"><p dir="ltr">Atividade/Semana do Ano</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">14</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">15</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">16</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">17</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">18</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">19</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">20</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">21</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">22</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">23</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">24</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">25</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">26</p></td></tr><tr><td style="border: 1px solid #000"><p dir="ltr">Definição do problema</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td></tr><tr><td style="border: 1px solid #000"><p dir="ltr">Coleta de dados</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td></tr><tr><td style="border: 1px solid #000"><p dir="ltr">Processamento/tratamento dos dados</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td></tr><tr><td style="border: 1px solid #000"><p dir="ltr">Análise/exploração dos dados</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td></tr><tr><td style="border: 1px solid #000"><p dir="ltr">Criação de modelo de ML</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="text-align: center;"><br></td></tr><tr><td style="border: 1px solid #000"><p dir="ltr">Interpretação dos resultados</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><br></td></tr><tr><td style="border: 1px solid #000"><p dir="ltr">Comunicação dos resultados</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><br></td></tr><tr><td style="border: 1px solid #000"><p dir="ltr">Apresentação do Trabalho</p></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><br></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td><td style="border: 1px solid #000"><p dir="ltr" style="text-align: center;">x</p></td></tr></tbody></table></div><br><p></p>
