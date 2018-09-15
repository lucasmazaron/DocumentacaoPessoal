# Diretivas
---

!!! question "Para que servem?"
    Serve para adicionar um comportamento a um elemento do DOM. Não possui template.

**Existem três tipos de diretivas**  

* Componentes - Que são as mais comuns;
* Estruturais - Mudam o template/estrutura do DOM. Ex: ngFor - ngIf;  
* Atributos - Associa um atributo a um elemento do DOM.  

## Estruturais  

!!! question "Como funcionam?"
    Trabalham com padrão de templates do HTML5.
    O * (asterisco) é a forma abreviada da diretiva para que não precise digitar o elemento template.

### ngIf

!!! question "O Que faz?"
    Renderiza ou não um conteúdo caso a condição for verdadeira.

```html
  <input type="text" [value]="user.name">
  <div *ngIf="user.isJedi">
    location of the jedi template
  </div>
```

### ngFor

!!! question "O Que faz?"
    Repete o conteúdo de um elemento para cada item de uma coleção de objetos.

```html
  <ul>
    <li *ngFor="let user of users">{{user.name}}</li>
  </ul>
```
!!! tip "Dica"
    Você pode declarar uma variável para indice(Index começa em 0):

        <ul>
          <li *ngFor="let user of users; let i=index">
            {{i+1}} - {{user.name}}
          </li>
        </ul>


### ngSwitch

```html
  <div [ngSwitch]="profile">
    <p *ngSwitchCase="root">You can read & write</p>
    <p *ngSwitchCase="user">You can read</p>
    <p *ngSwitchDefault>go back, please!</p>
  </div>
```
