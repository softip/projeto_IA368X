# Projeto - Primeira Entrega

O objetivo geral do projeto final desta disciplina é realizar a análise de dados relacionados à saúde, para usá-los em uma das seguintes possíveis tarefas: recomendação, estudo de associações, validação de hipóteses, análise exploratória, análise visual, análise comparativa e predição.

Na primeira entrega do projeto, seu grupo deverá:

 - Criar um repositório GitHub ou GitLab **público** que será usado ao longo de todo o projeto (o link deverá ser submetido na atividade correspondente no Google Classroom da disciplina);
 - Organizar o repositório segundo a estrutura de diretórios proposta abaixo;
 - Editar arquivo README.md do repositório com a proposta inicial do projeto, segundo modelo descrito a seguir;
 - Disponibilizar vídeo de duração máxima de 3 minutos de apresentação da proposta do projeto. Não é necessário que todos os membros da equipe apareçam ou participem do vídeo.

Após a primeira entrega, será agendada (em horário de aula) uma data de arguição da proposta de projeto. É obrigatória a participação de todos os membros durante o momento da arguição da proposta. Durante a arguição, os professores fornecerão feedbacks sobre a proposta e seu grupo poderá tirar dǘvidas sobre o encaminhamento do projeto. 

# Estrutura do Repositório

