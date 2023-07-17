# Certificação PHP
Preparando para a certificação PHP


## Links
- https://techguide.sh/pt-BR/path/php/


## Capítulo 2 - Entendendo o Básico do PHP

Tags permitidas:

- ``` <? ```
- ``` <?php ```
- ``` <script language="php"></script> ```

### 2.1 O PROBLEMA DAS TAGS PHP
Para evitar problemas de espaço em branco após a tag de fechamento, evite tag de fechamento para prvinir conflitos.


### 2.2 VARIÁVEIS
PHP é uma linguagem não tipada (fracamente tipada).
> https://www.php.net/manual/pt_BR/language.types.intro.php


``` 
$a = ''; //Válido
$123abc = ''; //Inválido
$_a = ''; //Válido
```

### 2.3 CAIXA ALTA OU CAIXA BAIXA

``` 
$a	=	0;
if(EMPTY($a))	{
	print 'Olá,	eu	estou	vazio';
}

``` 

ou 

``` 
CLASS Cachorro	{
				public function	latir() {
								print 'au	au	au!';
				}
}
$pastorAlemao	=	new	Cachorro();
$pastorAlemao->latir();

``` 

Ambas sintaxes são válidas. Porém não é recomendável usar para não causar confusões.

> obs: Apenas	 fique	 atento,	 pois	 esse	 tipo	 de	 comportamento	 não	 se
aplica	a	nome	de	variáveis.

### 2.4 CARACTERES ESPECIAIS?
``` 
$coração	=	'Olá,	eu	tenho	um	$coração';
print $coração;

``` 

O	 que	 você	 acha	 dessa	 sintaxe?	 Ela	 é	 válida?	 Sim,	 ela	 é	 válida.
Podemos	 definir	 variáveis	 com	 caracteres	 especiais,	 tais	 como		ç	,
	~	,		^	,	e	assim	por	diante.
	
> A	 única	 forma	 de	 invalidar	 a	 sintaxe	 de	 uma	 variável	 é
utilizando	números	no	começo,	lembre-se	disso.

### 2.5 STRINGS
Com	PHP,	podemos	utilizar	aspas	simples	ou	aspas	duplas	para
delimitar	uma	string.

``` 
$simples	=	'Olá';
$dupla			=	"Olá";

``` 


### 2.6 COMENTÁRIOS

``` 
// comentário

# comentário

/*
comentário
*/
``` 

### 2.7 OPERADORES ARITMÉTICOS

- ```+``` (Soma)
- ```-``` (Subtração)
- ```/``` (Divisão)
- ```*``` (Multiplicação)
- ```%``` (Módulo)

### 2.8 OPERADORES DE ATRIBUIÇÃO

```
$a = 'ZCPE'
```


```
$a = [
	0 => 1,
	1 => 2
]
```

### 2.9 COMPARAÇÕES

```
$a	=	0;
$b	=	'0';
if	($a	==	$b)	{
		print 'São	iguais!';
}
```

É obtido a resposta	"São	iguais!",
pois	com	um	sinal	igual	duplo,	o	PHP	compara	apenas	o	valor.	Ou
seja,	 aqui	 comparamos	 apenas	 	0		 da	 variável	 	$a		 com	 	0		 da
variável		$b	.

```
$a	=	0;
$b	=	'0';
if	($a	===	$b)	{
		print 'São	iguais!';
}
```

Ao executar o script agora, não será exibido o print.

> Com o sinal igual duplo, PHP comparará apenas valor, e com o igual triplo, comparará valor e tipo.


### 2.10 OPERADORES BITWISE
> https://www.php.net/manual/en/language.operators.bitwise.php


- ```&``` - AND (ou E)
- ``` | ``` - OR (ou OU)
- ``` ^ ``` - XOR
- ``` << ``` - LEFT SHIFT
- ``` \>> ``` - RIGHT SHIFT


- ```&=``` - AND (ou E)
- ``` |= ``` - OR (ou OU)
- ``` ^= ``` - XOR
- ``` <<= ``` - LEFT SHIFT
- ``` \>>= ``` - RIGHT SHIFT


> http://sandbox.onlinephpfunctions.com/.

#### Movendo	bits	à	esquerda	<<


```
print(7	<<	9);

# 7	*	2	^	9

# 2	^	9	=	2	*	2	*	2	*	2	*	2	*	2	*	2	*	2	*	2	=	512

# 7	*	512	=	3584

 ```

#### Movendo	bits	à	direita	>>

