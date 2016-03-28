# Padrões de Codificação

## Abertura e Fechando de Tag PHP
Para a abertura e fechamento de tag, deve-se utilizar a notação completa do PHP. 

```
`<?php` // Abertura
      // Conteúdo
      // Fechamento `?>`

// Para imprimir uma variável ou função em uma linha
`<?=` $this->name `?>`
// Ao invés de :
`<?php` echo $this->name; `?>`

// Usar Assim:
`<?=` $this->getName() `?>`
// Ao invés de :
`<?php` echo $this->getName(); `?>`
```

Para os arquivos contendo apenas código PHP deve-se sempre omitir a tag de fechamento do PHP (?>). 

## Indentação
Toda a indentação deve ser feita por tabulações (TAB), nunca por espaços. 
Porém o ajuste até o ponto exato, buscando o alinhamento entre os sinais de iguais deve-se utilizar apenas espaços.

```php
$var       = 'valor';
$variable  = 'valor2'; 
```


## Internacionalização
Para toda impressão de mensagens e conteúdo a ser disponibilizado para o usuário final, deve se fazer uso da função _(‘Valor a ser impresso’). Com essa metodologia iremos possibilitar uma tradução posterior de todas as mensagens.

Exemplo de uso da função de internacionalização:

```php
// Para imprimir na tela a mensagem "Registro inserido com sucesso"
echo _('Registro inserido com sucesso');

// Em momento nenhum deve-se usar uma impressão direta como:
echo 'Registro inserido com sucesso';
```

## Codificação dos Arquivos
Os arquivos devem ser salvos com codificação UTF-8.

## Convenções de Arquivos e Nomes de Classes

Os nomes de arquivos e classes devem ser representados em inglês sempre, salvo em raríssimas excessões explicitamente permitidas pelo coordenador do projeto.

Os nomes de arquivos devem corresponder ao nome de suas classes, que devem ser representados em CamelCase. Então se você possui uma classe AuthManagerClass, o nome do arquivo deve ser AuthManagerClass.php. 

Abaixo estão alguns exemplos de como nomear arquivos para diferentes tipos de classes:

* O Controller `MyCarsController` deverá ser encontrado em um arquivo chamado MyCarsController.php
* O Model `OptionValue` deverá ser encontrado em um arquivo chamado OptionValue.php
* O Helper `BestEverHelper` deverá ser encontrado em um arquivo chamado BestEverHelper.php

### Visibilidade de métodos e variáveis
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

### Controllers
As classes Controllers devem ser escritas no plural, usando o formato CamelCase e terminar com a palavra Controller. `PeopleController` e `LatestArticlesController` são dois exemplos de nomes de controllers que seguem a convenção.

O primeiro método que você pode escrever para um controller é o método index(). Quando uma requisição especifica o controller, mas não a ação, o comportamento padrão do será executar o método index(). Por exemplo, uma requisição para http://www.example.com/apples/ é esperado que seja mapeada para o método index() do controller `ApplesController`.

