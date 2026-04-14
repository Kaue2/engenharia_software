# Documento de Engenharia de Requisitos: CityGo

## 1. Requisitos funcionais

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** |  RF-001 |
| **Nome** | Cadastro de empresas de cooperativas e taxi/locadoras |
| **Descrição** | 1. Entrar no aplicativo <br> 2. Abrir a aba de cadastro <br> 3. Selecionar "Empresa parceira" |
| **Extensões** | 1. Empresa precisa ser avaliada para então ser aceita |
| **Critério de Aceitação** | 1. Dados da empresa devem ser preenchidos da maneira correta <br> 2. E-mail de contato deve ser verificado |
| **Dependências** | Funcionário responsável da empresa e rede internet para conexão |
| **Fonte** | Empresas parceiras |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-002 |
| **Nome** | Cadastro de motoristas vingulados a empresa já cadastrada |
| **Descrição** | 1. Entrar no aplicativo <br> 2. Abrir aba de cadastro <br> 3. Selecionar "Motorista" <br> 4. Seleção da empresa que o motorista trabalha <br> 5. Adicionar dados do motorista |
| **Extensões** |  |
| **Critério de Aceitação** | 1. Motorista deve trabalhar em empresa já cadastrada e avaliada |
| **Dependências** | Acesso a rede, avaliação da empresa |
| **Fonte** | motorista, administrador da frota |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-003 |
| **Nome** | Cadastro de passageiro |
| **Descrição** | 1. Entrar no aplicativo <br> 2. Abrir aba de cadastro <br> 3. Selecionar "Passageiro" <br> 4. Adição de dados do passageiro |
| **Extensões** | 1. O passageiro pode entrar no sistem utilizando sua conta google |
| **Critério de Aceitação** | 1. Dados do passageiro devem ser preenchidos de forma correta <br> 2. E-mail de contato deve ser verificado |
| **Dependências** | Acesso a rede |
| **Fonte** | Passageiro |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-004 |
| **Nome** | Login de usuário |
| **Descrição** | 1. Entrar no aplicativo <br> 2. Selecionar "Entrar" <br> 3. Preenchimento de dados do usuário em questão |
| **Extensões** | 1. O usuário pode se autenticar utilizando contas da microsoft ou google <br> 2. O login pode não ser necessário caso os dados tenham sido salvos em outro momento (persistência local) |
| **Critério de Aceitação** | 1. Usuário inseriu seus dados de forma correta |
| **Dependências** | Acesso a rede |
| **Fonte** | Passageiro, administrador de frota, motorista |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-005 |
| **Nome** | Solicitação de rotas |
| **Descrição** | 1. Entrar no aplicativo <br> 2. Digitar o endereço de destino na tela de "Procurar destino" |
| **Extensões** |  |
| **Critério de Aceitação** | 1. Passageiro inseri um destino válido |
| **Dependências** | Passageiro autenticado, acesso a rede |
| **Fonte** | Passageiro |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-006 |
| **Nome** | Estimativa de valor de rota |
| **Descrição** | 1. Destino deve ser selecionado <br> 2. Aplicativo deve obter a localização de usuário <br> 3. Cálculo de valor da rota deve ser feito com base na distância percorrida, horário, informações em relação a trânsito |
| **Extensões** | 1. Usuário pode ter cupons de desconto |
| **Critério de Aceitação** | 1. Rota possui caminho viável |
| **Dependências** | Passageiro autenticado, acesso a rede, conexão com GPS e localização |
| **Fonte** | Passageiro |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-007 |
| **Nome** | Cadastro de formas de pagamento |
| **Descrição** | 1. Entrar no aplicativo como passageiro <br> 2. Selecionar aba "Formas de pagamento" <br> 3. Selecionar forma de pagamento desejada |
| **Extensões** | 1. Usuário pode preencher formas de pagamento com carteiras digitais |
| **Critério de Aceitação** | 1. Dados de forma de pagamento inserido são válidos |
| **Dependências** | Passageiro autenticado, acesso a rede, autenticação de forma de pagamento com empresa responsável |
| **Fonte** | Passageiro |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-008 |
| **Nome** | Notificar motoristas nos arredores ao iniciar rota válida |
| **Descrição** | 1. Obter localização de motoristas em raio pré determinado <br> 2. Notificar motoristas parceiros <br> 3. Exibir para tais motoristas as informações da rota disponível, tais como destino, valor a ser recebido, duração e avaliação do usuário <br> 4. Exibir botões para aceitar ou recusar viagem <br> 5. Caso nenhum motorista aceite a viagem, aumente o raio de notificação e repita o processo |
| **Extensões** ||
| **Critério de Aceitação** | 1. Notificações enviadas <br> 2. Motoristas possuindo a oportunidade de aceitar ou recusar a viagem |
| **Dependências** | Passageiro autenticado, motorista vinculado a empresa prestando serviço, conexão a rede |
| **Fonte** | Motorista |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-009 |
| **Nome** | Atualização status da rota para usuário, ocorrendo quando a rota é aceita |
| **Descrição** | No momento que a rota for aceita por motorista, notificação deve ser enviada para usuário, contendo:<br> 1. Dados do motorista <br> 2. Localização do motorista <br> 3. Estimativa de tempo de chegada do motorista |
| **Extensões** | 1. Usuário pode cancelar a rota <br> 2. Usuário pode visualizar localização do motorista em tempo real <br> 3. Usuário é notificado mesmo com o aplicativo fechado |
| **Critério de Aceitação** | Usuário é notificado |
| **Dependências** | Usuário com acesso a rede, motorista com acesso a rede |
| **Fonte** | Motorista e usuário |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-010 |
| **Nome** | Exibição de localização do ponto de início de rota ao motorista |
| **Descrição** | No momento que a rota é aceita, motorista passa a visualizar ponto de chegada para buscar passageiro |
| **Extensões** | 1. Motorista pode visualizar caminho até o passageiro |
| **Critério de Aceitação** | Rota até o passageiro é visualizada |
| **Dependências** | Motorista com acesso a rede, localização em tempo real do motorista, informações de trânsito e cálculo de rota |
| **Fonte** | Motorista |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-011 |
| **Nome** | Inicialização de corrida pelo motorista |
| **Descrição** | Ao chegar ao local de embarque, passageiro entra no veículo e motorista aperta o botão "Iniciar corrida" |
| **Extensões** | 1. Notificações de início da corrida são disparados e status são atualizados no sistema |
| **Critério de Aceitação** | Motorista e passageiro precisam estar no local de embarque, botão precisa ser apertado pelo motorista |
| **Dependências** | Motorista com acesso a rede, localização em tempo real do motorista e do passageiro |
| **Fonte** | Motorista |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-012 |
| **Nome** | Notificação de início e andamento da rota aos contatos de motoristas e passageiros |
| **Descrição** | Ao início da corrida, notificação precisa ser disparada aos contatos de segurança do passageiro e a empresa contratante do motorista. <br> 1. É possível visualizar andamento da viagem <br> 2. É possível visualizar tempo restante <br> 3. Para a empresa, é possível visualizar valor da corrida |
| **Extensões** | Dados são exibidos por todo andamento da rota |
| **Critério de Aceitação** | Contatos devem ser notificados e ter a opção de visualizar status da rota |
| **Dependências** | Contatos necessitam ter acesso a rede, localização em tempo real do motorista e do passageiro |
| **Fonte** | Motorista (por inicializar rota), Contatos de passageiro e motorista (para visualizar dados) |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-013 |
| **Nome** | Gravação da rota em execução |
| **Descrição** | A rota em andamento deve ser gravada pelo sistema, sendo armazenadas informações quanto ao caminho utilizado, bem como data e horário de início e finalização da corrida |
| **Extensões** | Tais dados devem ser disponibilizados a ambas as partes |
| **Critério de Aceitação** | Dados necessários devem ser armazenados |
| **Dependências** | Rede, armazenamento |
| **Fonte** | Sistema |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-014 |
| **Nome** | Recálculo de rotas de acordo com trânsito e possíveis obstruções |
| **Descrição** | De acordo com o trânsito no percurso sendo tomado, o sistema deve ser capaz de encontrar novas rotas para que o passageiro chegue ao seu destino sem ou com o mínimo de aumento possível no tempo da rota |
| **Extensões** | Passageiro deve ser atualizado das mudanças de percurso, bem como mudanças de valor |
| **Critério de Aceitação** | Sistema deve recalcular rota |
| **Dependências** | Rede, localização em tempo real do motorista e passageiro, informações em tempo real de trânsito na região |
| **Fonte** | Motorista, passageiro |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-015 |
| **Nome** | Finalização da corrida |
| **Descrição** | Ao se aproximar do destino, sistema deve visualizar posição e proximidade do motorista e passageiro e exibir ao motorista opção para finalizar corrida, atualizando assim status da rota |
| **Extensões** | Opções de pagamento abas para avaliação do motorista e passageiro são exibidas |
| **Critério de Aceitação** | Ao clicar em "finalizar rota", status da rota é atualizado e próximos passos são exibidos |
| **Dependências** | Rede, localização em tempo real do motorista e passageiro |
| **Fonte** | Motorista |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-016 |
| **Nome** | Permissão para realizar pagamento ao finalizar rota |
| **Descrição** | Ao chegar ao destino, passageiro deverá realizar o pagamento do serviço prestado de acordo com o método de pagamento previamente selecionado. Sendo exibido caso o pagamento não tenha sido realizado de forma automática |
| **Extensões** | Passageiro pode escolher pagar na próxima viagem, caso não possua nenhum valor pendente de outra viagem |
| **Critério de Aceitação** | Opção de pagamento é selecionada, rota pode ter seu status atualizado de "em aguardo de pagamento" para "finalizado" |
| **Dependências** | Rede, conexões com empresas responsáveis por formas de pagamento |
| **Fonte** | Motorista, passageiro |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-017 |
| **Nome** | Notificar contatos de motorista e passageiro quanto ao final da corrida |
| **Descrição** | Ao finalizar rota, empresa contratante e contatos de segurança do passageiro devem ser notificados quanto a finalização da rota |
| **Extensões** | Empresa contratante pode visualizar método de pagamento realizado |
| **Critério de Aceitação** | Contatos são notificados |
| **Dependências** | Rede |
| **Fonte** | Sistema, contatos de ambas as partes |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-018 |
| **Nome** | Geração de recibo digital de cada rota |
| **Descrição** | Ao finalizar rota, recibo digital deve ser gerado e entregue a motoristas e passageiro, contendo informações legais a respeito da rota |
| **Extensões** | Recibo pode ser enviado por e-mail a ambas as partes |
| **Critério de Aceitação** | Recibo é gerado |
| **Dependências** | Rede, dados sobre rota, dados quanto ao pagamento |
| **Fonte** | Sistema, empresa contratante, passageiro |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-019 |
| **Nome** | Permissão de avaliação mútua |
| **Descrição** | Após finalização da rota, tanto passageiro quanto motorista possuem a opção de realizar avaliação mutuamente |
| **Extensões** | Empresa responsável pelo motorista será notificada quanto a nota que o mesmo receber |
| **Critério de Aceitação** | Exibição da opção de avaliação a ambas as partes |
| **Dependências** | Rede |
| **Fonte** | Motorista, passageiro, empresa contratante do motorista |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-020 |
| **Nome** | Permissão para visualização de histórico de rotas já realizadas |
| **Descrição** | Motoristas, empresas responsáveis e passageiros devem ter a opção de visualizar o histórico de rotas realizadas, sendo possível visualizar os valores, horários e datas, bem como o percurso de cada rota |
| **Extensões** | Rotas podem ser selecionadas para que haja foco na visualização |
| **Critério de Aceitação** | Lista é exibida a ambas as partes |
| **Dependências** | Rede, armazenamento |
| **Fonte** | Motoristas, empresas responsáveis e passageiros |
| **Prioridade** | Alta | 

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RF-021 |
| **Nome** | Repasses de valores a empresas parceiras |
| **Descrição** | Após receber o pagamento da rota que foi finalizada, valor deve ser repassado a empresa contratante do motorista, sendo decrementado devidas taxas de serviço da CityGo |
| **Extensões** | Recibos possuem taxas cobradas pela CityGo |
| **Critério de Aceitação** | Valores são repassados |
| **Dependências** | Rede |
| **Fonte** | Sistema |
| **Prioridade** | Alta | 


