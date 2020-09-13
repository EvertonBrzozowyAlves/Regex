# RegEx

## Char classes
Podemos definir classes de caracteres com **[]**.  
Dentro dos classes de caracteres, os símbolos especiais não tem valor, ou seja, . é . mesmo.  

```
[A-Z] - Letras de A a Z
[123] - 1, 2 ou 3
```
No próximo exemplo, que nessa classe de caracteres, pode haver um traço ou um ponto:
```
[-.]
```

O símbolo **\s** serve para informar espaços. Equivalente a:  
```
[ \r\t\n\f]

```
O símbolo **\w** serve para pegar qualquer caracter, letra ou número.

```
[A-Za-z0-9_]

```
O símbolo **\d** serve para informar todos os dígitos. Equivalente a:  
```
[0-9]
```

## Quantifiers
```
? - zero ou uma vez
* - zero ou mais vezes
+ - uma ou mais vezes
{n} - exatamente n vezes
{n,} - no mínimo n vezes
{n,m} - no mínimo n+1 vezes, no máximo m vezes
^ - negação dentro dos colchetes
```

## Anchors
Uma âncora não casa caracteres como as classes fazem, e nem definem quantidades. Âncoras marcam uma posição específica no alvo, por isso não é possível combiná-las com um quantifier.  
**\b** antes e depois do texto buscado, retorna as posições onde esse texto é localizado na string, desconsiderando wordchars antes e depois desse texto (\w ou [A-Za-z0-9_]).

## Exemplos
Pegar uma data por extenso: 11 de Abril de 1995  
```
[0123]?\d\s+de\s+[A-Z][a-zç]{1,8}\s+de\s+[12]\d{3}
```
