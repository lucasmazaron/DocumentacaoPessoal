# Operador de Navegação Segura

* A interrogação (?), nas expressões angular, serve para dizer ao Angular que se caso a expressão retorne undefined, não tente ler o atributo.

**Exemplo:**  
```html
  <div>
    Student: {{student?.name}} <!-- -->
    <div *ngIf="student?.isJedi">
      jedi Temple: {{student?.temple}}
    </div>
  </div>
```
