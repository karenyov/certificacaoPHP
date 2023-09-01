# Capítulo 5 - Arrays

## 5.1	 ARRAYS	 ASSOCIATIVOS	 X ENUMERATIVOS

``` 
print	[
'PHP',
'Certificação',
'Livro'
]

$elementos	=	[
	0	=>	'PHP',
	1	=>	'Certificação'
]
$elements[]	=	'Livro';

``` 

### Arrays associativos
> PHP	 sempre	 usará	 a	 última	 chave	 numérica	 para	 gerar	 a próxima	 chave	 caso	 nenhuma	 seja	 fornecida.	
> [Link](http://php.net/manual/pt_BR/language.types.array.php).

```
$frutas	=	[
'melao'				=>	'amarelo',
'melancia'	=>	'vermelha',
'kiwi'					=>	'verde'
]

$frutas	=	[
'melao'				=>	'amarelo',
'melancia'	=>	'vermelha',
'kiwi'					=>	'verde'
];
$frutas[]	=	'laranja	?';

Array
(
	[melao]	=>	amarelo
	[melancia]	=>	vermelha
	[kiwi]	=>	verde
[0] =>	laranja	?
)
```

```
$frutas	=	[
'melão'				=>	'amarelo',
'melancia'	=>	'vermelha',
'kiwi'					=>	'verde'
];
$frutas[10]	=	'laranja	?';
$frutas[]	=	'abóbora';


Array
(
	[melão]	=>	amarelo
	[melancia]	=>	vermelha
	[kiwi]	=>	verde
[10] =>	laranja	?
[11] =>	abóbora
)

```

### Arrays multidimensionais
> [Link](http://php.net/manual/pt_BR/language.types.array.php).

```
$matriz	=	[
'categorias'	=>	[
'subcategoria1'	=>	[
'sub1',
'sub2',
	],
'subcategoria2'	=>	[
'sub1',
'sub2',
	]
	]
];
print_r($matriz);

Array
(
	[categorias]	=>	Array
(
	[subcategoria1]	=>	Array
(
[0] =>	sub1
[1] =>	sub2
			)
	[subcategoria2]	=>	Array
(
[0] =>	sub1
[1] =>	sub2
	)
	)
)

```


```
$array	=	array(
	1				=>	'a',
"1"		=>	'b',
	1.5		=>	'c',
true	=>	'd',
);
print_r($array);

Array
(
[1] =>	d
)

```

Isso	ocorre	pois	o	PHP	possui	algumas	restrições	nas	chaves	dos
arrays,	 convertendo	 qualquer	 tipo	 booleano	 para	 inteiro.	 e
arredondando	tipos	float/double.


## 5.2	  ORGANIZANDO	 DADOS	 DENTRO	 DE ARRAYS
