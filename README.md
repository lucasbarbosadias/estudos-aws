# Estudos AWS

## Associate developer - AWS Certified Cloud Practitioner

### Introdução à Amazon Web Services

**Modelos de implantação de computação em nuvem:** são computação baseada na nuvem, on-premises (local) e híbrida (local e na nuvem).

Benefícios da computação em nuvem:
- Troque despesas iniciais por despesas variáveis
- Pare de gastar dinheiro para executar e manter data centers
- Pare de tentar adivinhar a capacidade
- Beneficie-se de grandes economias de escala
- Aumentar a velocidade e a agilidade
- Ter alcance global em minutos

### Computação na Nuvem

**Amazon Elastic Compute Cloud - EC2:** Servidor hospedado na Nuvem, oferece capacidade de processamento flexível e escalável, podemos criar e gerenciar instâncias (máquinas virtuais) com diferentes configurações de hardware e sistemas operacionais.

**Família de instâncias do EC2:**
- Uso geral
- Otimizadas para computação
- Otimizadas para memória
- Computação acelerada
- Otimizadas para armazenamento

**Opções de compra do EC2:**
- **Sob demanda:** paga apenas pelo uso, sem planos.
- **Saving plans:** mais barato mas precisa fixar plano de 1 ou 3 anos.
- **Instâncias reservadas:** carga de trabalho constante, mais barato, plano de 1 ou 3 anos, podendo ser pagamento total antecipado, adiantado parcial ou sem pagamento adiantado.
- **Instancias spot:** mais barato, porém ela pode ser desligada inesperadamente e ligada também, indicada para trabalhos que podem ser interrompidos.
- **Hosts dedicados:** são servidores físicos com capacidade totalmente dedicada ao uso do cliente.

**Amazon EC2 Auto Scaling**: abordagens disponíveis:
- **Scaling dinâmico:** responde às alterações na demanda. 
- **Scaling preditivo:** programa automaticamente o número correto de instâncias do Amazon EC2 com base na demanda prevista.

**Elastic load balancing - ELD:** distribui automaticamente o tráfego de entrada de aplicações entre vários recursos, como instâncias do Amazon EC2.

**Amazon Elastic Container Service - Amazon ECS:** é um sistema de gerenciamento de contêineres altamente dimensionável e de alto desempenho que permite executar e dimensionar aplicações em contêineres na AWS.

**Amazon Elastic Kubernetes Service - Amazon EKS:** é um serviço totalmente gerenciado que você pode usar para executar o Kubernetes na AWS.

**AWS Fargate:** é um mecanismo de computação sem servidor para contêineres. Ele funciona com o Amazon ECS e o Amazon EKS.

### Infraestrutura global e confiabilidade

Maneiras de interagir com os serviços da AWS:
- CONSOLE DE GERENCIAMENTO DA AWS
- AWS COMMAND LINE INTERFACE (CLI)
- KITS DE DESENVOLVIMENTO DE SOFTWARE (SDKS)

Ferramentas de gerenciamento:

- **AWS Elastic Beanstalk:** você envia definições de código e configuração, e o Elastic Beanstalk implanta os recursos necessários para executar tarefas.

- **AWS CloudFormation:** sua infraestrutura como código. Pode criar um ambiente escrevendo linhas de código em vez de usar o console de gerenciamento da AWS para provisionar recursos individualmente.

### Redes

**Virtual Private Cloud - VPC:** Podemos criar sub redes públicas e privadas nele, exemplo do caixa da cafeteria público e o barista privada. Para permitir o público acessar minha vpc preciso de um Gateway de internet, caso queira permitir acesso a minha vpc apenas recursos privados preciso de um Gateway privado virtual.

**AWS direct connect:** é uma conexão da minha empresa diretamente com a AWS sem passar pela internet normal.

**VPN virtual private network:** aí acessaria a AWS pela internet normal só que com "seguranças" pelo caminho, que seria a criptografia.

