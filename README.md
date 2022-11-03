## SharedTable
No caso do programa de sharedTable, é visto que a condição de Race Condition é colocado em prática, já que ao se rodar a função main, a quantidade de elementos adicionados à tabela de caracteres não corresponde ao que o código se propõe. Isso se deve a utilização de Threads para a inserção de forma paralela, ocasionando uma espécie de gargalo no momento da inserção

O fator que causa o erro na execução se deve que na função addMark na classe SharedTable. No momento de execução, os três runners estão tentando acessar essa função de forma igual, ocasionando um erro tanto na inserção quanto no seu indexamento no array.

```java
public void addMark(char c) {
    table[index] = c;
    spendSomeTime();
    index++;
  }
```
No momento em que a Thread que está atribuida em Runner é iniciada, o processo de acesso a Thread acaba por executar a função de adicionar o caracter especifico de forma concorrente. Devido a função addMark não estar sendo utilizada de forma sincronizada, mesmo que seja percorrido as 20 vezes para cada caracter, esse acaba por não ser inserido de forma correta, demonstrando o erro de Race Condition.



