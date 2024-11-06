# Material de estudos para certificação AWS AI Practitioner (AIF-C01)

## Machine Learning

### Machine Learning Supervisionada

Quando tem a supervisão de um humano, aqui basicamente vou informar uma quantidade de dados e passar uma instrução. Por exemplo envio várias imagens de casas e veículos e depois explico o que era cada uma para o aprendizado da máquina. Após isso, um modelo será criado onde ela saberá destinguir as próximas imagens.

### Machine Learning Não Supervisionada

Quando não tem a supervisão de um humano, aqui eu envio alguma informação sem descrever o que é, por exemplo a imagem de cachorros e gatos, e a máquina irá tentar separar com base nas caracteriscas que forem indentificadas, como tamanho, cor, tipo de orelha ou fucinho, e após o fim do treinamento vai ter uma estatística do aprendizado que foi realizado sem passarmos uma instrução.

### Machine Learning Reforçada

Quando forçamos ele aprender com seus próprios erros, basicamente após passar por um dos treinamentos mensionados anteriormente, iremos realizar perguntas sobre o assunto treinado, e com base nas respostas, iremos informar se ele acertou ou errou, com isso ele vai se ajustando para melhorar a porcentagem de acertos e corrigindo seu aprendizado.

## Engenharia de Prompt

### O que é um prompt?
O prompt é uma mensagem que usamos para solicitar algo, como o input que enviamos para o ChatGPT, quanto mais específico melhor, e também podemos listar algumas regras, para nossa IA não retornar dados sensíveis.

### Conteúdos de um prompt

Exemplo de um prompt para o ChatGPT:

```
Escreva uma história de um pai e um filho que estão planejando sair de férias para um acampamento. O pai adora acampar mas o filho prefere ficar mais em casa no seu telefone. Crie essa história com 3 parágrafos e no máximo 500 palavras.
```

Partes que existem em um Prompt:

1. **Instrução:** Escreva uma história de um pai e um filho que estão planejando sair de férias para um acampamento.
2. **Contexto:** Poderia falar que eles estão em algum local como na sala de estar (opcional).
3. **Entrada de dados:** O pai adora acampar mas o filho prefere ficar mais em casa no seu telefone.
4. **Saída de dados:** Crie essa história com 3 parágrafos e no máximo 500 palavras (formato ou caracteristicas).

Exemplo de output do ChatGPT:

```
João, um entusiasta de acampamentos, sempre sonhou em compartilhar essa paixão com seu filho, Lucas. Quando as férias de verão chegaram, ele decidiu que seria o momento perfeito para uma aventura ao ar livre. João passou semanas planejando tudo, desde a escolha do local até a preparação dos equipamentos. Ele falava com entusiasmo sobre as trilhas, as noites estreladas e o som da natureza, mas Lucas, de 12 anos, não parecia compartilhar o mesmo entusiasmo. Para ele, férias ideais incluíam ficar em casa, jogando videogame e conversando com amigos no telefone. `Pai, não precisa de Wi-Fi no meio da floresta?`, Lucas perguntou com desdém, sem imaginar que o verdadeiro objetivo do acampamento seria justamente desconectar.

No dia da partida, enquanto João animadamente carregava a mochila no carro, Lucas fazia cara feia, grudado na tela do celular. `Isso vai ser uma tortura`, ele pensou, enquanto colocava fones de ouvido. A viagem até o acampamento foi longa, e João tentou puxar conversa sobre as aventuras que eles teriam, mas Lucas estava distraído com seus jogos. Quando chegaram ao destino, uma bela área montanhosa, João respirou fundo e sorriu ao ver o lugar que ele tanto esperava explorar com o filho. `Vamos montar a barraca e depois fazer uma trilha`, ele disse. Lucas, por outro lado, apenas deu de ombros, ainda frustrado com a falta de sinal de internet.

Conforme os dias passavam, algo inesperado aconteceu. Aos poucos, Lucas começou a se interessar pelo que estava ao redor. Ele se encantou ao ver o céu limpo e estrelado, ficou fascinado com o som dos pássaros e, surpreendentemente, até pediu para ajudar o pai a acender a fogueira. O que começou como uma experiência indesejada, logo se tornou uma oportunidade de conexão verdadeira. João percebeu que seu filho estava finalmente presente, longe das distrações digitais. Na última noite de acampamento, os dois sentaram lado a lado, em silêncio, observando as estrelas. `Pai, até que isso foi legal`, Lucas disse, com um sorriso tímido. João sabia que aquela pequena vitória significava muito mais do que qualquer conexão com a internet poderia oferecer.
```

