# RegEx

Normalmente, a combinação .+ pega qualquer caracter e em qualquer quantidade.  
Para evitar esse comportamento, fazendo com que pare ao encontrar o próximo caracter informado, adicione um ? (.+?).  

## Char classes
Podemos definir classes de caracteres com **[]**.  
Dentro dos classes de caracteres, os símbolos especiais não tem valor, ou seja, . é . mesmo.  

```
[A-Z] = Letras de A a Z
[123] = 1, 2 ou 3
[-.] = pode haver um traço ou um ponto
```

O símbolo **\s** serve para informar espaços. Equivalente a:  
```
[ \r\t\n\f]

```
O símbolo **\w** serve para pegar qualquer caracter, letra ou número. **\W** Para tudo que não for wordchar.

```
[A-Za-z0-9_]

```
O símbolo **\d** serve para informar todos os dígitos. **\D** Para tudo que não for dígito.
```
[0-9]
```

## Quantifiers
```
? = zero ou uma vez
* = zero ou mais vezes
+ = uma ou mais vezes
{n} = exatamente n vezes
{n,} = no mínimo n vezes
{n,m} = no mínimo n+1 vezes, no máximo m vezes
^ = negação dentro dos colchetes
```

## Anchors
Uma âncora não casa caracteres como as classes fazem, e nem definem quantidades. Âncoras marcam uma posição específica no alvo, por isso não é possível combiná-las com um quantifier.  
```
^ = Buscar somente no início
$ = no final do termo, indica que tem que terminar com o padrão informado anteriormente.
\b = retorna as posições onde esse texto é localizado, 
desconsiderando wordchars antes e depois desse texto (\w ou [A-Za-z0-9_]).
\B = Faz o contrário. Seleciona um trecho que tenha prefixo ou sufixo como wordchar. 
```

## Groups
Criamos grupos para trabalhar com conjunto de informações. Grupos são definidos com **()**.  
Podemos deixar os caracteres dentro do grupo como opcionais, podemos extrair a informação apenas do grupo.  
Para remover um grupo dos resultados de busca por RegEx, dentro do grupo, no início, adicione: **?:**.
```
() = define um grupo
(\w+) = grupo de chars
(\w+)? = grupo de chars opcional
(\w+) = grupo de chars que não será capturado


```

## Backreference
Consiste em uma técnica de referencia um grupo já utilizado, para selecionar um parte do texto posterior com base nesse grupo.  
Devemos referenciar o grupo pelo número.

```
<(h1|h2).+?>([\w\sõãíç.]+)</\1>
```


## Exemplos
Pegar uma data por extenso: 11 de Abril de 1995:
```
[0123]?\d\s+de\s+[A-Z][a-zç]{1,8}\s+de\s+[12]\d{3}
```

Pegar o usuário de um email que termina com gmail ou outlook:
```
([a-z.]{4,14}[a-z\d])@(?:gmail.com.br|outlook.com.br)
``` 

Uma validação de email:
```
^([\w-]\.?)+@([\w-]+\.)+([A-Za-z]{2,4})+$
```