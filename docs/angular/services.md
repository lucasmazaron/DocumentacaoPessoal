# Serviços

!!! question "O que é um serviço?"
    São classes comuns em angular que você pode usar para injetar em componentes ou em outros serviços.  
    Geralmente usados para encapsular o acesso a API de Backend.  
    Podem ser **Singletons**. Ótimos para guardar dados compartilhados por toda a aplicação ou por parte dela.

!!! important "Importante!!!"
    São 3 os escopos que você pode usar para declararum serviço:  

      * **Módulo** - Todo serviço declarado na lista de providers do módulo raíz fica disponivel para ser injetado por todas as classes declaradas nesse mesmo módulo. Isso inclui componentes e outros serviços também. Todos compartilharão a mesma instância desse serviço;

      * **Componente e seus filhos** - Fica disponível apenas ao componente e seus filhos;

      * **Somente Componente - viewProviders[]** - Apenas ao componente.  

!!! tip "Dica"
    Serviços também pode solicitar injeção de outros serviços.  
    Para isso, eles devem usar o decorator **@injectable()**.

```typescript
  import { injectable } from '@angular/core'
  import { Http } from '@angular/core'

  @Injectable()

  export class MyService{

    constructor(private http: Http){// Here
    }

    list(){
      return this.http.get('url')
    }
  }
```

!!! warning "Atenção"
    **@Injectable()** não é necessário para que seu serviço seja injetado em outro objeto! Somente para receber.