```
print	(4	>>	6)

# 4	/	2	^	6

# 2	^	6	=	2	*	2	*	2	*	2	*	2	*	2	=	64

# 64	/	4	=	**0,0625**

 ```
 
#### Operador	de	negação	~

```
~7	

~x	=	-x	-	1.


print	(~7); // -8

```

### 2.11	FACILITANDO	A	VIDA
> http://php.net/manual/pt_BR/language.operators.bitwise.php


<img src="https://github.com/karenyov/certificacaoPHP/blob/main/img/2.11-%20Facilitando%20a%20vida%20-%201.png" width="350">
 
```
print	(5	&	2);
```

<img src="https://github.com/karenyov/certificacaoPHP/blob/main/img/2.11-%20Facilitando%20a%20vida%20-%202.png" width="350">
 
Podemos	 ver	 que,	 no	 resultado	 obtido,	 temos	 duas	 linhas	 na
tabela	 correspondentes	 ao	 valor	 5	 e	 ao	 valor	 2.	 Porém,	 não
possuímos	 nenhum	 bit	 ativo	 na	mesma	 coluna.	 Então,	 a	 operação
	&		 (AND)	 para	 os	 inteiros	 5	 e	 2	 resulta	 em	 0,	 pois	 não	 existe
nenhum	bit	ativo	em	ambos.



```
print	(5	|	2);
```

<img src="https://github.com/karenyov/certificacaoPHP/blob/main/img/2.11-%20Facilitando%20a%20vida%20-%203.png" width="350">
 
Se	você	conseguiu	chegar	ao	número	7,	está	totalmente	correto.

```
print	(3	^	2);
```

<img src="https://github.com/karenyov/certificacaoPHP/blob/main/img/2.11-%20Facilitando%20a%20vida%20-%204.png" width="350">
 
 
Aplicando	 o	 operador	 XOR,	 temos	 como	 resultado	 1.

### 2.12 CONSTRUTORES DE LINGUAGEM


#### Construtores de saída

- exit(): usado para exibir uma saída e, logo em seguida, finalizar a execução do script.
```
exit('Livro de certificação PHP');
```

- die(): usado para exibir uma saída e, logo em seguida, finalizar a execução do script.
```
exit('Livro de certificação PHP');
```

- echo(): usado para exibir uma saída.
```
echo 'PHP'; // ou echo ('PHP');
```

- return(): usado para retornar um valor e finalizar a execução do script, ou retornar o valor desejado para quem está executando o script.
```
echo 'Casa do código';

return ;

echo 'PHP'; // Essa linha nunca será executada
```

- print(): usado para exibir uma saída.
```
print 'PHP 5.5'; // Ou print ('PHP 5.5');
```

#### Construtores de avaliação

- empty(): usado para verificar se uma variável é vazia, ou seja, uma variável sem valor.
- eval(): usado para avaliar o conteúdo de uma string em PHP.
- include() e include_once: usado para incluir e avaliar um arquivo PHP, porém utilizando ```include```, apenas um aviso(warning) é exibido caso o PHP não encontre o arquivo desejado.
- require() e require_once(): usado para incluir e avaliar um arquivo PHP, porém, utilizando ```require```, ele exibe um erro fatal (fatal error) caso não consiga encontrar o arquivo desejado.


#### Outros
- isset(): usado para verificar se uma variável foi definida e que não possua o valor nulo.
- unset(): usado para remover uma variável.
- list(): usado para assinar um array a um grupo de variáveis


### 2.13 CONSTANTES
```
define('1CONSTANTE', 'valor'); //Inválido
define('_CONSTANTE', 'valor'); //Válido
define('minhaconstante', 'valor'); //Válido
define('$CONSTANTE', 'valor'); //Inválido
```

### 2.14 NAMESPACES
```
<?php
require	'MinhaClasse.php';

namespace	Zce\Exemplo;

```

```
namespace	zce;			//	Válido
namespace	1zce;		//	Inválido
namespace	_zce_;	//	Válido
```

### 2.15 EXTENSÕES

PHP	 nos	 possibilita	 usar	 extensões	 para	funcionalidades	 que	 o
próprio	 PHP	 não	 possui	 no	 seu	 core.	


### 2.16 OPCACHE

Como	 na	 maioria	 dos	 itens	 relacionados	 à
computação,	opCode	é	uma	abreviação	para	operation	code	(código
de	 operação),	 que	 nada	 mais	 é	 do	 que	 o	 código	 que	 a	 máquina entende	 (código	 que	 de	 fato	 a	 máquina	 executará),	 ou	 seja,	 o
opCache	realiza	um	cache	desse	código.


