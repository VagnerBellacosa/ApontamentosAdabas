# Adabas, Natural & Cia - continuação

Autores: Dante Carlos Antunes, Claudio Lopes Furquim, Paulo Antonio Fuck de Oliveira e Rogério Ribeiro da Fonseca Mendes  

Desde o início da década de 80, a CELEPAR tem utilizado o sistema gerenciador de banco de dados ADABAS e a linguagem NATURAL para desenvolver os sistemas de informação para os seus clientes. Hoje em dia, já existe uma cultura consolidada na empresa a respeito destes softwares.

Neste artigo, contaremos um pouco da história destes produtos e também falaremos da Software AG que é a fabricante do ADABAS, NATURAL e outros produtos correlatos, largamente utilizados no Brasil, onde são representados pela CONSIST, empresa sediada em São Paulo, com filiais em várias capitais do nosso país. Por último, faremos uma rápida abordagem sobre a experiência que estamos fazendo em nosso laboratório UNIX/NOVELL sobre a utilização da família ADABAS em múltiplas plataformas.

A FAMÍLIA DE PRODUTOS DA SOFTWARE AG

A Software AG tem sua matriz na cidade Darmstadt na Alemanha e filial em Reston, Virgínia nos EUA, sendo considerada uma das maiores empresas de software, notadamente de produtos voltados ao mercado de gerenciadores de bancos de dados, engenharia de aplicação e soluções para computação distribuída. Durante muitos anos, seus produtos foram voltados fundamentalmente a ambientes de grande porte, baseados em mainframes, porém, com a introdução da filosofia "ENTIRE FUNCTION SERVER - EFS", vem desenvolvendo esforços para o desenvolvimento de soluções para as mais diversas plataformas.

Dentro do conceito da EFS, os produtos ofertados ao mercado tomam por base fatores como a interoperabilidade (suportando uma grande gama de plataformas e protocolos, inclusive SQL, com facilidade de integração com uma infinidade de aplicações e serviços existentes), a portabilidade (as interfaces das aplicações programadas - API's, permitem acessos a dados, comunicação programa a programa. Esta portabilidade é conseguida utilizando-se da combinação dos API's com a linguagem de quarta geração NATURAL) e variados portes de plataforma (pode ser implantado em plataformas que variam do mainframe a um notebook).


São ainda características da EFS, a flexibilidade das soluções, ganhos de performance além da possibilidade de futuras expansões, tudo isto voltado ao funcionamento dentro da tecnologia de cliente/servidor.

O mundo Software AG é composto por vários países. No Brasil, seus maiores clientes são empresas que operam com grandes instalações, sendo que nos últimos meses foi registrado um aumento nos negócios envolvendo aplicações e software básico para ambientes de menor porte.

FAMÍLIA SOFTWARE AG E O UNIX

A história da Software AG com o UNIX iniciou-se em 1987, quando passou a examinar a melhor alternativa para lançar seus produtos dentro do conceito de sistemas abertos, notadamente para rodar em plataformas UNIX. Como primeira estratégia definida, os produtos ADABAS, NATURAL e NETWORK, escritos em linguagem Assembler, seriam reeditados em linguagem ANSI C. A segunda estratégia foi a adoção de um padrão de sistema operacional baseado em X/Open interfaces e de uma parceria comercial bem suportada. Após negociações foi firmado contrato com a HP (HP 9000 systems - HP/UX UNIX - número um em vendas UNIX da época), além de serem estabelecidos contatos com a IBM à medida que um número expressivo de potenciais clientes para esta solução valiam-se então da tecnologia IBM SNA (Iniciava-se a discussão do downsizing e da tecnologia cliente/servidor).

A estratégia de desenvolvimento foi baseada na criação de uma versão MASTER (HP/UX), que serviria de base para as futuras conversões para outras plataformas. A Software AG, em contraposição às soluções e aplicações então vigentes, exclusivas para cada tipo de hardware, buscou a portabilidade de aplicações através de uma camada de software, o que permitiria que independentemente da tecnologia em uso seus produtos pudessem ser utilizados.

Em setembro de 1991, após um longo período de testes, foram liberados os primeiros produtos para esta plataforma, obtendo-se uma boa aceitação junto aos mercados dos Estados Unidos, França e Espanha. No início de 1992, foram liberados para testes, releases para mais seis plataformas. Durante o período de avaliação, foram realizadas avaliações que demonstraram a possibilidade de utilização dos códigos gerados para aplicações em OS/2 e Windows.

Em fevereiro de 1992, foram liberadas para o Brasil as versões do Gerenciador de Banco de Dados ADABAS, da linguagem NATURAL e do Software NETWORK, para máquinas RISC. Inicialmente, estas versões poderiam ser utilizadas em plataformas HP 9000 série 800, valendo-se do Sistema Operacional HP-UX. Naquela época, anunciou-se que encontravam-se em fase de testes as versões para os ambientes RS 6000 da IBM, SUNsparc da SUN e RISC/ULTRIX da Digital.

