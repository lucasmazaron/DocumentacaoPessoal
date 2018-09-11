# Componentes
`Pequenas partes dependentes reusáveis. Elementos personalizados`  
`Dispostos em estrutura de *arvore*, onde na raíz há sempre um component parent seguido dos seus filhos.`  

* *Classes* com um determinado ciclo de vida;  
* *Template* para determinar a aparência;  
* *Selector* (tag) para ser usado por outras partes da aplicação.  

## Decorator `@Component`

```typescript
  @Component({
    selector: 'prefix-namecomponent',
    templateUrl: './myfirst.component.html' // pode ser arquivo externo ou direto usando o comando template: de vez de templateUrl:
    })
```

## Generate Component

`Para gerar novo component na aplicação`

```typescript
  ng generate component name --spec=false
  // ou
  ng g c name --spec=false
```

`--spec= determina se irá gerar ou não arquivos de testes`


## Property Binding
`Linkar valor de uma propriedade de um elemento a uma expressão angular.`  
`A atualização é sempre em um sentido. ONE-WAY BINDING - COMPONENT => TEMPLATE`

* Sintaxe:

```typescript
  // No componente
  user = {name: 'Luke Skywalker'}
```

```HTML
  <!-- no template do componente -->
  <input type="text" [value]="user.name">
```

## DOM (Document Object Model) - O que são propriedades do DOM?
`Propriedades identicas aos atributos HTML. Porém possui propriedades extras`

```typescript
  //in component
  user = {name: 'Luke Skywalker',
          isJedi: true}
```

```HTML
  <!-- in template -->
  <input type="text" [value]="user.name">
  <div [hidden]="!user.isJedi">
    location of the jedi temple
  </dib>
```

## Passando dados para os componentes
### Usando Decorator `@Input`
`As propriedades dos componentes são publicas porém, parar passar dados, devemos indicar ao Angular qual deles podem receber dados dos component parent através de property binding.`

* Primeira forma:

```typescript
  import { Component, Input } from '@angular/core'

  @Component({
    selector: 'mt-header',
    template: '<h1>{{title}}</h1>'
  })
  // Por padrão, nome do atributo exposto  
  export class HeaderComponent {
    @input() title: string
  }

  //Expor com outro nome
  export class HeaderComponent {
    @input('value') title: string //@input('nome a ser exposto')
  }
```  

```HTML
  <!-- usando o header -->
  <mt-header title="Minha APP"></mt-header>

  <!-- utilizando com template Interpolation -->
  <mt-header title="{{isJedi ? 'Jedi' : 'Sith'}}"></mt-header>

  <!--Property Binding -->
  <mt-header [title]="isJedi ? 'Jedi' : 'Sith'"></mt-header>

  <!-- usando o nome definido em @Input -->
  <mt-header value="Minha APP"></mt-header>
```
`Sempre que for passar um valor que não é String, utilizar property binding`
