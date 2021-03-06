# Padrões de Codificação

<div id='summary'/>

## Sumário

* [Abertura e Fechando de Tag PHP](#open-tag-php)
* [Indentação](#indentacao)
* [Internacionalização](#internationalization)
* [Codificação dos Arquivos](#code-files)
* [Convenções de Arquivos e Nomes de Classes](#conv-files-names)
    * [Models](#conv-files-models)
    * [Banco de Dados](#conv-files-bd)
    * [Controllers](#conv-files-controllers)
    * [Repositories](#conv-files-repositories)
    * [Views](#conv-files-views)
    * [Requests](#conv-files-requests)
    * [Routes](#conv-files-routes)
    * [Tests](#conv-files-tests)
* [Visibilidade de métodos e variáveis](#visibility-methods-and-variables)
* [Variáveis](#variables)
* [Constantes](#constants)
* [Palavras-chave](#key-words)
* [Estruturas de Controle](#control-structures)
* [Declaração Alternativa para o `if`](#alternative-statement-for-if)
* [Colchetes e Parênteses](#brackets-and-parentheses)
* [Concatenação de Strings](#concatenating-strings)
* [Operadores](#operators)
* [Arrays](#arrays)

<div id='open-tag-php'/>

## Abertura e Fechando de Tag PHP  

Para a abertura e fechamento de tag, deve-se utilizar a notação completa do PHP. 

```
<?php // Abertura
      // Conteúdo
      // Fechamento ?>

// Para imprimir uma variável ou função em uma linha
<?= $this->name ?>
// Ao invés de :
<?php echo $this->name; ?>

// Usar Assim:
<?= $this->getName() ?>
// Ao invés de :
<?php echo $this->getName(); ?>
```

Para os arquivos contendo apenas código PHP deve-se sempre omitir a tag de fechamento do PHP (?>). 

<div id='indentacao'/>

## Indentação  

Toda a indentação deve ser feita por tabulações (TAB), nunca por espaços. 
Porém o ajuste até o ponto exato, buscando o alinhamento entre os sinais de iguais deve-se utilizar apenas espaços.

```php
$var       = 'valor';
$variable  = 'valor2'; 
```

<div id='internationalization'/>

## Internacionalização  
Para toda impressão de mensagens e conteúdo a ser disponibilizado para o usuário final, deve se fazer uso da função __(‘Valor a ser impresso’). Com essa metodologia iremos possibilitar uma tradução posterior de todas as mensagens.

Exemplo de uso da função de internacionalização:

```php
// Para imprimir na tela a mensagem "Registro inserido com sucesso"
echo __('Registro inserido com sucesso');

// Em momento nenhum deve-se usar uma impressão direta como:
echo 'Registro inserido com sucesso';
```

<div id='code-files'/>

## Codificação dos Arquivos  

Os arquivos devem ser salvos com codificação UTF-8.

<div id='conv-files-names'/>

## Convenções de Arquivos e Nomes de Classes

Os nomes de arquivos e classes devem ser representados em inglês sempre, salvo em raríssimas excessões explicitamente permitidas pelo coordenador do projeto.

Os nomes de arquivos devem corresponder ao nome de suas classes, que devem ser representados em CamelCase. Então se você possui uma classe AuthManagerService, o nome do arquivo deve ser AuthManagerService.php. 

Abaixo estão alguns exemplos de como nomear arquivos para diferentes tipos de classes:

* O Controller `MyCarsController` deverá ser encontrado em um arquivo chamado MyCarsController.php
* O Model `OptionValue` deverá ser encontrado em um arquivo chamado OptionValue.php
* O Helper `BestEverHelper` deverá ser encontrado em um arquivo chamado BestEverHelper.php

<div id='conv-files-models'/>

### Models

O nome dos Models devem ser escritos no singular e no formato CamelCase. **Car**, **BigCar** e **ReallyBigCar** são todos exemplos de nomes de models que seguem a convenção.

Os Models devem obrigatoriamente extender da classe abstrata `AbstractModel` do core ou do módulo ao qual a classe pertença, assim todas as funções de base serão herdadas.

```php
class Company extends AbstractModel
{

}
```

<div id='conv-files-bd'/>

### Banco de Dados  

Nomes de tabelas correspondentes à models devem ser escritos no plural e usando underscores. As tabelas correspondentes para os models **Car**, **BigCar** e **ReallyBigCar** são respectivamente **cars**, **big_cars** e **really_big_cars**.

Nomes de colunas formadas por mais de uma palavra devem ser separadas usando underscore como em **first_name**.

Chaves estrangeiras em associações do tipo hasMany, belongsTo ou hasOne são reconhecidas por padrão como o nome (no singular) das tabelas relacionadas seguidas por _id. Então, se **Company hasMany (possui muitos) Employee**, a tabela `employees` irá fazer referência a tabela `companies` via chave estrangeira `company_id`. Para tabelas formadas por mais de uma palavra como category_types, a chave estrangeira seria category_type_id.

Tabelas de junções usadas em relacionamentos do tipo Many to Many (HABTM) entre models devem ser nomeadas usando o nome das tabelas dos models referenciados unidas em ordem alfabética e no singular (apple_zebra ao invés de zebras_apples).

Todas as tabelas com que os models interajam junto ao sistema (com exceção das tabelas de junção) requerem uma chave primária para identificar unicamente cada registro.

<div id='conv-files-controllers'/>

### Controllers  

As classes Controllers devem ser escritas no plural, usando o formato CamelCase e terminar com a palavra Controller. `PeopleController` e `LatestArticlesController` são dois exemplos de nomes de controllers que seguem a convenção.

Os Controllers devem obrigatoriamente extender da classe abstrata `AbstractController` do core ou do módulo ao qual a classe pertença, assim todas as funções de base serão herdadas.

```php
class AuthController extends AbstractController
{

}
```
<div id='conv-files-repositories'/>

### Repositories 
// Pendente

<div id='conv-files-views'/>

### Views  
// Pendente

<div id='conv-files-requests'/>

### Requests  
// Pendente

<div id='conv-files-routes'/>

### Routes  
// Pendente

<div id='conv-files-tests'/>

### Tests  
// Pendente

<div id='visibility-methods-and-variables'/>

## Visibilidade de métodos e variáveis  
A visibilidade dos métodos e variáveis devem sempre ser incluídas (public, protected, private).

```php
// Função privada - Disponível apenas para a classe atual
private function getName()
private $name;

// Função protegida - Disponível apenas para a classe atual e para as que a estenderem.
protected function getName()
protected $name;

// Função publica - Disponível para qual chamada dentro da aplicação
public function getName()
public $name;
```

<div id='variables'/>

## Variáveis

Os nomes das variáveis devem ser escritos usando o formato lowerCamelCase e serem precedidas de sua visibilidade. 

Os nomes de variáveis devem descrever seu conteúdo de forma explicita e concisa.

```php
// Exemplo de nomes válidos
protected $name;
protected $cityName;
private $companyAddressNumber;
```

Para variáveis utilizadas para controle em estruturas de loop, deve-se adotar um nome curto, preferencialmente de apenas um único caractere. 

```php
// Exemplo
for ($i = 0; $i < $max; $i++) 
```

Para melhorar a legibilidade do código, ao inicializar variáveis, deve ser fazer uma por linha.

```php
$var = '';
$otherVar = '';
```
<div id='constants'/>

## Constantes  

Para a nomeação de constantes, devem-se utilizar apenas letras maiúsculas e usar o underscore para separação das palavras. Assim como as variáveis seus nomes devem descrever seu conteúdo de forma explicita e concisa.

```php
define('USER_CODE', 100);
define('TEXT_DEFAULT', 'TEXTO');
define('TEMPLATE_PATH', '/home/templates/');
```

<div id='key-words'/>

## Palavras-chave  
As Palavras-chave como `true`, `false`, `null`, `as`, etc devem ser representadas em letras minúsculas. 
O mesmo vale para os tipos primitivos como `array`, `integer`, `string`.

```php
$variable = true;
$variable = false;
$variable = null;

foreach ($array as $key => $value)

public function myFunction(array $var)
```

<div id='control-structures'/>

## Estruturas de Controle  

As palavras-chave da estrutura, como `if`, `for`, `foreach`, `while`, `switch` devem ser seguidas por um espaço, e logo após, entre parênteses, os argumentos. As chaves devem ser colocadas na mesma linha após um espaço.

```php
if ($arg === true) {
    // conteúdo
}
elseif ($arg === null) {
    // conteúdo
}
else {
    // conteúdo
}
```
> Sempre que possível evitar o uso do else

```php
foreach ($array as $key => $value) {
    // conteúdo do looping
}

for ($i = 0; $i < $max; $i++) {
    // conteúdo do looping
}

while ($i < $max) {
    // conteúdo do looping
}

do {
    // conteúdo do looping
} while ($i < $max);
```

```php
switch ($var) {
    case 'a':
        // conteúdo
    break;
    case 'b':
        // conteúdo
    break;
    default:
        // conteúdo
    break;
}
```

<div id='alternative-statement-for-if'/>

## Declaração Alternativa para o `if`  

Em alguns momentos, o uso do if em sua estrutura completa  é um pouco demais para um código de atribuição condicional simples ou chamada de função. Nesses casos, podemos usar a lógica de execução do PHP para usar uma sintaxe mais curta. 

Não use está síntese quando houver mais que duas instruções condicionais.

```php
// Ao invés de usar 
if (empty($var)) {
    $var = 'Vazia';
}
else {
    $var = 'Com conteúdo';
}

// Use
$var = empty($var) ? 'Vazia' : 'Com conteúdo';

// Outros Exemplos
$var = isset($otherVar) ? $otherVar : 'Default Value';
$var = (isset($otherVar) && $otherVar > 0) ? $otherVar : 'Default Value';
```

<div id='brackets-and-parentheses'/>

## Colchetes e Parênteses  

Não se deve usar espaços desnecessários antes ou depois de Colchetes e Parênteses. 

```php
$array = [1, 2, 3, 4];
$array['index'] = 'something';

for ($i = 0; $i < $max; $i++)
```

<div id='concatenating-strings'/>

## Concatenação de Strings  

As aspas simples são preferíveis às aspas duplas.
Não deve haver espaços onde se precede a símbolo de concatenação (`.`), apenas separando a variável a ser concatenada.


```php
// Exemplos a serem seguidos:
$string = 'my string'. $var .'the rest of my string';
$string = 'my string'. $var . $secondVar .'the rest of my string';

// Abaixo exemplos aos quais devem ser evitados:
$string = 'my string'.$var.'the rest of my string';
$string = 'my string' . $var . 'the rest of my string';
$string = 'my string'.$var.$secondVar.'the rest of my string';
```

<div id='operators'/>

## Operadores  

```php
$variable = 'something';

// Espaço antes e depois dos operadores lógicos
if ($variable == 'something')

// Espaço antes e depois dos operadores matemáticos
$variable = $someVar + $otherVar;

// Sem espaço antes do incremento
$variable++;

//Sem espaço depois do incremento
++$variable;
```

<div id='arrays'/>

## Arrays  

Para representar uma array deve-se usar a nova notação do php baseada em colchetes, como se vê nos exemplos abaixo.

```php
// Formato de declaração preferencial
$array = [
   'always_load' => [
       'packages' => [
           'orm',
           'package' => '/my/special/package.php'
       ]
   ]
];


// Exemplo de formato que deve ser evitado:
$array = array (
   'always_load' => array (
       'packages' => array (
           'orm',
           'package' => '/my/special/package.php'
       )
   )
);

// Exemplo de formato que não deve ser usado
$array = [ 'always_load' => [ 'packages' => [ 'orm', 'package' => '/my/special/package.php' ] ];
```