**Controle de acesso:** uma sub rede é uma seção de uma VPC que posso agrupar recursos da AWS, podendo ser pública ou privada.

**ACLs de rede - lista de controle de acesso:** é um firewall da sub rede que controla o tráfego, igual aos oficiais que controlam os passaportes de quem pode acessar o país, quem está na lista aprovada acessa e quem não está na lista ou está em uma recusada não pode acessar, por padrão ela permite todo o tráfego de entrada e saída, se customizar ela bloqueia tudo e só libera o que adicionar na configuração. Ela filtra os pacotes de forma stateless onde pede permissão para entrar e para sair.

**Grupo de segurança:** firewall da EC2, controla o tráfego de entrada e saída e por padrão nega todo o tráfego de entrada, pode adicionar regras personalizadas para o tráfego que será permitido. Filtra os pacotes no modelo stateful, verifica a entrada e a saída não.

Redes globais:

**DNS:** Domain name service, basicamente recebe o nome do site e retorna o endereço ip dele.

**Route53:** faz esse serviço do DNS e também podemos comprar domínios por ele ou transferir os comprados por outro site para gerenciar aqui.

**Cloudfront:** realiza cópias dos conteúdos do meu servidor em cache em vários locais ao redor do mundo (locais de borda) para o cliente acessar do servidor mais próximo, o route53 trabalha em conjunto aqui para direcionar o cliente para o servidor mais eficiente e próximo.

### Armazenamento e Banco de dados

**Elastic Block Store - EBS:** é um meio temporário de armazenamento a nível de bloco para uma instância do EC2, disco físico anexado ao computador host para um EC2, caso a EC2 seja encerrada perdemos o conteúdo armazenado.
Armazena dados em uma única zona de disponibilidade e para anexar uma EC2 a um volume do EBS precisam estar na mesma zona de disponibilidade.

**Snapshot do EBS:** Backup de forma incremental, copia apenas as novas alterações desde o último snapshot.

**Simple Storage Service - S3:** Armazenamento de objetos, consiste em dados, metadados e uma chave. Dados podem ser qualquer tipo de arquivo, metadados contém informações sobre o tipo do dado e tamanho e assim por diante. Chave é seu identificador único. Dados são armazenados como objetos em buckets.
Podemos armazenar arquivos de backup, mídia, documentos diversos e espaço ilimitado, tamanho máximo de arquivo para um objeto é de 5tb.
Possuí permissionamento de visibilidade e acesso aos arquivos e versionamento.

Storage classes do S3: Pague somente pelo uso
Para escolher uma precisamos considerar:

```md
- Com que frequência você planeja recuperar seus dados
- Seus dados precisam estar muito ou pouco disponíveis
```

- **S3 Standard:** para dados acessados com frequência, armazena no mínimo em 3 zonas de disponibilidade.

- **S3 Standard – Infrequent Access (S3 Standard-IA):** Ideal para dados com pouca frequência de acesso, mas que precisam ter alta disponibilidade para quando necessário. Semelhante ao Amazon S3 Standard, mas com um preço de armazenamento mais baixo e um preço de recuperação mais alto. Armazena no mínimo em 3 zonas de disponibilidade.

- **S3 One Zone-Infrequent Access (S3 One Zone – IA):** Armazena dados em uma única Zona de Disponibilidade, tem um preço de armazenamento menor do que o Amazon S3 Standard-IA. É ideal para economizar custos com armazenamento. Você pode reproduzir facilmente seus dados em caso de falha na Zona de Disponibilidade.

- **S3 Intelligent-Tiering:** Ideal para dados com padrões de acesso desconhecidos ou em alteração, requer uma pequena taxa mensal de monitoramento e automação por objeto. S3 monitora e caso não tenha acesso a um objeto por 30 dias ele move o objeto para nível de acesso pouco frequente S3 Standard-IA, mas se acessarmos ele novamente o S3 move para o objeto novamente para o Nível de acesso frequente S3 Standard.

