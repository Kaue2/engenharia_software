# 3.1 Modelagem Comportamental - Fatia 1

**Fatia:** Cliente solicita uma viagem no aplicativo

**Justificativa da escolha do diagrama:** Escolhemos o **Diagrama de Sequência** porque esta fatia envolve alta coordenação síncrona e assíncrona entre o ator (Cliente), o backend (Core de Viagens), os serviços de cálculo e o segundo ator (Motorista). A sequência temporal e os fluxos alternativos (aceite vs. recusa) são críticos para entender esse Must Have.

## Diagrama de Sequência: Solicitação de Viagem

```mermaid
sequenceDiagram
    autonumber
    actor C as Cliente
    participant API as API Core (Backend)
    participant Tarifa as CalculadorTarifaDinamica
    actor M as Motorista

    C->>API: solicitarViagem(origem, destino)
    activate API
    API->>Tarifa: calcular(origem, destino)
    activate Tarifa
    Tarifa-->>API: valorEstimado
    deactivate Tarifa
    API-->>C: exibirDetalhesViagem(valorEstimado)
    deactivate API
    
    C->>API: confirmarViagem()
    activate API
    API->>API: criarRegistroViagem(status=BUSCANDO)
    API->>M: notificarOferta(viagemId, detalhes)
    
    alt Motorista aceita a corrida
        M->>API: responderOferta(viagemId, aceito=true)
        API->>API: atualizarStatus(status=ACEITA, motoristaId)
        API-->>C: notificarMotoristaEncontrado(dadosMotorista)
    else Motorista recusa ou Timeout
        M->>API: responderOferta(viagemId, aceito=false)
        API->>API: atualizarStatus(status=CANCELADA)
        API-->>C: erroNotificacao("Nenhum motorista disponível no momento")
    end
    deactivate API
```
