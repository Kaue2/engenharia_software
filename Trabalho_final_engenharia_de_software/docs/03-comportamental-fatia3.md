# 3.3 Modelagem Comportamental - Fatia 3

**Fatia:** Um administrador de frota se cadastra no sistema

**Justificativa da escolha do diagrama:** Retomamos o **Diagrama de Sequência** nesta fatia pois o foco arquitetural do cadastro corporativo está na integração entre componentes de fronteira. A complexidade não reside nos estados da frota, mas sim na orquestração: o sistema precisa validar dados em uma API externa (Receita Federal), instanciar o perfil corporativo e persistir no banco de dados com tratamento de exceções.

## Diagrama de Sequência: Cadastro Corporativo

```mermaid
sequenceDiagram
    autonumber
    actor AF as Admin de Frota
    participant API as API de Cadastro
    participant RFB as API Receita Federal (Externa)
    participant BD as Banco de Dados
    
    AF->>API: cadastrarFrota(cnpj, razaoSocial, emailCorporativo)
    activate API
    
    API->>RFB: consultarSituaçãoCNPJ(cnpj)
    activate RFB
    
    alt CNPJ Inválido ou Inativo
        RFB-->>API: 404 Not Found / Status Inativo
        API-->>AF: erroValidacao("CNPJ inválido ou inativo para operação")
    else CNPJ Válido e Ativo
        RFB-->>API: 200 OK (Dados da Empresa)
    end
    deactivate RFB
    
    opt Se CNPJ Válido
        API->>BD: salvarUsuario(AdministradorFrota)
        API->>BD: salvarFrota(Frota)
        activate BD
        BD-->>API: confirmacaoTransacao
        deactivate BD
        API-->>AF: sucesso("Conta corporativa criada com sucesso")
    end
    deactivate API
```
