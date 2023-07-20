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
