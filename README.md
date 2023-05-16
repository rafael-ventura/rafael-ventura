### Hi there, i'm Rafael


[![Rafael's github stats](https://github-readme-stats.vercel.app/api?username=rafael-ventura)](https://github.com/anuraghazra/github-readme-stats)



[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=rafael-ventura&layout=compact&langs_count=6&hide=java)](https://github.com/anuraghazra/github-readme-stats)


<!--
**tsydolmir/tsydolmir** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
-🌱 I’m currently learning React and Angular
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->




Análise Algorítmica do problema da Árvore Geradora Mínima














Grupo A4
Elmo Sanches, Hernan Matiello, Rafael Cantanhede, Santiago Pacheco E Vitor Indio







Introdução

O Algoritmo de Prim é um algoritmo que pertence à teoria dos grafos e é usado para encontrar uma árvore geradora mínima em um grafo conexo com pesos. Uma árvore geradora mínima de um grafo é uma árvore que conecta todos os vértices do grafo e tem o menor peso total possível, ou seja, a soma dos pesos de todas as arestas da árvore é a menor possível.

Explicação do problema

A árvore geradora mínima de um grafo é uma subárvore que conecta todos os vértices do grafo e tem o menor peso total possível. O problema é encontrar essa árvore geradora mínima. Esse problema é relevante em muitas aplicações da vida real, como a construção de redes de telecomunicações ou a distribuição de energia elétrica, onde se deseja conectar todos os pontos com o menor custo possível.

Definição formal do problema

Dado um grafo conexo e não-direcionado G = (V, E) com peso atribuído a cada aresta e , o problema é encontrar uma árvore geradora T de G tal que a soma dos pesos das arestas de T seja a menor possível.

Entrada: Um grafo conexo e não direcionado G com um peso atribuído a cada aresta.
Questão: Encontrar uma árvore geradora T de G tal que a soma dos pesos das arestas de T seja a menor possível.
Saída: A árvore geradora mínima T de G.


Exemplos de instâncias do problema

Exemplo 1: 
Um grafo com 5 vértices e as seguintes arestas e pesos: (A-B, 1), (A-C, 3), (B-C, 4), (B-D, 2), (C-D, 5), (C-E, 6), (D-E, 7).
Exemplo 2: 
Um grafo com 4 vértices e as seguintes arestas e pesos: (A-B, 5), (B-C, 10), (C-D, 5), (D-A, 10).
Exemplo 3: 
Um grafo com 3 vértices e as seguintes arestas e pesos: (A-B, 2), (B-C, 3), (C-A, 1).

Algoritmo
Descrição esquemática do algoritmo

O Algoritmo de Prim opera por meio da construção progressiva da árvore geradora mínima, incluindo um vértice de cada vez. O processo tem início a partir de um vértice escolhido aleatoriamente, e prossegue sempre selecionando a aresta de menor peso que estabelece uma conexão entre um vértice já incorporado à árvore e um vértice que ainda não foi incluído.

Descrição formal do algoritmo

Inicialize a árvore geradora mínima com um único vértice, escolhido arbitrariamente do grafo.
Cresça a árvore adicionando iterativamente a aresta de menor peso que conecta um vértice já na árvore a um vértice fora dela.
Repita o passo 2 até que todos os vértices estejam na árvore.
Algoritmo

Neste algoritmo, G é o grafo, V[G] são os vértices do grafo, Adj[u] são os vértices adjacentes a u, w(u, v) é o peso da aresta entre u e v, chave[v] é o peso mínimo da aresta conectando v a árvore geradora mínima e pai[v] é o vértice conectado a v na árvore geradora mínima com peso mínimo.



function prim(grafo, inicio) {
    const arvore = [];
    const visitados = new Set();
    let arestas = [];


    // Para cada vértice adjacente ao vértice inicial
    for (let para in grafo[inicio]) {
        // Obtemos o custo da aresta
        let custo = grafo[inicio][para];


        // Adicionamos a aresta na lista de arestas a serem processadas
        arestas.push([custo, inicio, para]);
    }


   while (arestas.length > 0) {
        // Ordenar as arestas para simular uma heap
        arestas.sort((a, b) => a[0] - b[0]);
        const [custo, de, para] = arestas.shift();
        
        if (!visitados.has(para)) {
            visitados.add(para);
            árvore.push([de, para, custo]);
	  for (let vizinho in grafo[para]) {
                if (!visitados.has(vizinho)) {
                    let custoVizinho = grafo[para][vizinho];
                    arestas.push([custoVizinho, para, vizinho]);
                }
            }
        }
    }


    return arvore;
}

Exemplos da solução algorítmica

Vamos começar com um grafo contendo cinco vértices, representados pelas letras A, B, C, D e E. As arestas entre os vértices e seus respectivos pesos são dados da seguinte maneira:

(A, B): peso 2
(A, C): peso 3
(B, C): peso 1
(B, D): peso 1
(C, D): peso 4
(C, E): peso 5
(D, E): peso 2

Primeiro, vamos começar com o vértice A. Entre as arestas que saem do vértice A, a aresta (A, B) tem o menor peso, que é 2. Portanto, selecionamos essa aresta e adicionamos à nossa árvore em crescimento.

Agora, temos dois vértices em nossa árvore, A e B. As arestas que saem desses vértices e que levam a vértices que ainda não estão em nossa árvore são (A, C), (B, C) e (B, D). Entre essas, a aresta (B, D) tem o menor peso, que é 1. Portanto, selecionamos essa aresta e a adicionamos à nossa árvore.

Em seguida, temos três vértices em nossa árvore, A, B e D. As arestas que saem desses vértices e que levam a vértices que ainda não estão em nossa árvore são (A, C), (B, C), (D, E) e (C, D). Entre essas, a aresta (D, E) tem o menor peso, que é 2. Portanto, selecionamos essa aresta e a adicionamos à nossa árvore.

Finalmente, temos quatro vértices em nossa árvore, A, B, D e E. As arestas que saem desses vértices e que levam a vértices que ainda não estão em nossa árvore são (A, C), (B, C) e (C, D). Entre essas, a aresta (B, C) tem o menor peso, que é 1. Portanto, selecionamos essa aresta e a adicionamos à nossa árvore.

Agora, todos os vértices estão em nossa árvore e formamos uma árvore geradora mínima. As arestas na árvore geradora mínima são (A, B), (B, D), (D, E) e (B, C), e o peso total da árvore é 6.


Portanto, a árvore geradora mínima para esse grafo é composta pelas arestas (A, B), (B, D), (D, E) e (B, C), com um peso total de 6.



Agora no segundo exemplo, veja a imagem do grafo a seguir:

Temos 6 vértices, que resultará num resultado de 5 arestas para a árvore. 

Primeiro passo é arbitrariamente escolher um vértice. Imagine que escolhemos o vértice 1.
Depois seguindo o algoritmo, escolhemos o menor caminho, que é a aresta que liga até o vértice 2, com peso 2.
Depois, escolhemos o menor caminho para um vértice que não está conectado, e este será o vértice 0.
Próximo passo será do vértice 2 ao 3, com a aresta de valor 2
Penúltimo passo será do vértice 2 ao 5, com a aresta de valor 4(note que a aresta que liga o vértice 3 ao 5 também vale 4, então não importará qual o caminho seguir.
E por último, o caminho a seguir será a aresta que liga o 5 ao 4, com valor 3.

Note que o resultado final, a árvore geradora mínima, está sublinhada em laranja.

Análise do algoritmo

O algoritmo de Prim é um algoritmo guloso, o que significa que ele faz a escolha localmente ótima em cada etapa com a esperança de que essas escolhas locais levarão a uma solução globalmente ótima. O algoritmo começa com um vértice arbitrário e seleciona a aresta de menor peso conectada a ele. Em seguida, adiciona essa aresta à árvore e repete o processo para os vértices adjacentes, sempre escolhendo a aresta de menor peso que conecta um vértice dentro da árvore a um vértice fora da árvore.

A complexidade de tempo do algoritmo de Prim é O(E log V) quando implementado com uma heap de Fibonacci, onde E é o número de arestas e V é o número de vértices. Isto é porque cada aresta e cada vértice são processados uma vez pelo algoritmo.

A complexidade do tempo do algoritmo de Prim é O(E log V) quando implementado com uma heap de Fibonacci. Isso ocorre porque cada aresta e cada vértice são processados uma vez pelo algoritmo. O uso de uma heap de Fibonacci permite a extração do mínimo e a diminuição da chave em tempo O(log V), o que é crucial para a eficiência do algoritmo de Prim.

O algoritmo de Prim começa por inicializar uma fila de prioridade, onde as chaves são os pesos das arestas e os valores são os vértices. Isso pode ser feito em tempo O(V), pois cada vértice deve ser inserido na fila de prioridade uma vez.

Em seguida, o algoritmo de Prim entra em um loop que continua até que todos os vértices tenham sido adicionados à árvore geradora mínima (MST). Durante cada iteração do loop, o algoritmo de Prim remove o vértice com a menor chave (ou seja, o vértice mais próximo) da fila de prioridade. Remover o mínimo de uma fila de prioridade tem uma complexidade de tempo O(log V), pois a fila de prioridade é implementada como uma heap.

Após remover um vértice da fila de prioridade, o algoritmo de Prim atualiza as chaves dos vértices adjacentes. Para cada vértice adjacente, ele verifica se a aresta que conecta o vértice removido ao vértice adjacente tem um peso menor do que a chave atual do vértice adjacente. Se sim, ele atualiza a chave do vértice adjacente na fila de prioridade. Como cada aresta é considerada exatamente uma vez durante o algoritmo, esse passo tem uma complexidade de tempo total de O(E log V), pois atualizar uma chave na fila de prioridade tem uma complexidade de tempo O(log V) e há E arestas.

Portanto, a complexidade total de tempo do algoritmo de Prim é O(V + E log V). Como geralmente E é maior que V em grafos conectados, simplificamos essa expressão para O(E log V).


Conclusão e Discussões
O algoritmo de Prim é eficiente para grafos densos, pois a complexidade do tempo é proporcional ao número de vértices. No entanto, para grafos esparsos, o algoritmo de Kruskal pode ser uma escolha melhor, pois sua complexidade de tempo é proporcional ao número de arestas.

Além disso, o algoritmo de Prim só funciona para grafos conectados. Se o grafo não for conectado, o algoritmo falhará, pois não será capaz de alcançar todos os vértices.

Uma vantagem do algoritmo de Prim é que ele é mais fácil de implementar para grafos representados como matrizes de adjacência em vez de listas de adjacência, ao contrário do algoritmo de Kruskal.

O algoritmo de Prim é uma ferramenta importante na teoria dos grafos e tem aplicações em muitos campos, como redes de computadores, circuitos elétricos e planejamento de rotas. Ele permite encontrar a árvore geradora mínima de um grafo conectado, proporcionando uma maneira eficiente de minimizar o peso total das arestas.


Referências bibliográficas

Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2009). Introduction to algorithms. MIT press. https://mitpress.mit.edu/books/introduction-algorithms-third-edition

Prim's Algorithm - https://www.geeksforgeeks.org/prims-minimum-spanning-tree-mst-greedy-algo-5/

Prim’s Minimum Spanning Tree Algorithm - https://www.tutorialspoint.com/design_and_analysis_of_algorithms/design_and_analysis_of_algorithms_prims_algorithm.htm

Prim's Algorithm - https://brilliant.org/wiki/prims-algorithm/

Graph Theory: Spanning Trees - https://www.cs.odu.edu/~toida/nerzic/390teched/graph/prim.html

Aula 18 - Árvores Geradoras - http://www2.ic.uff.br/~sylvia/TEACH/inf1052/2016.2/aula18-AGM.pdf

Minimum Spanning Tree: Prim’s Algorithm - https://algs4.cs.princeton.edu/lectures/43MinimumSpanningTrees.pdf

Prim’s and Kruskal’s Algorithms - https://www.cse.ust.hk/~dekai/271/notes/L13/L13.pdf

Análise de Algoritmos - Conteúdo adaptado de slides do Prof. Paulo Feofiloff e do Prof. José Coelho de Pina- https://www.ime.usp.br/~cris/aulas/07_2_338/slides/aula24.pdf

Prim's algorithm - https://en.wikipedia.org/wiki/Prim%27s_algorithm