## 2. Requisito não-funcionais

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RN-001 |
| **Título** | Proteção de Dados Sensíveis e Controle de Acesso |
| **Descrição** | O sistema deve garantir a confidencialidade dos dados. A autenticação de passageiros, motoristas e empresas deve exigir duplo fator (2FA). Dados sensíveis (como documentos e histórico) devem ser armazenados de forma criptografada no banco de dados. Além disso, a visualização de dados em tela deve ser restrita ao estritamente necessário para a corrida (ex: mascaramento do telefone ou sobrenome entre motorista e passageiro). |
| **Entrada** | Solicitações de usuários (cadastro, login e rotas) |
| **Processamento** |  |
| **Saída** |  |
| **Restrições** | O armazenamento e o tráfego de dados devem estar em conformidade com a LGPD. O banco de dados deve utilizar criptografia TDE (Transparent Data Encryption) ou AES-256 para as colunas sensíveis. |
| **Critérios de Aceitação** | 1. É impossível logar na plataforma sem confirmar o token de 2FA. <br>2. Uma inspeção direta no banco de dados não revela as senhas ou documentos em texto plano. <br> 3. O aplicativo do motorista não recebe via API o documento ou telefone real do passageiro (e vice-versa). |

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RN-002 |
| **Título** | Tempo de Resposta das APIs |
| **Descrição** | O sistema deve garantir uma experiência fluida. Operações cotidianas (como login, carregamento de perfil e atualização de localização) devem responder em menos de 500 milissegundos. Operações complexas (como cálculo de rotas longas) podem levar até no máximo 3 segundos. |
| **Entrada** | Solicitação de usuários |
| **Processamento** | Processamento dos dados |
| **Saída** | Retorno da requisição aos usuários |
| **Restrições** | Aplica-se ao tempo de processamento no servidor e tempo de resposta da rede até o cliente (excluindo a latência da internet da operadora do usuário, que foge do controle do sistema). |
| **Critérios de Aceitação** | 1. 95% (p95) das requisições gerais devem ser processadas em menos de 500ms. <br> 2. 100% dos cálculos de rota devem ser concluídos e retornados em menos de 3 segundos sob carga normal. |

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RN-003 |
| **Título** | Suporte a Usuários Simultâneos |
| **Descrição** | O sistema deve ser dimensionado para suportar uma base de 5.000 usuários cadastrados no primeiro ano, prevendo um crescimento de 100% ao ano. A infraestrutura deve suportar que até 10% dessa base (500 usuários) utilize o aplicativo ativamente e simultaneamente nos horários de pico sem degradação de performance. |
| **Entrada** | Solicitações de usuários |
| **Processamento** | Processamentos de dados necessários |
| **Saída** | Retorno das requisições |
| **Restrições** | A arquitetura deve permitir escalabilidade caso a meta de acessos simultâneos seja ultrapassada. |
| **Critérios de Aceitação** | 1. Testes de carga demonstram que o sistema atende 500 usuários fazendo requisições concorrentes sem que a taxa de erro passe de 1% e mantendo o RN-002. |

| Campo | Descrição |
| :--- | :--- |
| **ID do requisito** | RN-004 |
| **Título** | Volume de dados |
| **Descrição** | O banco de dados e os serviços de mensageria devem estar preparados para processar e registrar até 100.000 corridas no primeiro ano. O sistema deve suportar a alta frequência de atualizações de GPS e recálculos de rota oriundos de corridas em andamento. |
| **Entrada** | Rota em andamento |
| **Processamento** | Atualização de localização, recalculo de percurso, estimativa de tempo |
| **Saída** | Atualizações para a rota em andamento |
| **Restrições** | Atualizações de localização frequentes não devem sobrecarregar o banco de dados principal ; recomenda-se o uso de cache ou bancos otimizados para séries temporais/geolocalização para a telemetria em tempo real. |
| **Critérios de Aceitação** | 1. O sistema consegue inserir e processar as atualizações de GPS de 1000 rotas ativas simultaneamente sem travar as tabelas principais. <br> 2. O banco de dados suporta o armazenamento do histórico de 100.000 rotas (com detalhes de tempo e trajeto) sem comprometer o tempo de leitura dos relatórios.|