No âmbito das bases de dados, isolamento é um propriedade que define quando e como uma mudança feita por uma transacção se torna visível para outras transacções concorrentes. O Isolamento é também uma das propriedades do ACID.

A maioria dos SGBD permitem definir o nível de isolamento das transacções, permitindo controlar o grau de concorrência da base de dados. Cabe ao programador decidir qual o nível de isolamento que mais se adequa a aplicação em causa, a maior parte das aplicações não requerem um nível de isolamento muito restritivo, permitindo assim uma grande concorrência e evitando a possibilidade de deadlocks, pois quanto mais alto o nível de isolamento, menos concorrência permite e mais probabilidade do sistema entrar em deadlock de recursos.

Existem quatro níveis de isolamento definidos no standard ANSI/ ISO SQL. São eles o Read Uncommitted, Read Committed, Repeatable Read e o Serializable, estes níveis são classificados de acordo com a possibilidade de ocorrência de determinados fenómenos indesejados, que podem ser “Dirty reads“, “non-repeatable reads” e “Phantons”, tanto os níveis como os fenómenos são de seguida devidamente explicados.

Dirty Read Non-Repeatable Read Phantom
Read Uncommitted Sim Sim Sim
Read Committed Não Sim Sim
Repeatable Read Não Não Sim
Serializable Não Não Não

Dirty Read (Read uncommitted)- Ocorre quando uma transacção (T1) modifica determinada informação e de seguida uma outra transacção (T2) lê a mesma informação antes que T1 faça commit dessa informação ou rollback. Caso T1 faça rollback, T2 leu informação que nunca chegou a existir oficialmente na base de dados.

Non-Repeatable Read- Quando uma transacção T1 está aceder a informação, e uma outra transacção T2 apaga ou modifica essa informação T1 não vai conseguir voltar a reler a informação caso seja necessário.

Phantom (Repeatable reads)- É quando uma transacção T1 lê um grupo de registos que satisfazem uma dada condição, de seguida uma transacção T2 modifica ou insere um registo que satisfaz essa condição e faz commit, de seguida se T1 voltar a a ler os registos nas mesmas condições irá obter um resultado diferente.

Níveis de isolamento
Read Uncommitted – Este é o primeiro e menos proibitivo nível de isolamento. Neste nível podem ocorrer os três fenómenos pois não é adquirido qualquer tipo de lock de dados.

Read Commited – Este nível é o usado por defeito no Oracle e no SQL Server. Neste nível os Dirty Reads não ocorrem pois são usados locks partilhados que asseguram que nenhuma informação corrompida ou alterada por outra transacção e que ainda não tenha sido commited é lida, no entanto não assegura que os dados não vão ser alterados antes do fim da transacção, permite portanto a ocorrência de non-repeatable reads.

Repetable Read - Neste nível são adquiridos locks de leitura, prevenindo a ocorrência de dirty reads e de non-repetable reads mas permite a ocorrência de Phantoms, pois não são adquiridos “range-locks“.

Serializable – No nível serializable todas as transacções ocorrem num meio fechado, isto é, são todas executadas de modo sequencial. O SGBD pode executar transacções concorrentemente apenas se a ilusão de seruação for mantida, ou seja, se uma transacção não partilhar qualquer tipo de dados com a outra. Neste nível são usados range locks, não permitindo portanto qualquer ocorrencia de pahntoms ou de outros fenomenos.