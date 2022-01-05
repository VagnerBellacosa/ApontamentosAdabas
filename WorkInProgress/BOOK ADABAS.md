## [BOOK ADABAS](https://adabasmainframe.blogspot.com/2011/04/book-adabas.html)

Criado por Claudemar Martins de Sá Postado em domingo, abril 03, 2011 [4 comentarios](https://adabasmainframe.blogspot.com/2011/04/book-adabas.html#comment-form)

**OFF** - Eu comecei a escrever um livro sobre Adabas já fiz bastante coisa aproximadamente 50 páginas dai tive uma mudança de cargo no serviço - antes eu era DBA Adabas agora sou DBA SQL Server - vou deixar o livro parado por um tempo mais vou deixar o primeiro capitulo que escrevi para a galera para ver se aprova.



***\*Introdução\****

A empresa que desenvolveu o Adabas é a Software AG que tem sua matriz na cidade Darmstadt na Alemanha e filial em Reston, Virgínia nos EUA, sendo considerada uma das maiores empresas de software, notadamente de produtos voltados ao mercado de gerenciadores de bancos de dados, engenharia de aplicação e soluções para computação distribuída. Durante muitos anos, seus produtos eram voltados principalmente a ambientes de mainframes, porém, já a alguns anos vem desenvolvendo soluções para as mais diversas plataformas.

O Adabas (Adaptable Data Base System) é um sistema gerenciador de banco de dados, que em março de 1971 foi lançado para equipamentos Siemens, hoje atualmente ele roda em Mainframe nas plataformas, BS2000, z/OS, z/VSE mais também existem versões do Adabas para rodar em plataforma baixa (Unix, Linux e em Windows).

O Adabas é dividido categorias:

\- **Adabas C** - Além de rodar no mainframe, também roda na plataforma baixa (em UNIX, LINUX e WINDOWS).

\- **Adabas D** - É um banco de dados totalmente relacional que funciona nas plataformas, Windows (x86), AIX (Power), HP-UX (Itanium, Alpha), Solaris (SPARC), SUSE Linux Enterprise (x86, EM64T), Red Hat Enterprise Linux (x86, EM64T, zSeries)

O Adabas é um banco de dados baseado em Lista Invertidas. Ele é descrito no próprio manual da Software AG como um banco Relacional, mas pode ser comparado como um "Não Relacional" ou um "Quase Relacional" pelas suas características, ele tem tudo haver com o seu nome em si Adaptable Data Base System ou traduzindo Sistema de Banco de Dados Adaptável. Algumas diferenças entre o Adabas e um SGBD tradicional:

\- No Adabas é chamado de Files (Arquivos) e não Tabelas, como as principais unidade de organização;

\- Records (Registros) e não células, como menores unidade de organização;

\- Campos, e não colunas, como componentes de uma unidade;

\- Não baseado no sistema SQL precisando de um mecanismo de busca externo;

\- Dirty Read como modo de operação;

\- Suporta "Arquivo Expandido".

Um contraste comparado com outros SGBD que exigem um modelo único para todos os dados, o Adabas permite que você escolha qualquer tipo de estrutura que o Adabas permite. Você pode acessar os mesmos dados usando sua escolha de perspectiva do modelo de dados:

\- Relacionais, incluindo aninhamento relacional (tabelas dentro de tabelas);

\- Relação entre entidades, com capacidade comprovada para suportar objetos estruturais;

\- Modelo de Rede; Modelo Hierárquico;

\- Modelo Geográfico;

\- Texto;

Estes modelos de dados podem ser combinados em uma solução unica para qualquer empresa; múltiplas soluções pode visualizar os dados Adabas usando diferentes modelos de dados.

Ao desenvolver novas exigências, o Adabas evolui tanto em âmbito e complexidade sem redesenho do banco de dados ou a reprogramação de sistemas de aplicação. Por exemplo, as chaves de campo e de acesso podem ser adicionados a um arquivo Adabas a qualquer momento sem recarga ou reorganizar o arquivo.

O Adabas provou ser muito bem-sucedido em fornecer acesso eficiente aos dados e em manter a integridade da base de dados. O Adabas é agora usado extensamente nas aplicações que requerem um volume muito grande de processamento de dados, ou com grandes transações de processamento analitico online (OLAP).

Pela facilidade com que opera na recuperação de informações através de múltiplas chaves, o espaço é gerido dinamicamente os arquivos podem ser carregados e descarregados, rotinas de backup e de restauração e o desempenho do sistema pode ser analisado sem interromper a atividade do banco de dados.

***\*Destaques Operacionais\****

***\*Alta Disponibilidade\****

Adabas é projetado para funcionar sete dias por semana e 24 horas por dia. O espaço é gerido dinamicamente, os arquivos podem ser carregados e descarregados, backup e restauração, eo desempenho do sistema pode ser analisado sem interromper o banco de dados ativo.

***\*Otimização do armazenamento Espaço\****

O Banco de dados Adabas armazena em forma de comprimido para reduzir o espaço necessário. Desde bancos de dados modernos são medidos em gigabytes (1.000 megabytes) ou mesmo terabytes (1000 gigabytes), a economia de espaço em disco pode ser considerável. Os requisitos de espaço reduzido também significa que a entrada / saída (I/O) do sistema é mais eficiente.

***\*Desempenho\****

O desempenho é o factor chave do Adabas, que inclui uma série de recursos para melhorá-lo. Por exemplo, uma série de parâmetros de configuração estão disponíveis para afinar o ambiente de banco de dados operacional, e muitos deles podem ser modificados, enquanto o banco de dados está ativo.

***\*Tolerância a falhas\****

Adabas recupera automaticamente depois que um banco de dados anormais ou rescisão do sistema. Cada vez que um banco de dados Adabas é iniciado, uma verificação automática é iniciada para determinar se o banco de dados previamente terminadas de forma clara ou uma transação ativa foi interrompido. Se a transação foi interrompida, Adabas redefine automaticamente todas as alterações da transação não concluído, para que o banco de dados é consistente.

***\*Adabas Entidades\****

No Adabas, um campo é a menor unidade lógica de informação (por exemplo, o salário atual de um empregado) que podem ser definidos referenciados pelo usuário. Um registro é uma coleção campos relacionados que formam uma unidade completa de informação (por exemplo, todos os dados da folha de pagamento para um único funcionário). Um arquivos é um grupo de registros relacionados que têm o mesmo formato (com algumas exceções, ler vários tipos de registros em um arquivo). Um banco de dados é um grupo de arquivos relacionados.

***\*Limites do Adabas\****

O Adabas versão 8.1.2 tem os seus limites como qualquer banco, abaixo vamos destacar estes limites:

***\*Bases de dados\** - 65,535*****\*Blocos por banco\** - 2,147,483,646 usando RABNSIZE 4*****\*Arquivos por banco\** - o menor de 5.000 ou o tamanho do bloco Associator menos um*****\*Campos por registro\** - 926*****\*Comprimento do Descomprimento do Registro\** - Dependo do Sistema Operacional****
*****\*Terminologia e Conceitos Básicos\****

A terminologia a seguir pretende esclarecer os termos utilizados no Adabas, principalmente referentes aos conceitos básicos e típicos do mesmo.

***\*Registro\** – É um conjunto de campos constitui um registro Adabas, cada registro esta associado a um número seguencial interno (ISN) assinalado e administrado pelo Adabas. O comprimento do registro é variável, pois o Adabas armazena de forma comprimida os dados. Os registros são armazenados arbitrária na memória, através de uma tabela especial de controle de áreas disponíveis.**

***\*Bloco\** – Um bloco constitui um conjunto fisico de registros e possui tamanho fisico em função do tipo de disco utilizado. Cada vez que o Adabas transfere informações do disco para a memoria (ou vice e versa) é através do bloco fisico.**

***\*ISN\** – Internal Seguence Number – (Numero Seguencial Interno) Consiste num número seguencial interno associado a cada registro que entra no banco de dados Adabas, é único por arquivo, toda a manipulação de registro pelo Adabas base no ISN. O ISN tanto pode ser gerado pelo Adabas como pode ser assinalado pelo usuário.**

***\*RABM\** - Relative Block Number – O Adabas associa aos blocos dos data sets (ASSO, DATA entre outros) um número seguencial, o RBN é convertido em endereço fisíco do disco pelo método de acesso do sistema operacional (BDAM em IBM) antes de ser efetuada a operação de entrada e saida.**

O número de RABNs que pode ser atribuído a ASSO e o DATA depende do parâmetro RABNSIZE, que é especificado quando o banco de dados está definido. No RABNSIZE é especificado o comprimento relativo do número do bloco no banco de dados (não é o comprimento do bloco em si).

Se o banco foi definido com RABNSIZE=3 o número máximo de RABNs é 16.777.215 agora se foi definido com RABNSIZE=4 o máximo é 2.147.483.646.

***\*EXTENT\** – Um determinado Extent consist num conjunto de blocos fisícos contigos (de disco) alocados para uma determinada função Adabas.**

***\*FILE\** – (ARQUIVO) Um arquivo Adabas consiste num conjunto de blocos de dados do usuário e pode ser constituido de diversos extents fisicos.**

***\*FCB\** – (Bloco de controle de arquivo) – Para cada arquivo do banco existe uma FCB. Contém informações sobre área de estensão e de áreas livres.**

***\*FDT\** – Tabela de descrição de campos – Uma FDT corresponde a descrição dos campos que compõem cada FILE (arquivo) e corresponde ao esquema dos campos do campo no banco. Como os dados são compactados e há supressão de campos brancos e nulos, a FDT é frequentemente consultada quando uma vez obtida o valor de ISN e RABN, dai se efetua o varredura sequencial dos campos de registros lógicos. Na FTD estão em detalhes a descrição fisíca de todos os campos.**

***\*Qualificações Especiais de Campos Adabas\****

A seguir vamos destacar os tipos de campos para o Adabas.

***\*Campo\** – Corresponde ao nível elementar de informação manipulado pelo Adabas. Pode ser considerado como o campo propriamente dito onde está a informação. O campo esta associado atributos como nome, formato, comprimento, valor entre outras informações.**

***\*Campo Descritor\** - Um campo definido como descritor faz com que sejam criados as listas invertidas correspondentes aos diversos valores do campo. Assim, para um determinado valor de campo descritor ficar associado uma lista de ISN, e através de um conversor de endereços (Address Converter) podem ser obtidos pelo usuário os diversos blocos fisicos que contém os ISN. Para este tipo de campo a recuperação de dados deste tipo de campo é mais rapida.**

***\*Campo Multiplo\** – Pode possuir até 191 ocorrencias em um mesmo registro, onde ele pode assumir diversos valores dentro de uma ocorrência de registro. Cada campo deste tipo possui um contador que armazena a quantidade de ocorrencias do campo.**

***\*Campo de Grupo\** – Consiste em vários campos elementares consecutivos da FDT combinados em apenas um. Dessa forma pode-se acessar os campos com mais facilidade melhorando o desempenho quando devidamente utilizado durante o processo de manipulação de dados. A definição do campo grupo facilita o processo de referência aos campos e melhora o desempenho quando devidamente utilizado durante o processo de manipulação de dados.**

***\*Campo Periódico\** – É um campo que possibilita obter diversas ocorrencias dentro de uma mesma ocorrencia, pode ser repetido até 99 vezes. Não se pode definir um campo de grupo periódico dentro de outro grupo periódico, isso é, podemos ter somente um nivel de grupo periódico dentro do registro. O grupo periódico pode conter campos de múltiplos valores. A cada ocorrência do grupo periódico está associado um indice que indica a sua posição relativa entre as demais ocorrência do grupo.**

Exemplo de um registro em um campo

[![img](https://3.bp.blogspot.com/-vdx8RM_vysE/TZj0EEZYePI/AAAAAAAAF4g/9qAJElkSAYs/s400/field_types.png)](https://3.bp.blogspot.com/-vdx8RM_vysE/TZj0EEZYePI/AAAAAAAAF4g/9qAJElkSAYs/s1600/field_types.png)

***\*Observações\**: O Campo Multiplo deletando uma ocorrencia as outras ocorrencias assumem o lugar da que foi deletada, um exemplo você tem as ocorrencias 1,2,3 deletando a ocorrencia 2 a 3, 4 sobem (a 3 vai para o lugar da 2 e a 4 vai para o lugar da 3), agora o Campo Periodico você deletando a ocorrencia 2 este campo vai ficar em branco (1,x,3,4) - Outra diferença é a quantidade o campo de grupo cabe 191 ocorrencias agora o campo periodico cabe 99 ocorrencias.**

Quando se especifica um campo no Adabas, além do tipo, explicitam-se o formato, tamanho, opções de formatação e chaves (indices ou descritores). O comprimento máximo do campo que pode ser especificada em função do valor formato:

(**A**) Alfanumerico – De 1 até 253 bytes

(**B**) Binario – De 1 até 126 bytes

(**F**) Ponto Fixo – 8 bytes (exatamente 2, 4 ou 8 bytes)

(**G**) Ponto Flutuante – 8 bytes (4 ou 8 bytes)

(**P**) Decimal Compactado – Até 15 bytes

(**N**) Numerico – De 1 até 29 bytes

(**U**) Decimal Não Compactados – Até 29 bytes

(**W**) Wide character - 253 bytes

***\*HYPDE\** - O campo Hiperdescritor trata-se de descritores criados a partir de um algoritmo do próprio usuário. O descritor Hiperdercritor exige que o usuário escreva um algoritimo em linguagem assembly e este seja ligado em uma sub-rotina no banco Adabas.**

***\*PHONDE\** - O campo fonético é um campo definido com relação a um outro campo, o qual é considerado com o campo fonte de fonetização. Assim, se considerarmos a necessidade de pesquisa de forma fonética, uma base de dados de pessoal através do nome de funcionario. Campo Fonético não é permitidos em elementos de campos Periodicos.**

***\*SUBDE\** – O Subdescritor é um campo formado de uma parte de um outro campo.**

***\*SUBFN\** - O Subcampo é uma parte ou um subconjunto de um outro campo que pode ser lido como um campo normal. Subcampos não são permitidos adicionar ou atualizar registros.**

***\*SUPDE\** – O Superdescritor, é um campo formado de partes (ou de todo o campo) de diversos outros campos formando um novo campo descritor.**

***\*SUPFN\** – O Superfield é um campo formado por várias partes, porções, ou combinações de campos que podem ser lidos como um campo normal. Como subcampo, superdescritores não são permitidos ao adicionar ou atualizar registros.**

***\*Collation Descritor\** - Um alfanumérico ou um campo wide-character pode ser definido como um campo pai de um collation descritor. Um collation descritor é usado para classificar os valores de campo em uma seqüência especiais definidos pelo usuário. O comando LF relata a recolha de informação de campo descritor.**

Categories: [Adabas](https://adabasmainframe.blogspot.com/search/label/Adabas)