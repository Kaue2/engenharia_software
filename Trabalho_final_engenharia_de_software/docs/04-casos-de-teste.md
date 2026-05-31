# 4. Casos de Teste das Fatias Modeladas

Este documento detalha os cenários de teste para as fatias verticais selecionadas, seguindo as diretrizes do padrão IEEE-830. Para cada fatia, foi desenhado um cenário de "caminho feliz" e um cenário de "fronteira/exceção", visando validar regras de negócio críticas e transições de estado complexas.

## Fatia 1: Cliente solicita uma viagem no aplicativo

### Caso de Teste 1.1: Caminho Feliz - Viagem aceita pelo motorista
| Campo | Conteúdo |
| :--- | :--- |
| **ID** | TC-FATIA1-01 |
| **Fatia / História** | Fatia 1 — US-CLI-004 (Solicitar viagem) e US-CORE-012 (Aceitar oferta) |
| **Pré-condições** | Cliente autenticado; Motorista autenticado, online e com status `ATIVO` na mesma região. |
| **Dados de entrada** | Origem: "Av. Paulista, 1000", Destino: "Parque Ibirapuera". Clique em "Confirmar Viagem" e, no app do motorista, clique em "Aceitar". |
| **Passos** | 1) Cliente insere os endereços e confirma; 2) Sistema calcula tarifa e emite oferta; 3) Motorista recebe o card de oferta; 4) Motorista clica em "Aceitar". |
| **Resultado esperado** | A viagem é confirmada, o status muda para `ACEITA` e o cliente recebe os dados do motorista. |
| **Critério de aprovação** | Registro de viagem criado na base de dados, coluna `status` = 'ACEITA' e coluna `id_motorista` preenchida com o ID correto. |
| **Severidade em caso de falha** | Crítica |

### Caso de Teste 1.2: Caminho de Erro (Fronteira) - Timeout de motoristas
| Campo | Conteúdo |
| :--- | :--- |
| **ID** | TC-FATIA1-02 |
| **Fatia / História** | Fatia 1 — US-CORE-012 (Oferta de viagem) |
| **Pré-condições** | Cliente autenticado; Nenhum motorista disponível ou todos recusam a corrida. Tempo limite (timeout) do sistema configurado para 30 segundos. |
| **Dados de entrada** | Origem e Destino válidos. Nenhuma interação dos motoristas durante 30 segundos. |
| **Passos** | 1) Cliente solicita a viagem; 2) Ofertas são disparadas; 3) Aguardar o decurso do tempo de 30 segundos sem respostas. |
| **Resultado esperado** | O sistema deve cancelar a busca automaticamente e notificar o cliente sobre a indisponibilidade. |
| **Critério de aprovação** | (a) Status da viagem alterado para `CANCELADA`; (b) Mensagem "Nenhum motorista disponível no momento" exibida no app do cliente. |
| **Severidade em caso de falha** | Alta |

---

## Fatia 2: Motorista se cadastra em uma frota

### Caso de Teste 2.1: Caminho Feliz - Vínculo aprovado
| Campo | Conteúdo |
| :--- | :--- |
| **ID** | TC-FATIA2-01 |
| **Fatia / História** | Fatia 2 — US-FRO-022 (Aprovar/rejeitar vínculo) |
| **Pré-condições** | Solicitação de vínculo do motorista criada e com status `PENDENTE`. Admin da frota autenticado. |
| **Dados de entrada** | Seleção da solicitação na lista e clique no botão "Aprovar". |
| **Passos** | 1) Admin acessa o painel de solicitações da frota; 2) Abre os detalhes do motorista; 3) Clica em "Aprovar". |
| **Resultado esperado** | O vínculo é efetivado e o motorista passa a fazer parte da frota. |
| **Critério de aprovação** | O registro na tabela `solicitacao_vinculo` tem o status alterado para `APROVADO`. Motorista recebe notificação de sucesso. |
| **Severidade em caso de falha** | Alta |

### Caso de Teste 2.2: Transição Crítica de Estado (Fronteira) - Aprovar vínculo já rejeitado
| Campo | Conteúdo |
| :--- | :--- |
| **ID** | TC-FATIA2-02 |
| **Fatia / História** | Fatia 2 — US-FRO-022 (Aprovar/rejeitar vínculo) |
| **Pré-condições** | Solicitação de vínculo específica encontra-se com o status `REJEITADO` no banco de dados. |
| **Dados de entrada** | Disparo de requisição forçada (ex: duplo clique ou chamada direta à API) enviando a instrução de aprovação para este ID. |
| **Passos** | 1) Enviar requisição HTTP POST/PUT para a rota de aprovação do vínculo informando o ID da solicitação que já está rejeitada. |
| **Resultado esperado** | O sistema deve bloquear a ação, pois a transição de `REJEITADO` para `APROVADO` é inválida no diagrama de estados. |
| **Critério de aprovação** | (a) A API deve retornar erro 400 (Bad Request) ou 422 (Unprocessable Entity) com mensagem "Transição de estado inválida"; (b) O status no banco permanece `REJEITADO`. |
| **Severidade em caso de falha** | Crítica |

---

## Fatia 3: Um administrador de frota se cadastra no sistema

### Caso de Teste 3.1: Caminho Feliz - Cadastro de frota válido
| Campo | Conteúdo |
| :--- | :--- |
| **ID** | TC-FATIA3-01 |
| **Fatia / História** | Fatia 3 — US-FRO-001 (Cadastrar frota corporativa) |
| **Pré-condições** | Ambiente do sistema operante. API da Receita Federal (ou mock) online e operante. |
| **Dados de entrada** | CNPJ: "12.345.678/0001-99" (cadastrado e ATIVO na Receita). Email: "contato@frota.com". |
| **Passos** | 1) Usuário acessa tela de cadastro corporativo; 2) Preenche o formulário com o CNPJ; 3) Clica em "Cadastrar conta". |
| **Resultado esperado** | O sistema valida o CNPJ, processa a criação da entidade corporativa e o perfil de administrador, vinculando ambos. |
| **Critério de aprovação** | Inserção bem-sucedida confirmada nas tabelas `administrador_frota` e `frota` com a respectiva chave estrangeira associada. |
| **Severidade em caso de falha** | Crítica |

### Caso de Teste 3.2: Caminho de Erro (Fronteira) - CNPJ inativo na Receita Federal
| Campo | Conteúdo |
| :--- | :--- |
| **ID** | TC-FATIA3-02 |
| **Fatia / História** | Fatia 3 — US-FRO-001 (Cadastrar frota corporativa) |
| **Pré-condições** | Mock da integração com a API da Receita Federal configurado para devolver resposta com situação cadastral "BAIXADA" ou "INAPTA". |
| **Dados de entrada** | CNPJ com restrição inserido no formulário de cadastro corporativo. |
| **Passos** | 1) Usuário acessa tela de cadastro corporativo; 2) Preenche o formulário com o CNPJ inativo; 3) Clica em "Cadastrar conta". |
| **Resultado esperado** | O sistema aborta o cadastro e impede a inserção de lixo na base de dados, informando o erro de regularidade. |
| **Critério de aprovação** | (a) Nenhum registro persistido no banco de dados; (b) Tela exibe mensagem "CNPJ inválido ou inativo para operação. Verifique junto à Receita Federal." |
| **Severidade em caso de falha** | Alta |
