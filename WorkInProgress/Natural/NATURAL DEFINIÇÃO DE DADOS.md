## [NATURAL DEFINIÇÃO DE DADOS](https://adabasmainframe.blogspot.com/2011/02/natural-definicao-de-dados.html)

Criado por Claudemar Martins de Sá Postado em segunda-feira, fevereiro 14, 2011 [Sem Comentarios](https://adabasmainframe.blogspot.com/2011/02/natural-definicao-de-dados.html#comment-form)

**Acessar arquivos em programas ADABAS NATURAL**

Para fazer referência a um arquivo ADABAS e seus campos de dados em um programas natural, você deve criar uma definição de dados do Módulo NATURAL (DDM) com base no arquivo ADABAS. (Note que uma DDM é muitas vezes referida como um arquivo ADABAS, mesmo que ele é realmente apenas uma visão de um arquivo ADABAS reais.) A DDM tem um nome atribuído, que faz referência o número do arquivo ADABAS em que a DDM está baseada. Além disso, nomes de campo mais descritivos de dados pode ser atribuído a uma DDM. DDMs são armazenados em um arquivo de sistema, que é simplesmente um outro arquivo ADABAS.


**DDM Filename**

O nome do arquivo para uma DDM natural pode ser um máximo de 32 caracteres.

**Nomes de campo de dados**

Em uma DDM NATURAL, campos de dados podem ser atribuído um nome DDM externa de 3 a 32 caracteres. Por exemplo, na DDM CLIENTES, a DDM de dados CLIENTE nome de domínio corresponde ao arquivo Adabas de dois caracteres field name CU.

**Descritores ADABAS**

Se você planeja usar um campo de dados muitas vezes em critérios de seleção, pode designá-lo como um campo de chave. Você designa um campo de chave, especificando a opção descritor na instrução de definição ADACMP utilitário de dados. Quando um campo de dados é um campo de descritores, ADABAS mantém e armazena os valores em uma lista invertida. Uma lista invertida contém os valores diferentes de um campo de descritor de dados, juntamente com a contagem eo ISNs dos registros lógicos que contêm cada valor. Descritores Adabas também pode ser definido de modo a que as listas invertidas conter apenas valores únicos.

Especificando descritores ADABAS acelera o processo de seleção consideravelmente desde ADABAS é capaz de acessar valores-chave diretamente. Além disso, especifica os descritores controla ler sequência quando a leitura de dados ADABAS em sequência.

Vários tipos de descritores podem ser especificados para um campo de dados. Cada tipo de descritor é explicado abaixo.

**Subdescritor**

A subdescritor é um descritor ADABAS que é derivado de uma parte de um campo de dados elementar. Por exemplo, se o CEP é um campo de dados, um para subdescritor poderia ser ZIPLAST2 definidos para os dois últimos dígitos de um CEP.

**Superdescriptor**

A superdescriptor é um descritor ADABAS derivados de mais de um campo de dados, porções de campos de dados, ou combinações dos mesmos. Por exemplo, um superdescriptor denominado Estado-ZIPLAST2 poderia ser definido para os dois primeiros dígitos do campo de dados do Estado e os dois últimos dígitos do campo de dados CEP.

**Descritor Phonetic**

Um descritor fonético é um descritor ADABAS definido para executar pesquisas baseadas em valores fonéticos, por exemplo, a recuperação pelo nome de família.

Categories: [Natural](https://adabasmainframe.blogspot.com/search/label/Natural)