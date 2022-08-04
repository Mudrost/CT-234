# Capítulo 1 - Ordem de funções
## Notação O (Big-Oh) e similares

Motivação: medir assintóticamente o desempenho de algoritmos (em seus melhores, piores ou casos médios) de forma abstraída das particularidades de hardware, software ou input.

### Operações primitivas
As seguintes operações "custam" um tempo de execução unitário:
- Atribuição de valor para uma variável, ```x = 42;```
- Indexação, ```X[2]```
- Comparação entre valores, ```if(x < y)```
- Cálculo aritmético, ```x+23```
- Chamada de função, ```doSomething();```

Qual o número total de operações primitivas realizadas no código abaixo?
```cpp
int arrayMax(int A[], int n){    
    currentMax = A[0];                      // 1 atribuição + 1 indexação
    for(i = 1; i< n; i++){                  // 1 atribuição inicial + (1 teste + 1 incremento) por loop
        if (A[i] > currentMax)              // (1 indexação + 1 teste) por loop
            currentMax = A[i];              // (1 indexação + 1 atribuição) por loop - pior caso
    }                                       // 1 teste final (for)
return currentMax;                          // 1 retorno de função
}
```
Total de operações unitárias: 5 + 6*(n-1) = 5 + 6n -6 = 6n -1

### Taxa de crescimento e Notação O
*A taxa de crescimento do tempo de execução é uma propriedade intríseca do algorítmo*

A notação O fornece uma função para o "teto" para o comportamento **assintótico** do algorítmo.
Exemplo: 2n + 10 possui complexidade O(n). Admitindo que f(n) <= c * g(n), para todo n >= n0:
2n + 10 <= cn
(c-2)*n >= 10
n>= 10/(c-2)
Possível escolha: c = 3, n0 = 10. Existindo essas constantes, prova-se que O(n) é teto de f(n).