### Boas práticas para o Prompt

1. Adicione contexto
2. Claro e objetivo
3. Especificar como queremos o output
4. Adicionar exemplos
5. Caso tenha mais de uma tarefa, utilize `Step By Step` (Envie um passo a passo para que faça as tarefas em etapas)

### Tipos de Prompt

- **Zero-shot:** quando solicita algo sem passar nenhum exemplo
- **One-shot:** quando passa apenas um exemplo
- **Two-shot:** quando passa mais de um exemplo
- **Chain Of Thought - CoT:** quando envia um passo a passo

## Amazon Bedrock

Serviço da aws que possibilita trabalhar com `Gen-AI` de forma customizada, onde podemos treinar modelos com dados específicos para gerar conteúdos e respostas relevantes para certos casos de uso.

Exemplos de utilização:

- Chatbot, podemos treinar ele com dados para ser capaz de responder a perguntas, como chat de suporte tecnico ou dúvidas de conteúdos de produtos relacionados a uma empresa.

- Data Augmentation, utilizado para geração de dados, quando estamos treinando uma ML e precisamos de muitos dados mas não temos tantas fontes assim, podemos criar dados aleatórios no formato esperado.

- Sugestão de produtos similares em sites de vendas, com base em preferências e padrões do usuário.

### Foundation Models - FM

São modelos de IA já treinados e prontos para serem usados, mas de acordo com a quantidade de dados que alimentamos ele. Existem modelos da Amazon e de outras empresas de IA, cada modelo tem sua descrição se é utilizado para trabalhar com texto, imagem ou ambos e podemos comparar os modelos para ver o que se encaixa melhor em cada cenário de uso específico, com base em tempo de resposta e valores por cada pergunta/resposta.

### Preços

Para falar de preços é preciso entender o conceito de `Tokens`, eles são as unidades básicas de processamento em serviços de IA como o Amazon Bedrock. Cada token pode ser uma palavra, parte de uma palavra, ou até mesmo um caractere, dependendo da estrutura do texto que está sendo processado. Em termos práticos, um prompt ou resposta é contado em tokens, o que afeta diretamente o custo de cada requisição.

Como Funcionam os Tokens:
  
  1. **Contagem:** Cada entrada e saída do modelo é medida em tokens. Por exemplo, a frase `O gato está na casa.` pode ser contada como cinco tokens: `O`, `gato`, `está`, `na`, `casa`. Textos longos e complexos terão mais tokens, influenciando o custo.
  2. **Custo:** Os provedores de serviços cobram com base na quantidade de tokens processados. Isso significa que, quanto mais tokens existir em uma interação com o modelo, maior será o custo. Os preços podem variar entre diferentes modelos de IA.
  3. **Limites de Tokens:** Os modelos têm um limite máximo de tokens que podem ser processados em uma única requisição. Isso inclui tanto os tokens de entrada quanto os de saída. Se o limite for ultrapassado, a entrada pode ser truncada, resultando em uma resposta incompleta ou errada.
  4. **Eficiência:** Ao otimizar o uso de tokens (por exemplo, tornando prompts mais diretos e claros), você pode reduzir os custos e aumentar a eficiência do seu uso da IA.

Modelos de preços para os FMs no Bedrock

- **Sob demanda:** Paga-se apenas pelos tokens processados (entrada e saída) em cada requisição. É um modelo flexível, ideal para usos que variam em intensidade.
- **Lote (Batch):** Permite processar grandes volumes de dados em lotes, o que pode ser mais econômico para operações de alto volume, especialmente em inferências offline (previsões ou análises em grande volume de dados onde a resposta imediata não é necessária), podemos enviar um conjunto de dados de entrada para o modelo e receber as saídas correspondentes em um único processamento, em vez de fazer chamadas em tempo real para cada entrada.
- **Throughput provisionado:** Ideal para cargas de trabalho consistentes. Throughput (taxa de processamento) é a medida pelo número máximo de tokens de entrada ou saída processados por minuto, ao provisionar você garante uma capacidade fixa e previsível para processamento, com um custo geralmente mais baixo por token, cobrado por hora e podendo fixar um compromisso de 1 ou 6 meses. Modelos personalizados só podem ser acessados usando throughput provisionado.
- **Personalização de modelos:** Alguns modelos permitem a customização, onde você paga um custo adicional para treinar ou ajustar o modelo com seus próprios dados, aumentando a relevância das respostas.
- **Avaliação do modelo:** Normalmente, as empresas oferecem testes gratuitos ou descontos para avaliação do modelo. Isso permite validar o desempenho antes de um compromisso maior.

