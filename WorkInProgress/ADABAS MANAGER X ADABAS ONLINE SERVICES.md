## [ADABAS MANAGER X ADABAS ONLINE SERVICES](https://adabasmainframe.blogspot.com/2014/08/adabas-manager-x-adabas-online-services.html)

Criado por Claudemar Martins de Sá Postado em segunda-feira, agosto 25, 2014 

O Adabas Manager (AMA) é uma ferramenta de administração de banco de dados baseado em navegador que permite que você execute funções de DBA em bancos de dados de mainframe Adabas. Este tutorial mostra as principais características deste produto.

**Overview**

O Adabas Manager é uma ferramenta de administração de banco de dados baseado em navegador que permite que você execute funções de DBA em bancos de dados de mainframe Adabas. Administradores de banco de dados Adabas pode gerenciar seus bancos de dados diretamente de seus desktops, independentemente da plataforma em que Adabas executado. O Adabas Manager utiliza a interface de administração comum Software AG, que fornece um único ponto de administração para todos os produtos do SAG para dar aos usuários a mesma aparência e sentir-se em todos os produtos do SAG. Este artigo explica alguns dos recursos e funcionalidades do Gestor Adabas Manager.

**Adabas Manager e o Adabas Online services AOS**

[![img](https://2.bp.blogspot.com/-xBFa0y3GUi8/U_JJgd8ThHI/AAAAAAAAKY8/tNE4dp2gZjY/s1600/figure1.gif)](https://2.bp.blogspot.com/-xBFa0y3GUi8/U_JJgd8ThHI/AAAAAAAAKY8/tNE4dp2gZjY/s1600/figure1.gif)
Se você comparar as duas primeiras imagens, você pode ver que o Adabas Manager oferece a mesma funcionalidade básica como a do Adabas Online services (AOS), e na maioria dos casos, você pode usar qualquer ferramenta de administração para executar a mesma tarefa.

Adabas Online services

```
  15:42:07          ***** A D A B A S  BASIC  SERVICES *****       2014-08-18
  DBID 177                 - Display General DB-Layout -              PDRG002


   Database Name ............ DB.D177.PR.TREINAMENTO
   Database Number .......... 230
   Database Version ......... 7.4
   Database Load Date ....... 2012-03-11 10:55:40

   System Files ............. 19 , 20 , 0 , 0 , 0 , 0 , 0 , 0
   Maximum Number of Files .. 2048
   Number of Files Loaded ... 316
   Highest File Loaded ...... 405

   Size of RABN ............. 3 Bytes
   Current Log Tape Number .. 416
   Delta Save Facility ...... Inactive
   Recovery Aid Facility .... Inactive
   Universal Encoding Sup. .. Inactive


  PF1----- PF2------ PF3------ PF4------ PF6----- PF7----- PF8----- PF12-----
  Help               Exit                                           Menu
```

Figure 2 - Typical AOS Start Menu

A primeira coisa a notar é que, AOS não lhe dá uma lista de bancos de dados disponíveis; você tem que saber quais os que estão disponíveis no SVC onde AOS está em execução. Com o Adabas Manager, enquanto você pode ver imediatamente quais bancos de dados estão online (indicado pela caixa de luz do tráfego ao lado da entrada), você ainda tem que definir a conexão. Como fazer isso é explicado no artigo "Configuring Net-work for the Adabas Manager", publicado na edição de junho de técnicas, também disponível na comunidade Adabas e Natural "Know How". O restante deste artigo descreve como algumas das funções AOS são implementadas no Adabas Manager. Uma vez que o Adabas Manager está instalado, as operações são auto-explicativos; No entanto, se você precisa de ajuda, cada tela inclui uma função de ajuda on-line integrada. Note que também que o Adabas Manager usa uma versão atualizada do System Management Hub (SMH). Uma das novidades desta versão é que se você selecionar um item da árvore clicando o botão esquerdo sobre ele, um clique direito exibirá as opções de comando para este item.

**System Management Hub Feature**

Os recursos do System Management Hub Feature no Adabas Manager são demonstrado na tela a seguir: [![img](https://2.bp.blogspot.com/-E0p8AlFCwRo/U_JJgrfXt6I/AAAAAAAAKZA/ckunYpQII9I/s1600/figure3.gif)](https://2.bp.blogspot.com/-E0p8AlFCwRo/U_JJgrfXt6I/AAAAAAAAKZA/ckunYpQII9I/s1600/figure3.gif)

Adabas Online services

```
  15:45:38          ***** A D A B A S  BASIC  SERVICES *****          2014-08-18
  DBID 177                   -  Display User Queue  -                 PACQA32
  SEL-CRIT: MAX-NUM = 100
                                                           Total Users .. 25
  Mark entries with 'D' (Display) or 'S' (Select):
      I          I          I          I User I        I Last     I            I
    M I   TID    I  ET-ID   I Job Name I Type I Status I Activity I File(s)    I
   -----------------------------------------------------------------------------
    _ I CD9864D5 I          I BR230AXF I ET   I ET     I       63 I 15         I
    _ I CD9864D5 I          I BR230ABD I ET   I ET     I       63 I 8,15       I
    _ I      130 I          I BR230ABD I ET   I ET     I       63 I 8,15       I
    _ I      190 I 1001     I BR230ABD I ET   I ET     I      395 I 216        I
    _ I      210 I 1002     I BR230ABD I ET   I ET     I      398 I 216        I
    _ I      230 I 1003     I BR230ABD I ET   I ET     I      398 I 15,216     I
    _ I      250 I 1004     I BR230ABD I ET   I ET     I      398 I 15,216     I
    _ I      270 I 1005     I BR230ABD I ET   I ET     I      395 I 216        I
    _ I      290 I 1006     I BR230ABD I ET   I ET     I      395 I 216        I
    _ I      310 I 1007     I BR230ABD I ET   I ET     I      398 I 216        I
    _ I      330 I 1008     I BR230ABD I ET   I ET     I      398 I 216        I
    _ I      350 I 1009     I BR230ABD I ET   I ET     I      395 I 216        I

  PF1----- PF2------ PF3------ PF4------ PF6----- PF7----- PF8----- PF12-----
  Help               Exit      Refresh            -        +        Menu
```

**Session Monitoring**

A tela de parâmetros ativos mostra os parâmetros ADARUN para o banco de dados selecionado. Você pode modificar os parâmetros deste ecrã, deslocando-se para a parte inferior da página e selecionar "Alterar" e depois em "OK" para salvar as configurações. Tal como acontece com o AOS, apenas os parâmetros que podem ser atualizados em linha aparecerão realmente modificável no ecrã. [![img](https://3.bp.blogspot.com/-qrEmDVpE9hY/U_JJhOPu0uI/AAAAAAAAKZI/F1hvDV839yU/s1600/figure4.gif)](https://3.bp.blogspot.com/-qrEmDVpE9hY/U_JJhOPu0uI/AAAAAAAAKZI/F1hvDV839yU/s1600/figure4.gif)

Adabas Online services

```
  15:47:40          ***** A D A B A S  BASIC  SERVICES *****          2014-08-18
  DBID 177                   -  Display Parameters  -                 PACPD02


   -------------- Pools --------------  ------------- Queues ------------------
   Sort Area         (LS).. 99840       Command Queue          (NC) .. 60
   Int. User Buffer  (LU).. 65535       Hold Queue             (NH) .. 3000
   Buffer Pool      (LBP).. 8026880     User Queue             (NU) .. 200
   Format Pool      (LFP).. 2048000     ------------ Time Windows -------------
   ISN List Table    (LI).. 120000      Transaction Time       (TT) .. 300
   Seq. Cmd. Table   (LQ).. 50000       Max Transaction Time (MXTT) .. 3600
   Work Pool        (LWP).. 800000      Nonactivity ACC-User (TNAA) .. 900
   Attached Buffer  (NAB).. 400         Nonactivity ET-User  (TNAE) .. 900
   Security Pool    (LCP).. 2000        Nonactivity EXU-User (TNAX) .. 120
   UQ-DE Pool    (LDEUQP).. 5000        Max Nonactivity Time(MXTNA) .. 3600
   Flush I/O Pool (LFIOP).. 2000000     Time Limit Sx-Cmds (TLSCMD) .. 3600
   Err. Recovery (MSGBUF).. 0           Max Time for Sx-Cmds(MXTSX) .. 3600
                                        Command Time           (CT) .. 300
                                        SYNS60 Interval    (INTNAS) .. 3600

                                                                     Page 1 of 3
  PF1----- PF2------ PF3------ PF4------ PF6----- PF7----- PF8----- PF12-----
  Help               Exit                                  +        Menu
```

**Checkpoint Maintenance**

Para eliminar Checkpoint, selecione a entrada "Checkpoint" na árvore principal, em seguida, clique direito e selecione "Delete Checkpoints" no menu drop-down; [![img](https://3.bp.blogspot.com/-VSCmZ1HbqZw/U_JJhh_u6MI/AAAAAAAAKZM/z972AiEDm7k/s1600/figure5.gif)](https://3.bp.blogspot.com/-VSCmZ1HbqZw/U_JJhh_u6MI/AAAAAAAAKZM/z972AiEDm7k/s1600/figure5.gif)

Adabas Online services

```
  15:49:14          ***** A D A B A S  BASIC  SERVICES *****       2014-08-18
  DBID 170                      - List Checkpoints -                  PCPC002

    CP   CP     Date      Time      PLOG     Block      Vol/Ser   User Job Name
   Name Type                       Number    Number      Number   Type
   ---- ---- ---------- --------   ------  ----------   --------  ---- --------
   SYNS  60  2014-08-18 00:05:47                                       ADABAS
   SYNS  60  2014-08-18 01:10:58                                       ADABAS
   SYNS  60  2014-08-18 02:15:47                                       ADABAS
   SYNS  60  2014-08-18 03:21:45                                       ADABAS
   SYNS  60  2014-08-18 04:25:46                                       ADABAS
   SYNS  60  2014-08-18 05:31:45                                       ADABAS
   SYNS  60  2014-08-18 06:35:48                                       ADABAS
   SYNS  60  2014-08-18 07:40:21                                       ADABAS
   SYNS  60  2014-08-18 08:43:16                                       ADABAS
   SYNS  60  2014-08-18 09:46:13                                       ADABAS
   SYNS  60  2014-08-18 10:49:09                                       ADABAS
   SYNS  58  2014-08-18 11:12:40                                  ET   CICSB
   SYNS  57  2014-08-18 11:12:40                                  ET   CICSB
   SYNS  60  2014-08-18 11:52:16                                       ADABAS
   SYNS  60  2014-08-18 12:55:17                                       ADABAS
  PF1----- PF2------ PF3------ PF4------ PF6----- PF7 ----- PF8----- PF12-----
  Help               Exit                Top      -        +        Menu
```

**File Maintenance**

[![img](https://4.bp.blogspot.com/-B2KJ_h4g0Zc/U_JJiFLq8NI/AAAAAAAAKZY/goEYlhu034M/s1600/figure6.gif)](https://4.bp.blogspot.com/-B2KJ_h4g0Zc/U_JJiFLq8NI/AAAAAAAAKZY/goEYlhu034M/s1600/figure6.gif)

Adabas Online services

```
  15:50:11          ***** A D A B A S  BASIC  SERVICES *****       2014-08-18
  DBID 177                       - Display Files -                    PDRF002

 Fnr  File Name        Loaded     Top-ISN    Max-ISN    Ext. Pad %  Ind.   %Used
                                                        NUAD  A  D ACISEXU  A  D
 ---- ---------------- ---------- ---------- ---------- ---- -- -- ------- -----
    1 AAF-EMPLOYEES    1997-05-05       1297       4133 1111 10 10 NNNSNNN 22 13
    3 AAF-TNM-DATA     2000-01-15        117      11023 1111 10 10 NNISNNN  5  5
    4 AAF-PARM-NETPASS 1996-06-18       4196       5511 1111 10 10 NNNSNNN 44 27
    5 AAF-VEHICLES     1997-05-05        501       4133 1111 10 10 NNNSNNN  8  2
    6 AAF-FISICO-006   1999-03-10        323       6889 1111 10 10 NNISNNN  5  0
    7 AAF-FISICO-007   2003-08-31       1352       5511 1111 10 10 NNISNNN 16  4
    8 AAF-FISICO-008   2003-08-31     100216     121263 1111 10 10 NNISNNU 15 83
    9 AAF-FISICO-009   1993-05-02      17653      26181 1111 10 10 NNISNNN 16 27
   10 AAF-FISICO-010   1994-04-15    1005096    1225041 1122 10 10 NNISNNN 78 80
   11 AAF-FISICO-011   1996-04-19     888678    1001805 1111 10 10 NNISNNN 26 88
   12 AAF-FISICO-012   1993-03-01       4322       5511 1111 10 10 NNISNNN 10 33
   13 AAF-FISICO-013   1996-12-18          1      11023 1111 10 10 NNNSNNN  1  0
   15 AAF-FISICO-015   1999-07-06   13930553   14656407 1111 10 10 NNNSNNN 19 91
   16 AAF-FISICO-016   1990-09-17        603       2755 1111 10 10 NNISNNN  8  3

  PF1----- PF2------ PF3------ PF4------ PF6----- PF7----- PF8----- PF12-----
  Help     Repos     Exit                --       -        +        Menu
```

**Database Maintenance**

[![img](https://1.bp.blogspot.com/-rYmWde_iqVs/U_JJilN5s9I/AAAAAAAAKZc/rNpza22KEVM/s1600/figure7.gif)](https://1.bp.blogspot.com/-rYmWde_iqVs/U_JJilN5s9I/AAAAAAAAKZc/rNpza22KEVM/s1600/figure7.gif)

Adabas Online services

```
  15:53:56          ***** A D A B A S  BASIC  SERVICES *****       2014-08-18
  DBID 177                  - Display Unused Storage -                PDRU012

         I Device I     Total Number of      I Extent           in Blk.   I
         I Type   I   Blocks     /  Cyls.    I from        -      until   I
   ------I--------I------------------------- I----------------------------I
   DATA  I  8391  I         200           2  I      299703 -      299902  I
         I  8391  I         478           6  I      300327 -      300804  I
         I  8391  I      503587        6714  I      548809 -     1052395  I
   ------I--------I------------------------- I----------------------------I
   ASSO  I  8391  I         330           1  I      140454 -      140783  I
         I  8391  I          11           0  I      140852 -      140862  I
         I  8391  I      769077        4272  I      310912 -     1079988  I

  PF1----- PF2------ PF3------ PF4------ PF6----- PF7----- PF8----- PF12-----
  Help               Exit                                           Menu
```

**System Status**

[![img](https://3.bp.blogspot.com/-c-HJALBaGBY/U_JJjlIlUMI/AAAAAAAAKZg/L9sPBZW3BeM/s1600/figure8.gif)](https://3.bp.blogspot.com/-c-HJALBaGBY/U_JJjlIlUMI/AAAAAAAAKZg/L9sPBZW3BeM/s1600/figure8.gif)

Adabas Online services

```
  15:55:32          ***** A D A B A S  BASIC  SERVICES *****          2014-08-18
  DBID 177                      -  System Status  -                   PACUS02

                     Physical
               Reads          Writes                Call Distribution
             --------------------------  ---------------------------------------
   ASSO           19391            5154  Remote Logical .............          0
   DATA           41613            2160  Remote Physical ............          0
   WORK              43            3284  Local  Logical .............     278786
   PLOG                               0  Local  Physical ............          0

   Logical Reads:                        No. of HQEs active .........          0
     ...                      1,612,670  No. of UQEs in User Queue ..         25
   Buffer Efficiency ....          26,4  No. of CQEs waiting in CQ ..          0
   Format Translations ..          9840  Total intern. Autorestarts .          0
   Format Overwrites ....             0  No. of PLOG switches .......          0
                                         No. of Bufferflushes .......         84
   Throw Backs for ISN ..             0  No. of CLOGs ...............          2
   Throw Backs for Space.             0  No. of PLOGs ...............          0
                                                             page 1 of 2

  PF1----- PF2------ PF3------ PF4------ PF6----- PF7----- PF8----- PF12-----
  Help               Exit      Refresh                       +      Menu
```

[![img](https://3.bp.blogspot.com/-Dz1erSLDZrQ/WKXatY6ZOoI/AAAAAAAAf9o/9UbivFzccQIES5lrVqD5vniI8P9hMD0HwCPcBGAYYCw/s200/Adabas.jpg)](https://3.bp.blogspot.com/-Dz1erSLDZrQ/WKXatY6ZOoI/AAAAAAAAf9o/9UbivFzccQIES5lrVqD5vniI8P9hMD0HwCPcBGAYYCw/s1600/Adabas.jpg)