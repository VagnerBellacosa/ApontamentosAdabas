## [COMANDOS PARA O NÚCLEO DO BANCO DE DADOS ADABAS](https://adabasmainframe.blogspot.com/2013/04/comandos-para-o-nucleo-adabas.html)

Criado por Claudemar Martins de Sá Postado em terça-feira, abril 16, 2013 [Sem Comentarios](https://adabasmainframe.blogspot.com/2013/04/comandos-para-o-nucleo-adabas.html#comment-form)

Com o bando de dados no ar podemos dar comandos em uma sessão Adabas;

- terminar uma sessão de usuário ou Adabas;
- exibição ou informar do núcleo;
- log de comandos - CLOG;
- No Adabas pode alterar os parâmetros de funcionamento ou de condições.

Neste documento, os comandos são listados em ordem alfabética. Um comando, DSTA, está listado duas vezes: uma vez como um comando para exibir o status do núcleo, e, separadamente, como um comando para mostrar o status atual de operação utilitário Adabas.



- Para Adabas Caching Facility operator commands, consulte a documentação do Adabas Caching Facility.
- Para comandos do operador Adabas Parallel Services, consulte a documentação do Adabas Caching Facility operator commands.
- Para comandos do operador em um ambiente de cluster sysplex, consulte a documentação do Adabas Cluster Services.
- Dando comandos em sistemas z/OS

- Para entrar com os comandos do operador em ambientes z / OS, o uso do z / OS comando MODIFY (F), conforme mostrado abaixo:

- F JOBNAME-ADABAS,COMANDO

- Exemplo;

- F STC-DO-ADABAS,ADAEND

- É o comando para retirar o banco de dados do ar.

- COMANDOS

- Comando ADAEND

-  

- \- Use o comando ADAEND para encerrar a sessão Adabas normalmente. Após feito este comando não serão aceitos novos usuários para acessar o banco de dado. ET é a lógica de atualização continuou até o fim da transação atual lógica para cada usuário. Depois de toda a atividade foi concluída, conforme descrito acima, a sessão é encerrada Adabas. Em ambientes de núcleo cluster, a opção global pode ser usado para encerrar a sessão Adabas em todos os núcleos de cluster ativo.

- ```
  STC03611  F AAFAI333,ADAEND                                                 
  STC01517  +ADAN51 00333 2011-02-09 16:56:12 Operator type-in: ADAEND        
  STC01517  +ADAN42 00333 2011-02-09 16:56:12 Function accepted               
  STC01517  +ADAM97 00333 This ASCB/initiator will be terminated by MVS at EOJ
  STC01517  IEF404I AAFAI333 - ENDED - TIME=16.56.12                          
  STC01517  IEF352I ADDRESS SPACE UNAVAILABLE                                 
  STC01517  $HASP395 AAFAI333 ENDED
  ```

- Comando ALOCKF

-  

- \- Use o comando ALOCKF bloquear um arquivo com antecedência para garantir que um usuário EXU, EXF, ou UTI terá o controle exclusivo do arquivo especificado. O avanço bloqueio impede que novas operações possam usar o arquivo. Uma vez que todos os usuários atuais deixaram de usar o arquivo, o usuário tem o controle exclusivo do lock. Até então, o usuário controle exclusivo precisa esperar.

- ```
  -- Prendendo o file
   STC08623  F AAFAI333,ALOCKF=29                                                 
   STC01151  +ADAN41 00333 2018-07-26 08:34:22 Function completed                 
  
  -- Display pra ver se o file esta preso
   STC08623  F AAFAI333,DLOCKF                                                    
   STC01151  +ADAN30 00333 2018-07-26 08:34:35 No files locked                    
   STC01151  +ADAN30 00333 2018-07-26 08:34:35 A-Files=00029                      
   STC01151  +ADAN41 00333 2018-07-26 08:34:35 Function completed    
  
  -- Retirando lock
   STC08623  F AAFAI333,RALOCKF=29                                                
   STC01151  +ADAN41 00333 2018-07-26 08:37:18 Function completed 
  
  -- Display pra ver se o file esta preso
   STC08623  F AAFAI333,DLOCKF                                                    
   STC01151  +ADAN30 00333 2018-07-26 08:37:48 No files locked                    
   STC01151  +ADAN41 00333 2018-07-26 08:37:48 Function completed
  ```

- Para remover o bloqueio do avanço sem executar o utilitário, consulte o comando RALOCKF. Este comando não está disponível no modo single user ou para um núcleo só de leitura.

- Comando AOSLOG

-  

- \- Use o comando AOSLOG para ativar ou desativar o log de registro do Adabas em determinadas chamadas que modificar o núcleo para DD/PRINT. Essas chamadas são emitidos por ADADBS OPERCOM ou Adabas Online System. Read e display as chamadas não são registrados.

- Comando ASYTVS 

- \- Use o comando ASYTVS é para ativar ou desativar o asynchronous flushing of buffers no número de série do volume.

- Comando CANCEL

-  

- \- Use o comando CANCEL para cancelar a sessão Adabas imediatamente. Todo o processamento que estiver usando o banco de dados será imediatamente suspensa. A rotina de autorestart a ser executada durante a inicialização da sessão Adabas que vai resolver as pendencias que faltaram a ser feitas no banco. Em ambientes de cluster núcleo, a opção global pode ser usado para cancelar a sessão Adabas em todos os núcleos de cluster ativo.

- Comando CLOGMRG

-  

- \- Use o comando CLOGMRG dinamicamente modifica a configuração do parâmetro ADARUN CLOGMRG. O comando CLOGMRG é válida apenas em ambientes de cluster. É global, por definição, e afeta todos os núcleos do cluster.

- Comando CLUFREEUSER

-  

- \- O comando CLUFREEUSER é válida apenas em ambientes de cluster. Pode ser emitida para o núcleo local, ou, com a opção global, contra todos os núcleos ativos e inativos do cluster. Use o comando CLUFREEUSER para excluir restos de agrupar os elementos da tabela de usuário (UTEs ou PLXUSERs) armazenadas em comum que já não estão associados a elementos do usuário fila (UQEs) em um núcleo.

- Comando CT

-  

- \- Use o comando do CT para dinamicamente substituir o valor do parâmetro ADARUN do banco, ou seja, o número máximo de segundos que podem decorrer do tempo um comando Adabas foi concluída até que os resultados são retornados para o usuário através da comunicação interregion (que depende da particular sistema operacional usado). A configuração mínima é 1, o máximo é 16777215. Em ambientes de cluster núcleo, o comando do CT é, por definição, global e afeta todos os núcleos do cluster.

- Comando DAUQ

-  

- \- Use o comando DAUQ para mostrar os elementos do usuário fila de usuários que tenham executado o comando, pelo menos, um Adabas nos últimos 15 minutos.

- ```
  STC03611  F AAFAI330,DAUQ                                            
  STC08763  +ADAN11 00330 2011-02-09 16:58:11 User=00000001,JN=BROK330
  STC08763  +                       ,TID=G.K.....(C749D29035CA7002)    
  STC08763  +                                   TY= E,LA=19 S          
  STC08763  +ADAN11 00330 2011-02-09 16:58:11 User=00000002,JN=BROK330
  STC08763  +                       ,TID=G.K.....(C749D29035CACF42)    
  STC08763  +                                   TY= E,LA=19 S          
  STC08763  +ADAN11 00330 2011-02-09 16:58:11 User=00000287,JN=COMPLETD
  STC08763  +                       ,TID=DBA21(C1C1F9F5F0F0F4F1)    
  STC08763  +                                   TY= E,LA=97 S          
  STC08763  +ADAN11 00330 2011-02-09 16:58:11 User=00000288,JN=COMPLETD
  STC08763  +                       ,TID=DBA22(C1C1F9F5F0F0F4F2)    
  STC08763  +                                   TY= E,LA=89 S          
  STC08763  +ADAN41 00330 2011-02-09 16:58:11 Function completed       
  ```

- Comandos DCQ

-  

- \- Use o comando DCQ para mostrar todos os elementos de comando postado fila (CQEs). O comando DCQ mostra ID de cada usuário do CQE, nome do trabalho e tamanho do buffer.

- ```
  STC03611  F AAFAI333,DCQ                                       
  STC01517  +ADAN14 00333 2011-02-09 16:54:06 Current CQ is empty
  STC01517  +ADAN41 00333 2011-02-09 16:54:06 Function completed 
  ```

- DDIB

-  

- \- Use o comando DDIB para exibir o bloco de integridade de dados (DIB). Este bloco contém entradas indicando quais utilitários Adabas estão ativos e os recursos que estão sendo utilizados por cada utilitario.

- ```
  STC03611  F AAFAI333,DDIB                                                      
  STC01517  +ADAN25 00333 2011-02-09 16:53:06 DIB                                
  STC01517  +ADAN25 00333 2011-02-09 16:53:06 Jobname=AAFAI333,Starttime=16:42:29
  STC01517  +                                                                    
  STC01517  +ADAN41 00333 2011-02-09 16:53:06 Function completed                 
  ```

- Comando DDSF

-  

- \- Use o comando DDSF para mostrar Adabas Delta Save status Facility. O comando DDSF só está disponível se o núcleo Adabas é executado com o parâmetro ADARUN DSF=YES.

- Comando DELUF

-  

- \- Use o comando DELUF para excluir todos os usuários que estão usando o arquivo especificado. Todas as transações abertas dos usuários excluídos são backed out. Este comando não exclui usuários EXF ou UTI.

- O comando DELUF corresponde ao ADADBS OPERCOM STOPF=file-number,PURGE function.

- Atenção 

- \- Se Adabas está sendo executado com ADARUN OPENRQ=NO (especificando que os usuários não são obrigados a emitir OP como o primeiro comando da sessão), execute o comando DELUF somente se tiver certeza de que os usuários a ser excluído não estão mais ativos. Se um usuário com uma transação aberta é excluído, mas depois retorna (através do envio de um comando), não há nenhuma indicação sobre a devolução da transação. Se o usuário continuar a operação, inconsistências lógicas no banco de dados pode ocorrer.

- Comando DELUI

-  

- \- Use o comando DELUI para excluir todos os usuários que não tenham executado um comando durante o intervalo de tempo especificado (em segundos). Todas as transações abertas dos usuários excluídos são recuou. Este comando não exclui usuários EXF ou UTI. O comando DELUI corresponde ao ADADBS OPERCOM STOPI=time,PURGE function.

- Atenção 

- \- Se Adabas está sendo executado com ADARUN OPENRQ=NO (especificando que os usuários não são obrigados a emitir OP como o primeiro comando da sessão), execute o comando DELUI somente se tiver certeza de que os usuários a ser excluído não estão mais ativos. Se um usuário com uma transação aberta é excluído, mas depois retorna (através do envio de um comando), não há nenhuma indicação sobre a devolução da transação. Se o usuário continuar a operação, inconsistências lógicas no banco de dados pode ocorrer.

- Comando DFILES 

- \- Use o comando DFILES para mostrar o número de usuários a acessando, atualizando, ou controlar ou um arquivo específico (n) ou uma série de arquivos individuais, especificado em uma lista (N1,..., n5). Um máximo de cinco arquivos podem ser especificados na lista. Os usuários são exibidos pelo nome de trabalho e identificação do usuário Adabas atribuído e listado pelo arquivo.

- ```
  STC03611  F AAFAI330,DFILES=21,40,41,42,43                         
  STC08763  +ADAN31 00330 2011-02-09 17:07:19 File= 00021 is not used
  STC08763  +ADAN31 00330 2011-02-09 17:07:19 File= 00040 is not used
  STC08763  +ADAN31 00330 2011-02-09 17:07:19 File= 00041 is not used
  STC08763  +ADAN31 00330 2011-02-09 17:07:19 File= 00042 is not used
  STC08763  +ADAN31 00330 2011-02-09 17:07:19 File= 00043 is not used
  STC08763  +ADAN41 00330 2011-02-09 17:07:19 Function completed
  ```

- Comando DFILUSE 

- \- Use o comando DFILUSE para mostrar o número de comandos total processado até agora para o arquivo especificado durante a sessão atual. A contagem é exibido na mensagem ADAN33 núcleo.

- ```
  STC02760  F AAFAI333,DFILUSE=22
  STC03141  +ADAN33 00333 2015-08-25 16:32:37 File= 22    Usage=0
  STC03141  +ADAN41 00333 2015-08-25 16:32:37 Function completed
  ```

- Comando DHQ

-  

- \- Use o comando DHQ para exibir até cinco elementos a fila de espera.

- ```
  STC02760  F AAFAI333,DHQ
  STC03141  +ADAN07 00333 2015-08-25 16:33:57 Current HQ is empty
  STC03141  +ADAN41 00333 2015-08-25 16:33:57 Function completed
  ```

- Comando DHQA

-  

- \- Use o comando DHQA para exibir até 1.000 elementos fila de espera.

- ```
  STC02760  F AAFAI333,DHQA
  STC03141  +ADAN07 00333 2015-08-25 16:34:25 Current HQ is empty
  STC03141  +ADAN41 00333 2015-08-25 16:34:25 Function completed
  ```

- Comando DLOCKF

-  

- \- Use o comando DLOCKF para dar display dos files locked. 

- ```
  STC02760  F AAFAI333,DLOCKF
  STC03141  +ADAN30 00333 2015-08-25 16:20:17 No files locked
  STC03141  +ADAN41 00333 2015-08-25 16:20:17 Function completed
  ```

- Comandos DNC

-  

- \- Use o comando DNC para mostrar o número de elementos de comando postado fila de espera para ser selecionado. 

- ```
  STC02760  F AAFAI333,DNC
  STC03141  +ADAN13 00333 2015-08-25 16:21:02 Number of posted CQEs = 0
  STC03141  +ADAN41 00333 2015-08-25 16:21:02 Function completed
  ```

- Comando DNFV

-  

- \- Use o comando DNFV para mostrar as variáveis de arquivos do núcleo, ou seja, informações sobre o uso atual do arquivo. Este comando fornece informações sobre os arquivos em uso em um determinado ponto no tempo. Ele também indica que outros núcleos tem o controle de arquivo exclusivo, se, por exemplo, um programa do usuário recebe uma resposta 148, subcode 15. 

- ```
  STC02760  F AAFAI333,DNFV
  STC03141  +FNR=00008  A=Y U=  ID=      CA=00001   CU=00000
  STC03141  +FNR=00009  A=Y U=Y ID=      CA=00001   CU=00000
  STC03141  +FNR=00015  A=Y U=  ID=      CA=00001   CU=00000
  STC03141  +ADAN41 00333 2015-08-25 16:21:52 Function completed
  ```

- DNH

-  

- \- Use o comando DNH para mostrar o número de ISNs atualmente na hold queue (fila de espera).

- ```
  STC02760  F AAFAI333,DNH
  STC03141  +ADAN06 00333 2015-08-25 16:22:32 Number of HQEs = 0
  STC03141  +ADAN41 00333 2015-08-25 16:22:32 Function completed
  ```

- DNU

-  

- \- Use o comando DNU para exibir o número de usuários atuais.

- ```
  STC02760  F AAFAI333,DNU
  STC03141  +ADAN09 00333 2015-08-25 16:23:05 Number of UQEs = 2
  STC03141  +ADAN41 00333 2015-08-25 16:23:05 Function completed
  ```

- DONLSTAT

-  

- \- Use o comando DONLSTAT para exibir o status de cada reorder ativo, invert online, ou Event Replicator processo de estado inicial juntamente com a identificação do processo.

- ```
  STC03611  F AAFAI333,DONLSTAT                                          
  STC01517  +ADAN35 00333 2011-02-09 16:44:29 No online processes present
  STC01517  +ADAN41 00333 2011-02-09 16:44:29 Function completed
  ```

- DPARM

-  

- \- Use o comando DPARM para apresentar os parâmetros da sessão Adabas atualmente em vigor.

- ```
  STC03611  F AAFAI333,DPARM                                                     
  STC01517  +ADAN16 00333 2011-02-09 16:43:07 READONLY=NO,UTIONLY=NO             
  STC01517  +ADAN16 00333 2011-02-09 16:43:07 ASYTVS=YES,AOSLOG=NO               
  STC01517  +ADAN16 00333 2011-02-09 16:43:07 NC=250,NH=3000,NT=20,NU=3000       
  STC01517  +ADAN16 00333 2011-02-09 16:43:07 LBP=61467904,LFP=12288000,LWP=33000
  STC01517  +ADAN16 00333 2011-02-09 16:43:07 LI=300000,LP=25000,LQ=150000,LS=300
  STC01517  +ADAN16 00333 2011-02-09 16:43:07 LFIOP=15360000,FMXIO=1             
  STC01517  +ADAN16 00333 2011-02-09 16:43:07 TT=420,TNAA=900,TNAE=900,CT=300    
  STC01517  +ADAN16 00333 2011-02-09 16:43:07 TNAX=120,MXTT=3600,MXTNA=3600      
  STC01517  +ADAN16 00333 2011-02-09 16:43:07 Logging                            
  STC01517  +                                 LOGCB                              
  STC01517  +ADAN41 00333 2011-02-09 16:43:07 Function completed                 
  ```

- DPPT

-  

- \- Use o comando DPPT para exibir a parallel participant table (tabela participante paralelas) sigla (PPT), ou seja, a exibição do bloco do núcleo do proprio PPT. Este comando produz informações internas para o uso de Software AG suporte técnico.

- ```
  STC02760  F AAFAI333,DPPT
  STC03141  +ADAN24 00333 2015-08-25 16:24:43 Display PPT RABNs 0000281F to 00002
  STC03141  +ADAN24 00333 2015-08-25 16:24:43
  STC03141  +ADAN24 00333 2015-08-25 16:24:43          PPT RABN: 0000281F
  STC03141  +ADAN24 00333 2015-08-25 16:24:43 Number of entries: 01
  STC03141  +ADAN24 00333 2015-08-25 16:24:43 Nucleus indicator: 80
  STC03141  +ADAN24 00333 2015-08-25 16:24:43             NUCID: 0000
  STC03141  +ADAN24 00333 2015-08-25 16:24:43  PPT Entry length: 0022
  STC03141  +ADAN24 00333 2015-08-25 16:24:43          Entry ID: E6
  STC03141  +ADAN24 00333 2015-08-25 16:24:43 Dataset=/ADABAS/DBID333/WORK1/
  STC03141  +ADAN41 00333 2015-08-25 16:24:43 Function completed
  ```

- DRES

-  

- \- Use o comando DRES para mostrar o pool space e o mais alto nível de uso (high water mark) chegou até agora durante a sessão atual, contagem de registros e por cento para os seguintes recursos: 

- ```
   STC08623  F AAFAI333,DRES                                                      
   STC01129  +ADAN28 00333 2018-07-26 08:25:00 Resource       Size       Current  
   STC01129  +ADAN28 00333 2018-07-26 08:25:00 AB  -Pool     3276800         N/A  
   STC01129  +ADAN28 00333 2018-07-26 08:25:00 CQ  -Pool       48000           0  
   STC01129  +ADAN28 00333 2018-07-26 08:25:00 FI  -Pool    12288000           0  
   STC01129  +ADAN28 00333 2018-07-26 08:25:00 HQ  -Pool       84056           0  
   STC01129  +ADAN28 00333 2018-07-26 08:25:00 TBI -Pool      300000           0  
   STC01129  +ADAN28 00333 2018-07-26 08:25:00 TBS -Pool      150000           0  
   STC01129  +ADAN28 00333 2018-07-26 08:25:00 UQ  -Pool      925232         924  
   STC01129  +ADAN28 00333 2018-07-26 08:25:00 UQF -Pool      288360          72  
   STC01129  +ADAN28 00333 2018-07-26 08:25:00 WORK-Pool     3300000         416  
   STC01129  +ADAN41 00333 2018-07-26 08:25:00 Function completed   
  ```

- DSTAT

-  

- \- Use o comando DSTAT para exibir o status atual núcleo Adabas.

- ```
  STC03611  F AAFAI333,DSTAT                                                     
  STC04070  +ADAN17 00333 2011-02-10 13:54:13 Read I/Os A=365,D=2,W=3            
  STC04070  +ADAN17 00333 2011-02-10 13:54:13 Write I/O A=5,D=0,W=2              
  STC04070  +ADAN17 00333 2011-02-10 13:54:13 Nr. of commands=1,Buffer efficiency
  STC04070  +ADAN17 00333 2011-02-10 13:54:13 Nr. of Fmt-Tran.=6,Nr. of Fmt-Ovwr.
  STC04070  +ADAN17 00333 2011-02-10 13:54:13 Thread001=1 commands               
  STC04070  +ADAN41 00333 2011-02-10 13:54:13 Function completed
  ```

- DTH

-  

- \- Use o comando  DTH para dar display do status das threads.

- ```
  STC03611  F AAFAI333,DTH                                      
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=1,ST=AA ,Use=2
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=2,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=3,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=4,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=5,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=6,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=7,ST=UU ,Use=0 
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=8,ST=UU ,Use=0 
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=9,ST=UU ,Use=0 
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=10,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=11,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=12,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=13,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=14,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=15,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=16,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=17,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=18,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=19,ST=UU ,Use=0
  STC04070  +ADAN18 00333 2011-02-10 13:55:03 THN=20,ST=UU ,Use=0
  STC04070  +ADAN41 00333 2011-02-10 13:55:03 Function completed 
  ```

- DUQ

-  

- \- Use o comando DUQ para exibir até cinco elementos da fila ativos e inativos da user queue. 

- ```
  STC02760  F AAFAI333,DUQ
  STC03141  +ADAN11 00333 2015-08-25 16:29:25 User=00000001,JN=COMPLETD
  STC03141  +                       ,TID=DBA1(C1C1F0F1F0F5F5F1)
  STC03141  +                                   TY= U,LA=730 S
  STC03141  +ADAN11 00333 2015-08-25 16:29:25 User=00000004,JN=COMPLETD
  STC03141  +                       ,TID=DBA3(C1C1F0F1F0F5F5F3)
  STC03141  +                                   TY= E,LA=723 S
  STC03141  +ADAN41 00333 2015-08-25 16:29:25 Function completed
  ```

- DUQA

-  

- \- Use o comando DUQA para dar display até 100 elementos da user queue.

- ```
  STC02760  F AAFAI333,DUQA
  STC03141  +ADAN11 00333 2015-08-25 16:29:58 User=00000001,JN=COMPLETD
  STC03141  +                       ,TID=DBA1(C1C1F0F1F0F5F5F1)
  STC03141  +                                   TY= U,LA=763 S
  STC03141  +ADAN11 00333 2015-08-25 16:29:58 User=00000004,JN=COMPLETD
  STC03141  +                       ,TID=DBA3(C1C1F0F1F0F5F5F3)
  STC03141  +                                   TY= E,LA=756 S
  STC03141  +ADAN41 00333 2015-08-25 16:29:58 Function completed
  ```

- DUQE

-  

- \- Use o comando DUQE para mostrar o elemento da user queue para a identificação do usuário especificado Adabas-assigned user ID. O ID do usuário deve ser digitado no formato hexadecimal como segue: -- DUQE=X'A3C1F2' -- Não digite um nome de job no lugar do ID de usuário.

- DUUQE

-  

- \- Use o comando DUUQE para exibir elementos de utilitario da user queue. 

- ```
  STC02760  F AAFAI333,DUUQE
  STC03141  +ADAN11 00333 2015-08-25 16:40:10 Currently no utility UQE
  STC03141  +ADAN41 00333 2015-08-25 16:40:10 Function completed
  ```

- FEOFCL

-  

- \- Use o comando FEOFCL para fechar o registro atual do command log dual ou múltiplo e mudar para o command log para outro log. Esse comando é válido apenas se o comando dual ou múltiplo log está em vigor. Em ambientes de cluster núcleo, a opção global pode ser usado para fechar e mudar de comando duplo ou múltiplo registros em todos os núcleos de cluster ativo.

- FEOFPL

-  

- \- Use o comando FEOFPL para fechar o registro de protection log atual. Este comando é valido para dual ou múltipla de dados para mudar para o registo de uma outra proteção. Em ambientes usando cluster núcleo, a opção global pode ser usado para fechar e mudar a dupla proteção ou múltiplos registros em todos os núcleos de cluster ativo.

- FMXIO

-  

- \- Use o comando FMXIO para mudar dinamicamente a configuração do parâmetro ADARUN FMXIO.

- HALT

-  

- \- Use o comando HALT para realizar uma BT (back out transaction) para a sessão de cada usuário ativo que estiver usando a lógica de ET, em seguida, encerrar a sessão Adabas. Não serão gerados dumps produzidos usando o comando HALT. Em ambientes de cluster núcleo, a opção global pode ser usado para executar um BT para todas as sessões de usuários ativos usando a lógica ET e encerra a sessão Adabas em todos os núcleos de cluster ativo.

- ```
  --- Comando dado
   STC08623  F AAFAI333,HALT                                                      
   STC00647  +ADAN51 00333 2018-07-24 17:25:07 Operator type-in: HALT             
   STC00647  +ADAN42 00333 2018-07-24 17:25:07 Function accepted                  
  
  --- CLOG pedido - Plog este banco não tem
   STC00647  +UEX2   00333 CHAMADA P/ CLOG, FLAGS=X'4800'                         
   JOB07430  $HASP100 AAFAC333 ON INTRDR      DBA                   FROM STC00647 
   STC00647  +UEX2   00333 JOB AAFACLOG   SUBMETIDO                               
   STC00647  +UEX2   00333 RETORNO AO NUCLEO, WAITTIME= 000 S                     
   JOB07430  $SI(K)                                                               
   STC00647  +ADAM97 00333 This ASCB/initiator will be terminated by MVS at EOJ   
             $HASP892 INIT(11)  STATUS=INACTIVE,CLASS=S,NAME=K,ASID=0024          
   JOB07430  $HASP373 AAFAC333 STARTED - INIT K    - CLASS S - SYS CPAC           
   JOB07430  IEF403I AAFAC333 - STARTED - TIME=17.25.08                           
   STC00647  IEF404I AAFAI333 - ENDED - TIME=17.25.08                             
   STC00647  IEF352I ADDRESS SPACE UNAVAILABLE                                    
   STC00647  $HASP395 AAFAI333 ENDED                                              
  
  --- O banco saiu do ar
             IEA989I SLIP TRAP ID=X33E MATCHED.  JOBNAME=*UNAVAIL, ASID=00BC.     
   JOB07430 *CTS001  IEF233A M 089A,PRIVAT,SL,AAFAC333,COPYCLOG,ADABAS.C.DB333.CLO
   JOB07430 *IEF233A M 089A,PRIVAT,SL,AAFAC333,COPYCLOG,                          
   JOB07430          ADABAS.C.DB333.CLOG.G0001V00                                 
   JOB07430  IEC705I TAPE ON 089A,VC1069,SL,COMP,AAFAC333,COPYCLOG,ADABAS.C.DB333.
   JOB07430  IEC205I DDSIAUS1,AAFAC333,COPYCLOG,FILESEQ=1, COMPLETE VOLUME LIST,  
   JOB07430  DSN=ADABAS.C.DB333.CLOG.G0001V00,VOLS=VC1069,TOTALBLOCKS=1           
   JOB07430  CTS014  IEF234E K 089A,VC1069,PVT,AAFAC333,COPYCLOG                  
   JOB07430  IEF234E K 089A,VC1069,PVT,AAFAC333,COPYCLOG                          
   JOB07430  -                                              --TIMINGS (MINS.)--   
   JOB07430  -STEPNAME PROCSTEP    RC   EXCP   CONN    TCB    SRB  CLOCK   SERV  W
   JOB07430  -COPYCLOG             00    346    120    .00    .00     .0   9053  B
   JOB07430  IEF404I AAFAC333 - ENDED - TIME=17.25.13
  ```

- LOCKF

-  

- \- Use o comando LOCKF para bloquear o arquivo especificado. Este comando bloqueia até para utilitarios o acesso.

- ```
  -- Prendendo o arquivo
   STC08623  F AAFAI333,LOCKF=26                                                  
   STC00647  +ADAN41 00333 2018-07-24 17:09:23 Function completed                 
  
  -- Display dos arquivos presos
   STC08623  F AAFAI333,DLOCKF                                                    
   STC00647  +ADAN30 00333 2018-07-24 17:09:34 Files=00026                        
   STC00647  +ADAN41 00333 2018-07-24 17:09:34 Function completed                 
  
  -- Despredendo o arquivo preso
   STC08623  F AAFAI333,UNLOCKF=26                                                
   STC00647  +ADAN41 00333 2018-07-24 17:10:12 Function completed                 
  
  -- Display dos arquivos presos
   STC08623  F AAFAI333,DLOCKF                                                    
   STC00647  +ADAN30 00333 2018-07-24 17:10:20 No files locked                    
   STC00647  +ADAN41 00333 2018-07-24 17:10:20 Function completed 
  ```

- LOCKU

-  

- \- Use o comando LOCKU para bloquear o arquivo especificado para todos os usuários. Utilitários Adabas podem usar o arquivo especificado normalmente.

- ```
  -- Prendendo o arquivo
   STC08623  F AAFAI333,LOCKU=26                                                  
   STC00647  +ADAN41 00333 2018-07-24 17:13:49 Function completed                 
  
  -- Display dos arquivos presos
   STC08623  F AAFAI333,DLOCKF                                                    
   STC00647  +ADAN30 00333 2018-07-24 17:14:04 Files=00026                        
   STC00647  +ADAN41 00333 2018-07-24 17:14:04 Function completed                 
  
  -- Liberando o arquivo preso
   STC08623  F AAFAI333,UNLOCKU=26                                                
   STC00647  +ADAN41 00333 2018-07-24 17:14:12 Function completed                 
  
  -- Display dos arquivos presos
   STC08623  F AAFAI333,DLOCKF                                                    
   STC00647  +ADAN30 00333 2018-07-24 17:14:20 No files locked                    
   STC00647  +ADAN41 00333 2018-07-24 17:14:20 Function completed 
  ```

- LOCKX

-  

- \- Use o comando LOCKX para bloquear o arquivo especificado para todos os usuários, exceto os usuários EXU ou EXF. Usuários EXU e EXF podem usar o arquivo normalmente. O lock é liberada automaticamente quando um usuário emite um comando OP.

- ```
  -- Prendendo o arquivo
   STC08623  F AAFAI333,LOCKX=26                                                  
   STC00647  +ADAN41 00333 2018-07-24 17:13:49 Function completed                 
  
  -- Display dos arquivos presos
   STC08623  F AAFAI333,DLOCKF                                                    
   STC00647  +ADAN30 00333 2018-07-24 17:14:04 Files=00026                        
   STC00647  +ADAN41 00333 2018-07-24 17:14:04 Function completed                 
  
  -- Liberando o arquivo preso
   STC08623  F AAFAI333,UNLOCKX=26                                                
   STC00647  +ADAN41 00333 2018-07-24 17:14:12 Function completed                 
  
  -- Display dos arquivos presos
   STC08623  F AAFAI333,DLOCKF                                                    
   STC00647  +ADAN30 00333 2018-07-24 17:14:20 No files locked                    
   STC00647  +ADAN41 00333 2018-07-24 17:14:20 Function completed 
  ```

- LOGGING

-  

- \- Use o comando LOGGING para iniciar o command logging.

- LOGCB

-  

- \- Use o comando LOGCB para iniciar o log do Adabas control block para cada command logged.

- LOGFB

-  

- \- Use o comando LOGFB para iniciar o log do buffer de formato para cada command logged.

- LOGIB

-  

- \- Use o comando LOGIB para iniciar o log do ISN buffer para cada command logged.

- LOGIO

-  

- \- Use o comando LOGIB para iniciar o log de atividade do Adabas I/O para cada command logged.

- LOGRB

-  

- \- Use o comando LOGRB para iniciar o log de gravação do buffer para cada command logged.

- LOGSB

-  

- \- Use o comando LOGSB para iniciar o log no search buffer para cada command logged.

- LOGUX

-  

- \- Use o comando LOGUX para iniciar o log de dados do user exit B para inclusão no registro de CLOG. Este comando é válido apenas quando CLOGLAYOUT=5.

- LOGVB

-  

- \- Use o LOGVB para iniciar no Adabas o log do value buffer para cada command logged.

- NOLOGGING

-  

- \- Use comando NOLOGGING para parar ou impedir o log de registro.

- NOLOGCB

-  

- \- Use o comando NOLOGCB para parar ou impedir o log do Adabas control block.

- NOLOGFB

-  

- \- Use o comando NOLOGFB para parar ou impedir o log do Adabas format buffer.

- NOLOGIB

-  

- \- Use o comando NOLOGIB para parar ou impedir o log do Adabas ISN buffer.

- NOLOGIO

-  

- \- Use o comando NOLOGIO para parar ou impedir o log do Adabas I/O activity.

- NOLOGRB

-  

- \- Use o comando NOLOGRB para parar ou impedir o log do Adabas record buffer.

- NOLOGSB

-  

- \- Use o comando NLOGSB para parar ou previnir o log do Adabas search buffer.

- NOLOGUX

-  

- \- Use o comando NOLOGUX para parar o log de dados do user exit B inclusão no registro de CLOG. Este comando é válido apenas quando CLOGLAYOUT=5

- NOLOGVB

-  

- \- Use o comando NOLOGVB para parar ou impedir o log do Adabas value buffer.

- ONLRESUME

-  

- \- Use o comando ONLRESUME para retomar um novo pedido anteriormente suspensa processo do, online reorder, invert, or Event Replicator for Adabas initial-state.

- ONLSTOP

-  

- \- Use o comando para parar o ONLSTOP online reorder, invert, or Event Replicator for Adabas initial-state. O processo continua até o seu próximo ponto de interrupção, a fim de produzir um um consistente estado e, em seguida, encerra após realizar toda a limpeza necessária.

- ONLSUSPEND

-  

- \- Use o comando ONLSUSPEND para suspender o online reorder, invert, ou Event Replicator para o Adabas initial-state process. O processo continua até o seu próximo ponto de interrupção, a fim de produzir um consistente estado, realiza uma reminiscência de comando, e entra em um estado onde ele não pode ser selecionado para processamento. Este comando é útil se o processo on-line está consumindo muito dos recursos do núcleo.

- RALOCKF

-  

- \- Use o comando RALOCKF para remover o bloqueio do avanço no arquivo especificado (consulte o comando ALOCKF) sem executar o utilitário.

- RALOCKFA

-  

- \- Use o comando RALOCKFA para remover o bloqueio do avanço em todos os arquivos para os quais foi criado (consulte o comando ALOCKF) sem executar o utilitário.

- RDUMPST

-  

- \- Use o comando RDUMPST para encerrar o online dump status. Este comando é usado normalmente se a execução on-line do utilitário ADASAV foi encerrado de forma anormal.

- READONLY

-  

- \- Use o comando READONLY para mudar o status ON ou OFF. Um valor "YES" ON, o valor "NO" é OFF.

- REVIEW

-  

- \- Use o comando REVIEW para:

- ```
  * desativar o Review do Adabas;
  * Alterar de hub mode para local mode, ou;
  * para especificar ou alterar no Adabas hub Review com o qual nucleo comunica.
  ```

- STOPF

-  

- \- Use o comando STOPF para parar todos os usuários que estão usando o arquivo especificado. Todas as transações abertas dos usuários serão paradas imediatamente. Um usuário que esteja usando este file parado (através do envio de um comando) receberá o código de resposta 9. Este comando não pára usuários EXF ou UTI.

- ```
   STC08623  F AAFAI330,STOPF=498                                                 
   STC08152  +ADAN34 00330 2018-07-26 07:35:03    users stopped                   
   STC08152  +ADAN41 00330 2018-07-26 07:35:03 Function completed                 
  ```

- STOPI

-  

- \- Use o comando STOPI para parar todos os usuários que não tenham executado um comando durante o intervalo de tempo especificado (em segundos). Todas as transações abertas dos usuários serão paradas imediatamente. Um usuário que esteja usando este file que foi parado vai (através do envio de um comando) receberá o código de resposta 9. Este comando não pára usuários EXF ou UTI.

- ```
   STC08623  F AAFAI330,STOPI=900                                                 
   STC02861  +ADAN29 00330 2018-07-24 17:21:40 No users stopped                   
   STC02861  +ADAN41 00330 2018-07-24 17:21:40 Function completed 
  ```

- STOPU

-  

- \- Use o comando STOPU para parar e excluir o usuário com o user ID no Adabas atribuído (na forma mostrada nos comandos display), ou parar e excluir todos os usuários com o job name especificado (job-name). Todas as transações abertas dos usuários pararam será feito fora. 

- Cuidado

- : Se está a definido no Adabas ADARUN OPENRQ=NO (especificando que os usuários não são obrigados a emitir OP como o primeiro comando da sessão), execute o comando STOPU somente se tiver certeza de que os usuários a ser excluído não estão mais ativos. Se um usuário com uma transação aberta é excluído, e depois retorna (através do envio de um comando), não há nenhuma indicação sobre a devolução da transação. Se o usuário continuar a operação, inconsistências lógicas no banco de dados pode ocorrer. Nota - O comando STOPU=X'userid' não é permitida para reordenar os processos on-line ou invertido. Use o ONLSTOP=X'identifier'

- SYNCC

-  

- \- Use o comando SYNCC para forçar a sincronização de todos os usuários ET. O núcleo de espera para todos os usuários ET para alcançar status de ET.

- TCPIP

-  

- \- Use o comando TCPIP para abrir ou fechar uma conexão direta no com link do TCP/IP para o núcleo Adabas ou fechar todas as ligações TCP/IP quando nenhuma URL for especificada. Este comando só é possível quando o parâmetro ADARUN TCPURL é definido como "YES" e todas as condições para essa configuração foram atendidos. Este comando pode ser usado para fechar a URL definida no parâmetro ADARUN TCPURL, ou para abrir ou fechar adicionais ligações TCP/IP. Você deve identificar a universal resource locator (URL) para a ligação de TCP/IP que você deseja abrir ou fechar. A URL é um endereço de 20 bytes em conformidade com a especificação RFC para URLs.

- api-name = é um valor de caráter 3-1 identificar a interface de programação de aplicativo (API) para usar. Ambas as APIs para o IBM TCP/IP (HPS, OES) ea API para a Interlink pilha (ILK) são suportados atualmente.

- stackid = é um valor de caracter para indentificar de 8-1 a pilha para usar:

- \* for the HPS API, this is the name of the TCP/IP started task.

- \* for the OES API, no value is needed.

- \* for the ILK API, this is the subsystem identifier.

- port-number = é um número de caracteres 1-5 em notação decimal.

- Examplos

- TCPIP=OPEN=ILK://ILZ5:1234 TCPIP=CLOSE=ILK://ILZ5:1234

- Para fechar todas as URLs abertas:

- TCPIP=CLOSE

- TNAA

-  

- \- Use o comando TNAA definir o limite de tempo de atividade não-usuários para acesso somente. Este valor deve ser maior que zero e substitui o valor definido pelo parâmetro ADARUN TNAA. Em ambientes de cluster núcleo, o comando TNAA é global, por definição, e afeta todos os núcleos do cluster.

- TNAE

-  

- \- Use o comando TNAE defini o limite de tempo de atividade não-lógica para os usuários ET. Este valor deve ser maior que zero e substitui o valor definido pelo parâmetro ADARUN TNAE. Em ambientes de cluster núcleo, o comando TNAE é global, por definição, e afeta todos os núcleos do cluster.

- TNAX

-  

- \- Use o comando TNAX definir o limite de tempo de atividade não-usuários de control users. Este valor deve ser maior que zero e substitui o valor definido pelo parâmetro ADARUN TNAX. Em ambientes de cluster núcleo, o comando TNAX é global, por definição, e afeta todos os núcleos do cluster.

- TT

-  

- \- Use o comando TT para definir o limite de tempo de transação para os usuários lógica ET. Este valor deve ser maior que zero e substitui o valor definido pelo parâmetro ADARUN TT. Em ambientes de cluster núcleo, o comando TT é global, por definição, e afeta todos os núcleos do cluster.

- UNLOCKF

-  

- \- Use o comando UNLOCKF para desbloquear o arquivo especificado.

- UNLOCKU

-  

- \- Use o comando UNLOCKU para desbloquear o arquivo especificado que anteriormente foi bloqueado para todos os usuários não utilitários.

- UNLOCKX

-  

- \- Use o comando UNLOCKX para desbloquear o arquivo especificado que anteriormente foi bloqueado para usuários de controle não exclusivo.

- UTIONLY

-  

- \- Use o comando UTIONLY para mudar o parâmetro de status ADARUN UTIONLY ON (ligado) ou off (desligado). O default é NO.

- Categories: [Adabas](https://adabasmainframe.blogspot.com/search/label/Adabas)