A fim de uniformizar os repositórios de projetos da disciplina, os diretórios de seu repositório deverão ser nomeados e utilizados segundo a estrutura sugerida em [Home - Cookiecutter Data Science](https://drivendata.github.io/cookiecutter-data-science/), na seção "Directory structure".

Note que nem todos os diretórios ou arquivos serão necessários para todos os projetos. Foque em seguir o padrão para os diretórios que forem necessários. Não crie diretórios que não serão utilizados.

Seu repositório deverá obrigatoriamente conter o arquivo README.md, arquivo de documentação Markdown, que deverá conter a descrição do projeto conforme orientações a seguir.


# Editando Arquivo README.md

Este é um guia de como produzir documentação em Markdown. Para entender como criar documentos em Markdown no Github, veja o material/vídeo:
[Guia de Uso do Markdown](https://github.com/mc-unicamp/oficinas/tree/master/docs).

Vide detalhes sobre o Markdown em: [Mastering Markdown](https://guides.github.com/features/mastering-markdown/).

E mais especificamente sobre tabelas em: [Organizing information with tables](https://help.github.com/en/articles/organizing-information-with-tables)

Segue abaixo o modelo de como deve ser apresentado e documentado o projeto. Tudo o que for indicado entre `<...>` indica algo que deve ser substituído pelo indicado. No modelo são colocados exemplos ilustrativos, que serão substituídos pelos do seu projeto.

Segue abaixo o modelo de como devem ser documentadas as entregas.
> Tudo o que aparecer neste modo de citação se refere algo que deve ser substituído pelo indicado. No modelo são colocados exemplos ilustrativos, que serão substituídos pelos do seu projeto.

# Modelo para Apresentação do Projeto

# Projeto: Ciência de dados aplicada na definição de subgrupos prioritários para o Plano Nacional de Vacinação contra COVID-19.
# Project: Data science applied in the definition of priority subgroups for the National Vaccination Plan against COVID-19.

# Apresentação

O presente projeto foi originado no contexto das atividades da disciplina de pós-graduação [*Ciência e Visualização de Dados em Saúde*](https://github.com/datasci4health/home), oferecida no primeiro semestre de 2021, na Unicamp.

|Nome  | RA | Especialização|
|--|--|--|
| Ana Carolina Furiozo Arantes  | 228122  | Saúde|
| Ivan Paulino Pereira  | 262125  | Computação|
| Kleber Marcelo da Silva Rezende  | 232154  | Computação|
| Marília Santoro Cardoso  | 207705  | Saúde|


# Descrição Resumida do Projeto
O novo coronavírus (SARS-CoV-2), vírus causador da doença COVID-19, foi identificado pela primeira vez na cidade de Wuhan, localizada na China, em dezembro de 2019 [1]. Rapidamente, o vírus se disseminou mundialmente, o que levou a Organização Mundial de Saúde (OMS) a declarar que a epidemia da COVID-19 constituía uma Emergência de Saúde Pública de Importância Internacional, em 30 de janeiro de 2020 e, em 11 de março de 2020, uma pandemia [1, 2].

O primeiro registro no Brasil ocorreu em 26 de fevereiro de 2020 e o primeiro óbito em 20 de março do mesmo ano. Com a ascensão dos números de óbitos, a pandemia tem se apresentado como um dos maiores desafios sanitários mundial deste século [1–3]. Atualmente, a população brasileira totaliza cerca de 348 mil mortes pela doença, além de aproximadamente 13 milhões de casos confirmados [4].

A alta taxa de letalidade se dá devido sua alta transmissibilidade. A transmissão do vírus ocorre através de gotículas contaminadas de secreções da orofaringe de uma pessoa infectada, por contato com objetos e superfícies contaminadas, ou por via fecal-oral. Além disso, a transmissão é intensificada pelo elevado tempo de incubação (cerca de 5-6 dias, variando de 0 a 24 dias), e devido a pessoas assintomáticas, pré-sintomáticas ou com sintomas leves poderem espalhar a doença [2].

O SARS-CoV-2 foi nomeado como síndrome respiratória aguda grave coronavírus-2 devido à sua alta homologia (aproximadamente 80%) com SARS-CoV, que causou a síndrome do desconforto respiratório agudo e alta mortalidade durante 2002–2003. O vírus SARS-CoV-2 afeta principalmente o sistema respiratório. Além de envolver sintomas relacionados à infecção do trato respiratório inferior, incluindo febre, tosse seca e dispneia, cefaleia, tontura, fraqueza generalizada, vômito e diarreia [5].

Um número de mortes de pacientes com doenças graves continuou a aumentar em todo o mundo. Estudos epidemiológicos têm mostrado que a mortalidade acomete mais pessoas idosas e portadoras de doenças crônicas subjacentes, que requerem hospitalização, cuidados intensivos e uso de ventiladores mecânicos [2, 5].

Dados da secretaria de saúde do Distrito Federal (DF) exemplificam esse fato: dos mais de 300 mil infectados, pouco mais de 17 mil são portadores de comorbidades, totalizando 17,2% dos casos. A grande maioria desses pacientes (56,6%) são cardiopatas, seguido de pacientes obesos (7,3%) e imunossuprimidos (5,6%). Além disso, no DF dentre os mais de 5 mil mortos pela COVID-19, 85,1% tinham outras doenças que agravaram o quadro da infecção [6]

O mesmo pode ser observado em estudos realizados pela Caixa de Previdência e Assistência aos Servidores da Fundação Nacional de Saúde (CAPESESP) que avaliou 600 pessoas em 2020, acometidas ou não pelo Sars-CoV-2. Esse estudo revelou que a taxa de mortalidade por COVID-19 de pessoas diabéticas é 10% maior que a taxa de mortalidade entre pessoas saudáveis, devido a vulnerabilidade do paciente diabético em lidar com o quadro infeccioso do vírus [7]. O mesmo é pontuado por Marinho e colaboradores, que apontaram a desregulação imunológica e a inflamação metabólica do paciente diabético como pontos chave capazes de reduzir a habilidade do organismo em desenvolver cura contra a doença, justificando a maior taxa de mortalidade associada à essa população [8].

Em 16/12/2020 o governo brasileiro lançou o Plano Nacional de Imunização - PNI. O plano apresenta a caracterização dos grupos de risco para agravamento e óbito pela COVID-19. De acordo com o PNI, os principais fatores de risco associados a progressão para formas graves da doença e ao óbito são:

idade superior a 60 anos; diabetes mellitus; doença pulmonar obstrutiva crônica (DPOC); doença renal; doenças cardiovasculares e cerebrovasculares; hipertensão arterial grave; indivíduos transplantados de órgãos sólidos; anemia falciforme; câncer e obesidade mórbida (IMC≥40). 

O PNI define 14 grupos prioritários para vacinação, sendo eles: Trabalhadores de Saúde; Pessoas de 80 anos e mais; Pessoas de 75 a 79 anos; Pessoas de 70 a 74 anos; Pessoas de 65 a 69 anos; Pessoas de 60 a 64 anos; População indígena aldeado em terras demarcadas aldeada; Povos e comunidades tradicionais ribeirinhas e quilombolas; Grupo com comorbidades*; Trabalhadores da educação; Pessoas com deficiência permanente severa; Forças de Segurança e Salvamento; Funcionários do sistema de privação de liberdade; População privada de liberdade. Além disso, estima-se que serão necessárias 104.265.535 (cento e quatro milhões, duzentos e sessenta e cinco mil, quinhentos e trinta e cinco) doses, para vacinar uma população de 49.650.255 (quarenta e nove milhões, seiscentos e cinquenta mil, duzentos e cinquenta e cinco) pessoas dos grupos de Trabalhadores da saúde, pessoas com 60 anos ou mais e o Grupo com comorbidades.

Com o surgimento de novas linhagens do vírus de maior transmissibilidade, pesquisadores brasileiros já apontaram uma piora na situação epidemiológica das regiões acometidas por essas variantes. Entretanto, diferentemente do que tem sido apontado, Freitas e colaboradores sugerem uma mudança no padrão de mortalidade da doença, já que jovens entre 20-39 anos tem sido a população mais acometida com uma taxa de letalidade maior em 2,7 vezes [9].
Assim, a ampla capacidade de mutacidade do Sars-CoV-2, bem como a mudança de foco de infecção do vírus reiteram mais do que nunca o início de ações como: maiores estudos sobre a eficácia das vacinas disponíveis no país, compartilhamento mais eficiente de dados e informações referentes à pandemia além de um maior engajamento por parte dos envolvidos na produção de conhecimento sobre o assunto no Brasil [10].

Dado a quantidade reduzida de vacinas e o agravamento da doença, esse trabalho procura propor subgrupos de prioridade para imunização, considerando os fatores de risco. Além disso,  procura encontrar novos grupos de prioridade, dada a  mudança no padrão de mortalidade da doença.

> 
> Link para vídeo de apresentação da proposta do projeto (máximo 3 minutos).

# Perguntas de Pesquisa

- Qual perfil da população Brasileira está mais suscetível a sofrer ao óbito por meio de infecção por COVID-19?
- O programa de vacina está priorizando os grupos identificados?
- Quais características implicam em maior mortalidade por COVID-19?

# Bases de Dados
Para responder às perguntas de pesquisa será utilizada uma base de dados fornecida pelo Governo do Estado do Ceará. A base possui o registro dos infectados por COVID-19, apresentando suas comorbidades e o desfecho da infecção. Os dados foram obtidos do repositório no GitHub: https://github.com/integrasus/api-covid-ce.

A tabela abaixo apresenta o dicionário de dados do conjunto.


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
> Proposta de cronograma. Procure estimar quantas semanas serão gastas para cada etapa do projeto.