### Criando uma FM customizada

Para criar um Foundation Model (FM) customizado na AWS, há dois processos principais:

1. **Fine-Tuning** (Ajuste fino)

   - No fine-tuning, treinamos o modelo `uma única vez` para adaptá-lo a uma tarefa específica ou ajustar seu comportamento para um domínio de dados específico.
   - Esse ajuste é feito de forma que o modelo aprenda características e padrões adicionais sem alterar seu conhecimento base.
   - Após configurado, iniciamos o processo usando o modo de `Create Fine-Tuning` e aguardamos o modelo ser ajustado para nossas necessidades.

2. **Continued Pre-training** (Treinamento contínuo)

   - O continued pre-training permite que o modelo `continue aprendendo` e se adapte continuamente conforme novos dados são adicionados. Isso é útil quando o domínio de dados está sempre evoluindo ou mudando.
   - Para isso, iniciamos um `Create Continued Pre-Training job`, onde o modelo mantém o aprendizado sobre os novos dados.
   - É necessário que todos os dados de treinamento estejam armazenados no Amazon S3. Dessa forma, o modelo pode acessar os dados diretamente, garantindo eficiência e escalabilidade no treinamento.

Ambos os processos aproveitam dados no S3 e possibilitam criar uma FM ajustada aos objetivos específicos de empresas ou aplicações.

### Avaliando um modelo FM

Para avaliar um `Foundation Model` (`FM`) customizado, existem três abordagens de avaliação para verificar a precisão e a relevância das respostas geradas pela IA:

1. **Avaliação Automática**
   - Fluxo: `Texto de entrada -> FM -> Geração de texto pela IA Generativa -> Modelo de avaliação automática -> Retorno da resposta`.
   - Neste caso, o processo de validação é totalmente automatizado. Após a geração do texto pela IA, um modelo de avaliação automática (`JUDGE MODEL`) revisa a resposta, onde baseado nos pametros que o Bedrock utiliza, ele vai identificar se o texto gerado está correto, determinando sua precisão e conformidade com os objetivos.
   - Vantagem: Rápido e escalável para avaliar grandes volumes de respostas.

2. **Avaliação Humana com Equipe Própria**
   - Fluxo: `Texto de entrada -> FM -> Geração de texto pela IA -> Humano da sua equipe -> Retorno da resposta`.
   - Aqui, um humano da sua própria equipe revisa a resposta gerada pela IA, garantindo que ela esteja alinhada com os critérios específicos do seu negócio.
   - Vantagem: Oferece controle direto sobre a qualidade da revisão, com a flexibilidade de adaptar o julgamento humano a critérios personalizados.

3. **Avaliação Humana com Equipe Gerida pela AWS**
   - Fluxo: `Texto de entrada -> FM -> Geração de texto pela IA -> Humano gerido pela AWS -> Retorno da resposta`.
   - Nesta opção, uma equipe de revisão humana gerida pela AWS é responsável por verificar a precisão e a adequação das respostas geradas.
   - Vantagem: Pode ser uma alternativa interessante se você não tiver uma equipe dedicada, pois a AWS gerencia o processo de avaliação humana.

Essas abordagens possibilitam ajustes no nível de controle e eficiência, dependendo dos recursos e do objetivo da sua aplicação de IA.

### Bedrock Guardrail

Aqui é onde filtramos o que pode sair na resposta da nossa IA, para evitar conteúdos indevidos e sensíveis para o usuário final. Podemos criar filtros com base em tópicos, palavras, informações sensíveis como documentos de uma empresa, podemos controlar o `grounding check` referente a fatos atuais e o `relevance` referente ao nível de alucinação da IA se ela vai ser mais precisa ou mais criativa, podemos controlar todas essas porcentagens para modelar nossas respostas.