Com estes lançamentos, o marketing da Software AG buscava difundir sua tecnologia de EFS, baseada no modelo cliente/servidor, quando através de um sistema de comunicação podia-se executar aplicações em uma plataforma UNIX, comunicando-se com um servidor de banco de dados instalado em um mainframe IBM, de forma transparente para o usuário.

O software ADABAS UNIX é um banco de dados flexível, orientado a modelos relacionais, voltado a operações que envolvam um grande número de transações e enormes conjuntos de dados. Nesta versão, foi reescrito dentro de uma concepção MULTI-THREADING, utilitários ON-LINE, RESTART/RECOVERY automáticos, assegurando a funcionalidade e performance verificados em outros ambientes.

O NATURAL UNIX veio como uma alternativa de ambiente de desenvolvimento, que permitiria liberar recursos dos mainframes. Como principal característica do produto, merece registro sua total portabilidade, de tal maneira que qualquer aplicação escrita em NATURAL, possa ser executada em várias plataformas, requisito para o processo de distribuição do processamento.

Em março de 1993, foram liberadas para o ambiente UNIX as versões do NATURAL CONSTRUCT e do PREDICT. O primeiro é um software gerador de aplicações baseado em modelos, que permite ganhos de produtividade no desenvolvimento de sistemas, facilitando a prototipação dos mesmos. Seu funcionamento estabelece padrões de aplicações que definem a estrutura e as principais funções de diferentes partes da aplicação (tais como entradas de dados, menus e browse). Com uma biblioteca de modelos, o NATURAL CONSTRUCT permite ganhos imediatos de produtividade e qualidade, à medida que os programas podem partir destes modelos pré-testados. Uma vez gerado o código, este rodará em qualquer ambiente servido pela família ADABAS/NATURAL.

O PREDICT é um dicionário de dados integrado e ativo, que documenta e suporta o desenho técnico, a implantação e manutenção de bancos de dados e aplicações. Este software permite aos administradores de bancos de dados e desenvolvedores de aplicações gerenciar a informação sobre dados, programas e o uso de dados por programas. Este produto é tido como básico para os processos de rightsizing de sistemas de informações, uma vez que as funções de desenvolvimento de aplicações podem ser distribuídas em uma rede, funcionando o PREDICT como ponto central da coordenação desta atividade.

Outro produto, também lançado em março passado, foi o ADABAS SQL Server, que após testado e aprovado pelo National Institute of Standart and Technology dos Estados Unidos, foi disponibilizado para plataformas que utilizem o Sistema Operacional MVS da IBM e para as diversas plataformas UNIX já servidas pela Software AG.

Hoje os produtos da Software AG estão disponíveis para as plataformas IBM/AIX, HP-UX, NCR, SCO, SunOS e Unisys.

FAMÍLIA ADABAS INSTALADA NO LABORATÓRIO UNIX DA CELEPAR

A CONSIST, representante dos produtos da família ADABAS no Brasil, cedeu para a CELEPAR, sem custos, uma licença de uso do sistema gerenciador de banco de dados ADABAS e uma do compilador para linguagem NATURAL.

Além disto, outros softwares foram instalados a título de demonstração, entre eles o NETWORK que permite o acesso transparente a banco de dados remoto em plataformas diversas.

É a seguinte a lista de softwares instalados no laboratório UNIX e nos outros ambientes a ele conectados:

|                      |           | Situação software                     |
| -------------------- | --------- | ------------------------------------- |
| Ambiente Unix        |           |                                       |
| Adabas AIX           | Instalado | Celepar tem cópia livre p/ 8 usuários |
| Natural AIX          | Instalado | Celepar tem cópia livre p/ 8 usuários |
| Network AIX          | Instalado | Em demonstração                       |
| Estação. DOS/WINDOWS |           |                                       |
| Adabas (monousuário) | Instalado | Em demonstração                       |
| Natural 2.1.0        | Instalado | Em demonstração                       |
| Network              | Instalado | Em demonstração                       |
| Estação OS/2         |           |                                       |
| OS/2 2.0 (OS)        | Instalado | Comprado 5 cópias                     |
| Adabas (mono)        | Instalado | Celepar tem 5 cópias livres           |
| Natural 1.1.4.1      | Instalado | Celepar tem 5 cópias livres           |
| Adabas DB Server     | Instalado | Em demonstração                       |
| Network              | Instalado | Em demonstração                       |
| Novell OS2 Request   | Instalado | Comprado 2 cópias                     |
| BM Comunic Manager   | Instalado | Em demonstração                       |

A ser instalado:

. Placa SDLC ou Upgrade do Netware for SAA para comunicação via LU6.2 com Mainframes.

. Netware Lan WorkPlace for OS/2 para para comunicação via TCP/IP com Unix.

| Ambiente Central - Mainframes |               |                       |
| ----------------------------- | ------------- | --------------------- |
| Adabas 5.1.9                  | Em instalação | Comprado pela Celepar |
| Natural                       | Instalado     | Comprado pela Celepar |
| Network 5.2                   | Em instalação | Comprado pela Celepar |