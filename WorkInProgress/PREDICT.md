## [PREDICT](https://adabasmainframe.blogspot.com/2011/03/predict.html)

Criado por Claudemar Martins de Sá Postado em quinta-feira, março 24, 2011 [1 comentarios](https://adabasmainframe.blogspot.com/2011/03/predict.html#comment-form)

O Predict é um dicionário de dados integrado e ativo, que documenta e suporta o desenho técnico, a implantação e manutenção de bancos de dados e aplicações. Este software permite aos administradores de bancos de dados e desenvolvedores de aplicações gerenciar a informação sobre dados, programas e o uso de dados por programas. Este produto é tido como básico para os processos de rightsizing de sistemas de informações, uma vez que as funções de desenvolvimento de aplicações podem ser distribuídas em uma rede, funcionando o PREDICT como ponto central da coordenação desta atividade.

Informações e funções gerais sobre Predict

[![img](https://4.bp.blogspot.com/-M3EQJj4ltTY/TYvt4YKVeXI/AAAAAAAAF3o/oKFzs58IDMg/s400/2oved.png)](https://4.bp.blogspot.com/-M3EQJj4ltTY/TYvt4YKVeXI/AAAAAAAAF3o/oKFzs58IDMg/s1600/2oved.png)

Este diagrama fornece uma visão geral das funções disponíveis no Predict.

Algumas funções, por exemplo, recuperação, apenas o processo dicionário de dados. Outras funções, como por exemplo Administração, processo de dicionário de dados e objetos em um ambiente externo.

**DDEs**

Os objetos que são gerenciados pelo Predict são referidos como data definition entities (dados de entidades definição) ou DDEs. Esta terminologia permite uma referência específica às definições contidas no Predict versus o item físico que está sendo descrito. Uma grande quantidade de informação podem ser mantida dentro do Predict para cada tipo de entidade. Algumas das entidades comuns previstos são:

- File - Este é o objeto de preocupação para qualquer dicionário de dados, uma vez que representa uma coleção de base de dados relacionados. Predict pode ser usado para descrever muitos tipos diferentes de arquivos: VSAM, seqüencial conceitual, DB2 e Adabas curso. Os arquivos são discutidos em mais detalhes em "Arquivos e DDMs.
- Element - Predict define os campos de um arquivo como elementos de dados ou elementos elementares. Todos os elementos devem ser associados (definido em) um arquivo Predict. Cada elemento nome deve ser exclusivo para esse arquivo.
- Data Base - Um banco de dados pode ser uma entidade física, como uma base de dados Adabas, ou pode ser um agrupamento conceitual de arquivos relacionados. Os arquivos são relacionadas às bases de dados. Nossos arquivos Adabas estão associados com o nosso teste de base de dados Adabas no sistema de teste.
- Keyword - Uma Keyword (Palavra chave) devem ser pré-definidos, mas podem estar associadas a qualquer outra entidade Predict e são úteis para classificar e recuperar essas entidades.
- Verification Rule - As regras de verificação (Verification Rule) são as definições de validações específicas que devem ser realizados antes da aceitação dos dados de entrada. Eles podem ser conceituais ou explicitamente vinculados a determinados elementos de dados. No Natural são referidas como regras de processamento, mais especificamente como as regras de livre ou de regras automáticas quando eles estão armazenados no Predict.

Há muitas entidades Predict que não são tão cruciais para o nosso uso do Natural. Estes incluem aplicações, programas, módulos, usuários, entre outros.

**Arquivos e DDMs**

O Predict é um software para definir elementos em um nível conceitual ou projeto, antes de tomar decisões sobre a representação física dos dados. Conceptual arquivos são o único tipo que deve ser manipulado por pessoas fora da área do Administrador dicionário. Todos os arquivos devem ter um nome de arquivo exclusivo no Predict.

O acesso pelo Natural ao Adabas e arquivos VSAM através de uma interface chamada de Data Definition Module (Definição de Dados Módulo) ou DDM. A DDM fornece uma visão lógica e descrição de um arquivo para o programa Natural e programador. Algumas das vantagens deste interface são:







O uso de nomes de arquivo de 32 caracteres versus o DBID Adabas e número do arquivo.

Use de 32 nomes de elementos de caráter descritivo versus os dois nomes Adabas personagem.

Representação de campos numéricos em termos de número de dígitos atual versus o número de bytes de armazenamento interno ocupado.



DDMs são gerados por Predict a partir de definições de arquivo, ou arquivos física ou opiniões de usuários. A DDM é o que é conhecido e utilizado pelos naturais em utilidades, as definições de segurança e em tempo de compilação do programa. Por outro lado, grande parte da nossa análise e documentação é feita usando as entidades arquivo Predict. Devido à etapa de geração DDM, é possível a fase de implementação de alterações no arquivo, primeiro fazendo e revendo essas alterações como eles aparecem na prévia Predict a regeneração da DDM.

**Menus do SYSDIC**

Os menus do Predict estão estruturados por função, entidade, em seguida, a ação. As principais funções são de Manutenção, Recuperação e Geração. Os submenus para essas funções identifica as entidades que podem ser mantidos, recuperados ou gerados. funções de manutenção, onde são adicionar, alterar e ações de eliminação são realizadas. Geração é o lugar onde as cartas de controlo e ADACMP DDMs mencionados anteriormente são gerados a partir de definições de arquivo. As funções são para recuperação de investigação e notificação de definições Predict. Alguma familiaridade com a operação desta aplicação será benéfico para qualquer uso futuro.

**Telas do Predict no Mainframe**

[![img](https://1.bp.blogspot.com/-7zNh_OK-6z4/TYvwuRsWbiI/AAAAAAAAF3w/EA1JvVxW-Jw/s200/predict.png)](https://1.bp.blogspot.com/-7zNh_OK-6z4/TYvwuRsWbiI/AAAAAAAAF3w/EA1JvVxW-Jw/s1600/predict.png) [![img](https://4.bp.blogspot.com/-nQDjW4i3s5g/TYvzeMliC8I/AAAAAAAAF4Q/rHtZPV9I3vk/s200/predict4.png)](https://4.bp.blogspot.com/-nQDjW4i3s5g/TYvzeMliC8I/AAAAAAAAF4Q/rHtZPV9I3vk/s1600/predict4.png)[![img](https://1.bp.blogspot.com/-tlw9Xlv30RA/TYvwuqBRu4I/AAAAAAAAF34/0qyTpBlClHQ/s200/predict2.png)](https://1.bp.blogspot.com/-tlw9Xlv30RA/TYvwuqBRu4I/AAAAAAAAF34/0qyTpBlClHQ/s1600/predict2.png) [![img](https://2.bp.blogspot.com/-v4rIAoNyOZ8/TYvwu8StjSI/AAAAAAAAF4A/lZsP-148Bss/s200/predict3.png)](https://2.bp.blogspot.com/-v4rIAoNyOZ8/TYvwu8StjSI/AAAAAAAAF4A/lZsP-148Bss/s1600/predict3.png)

**Active Cross-reference**

Outra parte do Predict que está intimamente ligada com natural é o Active Cross-reference. Este mecanismo mantém automaticamente referenciada cruzada para identificar o uso que os objetos natural de dados e vice-versa. Estas informações são capturadas quando os objetos são compilados ou catalogado (termo Natural). O Predict oferece facilidades para permitir a análise destes dados de referência cruzada entre os aplicativos. O Natural também fornece os comandos para analisar os dados de referência cruzada em um único aplicativo.

Categories: [Predict](https://adabasmainframe.blogspot.com/search/label/Predict)