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

Listas são agrupamentos de valores, ex, [1,2,3,4, "banana", 2.3, nill, true, false]. Normalmente sequencia de dados similares.

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

#### As tuplas

```sh
    iex(2) > x = {1,2,3,4}
    {1, 2, 3, 4}
```

Acessar um elemento da tupla

```sh
    iex(2) > elem(x, 3)
    4
```

O conceito de tuplas, em elixir, é bastante utilizado para controlar fluxo e retorno de funções.
Ex:

```sh
    iex(2) > File.read("teste.txt")
    {:ok, ""}
```

Nesse exemplo a tupla foi retornada com o resultado da operação de leitura do arquivo e o conteúdo do arquivo.

```sh
    iex(2) > File.read("teste_.txt")
    {:error, :enoent}
```

Nesse exemplo a tupla foi retornada com o resultado da leitura do aquivo, o :error, e o tipo do erro: :enoent

O elixir utilizar as tuplas como uma forma mais elegante de lidar com excessões.

Caso seja necessário lançar a exceção, basta chamar a função assim:

```sh
    iex(2) > File.read!("teste_.txt")
    ** (File.Error) could not read file "teste_.text": no such file or directory

```

#### Keywords Lists, de forma rápida...

São listas de tuplas

```sh
    iex(2) > x = [ {:a, "valor de A"}, {:b, "valor de B"} ]
```

Normalmente keywords lists são utilizadas para passar opções para funções, onde as chaves devem ordenadas e únicas

#### Um pouco sobre Maps

Os Maps são a estrutura de chave,valor no elixir

Declarando um map com atoms

```sh
    iex(2) > x = %{a: 1, b: 2}
```

Acessando um valor com base na sua chave

```sh
    iex(2) > x[:a]
    1
```

```sh
    iex(2) > x[:b]
    2
```

Declarando um map com strings

```sh
    iex(2) > y = %{"a" => 1, "b" => 2}
```

Acessando um valor com base na sua chave

```sh
    iex(2) > y["a"]
    1
```

```sh
    iex(2) > y["b"]
    2
```

Quando o elemento é criado com atoms, é possível acessa-lo diretamente via .

```sh
    iex(2) > x.a
    1
```

```sh
    iex(2) > x.b
    2
```

Quando o elemento é criado com strins, não é possível acessa-lo diretamente via .
A notação de Maps com strings é bem mais útil no contexto do framework Pheonix

O módulo Map. contém diversas funções para trabalhar com Maps

#### Conhecendo um pouco do módulo enum

O módulo enum é um conjunto de funções que se utiliza internamente de interações para executar tarefas rotineira, dessa forma em elixir se usa pouco as funções tradicionais como for, each e while.
O Enum é muito utilizado para trabalhar com coleções de dados =)

Algumas funções comuns

```sh
    iex(2) > Enum.sort([1,2,3])
    [1, 2, 3]
```

```sh
    iex(2) > Enum.sort([1,2,3], :desc)
    [3, 2, 1]
```

Aplicando a função map

```sh
    iex(2) > Enum.map([1,2,3,4,5,6], fn el -> el ** 2  end)
   [1, 4, 9, 16, 25, 36]
```

No caso a função anonima precisa começar com fn e terminar com end

Utilizando o reduce

```sh
    iex(2) > Enum.reduce([1,2,3,4], 0, fn x, acc -> x + acc end)
   10
```

Utilizando o reduce com um Map

```sh
    iex(2) > Enum.reduce(%{a: 1, b: 2}, %{}, fn {k, v }, acc -> Map.put(acc, k, v + 1)   end )
   %{a: 2, b: 3}
```
