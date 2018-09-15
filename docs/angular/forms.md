# Formulários

!!! tip "Dica"
    Ao criar um `<form>` não esquecer de desabilitar a validação de formulários do browser.

        <form novalidade></form>

    Pois assim, todos os usuários terão a mesma experiência, mesmo com browsers diferentes.  
    Colocando **novalidate** delegamos essa validação para o angular, deixando o procedimento de validação uniforme.  

## Validações  

Diretiva `NGMODEL` disponibiliza os seguintes status que podem ser verificados para dar feedback ao usuário:  
> * **Valid|Invalid** - Se o valor do campo está de acordo com as regras de validação;  
> * **Pristine|Dirty** - *Pristine* é o estado inicial do campo/form. Uma vez que o usuário altera o valor do campo, ele se torna *dirty* e não volta mais;  
> * **Untouched|Touched** - A diferença entre *Pristine|Dirty* e *Untouched|Touched* é que para o alterar o status de *pristine*, é necessário alterar o valor, já *untouched* somente entrar no campo.  

Para saber o estado que o campo se encontra, precisamos obter uma referência para a diretiva `NGMODEL`do campo.  

!!! example "Exemplo"

```html
<form>
  <input name="name" [ngModel]="username" #ipt="ngModel" required minlength="5">
  <span *ngIf="ipt.invalid">Nome Inválido</span>
</form>
```

As validações que podemos usar em um campo são:  

> * **Required** - Caso um campo seja obrigatório;  
> * **Pattern - Regex** - Recebe um padrão de expressão regular
> * **Min e max length** - Determinar tamanho máximo ou mínimo do campo.