### Bedrock Agents

É um recurso da AWS que oferece modelos de IA generativa pré-treinados para facilitar a criação de assistentes virtuais. Utilizado para se "`passar por um ser humano`", ele utiliza modelos de linguagem, como os da família de modelos Bedrock, para realizar tarefas complexas, como interações automatizadas, respostas a perguntas simulando interações humanas de maneira fluida e execução de fluxos de trabalho automatizados, permitindo uma fácil integração em aplicações empresariais.

### Bedrock RAG e KB

O conceito de `RAG` (`Retrieval-Augmented Generation`) e `KB` (`Knowledge Base`) são componentes importantes para melhorar as respostas de IA com dados específicos e atualizados.

Explicação do Processo

   1. **RAG (Retrieval-Augmented Generation):** O RAG permite que a IA consulte fontes específicas de dados para complementar suas respostas. Em vez de se basear apenas no treinamento original, a IA faz uma "recuperação" de dados que podem estar em uma base de conhecimento (`KB`) atualizada. Esse método é útil em situações em que a IA precisa de informações específicas e atualizadas, como detalhes de produtos ou políticas internas.
	•	Fluxo RAG: No fluxo padrão (`Pergunta -> FM -> Resposta`), a IA utiliza apenas o conhecimento treinado no `Foundation Model` (`FM`). Já com o RAG, a IA consulta dados específicos do KB antes de gerar a resposta (`Pergunta -> KB -> FM -> Resposta`).

   2. **Knowledge Base (KB):** A base de conhecimento armazena dados empresariais e outras informações específicas, como manuais, sites, documentos internos e PDFs. O KB pode ser atualizado regularmente, permitindo que o modelo acesse dados novos sem precisar passar por um novo treinamento completo.

#### Vector Database no KB

Quando usamos o RAG para respostas personalizadas, a IA consulta a KB que contém dados específicos da empresa, porém, ao invés de buscar diretamente nesses documentos, o RAG usa um `vector database` para fazer essa consulta de forma eficiente e precisa.

Um vector database armazena dados na forma de vetores (listas de números) que representam características semânticas desses dados. Por exemplo, um documento sobre "novidades de um produto" é transformado em um vetor que representa as principais ideias e contextos desse documento.

Quando a IA recebe uma pergunta específica, o vector database ajuda a comparar o vetor da pergunta com os vetores armazenados na KB. Essa comparação permite que a IA encontre documentos ou informações com conteúdos mais próximos e relevantes para a pergunta. Assim, o vector database facilita a busca por similaridade, o que torna a resposta da IA mais precisa e focada no contexto fornecido pelo KB, sem precisar re-treinar o modelo para cada novo dado.

Em resumo, o vector database é uma camada que torna a consulta rápida e contextualmente relevante, permitindo que o RAG use dados externos de forma eficaz ao gerar respostas.

Vantagens:
   - **Atualização Constante:** Com o KB, dados específicos e atualizados podem ser facilmente incorporados sem treinar o modelo novamente.
   - **Personalização:** O KB permite adaptar o modelo com informações exclusivas da empresa, proporcionando respostas mais precisas em perguntas específicas.

Em resumo, o `RAG` combinado com o `KB` e o `vector database` amplia a capacidade da IA de responder perguntas com precisão, trazendo dados mais relevantes e continuamente atualizados para a resposta final.

### Machine Learning Inference

Inferência é quando um modelo de Machine Learning (ML) usa o que aprendeu durante o treinamento para fazer `previsões` ou responder a perguntas sobre `novos dados`. Em vez de ensinar o modelo novamente, você simplesmente fornece novos dados e o modelo gera uma resposta.

Como Funciona?

   1. Entradas Novas: Você dá ao modelo dados que ele nunca viu antes.
   2. Processamento: O modelo analisa esses dados usando o que aprendeu.
   3. Saída: O modelo fornece uma resposta ou previsão.

Tipos de Inferência

   - **Em Tempo Real:** O modelo responde rapidamente, como em assistentes de voz ou recomendações de produtos.
   - **Em Lote:** O modelo processa um grande número de dados ao mesmo tempo, como analisar um conjunto de dados de vendas.

Resumindo

