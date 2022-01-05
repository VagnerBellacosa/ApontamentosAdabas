## [ADABAS SECURITY](https://adabasmainframe.blogspot.com/2011/02/adabas-utility-execution.html)

Criado por Claudemar Martins de Sá Postado em domingo, fevereiro 13, 2011 [Sem Comentarios](https://adabasmainframe.blogspot.com/2011/02/adabas-utility-execution.html#comment-form)

Adabas oferece as seguintes facilidades para impedir o acesso não autorizado e/ou atualização de arquivos de banco de dados Adabas:



- Criptografia de dados Adabas (ciphering), que fornece segurança de dados;

- Arquivos Adabas multiclient para controlar o acesso aos registros em um arquivo;

- Adabas Security e os relacionados com a segurança de utilidade ADASCR, Adabas um add-on do utilitário que fornece ao usuário acesso seletivo/atualização da proteção de um arquivo de campo, e o nível de valor de campo, e;

- Adabas SAF Security (AAF or ADASAF), é um produto complementar, que prevê o controle dos recursos de um banco de dados Adabas / utilidade, comando ou arquivo de nível de segurança padrão através de pacotes com base no Sistema de Autorização Facility (SAF), como RACF, Secret CA-ACF2 e CA-Top. ADASAF está inicialmente disponível para z / OS sistemas operacionais apenas. Este produto integra Adabas em um repositório central de segurança e permite-lhe tirar o máximo proveito de seu investimento nesse repositório.


**Data Encryption**

Data Encryption é parte integrante do Adabas e não requer opções ou módulos extras. Os dados podem ser cifrados antes de serem colocados no banco de dados.

O usuário deve fornecer a chave de codificação no momento registros são armazenados. Essa chave não está armazenada e deve estar disponível para solicitar ou decifrar os dados. Isso minimiza as chances de dados a ser comprometida por acesso não autorizado ao sistema.

Para manter o máximo controle sobre os cipher codes, Adabas um programa de saída do usuário podem ser criadas para inserir o código cifrado atualmente válida para aplicações do usuário, o que elimina a necessidade de tornar os códigos conhecidos pelos usuários, e protege o arquivo de corrupção que pode ocorrer pela adição de dados que é criptografado com o código de cifra errada.

**Multiclient Files**

Também disponível como um recurso integrante do Adabas, que não exige opções ou módulos especiais é o arquivo multiclient.

Um arquivo único Adabas definido fisicamente como multiclient pode armazenar registros de vários usuários ou grupos de usuários. O recurso multiclient divide o arquivo físico em múltiplos arquivos lógicos, anexando uma identificação do proprietário interna para cada registro.

A identificação do proprietário é atribuído a um ID de usuário. A identificação do usuário pode ter apenas uma identificação de proprietário, mas uma identificação do proprietário pode pertencer a mais de um usuário. Cada usuário só pode acessar o subconjunto de registros que está associado com o ID do usuário proprietário.

Nota: Para qualquer pacote de segurança instalado externos, tais como RACF ou CA-Top Secret, o usuário ainda é identificado por qualquer Natural ETID ou identificação de logon.

Todos os pedidos de banco de dados para arquivos multiclient são tratadas pelo núcleo Adabas.

**Adabas Security and ADASCR**

Controle de Access/update está disponível apenas com o Adabas Security e da ADASCR utilitários relacionados a segurança que define e controla as funções de segurança Adabas.

Adabas Security oferece dois níveis de proteção: access/update e valor.

**Access/Update Level Protection
**

A proteção de nível de Access/update aplica um nível básico de segurança em uma base arquivo por arquivo. Acesso de proteção de atualizar / pode ser definida por alguns arquivos e não para outros. Ele restringe o uso de um arquivo ou campo dentro do arquivo para aqueles que têm um acesso adequado / atualização de definição de perfil e uma senha especificada pelo usuário do arquivo.

Permissão de Access/update os valores variando de 0 a 14 são definidos para cada usuário e anexado a senha do usuário, e cada um arquivo protegido (e campo selecionado ou campos, se desejar) tem acesso equivalente / atualização dos similares de proteção da mesma gama. Somente um usuário cuja valor da permissão for igual ou maior do que o nível de proteção do arquivo especificado (e, quando o campo, caso) está autorizada a realizar esse tipo de operação (acesso ou atualização) no arquivo ou campo. Um acesso / nível de permissão de atualização de 0 só permite o acesso / atualização de arquivos desprotegidos ou campos com nível de proteção 0 ou nenhuma proteção de senha definida.

**Valor Nível de Proteção**

O valor do nível de proteção aplica-se a restrições quanto ao tipo e faixa de valores que pode ser acessado ou atualizado em domínios específicos. As restrições são aplicadas de acordo com a senha do usuário (arquivos com campos usando a proteção ao nível de valor deve ser protegida por senha), pode ser para valores específicos ou intervalos de valores, e pode ser de aceitar ou rejeitar critérios.

**Adabas Interface de pacotes baseados em SAF**

O System Authorization Facility (SAF) é usado por z/OS e sites compatíveis para fornecer um controle rigoroso dos recursos disponíveis a um usuário ou grupo de usuários. Compatível com pacotes de segurança, tais como IBM RACF e 'Computer Associates' (CA) ACF2 ou Top Secret permitindo que o administrador do sistema para manter as credenciais do usuário de identificação, como identificação de usuário e senha, e estabelecer perfis de determinar os data sets, os volumes de armazenamento, transações e relatórios disponíveis para um usuário.

Geralmente, um pacote de segurança permite que o administrador do sistema para autorizar o acesso do usuário aos recursos do sistema. O pacote de segurança, em seguida, monitora todos os usuários e sua utilização de recursos para garantir que nenhum acesso não autorizado ou alteração. As tentativas por usuários não autorizados para usar o sistema ou recursos específicos do sistema são registrados e relatados.

Um perfil de usuário, que pode ser para um único usuário ou um grupo de usuários, define qual o sistema de recursos de hardware e software que um usuário tem permissão para usar. Um perfil de recursos define o acesso / atualização privilégios para um ou mais dispositivos, volumes e / ou programas (recursos que devem ser usados em conjunto para executar determinadas funções pode ser definido em conjunto no mesmo perfil).

Quando um usuário entra no sistema, o pacote de segurança usa a identificação de logon do usuário para identificar o perfil do usuário. Cada vez que o usuário tenta executar uma tarefa ou o acesso a informação, o pacote de segurança usa as informações nos perfis de seus recursos para permitir ou negar o acesso. Usando o conceito de perfil, o pacote de segurança expande o ponto único de autorização de início de sessão o ID para fornecer um amplo controle sobre todos os recursos do sistema.

A segurança resultante do repositório ea infra-estrutura para administrá-lo representam um investimento significativo. Ao mesmo tempo, o volume de informação crítica realizada por uma empresa está em constante crescimento, como é o número de usuários de referência dos dados. O desafio de controlar esses acessos cada vez mais exige uma solução que seja flexível, fácil de implementar e, acima de tudo, um que protege o investimento da empresa.

**Adabas SAF Security (ADASAF)**

Adabas SAF Security (ADASAF) aumenta o escopo dos pacotes de segurança SAF-base, integrando recursos Adabas para o repositório central de segurança. ADASAF permite:

\- um controle interno e auditoria do sistema para todos os recursos;
\- proteção padrão da indústria de dados Adabas e maximizado o retorno do investimento na segurança do repositório.

As oprações do ADASAF podem ser adaptadas em uma base do núcleo por núcleo, permitindo grande flexibilidade na sua aplicação. É composto por:

\- um servidor que operam em cada espaço de endereço protegido Adabas;
\- extensões roteador ligado à SVC Adabas;
\- uma administração em linha e sistema de monitoramento, um aplicativo escrito em Natural e acessados de qualquer demonstração ou versão completa do Adabas Online System (AOS), e um plug-in PINSAF rotina que faz a interface com a instalação de tratamento de erros Adabas. Ele é ativado automaticamente na inicialização para auxiliar o diagnóstico do problema.

ADASAF permite que você proteja os seguintes recursos Adabas:



| RESOURCE                        | PROTECTION                                                   |
| :------------------------------ | :----------------------------------------------------------- |
| Database Nucleus                | Controla os usuários autorizados a iniciar um núcleo Adabas. |
| Adabas Utilities                | Controla os usuários autorizados a executar serviços públicos de utilidade ou ID do banco de dados, por exemplo, um usuário ou grupo pode ter permissão para executar ADAREP mas não ADASAV contra um banco de dados. |
| Database Files                  | Controla os usuários autorizados a acessar os arquivos de banco de dados. |
| Database Commands               | Controla os usuários autorizados a utilizar acesso (READ/FIND) e atualização (STORE / UPDATE / DELETE) comandos. Para otimizar o desempenho, ADASAF ignora comandos como RC que não são de arquivo específico. |
| Production Environment Data     | Controla os usuários autorizados a operar em um ambiente de produção ou de teste. verificação do nível transversal, que poderia ser usado, por exemplo, para evitar danos por um programa aplicativo inadvertidamente catalogados, com o ID do banco de dados errado. |
| Transaction Data                | Controla os usuários autorizados a armazenar ou recuperar dados de ET. |
| Adabas Operator Commands        | Controla os comandos do operador Adabas, que pode ser emitido a partir do console do sistema. |
| File Passwords and Cipher Codes | Dinamicamente aplica senhas e códigos de segurança realizada no repositório ou fornecido por uma saída do usuário. Isso elimina a necessidade de uma aplicação para gerenciar dados de segurança e remove a necessidade de transmitir informações sigilosas do cliente para o banco de dados. |
| Adabas Basic Services           | Protege Adabas Basic Services em um nível selecionado (funções principais única ou a principal funções e subfunções) com perfis de recursos definidos e controla o acesso do usuário a esses perfis. |

Na figura a seguir, todo o tráfego entre os usuários do banco de dados Adabas e é controlado pelo roteador Adabas. Com ADASAF instalado, o roteador ADASAF substitui o roteador Adabas e controla todo o acesso ao Adabas:


[![img](https://2.bp.blogspot.com/-QHqTzQKYNZY/TXZ0cJ6RHuI/AAAAAAAAF24/P8RK7IqnBy4/s200/adasaf.png)](https://2.bp.blogspot.com/-QHqTzQKYNZY/TXZ0cJ6RHuI/AAAAAAAAF24/P8RK7IqnBy4/s1600/adasaf.png)

A identificação de logon central de segurança é usado para fazer logon no sistema. Através do sistema operacional ou monitor de TP, o pacote de segurança instalado do lado externo verifica a autorização do ID de logon. Para fazer chamadas a partir de uma estação de trabalho remota ou plataforma não-IBM, um processo de logon remoto é utilizado para dar a identificação de logon para ADASAF. O roteador contém uma saída de segurança que extrai o ID de logon do usuário a partir da ACEE para o usuário.

flexível, controle total é mantida com um usuário uma: uma abordagem de definição, enquanto os investimentos anteriores em segurança baseada em sistemas de acolhimento e infra-estruturas são reforçadas, não descartada.

**Adabas Online System Security
**
A versão demo do Adabas Online System (AOS) distribuído com Adabas inclui um mecanismo de segurança para restringir o acesso às instalações Adabas online. AOS Segurança requer Natural de Segurança como um pré-requisito. Veja o Adabas documentação de segurança para obter mais informações.

**Natural Security
**
O Natural Security system fornece segurança abrangente para usuários Adabas/Natural. Ele é necessário para AOS Segurança e recomendados para outros recursos do Adabas. Veja a documentação Natural de Segurança para obter mais informações.

**Using the SAF Repository to Secure Software AG Products
**
[Adabas SAF Security or ADASAF](http://documentation.softwareag.com/adabas/ada814mfr/adamf/concepts/cfsecurity.htm#cfsecurity_SAFpkgs) é um dos vários produtos de segurança Software AG que melhoram a eficácia da central de segurança SAF repositório:





| PRODUCT                        | PROTECTS                                |
| :----------------------------- | :-------------------------------------- |
| Adabas SAF Security            | Adabas                                  |
| Adabas SQL Server SAF Security | Adabas SQL Server (ESQ)                 |
| Entire Net-Work SAF Security   | Entire Net-Work version 5.6 and above   |
| EntireX Security               | EntireX, Entire Broker, Broker Services |
| Natural SAF Security           | Natural                                 |



### Entire Security SAF Gateway

Toda a segurança SAF Gateway pode ser instalado sob o z/OS. Ele pode ser usado para garantir a seguir ao utilizar um sistema de segurança compatível com SAF:

\- Adabas (versão 6.2 e anteriores) para mainframes
\- Adabas operacional do SQL Server em ambientes z / OS
\- Natural RPC usando Entire Broker
\- Natural de mainframes
\- Toda a operação Broker (pré-EntireX) em ambientes z / OS, UNIX e Windows (a segurança construído em webMethods EntireX agora protege EntireX Broker e do Agente de Serviços também).

**Facilidade de API do Windows e aplicações UNIX**

SAF Gateway protege cliente/servidor, peer-to-peer, e sistemas de aplicação padrão. O software é executado em pontos específicos onde a comunicação entre clientes, servidores e colegas é protegido usando as definições feitas no sistema de segurança baseado em SAF.

SAF Gateway compreende pelo menos dois componentes separados, em qualquer aplicação:

O componente principal, conhecido como o Portal SAF tarefa iniciada, opera em seu próprio z/OS como espaço de endereço de um gateway para os sistemas de segurança baseados em SAF. Como um nó na rede Software AG, concentra-se o processamento SAF-Based para os produtos que estão sendo protegidos. A task iniciada pode operar em conjunto com um banco de dados Adabas existentes.

O segundo componente depende do que está sendo protegido e representa os vários cenários diferentes distribuídos e mainframe listados acima. Pode ser localizado no software aplicativo em si, por exemplo, mainframe Natural. Aplicações distribuídas são protegidos por autenticação de clientes / servidores e garantir a comunicação entre diferentes componentes.

A instalação da API para aplicações Windows e UNIX já está sendo usado para proteger

\- Servidores Web que operam sob o Windows NT e UNIX
\- aplicações do Visual Basic no Windows
\- aplicações PowerBuilder em Windows
\- aplicativos Delphi no Windows
\- C e C + + no Windows e UNIX

**Entire Net-Work SAF Security (NETSAF)
**

O Entire Net-Work SAF Security (NETSAF) é um produto separado, opcional para z/OS rodando ambientes Entire Net-Work version 5.6 ou acima. Ele permite que os clientes Entire Net-Work para acessar fontes de dados da SAF-Security (targets), por exemplo, Adabas, EntireX Communicator, e Entire System Service.

NETSAF pode ser ativado em uma base de link-by-link. Se apenas um nó de várias comunica externamente, a segurança pode ser ativado para que o nó só e apenas para ligações externas.

Para assegurar Entire Net-Work, é necessário definir os perfis de recursos na SAF repositório. perfis de recursos são definidos para cada host de destino. Adabas perfis de recursos pode ser definida no nível de arquivo. O tipo de comando determina o nível de acesso necessário para autorização de sucesso: os níveis de acesso são válidas leitura, atualização e controle. CONTROLE aplica-se aos comandos de AOS, por exemplo.

Ponto de acesso a verificação de pedidos de entrada é feita contra a segurança SAF-based repositório central: todo o acesso de clientes de mainframe podem ser verificados contra o mesmo perfil de segurança.

Os controlos de segurança são baseadas em uma identificação de usuário confiável, que devem existir no repositório central de segurança. Em alguns casos, a identificação do usuário é autenticado no ambiente do chamador casa ou é fixo, por exemplo, a configuração de rede inteiro. A identificação do usuário podem ser perdidas se as chamadas são encaminhadas através de um nó gateway intermediário.




Original - [Clique Aqui](http://documentation.softwareag.com/adabas/ada814mfr/adamf/concepts/cfsecurity.htm#cfsecurity)

Categories: [Adabas](https://adabasmainframe.blogspot.com/search/label/Adabas)