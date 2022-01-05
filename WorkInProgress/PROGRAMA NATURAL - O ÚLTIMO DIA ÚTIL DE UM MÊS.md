## [PROGRAMA NATURAL - O ÚLTIMO DIA ÚTIL DE UM MÊS](https://adabasmainframe.blogspot.com/2014/08/programa-natural-o-ultimo-dia-util-de.html)

Criado por Claudemar Martins de Sá Postado em segunda-feira, agosto 18, 2014 [Sem Comentarios](https://adabasmainframe.blogspot.com/2014/08/programa-natural-o-ultimo-dia-util-de.html#comment-form)

O texto abaixo não é de minha autoria. É um texto que li e achei tão brilhante criado pelo Steve Robinson - [Clique Aqui](https://techcommunity.softwareag.com/pwiki/-/wiki/Main/How+to+Produce+the+Last+Business+Day+of+a+Given+Month)

Em meu trabalho atual, o meu cliente precisava de um código que, a partir de uma determinada data produziria o último dia útil desse mês. A lógica sugere para o código que iria ser muito pesado para ser executado. Teríamos tabelas envolvidas de dias em cada mês, um file a ser criado com dias úteis válidos, e assim por diante. Uma vez que este código iria ser muito utilizada, a eficiência foi uma consideração importante. I/O para acessar os arquivos é caro. Outra solução teria de ser encontrada. Acontece que o problema é realmente muito simples. Vou abordar o problema em etapas, a seguir, com cada estágio nos aproximar da solução desejada.

O inicio do programa

Vamos começar com uma data A8, que será passado por um CALLNAT. Aqui está o programa de partida:

```
* THIS PROGRAM HAS A DATE IN #DATE.
* WE WILL PRESUME THE DATE HAS BEEN VALIDATED
*
* WE REQUIRE THE LAST BUSINESS DAY OF THE MONTH
*
DEFINE DATA LOCAL
1 #DATE (A8) INIT <’20100214’>
1 #LAST-BIZ-DAY (A8)
1 #DAY-WEEK (A10)
1 #DATE-D (D)
END-DEFINE
*
INCLUDE AATITLER
*
CALLNAT ‘DATEB02’ #DATE #LAST-BIZ-DAY
*
MOVE EDITED #LAST-BIZ-DAY TO #DATE-D (EM=YYYYMMDD)
MOVE EDITED #DATE-D (EM=NNNNNNNNNN) TO #DAY-WEEK
*
WRITE 5T ‘FOR THE GIVEN DATE: ‘ #DATE (EM=XXXX-XX-XX)
//
        5T ‘THE LAST (BUSINESS?) DAY OF THE MONTH IS: ‘
            #LAST-BIZ-DAY (EM=XXXX-XX-XX) /
        5T ‘WHICH IS A ‘ #DAY-WEEK
*
END
```

Algumas notas sobre o programa acima:

\- AATITLER é apenas um copycode eu uso para substituir o nome padrão (que é apenas uma declaração TÍTULO WRITE). - A máscara de edição nnnnnnnnnnn produz o dia da semana, como texto. É dependentes do idioma. Em nossa primeira tentativa, não vai produzir o último dia útil do mês, apenas o último dia do mês.

O Subprograma



```
* THIS SUBPROGRAM WILL FIND THE LAST (BUSINESS?)
* DAY OF THE MONTH FOR A SPECIFIED DATE
*
DEFINE DATA PARAMETER
1 #DATE (A8)
1 #LAST-BIZ-DAY (A8)
LOCAL
1 #DATE-W (A8)
1 REDEFINE #DATE-W
    2 #YEAR (N4)
    2 #MONTH (N2)
    2 #DAY (N2)
1 #DATE-D (D)
END-DEFINE
*
* FIRST, WE CREATE THE FIRST DAY OF THE
* FOLLOWING MONTH
*
MOVE #DATE TO #DATE-W
MOVE 1 TO #DAY
ADD 1 TO #MONTH
IF #MONTH = 13
    MOVE 1 TO #MONTH
    ADD 1 TO #YEAR
    END-IF
*
* NOW WE CREATE THE DATE FORMAT OF OUR FIRST DAY
*
MOVE EDITED #DATE-W TO #DATE-D (EM=YYYYMMDD)
*
* NOW WE SUBTRACT ONE TO CREATE THE LAST DAY
* OF OUR GIVEN MONTH
*
SUBTRACT 1 FROM #DATE-D
*
MOVE EDITED #DATE-D (EM=YYYYMMDD) TO #LAST-BIZ-DAY
END
```

Uma nota interessante: Ao discutir um pedaço similar de código, um estudante uma vez perguntou por que eu MOVE'd nossa data de entrada para outra variável. Note que # DATA-W é alterado um pouco. Você não deve destruir os dados de entrada de um chamador não ser que seja absolutamente acordado que tal deveria acontecer. O mesmo aluno sugeriu que eu poderia ter colocado a "resposta" no #date originais, reduzindo assim o número de parâmetros para um. Mais uma vez, apenas se for absolutamente concordaram que o usuário ainda não vai precisar a data original, bem como a data do último dia útil.

Próximos passos

A lógica do programa é bastante simples. Nós adicionamos 1 ao mês, e definir o dia para 1 Sim, você tem que verificar se o mês é agora 13 Se assim for, você tem que definir o mês a 1 e adicionar 1 ao ano. Tome a data resultante (# DATA-W) e converta para o formato Data via MOVE EDITED. Você tem agora um dia depois da data que você quer (talvez). Para ser mais preciso, você tem um dia após o último dia do mês em questão. Então, subtraia um do formato da data. Nós não estamos completamente finalizado. Aqui está o resultado do nosso programa original, que passou a data de 14 de fevereiro, Dia dos Namorados de 2010 (meu aniversário, caso alguém queira enviar um presente no próximo ano). Na verdade, como você vai ver, fevereiro foi escolhido por uma razão muito específica.

```
PAGE # 1                 DATE: 08/08/10
PROGRAM: DATEB01         LIBRARY: DATES

FOR THE GIVEN DATE: 2010-02-14

THE LAST (BUSINESS?) DAY OF THE MONTH IS: 2010-02-28
WHICH IS A Sunday
```

Nota: O último dia de fevereiro, o dia 28, foi em um domingo. Lembre-se que a nossa exigência era produzir o último dia útil do mês. É evidente que não é ficou ok ainda.

Identificando os dias da semana, com data de edição da máscara

Se a data é for um sábado, subtraia 1 do formato da data. Se um domingo, subtraia dois. Assim, você vai ter convertido uma data do sábado ou domingo para uma de sexta-feira. Como você sabe o dia da semana? Há uma edição na mascara de Data maravilhosa que atende a essa necessidade. Ele é mostrada no código abaixo que testa para o sábado e domingo. Esta é inserida após a declaração SUBTRACT no código subprograma mostrado acima.

```
* NOW WE WILL TAKE CARE OF WEEKENDS
*
MOVE EDITED #DATE-D (EM=O) TO #DAY-OF-WEEK
IF #DAY-OF-WEEK = ‘1’
    SUBTRACT 2 FROM #DATE-D
    END-IF
IF #DAY-OF-WEEK = ‘7’
    SUBTRACT 1 FROM #DATE-D
    END-IF
*
```

Edite uma máscara para produzir um campo de caracteres alfa um que contém um número de um a sete. ATENÇÃO! A atribuição dos números é controlado pelo parâmetro DTFORM. Se você está familiarizado com DTFORM você sabe que é principalmente utilizado para controlar o formato de variáveis de data de exibição padrão. A definição de DTFORM é para Europe, G - Germany, I - International, and U - USA. DTFORM também controla as designações de edição para uma máscara O. Se DTFORM está definido para U (EUA), então o domingo será atribuído um sábado e será atribuído um sete. Qualquer outra definição de DTFORM resultará na segunda-feira que está sendo atribuído a um e domingo sendo atribuído a sete. Como você pode ver acima, eu assumi um cenário DTFORM de U, portanto, o domingo é um e o sábado é sete. Nós não vamos checar por semana, uma vez que não é necessário ajuste para eles (pelo menos, não ainda). Após fazer as alterações acima, aqui é o nosso nova saida:

```
PAGE # 1             DATE: 08/08/10
PROGRAM: DATEB01     LIBRARY: DATES

FOR THE GIVEN DATE: 2010-02-14

THE LAST (BUSINESS?) DAY OF THE MONTH IS: 2010-02-26
WHICH IS A Friday
```

Endereçando datas de feriados não-fixos

Agora para um pouco de diversão: Suponha que a nossa data de entrada é 05 de maio de 2010. Aqui está a nossa saída, usando o nosso subprograma atual:

```
PAGE # 1             DATE: 08/08/10
PROGRAM: DATEB01     LIBRARY: DATES

FOR THE GIVEN DATE: 2010-05-05

THE LAST (BUSINESS?) DAY OF THE MONTH IS: 2010-05-31
WHICH IS A Monday
```

Problema! Nos Estados Unidos, 31 de maio de 2010 foi um feriado na empresa (Memorial Day). Lá fui eu para a internet, um calendário do meu lado. À primeira vista, parecia que o Memorial Day, sempre cai última segunda-feira em maio, foi o único conflito em potencial e só um conflito se ele cai no dia 31 de maio. Isso foi muito fácil para testar usando o seguinte código, que eu inserido após os testes de fim de semana.

```
* NOW WE TEST FOR MEMORIAL DAY BEING THE 31’ST
*
IF #MONTH = 6 AND #DAY-OF-WEEK = ‘2’
    SUBTRACT 3 FROM #DATE-D
    END-IF
```

Há algo um pouco estranho no teste acima. Estou testando por ser 6; mas, Memorial Day é em maio. Lembre-se que eu aumentei o mês por um, quando eu criei o primeiro dia do próximo mês; portanto, seis, cinco não no teste. A saída do novo subprograma é mostrado no parágrafo seguinte.

```
PAGE # 1             DATE: 08/08/10
PROGRAM: DATEB01     LIBRARY: DATES

FOR THE GIVEN DATE: 2010-05-05

THE LAST (BUSINESS?) DAY OF THE MONTH IS: 2010-05-28
WHICH IS A Friday
```

Nota: Mesmo que o último dia de maio foi um dia de negócios, que apoiou-nos com sucesso até a sexta-feira dia 28 de maio.

Mais uma data de problema - O alvo em movimento

Na empresa do cliente, a sexta-feira santa é considerada um feriado na empresa. Esta é mais difícil para testar, como a sexta-feira santa não é um feriado "previsível" que cai no mesmo dia a cada ano. Não existe uma regra simples assim para o Memorial Day dos EUA, que cai na última segunda-feira de maio. A "regra" de Sexta-feira santa é que ele cai na sexta-feira antes do feriado de Páscoa - que também não é uma data fixa. Isto pode variar de 22 março - 25 abril. Claramente sexta-feira santa não pode criar um problema em relação a último dia útil de abril. Março é o problema em potencial. Mais uma vez, um calendário e da Internet revelou-se útil. Se a sexta-feira Santa caísse em 31 de março, claramente nós queremos que a nossa "resposta" a ser 30 de março. Suponha que a sexta-feira santa caísse em 30 de março? O último dia de março seria sábado dia 31 de março Nosso código de fim de semana apoiaria a 31 até um dia para o trigésimo, que teria, então, para fazer o backup para o 29. Mais uma possibilidade para se preocupar: suponha que Sexta-feira Santa caísse em 29 de março o último dia de março seria 31 de março (o que seria o Domingo de Páscoa). Nosso código de fim de semana apoiaria a 31 até dois dias para o 29. Nosso código teria que apoiar isso mais um dia para o 28. Para a Internet ... Há seis anos, entre os anos de 2000 e 2050, onde Sexta-feira Santa cai entre março 29-31 (2002, 2013, 2018, 2024, 2029, 2040). Em cada caso, o nosso sub-programa atual será terá dia de folga. Então, eu escrevi o seguinte código e inseri-lo depois que o código US Memorial Day:

```
* NOW WE TEST FOR GOOD FRIDAY
*
IF #MONTH = 4 AND #YEAR = #FIX-YEARS (*) /* YES, =4,NOT 3;
                                         /* SEE ABOVE
DISCUSSION
    SUBTRACT 1 FROM #DATE-D
    END-IF
```

é definido como N4/1:6 e dado valores CONST como indicado no parágrafo acima. Aqui está o resultado de uma determinada data de 20 de marco de 2018 para.

```
PAGE # 1             DATE: 08/08/10
PROGRAM: DATEB01     LIBRARY: DATES

FOR THE GIVEN DATE: 2018-03-20

THE LAST BUSINESS DAY OF THE MONTH IS: 2018-03-29
WHICH IS A Thursday
```

Como você pode ver acima, o nosso código funcionou (é sempre bom quando isso acontece!)

Adaptando o código para outros calendários/países

Se você tiver feriados em dias de negócios ou outras datas que podem criar um problema (como Memorial Day nos Estados Unidos, ou Sexta-feira Santa) nunca é particularmente difícil de escrever código para testá-las. Normalmente, uma simples IF com uma matriz de anos será suficiente como mostrado no código acima. Na verdade, você pode substituir o "composto" IF acima com uma variedade de combinações mês-ano, que criam um problema. Não se esqueça de alterar as provas de fim de semana, se você tem DTFORM programado para o U.

Uma variação sobre o tema - uma data significativa que se repete mensalmente

Eu já vi uma variação sobre o tema apresentado neste artigo em várias lojas. O problema é simples. Há uma data significativa em cada mês ... vamos pegar o 15, por exemplo. Para um determinado mês (que é uma determinada combinação ano e mês), é necessário para encontrar o último dia útil até e incluindo o décimo quinto. Para esclarecer: suponha que o 15 não é um feriado, é uma terça-feira. Em seguida, o 15 seria a data pretendida. No entanto, suponha que o 15 foi um sábado. Em seguida, o décimo quarto seria a data necessária, a menos, o décimo quarto era um feriado, caso em que a data exigida seria o décimo terceiro. Vamos supor que nunca há dois dias em uma fila que são feriados. Se só contamos feriados do governo federal nos Estados Unidos, isso é verdade. Os dois únicos feriados norte-americanos que têm um possível conflito com o 15 de um mês são os dias Dia do Presidente (terceira segunda-feira de fevereiro) e aniversário de Martin Luther King Jr. (terceira segunda-feira de janeiro). Como no exemplo acima para Sexta-Feira Santa, uma simples instrução IF contra uma série de anos em que o 15 é uma segunda-feira é suficiente para testar as condições que exigem uma mudança (neste caso, a sexta-feira anterior). Também é fácil, como mostrado abaixo, para testar o 15 de ser uma segunda-feira em janeiro ou fevereiro. Aqui é um subprograma que realiza um teste para o último dia útil antes do décimo quinto dia do mês.

```
* LAST DAY OF THE MONTH PRIOR TO THE FIFTEENTH
*
DEFINE DATA PARAMETER
1 #DATE (A8)
1 #LAST-BIZ-DAY (A8)
LOCAL
1 #DATE-W (A8)
1 REDEFINE #DATE-W
    2 #YEAR (N4)
    2 #MONTH (N2)
    2 #DAY (N2)
1 #DATE-D (D)
1 #DAY-OF-WEEK (A1)* THIS SUBPROGRAM WILL FIND THE
LAST BUSINESS
END-DEFINE
*
* FIRST, WE CREATE THE FIFTEENTH DAY OF THE
* SPECIFIED MONTH
*
MOVE #DATE TO #DATE-W
MOVE 15 TO #DAY
*
* NOW WE CREATE THE DATE FORMAT OF THE FIFTEENTH
*
MOVE EDITED #DATE-W TO #DATE-D (EM=YYYYMMDD)
*
* NOW WE WILL TAKE CARE OF WEEKENDS
*
MOVE EDITED #DATE-D (EM=O) TO #DAY-OF-WEEK
IF  #DAY-OF-WEEK = ‘1’
    SUBTRACT 2 FROM #DATE-D
    END-IF
IF #DAY-OF-WEEK = ‘7’
    SUBTRACT 1 FROM #DATE-D
    END-IF
*
* NOW WE TEST FOR PRESIDENTS DAY BEING THE 15’TH
*
IF #MONTH = 2 AND #DAY-OF-WEEK = ‘2’
    SUBTRACT 3 FROM #DATE-D
    END-IF
*
* NOW WE TEST FOR MARTIN LUTHOR KING DAY
*
IF #MONTH = 1 AND #DAY-OF-WEEK = ‘2’
    SUBTRACT 3 FROM #DATE-D
    END-IF
*
MOVE EDITED #DATE-D (EM=YYYYMMDD) TO #LAST-BIZ-DAY
END
```

E aqui está um pouco de saída a partir de fevereiro deste ano:

```
PAGE # 1             DATE: 08/21/10
PROGRAM: DATEB04     LIBRARY: DATES

FOR THE GIVEN DATE: 2010-02-20

THE LAST BUSINESS DAY OF THE MONTH
(PRIOR TO THE 15’TH) IS: 2010-02-12
WHICH IS A Friday
```

Nota: Nós corretamente "Salvamos" para sexta-feira anterior.

Um par de notas importantes em resumo

O formato da data é muito útil para encontrar os primeiros/últimos dias de um determinado mês (ou no próximo mês ou no mês anterior). Há uma série de máscaras de edição muito úteis para as datas. Dê uma olhada na documentação Natural para uma lista completa. Nos programas acima fizemos uso do EM=O (para obter o dia da semana para uma determinada data, ter cuidado em relação DTFORM) e NNNNN ... para obter o texto para o dia da semana.

[![img](https://4.bp.blogspot.com/-W_VAm4YGBvU/WKYO6U-IsEI/AAAAAAAAf-g/haM8HoWhCKs2_BqS46EeunbpNKA0xHfOwCPcBGAYYCw/s200/natural.jpg)](https://4.bp.blogspot.com/-W_VAm4YGBvU/WKYO6U-IsEI/AAAAAAAAf-g/haM8HoWhCKs2_BqS46EeunbpNKA0xHfOwCPcBGAYYCw/s1600/natural.jpg)

Categories: [Natural](https://adabasmainframe.blogspot.com/search/label/Natural)