A inferência é a aplicação prática do que um modelo de ML aprendeu, permitindo que ele faça previsões e ofereça respostas com base em novos dados. É uma etapa essencial para utilizar modelos de ML em situações do dia a dia, como prever tendências ou categorizar informações.

## Amazon Q

O Amazon Q e o Amazon Q Business são versões distintas do assistente generativo da AWS, cada uma com funcionalidades adaptadas a diferentes necessidades empresariais. Enquanto o Amazon Q é voltado para desenvolvedores e equipes de TI, integrando-se em ambientes de desenvolvimento como a AWS CLI, IDEs e Slack, o Amazon Q Business é mais voltado para uso corporativo em geral, permitindo que qualquer funcionário tenha acesso rápido a informações e soluções de tarefas repetitivas.

### Amazon Q Business

O Amazon Q Business é um assistente totalmente gerenciado e alimentado por IA generativa que pode ser configurado para responder perguntas, fornecer resumos, gerar conteúdo e concluir tarefas com base em dados empresariais. 

Também ajuda a simplificar tarefas e acelerar a resolução de problemas, podendo automatizar tarefas ou executar ações de rotina, como enviar solicitações de folga e enviar convites para reuniões.

O Amazon Q possuí duas partes:

   - **Data conector:** são fontes de dados onde o Amazon Q vai consultar para obter informações, aqui vai desde banco de dados, S3, RDS, Aurora, até o Google Drive e Slack entre diversas outras.
   - **Plugins:** permite executar tarefas externas apenas por meio do AmazonQ, por exemplo abrir um chamado no Jira. Ele tem integração com outros serviços também como Zendesk, ServiceNow, entre outros, e permite a criação de plugins personalisados que vão executar APIs, com isso podemos conectar qualquer aplicação que utilizamos em nossa empresa.

### Amazon Q Developer

Utilizado para apoiar o ciclo de vida de desenvolvimento de software, com foco em geração de código, documentação e automação de segurança. Ele inclui suporte a cenários como a modernização de código, geração automática de sugestões e detecção de vulnerabilidades em código, melhorando a produtividade de equipes técnicas e reduzindo o débito técnico, podendo ser utilizado em uma extensão do VsCode.

## Sage Maker

Utilizado para criar modelos de machine learning. Ele remove o trabalho difícil do processo de criar, treinar e implantar modelos de ML rapidamente. Existem alguns modelos base mas podemos criar um do zero também. No fluxo de desenvolvimento, primeiro coletamos e preparamos os dados e depois criamos e treinamos nosso modelo, por fim realizamos o deploy e monitoramento dos resultados. Na etapa de deploy com um único clique implementamos o modelo para endpoints de inferência em tempo real ou em lotes e podemos realizar o monitoramento por ferramentas do SageMaker facilitando ajustes e retreinamentos.

Fluxo: `Data -> ML -> Deploy` || `Dados -> Criação e Treinamento do Modelo (ML) -> Deploy -> Monitoramento`

## Serviços de IA na AWS

**Amazon Comprehend:** descobre padrões ou sentimentos expressos em texto, para isso o serviço utiliza `processamento de linguagem natural` (`NLP`) que usa Machine Learning.

**Amazon Translate:** utilizado para tradução de textos.

**Amazon Transcribe:** converte fala em texto. Para isso, ele utiliza o sistema `Automatic Speech Recognition` (`ASR`), capaz de entender diversas línguas, e também oferece suporte à detecção de `Personally Identifiable Information` (`PII`), que identifica e oculta dados sensíveis, como documentos e números de telefone.​

**Amazon Polly:** converte texto em fala.

**Amazon Rekognition:** Identifica pessoas, textos e objetos em imagens.

**Amazon Lex:** cria chatbots de voz e texto. É o sitema utilizado nos dispositivos Alexa, utiliza `Automatic Speech Recognition` (`ASR`) para converter fala em texto e `Natural Language Understanding` (`NLU`) para entender o que estamos falando ou pedindo.

**Amazon Textract:** extrai textos de imagens.

**Amazon Kendra:** aprendizado de máquina sobre grande volume de dados para realizar buscas de respostas precisas.

**Amazon Forecast:** cria previsões com base nos dados fornecidos. Ele usa Machine Learning para gerar previsões precisas a partir dos dados inseridos, considerando padrões históricos e outros fatores relevantes.

