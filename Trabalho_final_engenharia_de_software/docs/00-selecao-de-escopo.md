## Justificativa do escopo

Neste documento serão modelados os fluxos de:

* Cliente solicita uma viagem no aplicativo
* Motorista se cadastra em uma frota
* Um adminstrador de frota se cadastra no sistema


# 0. Seleção de Escopo

Neste trabalho, optou-se por não modelar a totalidade do sistema de gerenciamento de frotas e corridas. Em vez
disso, o escopo foi delimitado a três fatias verticais representativas que atravessam os principais componentes
da arquitetura, permitindo uma análise aprofundada das regras de negócio, interações de atores e transições de
estados críticos.

## Subsistemas e Atores Identificados (Recapitulação)

Para contextualizar as fatias, o sistema divide-se essencialmente em três grandes ecossistemas:

* **Core de Viagens:** Responsável pelo matching, rotas, cálculo de tarifas e tracking em tempo real. (Atores: Cliente, Motorista)
* **Gestão Corporativa (Frotas):** Responsável pelo vínculo de motoristas a empresas, gerenciamento de veículos e permissões. (Atores: Administrador de Frota, Motorista)
* **Acesso & Cadastro:** Validação de perfis e segurança. (Atores: Cliente, Motorista, Administrador de Frota)

---

## Fatias Selecionadas

### Fatia 1 — Cliente solicita uma viagem no aplicativo

* **Histórias cobertas:** US-CLI-004 ("Como cliente, quero solicitar uma viagem informando origem e destino para me locomover"), US-CORE-012 ("Como motorista, quero receber ofertas de viagens próximas para aceitar ou recusar"), US-CORE-015 ("Como sistema, devo calcular o valor estimado da viagem com base na distância e demanda").
* **Por que é representativa:** É o Must Have absoluto do produto. Atravessa os subsistemas de Localização (geolocalização), Core de Viagens (algoritmo de alocação de motoristas) e Pagamentos. Envolve caminhos de exceção complexos, como nenhum motorista aceitar a corrida ou o cliente cancelar antes do aceite.
* **O que esperamos aprender:** Como modelar interações assíncronas e distribuídas em tempo real (provável Diagrama de Sequência), lidando com concorrência (múltiplos motoristas recebendo a mesma oferta) e gerenciamento de timeouts.

### Fatia 2 — Motorista se cadastra em uma frota

* **Histórias cobertas:** US-MOT-008 ("Como motorista autônomo, quero solicitar vínculo a uma frota existente para trabalhar sob as regras dela"), US-FRO-022 ("Como administrador de frota, quero aprovar ou rejeitar a associação de um motorista para manter o controle da minha equipe").
* **Por que é representativa:** Envolve a interação direta entre dois atores humanos distintos com interesses conectados. Possui regras de negócio corporativas importantes (como checagem de documentos, limites de motoristas por frota e regras de comissão interna da própria frota).
* **O que esperamos aprender:** Como representar um ciclo de vida de vínculo que possui estados claros (Pendente, Aprovado, Rejeitado, Desvinculado) e regras de validação cruzada entre entidades de domínios diferentes.

### Fatia 3 — Um administrador de frota se cadastra no sistema

* **Histórias cobertas:** US-FRO-001 ("Como gestor de uma empresa de transportes, quero cadastrar minha frota informando CNPJ e dados corporativos para operar na plataforma").
* **Por que é representativa:** Embora pareça um cadastro simples à primeira vista, não se trata de um CRUD comum (usuário final). Exige validações severas de regras de negócio de backoffice (validação de CNPJ na Receita, checagem de elegibilidade da empresa e ativação de conta jurídica).
* **O que esperamos aprender:** Como isolar a lógica de parametrização de uma conta corporativa de alta hierarquia no sistema, mapeando heranças ou composições de perfis organizacionais e fluxos de segurança baseados em papéis (RBAC).

---

## Cobertura dos Critérios Obrigatórios

| Critério | Fatia 1 (Solicitar Viagem) | Fatia 2 (Cadastro em Frota) | Fatia 3 (Cadastro de Admin) |
| :--- | :---: | :---: | :---: |
| **Pelo menos 1 Must Have** | ✅ Sim | ⚪ Should Have | ⚪ Should Have |
| **Mais de um subsistema/ator** | ✅ Sim | ✅ Sim | ⚪ Foco em Backoffice |
| **Regras não-triviais** | ✅ Sim | ✅ Sim | ✅ Sim |

---

## O que fica de fora (e por quê)

Para garantir a profundidade exigida, as seguintes funcionalidades mapeadas anteriormente não serão modeladas:

1. **Autenticação padrão (Login/Logout/Recuperação de senha):** Segue padrões universais de mercado e não adiciona complexidade ou regras específicas ao domínio de transporte e frotas.
2. **Avaliação mútua (Estrelas/Comentários pós-corrida):** É um fluxo isolado e predominantemente CRUD, cuja persistência e lógica não desafiam o design arquitetural neste momento.
3. **Histórico financeiro e relatórios de faturamento da frota:** Embora altamente críticos para o negócio real, são componentes puramente de leitura de dados persistidos, sem transições de estado complexas na camada de domínio.
