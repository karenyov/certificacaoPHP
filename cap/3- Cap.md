# Capítulo 3 - Strings	e	padrões

## 3.1	HEREDOC, NOWDOC

- NOWDOC
> Utilizado para texto puro, e não conseguimos interpretar variáveis.

``` 
$texto	=	<<<'MEUTEXTO'
				SELECT	id,	nome,	idade	FROM	aluno
				INNER	JOIN	aluno_historico	ON	id	=	id
				INNER	JOIN	tabela	2
				INNER	JOIN	tabela	3
				INNER	JOIN	tabela	4
				WHERE	aluno	status	IS	NOT	IN	(1,	2,	3)
					...
					...
					...
					...
MEUTEXTO;

```

- HEREDOC

``` 
$a = 10;
$texto	=	<<<'MEUTEMPLATE'
	Agora podemos utilizar a variável, e 5 + 5 é $a
MEUTEMPLATE;

```

## 3.2	MANIPULANDO STRINGS

### strpos

``` 
$texto = 'abcde';
print strpos($texto, 'b'); //1


$texto = 'abcde';
if (strpos($texto, 'b')) {
	print 'Olá eu existo';
}

$texto = 'abcde';
print strpos($texto, 'a'); //0

// o print dentro do if não será exibido, pois o PHP entende ue 0 convertido para booleano é FALSE
$texto = 'abcde';
if(strpos($texto, 'a')) {
	print 'Olá eu existo';
}

// o print abaixo será exibido, pois é comparado o tipo de retorno
$texto = 'abcde';
if (false === strpos($texto, 'a')) {
	print 'Olá eu existo';
}

// param posição que será feito a busca na string, neste exemplo nenhuma saída será exibida
$texto = 'abcde';
if (false === strpos($texto, 'a', 1)) {
	print 'Olá eu existo';
}

// Não é permitido utilizar valores negativos no terceiro parâmetro. Nesse caso o PHP exibirá um warning "strpos(): Offset not contained in string..."
$comecar	=	-1;
if(false	===	strpos($texto,	'a',	$comecar))	{
	...
}

```

### stripos
Tem o mesmo comportamento que o ```strpo```, porém não leva em consideração letras maiúsculas ou minúsculas, ou seja, a tring php é a mesma que PHP.

```
$texto	=	'ABCDE';
if(false	===	stripos($texto,	'a'))	{
	print 'Olá	eu	existo';
}
```

## 3.3	STRINGS	TAMBÉM	SÃO	ARRAYS?

Podemos iterar sobre strings, pois strings são arrays.

```
$texto	=	'Zend Certified	Engineer';
for	($i	=	0;	$i	<	strlen($texto);	$i++)
{
	print $texto[$i];
}


// Zend Certified Engineer
```

### strstr
```
// exibir metade de uma string, exibe apenas o domínio do e-mail
$email	=	'php@php.net';
print	strstr('@',	$email); // @php.net

// retornar a assinatura
$email =	'php@php.net';
print	strstr('@',	$email,	true); // php
```

### substr
> http://php.net/manual/pt_BR/function.substr.php.
```
// extrair porção da string
$codigo =	'A3-11111.ABC';
print	substr($codigo,	0,	2);	//	A3
```

### trim,	ltrim	e	rtrim
```
// trim: remove os espaços em branco no começo e no final da string
$livro	=	'	PHP	';
print	trim($litro);	//	PHP

// remove caracter no começo e final da string
$nome	=	'aPHPa';
print	trim($nome,	'a'); //	PHP

//ltrim (início): remove os espaços em brancos (por padrão) de uma string ou remove a string desejada.
$nome	=	'aPHPa';
print	ltrim($nome, 'a'); // PHPa

//rtrim (final): remove os espaços em brancos (por padrão) de uma string ou remove a string desejada.
$nome	=	'aPHPa';
print	rtrim($nome,	'a'); // aPHP

```

> PHP	 possui	 uma	função	 chamada	 	chop	,	 que	 é	 apenas	 uma
atalho	para	a	função		rtrim	.	Então,	lembre-se:	ao	ver	a	função
chop	 ,	 ela	 terá	 o	 mesmo	 comportamento	 que	 a	 função
rtrim

### str_replace
```
// subistitui textos
$texto	=	'Comprei	um	livro	da	cor	azul';
print	str_replace('azul',	'laranja',	$texto); //Comprei	um	livro	da	cor	laranja

$texto	=	'Comprei	um	livro	da	cor	azul	e	amarelo';
print	str_replace(['azul',	'amarelo'],	['laranja',	'preto'],	$texto
);
// Comprei	um	livro	da	cor	laranja	e	preto


$texto	=	'Comprei	um	livro	da	cor	azul	e	amarelo';
print	str_replace(['azul',	'amarelo'],	'lilás',	$texto);
// Comprei	um	livro	da	cor	lilás	e	lilás


$texto	=	'Comprei	um	livro	da	cor	azul	e	amarelo';
$substituicoes	=	0;
str_replace(['azul',	'amarelo'],	'lilás',	$texto,	$substituicoes);
print $substituicoes; // 2

/*
Um	detalhe	importante	é	que	o	parâmetro	usado	para	contar	o
total	de	substituições	realizadas	é	passado	por	referência,	e	não	por
valor,	o	que	não	torna	possível	passar	um	valor	estático.

Será exibido um erro: O	erro nos	diz	que	não	é	possível	passar	valor	estático
por	referência,	apenas	variáveis.

*/

str_replace(['azul',	'amarelo'],	'lilás',	$texto,	0);

```

### strcasecmp
Comparação	 binária	 com	 strings	 em	 PHP.
```
// realiza	uma	comparação	independentemente	de letras	maiúsculas	ou	minúsculas
$string1	=	'olá!';
$string2	=	'OLá!';
if	(	0	===	strcasecmp($string1,	$string2))	{
print 'Iguais	!';
}
```

<img src="https://github.com/karenyov/certificacaoPHP/blob/main/img/2.11-%20Facilitando%20a%20vida%20-%202.png" width="350">
 