- **S3 Glacier Instant Retrieval:** Funciona bem para dados arquivados que requerem acesso imediato, pode recuperar objetos em alguns milissegundos igual o S3 Standard.

- **S3 Glacier Flexible Retrieval:** Armazenamento de baixo custo projetado para arquivamento de dados, capaz de recuperar objetos em poucos minutos a horas (1m a 12h), ideal para arquivamento de dados.

- **S3 Glacier Deep Archive:** Storage class de objetos de menor custo, ideal para arquivamento, capaz de recuperar objetos de 12 horas a 48 horas. Suporte a retenção de longo prazo e preservação digital de dados acessados uma ou duas vezes por ano. Todos objetos são replicados e armazenados em pelo menos 3 zonas de disponibilidade geograficamente dispersas.

- **S3 Outposts:** Cria buckets do S3 no Amazon S3 Outposts, torna mais fácil recuperar, armazenar e acessar dados no AWS Outposts. Armazenamento durável e redundante em vários dispositivos e servidores, mantém dados próximos a aplicações on-premises, funciona bem para cargas de trabalho que exigem alto desempenho e a permanência de dados no local.

**Elastic File System - EFS:** No armazenamento de arquivos vários clientes podem acessar os dados em pasta de arquivos compartilhados, servidor de armazenamento em bloco com sistema de arquivos local para organizar os arquivos, acessados por meio de caminhos de arquivo. Ideal para casos de uso em que um grande número de serviços e recursos precisam acessar os mesmos dados ao mesmo tempo. É dimensionável usado com AWS Cloud Services e recusos on-premises, a medida em que adiciona e remove arquivos o EFS expande e retrai automaticamente. Serviço regional, armazena em várias zonas de disponibilidade e entre elas. Servidores on-premises podem acessar o EFS usando o AWS Direct Connect.

**Relational Database Service - RDS:** é um serviço que permite executar bancos de dados relacionais na nuvem AWS. Em um banco de dados relacional, os dados são armazenados de modo que se relacionem a outros dados, usa linguagem de consulta estruturada (SQL).
O RDS automatiza tarefas como provisão de hardware e configuração do banco de dados, patch e backups. Possuí inúmeras opções de segurança, muitos mecanismos de banco de dados do RDS oferecem criptografia em repouso e trânsito dos dados.

Disponível em seis mecanismos de banco de dados:

- Amazon Aurora
- PostgreSQL
- MySQL
- MariaDB
- Oracle Database
- Microsoft SQL Server

**Amazon Aurora:** é um banco de dados relacional de nível empresarial, compatível com bancos de dados relacionais MySQL e PostgreSQL, até 5 vezes mais rápido do que os bancos MySQL comuns e até 3 vezes mais rápido que os bancos de dados PostgreSQL comuns.
Ajuda a reduzir custos de operações desnecessárias de entrada e saída (E/S), considere o uso para cargas de trabalho que exigem alta disponibilidade, replica seis cópias de dados em 3 zonas de disponibilidade e faz backups contínuos para o S3.

**DynamoDB:** é um serviço de banco de dados chave-valor, com desempenho de um dígito de milissegundos em qualquer scaling. Banco de dados não relacional - NoSQL, usam estruturas diferentes de linhas e colunas, usam pares de chave e valor, os dados são organizados em itens(chaves) e cada item tem um atributo(valor), os itens não precisam ter os mesmos tipos.
Sem servidor, não precisamos gerenciar. Auto scaling, dimensionado a medida que seu tamanho expande ou retrai e mantém desempenho consistente, ideal para casos de uso que exigem alto desempenho durante o scaling.

**Amazon Redshift:** serviço de data warehouse que você pode usar para análise de Big Data. Ele oferece a capacidade de coletar dados de muitas fontes além de ajudar a entender relações e tendências em todos os seus dados.

