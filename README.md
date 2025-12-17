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