**Amazon Personalize:** utiliza Machine Learning para criar recomendações personalizadas em tempo real para usuários, como sugestões de produtos em sites de compras, filmes, músicas ou qualquer outro tipo de conteúdo, com base no comportamento dos usuários e nas interações anteriores.

**Amazon Mechanical Turk:** Local onde empresas publicam serviços que precisam ser feitos por humanos, `Human Intelligence Tasks` (`HITs`), e as pessoas recebem após a conclusão da tarefa.

**Amazon Augmented AI - A2I:** facilita a integração de revisões humanas com base nas respostas da IA. O A2I permite que certas respostas geradas pela IA, quando classificadas como incertas ou críticas, sejam encaminhadas para uma equipe humana revisar (que pode ser composta por funcionários da sua empresa ou trabalhadores do Amazon Mechanical Turk). Após a análise humana, a decisão é enviada de volta para o sistema, mas a IA em si não aprende automaticamente com essa revisão, mas essas intervenções humanas podem ser usadas para treinar o modelo novamente e aumentar sua precisão. O objetivo é garantir que a qualidade das respostas melhore com a intervenção humana onde necessário.

**Amazon DeepRacer:** é uma plataforma de aprendizado desenvolvida pela AWS para ensinar e praticar `reinforcement learning` (aprendizado por reforço) por meio de competições de corridas autônomas de carros em miniatura. Ele oferece um carro em escala 1/18 totalmente autônomo, que os usuários podem treinar em simulações virtuais ou físicas para correr em pistas usando algoritmos de machine learning. A AWS organiza uma competição chamada `AWS DeepRacer League`, onde os participantes podem competir globalmente com seus modelos de machine learning.

**Amazon Fraud Detector:** Identifica atividades on-line potencialmente fraudulentas.

**Amazon CodeWhisperer:** Receba recomendações enquanto escreve e identifica problemas de segurança no seu código.

## Práticas e Responsabilidades de IA

### Responsabilidades com IA

- **Privacidade e Segurança:** Devemos ter cuidado com a origem de onde os dados que iremos usar no treinamento de nossa IA estão vindo, devemos usar dados públicos ou ter autorização do proprietário de dados privados. E ao utilizar dados privados não deixar o modelo livre para qualquer um utilizar.
- **Controlabilidade:** Devemos garantir que os dados gerados pela nossa IA respeitem os valores humanos e que sejam éticos. Existem ferramentas para auxiliar essa parte.
- **Veracidade:** Devemos garantir a veracidade dos dados usados no treinamento do modelo, para garantir que as respostas sejam verdadeiras e não duvidosas.
- **Robusta:** Garantir a alta escalabilidade da minha aplicação. Os serviços de IA que são gerenciados pela AWS já possuem suporte a escalabilidade devido a infraestrutura da Amazon.
- **Transparencia:** Ter transparencia de como a IA funciona e como chegou na resposta, um exemplo disso é em alguns retornos do ChatGPT que agora possuem a fonte de sites que ele consultou para chegar na resposta.

### Conformidade com IA

A conformidade(compliance) com IA envolve garantir que os sistemas de inteligência artificial sigam padrões rigorosos de segurança, privacidade e ética. Organizações e países frequentemente precisam cumprir regulamentações específicas e certificações para demonstrar que suas operações com IA são seguras, confiáveis e protegidas. A AWS, com sua extensa infraestrutura de nuvem, apoia conformidade atualmente com 143 certificações globais e padrões de segurança, uma delas é a ISO 9001.

Essas certificações cobrem aspectos essenciais, como

  1. **Segurança de Dados:** Proteger dados contra acesso não autorizado.
  2. **Privacidade:** Garantir que os dados dos usuários sejam manipulados conforme os regulamentos de privacidade, como o GDPR na União Europeia.
  3. **Gestão de Qualidade:** Certificações como ISO 9001 garantem que processos de IA e ML sejam projetados para gerar resultados consistentes e de alta qualidade.
  4. **Conformidade Legal:** Cumprir regulamentações locais e globais ajuda as empresas a operar legalmente em diferentes países e setores.

### Serviços IA para responsabilidade

Abaixo para cada serviço da AWS listo algumas ferramentas que podem ajudar a garantir a responsabilidade e conformidade ao desenvolver e implantar IA:

#### AWS SageMaker