**Database Migration Service - DMS:** permite migrar bancos de dados relacionais e não relacionais e outros tipos de armazenamentos de dados. Permite mover dados entre bancos de dados de origem e de destino. Os bancos de dados de origem e de destino podem ser do mesmo tipo ou de tipos diferentes.
Durante a migração, o banco de dados de origem permanece operacional, reduzindo o tempo de inatividade em qualquer aplicativo que dependa do banco de dados. Permite a combinação de vários bancos de dados em um único, caso o banco a ser migrado seja de um tipo diferente do destino o DMS converte seus dados para serem migrados corretamente para o destino.
Permite o desenvolvimento e teste de migrações de banco de dados de produção sem afetar os usuários, realizando uma cópia de produção para ambiente de desenvolvimento. Replicação contínua, ele envia cópias dos dados para outras fontes de destino em vez de fazer uma migração única.

**Amazon documentDB:** serviço de banco de dados de documentos compatível com cargas de trabalho do mongoDB (mongoDB é um programa de banco de dados de documentos).

**Amazon Neptune:** serviço de banco de dados de grafo, pode ser usado para criar e executar aplicações que funcionam com conjunto de dados altamente conectados como mecanismos de recomendação - redes sociais, detecção de fraude e grafos de conhecimento.

**Amazon Quantum Ledger Database - QLDB:** é um serviço de banco de dados ledger, pode ser usado para ver um histórico completo de todas as alterações feitas nos dados da aplicação.

**Amazon Managed Blockchain:** é um serviço para criar e gerenciar redes de blockchain com frameworks de código aberto, o Blockchain é um sistema de registro distribuído que permite que várias partes executem transações e compartilhem dados sem uma autoridade central.

**Amazon ElastiCache:** é um serviço que adiciona camadas de cache sobre bancos de dados para ajudar a melhorar os tempos de leitura de solicitações comuns. Ele é compatível com dois tipos de armazenamentos de dados: Redis e Memcached.

**Amazon DynamoDB Accelerator - DAX:** é um cache em memória do DynamoDB, ele ajuda a melhorar os tempos de resposta de milissegundos para microssegundos.

### Segurança

**Modelo de responsabilidade compartilhada da AWS:**
- **Clientes:** responsabilidade na nuvem, atualizações de segurança, configurações de rede, permissionamento.
- **Amazon:** responsabilidade da nuvem, segurança dos data centers, segurança das suas aplicações e serviços.

**Identity and Access Management - IAM:** permite gerenciar acessos e permissões aos serviços e recursos da AWS com segurança. Recursos do IAM:

- Usuários, grupos e perfis do IAM
- Políticas do IAM
- Autenticação multifator

**Usuário do IAM:** é uma identidade que você cria na AWS. Ele representa a pessoa ou o aplicativo que interage com os serviços e recursos AWS. Consiste em um nome e credenciais.

**Política do IAM:** é um documento que concede ou nega permissões para serviços e recursos AWS.  Permite personalizar os níveis de acesso aos usuários dos recursos.

**Grupo do IAM:** é um conjunto de usuários do IAM. Quando você atribui uma política do IAM a um grupo, todos os usuários do grupo recebem permissões especificadas pela política.

**Perfil do IAM:** é uma identidade que você pode assumir para obter acesso *temporário* a permissões, em vez de um acesso de longo prazo.  Utilizada quando um funcionário alterna entre tarefas diferentes, ele abre mão do acesso a uma estação de trabalho e ganha acesso a outra, podendo alternar facilmente entre as estações de trabalho.

**Autenticação com multifator:** é uma camada extra de segurança para sua conta AWS. Por exemplo quando acessamos um site e em seguida pede uma segunda forma de autenticação, como um código aleatório enviado por email ou é solicitado ao usuário que informe a resposta de autenticação de seu dispositivo MFA da AWS. Esse dispositivo pode ser uma chave de segurança de hardware, um dispositivo de hardware ou uma aplicação de MFA em um dispositivo, como um smartphone.

