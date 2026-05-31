# 3.2 Modelagem Comportamental - Fatia 2

**Fatia:** Motorista se cadastra em uma frota

**Justificativa da escolha do diagrama:** Escolhemos o **Diagrama de Estados** porque a essência dessa fatia não é a troca de mensagens imediatas, mas sim o ciclo de vida da entidade `SolicitacaoVinculo`. Há transições críticas acionadas por eventos (aprovação ou rejeição) e regras de negócio claras que governam a mudança de estado dessa associação.

## Diagrama de Estados: Ciclo de Vida do Vínculo

```mermaid
stateDiagram-v2
    [*] --> Pendente : Motorista solicita vínculo
    
    Pendente --> Aprovado : Admin avalia / aprovar() [Docs Válidos]
    Pendente --> Rejeitado : Admin avalia / rejeitar() [Inconsistência]
    
    state Aprovado {
        [*] --> Ativo
        Ativo --> Suspenso : [Motorista inativo > 30 dias]
        Suspenso --> Ativo : [Motorista retorna]
    }
    
    Aprovado --> Desvinculado : Admin remove / Motorista sai
    
    Rejeitado --> [*]
    Desvinculado --> [*]
```