- **ClariFy:** realiza verificação de conteúdo tóxico,  `bias detection` (se o modelo favorece mais um lado que o outro), a robustez da plataforma e a precisão das respostas, garantindo que o modelo seja justo e ético.
- **Data Wrangler:** ele verifica a parte de `bias datasets` (se o modelo favorece mais um lado que o outro mas para grande quantidade de dados).
- **Model Monitor:** monitora continuamente a qualidade e o desempenho do que é produzido pelo modelo em produção.

#### AWS Bedrock
- **Verificação Humana:** permite revisões humanas automáticas do conteúdo gerado por modelos FMs.
- **Guardrails:** inclui restrições de segurança como bloqueio de `PII` (informação pessoal identificável) dados sensíveis de documentos pessoais e endereços, filtra conteúdos inadequados e nega tópicos específicos nas respostas.

#### Augmented AI (A2I)
- **Revisões humanas do modelo de AI:** Utiliza intervenções humanas para verificar respostas de IA em situações onde a precisão é crítica ou quando o modelo gera respostas incertas. Após a revisão, a decisão humana é incorporada, garantindo uma supervisão adicional para melhorar a qualidade do modelo.

Essas ferramentas ajudam as empresas a manter altos padrões éticos e de segurança ao longo de todo o ciclo de vida dos modelos, desde a preparação dos dados até a verificação em produção.

### Governança com IA

A governança com IA refere-se a práticas estruturadas para garantir que soluções de IA desenvolvidas por uma empresa estejam alinhadas com valores éticos, segurança e transparência. Esse processo envolve criar uma estrutura confiável e organizada que ajude a demonstrar ao público e às partes interessadas como a IA é desenvolvida e supervisionada dentro da empresa.

Para isso devemos passar o máximo de confiabilidade do que estamos fazendo com nossas soluções de IA para outras empresas, clientes ou serviços que estamos oferendo ao público. Mostrar como funciona o departamento de desenvolvimento de IA, quanto mais organizado melhor. Por exemplo, falar que o departamento possuí um time de diretores, advogados e experts do assunto que estão sempre analisando e aprovando as soluções de IA desenvolvidas e que cada um deles seguem regras, processos e funções que devem ser seguidas.

A governança com IA não só fortalece a confiança do cliente e a credibilidade da empresa, como também ajuda a mitigar riscos, estabelecendo uma linha clara de responsabilidade e promovendo um desenvolvimento de IA transparente e responsável.

### Segurança com GenAI

Os escopos vão do mais baixo até o mais alto nível de responsabilidade sobre a segurança no uso da solução de IA.

Escopos:
  - **Consumer APP:** quando somos os consumidores, usando uma IA generativa de terceiros, como chatGPT, aqui não precisamos se preocupar com a segurança e se algo der errado na IA não somos processados.
  - **Enterprise APP:** quando usamos uma aplicação Saas com IA generativa como Salesforce, aqui podemos customizar o serviço, temos um pouco mais de responsabilidade em cima da customização.
  - **Pre-trained Models:** quando usamos modelos pré treinados, como Amazon Bedbrock, nesse caso temos algumas responsabilidades como quem acessa e quem tem permissão para treinar algo novo nesse modelo.
  - **Fine-tuned Models:** quando pegamos modelos pré treinados, como Amazon Bedbrock mas realizamos modificações no modelo(`tuning`), como treinar o modelo com novos dados, aqui temos maior responsabilidade sobre o que foi alterado nele, a origem desses dados e devemos documentar as alterações feitas no modelo.
  - **Self-trained Models:** ao criar e treinar modelos do zero, como com o Amazon SageMaker, assumimos o nível mais alto de responsabilidade, abrangindo o controle completo sobre a segurança dos dados de treinamento, a arquitetura do modelo, o gerenciamento de acessos, e a transparência sobre as decisões e seu funcionamento, já que somos os criadores dessa IA.

#### Fonte:
---

- [Serviços de IA da AWS](https://aws.amazon.com/pt/ai/services/)

- Cursos:
[Certificação Amazon Certified AWS AI Practitioner AIF-C01)](https://www.udemy.com/course/certificacao-amazon-aws-ai-practitioner/?couponCode=KEEPLEARNING)

- Prova:
[AWS Certified AI Practitioner](https://aws.amazon.com/pt/certification/certified-ai-practitioner/?ch=sec&sec=rmg&d=1)