**AWS Organizations:** consolida e gerencia múltiplas contas AWS em um local central. Podemos controlar de maneira centralizada as permissões para as contas em sua organização usando as políticas de controle de serviço (SCPs), como o que cada uma pode acessar. Podemos agrupar contas em unidades organizacionais (UO) para facilitar o gerenciamento de contas com requisitos de negócios ou segurança semelhantes.

**AWS Artifact:** é um serviço que concede acesso sob demanda a relatórios de segurança e conformidade da AWS e a contratos on-line selecionados. Dependendo do setor de sua empresa, talvez seja necessário manter padrões específicos. Uma auditoria ou inspeção assegurará que a empresa cumpriu esses padrões, e para isso usamos o Artifact.

**AWS Artifact Agreements:** podemos ver, aceitar e gerenciar contratos para uma conta individual e para todas as suas contas no AWS Organizations.

**AWS Artifact Reports:** oferece relatórios de conformidade por auditores terceirizados. Esses auditores testaram e verificaram se a AWS está em conformidade com diversas normas e regulamentações de segurança globais, regionais e específicas do setor. Bom para desenvolvedores que estão criando algo e precisam ver se estão seguindo a conformidade com padrões regulatórios.
AWS possuí o *centro de conformidade para o cliente*, onde contém recursos que ajudam a saber mais sobre a conformidade da AWS, como histórias de clientes e casos de uso.

**AWS Shield:** é um serviço que protege aplicações contra ataques DDoS. O AWS Shield oferece dois níveis de proteção: 
- **Standard:** protege automaticamente todos os clientes AWS sem nenhum custo. Ele protege seus recursos AWS contra os tipos de ataques DDoS mais comuns e frequentes. 
- **Advanced:** é um serviço pago que fornece diagnósticos detalhados de ataques e a capacidade de detectar e mitigar ataques elaborados de DDoS. Ele também se integra a outros serviços, como o Amazon CloudFront, o Amazon Route 53 e o Elastic Load Balancing. Além disso, você pode integrar o AWS Shield ao AWS WAF escrevendo regras personalizadas para mitigar ataques complexos de DDoS.

**AWS Key Management Service - AWS KMS**: permite executar operações de criptografia utilizando chaves. As chaves são uma cadeia aleatória de digítos utilizada para criptografar e descriptografar dados. Com o KMS podemos gerenciar essas chaves.

**AWS WAF:** é um firewall de aplicação web que permite monitorar solicitações de rede que entram em aplicações web. Ele trabalha em conjunto com o Amazon CloudFront e um Application Load Balancer. Basicamente ele permite ou bloqueia o tráfego na rede, ele faz isso usando uma lista de controle de acesso (ACL) da web para proteger os recursos da AWS.

**Amazon Inspector:** ajuda a melhorar a segurança e a conformidade das aplicações executando avaliações de segurança automatizadas. Ele verifica os aplicativos quanto a vulnerabilidades de segurança e desvios das práticas recomendadas de segurança, como acesso aberto a instâncias do Amazon EC2 e instalações de versões de software vulneráveis.

**Amazon GuardDuty:** é um serviço que realiza detecção inteligente de ameaças para sua infraestrutura e seus recursos AWS. Ele identifica ameaças monitorando continuamente a atividade da rede e o comportamento da conta no seu ambiente AWS.

### Monitoramento e Análise

**Amazon CloudWatch:** é um serviço da web que permite monitorar e gerenciar várias métricas e configurar ações de alarme de acordo com os dados dessas métricas que vão executar ações automaticamente se o valor da métrica ultrapassar ou for inferior a um limite predefinido. O recurso de painel do CloudWatch permite que você acesse todas as métricas dos seus recursos em um único local.

