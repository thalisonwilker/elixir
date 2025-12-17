## Elixir

## Programação funcional

É transformar o dado através de funções

[Instalação do Erlang e Elixir com ASDF no Ubuntu - Dev Community](https://dev.to/allefgomes/instalacao-do-erlang-e-elixir-com-asdf-no-ubuntu-5hnn)

### O IEX

Interactive Elixir

```sh
    iex
```

#### Tipo básicos

Os tipos inteiros
Inteiros

```sh
    iex(2) > 1 + 1
    2
```

Double, ou com ponto flutuante

```sh
    iex(2) > 2 / 2
    1.0
```

Tipagem dinâmica

```sh
    iex(2) > x=1
    1
```

Strins

```sh
    iex(2) > x="thalyson"
    "thalyson"
```

nulos

```sh
    iex(2) > x=nil
    nil
```

Atoms

```sh
    iex(2) > x=:thalyson
    :thalyson
```

#### Módulos e funções

O módulo Kernel contém um conjunto de funções, como se fosse o builtins do python, que podemos usar livremente, como por exemplo: is_float/1, is_nil/1, etc..

Algumas funções no elixir são apresentada com o "/1", "/2", "/3". isso significa a quantidade de argumentos que a função recebe, ou a aridade da função.
A mesma função pode receber aridades (quantidade de argumentos) diferentes e trabalhar de formas diferentes com os dados.

No paradigma de OO, é muito utilizado "String".metodo(), ex: "String".downcase()

No elixir é sempre função para função, ou seja, tem que verificar qual o módulo estamos trabalhando e assim chamar a função correspondente a tarefa a ser realizada.
Ex, String.downcase("StRinGSS"), irá converter a string para minuscula

#### Um pouco sobre imutabilidade

```sh
    iex(2) > x="Thalyson"
    "Thalyson"
```

Erro comum em relação a orientação a objetos

```sh
    iex(2) > x.downcase()
    (ArgumentError) you attempted to apply a function named :downcase on "Thalyson"
```

Pois "x" não é reconhecido como função. Para alterar o valor de x, é necessario aplicar uma função do módulo String

```sh
    iex(2) > String.downcase(x)
    "thalyson"
```

#### As listas

Listas são agrupamentos de valores, ex, [1,2,3,4, "banana", 2.3, nill, true, false]
As listas são encadeadas, ou linked lists: "estruturas de dados lineares onde elementos (nós) não são armazenados contiguamente na memória, mas sim conectados por ponteiros, formando uma sequência lógica a partir de uma "cabeça" (primeiro nó)."
Para acessar algum elemento, normalmente a lista precisa ser percorrida, já que acessar o índice não funciona.
ex:

```sh
    iex(2) > x = [1,2,3,4]
    [1,2,3,4]
```

```sh
    iex(2) > x[0]
    ** (ArgumentError) the Access calls for keywords expect the key to be an atom, got: 0
```

Adicionar um novo elemento no início da lista é uma operação considerada barata, pois é simples acessar o primeiro elemento da lista.

```sh
    iex(2) > [0 | x]
    [0, 1, 2, 3, 4]
```

Adicionar um novo elemento no final da lista é uma operação considerada mais cara, pois teria que percorrer a lista até encontrar o elemento que aponta para o nada.

Nas listas em elixir existe o conceito de head e tail, ou seja, cabeça e calda.

A cabeça ( head ) é o primeiro elemento da lista

```sh
    iex(2) > hd [0 | x]
    0
```

A calda ( tail ) são todos os elementos a partir da cabeça da lista

```sh
    iex(2) > tl [0 | x]
    [1, 2, 3, 4]
```

Operações com listas

Somar listas

```sh
    iex(2) > [1, 2, 3] ++ [4, 5, 6]
    [1, 2, 3, 4, 5, 6]
```

Subtração de listas

```sh
    iex(2) > [1, 2, 3] -- [3, 4, 5, 6]
    [1, 2]
```

Na subtração de listas, o resultado é a primeira lista menos os elementos em comum da segunda lista.

Exete o módulo List, para aplicar efetuar operações com listas.

```sh
    iex(2) > List.last([1,2,3,4])
    4
```

```sh
    iex(2) > List.delete_at( [1,2,3,4], 2 )
    [1, 2, 4]
```
