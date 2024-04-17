# estudos-aws

## Associate developer

### Armazenamento e banco de dados

**Elastic Block Store - EBS:** é um meio temporário de armazenamento a nível de bloco para uma instância do EC2, disco físico anexado ao computador host para um EC2, caso a EC2 seja encerrada perdemos o conteúdo armazenado.
Armazena dados em uma única zona de disponibilidade e para anexar uma EC2 a um volume do EBS precisam estar na mesma zona de disponibilidade.

**Snapshot do EBS:** Backup de forma incremental, copia apenas as novas alterações desde o último snapshot.

**Simple Storage Service - S3:** Armazenamento de objetos, consiste em dados, metadados e uma chave. Dados podem ser qualquer tipo de arquivo, metadados contém informações sobre o tipo do dado e tamanho e assim por diante. Chave é seu indentificador único. Dados são armazenados como objetos em buckets.
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

**Elastic File System - EFS:** No armazenamento de arquivos vários clientes podem acessar os dados em pasta de arquivos compartilhadas, servidor de armazenamento em bloco com sistema de arquivos local para organizar os arquivos, acessados por meio de caminhos de arquivo. Ideal para casos de uso em que um grande número de serviços e recursos precisam acessar os mesmos dados ao mesmo tempo. É dimensionável usado com AWS Cloud Services e recusos on-premises, a medida em que adiciona e remove arquivos o EFS expande e retrai automaticamente. Serviço regional, armazena em várias zonas de disponibilidade e entre elas. Servidores on-premises podem acessar o EFS usando o AWS Direct Connect.

**Relational Database Service - RDS:** é um serviço que permite executar bancos de daos relacionais na nuvem AWS. Em um banco de dados relacional, os dados são armazenados de modo que se relacionem a outros dados, usa linguagem de consulta estruturada (SQL).
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
Sem servidor, não precisamos gerenciar. Auto scaling, dimensaionado a medida que seu tamanho expande ou retrai e mantém desempenho consistente, ideal para casos de uso que exigem alto desempenho durante o scaling.

**Amazon Redshift:** serviço de data warehouse que você pode usar para análise de Big Data. Ele oferece a capacidade de coletar dados de muitas fontes além de ajudar a entender relações e tendências em todos os seus dados.

**Database Migration Service - DMS:** permite migrar bancos de dados relacionais e não relacionais e outros tipos de armazenamentos de dados. Permite mover dados entre bancos de dados de origem e de destino. Os bancos de dados de origem e de destino podem ser do mesmo tipo ou de tipos diferentes.
Durante a migração, o banco de dados de origem permanece operacional, reduzindo o tempo de inatividade em qualquer aplicativo que dependa do banco de dados. Permite a combinação de vários bancos de dados em um único, caso o banco a ser migrado seja de um tipo diferente do destino o DMS converte seus dados para serem migrados corretamente para o destino.
Permite o desenvolvimento e teste de migrações de banco de dados de produção sem afetar os usuários, realizando uma cópia de produção para ambiente de desenvolvimento. Replição contínua, ele envia cópias dos dados para outras fontes de destino em vez de fazer uma migração única.

**Amazon documentDB:** serviço de banco de dados de documentos compatível com cargas de trabalho do mongoDB (mongoDB é um programa de banco de dados de documentos).

**Amazon Neptune:** serviço de banco de dados de grafo, pode ser usado para criar e executar aplicações que funcionam com conjunto de dados altamente conectados como mecanismos de recomendação - redes sociais, detecção de fraude e grafos de conhecimento.

**Amazon Quantum Ledger Database - QLDB:** é um serviço de banco de dados ledger, pode ser usado para ver um histórico completo de todas as alterações feitas nos dados da aplicação.

**Amazon Managed Blockchain:** é um serviço para criar e gerenciar redes de blockchain com frameworks de código aberto, o Blockchain é um sistema de registro distribuído que permite que várias partes executem transações e compartilhem dados sem uma autoridade central.

**Amazon ElastiCache:** é um serviço que adiciona camadas de cache sobre bancos de dados para ajudar a melhorar os tempos de leitura de solicitações comuns. Ele é compatível com dois tipos de armazenamentos de dados: Redis e Memcached.

**Amazon DynamoDB Accelerator - DAX:** é um cache em memória do DynamoDB, ele ajuda a melhorar os tempos de resposta de milissegundos para microssegundos.