**AWS CloudTrail:** utilizado para auditoria, com ele podemos rastrear atividades dos usuários e solicitações de APIs em toda infraestrutura da AWS. Filtros por logs para auxiliar análises operacional e solução de problemas. Ele registra informações como chamador da API, hora da chamada da API, endereço IP de origem do chamador da API e muito mais.
O CloudTrail Insights é um recurso opcional que permite o CloudTrail detectar automaticamente atividades de API incomuns em sua conta AWS.

**AWS Trusted Advisor:** é um serviço da web que inspeciona seu ambiente AWS e faz recomendações em tempo real de acordo com as práticas recomendadas da AWS. Ele faz as verificações seguindo os cinco pilares: otimização de custos, desempenho, segurança, tolerância a falhas e limites de serviço. Para cada um desses ele retorna uma lista de ações recomendadas (vermelho), investigações recomendadas (amarelo) e nenhum problema foi detectado (verde).

### Definição de preços e suporte

**Nível gratuito da AWS:** use determinados serviços sem ter que se preocupar com o custo durante o período especificado. Três tipos de ofertas estão disponíveis: 
- Sempre gratuito
- 12 meses gratuitos
- Versões de teste

**Cobrança consolidada do AWS Organizations:** permite que você receba uma única fatura para todas as contas AWS na sua organização. Ao consolidar, você pode rastrear facilmente os custos combinados de todas as contas vinculadas em sua organização.

**AWS Budgets:** você pode criar orçamentos para planejar o uso do serviço, os custos de serviço e as reservas de instâncias. Coloca que o orçamento mensal é $100 dólares, e um aviso caso chegue em $50, outro para caso chegue em $90, e podemos ver o valor gasto, valor previsto e valor do orçamento por todos os serviços ou filtrado por cada um, o que facilita o acompanhamento dos gastos.

**AWS Cost Explorer:** é uma ferramenta que permite visualizar, interpretar e gerenciar seus custos e uso da AWS ao longo do tempo. Lista o valor gasto por cada recurso da AWS, pode filtrar por datas, tags, entre outros para ver relatórios específicos e realizar análise de gastos.

**Planos AWS Suporte:** a AWS oferece quatro planos de suporte diferentes para ajudar a solucição de problemas, reduzir custos e usar os serviços da AWS de maneira eficiente:

- Basic
- Desenvolvedor
- Empresarial
- Empresarial Rápido
- Empresarial de Grande Porte

**Technical Account Manager - TAM:** principal ponto de contato com a AWS. Disponível apenas para assinaturas Support Empresarial de Grande Porte ou Empresarial Rápido, o TAM educa, capacita e desenvolve sua jornada para a nuvem em toda a gama de serviços da AWS. Prestam orientação especializada em engenharia, ajuda na projeção de soluções que integram com eficiência os serviços da AWS, auxiliam com arquiteturas econômicas e resilientes e concedem acesso direto aos programas da AWS e a uma ampla comunidade de especialistas.

**AWS Marketplace:** é um catálogo digital com milhares de ofertas de software de provedores independentes de software. Você pode usar o AWS Marketplace para encontrar, testar e comprar software que pode ser executado na AWS.

### Migração e Inovação

**AWS Cloud Adoption Framework - AWS CAF:** possuí orientações para cada parte da empresa, sobre o que cada um precisa saber ao realizar uma migração para AWS. As orientações são organizadas em seis áreas de foco chamadas perspectivas. Cada perspectiva aborda responsabilidades distintas. 
O processo de planejamento ajuda as pessoas certas em toda a organização a se prepararem para as mudanças futuras.

Em geral, as perspectivas de negócio, pessoas e governança se concentram nos recursos comerciais, enquanto as perspectivas de plataforma, segurança e operações se concentram em capacidades técnicas.

