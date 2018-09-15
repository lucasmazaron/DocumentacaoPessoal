# Programação Reativa (Reactive Programming)

!!! question "Como funciona?"
    Um evento acontece e os que estão interessados são notificados e reagem a ele.  
    Baseado em um padrão bem comum chamado **OBSERVER**. Nesse padrão, você terar o *Observer* que é o foco do interesse e você terá outros objetos que são os interessados em alguma mudança desse primeiro objeto que são os *listeners*.  
    Os **listeners** se inscrevem esperando uma mudança (evento). Quando o *evento* acontece, o *listener*, executa uma ação.  

!!! tip "Dica"
    É portanto a combinação de dois padrões.  
    * **ITERATOR** - Porque vai de item a item;    
    * **OBSERVER** - Porque notifica os *listeners* interessados.
