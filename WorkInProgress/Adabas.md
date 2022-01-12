# Adabas

*Autor: Nelson Naoki Umeda*


O Sistema Gerenciador de Banco de Dados em sua última versão (ADABAS 5.1.6) foi implementado na Celepar em 06/08/90. com significativos ganhos em relação a sua versão anterior (Adabas 4.1.1).

A arquitetura do Adabas foi modificado na versão 5, visando a atender as necessidades atuais de processamento distribuído, conforme veremos mais adiante.

Além disso, as mudanças reduziram o consumo de recursos e melhoraram performance do software, além de torná-lo mais funcional.

NOVAS CARACTERÍSTICAS:

\- processamento de update em multi-thread, que significa a atualização do banco de dados realizada concorrentemente por vários usuários(1), mesmo que esta seja feita file e/ou no mesmo bloco físico.

\- realização de I/O através de suas próprias rotinas, não utilizando os métodos de acesso fornecidos pelo sistema operacional que são consideravelmente mais lentos.

\- redução substancial de I/O no arquivo work em ambiente com transações com muito acesso a disco.

\- a lógica do algoritmo de pesquisa foi melhorada, o que significa dizer que o comando FIND, por exemplo, quando recupera muitos registros, está mais rápidos.

GANHOS ADICIONAIS

Podemos obter ganhos adicionais na performance e throughput(2) através da parametrização adequada do ADABAS. Por exemplo:

\- definições de áreas auxiliares de memória, utilizando as facilidades do MCS/XÁ, para permitir com isto que dados referenciados freqüentemente permaneçam na memória, reduzindo a quantidade de I/O físico.

\- transferência das listas resultantes de uma pesquisa de memória, propiciando grande economia de I//O, pois este processo anteriormente utilizava áreas em disco.

Os programas utilitários do ADABAS, foram modificados para diminuir o tempo de processamento de grandes volumes de dados. Por exemplo, o backup de um DB em um núcleo ADABAS V4 processava em seis horas; na versão 5, o mesmo processamento durou cerca de cinqüenta minutos.

Com o Adabas 5, outra novidade: a utilização de endereços alternativos que apontam para aqueles blocos que necessitaram ser regravados em função de um erro de I/O ter ocorrido na primeira tentativa. Assim, o banco de dados permanece íntegro e o processamento prossegue de forma transparente ao usuário. Na versão anterior, quando ocorria um erro de I/O, não era possível seguir com o processamento e manter a integridade do banco.

Surgiram, igualmente, facilidades para definição de dados:

\- superdescritores, agora, podem ser definidos como unique, ou seja ADABAS é dito para não permitir a duplicação de chaves assim definidas.

\- hiperdescritores, um conceito inovador! Tratam-se de descritores criados a partir de um algoritmo do próprio usuário.

\- a quantidade de campos por file aumentou de 500 para 926.

\- superdescritores passam a ter no máximo 253 bytes.

O processo que o usuário utiliza para se comunicar com o ADABAS chama-se interregion communication (comunicação entre address spaces). O usuário do CICS emite um comando para o ADABAS e aguarda até que este processe e lhe informe em que endereço o CICS pode recuperar a resposta.

No ADABAS 4, a interregion communication é executada através da criação de áreas auxiliares, duplicando assim a necessidade de memória. O ADABAS 5 executa este mesmo processo disponibilizando a informação a informação diretamente na área de trabalho do usuário, Desta forma existe uma dupla economia: redução pela metade da memória. O ADABAS 5 executa esse mesmo processo disponibilizando a informação diretamente na área de trabalho do usuário. Desta forma existe uma dupla economia do processador pela não realização da dupla transferência, isto é, do ADABAS para área auxiliar e posteriormente para a área de trabalho do usuário.

Alterações adicionais foram feitas no ADABAS5, para permitir que ADABAS DE CPU's diferentes se comuniquem, com vistas ao processamento distribuído.

Nasceram, com esta filosofia, alguns conceitos novos:

\- ADANET: gerenciador de banco de dados distribuídos.

\- NETWORK: distribuição de bancos de dados distribuídos.

\- NETWORK VWS: acesso a um ou mais ADABAS ativos em computadores diferentes, tais como o IBM (MVS) conversando com o super-mini dec (VAX) de modo transparente.

Adanet e Network são componentes chaves, junto com o ADABAS 5 para a implementação de um ambiente de banco de dados distribuído.

AMBIENTE CELEPAR:

No ambiente CELEPAR, já trabalhamos com o conceito de banco de dados distribuído, através do software ADABAS VTAM.

Possivelmente em breve, veremos nossas CPU's se comunicam com super-minis. Aguardemos, pois!

(1)No ADABAS 4 havia uma thread de atualização, o que significa dizer que os comandos de atualização, emitidos por vários usuários enfileiravam em uma única porta de entrada. Um comando ficou na comand queue aguardando outro acabar.

(2)Throughput: carga de trabalho efetuada em uma determinada unidade de tempo.