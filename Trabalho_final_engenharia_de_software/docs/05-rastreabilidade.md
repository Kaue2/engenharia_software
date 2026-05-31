# 5. Matriz de Rastreabilidade

A tabela abaixo consolida a rastreabilidade entre os requisitos do sistema (Histórias de Usuário mapeadas no Trabalho 2) e todos os artefatos de modelagem estrutural, de dados, comportamental e de qualidade gerados neste documento. Isso garante que nenhuma classe, tabela ou fluxo foi criado sem justificativa de negócio.

| Fatia | História(s) (T2) | Classes envolvidas | Entidades MER | Diagrama comportamental | Casos de teste |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Fatia 1** (Solicitar Viagem) | US-CLI-004, US-CORE-012, US-CORE-015 | Cliente, Motorista, Viagem, CalculadorTarifa, CalculadorTarifaDinamica | usuario, cliente, motorista, viagem | Sequência (Seção 3.1) | TC-FATIA1-01, TC-FATIA1-02 |
| **Fatia 2** (Cadastro em Frota) | US-MOT-008, US-FRO-022 | Motorista, AdministradorFrota, Frota, SolicitacaoVinculo | usuario, motorista, administrador_frota, frota, solicitacao_vinculo | Estados (Seção 3.2) | TC-FATIA2-01, TC-FATIA2-02 |
| **Fatia 3** (Cadastro de Admin) | US-FRO-001 | AdministradorFrota, Frota | usuario, administrador_frota, frota | Sequência (Seção 3.3) | TC-FATIA3-01, TC-FATIA3-02 |

> **Nota de Validação:** A classe abstrata `Usuario` está implícita nas três fatias estruturais, sendo resolvida no banco de dados pela tabela `usuario` somada à respectiva tabela filha de cada ator.
