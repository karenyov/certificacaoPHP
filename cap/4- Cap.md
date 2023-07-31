# Capítulo 4 - 	XML,	JSON	e	utilização	de	datas

## 4.1	SIMPLE_XML_*,	SIMPLEXMLELEMENT

``` 
$meuXML	=	'<root/>';
simple_xml_load_string($meuXML);
```

``` 
$meuXML	=	'<root/>';
simple_xml_load_string($meuXML,	'SimpleXMLElement');
```

``` 
class MeuSimpleXml extends SimpleXMLElement	{}
$meuXML	=	'<root/>';
simple_xml_load_string($meuXML,	'MeuSimplesXml');
```

> [Link](http://php.net/manual/pt_BR/libxml.constants.php).

``` 
simple_xml_load_string($meuXML,	'SimpleXMLElement',	LIBXML_NOERROR
);
``` 

``` 
simple_xml_load_string($meuXML,	'SimpleXMLElement',	LIBXML_NOERROR,	'namespace');
``` 

``` 
$meuXml	=	<<<XMLDATA
<zce>
	<basico>
	<sintaxe>
	PHP	tags,	Bitwise
	</sintaxe>
			</basico>
</zce>
XMLDATA;
``` 

``` 
$meuXml	=	new	SimpleXMLElement($meuXml);
$meuXml->basico;	//irá	retornar	um	objeto	SimpleXMLElement
``` 

``` 
$meuXml	=	new	SimpleXMLElement($meuXml);
$meuXml->children();	//irá	retornar	um	objeto	SimpleXMLElement
``` 

> [Link](http://php.net/manual/en/refs.xml.php).

## 4.2	DOM	(DOCUMENT	OBJECT	MODEL)

> [Link](http://php.net/manual/en/book.dom.php).


``` 
$load	=	new	DOMDocument();
$load->load('/caminho/para/arquivo/meu.xml');
``` 

``` 
$loadHtml	=	new	DOMDocument();
$loadHtml->loadHTML('<html><p>Hello</p><br></html>');
``` 

``` 
$loadHtmlFile	=	new	DOMDocument();
$loadHtmlFile->loadHTMLFile('/caminho/para/arquivo/meu.html');
``` 

``` 
$loadString	=	new	DOMDocument();
$loadString->loadXML('<root><nome>PHP</nome></root>);
``` 

## 4.3	 COMBINANDO	 DOMDOCUMENT E SIMPLEXMLELEMENT

``` 
// converter	um objeto		SimpleXMLElement		para	um		DOMNode
$no	=	new	DOMDocument();
$no->loadXML('<root></root>');
simplexml_import_dom($no);
``` 

``` 
class MeuElemento extends SimpleXMLElement	{}
$no	=	new	DOMDocument();
$no->loadXML('<root/>');
simplexml_import_dom($no,	'MeuElemento');
``` 

``` 
//converter	 um	 DOMNode	 para	 um SimpleXMLElement
$no	=	new	SimpleXMLElement('<root/>');
dom_import_simplexml($no);
``` 


## 4.4	XPATH	E	DOMDOCUMENT

> [DOMXPath Link](https://www.php.net/manual/pt_BR/class.domxpath.php).
> [SimpleXMLElement Link](https://www.php.net/manual/pt_BR/simplexmlelement.xpath.php).


``` 
$xml	=	'
<biblioteca>
	<livro	id="1">
	<nome>PHP</nome>
	<descricao>Aprenda	PHP</descricao>
			</livro>
</biblioteca>
';
$documento	=	new	DOMDocument();
$documento->loadXML($xml);
$xpath	=	new	DOMXpath($documento);
$elemento	=	$xpath->query('/biblioteca/livro');

print_r($elemento);

/*
DOMNodeList	Object
(
	[length]	=>	1
)

*/
``` 

``` 
foreach	($elementos as $no)	{
			print $no->nodeValue;
}

``` 

<img src="https://github.com/karenyov/certificacaoPHP/blob/main/img/4.4%20-%20Xpath%20-%201.png" width="500">


``` 
$xml	=	'
<biblioteca>
	<estante	identificador="C2">
	<livro	id="1">
	<nome>PHP</nome>
	<descricao>Aprenda	PHP</descricao>
	</livro>
	<livro	id="2">
	<nome>Zend	framework</nome>
	<descricao>Como	utilizar	o	Zend	framework</descricao>
			</livro>
	</estante>
	<estante	identificador="D1">
	<livro	id="5">
	<nome>Bitwise</nome>
	<descricao>Manipulação	de	bitwise	para	ninjas</descric
ao>
	</livro>
			</estante>
</biblioteca>
';
$documento	=	new	DOMDocument();
$documento->loadXML($xml);
$xpath	=	new	DOMXpath($documento);
$elemento	=	$xpath->query('//livro');
print_r($elemento);

/*
DOMNodeList	Object
(
	[length]	=>	3
)

*/

``` 

``` 
$documento	=	new	DOMDocument();

$documento->loadXML($xml);
$xpath	=	new	DOMXpath($documento);
$elemento	=	$xpath->query('/biblioteca/estante[@identificador="D1"
]//livro');
print_r($elemento);

/*
DOMNodeList	Object
(
	[length]	=>	1
)
*/

```


## 4.5	XPATH	E	SIMPLE_XML_*

```
$texto	=	'
<biblioteca>
	<livro	id="1">
	<nome>PHP</nome>
	<descricao>Aprenda	PHP</descricao>
			</livro>
</biblioteca>';
$xml	=	simplexml_load_string($texto);
$elementos	=	$xml->xpath('/biblioteca/livro');
print_r($elementos);

/*
Array
(
[0] =>	SimpleXMLElement	Object
(
	[@attributes]	=>	Array
(
	[id]	=>	1
	)
	[nome]	=>	PHP
	[descricao]	=>	Aprenda	PHP
	)
)

*/

```

## 4.6	JSON	ENCODE,	DECODE
> [Link](https://www.json.org/json-en.html).

### JSON ENCODE

```
// a	transformar	um	tipo	de	dado	PHP	em	JSON
print	json_encode([
'zcpe'	=>	[
'básico',
'avançado'
	]
]);

```

```
print	json_encode([
'zcpe'	=>	[
'básico',
'avançado'
	]
],	JSON_HEX_QUOT);
```

```
print	json_encode([
'zcpe'	=>	[
'básico',
'avançado'
	]
],	JSON_HEX_QUOT	|	JSON_HEX_TAG);
```

> JSON_HEX_QUOT	 	 transformará	 todas	 as	 aspas	 (	 "	 )	 em
\u0022	 ,	 ou	 podemos	 utilizar	 	 JSON_HEX_TAG	 ,	 que
transformará	os	sinais		<		e		>		em		\u003C		e		\u003E	.	O	PHP
nos	 fornece	 uma	 lista	 com	 todas	 as	 opções	 possíveis	 para
utilizar,	 e	 isso	 pode	 ser	 conferido	 em [Link](https://www.php.net/manual/en/json.constants.php).


```
print	json_encode([
'zcpe'	=>	[
'básico',
'avançado'
	]
],	JSON_HEX_QUOT	|	JSON_HEX_TAG,	2);
```

### JSON DECODE

```
$json	=	'{"zcpe":["básico","avançado"]}';
print	json_decode($json);
```

###  4.7	 SOAP	 (SIMPLE	 OBJECT	 ACCESS PROTOCOL)4.6	JSON	ENCODE,	DECODE


- SOAP é um protocolo para troca de mensagens independentemente da tecnologia;
- SOAP utiliza WSDL (Web Services Description Language) para descrever seus serviços;
- SOAP utiliza apenas XML,

```
$cliente = new SoapClient('http://meu.servico.com?wsdl');
```

```
$cliente	=	new	SoapClient('http://meu.servico.com?wsdl');
$cliente->__getFunctions(); 
```

```
$cliente	=	new	SoapClient('http://meu.servico.com?wsdl');
$cliente->meuMetodo(['parametro1',	'parametro2']);
```

```
$parametros	=	[
'parametro1'	=>	'valor1',
'parametro2'	=>	'valor2',
];
$response	=	$soapClient->__soapCall('meuMetodo',	[$parametros]);
```

```
$soapServer	=	new	SoapServer('servico.wsdl');
```


```
$soapServer	=	new	SoapServer(null,	[
			'uri'	=>	'http://localhost/wsdl'
]);
```

```
class MeuServico	{
public function	ola()
{
return 'Método	ola	do	meu	serviço';
	}
}
$soapServer->setClass('MeuServico');
$soapServer->handle();

```

### 4.8	PHP.INI	E	SOAP
> Configurações feitas no php.ini


```
soap.wsdl_cache_enabled=1 //habilitar cache

soap.wsdl_cache_dir="/tmp" //definir diretório onde cache será armazenado

soap.wsdl_cache_ttl=86400 // definir tempo

soap.wsdl_cache_limit = 5 // tamanho cache
```

### 4.9 REST
> REST (Representational State Transfer)

- GET: leitura de registros
- POST: criar novo recurso
- PUT: atualizar registros
- PATCH: atualizar parte do recurso
- DELETE: deletar registros

### 4.10 REST E PHP

```
$nome = $_GET['nome'];
$nome = $_POST['nome'];

print file_get_contents('php://inout');

```

### 4.11 DATE

> [Link](http://php.net/manual/pt_BR/function.date.php).

```
print date('d/m/Y');

print	date('d/m/Y',	time()	+	86400);	//	adiciona	um	dia	na	data	at
ual


```


<img src="https://github.com/karenyov/certificacaoPHP/blob/main/img/4.11%20-%20Date%20-%201.png" width="450">

### 4.12 A	CLASSE	DATETIME

```
$data	=	new	DateTime();

ATOM	=	"Y-m-d\TH:i:sP"	;
COOKIE	=	"l,	d-M-Y	H:i:s	T"	;
ISO8601	=	"Y-m-d\TH:i:sO"	;
RFC822	=	"D,	d	M	y	H:i:s	O"	;
RFC850	=	"l,	d-M-y	H:i:s	T"	;
RFC1036	=	"D,	d	M	y	H:i:s	O"	;
RFC1123	=	"D,	d	M	Y	H:i:s	O"	;
RFC2822	=	"D,	d	M	Y	H:i:s	O"	;
RFC3339	=	"Y-m-d\TH:i:sP"	;
RSS	=	"D,	d	M	Y	H:i:s	O"	;
W3C	=	"Y-m-d\TH:i:sP"	;


```

```
$hoje			=	new	\DateTime('now');
$amanha	=	$hoje->add(new	\DateInterval('P1D'));
```

### 4.13 DATETIMEIMMUTABLE