- **Perspectiva de negócio:** Para gerentes de negócios, gerentes financeiros, proprietários de orçamento e stakeholders de estratégia. Garante que a TI esteja alinhada com às necessidades de negócio e que os investimentos em TI estejam vinculados aos principais resultados de negócios.
- **Perspectiva de pessoas:** Para recursos humanos, equipe e gerente de pessoas. Promove o desenvolvimento de uma estratégia de alterações em toda organização para adoção bem-sucedida da nuvem.
- **Perspectiva de governança:** Para Chief Information Officer (CIO), Gerentes do programa, Enterprise architect, Analistas de negócios e Gerentes de portfólio. Se concentra nas habilidades e processos para alinhar a estratégia de TI à estratégia de negócios. Isso garante que você maximize o valor comercial e minimize os riscos.
- **Perspectiva de plataforma:** Para Chief Technology, Officer (CTO), Gerentes de TI e Arquitetos de soluções. Inclui princípios e padrões para implementação de novas soluções na nuvem e migração de cargas de trabalho on-premises para a nuvem.
- **Perspectiva de segurança:** Para Chief information security officer (CISO), Gerentes de segurança de TI e Analistas de segurança de TI. Garante que a organização atenda aos objetivos de segurança de visibilidade, auditoria, controle e agilidade.
- **Perspectiva de operações:** Para Gerentes de operações de TI e Gerentes de suporte de TI. Ajuda a ativar, executar, usar, operar e recuperar cargas de trabalho de TI para o nível definido com os stakeholders da empresa.

**Seis estratégias de migração (6Rs):** ao migrar aplicações para a nuvem, podemos usar seis das estratégias de migração mais comuns:

- **redefinição de hospedagem:** (também conhecido como "lift-and-shift"), envolve a movimentação de aplicações sem alterações. 
- **redefinição de plataforma:** (também conhecido como “lift, tinker and shift”) envolve fazer algumas otimizações na nuvem para obter um benefício tangível. A otimização é alcançada sem alterar a arquitetura central do aplicativo.
- **refatoração/rearquitetura:** (também conhecida como rearquitetura) envolve reimaginar como uma aplicação é arquitetada e desenvolvida usando recursos nativos da nuvem. A refatoração costuma ser orientada pela forte necessidade que a empresa tem de adicionar recursos, scaling ou desempenho que, de outra forma, seriam difíceis de obter no ambiente atual da aplicação.
- **recompra:** envolve a mudança de uma licença tradicional para um modelo de software como serviço. 
- **retenção:** consiste em manter as aplicações essenciais para a empresa no ambiente de origem. Isso pode incluir aplicativos que exigem refatoração importante antes de serem migrados ou trabalhos que podem ser adiados.
- **retirada:**  é o processo de remoção de aplicações que não são mais necessárias.

**AWS Snow Family:** é uma coleção de dispositivos físicos para transporte físico de até exabytes de dados para dentro e para fora da AWS. A AWS é a proprietária e responsável pelo gerenciamento da Snow Family, que integra recursos de segurança, monitoramento, gerenciamento de armazenamento e computação da AWS.

Dispositivos/serviços existentes:

- **AWS Snowcone:** é um dispositivo pequeno, robusto e seguro para transferência de dados e computação de borda. Ele tem 2 CPUs, 4 GB de memória e até 14 TB de armazenamento utilizável.
- **AWS Snowball:** Aqui existem dois tipos de dispositivos: **Snowball Edge Storage Optimized** são ideais para migrações de dados de grande escala e fluxos de trabalho de transferência recorrentes, em além da computação local com necessidades maiores de capacidade. Armazenamento: 80 TB de capacidade de disco rígido (HDD) para volumes de blocos e armazenamento de objeto compatível com o Amazon S3, além de unidade de estado sólido (SSD) do SATA de 1 TB para volumes de blocos. Computação: 40 vCPUs e 80 GiB de memória para dar suporte a instâncias sbe1 do Amazon EC2 (equivalente a C5). O **Snowball Edge Compute Optimized** fornece recursos de computação poderosos para casos de uso, como machine learning, análise de vídeo em movimento completo, análise e pilhas de computação locais. Armazenamento: capacidade de HDD utilizável de 80 TB para armazenamento de objeto compatível com o Amazon S3 ou volumes de blocos compatíveis com o Amazon EBS e também 28 TB de capacidade de SSD NVMe utilizável para volumes de blocos compatíveis com o Amazon EBS. Computação: 104 vCPUs, 416 GiB de memória e uma GPU NVIDIA Tesla V100 opcional. Os dispositivos executam as instâncias sbe-c e sbe-g do Amazon EC2, que são equivalentes às instâncias C5, M5a, G3 e P3.
- **AWS Snowmobile:** é um serviço de transferência de dados na escala de exabytes usado para mover grandes quantidades de dados para a nuvem AWS. Você pode transferir até 100 petabytes de dados por Snowmobile, um contêiner de transporte reforçado com 13,71 metros de comprimento puxado por um caminhão semirreboque.

