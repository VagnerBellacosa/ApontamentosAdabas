## [ARQUITETURA ADABAS](https://adabasmainframe.blogspot.com/2011/02/arquitetura-adabas.html)

Criado por Claudemar Martins de Sá Postado em segunda-feira, fevereiro 14, 2011 [Sem Comentarios](https://adabasmainframe.blogspot.com/2011/02/arquitetura-adabas.html#comment-form)

Um resumo sobre a arquitetura do Adabas;

- **Módulo de Multiprogramação (MPM):** a pedra fundamental do Núcleo Adabas, contém a lógica que permite que vários programas, tanto em batch quanto online, acessem os bancos de dados Adabas simultaneamente.
- **ASSO:** onde é gravado os relacionamentos e informações de FILE (FDT) assim como listas de files, LISTAS INVERTIDAS!
- **DATA:** Dados dos FILES, que podem ser tanto de utilização do ADABAS como SYSFILE, FUSER e FDIC quanto os FILES dos usuários.
- **WORK:** Area de trabalho do ADABAS, que é formado pela Protection Area, Temporay Intermediate results e Results of inquiries.
- **PLOG:** Log das modificações efetuadas no banco (por registro) e pode ser utilizado em casos de danos físicos
- **CLOG:** Log dos comandos das atividades dos usuários.

[![img](https://4.bp.blogspot.com/-7DaOKKp0aKI/TVmbuIwEPEI/AAAAAAAAFww/gHMj6Nsatvw/s200/ada1.png)](https://4.bp.blogspot.com/-7DaOKKp0aKI/TVmbuIwEPEI/AAAAAAAAFww/gHMj6Nsatvw/s1600/ada1.png)



Categories: [Adabas](https://adabasmainframe.blogspot.com/search/label/Adabas)