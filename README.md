<p align="center">
  <img src="https://user-images.githubusercontent.com/106783009/191138556-b0ec92fb-8eb0-4151-b109-d5ca961b5c3c.png" />
</p>
*Alunos: Felipi Yuri Santos (11917272) e Vicenzo d'Arezzo (?????)*



# LabICC2 - Trabalho 02 - Wall-e



&ensp;Neste relatório será realizada a comparação entre dois algoritmos para buscas: a **busca sequencial** (versão iterativa) e a **busca binária** (versão recursiva). A comparação será feita na linguagem C, e seus respectivos custos operacionais por meio do tempo de execução usando o comando de time no Bash de um Linux Mint, biblioteca.

&ensp; As instruções para os programas são as seguintes: Receber um conjunto de k valores inteiros, onde
$$
0 <k \leq 10^6
$$
&ensp;Após a definição do valor de k, a entrada consiste em k números inteiros, que compõem o conjunto de valores “válidos”. A seguir, a entrada contém um número inteiro q, sendo 
$$
(0 < q \leq 10^6 )
$$
que representará o número de consultas a serem feitas. Cada uma das próximas q linhas contém um inteiro representando número a ser buscado dentre os k valores lidos anteriormente. Caso esse número seja encontrado, sua saída deve conter uma única linha com a palavra “Encontrou”. Caso contrário, seu programa deve imprimir “Nao encontrou”. 

## Implementação Iterativa

![image](https://user-images.githubusercontent.com/106783009/191133682-387c5718-6be5-4670-933a-a8d3a88fd2c2.png)

&ensp;Para solucionar o estouro de variável, a cada laço de n * n * ... * n, é extraído o módulo do resultado obtido por 1000, extraindo assim os últimos 3 dígitos do número. Decompondo um número qualquer para o somatório da múltiplicação de cada um de seus algarismos pela respectiva potência de 10 correspondente à sua posição, é fácil verificar que essa operação de módulo afeta apenas o valor dos algarismos à esquerda dos 3 primeiros, que são irrelevantes no caso do exercício. Além disso, mesmo não sendo necessário calcular o módulo a cada iteração, o custo operacional de se testar essa necessidade a cada iteração seria semelhante ou maior.

## Implementação Recursiva

![image](https://user-images.githubusercontent.com/106783009/191134629-151001d6-57d7-4fc1-a432-5cf030611dc0.png)

&ensp;Para solucionar o estouro de variável, para cada retorno da função recursivePow, é extraído o módulo do resultado obtido por 1000, extraindo assim os últimos 3 dígitos do número. Decompondo um número qualquer para o somatório da múltiplicação de cada um de seus algarismos pela respectiva potência de 10 correspondente à sua posição, é fácil verificar que essa operação de módulo afeta apenas o valor dos algarismos à esquerda dos 3 primeiros, que são irrelevantes no caso do exercício. Além disso, mesmo não sendo necessário calcular o módulo a cada iteração, o custo operacional de se testar essa necessidade a cada iteração seria semelhante ou maior.

## Casos de teste

| Casos            | #1    | #2       | #3        | #4         | #5            |
| ---------------- | ----- | -------- | --------- | ---------- | ------------- |
| Entrada Esperada | 2 10  | 99 75301 | 37 543210 | 27 6543101 | 52 1000000000 |
| Saída Esperada   | 24    | 99       | 849       | 27         | 376           |

## Comparação dos Tempos de Execução

### Tempo de Execução da Versão Iterativa
![image](https://user-images.githubusercontent.com/106783009/191138358-40740fd1-10a9-46d8-9175-aa8c2a5eecf7.png)

### Tempo de Execução da Versão Recursiva
![image](https://user-images.githubusercontent.com/106783009/191138486-b2762f17-dc79-404b-a5ea-61eb29cd972e.png)

&ensp;O computador utilizado para os testes foi um notebook Dell G15 5510, com um processador Intel Core i5-10500H, funcionando à bateria com Eficiência Agressiva selecionado como opção de modo de aumento de desempenho do processador nas opções de energia do Windows 10 Pro 21H2.

## Considerações

&ensp;Devido à natureza de cada algoritmo, enquanto a versão iterativa executa a multiplicação k vezes, a versão recursiva é capaz de aproveitar a propriedade n^k = n^(k/2) * n^(k/2) para realizar um número exponencialmente menor de múltiplicações, ao custo de multiplicar números maiores mais vezes, o que nesse caso se provou excepcionalmente mais eficiente.