**Inovação com serviços AWS:** Para trabalhar sem servidor na AWS temos o AWS Lambda, para trabalhar com Machine learning temos o Amazon SageMaker que remove o trabalho difícil do processo de criar, treinar e implantar modelos de ML rapidamente. e para trabalhar com Inteligência artificial temos uma variedade de serviços: 
- Receba recomendações enquanto escreve e identifica problemas de segurança no seu código com o Amazon CodeWhisperer.
- Converter fala em texto com o Amazon Transcribe.
- Descobrir padrões em texto com o Amazon Comprehend.
- Identificar atividades on-line potencialmente fraudulentas com o Amazon Fraud Detector.
- Criar chatbots de voz e texto com o Amazon Lex.

### Jornada para nuvem

**AWS Well-Architected Framework:** ajuda você a entender como projetar e operar sistemas confiáveis, seguros, eficientes e econômicos na nuvem AWS. Com ele, é possível avaliar de maneira consistente suas arquiteturas em relação às práticas recomendadas e aos princípios de projeto e a identificar áreas para melhorias.

O Well-Architected Framework se baseia em cinco pilares: 

- **Excelência operacional:** é a capacidade de executar e monitorar sistemas para entregar valor comercial e melhorar continuamente os processos e procedimentos de apoio.
- **Segurança:** inclui a capacidade de proteger informações, sistemas e ativos e, ao mesmo tempo, entregar valor comercial por meio de avaliações de risco e estratégias de mitigação. 
- **Confiabilidade:** é a capacidade de um sistema recuperar-se de interrupções na infraestrutura ou no serviço, adquirir dinamicamente recursos de computação para atender à demanda e reduzir interrupções, como configurações incorretas ou problemas de rede transitórios.
- **Eficiência de desempenho:** é a capacidade de usar recursos computacionais com eficiência para cumprir requisitos do sistema e manter essa eficiência à medida que a demanda muda e as tecnologias evoluem. 
- **Otimização de custos:** é a capacidade de executar sistemas para entregar valor comercial com o menor preço.
- **Sustentabilidade:** é a capacidade de melhorar continuamente os impactos da sustentabilidade, reduzindo o consumo de energia e aumentando a eficiência em todos os componentes de uma carga de trabalho, maximizando os benefícios dos recursos provisionados e minimizando o total de recursos necessários.

**Vantagens da computação em nuvem:** Operar na nuvem AWS oferece muitos benefícios em relação à computação em ambientes on-premises ou híbridos, entre eles:

- Trocar despesa antecipada por despesas variáveis.
- Benefícios de enormes economias de escala.
- Parar de tentar adivinhar a capacidade.
- Aumentar a velocidade e a agilidade.
- Parar de gastar dinheiro com execução e manutenção de data centers.
- Ter alcance global em minutos.

#### Fonte:

[Curso Elementos essenciais do AWS Cloud Practitioner](https://explore.skillbuilder.aws/learn/course/8287/play/93778/elementos-essenciais-do-aws-cloud-practitioner-portugues-aws-cloud-practitioner-essentials-portuguese-na)
