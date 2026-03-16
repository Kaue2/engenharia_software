# Documento de Visão do Produto: CityGo

## 1. Visão Geral do Produto

### 1.1 Declaração do Problema e Oportunidade de Negócio
**O Problema:** Nos grandes centros urbanos, a mobilidade é um desafio constante. Muitas pessoas necessitam de deslocamentos rápidos e práticos, mas esbarram na ineficiência do transporte público e no alto custo de manter um veículo próprio. Em contrapartida, motoristas e proprietários de frotas (cooperativas, locadoras) buscam oportunidades de rentabilizar seus veículos ociosos de forma flexível. Segundo dados de institutos de pesquisa em mobilidade urbana [pesquisa mobilidade](https://nossasaopaulo.org.br/wp-content/uploads/2019/01/Viver-em-SP-2024_Mobilidade_resumida.pdf), o tempo de deslocamento e a busca por transportes alternativos crescem a cada ano no Brasil.

**A Oportunidade:** O CityGo atua exatamente nessa lacuna, operando como uma ponte entre passageiros e frotas organizadas. Diferente de aplicativos convencionais focados apenas no motorista individual, o CityGo cria um modelo de negócio B2B2C, permitindo que empresas de transporte e cooperativas gerenciem suas equipes e áreas de atuação de forma centralizada, enquanto oferece ao usuário final uma viagem segura e rastreável.

### 1.2 Perspectiva do Produto
O CityGo insere-se no mercado de aplicativos de *ride-hailing* (transporte por aplicativo), competindo por uma fatia do mercado de mobilidade urbana. 
* **Público-alvo:** Passageiros que buscam transporte ágil; Administradores de Frotas (cooperativas, empresas de táxi/locadoras); e Motoristas vinculados a essas frotas.
* **Proposta de Valor:** Para o passageiro, a garantia de uma viagem segura com preço e tempo estimados previamente. Para as frotas, um sistema completo de gestão de motoristas, veículos, rastreamento de ganhos e definição de praças de atuação.

### 1.3 Capacidades do Produto
O sistema oferece as seguintes capacidades principais:
* **Gestão de Frotas:** Cadastro e controle de veículos, motoristas e relatórios financeiros por parte dos administradores.
* **Match de Viagens:** Algoritmo que conecta a solicitação de origem/destino do passageiro ao motorista da frota mais próxima disponível.
* **Acompanhamento em Tempo Real:** Integração com mapas para cálculo de rotas, estimativa de tempo e acompanhamento via GPS.
* **Pagamento Automatizado:** Processamento seguro do pagamento ao final da corrida e emissão de recibos.
* **Sistema de Avaliação:** Avaliação mútua para garantir a segurança e a qualidade da plataforma.

*(Nota: [Inserir aqui os Wireframes de baixíssima resolução dos fluxos principais, como a tela de pedir corrida do passageiro e a tela de aceitar corrida do motorista])*

---

## 2. Descrição dos Usuários

| Atributo | Descrição |
| :--- | :--- |
| **Usuário ID** | USER-001 |
| **Nome do Perfil** | Administrador da Frota |
| **Descrição** | Responsável por gerenciar a cooperativa/empresa de transporte na plataforma. |
| **Experiência Técnica** | Média; familiaridade com painéis de gestão e relatórios. |
| **Frequência de Uso** | Diária, para monitoramento de frota e repasses. |
| **Principais Objetivos** | Cadastrar veículos/motoristas, definir regiões de atuação e acompanhar o faturamento da frota. |
| **Desafios** | Manter a frota ativa e acompanhar o desempenho da equipe em tempo real. |
| **Restrições** | Tem acesso apenas aos dados da sua própria frota e de seus respectivos motoristas. |
| **Requisitos Principais** | Painel de controle de frota, relatórios de viagens e gestão de pagamentos. |

| Atributo | Descrição |
| :--- | :--- |
| **Usuário ID** | USER-002 |
| **Nome do Perfil** | Motorista |
| **Descrição** | Condutor do veículo vinculado a uma frota cadastrada. |
| **Experiência Técnica** | Baixa a Média; uso cotidiano de smartphones e apps de GPS. |
| **Frequência de Uso** | Alta/Contínua durante a jornada de trabalho. |
| **Principais Objetivos** | Receber solicitações de viagem, navegar até o destino e visualizar seus ganhos. |
| **Desafios** | Lidar com instabilidades de GPS e trânsito intenso. |
| **Restrições** | Visualiza apenas as informações da corrida atual. Não tem acesso ao histórico completo do passageiro. |
| **Requisitos Principais** | Botão de online/offline, mapa integrado e aceite rápido de corridas. |

| Atributo | Descrição |
| :--- | :--- |
| **Usuário ID** | USER-003 |
| **Nome do Perfil** | Passageiro |
| **Descrição** | Cliente final que necessita de locomoção urbana. |
| **Experiência Técnica** | Baixa; usuário comum de aplicativos de celular. |
| **Frequência de Uso** | Variável (ocasional a diária). |
| **Principais Objetivos** | Solicitar transporte rápido, seguro e saber o preço antecipadamente. |
| **Desafios** | Encontrar motoristas disponíveis rapidamente em horários de pico. |
| **Restrições** | Acessa apenas seu próprio histórico e dados da corrida solicitada. |
| **Requisitos Principais** | Inserção fácil de origem/destino, estimativa de preço e cadastro de cartão. |

---

## 3. Restrições do Projeto e do Produto

| Campo | Descrição |
| :--- | :--- |
| **Restrição ID** | RES-TEC-001 |
| **Título** | Dependência de Serviços de Terceiros (Mapas e Pagamentos) |
| **Descrição** | O sistema depende obrigatoriamente da integração com APIs externas de geolocalização/mapas e gateways de pagamento. |
| **Origem** | Arquitetura do Sistema |
| **Critérios de verificação** | O sistema não pode processar viagens se a API de mapas estiver indisponível. |
| **Relacionamento** | Relaciona-se com os Requisitos Funcionais de rotas (RF04, RF06) e pagamentos (RF08). |

| Campo | Descrição |
| :--- | :--- |
| **Restrição ID** | RES-LEG-001 |
| **Título** | Proteção de Dados e Privacidade |
| **Descrição** | O sistema deve mascarar os dados pessoais entre motoristas e passageiros (ex: número de telefone real), em conformidade com leis de proteção de dados. |
| **Origem** | Legislação vigente (LGPD) |
| **Critérios de verificação** | Auditoria de segurança e testes de intrusão no banco de dados. |
| **Relacionamento** | Requisitos não-funcionais de Segurança básica. |

---

## 4. Análise de Riscos e Mitigação

| Campo | Descrição |
| :--- | :--- |
| **ID do Risco** | RISCO-001 |
| **Descrição** | Falta de motoristas disponíveis em determinada região solicitada pelo passageiro. |
| **Categoria** | Operacional / Negócio |
| **Probabilidade** | Média |
| **Impacto** | Alto (Gera frustração e perda de usuários) |
| **Ação de Mitigação** | Criar incentivos e campanhas com as frotas para cobrir áreas de alta demanda (preço dinâmico ou bônus). |
| **Plano de Contingência** | Exibir mensagem clara de "Sem motoristas no momento" e sugerir tentar novamente em alguns minutos. |

| Campo | Descrição |
| :--- | :--- |
| **ID do Risco** | RISCO-002 |
| **Descrição** | Imprecisão ou falha no sinal do GPS durante a corrida ou na busca pelo passageiro. |
| **Categoria** | Técnico |
| **Probabilidade** | Alta |
| **Impacto** | Médio |
| **Ação de Mitigação** | Utilizar APIs de mapas redundantes ou de alta fidelidade e manter o app otimizado. |
| **Plano de Contingência** | Permitir que o passageiro e o motorista troquem mensagens de texto anônimas dentro do app para facilitar o encontro físico. |


---

## 5. Referências
* [Pesquisa de mobilidade](https://nossasaopaulo.org.br/wp-content/uploads/2019/01/Viver-em-SP-2024_Mobilidade_resumida.pdf)
* [Matéria Jovem Pam](https://jovempan.com.br/programas/jornal-da-manha/tempo-gasto-no-transporte-publico-na-cidade-de-sao-paulo-sobe-para-2h47.html)
* [Matéria Mobilize Brasil](https://www.mobilize.org.br/noticias/14251/na-contramao-da-mobilidade-urbana.html)
* [Wireframes de baixissima resolução](https://www.figma.com/design/eq3HicIS1rX8LCOToApptt/Price-Crawler?node-id=1043-2&t=HSHctMRsnIwYWpAD-1)
