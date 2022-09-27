# README

![https://user-images.githubusercontent.com/106783009/191138556-b0ec92fb-8eb0-4151-b109-d5ca961b5c3c.png](https://user-images.githubusercontent.com/106783009/191138556-b0ec92fb-8eb0-4151-b109-d5ca961b5c3c.png)

*Discentes: Felipi Yuri Santos (11917272) e Vicenzo d’Arezzo (13671790)*

# LabICC2 - Trabalho 02 - Wall-e

Neste relatório será realizada a comparação entre dois algoritmos para buscas: a **busca sequencial** (versão iterativa) e a **busca binária** (versão recursiva). A comparação será feita na linguagem C, e seus respectivos custos operacionais por meio do tempo de execução usando o comando de time no Bash de um Linux Mint, da biblioteca.

As instruções para os programas são as seguintes: Receber um conjunto de $k$ valores inteiros, onde $0 < k \leq 10^6$. Após a definição do valor de $k$ , a entrada consiste em $k$ números inteiros, que compõem o conjunto de valores “válidos”. 

A seguir, a entrada contém um número inteiro $q$, sendo $0 < q \leq 10^6$ que representará o número de consultas a serem feitas. Cada uma das próximas $q$ linhas contém um inteiro representando número a ser buscado dentre os $k$ valores lidos anteriormente. Caso esse número seja encontrado, sua saída deve conter uma única linha com a palavra “Encontrou”. Caso contrário, seu programa deve imprimir “Nao encontrou”.

## Implementação da Busca Sequencial

![*Print da função busca_sequencial()*](https://user-images.githubusercontent.com/38444497/192427992-64565c54-84ba-4daf-964b-4f1d8a0974ed.png)


*Print da função busca_sequencial()*

A solução sequencial é a mais simples que existe, ela é um método totalmente de força bruta que vai percorrer todo o vetor de input, verificando elemento a elemento até encontrar o elemento-chave, ou seja, o elemento buscado. É simples assim. Na análise de complexidade de tempo para esse algoritmo/função, temos $O(n)$, já que fazemos n operações de comparação. E, na complexidade espacial teremos $O(1)$, já que apenas precisamos de uma variável declarada uma vez por looping de iteração.

Existe uma variação desse algoritmo conhecida como Busca Sequencial Indexada que melhora um pouco essa complexidade de tempo, mas foge do escopo deste relatório.  

## Implementação da Busca Binária (versão recursiva)

![*Print da função buscaBinaria_recursiva()* ](https://user-images.githubusercontent.com/38444497/192428041-db9fd853-9666-4e29-9a8a-8d9bb33af96b.png)


*Print da função buscaBinaria_recursiva()* 

Agora com a implementação da busca binária, temos a mesma situação, porém o grande truque aqui é procurar até certo ponto (isso é um padrão recorrente nos algoritmos de busca, aparentemente). Primeiramente assumimos um vetor ordenado (dadas as circunstâncias do ambiente para simulação, foi usado o método de ordenação *qsort()* da biblioteca-padrão stdlib.h da linguagem C. Nós procuramos no vetor ordenado saber se o valor da posição mediana, ou seja, o elemento no índice da mediana do vetor é maior ou menor do que nossa chave buscada. Caso seja menor, procuraremos a chave na primeira metade antes do início do vetor até sua mediana. Caso contrário, na segunda metade, a partir da mediana até o final do vetor.

O if comentado na foto é desnecessário porque em tese, caso a chave não seja nem menor, nem igual a mediana, e nem tenhamos chego no final do vetor, só há uma recorrência possível que é o fato da chave ser maior que o elemento na mediana (é uma boa até porque o C gera warnings caso use a flag -Wall, impossibilitando o aluno de upar o exercício no Run.Codes).  

A complexidade de tempo para a busca binária recursiva é $O(log_2{n})$. Já a complexidade espacial para a busca binária recursiva é apenas $O(n)$.

## Comparação dos Tempos de Execução

### 1. Tempo de Execução da Busca Sequencial

![Untitled 2](https://user-images.githubusercontent.com/38444497/192428112-3abad4b3-dedf-4ed1-85d3-a864cbcbd4a9.png)


### 2. Tempo de execução da da Busca Binária Recursiva

![Untitled 3](https://user-images.githubusercontent.com/38444497/192428130-897a60c0-fcaa-418d-b413-b87cb5bd0f96.png)


### Tabela comparativa

| --- | --- | --- | --- | --- | --- |

| #3 | 500 | 1000 | 1ms | 1ms | 0ms |
| #4 | 50 | 900000 | 77ms | 47ms | 30ms |
| #5 | 50 | 100000 | 12ms | 10ms | 2ms |

O computador utilizado para os testes foi um desktop B450M com um processador AMD Ryzen 5600 sem overclock.

### Considerações finais

Com a análise comparativa, ficou nítido que caso busquemos implementar o melhor algoritmo no sentido de tempo de execução, estaremos falando da busca binária, já que pra grandes valores para $n$, ela irá compensar mais por ter sua complexidade baseada em logaritmos, em vez do outro algoritmo, que é linear. Entretanto, seu único lado ruim mesmo é que provavelmente algumas vezes não irá compensar pois devemos levar em conta que o vetor pedido deverá estar previamente ordenado. E, se não tivermos um algoritmo de ordenação muito eficiente, poderá ser custoso pois aí o resultado final poderá depender até mais do algoritmo de ordenação do que do algoritmo de busca.
