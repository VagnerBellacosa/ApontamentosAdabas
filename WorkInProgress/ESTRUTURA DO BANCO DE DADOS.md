## [ESTRUTURA DO BANCO DE DADOS](https://adabasmainframe.blogspot.com/2013/04/estrutura-do-banco-de-dados.html)

Criado por Claudemar Martins de Sá Postado em terça-feira, abril 16, 2013 [Sem Comentarios](https://adabasmainframe.blogspot.com/2013/04/estrutura-do-banco-de-dados.html#comment-form)

**Estrutura do Banco de Dados**

Um banco de dados Adabas consiste em um ou mais arquivos de dados do usuário, e também todas os dados e arquivos necessarias para o Adabas na Administração do banco de dados. O banco Adabas é composto por alguns data sets para ele poder rodar no mainframe. ASSO / DATA / WORK – (PLOG / CLOG)

Data sets do Adabas
+----------------------------+   +-----------------------------------------------------+
|  Banco de Dados Adabas  |   |        Outros tipos de Data Sets      |
| +---------------------+  |   | +---------------------+  +---------------------+ |
| |           |  |   | |           |  |           | |
| |   ASSOCIATOR   |  |   | |PROTECTION LOG (PLOG)|  |     TEMP    | |
| |           |  |   | |           |  |           | |
| +---------------------+  |   | +---------------------+  +---------------------+ |
|              |   |                           |
| +---------------------+  |   | +---------------------+  +---------------------+ |
| |           |  |   | |           |  |           | |
| |  DATA STORAGE   |  |   | | COMMAND LOG (CLOG) |  |    SORT1    | |
| |           |  |   | |           |  |           | |
| +---------------------+  |   | +---------------------+  +---------------------+ |
|              |   |                           |
| +---------------------+  |   | +---------------------+  +---------------------+ |
| |           |  |   | |           |  |           | |
| |    WORK     |  |   | | RECOVERY LOG (RLOG)|  |    SORT2    | |
| |           |  |   | |           |  |           | |
| +---------------------+  |   | +---------------------+  +---------------------+ |
|              |   |                           |
+----------------------------+   +-----------------------------------------------------+

**ASSOCIATOR** – Cada registro que é armazenado no banco de dados é associado para ele um número seguencial interno (ISN) onde este número é único por arquivo, o data set Associator é onde estão armazenado estas informações, além disso o Associator contém:

\- Dois blocos de controle geral (GCBs) para o banco de dados. O GCBs fornece informações sobre as características físicas do banco de dados, tais como identificação o banco de dados de identificação (DBID), o número de arquivos carregados, o número de Associator, Data Storage, extents de Trabalho e os tipos de dispositivos de Trabalho, informações sobre o sistema de arquivos, e as extents do Data Storage Space Table (DSST), e o indicador de versão do banco de dados.

\- Para cada arquivo uma individual file control blocks (FCBs). O FCBs identificam as características físicas e RABNs associados dos arquivos do banco de dados. O conteúdo inclui o nome do arquivo, número do processo, o status do arquivo atual, as configurações de reutilização do ISN, as configurações de reutilização do espaço, as configurações do minimo e maximo ISN, os primeiros ISN livres, e o número de atualizações com o arquivo. Além disso, os primeiros e os ultimos RABN, e os primeiros RABNs não utilizadas são armazenadas no FCB.

\- Todas as tabelas necessárias para controlar e manter o banco de dados, incluindo uma tabela de definição de campo (FDT) para cada arquivo e listas de engate para arquivos fisicamente acoplados. Para obter mais informações sobre o FDT, leia Records e Definições de campo. Para obter mais informações sobre arquivos fisicamente acoplado, leia Acoplado arquivos.

\- Uma lista invertida para cada descritor em cada arquivo do banco de dados e do conversor de endereço de cada arquivo.

\- Se o banco tiver spanned records (registros estendidos) são usados em um arquivo, um conversor de endereço secundário para o arquivo.

**DATA STORAGE** – É onde no banco estão os dados, o Adabas armazena estes dados de forma comprimida, diminuindo o indice de utilização de memória em disco.

Data Storage é dividido em blocos que são chamados de RABN, estes blocos são definidos no inicio quando é criado o banco que podem ser RABN 3 ou RABN 4 eles são importantes para o banco pois determina a quantidade de registros que o banco vai suportar (RABNSIZE=3 suporta até o número máximo de RABNs de 16.777.215 e o RABNSIZE=4 suporta até o máximo é 2.147.483.646 RABN). o RABN identifica a localização fisica de um registro no banco. Blocos de armazenamento de dados contém um ou mais registros físicos e uma área de enchimento para absorver o 
expansão dos registros no bloco. 

Um identificador lógico armazenado nos primeiros quatro bytes de cada registro físico é o único controle 
informações armazenadas no bloco de dados. Este interna Número de seqüência ou ISN identifica cada 
registro muda e nunca. Quando um registro é adicionado, é atribuído um ISN iguais ao maior existente 
ISN mais um. Quando um registro é excluído, o seu ISN é reutilizado apenas se você instruir Adabas para o fazer. 

Reutilizando ISNs reduz a sobrecarga do sistema durante alguns pesquisas e é recomendado para arquivos com registros que freqüentemente são adicionados e excluídos. 

Para cada arquivo, entre 10-90 por cento (padrão 10%) de cada bloco pode ser alocado como preenchimento com base no a quantidade eo tipo de atualização que o esperado. Este espaço reservado permite expandir sem registros migrando para outro bloco e, portanto, ajuda a minimizar a sobrecarga do sistema.



[![img](https://4.bp.blogspot.com/-ElAmVYKjVsc/UW29cI1zLVI/AAAAAAAAIdc/qIjGcQnX3dY/s1600/storage_blocks.png)](https://4.bp.blogspot.com/-ElAmVYKjVsc/UW29cI1zLVI/AAAAAAAAIdc/qIjGcQnX3dY/s1600/storage_blocks.png)



**WORK** – Contém a área de proteção de dados e de armazenamento temporário para resultados intermediários durante as operações de busca complexos ou processamento de transações distribuídas. Este data set pelo nucleo do banco Adabas como arquivo de trabalho que executa as tarefas abaixo:

01 – Proteção e recuperação do banco de dados.
02 – Armazenamento intermediario das listas de ISN proveniente de pesquisas.
02 – Area intermediaria para operação dos algoritimos de pesquisa.

**Outros Componentes**

**Protection Log e Command Log**

O Adabas usa as seguintes data set de logs, elas são são opcionais, não necessita delas para que o Adabas possa funcionar:

**Command Log** (CLOG) registra as informações do bloco de controle de cada comando Adabas que é emitido. O CLOG proporciona uma trilha de auditoria e pode ser usado para depuração e para o acompanhamento da utilização dos recursos. O CLOG é usado para se fazer estatísticas sobre os programas, usuários, jobs, files (entre outros) que acessam o banco, com a Command Log habilitado (e com uma ferramenta que analise estas informações) dá para saber qual é o pior programa (e o comando que ele deu) no banco que esta consumindo mais recursos do banco, isso é bom para se fazer auditoria. A Software AG tem tema uma ferramenta que analisa os dados da Command Log e mostra tudo detalhado para os DBA o nome dela é Review, tem um outro software chamado Trim da Treehouse que faz algo parecido com os dados do Command Log.

**Protection Log** (PLOG) registra as imagens de antes e as imagens após dos registros e outros elementos quando são feitas alterações à base de dados. Ele é usado para recuperar o banco de dados (até a última transação concluída ou "ET") após a reinicialização. 

O **Recovery Log** (RLOG) é usado quando ocorre uma falha de funcionamento no banco de dados, o Adabas Recovery Aid pode criar um fluxo de trabalho que reconstrói o banco de dados até o ponto de falha. O Recovery Aid combina o registo de protecção (PLOG) e o status de banco de dados arquivados em operações anteriores ADASAV com a sua próprio RLOG para reconstruir a seqüência de trabalho. O resultado é uma seqüência de instrução reconstruída trabalho (recuperação de fluxo de trabalho) que é colocado em uma saída de dados, especialmente conjunto nomeado. 

**Data set de SORT e TEMP**

Determinados utilitarios Adabas (ADAINV, ADALOD) precisam de dois data sets adicionais, SORT e TEMP, para fazer a triagem e armazenamento intermediario dos dados. Algumas funções exigem outras utilidades para o data set de TEMP para o armazenamento intermediario. O tamanho do data set de TEMP/SORT varia de acordo com a função a ser executada. Estes data sets são usando durante ao trabalho e quando termina este trabalho os arquivos que foram carregados nos data sets de TEMP/SORT é liberado

**Arquivos de Sistema**

O Adabas usa determinados arquivos para armazenar informações de sistema e para o proprio controle do banco. Arquivos como de Checkpoint, Security, System File ou arquivos Coupled o número do file não pode ser superior a 255, outros arquivos, incluindo o arquivo de trigger pode ter dois bytes no número do file, número dos arquivos são atribuido pelo DBA Adabas em qualquer seguencia, a versão 8.2.2 do Adabas usa estes arquivos de sistema:

**CHECKPOINT** - É um arquivo de sistema é utilizado para armazenar informações de checkpoint e dados relacionados com os processos de reinicio ou back-out a nível de transação online, ou ainda transações em tarefas de sincronização de checkpoint de jobs batch.

**SECURITY** - Este é o arquivo de segurança.

**SYSFILE** - É um system file do Adabas. Este tipo de arquivo de sistema é utilizado para alguns ADD-ONS do Adabas (por exemplo, Sysfiles 5 e 6 são reservados para o núcleo do Adabas Transaction Manager (ATM) por exemplo.

**TRIGGER** - Arquivos onde estão armazenadas os procedimentos das triggers.

**Couple Files**

Arquivos de Acoplamento (Couple Files) permite a você selecionar, usando um único comando de busca. os registros de um arquivo que estão ligados (Couple) para os registros contendo valores especificos em um segundo file adabas.

Dois arquivos com o número abaixo de 255 podem ser fisicamente acopladas se um descritor comum, com formato idêntico e definições de comprimento que está presente em ambos os arquivos. Um único arquivo pode ser associado a até 18 outros arquivos, mas apenas uma relação de engate pode existir entre dois arquivos de uma vez. Um arquivo não pode ser associado a si mesmo.

Quando os arquivos estão acoplados, listas de engate são criados no Associator para cada arquivo a ser acoplado. Arquivo de engate é bidirecional e não hierárquico em que o acoplamento duas listas são criadas para cada relação de engate com cada lista contendo os ISNs que são acoplados a outro arquivo.

Uma vez que as listas de ligação física ter sido criado, qualquer campo de chave em qualquer arquivo pode ser usado dentro de um critério de pesquisa.

Acoplamento físico pode adicionar uma quantidade considerável de sobrecarga, se os arquivos envolvidos são atualizados com freqüência. As listas de engate deve ser atualizada se um registro em um dos arquivos é adicionado ou excluído, ou se o descritor utilizado como base para o engate é atualizado em qualquer arquivo.

Acoplamento físico pode ser útil para sistemas de recuperação de informação em que

\* arquivos raramente mudam;
\* a sobrecarga adicional da lista de engate é insignificante em comparação com a maior facilidade de formulação de consultas, ou
\* arquivos são pequenos e principalmente de consulta orientada.

File Coupling (Duas Views) 

Primeira View File 10
DDM DBID 0   DDM FNR 10  VSAM Name     Default Sequence
                                 
T L DB Name               F Leng S D Remark   
\- - -- -------------------------------- - ---- - - -----------
 1 AA S-NR             N 5.0  N D   
 1 AB A-NR             N 5.0  N D   
 1 AC S-NAME            A 10  N 
 1 AD S-COMM            N 3.0  N D

Segunda View File 40

DDM DBID 0   DDM FNR 40  VSAM Name     Default Sequence
                                 
T L DB Name               F Leng S D Remark   
\- - -- -------------------------------- - ---- - - -----------
 1 AA A-NR             N 5.0  N D   
 1 AB S-NR             N 5.0  N D   
 1 AC A-TURNO            N 8.0  N D

Da primeira view o campo **AA** - nome **S-NR** é um número 5.0 descritor é igual ao campo AB - nome S-NR é um número 5.0 descritor da segunda view

**Arquivos Expandido**

Se você tem um grande número de registros de um único tipo, você pode precisar distribuir os registros através de vários arquivos físicos.

Para reduzir o número de arquivos acessados o Adabas permite unir vários arquivos físicos contendo registros do mesmo formato, em conjunto como um único arquivo lógico. Essa estrutura é chamada de arquivo expandido (expanded file) e os arquivos físicos que o compõem são os arquivos do componente. Um arquivo expandido pode incluir até 128 arquivos de componentes, cada um com uma gama única de ISNs lógico. Um arquivo expandido não pode exceder 4.294.967.294 registros.

**Nota** - O Adabas agora suporta arquivos maiores e um maior número de arquivos e bancos de dados Adabas fisicamente, a necessidade de arquivos expandidos existe, na maioria dos casos, não é muito utilizada atualmente.

Categories: [Adabas](https://adabasmainframe.blogspot.com/search/label/Adabas)