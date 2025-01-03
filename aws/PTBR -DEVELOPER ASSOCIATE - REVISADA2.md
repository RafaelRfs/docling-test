AWS DEVELOPER ASSOCIATE

 Associate



ÍNDICE

 Associate



API REST x API HTTP x API Websocket	58

Variáveis de estágio de integração proxy	58

versus não proxy	59

Modelos de mapeamento	60

invalidando o	62

compartilhamento de recursos entre origens do cache (CORS)	62

Autorizadores	64

Planos de uso	66

Amazon DynamoDB	67

Componentes principais	67

Índice Secundário Local vs. Índice Secundário Global (LSI vs. GSI)	68

Operações de	69

verificação e consulta de	69

projeções Calculando a unidade de capacidade de leitura e gravação necessária para sua tabela do	70

DynamoDB Fluxos do	73

DynamoDB DynamoDB Accelerator (DAX)	75

Transações do DynamoDB	77

Tempo de vida do DynamoDB (TTL)	78

Tabelas globais do DynamoDB	79

AWS CloudFormation	81

Pilha	81

Partes do modelo CloudFormation	81

Funções intrínsecas e pseudoparâmetros	82

Usando referências dinâmicas para passar credenciais com segurança Modelo de aplicativo sem servidor da AWS (SAM)

Modelo SAM

Comandos SAM CLI comumente usados

Funções de etapas da AWS

Estados

Processamento de entrada e saída AWS ElasticBeanstalk

Políticas de implantação Implantação azul/

verde .ebextensions

Política de ciclo de vida de aplicativos

Interface de linha de comando EB (CLI)

84

86

86

87

88

88

89

96

96

102

104

105

107

	2

Serviço de fila simples da Amazon (SQS) Fila padrão versus fila FIFO Conceitos

Grupo de usuários do

Amazon Cognito versus grupo de

identidades Concedendo acesso para identidades não autenticadas

AWS Amplify Amplify Studio

Hospedagem do Amplify

Bibliotecas do AWS Amplify Interface de linha de comando do Amplify AWS CodeCommit

Autenticação de acesso (HTTPS) no CodeCommit AWS CodeBuild

Arquivo de especificação de construção

108

108

108

110

110

114

115

115

115

116

116

116

117

118

118

Integrações com outros serviços AWS	118

AWS CodeDeploy

Configurações de implantação

Arquivo AppSpec

Grupos de implantação AWS Code Pipeline

Ações de aprovação manual AWS CodeArtifact

AWS CodeStar Amazon Code Guru

Serviço de gerenciamento de chaves da AWS (KMS)

Chave AWS KMS Criptografia de envelope

120

120

121

123

124

124

126

127

128

129

129

130

API KMS	130

Amazon Cloud Front

Política de protocolo do visualizador versus política de protocolo de origem

Gatilhos de eventos do CloudFront

Funções Lambda@Edge vs CloudFront Amazon S3

Classes de armazenamento de objetos

Duração mínima de armazenamento

132

132

133

135

136

136

138

	3

Criptografia Amazon S3

Notificações de eventos S3

Objeto S3 Lambda

Outros recursos importantes do bucket S3

Raio X da AWS

Conceitos chave Amazon Event Bridge

Acesso entre contas ao Event Bus

Amazon CloudWatch

Publicação de métricas personalizadas

Amazon CloudTrail Conceitos

Gerenciador de segredos da AWS

Armazenamento de parâmetros do AWS Systems Manager

Amazon EC2

Dados do usuário da instância versus metadados da instância

Grupo de escalonamento automático

Construtor de imagens EC2

Amazon Elastic Load Balancing (ELB)

Tipos de balanceador de carga

Balanceador de carga de rede (NLB) Balanceador de carga de gateway (GWLB)

Componentes ELB

Condições da regra do listener do balanceador de carga do aplicativo

Cabeçalhos com vários valores

Preservando o endereço IP do cliente usando o cabeçalho X-Forwarded-For Amazon Elasticache

Memcached x Redis

Estratégias de cache Amazon Kinesis

Fluxo de dados do Kinesis

Fragmentos

Modo de capacidade provisionada versus sob demanda Gravando e lendo dados em fragmentos

Dimensionamento, refragmentação e processamento paralelo

Mangueira de dados Kinesis

138

139

141

141

143

144

146

146

148

148

150

150

152

153

154

154

157

158

159

159

159

160

161

161

164

164

166

166

166

171

171

171

171

172

174

175

	4

 Associate



Amazon Elastic Container Service (ECS)

Função de instância de contêiner do Amazon ECS versus função de execução de tarefa versus função de tarefa

Amazon OpenSearch Service (sucessor do Amazon Elasticsearch Service) Serviços Amazon Elastic Kubernetes (Amazon EKS)

Amazon Atenas

Kit de desenvolvimento de nuvem AWS (CDK) Rota Amazônica 53

Gerenciamento de DNS Gestão de tráfego

Firewall de aplicativos da Web da AWS (WAF) Amazon MemoryDB para Redis

AWS AppConfig AWS AppSync

Gerente de sistemas AWS Gerenciador de certificados AWS

COMPARAÇÃO DE SERVIÇOS AWS

S3 Standard vs S3 Standard-IA vs S3 One Zone-IA vs S3 Intelligent Tiering RDS versus DynamoDB

Índice Secundário Global vs Índice Secundário Local

Serviços de contêiner EC2 ECS vs Lambda

Elastic Beanstalk x CloudFormation x OpsWorks x CodeDeploy Grupo de segurança vs NACL

Balanceador de carga de aplicativo versus balanceador de carga de rede versus balanceador de carga de gateway

CloudTrail x CloudWatch CONSIDERAÇÕES FINAIS E DICAS SOBRE OS AUTORES

175

175

177

178

178

180

181

181

183

183

185

186

187

188

189

190

191

194

197

200

201

204

206

209

210

211

<!-- image -->

	5





INTRODUÇÃO

A tendência das tecnologias emergentes que têm um grande impacto nas indústrias é um tema comum nas manchetes de hoje.

Cada vez mais empresas estão adotando tecnologias mais recentes que lhes permitirão crescer e aumentar os retornos. A

nuvem Amazon Web Services (AWS) é um exemplo disso. Existem mais de um milhão de usuários ativos da Amazon Web Services. Esses usuários são uma mistura de pequenas empresas, prestadores de serviços independentes, grandes empresas,

desenvolvedores, estudantes e muito mais. Não há dúvida de que a AWS já possui uma comunidade de usuários e o número de recém- chegados aumenta rapidamente a cada dia.

Com a AWS, você não precisa adquirir e gerenciar sua infraestrutura. É uma economia de custos considerável para sua empresa e também um suspiro de alívio para sua equipe de administração de sistemas. Embora a AWS ofereça uma enorme coleção de serviços e produtos que exigem pouca configuração, ela também oferece serviços tradicionais, como VMs e dispositivos de armazenamento, que funcionam de maneira semelhante aos seus equivalentes físicos. Isso significa que a transição de um tipo de ambiente local para um ambiente virtualizado da AWS deve ser simples.

Acreditamos que os desenvolvedores são os que mais se beneficiam da nuvem. Você pode acessar seus aplicativos de qualquer lugar se tiver um navegador e uma conexão com a Internet (e talvez um cliente SSH/RDP também). Você pode ativar máquinas em questão de minutos a partir de um catálogo de sistemas operacionais e versões que atendem às suas necessidades. Você também tem controle sobre seus dispositivos de armazenamento, que também podem ser provisionados e desprovisionados facilmente. Além das VMs tradicionais, a AWS também oferece outras opções, como instâncias de contêiner, instâncias em lote e modelos sem servidor que podem ser facilmente integrados a APIs. Você também não precisa se preocupar com bancos de dados. Você pode hospedá-los

por conta própria em VMs com suas próprias licenças ou usar licenças fornecidas pela AWS, ou pode até usar um banco de dados gerenciado, para não precisar se preocupar com infraestrutura. Se isso for demais para um aplicativo simples que você deseja apenas testar, a AWS tem uma solução de plataforma como serviço na qual você pode simplesmente implantar seu código e o serviço cuidará da infraestrutura para você. Em essência, a AWS já forneceu as ferramentas de que seus usuários precisam para aproveitar rapidamente as vantagens da nuvem.

Com todos os benefícios apresentados no uso da AWS, o verdadeiro valor de ser um AWS Certified Developer tem seu conhecimento e habilidades em desenvolvimento na AWS reconhecidos pelo setor. Com esse reconhecimento, você obterá mais oportunidades de crescimento profissional, financeiro e também pessoal. Indivíduos certificados podem negociar salários mais altos, buscar

promoções ou conseguir cargos mais elevados. Tornar-se um AWS Certified Developer Associate também é uma ótima maneira

de começar sua jornada no DevOps, que é uma das funções mais requisitadas e bem remuneradas no setor de TI atualmente. Este certificado é essencial em seu portfólio se você deseja progredir em sua carreira na AWS.

Observação: tomamos cuidado extra ao criar esses guias de estudo e folhas de dicas. No entanto, este pretende ser apenas um recurso complementar na preparação para o exame. É altamente recomendável trabalhar em sessões práticas e exames práticos para expandir ainda mais seu conhecimento e melhorar suas habilidades para fazer testes.

	6

 Associate



VISÃO GERAL DO EXAME DE ASSOCIADO DE DESENVOLVEDOR CERTIFIED DA AWS

A Amazon Web Services (AWS) iniciou o Programa de Certificação Global com o objetivo principal de validar o habilidades técnicas e conhecimento para criar aplicativos baseados em nuvem seguros e confiáveis usando a AWS

plataforma. Ao passar com êxito no exame da AWS, os indivíduos podem comprovar seu conhecimento em AWS para seus conhecimentos atuais e futuros empregadores.

O exame AWS Certified Solutions Architect - Associate foi a primeira certificação AWS lançada em

2013, seguido por duas outras certificações baseadas em funções: Administrador de Operações de Sistemas (SysOps) e Desenvolvedor associado no final daquele ano. A AWS está sempre lançando novos serviços e recursos de desenvolvimento em seus plataforma em nuvem; portanto, há um fluxo contínuo de atualizações sobre o conteúdo do exame. Algumas mudanças são pequenas uns, enquanto outros são atualizações importantes que revisam todo o teste de certificação.

A primeira versão do exame AWS Certified Developer - Associate (DVA-C00) foi lançada em janeiro

2014. Quatro anos depois, em junho de 2018, a AWS lançou a versão atualizada deste teste com um código de exame de

DVA-C01. A AWS revelou a terceira iteração deste teste com DVA-C02 como seu código de exame mais recente. Você pode notar que para cada atualização importante do exame, o último dígito do código do exame é incrementado, então espere que o próximo será denominado DVA-C03 após vários anos. É muito importante conhecer os detalhes relevantes do exame AWS

versão para garantir que você esteja usando materiais de revisão atualizados.

Detalhes do exame

O exame AWS Certified Developer - Associate é destinado a indivíduos que realizam um desenvolvimento

função e ter um ou mais anos de experiência prática no desenvolvimento e manutenção de um sistema baseado em AWS aplicativo.

Código do exame:

Nº de perguntas:

Faixa de pontuação: Custo:

Pontuação de aprovação:

Limite de tempo:

DOIS-C02 65

100/1000

150 dólares 720/1000

2 horas e 10 minutos (130 minutos)

<!-- image -->

Método de Entrega:	Centro de testes ou exame supervisionado on-line

	7





Domínios de exame

O exame AWS Certified Developer - Associate tem quatro (4) domínios diferentes, cada um com peso e cobertura de tópico correspondentes. Os domínios do exame são Desenvolvimento com serviços AWS (32%), Segurança (26%), Implantação (24%) e Solução de problemas e

otimização (18%)

Domínio 1: Desenvolvimento com serviços AWS (32%)

1.1 Desenvolver código para aplicativos hospedados na AWS 1.2 Desenvolver código para AWS Lambda 1.3

Usar armazenamentos de dados no desenvolvimento de aplicativos

Domínio 2: Segurança (26%)

2.1 Implementar autenticação e/ou autorização para aplicativos e serviços da AWS 2.2 Implementar criptografia usando serviços da AWS 2.3 Gerenciar dados confidenciais no

código do aplicativo.

Domínio 3: Implantação (24%)

- Prepare artefatos de aplicativos a serem implantados na AWS.
- Testar aplicativos em ambientes de desenvolvimento 3.3 Automatizar testes de implantação 3.4

Implantar código usando serviços AWS CI/CD.

Domínio 4: Solução de problemas e otimização (12%)

5.1 Auxiliar na análise de causa raiz. 5.2 Instrumentar código para observabilidade.

5.3 Otimize aplicativos usando serviços e recursos da AWS.

	8







<!-- image -->

Pontuação do exame

Você pode obter uma pontuação de 100 a 1.000 com uma pontuação mínima de aprovação de 720 ao fazer o exame AWS Certified Developer Associate. A AWS usa um modelo de pontuação em escala para associar pontuações em vários tipos de exames que podem ter diferentes níveis de dificuldade. Seu relatório completo de pontuação será enviado a você por

e-mail de 1 a 5 dias úteis após o exame. No entanto, assim que terminar o exame, você verá imediatamente uma notificação de aprovação ou reprovação na tela do teste.

Para indivíduos que infelizmente não passam nos exames, você deve esperar 14 dias antes de poder refazer o exame. Não há limite rígido para o número de tentativas que você pode refazer um exame. Depois de aprovado, você receberá vários benefícios, como um cupom de desconto que poderá usar em seu próximo exame da AWS.

Depois de receber seu relatório de pontuação por e-mail, o resultado também deverá estar salvo em sua conta AWS Certification. O relatório de pontuação contém uma tabela do seu desempenho em cada domínio e indicará se você atingiu o nível de competência exigido para esses domínios. Observe que você não precisa obter competência em todos os domínios para

passar no exame. No final do relatório, haverá uma tabela de pontuação de desempenho que destaca seus pontos fortes e fracos, o que o ajudará a determinar as áreas que você precisa melhorar.

	9

<!-- image -->

o

Benefícios do exame

Se você for aprovado em qualquer exame da AWS, terá direito aos seguintes benefícios:

- Desconto em exames - você receberá um voucher de 50% de desconto para solicitar sua recertificação ou qualquer outro exame que pretenda realizar. Para acessar o código do voucher de desconto, vá para a seção “Benefícios” da sua conta da AWS Certification e aplique o voucher ao se inscrever para o próximo exame.
- Loja certificada pela AWS : todos os profissionais certificados pela AWS teriam acesso a produtos exclusivos certificados pela AWS. Você pode obter acesso à sua loja na seção “Benefícios” da sua conta da AWS Certification.
- Selos Digitais de Certificação - Você pode mostrar suas conquistas para seus colegas e empregadores com selos digitais em suas assinaturas de e-mail, perfil do Linkedin ou em suas contas de mídia social. Você também pode mostrar seu selo digital para obter acesso exclusivo às salas de certificação na AWS re-invent, recepções de agradecimento regionais e eventos selecionados do AWS Summit. Para visualizar seus selos, vá para a seção “Selos digitais” da sua conta da AWS Certification.
- Elegibilidade para ingressar no AWS IQ: com o programa AWS IQ, você pode monetizar on-line suas habilidades na AWS, fornecendo assistência prática a clientes em todo o mundo. O AWS IQ ajudará você a se manter atualizado e bem versado em diversas tecnologias da AWS. Você pode trabalhar no conforto da sua casa e decidir quando ou onde deseja trabalhar.

Você pode visitar a página oficial de perguntas frequentes da AWS Certification para ver as perguntas frequentes sobre como obter a certificação AWS e outras informações sobre a certificação AWS: https://aws.amazon.com/certification/faqs/.

	10

<!-- image -->





EXAME DE ASSOCIADO DE DESENVOLVEDOR CERTIFIED DA AWS - GUIA DE ESTUDO E DICAS

A certificação AWS Certified Developer Associate é para aqueles que estão interessados em lidar com aplicativos

e serviços baseados em nuvem. Normalmente, os aplicativos desenvolvidos na AWS são vendidos como produtos no AWS Marketplace. Isso permite que outros clientes usem o aplicativo personalizado e compatível com a nuvem

para suas próprias necessidades comerciais. Por causa disso, os desenvolvedores da AWS devem ser proficientes no uso da AWS CLI, APIs e SDKs para desenvolvimento de aplicativos.

O exame AWS Certified Developer Associate (ou AWS CDA, abreviadamente) testará sua capacidade de:

- Demonstrar melhor compreensão dos principais serviços e usos da AWS e da arquitetura básica da AWS práticas.
- Demonstrar proficiência no desenvolvimento, implantação e depuração de aplicativos baseados em nuvem usando AWS.

Ter experiência anterior em programação e script para aplicativos padrão, em contêineres e/ou sem servidor facilitará muito sua análise. Além disso, recomendamos ter uma conta AWS disponível para você experimentar e visualizar melhor as partes da sua revisão que envolvem código. Para obter mais detalhes sobre o seu exame, você pode conferir este caminho de estudo do exame AWS.

Materiais de estudo

Se você não conhece bem os fundamentos da AWS, sugerimos que visite nosso guia de revisão do AWS Certified Cloud Practitioner para começar. A AWS também oferece um curso virtual gratuito chamado AWS Cloud Practitioner Essentials que você pode fazer em seu portal de treinamento. Conhecer os conceitos e serviços básicos da AWS tornará sua análise mais coerente e compreensível para você.

Os principais materiais de estudo que você usará para sua revisão são : curso de vídeo GRATUITO de preparação para exames da

AWS, exemplos de perguntas oficiais da AWS, white papers da AWS, perguntas frequentes, folhas de dicas da AWS, exames práticos da AWS e curso de vídeo da AWS com laboratórios práticos incluídos.

	11





<!-- image -->

Para white papers, eles incluem o seguinte:

- Implementação de microsserviços na AWS – Este artigo apresenta as maneiras de implementar um sistema de microsserviços em diferentes plataformas de computação da AWS. Você deve estudar como esses sistemas são construídos e o raciocínio por trás dos serviços escolhidos para esse sistema.

- Executando microsserviços em contêineres na AWS – Este artigo fala sobre as melhores práticas em

implantando um sistema de microsserviços em contêineres na AWS. Concentre-se nos cenários de exemplo onde as melhores práticas são aplicadas, como são aplicadas e quais serviços são usados para fazê-lo.

- Otimizando a economia empresarial com arquiteturas sem servidor – Leia sobre os casos de uso de serverless em diferentes plataformas. Entenda quando é melhor usar serverless em vez de manter seus próprios servidores. Além disso, familiarize-se com os serviços da AWS que estão no kit de ferramentas sem servidor.

- Arquiteturas sem servidor com AWS Lambda – Aprenda sobre Serverless e Lambda tanto quanto você pode. Conceitos, configurações, código e arquiteturas são importantes e provavelmente

	12

<!-- image -->



para aparecer no exame. Criar sua própria função Lambda ajudará você a lembrar os recursos com mais rapidez.

- Praticando integração contínua e entrega contínua em software de aceleração AWS

Entrega com DevOps – Se você é um desenvolvedor que busca o curso de DevOps, este whitepaper está repleto de práticas para você aprender. CI/CD envolve muitos estágios que permitem implantar seus aplicativos com mais rapidez. Portanto, você deve estudar os diferentes métodos de implantação e entender como cada um deles funciona. Além disso, familiarize-se com a implementação de CI/CD na AWS. Recomendamos realizar um laboratório disso em sua conta AWS.

- Implantações Azul/Verde na AWS – Implantações Azul/Verde é um método de implantação popular que você deve aprender como desenvolvedor AWS. Estude como as implantações azul/verde são implementadas e

conheça o conjunto de serviços AWS usados na implantação de aplicações. Também é crucial que você entenda os cenários em que as implantações azul/verde são benéficas e onde não são. NÃO misture seu ambiente azul com seu ambiente verde.

- Práticas recomendadas de segurança da AWS – Entenda as práticas recomendadas de segurança e sua finalidade em seu ambiente. Alguns serviços oferecem mais de uma forma de recurso de segurança, como vários esquemas de gerenciamento de chaves para criptografia. É importante que você possa determinar qual formulário é mais adequado para os cenários apresentados em seu exame.
- AWS Well-Architected Framework – Este whitepaper é um dos artigos mais importantes que você deve estudar para o exame. Ele discute os diferentes pilares que constituem um ambiente de nuvem bem arquitetado. Espere que os cenários do seu exame sejam fortemente baseados nesses pilares.

Cada pilar terá um whitepaper correspondente que discute o respectivo pilar com mais detalhes.

Serviços AWS para focar

A AWS oferece documentação extensa e perguntas frequentes bem escritas para todos os seus serviços. Esses dois serão sua principal fonte de informações ao estudar a AWS. Você precisa ter conhecimento de muitos produtos e serviços da AWS, pois quase sempre os usará em seu trabalho. Eu recomendo verificar as folhas de dicas da AWS do Tutorials Dojo, que fornecem um conjunto resumido, mas altamente informativo, de notas e dicas para sua revisão sobre

esses serviços.

Serviços para estudar:

	13





- Amazon EC2 / ELB / Auto Scaling – Sinta-se confortável com a integração do EC2 aos ELBs(ELASTIC LOAD BALANCERS) e ao Auto Scaling. Estude os comandos AWS CLI, APIs e código SDK comumente usados nesses serviços. Concentre-se também na segurança, mantendo a alta disponibilidade e permitindo a conectividade de rede do seu ELB

às suas instâncias do EC2. AWS Elastic Beanstalk – Saiba quando o Elastic Beanstalk é mais apropriado para uso do que outras soluções de computação ou infraestrutura como código, como CloudFormation ou

OpsWorks. Experimente você mesmo o serviço em sua conta AWS e entenda como você pode implantar e manter seu próprio aplicativo no Beanstalk.

- Amazon ECS – Estude como você pode gerenciar seu próprio cluster usando ECS. Além disso, descubra como o ECS pode ser integrado a um pipeline de CI/CD. Certifique-se de ler atentamente as perguntas frequentes, pois o exame inclui várias perguntas sobre contêineres.

- AWS Lambda – A melhor maneira de aprender Lambda é criar você mesmo uma função. Além disso, lembre-se de que o Lambda permite tempos de execução personalizados que o próprio cliente pode fornecer. Descubra

quais serviços podem ser integrados ao Lambda e como as funções do Lambda podem capturar e manipular eventos recebidos. Por último, estude o Serverless Application Model (SAM).

- Amazon RDS / Amazon Aurora – Entenda como o RDS se integra à sua aplicação por meio de EC2, ECS, Elastic Beanstalk e muito mais. Compare o RDS com o DynamoDB e o Elasticache e determine quando o RDS é melhor usado.

Além disso, saiba quando é melhor usar o Amazon Aurora do que o Amazon RDS e quando o RDS é mais útil do

que hospedar seu próprio banco de dados dentro de uma instância EC2.

- Amazon DynamoDB – Você deve ter um conhecimento completo do serviço DynamoDB, pois isso é muito importante em seu exame. Leia a documentação do DynamoDB, pois ela é mais detalhada e informativa que o FAQ. Como desenvolvedor, você também deve saber como provisionar sua própria tabela do DynamoDB e ser capaz de ajustar suas configurações para atender aos requisitos do aplicativo.

- Amazon Elasticache – Elasticache é um serviço de cache que você encontrará frequentemente no exame. Compare e contraste Redis do Memcached. Determine quando o Elasticache é mais adequado que o DynamoDB ou o RDS.

- Amazon S3 – S3 geralmente é o armazenamento preferido para objetos. Estude como você pode garantir seu objetos por meio de criptografia KMS, ACLs e políticas de bucket. Saiba como o S3 armazena seus objetos para mantê-los altamente duráveis e disponíveis. Além disso, aprenda sobre as políticas de ciclo de vida. Compare S3 com EBS e EFS para saber quando S3 é mais preferido que os outros dois.

- Amazon EFS – O EFS é usado para configurar sistemas de arquivos para várias instâncias do EC2. Comparar e compare S3 com EFS e EBS. Estude também a criptografia de arquivos e a otimização do desempenho do EFS.

	14

<!-- image -->



- Amazon Kinesis– Geralmente há perguntas complicadas sobre o Kinesis, então você deve ler seu documentação também. Concentre-se no Kinesis Data Streams e explore os outros serviços do Kinesis.

Familiarize-se com APIs do Kinesis, Kinesis Sharding e integração com serviços de armazenamento como S3 ou serviços de computação como AWS Lambda.

- Amazon API Gateway – o API Gateway geralmente é usado junto com o AWS Lambda como parte do modelo de aplicativo sem servidor. Entenda a estrutura do API Gateway, como recursos, estágios e métodos. Saiba como combinar o API Gateway com outros serviços da AWS, como Lambda ou CloudFront. Determine como você pode proteger

suas APIs para que apenas um número selecionado de pessoas possa executá-las.

- Amazon Cognito – Cognito é usado para autenticação móvel e web. Você geralmente encontra perguntas do Cognito no exame junto com Lambda, API Gateway e DynamoDB. Isso geralmente envolve algum aplicativo móvel que requer um recurso fácil de inscrição/login da AWS. É altamente recomendável que você tente usar o Cognito para entender melhor seus recursos.
- Amazon SQS – Estude a finalidade das diferentes filas SQS, tempos limite e como suas mensagens são tratadas dentro das filas. As mensagens em uma fila SQS não são excluídas quando pesquisadas, portanto, leia isso também. Existem diferentes mecanismos de pesquisa no SQS, portanto você deve comparar e contrastar cada um.
- Amazon CloudWatch – CloudWatch é uma ferramenta primária de monitoramento para todos os seus serviços AWS. Verifique se você sabe quais métricas podem ser encontradas no monitoramento do CloudWatch e quais métricas exigem a instalação de um agente do CloudWatch. Além disso, estude CloudWatch Logs, CloudWatch Alarms e

monitoramento de faturamento. Diferencie os tipos de logs armazenados no CloudWatch e os logs armazenados no CloudTrail.

- AWS IAM – IAM é o centro de segurança da sua nuvem. Portanto, você deve se familiarizar

com os diferentes recursos do IAM. Estude como as políticas do IAM são escritas e o que cada seção da política significa. Entenda o uso de funções de usuário e funções de serviço do IAM. Você deve ter lido o whitepaper de práticas recomendadas para proteger sua conta da AWS por meio do IAM.

- AWS KMS – KMS contém chaves que você usa para criptografar EBS, S3 e outros serviços. Saiba quais são esses serviços. Aprenda os diferentes tipos de chaves KMS e em quais situações cada tipo de chave é usado.

- AWS CodeBuild / AWS CodeCommit / AWS CodeDeploy / AWS CodePipeline – Estas são suas ferramentas para implementar CI/CD(Continuos Integration/Deploy) na AWS. Estude como você pode criar aplicativos no CodeBuild (buildspec) e como preparar arquivos de configuração (appspec) para o CodeDeploy.

CodeCommit é um repositório git, portanto, ter conhecimento em Git será benéfico. Sugiro que você crie seu próprio pipeline simples no CodePipeline para ver como deve gerenciar suas implantações de código. Também é importante aprender como você pode reverter para o aplicativo anterior

	15





versão após uma implantação com falha. Os whitepapers acima deveriam ter explicado as implantações locais e as implantações azul/verde e como realizar a automação.

- AWS CloudFormation – Estude a estrutura dos scripts CloudFormation e como você pode usar

para construir sua infraestrutura. Esteja confortável com os formatos JSON e YAML. Leia um pouco sobre StackSets.

Liste os serviços que usam CloudFormation no back-end para

provisionamento de recursos da AWS, como AWS SAM, e processos, como em CI/CD.

Além dos conceitos e serviços, você deve estudar a AWS CLI, as diferentes APIs comumente usadas (para serviços como EC2, EBS ou Lambda) e os AWS SDKs. Leia sobre o AWS Serverless Application Model (AWS SAM) e os AWS Server Migration Services, bem como aqueles que podem surgir no exame. Também será muito útil ter experiência em interagir com APIs e SDKs da AWS e solucionar quaisquer erros encontrados ao usá-los.

Cenários comuns de exames

<!-- image -->

Cenário	Solução

AWS Lambda

Uma aplicação executada em um servidor local é convertida em uma função Lambda. Quando a função foi testada, um erro Não foi possível importar o módulo foi exibido.

Instale os módulos ausentes na pasta do seu aplicativo e empacote- os em um arquivo ZIP antes de fazer upload para o AWS Lambda.

Um desenvolvedor está escrevendo uma função Lambda que será usada para enviar uma solicitação a uma API em

diferentes ambientes (Prod, Dev, Test). A função precisa invocar automaticamente a chamada de API correta com base no ambiente.

Use variáveis de ambiente

Uma função Lambda precisa de armazenamento temporário para armazenar arquivos durante a execução.

Armazene os arquivos no diretório /tmp

A função Lambda está gravando dados em um banco de dados RDS. A função precisa reutilizar a conexão com o banco de dados para

reduzir o tempo de execução.

Um desenvolvedor precisa aumentar a CPU disponível para uma função Lambda para processar dados com mais eficiência.

Use o contexto de execução colocando a lógica de conexão do banco de dados fora do manipulador de eventos. E mais adiante RDS Proxy ...(RFS REVIEW)

Aumente a memória alocada da função.

Gateway de API da Amazon

	16





<!-- image -->

Habilite o CORS no console do API Gateway.

Um site integrado ao API Gateway exige que as solicitações do usuário cheguem ao servidor backend sem intervenção do API Gateway. Qual tipo de integração deve ser usado?

PROXY HTTP

Um aplicativo sem servidor é composto por AWS Lambda, DynamoDB e API Gateway. Os usuários estão reclamando de erros HTTP 504.

As solicitações de API estão atingindo o tempo limite máximo de integração do API Gateway (29 segundos).

Como invalidar o cache do API Gateway?

- Envie uma solicitação com um cabeçalho Cache-Control: max-age.

- Habilite a opção Exigir autorização nas configurações de cache da API.

Um desenvolvedor precisa implantar diferentes versões de API em Gateway de API

Use variáveis de estágio

Amazon DynamoDB

Um desenvolvedor precisa de uma solução econômica para excluir dados de sessão em uma tabela do DynamoDB.

Expire os dados da sessão com DynamoDB TTL

Novas alterações em uma tabela do DynamoDB devem ser registradas em outra tabela do DynamoDB.

Reduza o tempo de resposta do banco de dados DynamoDB.

Usar fluxos do DynamoDB

Use o acelerador DynamoDB (DAX)

Escolhendo a melhor chave de partição para a tabela DynamDB.                       Use a chave de partição com a cardinalidade mais alta (por exemplo,	 carteira de estudante, carteira de funcionário)

Um aplicativo usa um banco de dados DynamoDB com Índice Secundário Global. As solicitações do DynamoDB estão retornando um erro ProvisionedThroughputExceededException . Por que isso está acontecendo?

A capacidade de gravação do GSI é menor que a da tabela base.

CloudFormation e AWS SAM

Qual seção deve ser adicionada a um modelo CloudFormation para incluir recursos definidos pelo AWS SAM?

Transformar

	17





<!-- image -->

Um desenvolvedor precisa de uma estrutura confiável para construir aplicativos sem servidor na AWS

AWSSAM

Um processo de criação de pilha do CloudFormation falhou inesperadamente.

O CloudFormation será revertido excluindo recursos que já criou.

Um modelo CloudFormation será usado em várias contas AWS

Use StackSets do CloudFormation

Implantação e segurança

É necessário que o tráfego de entrada seja deslocado em dois incrementos. 10% do tráfego deve ser deslocado no primeiro incremento e

os 90% restantes devem ser implantados após alguns minutos.

Canário

Você precisa autenticar os usuários de um site usando perfis de identidade de mídia social.

Uma empresa possui duas contas. Os desenvolvedores da Conta A precisam acessar os recursos da Conta B.

Grupos de identidades do Amazon Cognito

Usar função de acesso entre contas

Vários desenvolvedores precisam fazer atualizações incrementais de código em um único projeto e depois implantar as novas alterações.

Use o AWS CodeCommit como repositório de código e implante diretamente o novo pacote usando o AWS CodeDeploy.

Uma equipe de desenvolvimento está usando o CodePipeline para automatizar o processo de implantação. As alterações no código

Adicione um estágio de ação de aprovação manual

devem ser revisadas por uma pessoa antes de serem liberadas

para produção

Comandos API/CLI relevantes

Um desenvolvedor precisa decodificar uma mensagem codificada de falha de autorização.

Use o comando aws

sts decode-authorization-message.

Como um desenvolvedor pode verificar a permissão para chamar um comando CLI sem realmente fazer uma solicitação?

Use o parâmetro --dry-run junto com o comando CLI.

Um desenvolvedor precisa implantar um modelo CloudFormation de um computador local.

Use o pacote aws cloudformation e o comando aws cloudformation deploy

Um desenvolvedor deve garantir que nenhum aplicativo possa buscar uma mensagem de uma fila SQS que esteja sendo processada ou que já tenha sido processada.

Aumente o valor VisibilityTimeout usando a API ChangeMessageVisibility e exclua a mensagem usando a API DeleteMessage.

	18





<!-- image -->

de API o desenvolvedor deve usar para permitir que o aplicativo faça solicitações de upload?



Use a API AssumeRole

19

<!-- image -->





Aprofundamentos da AWS: PARTE TEÓRICA

AWS Identity Access Manager (IAM)

IAM é a principal ferramenta para controlar e gerenciar o acesso a uma conta AWS. Ele está no centro da segurança da AWS;

tudo o que você faz com a AWS, seja criar uma função Lambda, fazer upload de um arquivo para um bucket S3 ou algo mundano como visualizar instâncias EC2 no console, é governado pelo IAM. Ele permite que você especifique quem, quais recursos da AWS, bem como quais ações eles podem ou não realizar. Eles também são conhecidos como autenticação e autorização.

Identidades IAM

As identidades IAM tratam do aspecto de autenticação da sua conta AWS. Pertence a qualquer usuário, aplicativo ou grupo que pertença à sua organização.

Uma identidade do IAM pode ser um usuário do IAM, uma função do IAM ou um grupo do IAM.

	20

<!-- image -->



Um usuário IAM representa o usuário ou aplicativo que interage com os serviços da AWS. Observe que um usuário IAM é diferente do usuário root. Embora permissões completas de administrador possam ser concedidas a um usuário do IAM, há certas ações que somente um usuário root pode realizar, como excluir uma conta da AWS. Os usuários do IAM recebem credenciais de longo prazo

para acessar os serviços da AWS. Essas credenciais podem ser na forma de nome de usuário e senha (para acesso ao console) ou chave de acesso e chave secreta (para acesso programático). O primeiro é usado principalmente ao fazer login no Console AWS, enquanto

o último é usado ao interagir com os serviços AWS por meio de comandos CLI/API.

Uma função do IAM não se destina a ser associada a um usuário único; em vez disso, deve ser assumida por determinados serviços da AWS ou por um grupo de usuários externos com funções comerciais comuns. Ao contrário dos usuários do IAM, as

funções usam credenciais de segurança com tempo limitado para acessar a AWS. Ao criar uma função, você escolhe uma entidade confiável. A entidade confiável determina quem está autorizado a assumir a função do IAM.

Uma função do IAM pode ser assumida pelos serviços da AWS para executar ações em seu nome, um usuário do IAM em sua

conta ou de uma conta externa e usuários federados por provedores de identidade nos quais a AWS confia. Exemplos desses provedores de identidade são Microsoft Active Directory, Facebook, Google, Amazon ou qualquer IdP compatível com OpenID Connect (OIDC) e SAML 2.0.

O Grupo IAM é simplesmente uma coleção de usuários IAM. As políticas anexadas a um grupo IAM são herdadas pelos usuários do IAM nele. É possível atribuir um usuário IAM a vários grupos, mas os grupos não podem ser aninhados (um grupo dentro de um grupo).

O grupo IAM oferece uma maneira fácil de gerenciar usuários em sua conta. Por exemplo, se você tiver uma equipe de desenvolvedores que precisa de acesso ao AWS Lambda, em vez de anexar a permissão necessária para eles individualmente, você pode reunir os desenvolvedores em um grupo IAM chamado 'Desenvolvedores' e associar o

	21

Tutoriais Guia de estudo do

Permissões do Lambda para esse grupo. Se um novo membro ingressar na equipe, basta adicioná-lo ao grupo IAM 'Desenvolvedores'.

Política IAM

Uma identidade do IAM não pode executar ações da AWS sem uma política do IAM anexada a ela, a menos que o recurso que está sendo acessado permita que a identidade do IAM faça isso. Uma política do IAM é o que autoriza um usuário ou função do IAM a controlar e acessar seus recursos da AWS. Existem três tipos de políticas IAM para escolher:

- Políticas gerenciadas pela AWS: são políticas integradas que foram criadas para estar em conformidade com casos de uso e funções de trabalho comuns. Por exemplo, digamos que você esteja trabalhando como administrador de sistema e precise conceder ao novo administrador de banco de dados as permissões necessárias para realizar seu trabalho. Em vez de descobrir as

permissões corretas, você pode simplesmente usar a política gerenciada DatabaseAdministrator, que concede acesso completo aos serviços da AWS necessários para instalar e configurar os serviços de banco de dados da AWS. As políticas gerenciadas pela AWS não podem ser excluídas ou modificadas.

- Política gerenciada pelo cliente - refere-se às políticas que você cria manualmente em sua conta.

- Política Inline - uma política incorporada em uma identidade do IAM. Diferentemente das políticas gerenciadas pela AWS e Políticas gerenciadas pelo cliente, uma política em linha não possui seu próprio ARN; portanto, não pode ser referenciado por outras identidades do IAM. O escopo é de um usuário ou função específica do IAM.

Referências:

https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_users.html https:// docs.aws.amazon.com/IAM/latest/UserGuide/access\_policies.html https://docs.aws. amazon.com/ IAM/latest/UserGuide/id\_groups.html

Estrutura da política IAM

Uma política IAM é expressa como um documento JSON. É composto por dois componentes: informações sobre toda a política e uma ou mais declarações. As informações de toda a política são um elemento opcional colocado na parte superior do documento. Geralmente é apenas um elemento Version pertencente à versão da linguagem da política da AWS que está sendo usada. Esse elemento geralmente tem um valor estático de 17/10/2012, referindo-se à data de lançamento da linguagem atual de acesso à política da AWS.

O bloco Statement é onde você adiciona as permissões necessárias para acessar vários serviços da AWS. Uma política pode ter instruções únicas ou múltiplas, onde cada instrução é colocada entre colchetes.

A seguir está um exemplo de uma política IAM.

	22

<!-- image -->



{

"Versão": "17/10/2012", "Declaração": [{

"Sid": "AllowFullEC2AccessFromMyNetwork", "Effect": "Allow", "Action":

["ec2:DescribeInstance*"], "Resource": "*", "Condition":

{"IpAddress": {"aws: FonteIp": "180.0.111.0/24"}}

}]

}

Uma declaração individual possui os seguintes elementos:

- ID do extrato (Sid) - este é apenas um rótulo que você atribui a um extrato. É útil para identificar rapidamente para que serve uma declaração, em vez de revisar o que está na Ação, no Efeito ou no Recurso. Este elemento é opcional; no entanto, pode ser útil ao modificar ou depurar políticas com múltiplas instruções.

- Efeito - determina explicitamente se a política permite ou nega acesso a um determinado recurso. Ele aceita apenas Permitir ou Negar.

- Ação - este elemento contém a lista de ações que a política permite ou nega. Você pode usar o curinga (*) para conceder acesso a todas ou a um subconjunto de operações da AWS. No exemplo acima, ec2:DescribeInstance*

refere-se a todas as ações que começam com a string “DescribeInstance”. Portanto, isso pode estar se referindo a DescribeInstanceAttribute, DescribeInstances, DescribeInstancesStatus e

breve.

- Recurso - a lista de recursos da AWS aos quais o elemento Action é aplicado. A política de exemplo acima usa apenas um curinga (*) para corresponder a todos os caracteres. Isto implica que a Ação é aplicável a todos os recursos. Você pode ser mais restritivo aos recursos com os quais deseja trabalhar, especificando seus nomes de recursos da Amazon (ARN).

- Condição - um elemento opcional que você pode usar para aplicar lógica à sua política quando ela estiver em vigor. Para

Por exemplo, o exemplo de política acima permite apenas solicitações originadas da rede 180.0.111.0/24.

Algumas condições das quais você deve estar ciente são:

- StringEquals - Correspondência exata de strings e distinção entre maiúsculas e minúsculas • StringNotEquals - Correspondência negada
- StringLike - Correspondência exata, mas ignorando maiúsculas e minúsculas • StringNotLike - Correspondência negada

	23

<!-- image -->

 Associate por

e o

- Bool - Permite construir elementos Condition que restringem o acesso com base em valores verdadeiros ou falsos.
- IpAddress – endereço IP ou intervalo especificado correspondente.
- NotIpAddress - Todos os endereços IP, exceto o endereço IP ou intervalo especificado • ArnEquals, ArnLike •

ArnNotEquals, ArnNotLike • Use um

operador de condição Nulo para verificar se uma chave de condição está presente no momento da autorização. • Você pode adicionar IfExists ao final de qualquer nome de operador de condição (exceto Null

condição) — por exemplo, StringLikeIfExists.

Referências:

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html https:// aws.amazon.com/blogs/security/back-to-school-understanding-the -iam-política-gramática/

Política baseada em identidade versus política baseada em recursos

Existem seis tipos de política IAM: políticas baseadas em identidade, políticas baseadas em recursos, limites de permissões IAM, políticas de controle de serviço, políticas de sessão e listas de controle de acesso (ACLs). Para efeitos do exame, focaremos apenas nas políticas baseadas em identidade e em recursos. A diferença entre eles é bem simples. As políticas baseadas em identidade são políticas que você anexa a uma identidade do IAM, como usuário do IAM ou função do IAM. Por outro lado, as políticas baseadas em recursos são anexadas aos recursos da AWS, como um bucket S3 (política de bucket), chave KMS

(política de chave) ou uma função Lambda. Observe que nem todos os recursos da AWS oferecem suporte a políticas baseadas em recurso

	24

<!-- image -->



Uma política baseada em identidade define os recursos e ações aos quais um usuário ou função do IAM tem acesso. Como a política está anexada ao usuário ou à função do IAM, o elemento Principal não precisa ser especificado explicitamente. Em outras palavras, o usuário ou função do IAM ao qual a política está anexada é implicitamente considerado o principal.

Uma política baseada em recursos, por outro lado, deve incluir os elementos Principal e Recurso. O elemento Principal especifica quais identidades do IAM têm permissão para acessar o recurso, enquanto o elemento Resource especifica em quais recursos os usuários têm permissão para executar ações. Por exemplo, uma política de bucket é um tipo de política baseada em recursos anexada a um bucket do Amazon S3. A política especifica as ações permitidas no bucket e os usuários ou funções do IAM que têm permissão para executar essas ações.

	25

<!-- image -->



A política de bucket do S3 a seguir é um exemplo de como o elemento Resource é usado para conceder permissões em nível de recurso. Você pode ver que o bucket tdojo S3 contém duas pastas, john-folder e dave-folder, às quais os usuários do IAM John e Dave têm acesso de leitura, respectivamente.

{

"Versão": "17/10/2012", "Declaração" : [ {

"Efeito": "Permitir",

"Principal": {"AWS": "arn:aws:iam::123456789000:user/john"}, "Ação": ["s3:GetObject","s3:GetObjectVersion"],

"Recurso": ["arn:aws:s3:::tdojo/john-folder"] }, {

"Efeito": "Permitir",

"Principal": {"AWS": "arn:aws:iam::123456789000:user/dave"}, "Ação": ["s3:GetObject","s3:GetObjectVersion"],

"Recurso": ["arn:aws:s3:::tdojo/dave-folder"] }]}

Um aspecto importante do IAM que você precisa entender é como as diferentes políticas são avaliadas. Antes de determinar se sua solicitação é permitida ou não, a AWS avalia primeiro todas as declarações DENY explícitas em todas as

políticas envolvidas. Se o solicitante for especificado em uma instrução DENY em qualquer uma das políticas, o IAM negará a solicitação. Em segundo lugar, entre as políticas baseadas em recursos e as políticas baseadas em identidade, as políticas baseadas em recursos são avaliadas primeiro. Por exemplo, um usuário do IAM com uma política do IAM vazia ainda poderá acessar um bucket do S3, desde que sua política de bucket permita que o usuário do IAM execute ações no bucket.

Aqui está uma versão simplificada do fluxograma da AWS sobre avaliação de políticas. Somente políticas baseadas em recursos e em IAM são incluídas para simplificar.

	26

<!-- image -->



Referências:

https://docs.aws.amazon.com/IAM/latest/UserGuide/access\_policies\_identity-vs-resource.html https:// docs.aws.amazon.com/IAM/latest/UserGuide/reference\_policies\_evaluation-logic.html

Acesso entre contas

A lógica de avaliação de política discutida na seção anterior é para acesso intraconta, que envolve usuários e recursos da AWS interagindo entre si na mesma conta. A avaliação das políticas é bastante diferente quando se trata de acesso entre contas.

O acesso entre contas refere-se ao acesso entre duas ou mais contas separadas da AWS. Pode ser uma instância EC2 em uma conta da AWS acessando um bucket S3 em uma conta diferente da AWS ou um usuário em uma conta assumindo uma função em outra conta para acessar recursos nessa conta.

	27

<!-- image -->



Entre contas para usuários do IAM

Imagine um usuário IAM chamado 'Tucker' na conta A que precisa baixar documentos da pasta private/documents de um bucket S3 na conta B.

Para conceder esta permissão, as seguintes ações devem ser configuradas:

- Na conta B, o proprietário do bucket S3 cria uma política de bucket S3 que especifica que Tucker tem permissão para baixar os documentos. A política deve ser anexada ao bucket privado do S3 na conta B.

Exemplo de política de bucket S3 na conta B:

{

"Versão": "17/10/2012", "Declaração": [ {

"Efeito": "Permitir",

"Principal": { "AWS": "arn:aws:iam::<ID da conta A>:user/Tucker" }, "Ação": "s3:GetObject",

"Recurso": "arn:aws:s3:::private/documents/*"

}

]

}

- Na conta A, Tucker deve ter uma política IAM que conceda permissões para acessar o bucket S3 na conta B. A política permite que Tucker acesse o bucket S3 sem assumir uma função IAM.

Exemplo de política IAM para Tucker na conta A:

{

"Versão": "17/10/2012", "Declaração": [ {

"Sid": "BaixarDocumentos", "Efeito": "Permitir",

"Ação": [ "s3:GetOb

	28

<!-- image -->



"Recurso": "arn:aws:s3:::private/documents/*"

}

]

}

Depois de configurar as permissões necessárias em ambas as contas, Tucker agora pode usar AWS SDK ou CLI para acessar o bucket S3 na conta B e baixar os documentos.

Como o acesso é avaliado?

Se Tucker fizer uma solicitação ao bucket na conta B, a AWS realizará duas avaliações para determinar se a solicitação é permitida ou negada, uma na conta confiável (AccountB) e outra na conta confiável (AccountA). Na conta A,

a AWS verifica a política baseada em identidade de Tucker e quaisquer políticas que possam limitar as ações que ele está solicitando. Na AccountB, a AWS avalia a política do bucket e quaisquer políticas que possam limitar a ação solicitada. A solicitação só será permitida se ambas as avaliações resultarem em uma decisão “Permitir”. Se alguma avaliação de política retornar uma decisão "Negar", a solicitação de acesso será negada.

Entre contas para funções do IAM

Alternativamente, um administrador na Conta B pode criar uma função IAM para Tucker assumir. Este método fornece uma solução mais escalonável e flexível, pois o administrador pode facilmente modificar ou revogar o acesso ao bucket S3 conforme necessário. Por exemplo, se houver outros usuários do IAM na conta A que precisem de acesso semelhante ao bucket, o administrador poderá simplesmente conceder permissão para que eles assumam a função do IAM em vez de modificar a política de bucket do S3 para cada usuário. Essa abordagem reduz a sobrecarga administrativa na concessão de acesso ao bucket.

Aqui estão as etapas para conceder a qualquer usuário do IAM na conta A que assuma uma função do IAM na conta B.

- Na conta B, o administrador do IAM cria uma função do IAM com uma política que concede acesso ao S3 balde.

Exemplo de política de bucket S3 na conta B:

{

"Versão": "17/10/2012", "Declaração": [ {

"Sid": "BaixarDocumentos", "Efeito": "Permitir",

"Ação": [

	29

<!-- image -->



"s3:GetObject

"Recurso": "arn:aws:s3:::private/documents/*"

}

]

}

- O administrador do IAM também deve anexar uma política de confiança à função do IAM, especificando quais contas e entidades da AWS têm permissão para assumir a função. Neste caso, a política de confiança deve incluir a Conta A como uma conta confiável.

Exemplo de política de confiança na Conta B (observe que “root” se refere a qualquer Principal na Conta A, excluindo o usuário root):

{

"Versão": "17/10/2012", "Declaração": [ {

"Efeito": "Permitir", "Diretor": {

"AWS": "arn:aws:iam::AccountA:root"

},

"Ação": "sts:AssumeRole"

}

]

}

- A política para um usuário do IAM na conta A deve permitir a ação sts:AssumeRole no ARN do IAM

função na conta B.

Exemplo de política do IAM para um usuário do IAM na conta A:

{

"Versão": "17/10/2012", "Declaração": [ {

"Efeito":   "Permitir", "Ação": "sts:AssumeRole",

	30

<!-- image -->



"Recurso": "arn:aws:iam::<ID da conta B>:role/RoleName"

}

]

}

Como o acesso é avaliado?

Depois que a política de confiança é avaliada na conta B, a AWS verifica se o usuário do IAM (na conta A) que assume a função do IAM está autorizado a fazê-lo. Depois que o usuário do IAM assume a função, a AWS verifica se a função do IAM tem permissões suficientes para acessar o recurso solicitado no bucket. Depois disso, a política do bucket S3 será avaliada e o acesso será concedido somente se todas as avaliações da política resultarem em uma decisão de "Permitir".

Referências:

https://docs.aws.amazon.com/IAM/latest/UserGuide/reference\_policies\_evaluation-logic-cross-account.html https:// aws.amazon.com/blogs/security/how-to-use-trust-policies -com-iam-roles/

IAM:Permissão PassRole

A ação iam:PassRole concede a um usuário permissão para anexar funções do IAM a um recurso da AWS. Esta é uma permissão simples, mas poderosa, que merece o devido escrutínio ao construir políticas IAM. Você pode, por exemplo, usar a permissão PassRole para proibir determinados usuários do IAM de transmitir funções que tenham permissões maiores do que as que o usuário pode ter. Deixe-me pintar um cenário para você explicar isso.

Digamos que sua empresa tenha uma função Lambda que processe dados armazenados no Amazon S3. Uma função de execução com acesso total ao S3 está anexada à função Lambda. A função Lambda é executada de acordo com uma programação e somente os administradores estão autorizados a fazer alterações de código nela. Mesmo que você não tenha acesso à função do Lambda, você poderá ignorar as permissões concedidas a você se a política a seguir estiver anexada ao seu usuário do IAM.

{

"Versão": "17/10/2012", "Declaração": [{

"Efeito": "Permitir",

"Ação": "iam:PassRole",

"Recurso": "*"

}] }

A política do IAM anterior permite que você transmita quaisquer funções do IAM que existam na conta da AWS da sua empresa.

Isso cria uma falha de segurança que pode ser explorada para aumentar seu acesso. Dado que você tem permissões suficientes para

	31

<!-- image -->



Para criar funções Lambda, tudo o que você precisa fazer é iniciar uma nova função Lambda e anexar a função de execução que tenha acesso total ao S3. Fazendo isso, mesmo que seu usuário IAM não tenha permissões S3, você ainda poderá acessar o Amazon S3 usando a função Lambda.

	32

<!-- image -->





Para melhor segurança, seja mais granular no que diz respeito ao fornecimento de acesso. Por exemplo, liste as funções específicas do IAM que um usuário pode transmitir em vez de apenas usar um curinga, como mostrado abaixo:

{

"Versão": "17/10/2012", "Declaração": [ {

"Efeito": "Permitir", "Ação": "iam:PassRole", "Recurso":

[ "arn:aws:iam::123456789123:role/td-cloudwatch-agent-role", "arn:aws:iam::123456789123:role/td-s3-role"

]

}

]

}

Referências:

https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_use\_passrole.html https:// docs.aws.amazon.com/IAM/latest/UserGuide/reference\_policies\_examples\_iam-passrole-service.html

	33





AWS STS

O AWS Security Token Service (AWS STS) é um serviço web global que permite gerar acesso temporário para usuários do IAM ou usuários federados para obter acesso aos seus recursos da AWS. Essas credenciais temporárias são baseadas em sessão, o

que significa que são apenas para uso de curto prazo; uma vez expirados, eles não poderão mais ser usados para acessar seus recursos da AWS.

AWS STS não pode ser acessado no console AWS; só é acessível através da API. Todas as solicitações STS vão para um único endpoint em https:// sts.amazonaws.com/, e os logs são então registrados no AWS CloudTrail.

Operações da API STS

AssumirPapel

A operação da API AssumeRole permite que um usuário do IAM assuma uma função do IAM pertencente à sua conta ou a

uma externa (acesso entre contas). Assim que a solicitação for bem-sucedida, a AWS gera e retorna credenciais temporárias que consistem em um ID de chave de acesso, uma chave de acesso secreta e um token de segurança. Essas credenciais podem então ser usadas pelo usuário do IAM para fazer solicitações aos serviços da AWS.

AssumeRoleWithWebIdentity

A operação da API AssumeRoleWithWebIdentity retorna credenciais de segurança temporárias para usuários federados que são autenticados por meio de um provedor de identidade público (por exemplo, Amazon Cognito, Login com Amazon, Facebook, Google ou qualquer provedor de identidade compatível com OpenID Connect). As credenciais temporárias podem então ser usadas pelo seu aplicativo para estabelecer uma sessão com a AWS. Assim como a API AssumeRole, as entidades confiáveis que assumirão

a função devem ser especificadas. Desta vez, em vez de usuários IAM, será um provedor de identidade.

AssumeRoleWithWebIdentity não requer credenciais de identidades do IAM, o que o torna adequado para aplicativos móveis

que exigem acesso à AWS. O AssumeRoleWithWebIdentity é uma das APIs que o Amazon Cognito usa internamente para facilitar a troca de tokens e credenciais em seu nome. Como o Amazon Cognito abstrai os problemas associados à autenticação do usuário, é recomendável usar o Amazon Cognito ao fornecer acesso da AWS aos usuários do aplicativo. No entanto, você pode usar AssumeRoleWithWebIdentity apenas como uma operação autônoma.

AssumirRoleWithSAML

A operação da API AssumeRoleWithSAML retorna um conjunto de credenciais de segurança temporárias para usuários federados que são autenticados por provedores de identidade corporativos compatíveis com SAML 2.0. Os usuários também devem usar

	34

 Associate



SAML 2.0 (Security Assertion Markup Language) para passar informações de autenticação e autorização para a AWS.

Esta operação de API é útil para organizações que integraram seus sistemas de identidade (como Windows Active Directory ou OpenLDAP) com software que pode produzir asserções SAML.

GetFederationToken

A operação da API GetFederationToken retorna um conjunto de credenciais de segurança temporárias que consiste em um token de segurança, chave de acesso, chave secreta e expiração para um usuário federado. Essa API geralmente é usada para federar o acesso a usuários autenticados por um agente de identidade personalizado e só pode ser chamada usando as credenciais programáticas de um usuário do IAM (as funções do IAM não são suportadas). Embora seja possível usar as

credenciais de segurança de um usuário root para chamar GetFederationToken, isso não é recomendado por motivos de segurança.

Em vez disso, a AWS recomenda a criação de um usuário IAM especificamente para um aplicativo proxy que realiza o processo de autenticação.

O período de expiração padrão para esta API é significativamente maior que AssumeRole (12 horas em vez de uma hora). Como

você não precisa obter novas credenciais com tanta frequência, o período de expiração mais longo pode ajudar a reduzir o número de chamadas para a AWS.

Você pode usar as credenciais temporárias criadas por GetFederationToken em qualquer serviço da AWS, exceto o seguinte:

- Você não pode chamar nenhuma operação do IAM usando a AWS CLI ou a API da AWS.
- Você não pode chamar nenhuma operação STS, exceto GetCallerIdentity.

DecodeAuthorizationMessage

DecodeAuthorizationMessage decodifica informações adicionais sobre o status de autorização de uma solicitação de uma mensagem codificada retornada em resposta a uma solicitação da AWS.

Por exemplo, um usuário pode chamar uma API à qual não tem acesso; a solicitação resulta em uma resposta Client.UnauthorizedOperation. Algumas operações da AWS também retornam uma mensagem codificada que pode fornecer detalhes sobre essa falha de autorização. A mensagem é codificada para que os detalhes de privilégio sobre a autorização fiquem ocultos

do usuário que solicitou a operação. Para decodificar uma mensagem de status de autorização, é necessário receber permissão por meio de uma política do IAM para solicitar a ação DecodeAuthorizationMessage.

Referências:

https://docs.aws.amazon.com/STS/latest/APIReference/API\_Operations.html

https:// docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_temp\_request.html

	35





AWS Lambda

O AWS Lambda permite executar códigos sem gerenciar servidores. Você não precisa se preocupar com tarefas como dimensionamento, aplicação de patches e outras operações de gerenciamento que normalmente são realizadas em instâncias do EC2 ou em servidores locais. Você pode alocar o máximo de memória disponível para uma função do Lambda, bem como a duração

da execução da função, antes do tempo limite. A memória, que é dimensionada proporcionalmente à potência da CPU, pode variar de 128 MB a 10.240 MB em incrementos de 1 MB. O tempo limite padrão é de três segundos, com valor máximo de 900 segundos (15 minutos).

Uma função Lambda pode ser invocada de diferentes maneiras. Você pode invocar uma função diretamente no console do AWS Lambda, por meio do comando Invoke API/CLI ou por meio de um URL de função. Você também pode configurar determinados serviços da AWS para invocar uma função Lambda. Por exemplo, você pode criar uma função do Lambda que responda a eventos do Amazon S3 (por exemplo, processar arquivos à medida que são carregados em um bucket do S3) ou configurar uma regra do Amazon EventBridge que acione uma função do Lambda toda semana para executar o processamento em lote. As funções Lambda também são

comumente usadas como back-end para APIs que não exigem carga constante, como manipulação de solicitações de login ou processamento de imagens em tempo real.

	36





Invocações síncronas vs. assíncronas

Existem dois tipos de invocação no AWS Lambda.

O primeiro tipo é chamado de invocação síncrona, que é o padrão. A invocação síncrona é bastante direta. Quando uma função é invocada de forma síncrona, o AWS Lambda espera até que o processamento da função seja concluído e então retorna o resultado.

Vamos ver como isso funciona através do seguinte exemplo:

A imagem acima ilustra uma API baseada em função Lambda gerenciada pelo API Gateway. Quando o API Gateway

recebe uma solicitação GET do recurso /getOrder, ele invoca a função getOrder. A função recebe um evento contendo a carga útil, processa-a e retorna o resultado.

Considerações ao usar a invocação síncrona:

- Se você planeja integrar o AWS Lambda ao API Gateway, observe que o tempo limite de integração do API Gateway é de 29 segundos. Se uma função demorar mais para ser concluída, a conexão atingirá o tempo limite e a solicitação falhará. Portanto, use invocações síncronas para aplicativos que não demorem muito para serem concluídos (por exemplo, autorização de solicitações e interação com bancos de dados). • As

funções invocadas de forma síncrona podem aceitar uma carga útil de até 6 MB. •

Talvez seja necessário implementar uma lógica de nova tentativa no seu código para lidar com erros intermitentes.

	37

<!-- image -->



o

Para chamar uma função Lambda de forma síncrona via API/CLI, defina RequestResponse como o valor do parâmetro invocation-type ao chamar o comando Invoke, conforme mostrado abaixo:

aws lambda invocar \ --

nome da função testFunction \

--invocation-type RequestResponse \

--cli-formato binário raw-in-base64-out \

--payload '{ "input": "input\_value" }' resposta.json

Como alternativa, você pode simplesmente omitir o parâmetro invocation-type, pois o AWS Lambda invoca funções de forma síncrona por padrão.

Serviços que invocam funções Lambda de forma síncrona: (serviços irrelevantes para o exame são excluídos):

- Amazon API Gateway • Balanceador de carga de aplicações
- Amazon Cognito •

Amazon Kinesis Data Firehose

- Amazon CloudFront (Lambda@Edge)

Uma invocação assíncrona normalmente é usada quando um cliente não precisa esperar por resultados imediatos de uma função.

Alguns exemplos disso são processos de longa latência executados em segundo plano, como operações em lote, codificação de vídeo e processamento de pedidos.

Quando uma função é invocada de forma assíncrona, o AWS Lambda armazena o evento em uma fila interna gerenciada por ele. Vamos entender a invocação assíncrona através do exemplo abaixo:

	38

<!-- image -->





Uma solicitação PUT é feita ao recurso /putOrder. Assim como no exemplo anterior, a solicitação passa pelo API Gateway, que produz um evento. Desta vez, em vez de o API Gateway invocar diretamente a função, o AWS Lambda coloca o evento na fila. Se o evento for enfileirado com êxito, o AWS Lambda retornará uma carga vazia com código de status HTTP 202. O código de status 202 é apenas uma confirmação de que o evento está na fila; não é indicativo de uma invocação bem-sucedida. O cliente não será obrigado a aguardar a conclusão da função Lambda. Portanto, para

melhorar a experiência do usuário, você pode criar um trabalhador que rastreie a conclusão do pedido e envie notificações assim que o pedido for processado com sucesso.

Para chamar uma função Lambda de forma assíncrona por meio do comando Invoke, basta definir Event como o valor do parâmetro invocation-type, conforme mostrado abaixo:

aws lambda invocar \ --

function-name testFunction \ --invocation- type Event \

--cli-formato binário raw-in-base64-out \

--payload '{ "input": "input\_value" }' resposta.json

Considerações ao usar invocação assíncrona:

- As funções invocadas de forma assíncrona só podem aceitar uma carga útil de até 256 KB.

	39

<!-- image -->

 Associate por

e o

- O serviço Lambda implementa uma lógica de nova tentativa para funções invocadas de forma assíncrona.
- Bom para aplicativos executados em segundo plano.

Serviços que invocam funções Lambda de forma assíncrona: (serviços irrelevantes para o exame são excluídos):

- Amazon API Gateway (especificando Event no cabeçalho de solicitação X-Amz-Invocation-Type de uma API de integração não proxy ) • Amazon S3

- Amazon CloudWatch Logs •

Amazon EventBridge • AWS CodeCommit

- AWS CloudFormation

•AWSConfig

Tratamento de invocações assíncronas com falha

O AWS Lambda possui um mecanismo de repetição integrado para invocações assíncronas. Se a função retornar um erro, o Lambda tentará repetir a solicitação mais duas vezes, com um intervalo de espera maior entre cada tentativa.

A solicitação é descartada depois que o AWS Lambda esgota todas as tentativas restantes. Para evitar a perda de eventos, você pode redirecionar as tentativas de solicitação com falha para uma fila de mensagens mortas do SQS para que você possa depurar o erro posteriormente e fazer

com que outra função tente novamente.

Referências:

https://docs.aws.amazon.com/lambda/latest/dg/lambda-invocation.html

	40

<!-- image -->





https://aws.amazon.com/blogs/architecture/understanding-the- Different-ways-to-invoke-lambda-functions/

Mapeamentos de origem de eventos

Recursos baseados em fluxo ou fila, como fluxos do DynamoDB, filas SQS e fluxos do Kinesis Data Streams, não invocam funções do Lambda diretamente. Normalmente, lemos os registros desses recursos usando pollers. Um poller é um aplicativo que verifica periodicamente uma fila, extrai registros dela (às vezes em lotes) e os envia para um serviço downstream que os processará.

Um mapeamento de origem de eventos é uma espécie de agente de pesquisa gerenciado pelo Lambda. Os mapeamentos de fontes de eventos eliminam a sobrecarga de escrever pollers do zero para recuperar mensagens de filas/streams. Isso permite que você se concentre na construção da lógica de domínio do seu aplicativo.

O mapeamento da origem do evento invoca uma função de forma síncrona se uma das seguintes condições for atendida:

- O tamanho do lote foi atingido – O tamanho mínimo do lote pode ser definido como 1, mas os tamanhos padrão e máximo do lote variam de acordo com o serviço da AWS que invoca sua função.
- A janela máxima de lote é atingida - A janela de lote é a quantidade de tempo que o Lambda espera para coletar e agrupar

registros. A janela de lote padrão para Amazon Kinesis, Amazon DynamoDB e

	41

<!-- image -->





Amazon SQS é 0. Isso significa que uma função Lambda receberá lotes o mais rápido possível. Você pode ajustar o valor da janela do lote com base na natureza do seu aplicativo.

- A carga útil total é de 6 MB - Como os mapeamentos de origem de eventos invocam funções de forma síncrona, a carga útil total (dados de eventos) que uma função pode receber também é limitada a 6 MB (o limite para invocações síncronas). Isso significa que se o tamanho máximo do registro em uma fila for 100 KB, o tamanho máximo do lote que você pode definir será 60.

Filtragem de eventos

Uma função Lambda é cobrada com base no tempo de execução. A frequência com que as funções são invocadas também desempenha um fator importante. É por isso que o Lambda é ótimo para trabalhos agendados, tarefas de curta duração e processos baseados em eventos. Mas isso significa que você não deve usá-los para aplicações de alto volume de tráfego? Não há uma resposta definitiva, pois sempre será caso a caso. Geralmente depende de fatores como os requisitos da sua

aplicação e a compensação de custos que você está disposto a fazer. Independentemente disso, se você quiser usar o Lambda em um aplicativo de alta atividade, como processamento de fluxo, é bom saber que existem métodos disponíveis para compensar o custo da execução de funções.

O lote é uma técnica de otimização de custos para funções Lambda. Ao aumentar o valor do tamanho do lote, você pode reduzir a frequência com que sua função é executada. Além disso, você também pode filtrar eventos que são necessários apenas para sua função, reduzindo ainda mais o custo.

Considere o seguinte cenário:

Você está encarregado de desenvolver uma função que reaja a quedas de tensão ou mudanças de temperatura que possam indicar componentes defeituosos em um local. Vários sensores enviam leituras para um stream do Kinesis Data Stream, que deve ser consumido e processado por uma função Lambda.

Seu primeiro instinto pode ser implementar a lógica de filtragem na função Lambda, conforme mostrado abaixo:

def lambda\_handler(evento, contexto):

temperatura = evento["temperatura"] tensão = evento["tensão"] se temperatura >

100 ou tensão < 5: #faça alguma coisa

outro:

#fazer nada

	42

<!-- image -->





O código pode ser válido, mas é considerado ineficiente devido ao custo, pois a função Lambda será invocada

desnecessariamente a cada transmissão de dados do sensor, mesmo que não exija processamento. Suponha que os dados do sensor sejam enviados a cada segundo, resultando em 60 invocações por minuto em um tamanho de lote 1 e uma janela de lote 0. Isso pode levar a uma perda de tempo e recursos se nenhuma das leituras contiver os valores de tensão e temperatura desejados.

Para resolver isso, em vez de fazer verificações condicionais para cada evento no nível da função, você deve filtrar os eventos antes que eles sejam transmitidos à sua função. Voltando ao cenário, como você está interessado apenas em valores específicos de tensão e temperatura, você pode especificar um padrão de filtro usando o parâmetro filter-criteria do comando CreateEventSourceMapping.

	43

<!-- image -->



aws lambda create-event-source-mapping \ --function-name process-sensor-readings \ --batch-size 10 \ --starting-position LATEST \ --event-source-arn arn:aws:kinesis:us- east-1:123456789123:stream/sensores \ --critérios

de filtro

'{"Filtros": [{"Padrão": "{\"temperatura\": [{\"numeric\": [\">\", 100]}]}"},{\"tensão\": [{\"numérico\": [\"<\", 5]}]}]}'

Uma única fonte de eventos pode ter até cinco filtros exclusivos. Se um evento corresponder a algum dos filtros, o Lambda o encaminhará para sua função. Caso contrário, o evento é descartado. O exame não espera que você seja um especialista em filtragem de eventos, mas você deve estar familiarizado com isso em alto nível. Você também pode consultar isto para obter a lista completa da sintaxe do filtro.

Referências:

https://docs.aws.amazon.com/lambda/latest/dg/invocation-eventfiltering.html https://aws.amazon.com/ blogs/compute/filtering-event-sources-for-aws-lambda-functions /

Ciclo de vida do ambiente de execução

As funções Lambda passam por três fases quando invocadas. Estes são:

- Fase INIT

- Ocorre quando uma função do Lambda é invocada pela primeira vez após ser implantada ou após um longo período período de inatividade.
- Consiste em duas etapas: criação do ambiente e inicialização do código. • Criação de

ambiente - o AWS Lambda cria uma instância de uma função em um ambiente isolado e seguro dentro de uma micromáquina virtual. Este 'ambiente de execução' é onde o código da função Lambda realmente é executado. Nos

bastidores, o AWS Lambda usa uma tecnologia de virtualização chamada Firecracker para provisionar ambientes. O Firecracker utiliza micromáquinas virtuais leves, permitindo que o AWS Lambda crie ambientes rapidamente, mesmo com um grande volume de solicitações, sem sacrificar a segurança ou o desempenho. A quantidade de CPU e memória alocada para o ambiente de execução é determinada pelas configurações de memória que

você configurou para sua função Lambda. • Inicialização - após configurar o ambiente, o Lambda extrai seu código do Amazon S3

(Os códigos de função Lambda são armazenados com segurança no Amazon S3) e executa o código de inicialização. Código de inicialização é qualquer código escrito fora da função manipuladora. Estas podem ser suas dependências importadas, variáveis globais, objetos, etc.

	44

<!-- image -->



- O tempo que leva para a fase INIT ser concluída adiciona latência ao tempo total de execução da sua função. Esse 'atraso' causado pela inicialização dos ambientes de execução também é conhecido como inicialização a frio. A AWS não cobra

pela inicialização a frio que ocorre durante a fase INIT; entretanto, os tempos de inicialização não devem exceder 10 segundos.

- Fase INVOCAR

- Este é o estágio em que a função de tratamento é executada. Depois que a função do manipulador estiver concluída processamento, o AWS Lambda mantém seu ambiente de execução aquecido (em espera) por um período de tempo. Isso permite que a função aceite solicitações de invocação subsequentes sem precisar criar um novo ambiente de execução. Como resultado, o tempo total de execução da sua função é reduzido porque o Lambda não precisa repetir tudo o que foi feito durante a fase INIT.

	45

<!-- image -->

 Associate por

e o

- Fase de DESLIGAMENTO

- Quando um ambiente de execução deixa de receber solicitações de invocação por algum tempo, o AWS Lambda o encerra. Não há limite de tempo documentado, mas com base na experiência, os ambientes de execução normalmente são mantidos aquecidos por 5 a 15 minutos, embora isso possa variar.

A imagem abaixo ilustra o ciclo de vida de uma função Lambda.

Referência:

https://docs.aws.amazon.com/lambda/latest/dg/runtimes-context.html

	46

<!-- image -->

 Associate por

e o

Reduzindo partidas a frio

Quanto mais bibliotecas/pacotes você incluir, mais longa será a inicialização a frio da sua função. Dito isto, é preciso estar atento e cuidadoso na escolha de quais dependências importar. Existem duas abordagens que você pode adotar para lidar com partidas a

frio. A primeira é carregar apenas o que você precisa. Este método é totalmente gratuito. Você simplesmente precisa ser mais específico e conciso no que diz respeito aos recursos que inclui em sua função. Ao fazer isso, menos dados serão inicializados.

A segunda é usando Simultaneidade Provisionada. Simultaneidade provisionada é um recurso do Lambda que permite alocar ambientes pré-aquecidos para suas funções do Lambda. Isso fornecerá ao seu aplicativo latência constante, permitindo que ele responda a consultas em milissegundos de dois dígitos. Observe que a simultaneidade provisionada é diferente da simultaneidade

reservada. No entanto, o conceito de simultaneidade compartilhada é o mesmo.

O limite de simultaneidade vinculado a uma região é dividido entre simultaneidade compartilhada e simultaneidade provisionada.

Referências:

https://aws.amazon.com/blogs/compute/operating-lambda-performance-optimization-part-1/ https://aws.amazon.com/ blogs/compute/operating-lambda-performance-optimization- parte 2/

Reutilização do Ambiente de Execução

Reutilizar seu ambiente de execução existente envolve reutilizar as configurações, dependências, variáveis globais ou até mesmo conexões de banco de dados que já foram inicializadas durante a fase INIT. Para reutilizar, basta colocar todas as variáveis globais, conexões de banco de dados ou clientes SDK que você possui fora da função de manipulador.

Abaixo está um exemplo de código de função Lambda em que um recurso inicializado não é aproveitado. Você pode ver que o cliente do banco de dados está escrito dentro do manipulador de função.

	4

<!-- image -->





Se for esse o caso, sua função abrirá uma nova conexão com o banco de dados sempre que for invocada, o que é caro em

termos de computação e adiciona latência ao tempo de execução. Para eliminar esse tempo extra, mova o objeto de conexão para fora da função manipuladora para que ele seja inicializado apenas uma vez. Dessa forma, as solicitações subsequentes poderão

se reconectar à conexão existente. Você é cobrado pelo tempo que sua função leva para ser executada, portanto, uma duração de execução mais curta significa que você pagaria menos.

Além disso, lembre-se de que cada ambiente de execução oferece 512 MB a 10 GB de armazenamento temporário que pode ser acessado no diretório /tmp. Esse armazenamento temporário é bastante útil para armazenar em cache quaisquer dados que sua função precise processar a cada invocação. Imagine uma função Lambda que baixa um arquivo S3 na memória cada

vez que é chamado. Isso é ineficiente se o arquivo raramente for atualizado e lido por vários usuários. Além disso, devido a restrições de recursos ou problemas de desempenho de código, nem sempre é viável carregar grandes dados na memória de uma só vez. Para resolver isso, em vez de consumir dados diretamente da memória, armazene os dados no diretório /tmp e processe-os em partes. Como resultado, na próxima vez que o mesmo arquivo for solicitado, sua função Lambda simplesmente o recuperará do armazenamento local, em vez do bucket S3.

Referências:

https://docs.aws.amazon.com/lambda/latest/operatorguide/execution-environment.html https:// docs.aws.amazon.com/lambda/latest/dg/best-practices.html

Variáveis ambientais

Uma variável de ambiente é um par chave-valor que você pode armazenar e recuperar em sua função Lambda.

As variáveis de ambiente estão vinculadas a uma função e à sua versão específica, o que significa que nenhuma outra função pode acessá-la, exceto a função à qual está associada. Variáveis de ambiente são compartilhadas entre ambientes de execução que pertencem à mesma função.

	48

<!-- image -->





Um cenário comum em que as variáveis de ambiente são úteis é quando você deseja configurar diferentes parâmetros para um aplicativo sem alterar o código. Digamos que você tenha uma função Lambda que precisa ser testada em uma API de desenvolvimento

antes de usar a API de produção. Nesse caso, em vez de codificar os pontos de extremidade e as chaves da API no código de função, você cria duas variáveis de ambiente e as extrai usando os métodos disponíveis para a linguagem de programação que você está usando.

Dessa forma, você poderá alterar parâmetros vinculados a diferentes ambientes sem editar e reimplantar seu código. Basta

atualizar os valores das suas variáveis de ambiente. Fazer edições manuais no código real não é grande coisa, mas pode ser complicado e levar a erros, portanto, essa variável de ambiente é um recurso interessante para ajudá-lo a escrever funções sem servidor limpas e reutilizáveis.

Existem 4 coisas que você deve considerar ao criar uma variável de ambiente:

- As chaves devem começar com uma letra e ter pelo menos dois caracteres.
- As chaves devem consistir apenas em letras, números e o caractere sublinhado (\_).
- Existem variáveis de ambiente que o AWS Lambda usa durante a fase INIT. Elas são chamadas de variáveis de ambiente reservadas. Uma chave para uma variável de ambiente reservada não pode ser usada na configuração da sua função. Por exemplo, se estiver usando um AWS SDK, você poderá definir uma variável chamada 'AWS\_REGION'. Isso resultará em um erro, pois AWS\_REGION é uma variável reservada.
- O tamanho total de todas as variáveis de ambiente não deve exceder 4 KB.

Referências:

https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html  https://aws.amazon.com/

premiumsupport/knowledge-center/lambda-common-environment-variables/ https ://aws.amazon.com/premiumsupport/knowledge- center/lambda-environment-variables-iam-access/

URL da função Lambda

Opcionalmente, você pode configurar um endpoint HTTPS (também conhecido como URL de função) que mapeia para um alias ou versão específica da sua função Lambda. Como quaisquer outros URLs, os URLs de função podem ser acessados por meio de navegadores da web ou por meio de clientes HTTP como urllib3, request (em Python) ou axios (em Node.Js).

Ao habilitar o URL da função, você pode escolher entre dois tipos de autenticação: AWS\_IAM e NONE.

AWS\_IAM, como o nome indica, só é aplicável a identidades IAM; o solicitante deve ser um usuário ou função do IAM. O AWS Lambda decidirá se concederá acesso a uma função com base nas permissões do usuário ou da função do IAM.

URLs de função com tipo de autenticação NONE, por outro lado, permitem que uma função Lambda seja invocada publicamente. À

primeira vista, parece arriscado, e você pode se perguntar por que alguém faria isso. Quando você usa o tipo de autenticação NONE, o AWS Lambda não é mais responsável pela autenticação de solicitações. Isso lhe dá a liberdade de implementar sua própria lógica de autenticação. Você pode, por exemplo, permitir acesso à sua função Lambda apenas para aqueles que

	49

<!-- image -->





estão logados em seu site. Além disso, você também pode definir uma configuração CORS para especificar os domínios dos quais as solicitações de invocação devem se originar.

Referências:

https://docs.aws.amazon.com/lambda/latest/dg/lambda-urls.html  https://

aws.amazon.com/blogs/aws/announcing-aws-lambda-function-urls-built -in-https-endpoints-for-single-f unction-microservices/

Implantando Códigos com Dependências Externas

Como desenvolvedores, quer você esteja codificando no trabalho ou construindo seu próprio projeto, é altamente provável que você importe pelo menos um módulo, estrutura ou biblioteca. As bibliotecas economizam tempo e tornam você mais produtivo. Você não gostaria de reinventar a roda e construir funções do zero, a menos que esteja enfrentando um caso único que não tenha sido resolvido antes. Se você pretende criar aplicativos no AWS Lambda, é essencial saber como incluir dependências em suas funções do Lambda.

Existem dependências que vêm pré-construídas para um tempo de execução específico e também existem dependências externas. O primeiro pode ser usado imediatamente. Este último geralmente é baixado de um repositório público e instalado no seu computador. Freqüentemente, isso é feito com a ajuda de um gerenciador de pacotes (por exemplo, npm para NodeJs, pip para

Python). O AWS Lambda não possui um terminal onde você possa executar comandos pip/npm para instalar dependências externas em um ambiente de execução. E não faria sentido ter um, já que as funções do Lambda são executadas em

ambientes temporários.

Para implantar códigos com dependências externas no AWS Lambda, execute as seguintes etapas:

- Instale todas as dependências externas localmente na pasta do seu aplicativo.
- Crie um pacote de implantação compactando a pasta do projeto. Você pode conseguir isso usando o utilitário zip nativo do Windows ou o comando zip no Linux.
- Carregue o pacote de implantação no AWS Lambda. Você pode enviar o arquivo diretamente para o console do AWS Lambda ou armazená-lo primeiro no Amazon S3 e implantá-lo a partir daí.

O primeiro passo é sempre o mais importante. Certifique-se de instalar as dependências exigidas pelo seu aplicativo localmente em sua pasta e certifique-se de referenciá-las corretamente em seu código. Se não for feito corretamente, você poderá encontrar um erro Unable to import module, o que pode significar duas coisas: ou você colocou as dependências em um local que o Lambda não conseguiu encontrar ou simplesmente não existe.

Referências:

https://docs.aws.amazon.com/lambda/latest/dg/python-package.html https:// aws.amazon.com/premiumsupport/knowledge-center/build-python-lambda-deployment-package /

	50

<!-- image -->





Camadas Lambda

Agrupar dependências externas junto com o código de função dá conta do recado, mas tem algumas desvantagens.

Primeiro, implantar várias funções Lambda que tenham as mesmas dependências é ineficiente e apenas aumentaria o tamanho total de suas funções. Em segundo lugar, atualizar dependências exige tempo e esforço. Atualizar cada função que compartilha dependências semelhantes pode retardar o processo de desenvolvimento. Lambda Layers resolve esses problemas.

Lambda Layers permite armazenar qualquer código adicional (por exemplo, dependências externas, tempos de execução personalizados) separadamente do seu pacote de implantação. Assim como um pacote de implantação, as dependências externas devem estar no formato zip antes de serem carregadas no AWS Lambda.

As camadas Lambda podem ser compartilhadas entre funções Lambda, tornando conveniente e fácil atualizar dependências. Além disso, o processo de implantação se torna mais modularizado e o pacote de implantação fica significativamente menor.

Referências:

https://docs.aws.amazon.com/serverlessrepo/latest/devguide/sharing-lambda-layers.html https://aws.amazon.com/ blogs/aws/new-for-aws-lambda-use-any -linguagem de programação e componentes comuns de compartilhamento

	51

<!-- image -->





Simultaneidade e limitação

O AWS Lambda é inerentemente escalável, mas, como muitas outras coisas, há um limite de escalabilidade. E é importante que você esteja ciente disso, especialmente ao criar um aplicativo de alto rendimento usando funções Lambda.

Simultaneidade é o número de execuções de funções do Lambda que podem ser executadas simultaneamente por um período de tempo. Por padrão, a AWS impõe um limite de 1.000 execuções simultâneas não reservadas em todas as funções do Lambda para cada região por conta. Mas você pode superar esse limite e aumentar ainda mais as execuções simultâneas para centenas de milhares entrando em contato com o AWS Support.

Você pode distribuir simultaneidades estrategicamente entre suas funções, mas a contagem não reservada não deve ficar abaixo de

- Isso significa que o valor máximo padrão de execuções simultâneas reservadas permitidas é limitado

para 900. As execuções simultâneas reservadas alocadas para uma função definem o número máximo de execuções simultâneas instâncias para essa função.

Exemplo:

Função lambda A

- lê e carrega arquivos no Amazon S3.
- 150 execuções simultâneas são reservadas para esta função.

Função lambda B

- grava e atualiza itens em uma tabela do DynamoDB
- 250 execuções simultâneas são reservadas para esta função.

Função lambda C

- processa solicitações HTTP do API Gateway - simultaneidade sem reservas.

A simples adição das execuções simultâneas das funções A e B nos dá uma simultaneidade reservada total de 400.

Isso nos deixa com 600 execuções simultâneas sem reservas. Então, o que acontece quando a demanda pela função Lambda A excede 150 execuções simultâneas? É aqui que o estrangulamento entra em jogo. Quando uma função atinge seu limite máximo de simultaneidade, o AWS Lambda rejeitará as invocações recebidas e retornará um erro de limitação do código de status 429. Não é possível que a função Lambda A faça empréstimo do pool de simultaneidade não reservado restante.

	52

<!-- image -->

 Associate por

e o

Ao calcular os limites de simultaneidade para uma função Lambda, considere duas coisas:

- Tempo de execução
- Número de solicitações tratadas por segundo (solicitações por segundo)

Exemplo:

Função lambda

- processa solicitações HTTP do API Gateway com simultaneidade não reservada

- Espera um tempo médio de execução de 10 segundos

- Espera 150 solicitações por segundo.

Multiplicar o tempo médio de execução pelo número de solicitações por segundo nos dá 1.500 execuções simultâneas. Isso está além do limite padrão. Se você colocar essa função em produção, terá muitas solicitações com falha devido à limitação. Uma das coisas que você pode tentar fazer neste cenário é otimizar o código Lambda e esperar reduzir o tempo de execução. Uma alternativa segura

seria aumentar o limite padrão entrando em contato com o AWS Support.

Referências:

https://docs.aws.amazon.com/lambda/latest/dg/configuration-concurrency.html https:// aws.amazon.com/blogs/compute/managing-aws-lambda-function-concurrency/

Conectando uma função Lambda a uma VPC Se quiser que

sua função Lambda interaja com recursos (por exemplo, banco de dados RDS, instância EC2) dentro de uma sub-rede privada, você não poderá fazer isso por padrão. A razão para isso é que as funções Lambda residem em uma VPC isolada e segura gerenciada pela AWS. É por isso que ao criar uma função Lambda, você não passa por nenhuma configuração de rede (VPC, sub-rede, ENIs), ao contrário da criação de instâncias EC2. Você não pode estabelecer uma conexão de peering de VPC entre a VPC onde as funções do Lambda são executadas e a VPC onde seus recursos privados estão localizados porque a primeira não está acessível aos clientes. A maneira correta é configurar sua função para se conectar a um VPC.

Para conectar sua função Lambda a uma VPC, primeiro certifique-se de que a função de execução de sua função tenha as permissões necessárias para gerenciar a criação e exclusão de Elastic Network Interfaces (ENI). Isso é necessário porque o AWS Lambda cria e exclui interfaces de rede elásticas em sub-redes especificadas na configuração de VPC da sua função. A AWS usa um serviço interno chamado AWS Hyperplane, que serve como um serviço NAT, conectando funções Lambda aos ENIs em sua VPC. Felizmente, existe a política de IAM gerenciada AWSLambdaVPCAccessExecutionRole , que contém as permissões necessárias para o trabalho.

	53

<!-- image -->





Em seguida, especifique a VPC onde seus recursos privados estão localizados nas configurações de rede da função Lambda. Ao criar uma configuração de VPC, você pode escolher as sub-redes onde as ENIs são implantadas e um grupo de segurança que controla o tráfego entre sua função Lambda e a VPC.

Uma vez conectado, sua função Lambda perderá o acesso à Internet. Isso acontece porque o AWS Lambda atribui apenas endereços IP privados às ENIs que ele cria. Mesmo que sua função esteja conectada a uma sub-rede pública, o gateway de Internet da sua VPC ainda não conseguirá rotear o tráfego entre a Internet e sua função.

Para conceder acesso à Internet à sua função Lambda, crie um gateway NAT na sub-rede pública da VPC da sua função e adicione uma entrada à tabela de rotas da sub-rede privada. Defina 0.0.0.0/0 como destino e o gateway NAT como destino.

	54

<!-- image -->

 Associate por

e o

Referências:

https://aws.amazon.com/premiumsupport/knowledge-center/internet-access-lambda-function https:// docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html

Versões e aliases

As revisões são quase inevitáveis ao desenvolver aplicativos, seja adicionando novos recursos ou corrigindo bugs. Em vez de fazer alterações diretamente na versão estável de sua função Lambda, você pode publicar novas versões dela, onde poderá brincar e experimentar à vontade, sem afetar a versão estável.

Uma versão é um instantâneo do estado de uma função Lambda em um determinado momento. Quando você publica uma nova versão, um sufixo :version-number é anexado ao ARN da sua função, que indica sua versão. Um exemplo é mostrado abaixo:

arn:aws:lambda:us-east-2:123456789123:function:cool-function:1

	55

<!-- image -->

e o

O AWS Lambda atribui números de versão monotonicamente. Isso significa que se você excluir uma versão e publicar outra, a sequência de números conforme você adiciona versões não será redefinida; em vez disso, apenas aumentará.

A versão não publicada também é chamada de versão $LATEST. Se você chamar uma função sem qualquer sufixo, o AWS Lambda invocará implicitamente a versão $LATEST. Observe que as versões publicadas são imutáveis; quaisquer modificações no código ou na configuração da função não são possíveis. Se você quiser fazer atualizações de código ou configuração, aplique as alterações à versão $LATEST e publique-a como outra versão.

O problema com as versões é que você não tem controle sobre o que é anexado ao ARN da função. Pode ser incômodo ter que atualizar o ARN da função no código ou nos parâmetros do aplicativo sempre que uma nova versão é lançada. Não seria ótimo se houvesse um ponteiro que pudéssemos usar para alternar entre versões? Dessa forma, você pode simplesmente definir e esquecer o ARN da função. É aqui que os aliases entram em jogo. Você pode pensar em um alias como um apelido dado a um número de versão.

Para invocar uma função com um alias, basta anexar um sufixo :alias-name ao ARN da sua função, como no exemplo abaixo:

arn:aws:lambda:us-east-2:123456789123:function:cool-function:PROD

Você pode alterar a versão para a qual o alias está apontando no console do Lambda ou por meio da API UpdateAlias.

Referências:

https://docs.aws.amazon.com/lambda/latest/dg/configuration-aliases.html https:// docs.aws.amazon.com/lambda/latest/dg/configuration-versions.html

	56

<!-- image -->



Gateway de API da Amazon

O Amazon API Gateway é um serviço totalmente gerenciado que permite publicar, manter, monitorar e proteger suas APIs RESTful. Ele serve como ponto de entrada para seus serviços de back-end com tecnologia AWS Lambda, Amazon EC2, Amazon ECS, AWS

Elastic Beanstalk ou qualquer aplicativo web.

O diagrama a seguir ilustra como uma solicitação flui pelo API Gateway quando uma API é chamada.

- Solicitação de método
    - Esta seção é onde as solicitações do cliente são validadas. Aqui você pode configurar o tipo de autorização

(AWS\_IAM, NONE, autorizador Lambda, autorizador Cognito) para controlar o acesso à API, habilitar o uso de chaves de API ou configurar um validador de corpo de solicitação usando uma função Lambda.

- Você também pode declarar na solicitação de método qualquer corpo de entrada, parâmetros de string de consulta e HTTP cabeçalhos que sua API pode aceitar.
- Solicitação de integração • A

seção Solicitação de integração contém configurações sobre como o API Gateway se comunica com o backend de sua escolha (função Lambda, endpoint HTTP, Mock, AWS Service, VPC Link) e o tipo de integração (proxy ou não proxy) API Gateway usa.

- Para integração sem proxy, você tem a opção de usar modelos de mapeamento para modelar a estrutura dos dados da solicitação que são encaminhados ao back-end.
- Resposta de Integração

	57

<!-- image -->



o

- Esta seção se aplica apenas a uma integração sem proxy. A resposta de integração intercepta o resultado retornado do back-end antes de ser retornado ao cliente.
- Você deve configurar pelo menos uma resposta de integração. A resposta padrão é Passthrough,

que instrui o API Gateway a retornar a resposta como está. Você também pode transformar a resposta para outro formato (base64 ou texto).

- Da mesma forma que na solicitação de integração, você tem a opção de transformar os dados de resposta antes dela é devolvido ao cliente.
- Resposta do Método
    - Assim como a Solicitação de Método, a Resposta do Método é onde você pode definir quais cabeçalhos HTTP o método pode retornar.

API REST x API HTTP x API Websocket

Ao criar uma API, você pode escolher entre uma API REST, uma API HTTP e um endpoint de API WebSocket.

- API REST

- Para casos de uso padrão, a API REST é o que você deseja usar. • Isso lhe dá

controle total sobre a solicitação e a resposta, juntamente com outros recursos de gerenciamento de API, como armazenamento em cache, criação de chaves de API e planos de uso.

- API HTTP

- Mais barato que a API REST
- Projetado para aplicações simples •

Não possui outros recursos do API Gateway

- API WebSocket

- Normalmente usado para aplicações em tempo real (por exemplo, aplicações de chat, aplicações de negociação de mercado)

Referências:

https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-vs-rest.html https:// docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-basic -conceito.html

Integração proxy versus não proxy Em

uma integração proxy, a solicitação do cliente é transmitida como está para o back-end, incluindo quaisquer cabeçalhos ou parâmetros de consulta. Nenhuma modificação é feita nos dados da solicitação. Quanto à resposta, seu backend é responsável por retornar o código de status da resposta, os cabeçalhos e a carga útil ao cliente.

Em uma integração sem proxy, o API Gateway tem controle sobre como os dados do cliente são formatados antes de serem transmitidos ao back-end de integração ou antes de serem retornados ao cliente. Por exemplo, em vez de fornecer todos os

dados da solicitação ao seu back-end, você pode filtrá-los primeiro usando modelos de mapeamento no nível da solicitação de integração

	58

<!-- image -->

 Associate por

e o

para obter apenas a porção que importa. A integração Non-Proxy é um pouco mais complexa de implementar e requer que você tenha conhecimento da Apached Velocity Template Language (VTL), que é o mecanismo que o API Gateway usa para modelos de mapeamento.

Referência:

https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-api-integration-types.html

Variáveis de estágio

Uma variável Stage é um valor de par de chaves que pode ser associado a um estágio de implementação de uma API REST. Você pode

considerá-los como variáveis de ambiente onde você armazena diferentes parâmetros ou valores de configuração que sua API pode acessar em tempo de execução.

Fazer lançamentos canário dentro do mesmo estágio da API REST é uma ótima aplicação de variáveis de estágio. Canary é uma abordagem de implantação na qual o tráfego é dividido em duas partes, uma das quais transporta uma porção maior do tráfego e é roteada para a versão de produção, enquanto a porção menor aponta para o ambiente no qual a nova versão é implantada. Pode ser uma divisão 90/10, uma divisão 70/30 ou até mesmo uma divisão 50/50. Tudo depende de quão agressivo você deseja que sua implantação seja. Esse tipo de configuração permite que os desenvolvedores exponham novos recursos ou correções de bugs a um subconjunto de usuários e recebam feedback deles sem precisar desligar ou fazer alterações diretas na versão de produção.

Considere um estágio de API REST com uma função Lambda como back-end. Suponha que você esteja prestes a lançar uma nova versão da sua API e queira testá-la com um subconjunto de usuários enquanto continua atendendo a maior parte do tráfego com a versão antiga. Você pode transferir todo o tráfego para a nova versão quando estiver satisfeito com ela. Conforme mostrado no diagrama abaixo, o objetivo é ter um único endpoint de API que interaja dinamicamente com duas versões distintas da função Lambda.

	59

<!-- image -->

e o

É aqui que as variáveis de estágio entram em jogo. No exemplo, temos uma função Lambda com dois aliases (prod e beta). Em vez de escrever os aliases reais nas configurações do back-end de integração, podemos usar a variável de estágio ver como espaço reservado. Você pode então alternar entre diferentes valores de ver na configuração Canary do estágio API e controlar a quantidade de tráfego que vai para diferentes aliases.

Referências:

https://docs.aws.amazon.com/apigateway/latest/developerguide/stage-variables.html https:// docs.aws.amazon.com/apigateway/latest/developerguide/canary-release.html

Modelos de mapeamento

Os modelos de mapeamento permitem modificar quaisquer dados de solicitação antes que eles sejam encaminhados para o back-end de integração. Por outro lado, pode ser usado para transformar os dados de resposta antes de serem retornados ao cliente. Vamos entender melhor como isso funciona com um exemplo.

Digamos que você criou uma API para um aplicativo de música que retorna vários detalhes sobre um artista. Para simplificar, considere os seguintes dados JSON:

{

"id": 1234,

"artista": "Queen", "popularidade": 90,

"gêneros": ["Rock progressivo", "Pop rock", "Glam rock"]

}

	60

<!-- image -->



Se um usuário deseja obter a pontuação de popularidade ou o gênero de um determinado artista, não há como ele recuperar as informações que lhe interessam. Para resolver isso, você pode usar modelos de mapeamento para modificar a resposta antes que ela seja enviada de volta ao usuário. Supondo que sua API tenha um caminho de recurso chamado /{id}, um caminho de recurso filho chamado /genres pode ser criado nela. Nas configurações de resposta de integração, adicione um modelo de mapeamento para construir a nova resposta.

Depois de reimplantar a API, os usuários agora podem enviar solicitações GET para o recurso /{id}/genres. No nosso exemplo, a resposta seria simplesmente:

{

'gênero': [" Rock progressivo ","Pop rock","Glam rock"]

}

Os modelos de mapeamento são escritos na Velocity Template Language ou VTL — um mecanismo de modelo baseado em Java desenvolvido pela Apache. Se você não estiver familiarizado com ele, pode levar algum tempo para se familiarizar com os modelos de mapeamento. Não se preocupe, pois o conhecimento de VTL não é exigido no exame CDA; você só deve entender o que é um modelo de mapeamento e para que ele é usado em alto nível.

Lembre-se de que os modelos de mapeamento funcionam apenas para integrações sem proxy. Isso ocorre porque nas integrações de proxy, o API Gateway simplesmente passa os dados que recebe para ambas as extremidades e não tem conhecimento de como a solicitação/resposta é modelada.

	61

<!-- image -->

 Associate por

e o

Você também pode usar modelos de mapeamento para modernizar aplicativos legados. Se você tiver um aplicativo legado que deseja expor, digamos, um serviço web SOAP que processe dados XML, poderá fazer com que os clientes enviem solicitações no formato JSON e, em seguida, fazer com que o Amazon API Gateway transforme esses dados JSON em XML

usando modelos de mapeamento. Quanto ao backend de integração, você pode usar uma função Lambda como middleware para transmitir o XML como uma carga útil para o serviço web SOAP.

Invalidando Cache

O cache geralmente leva à inconsistência de dados, que é um problema comumente enfrentado. Quando o conteúdo é armazenado em cache, o API Gateway não atualiza as entradas de cache até que o Time-To-Live (TTL) expire. Como resultado, quaisquer alterações feitas no banco de dados não serão refletidas imediatamente no lado do cliente, levando a uma disparidade entre o conteúdo real e o que é exibido no aplicativo. No entanto, você pode tomar medidas para atenuar esse problema enviando uma solicitação de invalidação ao endpoint da API. Isso solicitará que o API Gateway atualize seu cache em vez de aguardar a expiração do TTL.

Para invalidar uma entrada de cache, basta incluir o cabeçalho Cache-Control em uma solicitação com idade máxima de 0, conforme mostrado no exemplo abaixo que utiliza a API Fetch em Javascript.

fetch('https://aaaa4vb5wf.execute-api.us-east-1.amazonaws.com/v1', { método: 'GET',

cabeçalhos: {

'Controle de cache': 'idade máxima = 0'

}

});

Referência:

https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-caching.html#invalidate-metho d-caching

Compartilhamento de recursos entre origens (CORS)

CORS é um mecanismo de segurança que a maioria dos navegadores da web, como Google Chrome ou Mozilla Firefox, impõe para relaxar as restrições da política de mesma origem. A política de mesma origem é um recurso de segurança do navegador que limita os scripts carregados de uma origem para interagir apenas com recursos da mesma origem. Embora a intenção seja boa, às vezes pode ser muito restritiva. As empresas hoje geralmente contam com APIs de terceiros para adicionar recursos rapidamente aos seus aplicativos. Isto não seria possível com a Política de Mesma Origem em vigor. Para resolver esse problema, os engenheiros tiveram a ideia do compartilhamento de recursos entre origens para afrouxar as restrições da Política de Mesma Origem.

	62

<!-- image -->





Como funciona o CORS?

Digamos que você visite um site chamado pet.com usando o Google Chrome. Após o carregamento, o Google Chrome baixará os ativos necessários (HTML, Javascript, imagens, fontes, etc.) do servidor do site para renderizar a página. Ao navegar no site, você se depara com um recurso divertido que usa Inteligência Artificial (IA) para identificar raças de cães ou gatos com base em uma imagem que você carrega. Este recurso é alimentado por uma API de terceiros (petbreed.com), que é acessada por meio de um arquivo Javascript. O Google Chrome não enviará imediatamente uma solicitação GET para petbreed.com após você enviar uma imagem. Em vez disso, ele primeiro enviará uma solicitação OPTIONS de comprovação para confirmar se petbreed.com realmente permite que pet.com faça solicitações GET. No final do servidor petbreed.com, os domínios e métodos permitidos podem ser especificados através dos cabeçalhos

Access-Control-Allow-Origin e Access-Control-Request-Method . O desenvolvedor da API pode selecionar quais valores colocar nesses cabeçalhos. Por exemplo, pet.com pode ser definido como um valor de cabeçalho Access-Control- Allow-Origin e GET como um valor de cabeçalho Access-Control-Request-Method. Isso permitirá explicitamente que pet.com faça solicitações GET para petbreed.com. Em seguida, petbreed.com retorna a lista de métodos e domínios

de API permitidos para o Google Chrome. Se pet.com estiver especificado em Access-Control-Allow-Origin, somente então o Google Chrome enviará a solicitação GET real.

	63

<!-- image -->

e o

Assim como petbreed.com, você também pode configurar o CORS no API Gateway. Observe que o CORS está desabilitado por padrão. O CORS é configurado no nível do método de recurso ao usar integrações não proxy. Você deve especificar os cabeçalhos de controle de acesso adequados nos mapeamentos de cabeçalho da resposta de integração da sua API. Por outro lado, se estiver usando uma integração de proxy, você deverá declarar explicitamente os cabeçalhos de controle de acesso na resposta retornada pelo seu back-end.

Referências:

https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html https:// aws.amazon.com/blogs/compute/configurando-cors-on-amazon-api -gateway-apis/

Autorizadores

O API Gateway permite usar o grupo de usuários Cognito ou uma função Lambda para autorizar solicitações de clientes.

Como funciona o autorizador do grupo de usuários do Cognito:

	64

<!-- image -->



- Quando um usuário faz login no grupo de usuários, o Cognito verifica se as credenciais enviadas pelo usuário são válidas.
- Se o login for bem-sucedido, o Cognito retornará um token web JSON (JWT) ao cliente.
- O token web JSON (JWT) é passado para um cabeçalho personalizado que é incluído como parte da solicitação da API.
- O API Gateway procurará o cabeçalho personalizado e verificará sua validade no Amazon Cognito.
- Depois de verificado, o API Gateway aceita a solicitação e realiza a chamada de API. Nesse caso, a função Lambda, que é o backend, é invocada. Se não houver problemas, o API Gateway retornará ao cliente um código de status 200 junto com a resposta da função Lambda.

Talvez você queira implementar um autorizador de função Lambda para impor lógica de autorização personalizada, como aquelas que empregam estratégias de autenticação de token de portador (OAuth) ou algo que usa parâmetros de solicitação para determinar a identidade do chamador. Por se tratar de um método customizado, é necessário escrever a lógica que executa o processo de autorização. Como resultado, isso exige mais esforço de desenvolvimento de sua parte em comparação ao uso do grupo de usuários do Cognito.

Como funciona um autorizador de função Lambda

	65

<!-- image -->





- O aplicativo envia um método GET para o API Gateway, juntamente com um token de acesso ou parâmetros de solicitação.
- O API Gateway verificará se um autorizador Lambda está habilitado para o método. Se for, API Gateway chama a função Lambda que autoriza a solicitação.
- A função Lambda autentica a solicitação. Se a chamada for bem-sucedida, a função Lambda concederá acesso retornando um objeto de saída contendo pelo menos uma política do IAM e um identificador principal.
- O API Gateway avalia a política. Se o acesso for negado, o API Gateway retornará um status 403 proibido código e se o acesso for permitido, o API Gateway executa a solicitação GET.

Referência:

https://aws.amazon.com/blogs/compute/introduzindo-custom-authorizers-in-amazon-api-gateway/

Planos de uso

Se você tem uma ideia para uma API que gostaria de expor ou vender, talvez você tenha criado um serviço de IA que pode ajudar outras empresas, talvez você queira dar uma olhada nos Planos de uso. Os planos de uso são um recurso do API Gateway que pode ajudá-lo a controlar diferentes níveis de acesso a uma API. Por exemplo, você pode criar três planos de assinatura para sua API: plano básico, padrão e premium. Um plano de uso pode ser usado para definir limitações distintas de limitação e cota com base em uma assinatura, que é então aplicada em chaves de API de cliente específicas.

Além disso, você pode vender sua API como um produto no AWS SaaS Marketplace para que outros usuários ou empresas possam ver seu produto e assiná-lo. Os assinantes da API são cobrados com base no número de solicitações feitas ao plano de uso.

Referências:

https://aws.amazon.com/blogs/aws/new-usage-plans-for-amazon-api-gateway/ https:// docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway- api-usage-plans.html

	66

<!-- image -->





Amazon DynamoDB

Amazon DynamoDB é um banco de dados não relacional sem servidor. É chamado de não relacional porque não segue um design de esquema tabular fixo, como um banco de dados relacional o forçaria a fazer. Existem diferentes variações de bancos de dados não relacionais, como banco de dados de valores- chave, banco de dados na memória, banco de dados de documentos e banco de dados gráfico. Você pode pensar no DynamoDB como uma combinação de modelo de banco de dados de valor-chave e documento. Em um banco de dados de valores-chave, os dados são armazenados como pares de valores-chave. A chave atua como um identificador para que o DynamoDB saiba onde no armazenamento ele localizará e recuperará o valor associado à chave. O valor de uma chave pode ser um dado String simples, um número, um valor booleano, um binário, uma lista ou até mesmo uma estrutura de dados complexa, como um documento JSON aninhado.

O DynamoDB oferece alto rendimento e desempenho de latência de um dígito em qualquer escala, por isso é ótimo para casos de uso

que exigem acesso de recuperação rápido, como alto tráfego na Web ou aplicativos de jogos. Como qualquer outro produto sem servidor na AWS, o DynamoDB é totalmente gerenciado e não requer nenhuma administração, portanto, tarefas como aplicação de patches e atualização não são mais sua preocupação.

Por padrão, o DynamoDB replica dados em diversas zonas de disponibilidade em uma região. Possui capacidade integrada de tolerância a falhas e pode ajustar automaticamente a capacidade com base no volume de solicitações. Ao contrário de um banco de dados relacional normal, você não precisa fornecer um endpoint, nome de usuário ou senha do banco de dados ao se conectar ao DynamoDB. Você simplesmente precisa especificar o nome da tabela e usar comandos da API do DynamoDB que correspondam a uma operação CRUD necessária. As permissões para acessar o DynamoDB são gerenciadas pelo serviço IAM.

Componentes do núcleo

Mesa

- uma coleção de itens relacionados • pode ter zero ou mais itens

Item

- representa um único registro que você deseja inserir em uma tabela • cada item pode ter um ou mais atributos

Atributo

- um elemento de dados fundamental de um item

Chaves

primárias 1. Chave de partição (obrigatória)

- identifica exclusivamente cada item em uma tabela

	67



 Associate por

e o

- um valor de chave de partição é usado como entrada para a função hash interna no DynamoDB. A saída dessa função hash determina a partição ou o armazenamento físico interno no qual o item será armazenado ou recuperado.

- Chave de classificação (opcional)

- oferece flexibilidade adicional ao consultar dados • uma tabela com chave de

partição e chave de classificação pode ter vários itens com chave de partição semelhante valores, visto que eles possuem valores de chave de classificação exclusivos.

- pode classificar os dados em ordem.

Referências:

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html https://docs.aws.amazon.com/ amazondynamodb/latest/developerguide/Introduction.html

Índice Secundário Local vs. Índice Secundário Global (LSI vs. GSI)

O DynamoDB oferece suporte a dois índices secundários: Índice Secundário Global (GSI) e Índice Secundário Local (LSI).

Um índice secundário global pode ter uma chave de partição e uma chave de classificação diferentes daquelas da sua tabela base. Você pode pensar nela como uma tabela secundária que pode ter um design de esquema completamente diferente. Um Índice Secundário Global é 'global' no sentido de que uma consulta no índice pode abranger todos os dados da tabela base em todas as partições.

Um índice secundário local permite criar um índice onde você pode usar um atributo não-chave de sua tabela base como uma chave de classificação. As partições

de dados no LSI são organizadas automaticamente pelo DynamoDB usando a chave de partição de sua tabela base. Você só precisa especificar a chave de classificação e os atributos que deseja projetar. Ao contrário do GSI, o único momento em que você pode criar um Índice Secundário Local é durante a criação de uma tabela. Não é possível criar um LSI em uma tabela existente.

Principais diferenças:

Índice Secundário Global	Índice Secundário Local

Atributos-chave Um índice secundário pode ter uma chave de partição,

chave de classificação e atributos não-chave.

Um índice secundário pode ter apenas uma chave de classificação e atributos não-chave

Consulta de extensão

As consultas abrangem todos os dados da tabela base, em todas as partições

As consultas têm como escopo a chave de partição de sua tabela base

Operações de índice

Pode ser criado a qualquer momento

Só pode ser criado durante a criação de uma tabela

Tamanho

Sem restrição

Tamanho total dos itens indexados em um

<!-- image -->

	68







restrições por

valor da chave de partição

o valor da chave de partição não deve exceder 10 GB

Consistência de leitura

Consistência eventual

Suporta Eventual e Forte Consistência

Provisionado

Consumo de rendimento

Tem seu próprio rendimento provisionado para atividades de leitura e gravação

Consome unidades de capacidade de sua tabela base

Projetado Atributos

Só é possível solicitar atributos que estejam projetados no GSI

Atributos solicitados que não são projetados no LSI são buscados automaticamente na tabela base pelo DynamoDB

<!-- image -->

Referências:

https://aws.amazon.com/blogs/database/how-to-design-amazon-dynamodb-global-secondary-indexes/ https:// docs.aws.amazon.com/amazondynamodb/latest/developerguide/SecondaryIndexes.html https://docs.aws.amazon.com/ amazondynamodb/latest/developerguide/LSI.html

Projeções Ao

criar um LSI ou GSI você define a lista de atributos que deseja projetar ou copiar da tabela base para o índice secundário. As chaves primárias (partição e chave de classificação) são sempre projetadas no índice secundário, mas você também pode especificar atributos não-chave que serão projetados no índice.

Três opções na projeção de atributos:

- KEYS\_ONLY - todos os itens de um índice conterão apenas as chaves primárias da tabela base que você definiu.
- INCLUIR - permite escolher outros atributos não-chave que serão incluídos junto com as chaves primárias da sua tabela base.
- TODOS - todos os atributos da sua tabela base serão copiados para o seu índice secundário.

Referência:

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html

Operações de verificação e

consulta Uma operação de consulta realiza uma pesquisa direta em itens específicos que você deseja pesquisar com base em uma chave de partição. É como folhear o índice de um livro para determinar em quais páginas uma palavra-chave pode ser encontrada. A

	69

<!-- image -->

 Associate por

e o

A operação de digitalização, por outro lado, é análoga a percorrer as páginas uma por uma para encontrar uma determinada informação. No caso do DynamoDB, uma operação Scan irá literalmente ler e retornar todos os itens de uma tabela.

Opcionalmente, você pode fornecer uma expressão de filtro ao solicitar que um Scan retorne apenas um subconjunto de itens na tabela. No entanto, a filtragem ocorre somente após a conclusão da verificação. Na verdade, você ainda será cobrado por todos os itens lidos.

Em termos de eficiência, custo e velocidade, o Query supera facilmente o Scan, especialmente em tabelas grandes. À medida que o número de seus itens aumenta, mais lenta e cara se torna a verificação. Como prática recomendada, use a operação Consulta junto com índices secundários, tanto quanto possível. A varredura só deve ser usada quando absolutamente

necessário.

Referências:

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Scan.html https:// docs.aws.amazon.com/amazondynamodb/latest/developerguide/Query.html

Calculando a unidade de capacidade de leitura e gravação necessária para sua tabela do DynamoDB

Unidade de capacidade de leitura

Modo sob demanda

Quando você escolhe o modo sob demanda, o DynamoDB acomoda instantaneamente suas cargas de trabalho à medida que elas aumentam ou diminuem para qualquer nível de tráfego alcançado anteriormente. Se o nível de tráfego de uma carga de trabalho atingir um novo pico, o DynamoDB se adaptará rapidamente para acomodar a carga de trabalho. A taxa solicitada é limitada apenas pelos limites da tabela padrão de taxa de transferência do DynamoDB, mas pode ser aumentada mediante solicitação.

Para tabelas de modo sob demanda, você não precisa especificar a quantidade de taxa de transferência de leitura que espera que seu aplicativo execute. O DynamoDB cobra pelas leituras que seu aplicativo executa nas tabelas em termos de unidades de solicitação de leitura.

- 1 unidade de solicitação de leitura (RRU) = 1 leitura fortemente consistente de até 4 KB/s = 2 leituras eventualmente consistentes de até 4 KB/s por leitura. • 2 RRUs = 1

solicitação de leitura transacional (uma leitura por segundo) para itens de até 4 KB. • Para leituras de itens maiores que 4 KB, número total de leituras necessárias = (tamanho total do item/4 KB) arredondado

acima.

Modo provisionado

	70

<!-- image -->





Se você escolher o modo provisionado, especifique o número de leituras e gravações por segundo necessárias para seu aplicativo. Você pode usar o escalonamento automático para ajustar automaticamente a capacidade provisionada da sua tabela em resposta às alterações de tráfego.

Para tabelas de modo provisionado, você especifica a capacidade de rendimento em termos de unidades de capacidade de leitura (RCUs).

- 1 unidade de capacidade de leitura (RCU) = 1 leitura fortemente consistente de até 4 KB/s = 2 leituras eventualmente consistentes de até 4 KB/s por leitura. • 2

leituras eventualmente consistentes de até 4 KB/s por leitura também equivalem a 1 leitura eventualmente consistente de até 8 KB/s por leitura.

- Para obter o RCU por item, você deve dividir o tamanho médio do item por 4 KB (para consistência forte) ou 8 KB (para consistência eventual).

- 2 RCUs = 1 solicitação de leitura transacional (uma leitura por segundo) para itens de até 4 KB. • Para leituras de itens maiores que 4 KB, número total de leituras necessárias = (tamanho total do item/4 KB) arredondado

acima.

Unidade de capacidade de gravação

Modo sob demanda

Para tabelas de modo sob demanda, você não precisa especificar a quantidade de taxa de transferência de gravação que espera que seu aplicativo execute. O DynamoDB cobra pelas gravações que seu aplicativo executa nas tabelas em termos de unidades de solicitação de gravação.

- 1 unidade de solicitação de gravação (WRU) = 1 gravação de até 1 KB/s.

	71

<!-- image -->





- 2 WRUs = 1 solicitação de gravação transacional (uma gravação por segundo) para itens de até 1 KB. • Para

gravações maiores que 1 KB, o número total de gravações necessárias = (tamanho total do item/1 KB) arredondado para cima

Modo provisionado

Para tabelas de modo provisionado, você especifica a capacidade de rendimento em termos de unidades de capacidade de gravação (WCUs).

- 1 unidade de capacidade de gravação (WCU) = 1 gravação de até 1

KB/s. • 2 WCUs = 1 solicitação de gravação transacional (uma gravação por segundo) para itens de até 1 KB.

- Para gravações maiores que 1 KB, o número total de gravações necessárias = (tamanho total do item / 1 KB) arredondado para cima.

Exemplo: um aplicativo grava 75 itens em uma tabela do DynamoDB a cada segundo, onde cada item tem 11,5 KB de tamanho. Para obter o WCU, basta seguir estes três passos simples abaixo:

Etapa 1: Obtenha o tamanho médio do item

= 11,5 KB = 12 KB (arredondado)

Etapa 2: obtenha o WCU por item dividindo o tamanho médio do item por 1 KB

Divida o tamanho médio do item por 1 KB e arredonde o resultado:

= 12KB / 1KB

= 12 WCU por item

Etapa # 3 Multiplique o WCU por item pelo número de itens a serem gravados por segundo

= 12 WCU por item × 75 gravações por segundo

= 900 WCU

	72

<!-- image -->

 Associate por

e o

Referência:

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadWriteCapacityMod       e.html

DynamoDB Streams

DynamoDB Streams é um recurso que captura alterações no nível do item em uma tabela do DynamoDB quase em tempo real. Quando um item é modificado usando qualquer uma das operações de gravação (PutItem, UpdateItem ou DeleteItem), o DynamoDB o detecta como um

evento e envia o registro modificado para um log de transações. Cada registro de fluxo aparece exatamente uma vez no log e é retido por 24 horas. Além disso, a ordem em que os itens são modificados na tabela é preservada conforme são gravados no log.

Observe que uma modificação real deve ser feita em um item para que ele seja considerado um evento. Se você enviar uma solicitação UPDATE que não altere nada, o DynamoDB simplesmente a ignorará e um registro desse evento não será criado. De certa forma, isso evita a geração de registros duplicados caso uma alteração seja aplicada acidentalmente mais de uma vez a um item.

Casos de uso

	73

<!-- image -->





- Agregação de dados para auditoria – no exemplo abaixo, a tabela Transações é a tabela de origem.

Quando novas transações são inseridas nele, novos registros preencherão os fluxos do DynamoDB. A função Lambda lê os registros do stream e incrementa os atributos total e total\_tx da tabela TotalTransactions.

- Notificação - no exemplo abaixo, a função Lambda lê os Streams do DynamoDB, verifica os detalhes da transação, constrói uma mensagem de notificação e a envia para um tópico SNS. Os usuários inscritos no tópico SNS recebem

mensagens de alerta por e-mail sobre suas atividades de transação.

	74

<!-- image -->





Existem quatro tipos de visualização de stream que você pode escolher ao usar Streams do DynamoDB. O Stream View Type determina que tipo de dados você deseja capturar.

- KEYS\_ONLY - apenas os atributos chave (Chave de Partição + Chave de Classificação) do item modificado são capturados.
- NEW\_IMAGE - o estado mais recente de todo o item modificado será capturado.
- OLD\_IMAGES - todo o item que aparecia antes da atualização é capturado.
- NEW\_AND\_OLD\_IMAGES - o estado anterior e o mais recente antes da atualização são capturados.

Se precisar de um aplicativo de streaming mais complexo, talvez você queira configurar o DynamoDB para enviar registros para um stream do Kinesis Data. Isso lhe dará acesso a recursos mais avançados, como retenção de dados mais longa (> 24 horas), funções integradas para processamento de grandes quantidades de dados e integrações com outros serviços Kinesis (Kinesis Firehose e Kinesis Data Analytics).

Observe que a integração com o Kinesis Data Stream é um recurso diferente do DynamoDB Streams

Referências:

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.html https://aws.amazon.com/ blogs/database/dynamodb-streams-use-cases-and-design-patterns/ https ://docs.aws.amazon.com/amazondynamodb/ latest/developerguide/kds.html

Acelerador DynamoDB (DAX)

DAX é um cache na memória altamente disponível criado propositadamente para o DynamoDB. Uma tabela DynamoDB sem qualquer camada de cache já oferece tempos de resposta na faixa de milissegundos de um dígito. Agora, com o DAX implementado, você pode até atingir tempos de resposta em microssegundos para milhões de solicitações por segundo.

Habilitar o DAX não é tão complicado. No entanto, as etapas não são tão simples quanto as de outros recursos do DynamoDB,

como DynamoDB Streams ou GSI, onde você simplesmente clica em um botão no Console AWS. Para usar o DAX, primeiro você precisa criar um cluster DAX. Um cluster DAX é simplesmente um grupo de instâncias EC2 (também chamadas de nós). O DynamoDB é responsável pelo gerenciamento e operação do cluster. Você é quem definirá o tamanho do cluster, o número de nós e sua distribuição nas zonas de disponibilidade. A implantação de um cluster DAX de nó único em uma única AZ é possível, mas não é recomendada

porque essa configuração não sobreviverá a uma falha de máquina ou de AZ. É importante observar que um cluster DAX está hospedado em uma VPC, o que significa que não é acessível publicamente por padrão, a menos que você o configure. Se desejar ler de um cluster DAX usando uma função Lambda de maneira privada, você deverá primeiro configurar essa função para se conectar à VPC do seu cluster.

Depois de criar o cluster DAX, você precisa fazer pequenos ajustes no código do seu aplicativo. Primeiro, você precisa baixar e importar o SDK do cliente DAX. Em seguida, aponte suas chamadas de API existentes do DynamoDB para o endpoint do cluster DAX, substituindo o cliente DynamoDB existente por um novo cliente DAX. Você não precisa preencher o

	75

<!-- image -->





armazenar em cache ou gravar qualquer lógica de cache, como carregamento lento ou invalidação de cache. Todas as operações pesadas são feitas para você pelo cliente DAX.

importar boto3 importar amazondax

DAX\_endpoint = 'dax://tdojo.aaabb2.dax-clusters.us-east-2.amazonaws.com'

#Cliente DynamoDB

#dynamodb\_client = boto3.client('dynamodb')

#Cliente DAX

dax\_client = amazondax.AmazonDaxClient(endpoint\_url=DAX\_endpoint)

#GetItem usando a resposta do cliente DAX

= dax\_client.get\_item( TableName='Music', Key={ 'artist': {'S': 'Foo

Fighters'}, 'song': {'S': 'Walk'}

})

Use DAX se:

- Você tem um aplicativo de leitura intensiva que requer tempo de resposta na faixa de microssegundos.
- Você tem um grande conjunto de dados que são lidos com frequência.
- Seu aplicativo pode eventualmente tolerar leituras consistentes.

Não use DAX se:

- Seu aplicativo requer leituras fortemente consistentes.
- Seu aplicativo executa mais gravações do que leituras.

Referências:

https://aws.amazon.com/dynamodb/dax/ https://

aws.amazon.com/blogs/database/how-to-increase-performance-while-reduce-costs-by-using-amazo n -dynamodb-accelerator-dax-and- aws-lambda/

	76





ACID de transações do

DynamoDB (atomicidade, consistência, isolamento, durabilidade) são quatro propriedades de banco de dados que garantem a integridade e validade dos dados mesmo em caso de queda de energia ou falha do sistema. A maioria dos bancos de dados relacionais (MySQL, SQL Server, PostgreSQL) que vemos hoje aderem ao princípio do ACID, tornando-os adequados

para aplicações críticas de negócios, como aquelas que lidam com transações financeiras como bancárias, processamento

de cartão de débito ou execução de pedidos. . Apesar de ser um banco de dados não relacional, você pode obter o mesmo suporte ACID para DynamoDB por meio de transações do DynamoDB.

Mas primeiro, o que é uma transação?

Uma transação nada mais é do que uma coleção de consultas que atua efetivamente como uma única unidade de trabalho. Para explicar isso, considere o seguinte exemplo:

Conta A

<!-- image -->

Equilíbrio

165	US$ 500

Conta B

Equilíbrio

785	US$ 800

Acima estão duas tabelas simples que pertencem a contas bancárias imaginárias. Digamos que a Conta A queira transferir $ 100 para a Conta B. Antes de prosseguir, é lógico verificar primeiro se a Conta A tem saldo suficiente para suportar a transação. O DynamoDB possui uma operação condicional que podemos usar para verificar se o saldo da Conta A é maior que US$ 100. Se for, passamos para a

próxima etapa. Caso contrário, abortaremos a transferência. A segunda etapa seria subtrair US$ 100 da Conta A, totalizando seu novo saldo em US$ 400. A terceira e última etapa é adicionar US$ 100 à Conta B, totalizando seu novo saldo em US$ 900. Muito simples, certo? Em cenários do mundo real, as operações CRUD não são executadas individualmente, especialmente para cargas de trabalho críticas,

como transações financeiras.

Em nosso exemplo, precisávamos de três operações executadas sequencialmente para concluir a transferência. Surge um

problema se ocorrer uma falha durante a terceira etapa. $ 100 seriam deduzidos da Conta A, mas você não veria esse valor adicionado à Conta B.

	77

<!-- image -->





Com as transações do DynamoDB, você pode agrupar essas três operações individuais em uma única função. Esta função equivale a 1 transação. Como resultado, se uma das operações falhar, a transação como um todo também falhará. A condição para o sucesso da transação é bastante simples. Todas as três operações devem ser bem-sucedidas – é tudo ou nada.

O DynamoDB oferece duas operações de transação:

- TransactWriteItems - você pode agrupar até 100 ações de gravação em uma única operação do tipo tudo ou nada. As ações que você pode adicionar são as operações PutItem, UpdateItem, DeleteItem e ConditionCheck.
- TransactGetItems - contém um conjunto de leitura, com uma ou mais operações GetItem. Cada transação pode inclua até 100 itens Get exclusivos ou até 4 MB de dados, incluindo condições.

As transações são 2 vezes mais caras do que leituras ou gravações regulares porque o DynamoDB precisa realizar duas leituras/ gravações subjacentes de cada item; um para preparar a transação e outro para confirmar a transação.

Referências:

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transaction-apis.html https://aws.amazon.com/blogs/ aws/new-amazon-dynamodb-transactions/ https:/ /aws.amazon.com/blogs/aws/new-amazon-

dynamodb-transactions/

Tempo de vida do DynamoDB (TTL)

Time-To-Live ou TTL permite expirar automaticamente um item com base em um carimbo de data/hora definido. O TTL pode ser uma ferramenta poderosa para limpar sua tabela do DynamoDB e manter seu tamanho pequeno e gerenciável ao longo do tempo. O tamanho da tabela afeta diretamente o custo de armazenamento e execução de consultas, portanto, ter menos dados para ler e armazenar significa mais economia de custos para você.

	78



 Associate por

e o

O TTL também é útil em situações em que você só precisa manter os dados por um determinado período de tempo e, depois disso, você se livra deles. Por exemplo, se você tiver um aplicativo que oferece acesso a um serviço por tempo limitado, em vez de codificar a lógica para expirar o acesso do usuário, pode ser mais fácil apenas ativar o TTL e deixar o DynamoDB

cuidar disso para você.

Como usar o TTL?

- Habilite o TTL por meio do console do DynamoDB ou usando a API UpdateTimeToLive.

- Atribua o nome do atributo TTL que o DynamoDB procurará para determinar se um item está qualificado para expiração.

Você pode escolher qualquer nome para um atributo TTL, mas deve ser o mesmo para todos os itens que você deseja remover eventualmente, porque o TTL se aplica no nível da tabela.

- O atributo TTL deve ser um tipo de dados Número e seu valor deve estar no formato de época Unix.

Referências:

- Os itens não são excluídos instantaneamente no momento em que o TTL expira. O TTL tem um atraso que aumenta à medida que o tamanho da tabela aumenta. De acordo com a documentação oficial, o DynamoDB exclui itens expirados dentro de 48 horas após a expiração, algo que você pode levar em consideração ao projetar um aplicativo.

<!-- image -->

Tabelas globais do DynamoDB

As tabelas globais do DynamoDB permitem replicar automaticamente sua tabela do DynamoDB nas regiões da AWS de sua escolha. Se você está optando por uma arquitetura multirregional para um aplicativo, a vantagem para você, como desenvolvedor, é que você não precisa mais supervisionar a replicação de dados por conta própria. O DynamoDB usa DynamoDB Streams para gerenciar a sincronização de tabelas. Portanto, antes de poder usar tabelas globais, você deve habilitar Streams do DynamoDB com o NEW\_AND\_OLD\_IMAGES StreamViewType.

	79

<!-- image -->





Por que usar tabelas globais?

- Para proteger seu aplicativo contra falhas regionais - as tabelas globais do DynamoDB podem fazer parte do seu

plano de recuperação de desastres, pois pode ajudá-lo a mitigar o impacto das interrupções nas regiões da AWS. Se uma região enfrentar alguns problemas que afetem seu aplicativo, você sempre poderá transferir o tráfego de usuários afetados para uma região de trabalho.

- O redirecionamento do tráfego para tabelas em outras regiões não é feito automaticamente pelo DynamoDB. Você ainda precisa implementar a lógica de failover em seu aplicativo.

- Para melhorar o desempenho de aplicativos sensíveis à latência - se você tiver um aplicativo sensível à latência aplicativo com alcance global, você deseja manter a latência o mais baixa possível, independentemente de onde seus usuários estejam localizados. A latência é amplamente afetada pela distância. Imagine ter uma tabela DynamoDB em Cingapura (ap-sudeste-1). Aqueles em Singapura e nos países vizinhos terão tempos de resposta mais rápidos do que os utilizadores, por exemplo, nos Estados Unidos. Isso se deve ao fato de as pessoas estarem geograficamente mais próximas de seus dados. Portanto, é importante trazer os dados o mais próximo possível dos usuários.

Referências:

https://aws.amazon.com/dynamodb/global-tables/ https://

aws.amazon.com/blogs/database/how-to-use-amazon-dynamodb-global-tables-to-power-multiregion- uma arquitetura/

	80

<!-- image -->

 Associate



AWS CloudFormation

Gerar recursos da AWS por meio do console da AWS pode não parecer grande coisa se você estiver acostumado com o

processo; independentemente disso, ainda pode levar muito tempo, especialmente se você tiver que configurar um ambiente grande com muitos componentes. Sem mencionar que os processos manuais estão sujeitos a erros humanos. Em vez de iniciar manualmente o recurso, você pode descrevê-lo em um arquivo de texto, facilitando muito a criação de ambientes previsíveis.

Com o CloudFormation, você pode modelar todo o seu ambiente de nuvem em um modelo do CloudFormation usando JSON ou YAML. Para criar um ambiente, basta fazer upload do seu modelo CloudFormation para o Amazon S3.

CloudFormation pegará o modelo do S3 e criará os recursos especificados nele.

Pilha

Os recursos individuais criados pelo CloudFormation são tratados como uma única unidade chamada 'pilha'. Por padrão, se um dos recursos não for criado durante a criação da pilha, a pilha reverterá para seu último estado de funcionamento. Se não houver um último estado de funcionamento, todos os recursos serão encerrados, incluindo aqueles que foram criados com êxito antes da falha.

Referência:

https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html

Partes do modelo CloudFormation

- AWSTemplateFormatVersion - permite definir a versão do modelo que você deseja usar, que

determina os recursos do modelo. Se você não atribuir uma versão, o CloudFormation assumirá automaticamente que você deseja usar a versão mais recente.

- Descrição - permite incluir comentários sobre seu modelo para ajudá-lo a descrever e adicione mais detalhes sobre o seu modelo.

- Metadados - permite fornecer objetos que fornecem detalhes sobre o modelo ou até mesmo detalhes de implementação de recursos específicos.

- Recursos (OBRIGATÓRIOS) - É aqui que você define todos os recursos que deseja incluir em sua pilha.

Recursos da AWS, como instância EC2, função Lambda e bucket S3, são declarados na seção Recursos. Observe que

a seção Recursos é a única seção OBRIGATÓRIA em um modelo CloudFormation. Todas as outras seções são opcionais.

- Mapeamentos - corresponde uma chave a um conjunto correspondente de valores nomeados.

- Parâmetros - ao escrever modelos do CloudFormation, é muito improvável que haja valores codificados, como ID de AMI, ID de

grupo de segurança e assim por diante. Os parâmetros permitem que os usuários passem valores dinamicamente com base em seu caso de uso.

	81

<!-- image -->

 Associate por

e o

- Condições - define condições usando as funções de condição intrínseca. Essas condições determinam quando o AWS CloudFormation cria os recursos associados.

- Transformar - você pode usar esta seção para escrever modelos no AWS Serverless Application Model Sintaxe (AWS SAM). A sintaxe usada no SAM é diferente do modelo padrão do CloudFormation.

Nos bastidores, o CloudFormation converte e 'transforma' os modelos escritos na seção Transform em um modelo normal do CloudFormation.

Referências:

https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html https:// docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/gettingstarted.templatebasics.html

Funções intrínsecas e pseudoparâmetros

CloudFormation oferece várias funções integradas e pseudoparâmetros predefinidos que você pode usar para criar modelos dinâmicos e flexíveis. Nesta seção, examinaremos alguns dos mais comuns e veremos como eles são realmente usados.

- !Ref - retorna o valor de um parâmetro ou recurso. Quando você especifica o nome lógico de um recurso, ele gera um

valor que pode ser usado para fazer referência a esse recurso (por exemplo, ID da instância, nome do bucket, ID da API). Normalmente, numa pilha, haverá dependências entre recursos. Por exemplo, se quiser anexar um endereço IP elástico (EIP) a uma instância do EC2, você deverá especificar a instância usando seu ID de instância. O problema é que o ID da instância não estará disponível até que a instância EC2 seja criada, portanto, não é possível codificá-lo no modelo

CloudFormation. Para contornar isso, podemos usar a função Ref para recuperar o ID da instância assim que estiver disponível e fazer com que o CloudFormation o insira durante a criação da pilha.

Recursos: MyEC2Instance:

Tipo: AWS::EC2::Instance

Propriedades:

ImageId: ami-0cd490fb43e2559ed InstanceType: t2.micro MyEIP:

Tipo:

AWS::EC2::EIP Propriedades: InstanceId: !Ref

MyEC2Instance

- !FindInMap - este funciona apenas com a seção Mapeamentos. FindInMap retorna um valor nomeado com base em uma chave especificada. Por exemplo, suponha que você tenha AMIs personalizadas em us-east-1 e us-east-2. E você

	82

<!-- image -->





desejam ter certeza de que seus IDs de imagem estão acessíveis em tempo de execução, independentemente da região em

que a pilha está implantada. Primeiro, crie um mapa de dois níveis na seção Mapeamentos. Cada mapa é uma chave que aponta para um par nome-valor. Faça das regiões suas chaves de nível superior, seguidas por um par nome-valor que representa o nome da AMI e seu ID de imagem correspondente. Recupere os IDs das imagens com FindInMap usando a sintaxe abaixo:

!FindInMap [MapaNome, TopLevelKey, SecondLevelKey ]

Mapeamentos:

Minhas regiões: us-east-1:

Ubuntu personalizado: ami-0cd490fb43e2559ed nós-leste-2:

Ubuntu personalizado: ami-01581ffba5551cdf3

Recursos:

MyEC2Instance: Tipo: AWS::EC2::Instance Propriedades:

ImageId: !

FindInMap [ MyRegions, !Ref "AWS::Region", CustomUbuntu ] Tipo de instância: t2.micro

No trecho acima, MyRegions é o nome do mapa. Para a chave de nível superior, o pseudoparâmetro AWS::Region é usado em vez de um valor estático para capturar a região onde a pilha será implantada. Por último, a chave CustomUbuntu é mapeada para o ID da imagem real. Dessa forma, se um usuário optar por implantar a pilha em us-east-1 ou us-east-2, não haverá problema.

- !GetAtt - retorna o valor de um atributo de um recurso. Esta função intrínseca funciona de maneira semelhante à função !Ref. Só que

desta vez, há mais valores para escolher, dependendo do recurso.

Sintaxe para o nome da função (abreviação):

!GetAtt nomelógicoOfResource.attributeName

O recurso AWS::EC2::Instance contém atributos como a zona de disponibilidade onde a instância especificada é executada, seu endereço IP público e privado e seu nome DNS público. Se você deseja recuperar o IP público do recurso MyEC2Instance, use a função !GetAtt MyEC2Instance.PublicIp.

Sempre verifique a documentação dos atributos disponíveis para um determinado recurso.

	83

<!-- image -->

 Associate



Referências:

https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html https:// docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/pseudo-parameter-reference .html

Usando referências dinâmicas para passar credenciais com segurança

As referências dinâmicas permitem fazer referência a valores externos em seu modelo de pilha. Esses valores podem ser parâmetros de configuração, cadeias de conexão de banco de dados ou segredos, como senhas ou chaves de API armazenadas no Systems Manager Parameter Store e no AWS Secrets Manager. Com referências dinâmicas, você não precisa codificar credenciais na

seção de parâmetros do seu modelo de pilha. Em vez disso, você pode usar espaços reservados para referenciá-los. Quando você implanta a pilha, o CloudFormation recupera os valores reais do serviço externo e os substitui nos espaços reservados. Isso evita que segredos sejam expostos nos recursos ou logs da pilha do CloudFormation.

CloudFormation oferece suporte aos seguintes nomes de chaves de referência:

- ssm (parâmetro de texto simples do SSM Parameter Store)
- ssm-secure (parâmetro de string segura do SSM Parameter Store) 3. secretsmanager (segredo do Secrets Manager)

Suponha que você esteja construindo uma pilha para um aplicativo composto por uma função Lambda e um banco de

dados RDS. Para proteger as credenciais do banco de dados contra exposição, você não deve armazená-las em texto simples no modelo, no código de função ou nas variáveis de ambiente da função. Em vez disso, você pode armazenar as credenciais como um segredo no AWS Secrets Manager e depois referenciá-las em seu modelo por meio da chave de referência integrada do secretsmanager.

MyRDSInstance:

Tipo: 'AWS::RDS::DBInstance' Propriedades:

DBName: MyRDSInstance

AllocatedStorage: '20' DBInstanceClass: db.t2.micro

Motor: mysql

	84

<!-- image -->





MasterUsername: '{{resolve:secretsmanager:DBcreds:SecretString:nomedeusuário}}' MasterUserPassword: '{{resolve:secretsmanager:DBcreds:SecretString:password}}'

Você pode passar o nome secreto (neste exemplo, "DBcreds") como uma variável de ambiente para a função Lambda.

AWSTemplateFormatVersão: '2010-09-09' Recursos:

Minha função Lambda:

Digite: 'AWS::Lambda::Function' Propriedades:

Código:

S3Bucket: nome do seu bucket s3 S3Key: my-lambda- function.zip Handler: index.handler

Função: !GetAtt MyLambdaExecutionRole.Arn Tempo de execução: python3.9 Ambiente:

Variáveis:

SECRET\_NAME: 'DBCreds'

A função Lambda pode então recuperar o valor secreto do AWS Secrets Manager em tempo de execução usando a API GetSecretValue.

importar json importar boto3

importar sistema operacional

def lambda\_handler(evento, contexto):

# Obtenha o nome do segredo de uma variável de ambiente secret\_name = os.environ['SECRET\_NAME']

# Crie um cliente do Secrets Manager secretsmanager

= boto3.client('secretsmanager')

# Obtenha o nome de usuário e a senha do segredo secret\_value = secretsmanager.get\_secret\_value(SecretId=secret\_name) secret\_dict = json.loads(secret\_value['SecretString'])

	85

<!-- image -->





nome de usuário = secret\_dict['nomedeusuário'] senha = secret\_dict['senha']

Referências:

https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/dynamic-references.html https:// aws.amazon.com/premiumsupport/knowledge-center/cloudformation-stack-dynamic-parameters/

Modelo de aplicativo sem servidor da AWS (SAM)

O AWS Serverless Application Model, ou AWS SAM, é uma estrutura de código aberto para a construção de aplicativos sem servidor. O SAM é dividido em duas partes: o modelo SAM e a Interface de Linha de Comando (CLI) do SAM.

Modelo SAM

Os modelos SAM fornecem acesso a tipos de recursos personalizados, que são basicamente wrappers para os existentes disponíveis no CloudFormation. Esses tipos de recursos personalizados permitem construir aplicativos sem servidor em menos linhas de código. O recurso SAM AWS::Serverless::Function, por exemplo, faz mais do que apenas criar uma função Lambda. Este tipo de recurso pode gerar uma função Lambda, uma função de execução IAM,

uma fonte de evento e conectá-los todos juntos. Como resultado, o tempo de desenvolvimento é significativamente reduzido.

Antes de poder acessar os recursos personalizados no SAM, você deve declarar a macro de transformação AWS::Serverless na seção Transform de um modelo do CloudFormation.

	86

<!-- image -->





Quando você implanta um modelo SAM, o CloudFormation procurará primeiro a seção Transform e, se houver, todos os recursos definidos nela serão expandidos para seus recursos nativos do CloudFormation. O SAM tem opções limitadas em termos de tipos de recursos. É muito específico para recursos sem servidor, como funções Lambda, estágios API Gateway, buckets Amazon S3 e tabelas DynamDB.

Os recursos SAM podem ser escritos junto com os recursos nativos do CloudFormation. Portanto, se houver necessidade de criar recursos não disponíveis no SAM, como uma instância EC2, você pode declará-los em sua sintaxe original do

CloudFormation. Você também pode usar funções intrínsecas e pseudoparâmetros em um modelo SAM, assim como faria em um modelo nativo do CloudFormation.

Referências:

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-specification.html https://aws.amazon.com/ blogs/mt/build-deploy-serverless-app -usando-aws-serverless-application-model-and-a ws-cloudformation/

Comandos SAM CLI comumente usados

1. sam init - gera modelos pré-configurados do AWS SAM. 2. pacote sam -

agrupa o código e as dependências do seu aplicativo em um arquivo .zip (pacote de implantação).

O arquivo .zip é então carregado no bucket do S3 especificado. Depois disso, ele retorna uma cópia do seu modelo AWS SAM, substituindo referências a artefatos locais pelo local do Amazon S3 onde os artefatos são carregados. Observe que o pacote sam é um comando legado. Talvez você não precise executar isso porque sua funcionalidade já está incorporada no comando sam deploy. No entanto, você ainda pode ter dúvidas sobre o pacote sam, por isso ainda é bom saber o que é e o que faz. 3. sam deploy - agrupa o código do seu aplicativo em um pacote de implantação e implanta-

o como um SAM aplicativo.

4. invocação local de sam - permite testar funções Lambda e aplicativos sem servidor baseados em SAM localmente em um ambiente de execução semelhante ao Lambda.

Referência:

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-reference. HTML

	87

<!-- image -->





Funções de etapas da AWS

Step Functions permite orquestrar os componentes de um aplicativo em um fluxo de trabalho sem servidor. Um fluxo de trabalho é uma série de etapas com a saída de uma etapa atuando como entrada para a próxima etapa. Um fluxo de trabalho define o processo pelo qual seu aplicativo atinge seu objetivo do início ao fim.

Em Step Functions, nos referimos ao fluxo de trabalho como máquinas de estado, e cada etapa em uma máquina de estado é chamada de estado.

Uma State Machine é escrita usando Amazon States Language ou ASL, que possui uma sintaxe semelhante a um documento JSON. Se você não quiser escrever em ASL, o Step Functions também fornece uma interface de arrastar e soltar que simplifica ainda mais a forma como você constrói sua máquina de estado. Step Functions escreverá a definição da máquina de estado para você.

Estados

Existem oito tipos de estado que você pode usar para construir uma máquina de estado:

- Estado da tarefa - representa uma única unidade de trabalho na sua máquina de estado. O código do aplicativo que precisa ser executado pela função Lambda é feito pelo estado Task. Um estado de tarefa pode incluir apenas uma única função Lambda, uma tarefa ECS, notificação SNS, ação DynamoDB, etc.

- Estado de escolha - adiciona uma lógica de ramificação ao seu fluxo de trabalho. Você pode pensar nisso como uma declaração if- then-else onde há mais de um resultado possível que pode ocorrer ao avaliar um parâmetro em relação a uma condição que você definiu.

- Estado paralelo - executa duas ramificações de execução ao mesmo tempo. Um caso de uso para isso é quando você deseja executar duas atividades independentes que executam processos diferentes para uma entrada do mesmo nó.

- Estado de espera - adiciona um atraso à sua máquina de estado antes que ela continue executando estados. Isto é semelhante a como funciona uma função Sleep em Python.

- Fail State - interrompe a execução da máquina de estado e marca-a como uma falha. Um exemplo em que você pode usar isso é quando você tem um processo de registro e deseja negar qualquer formulário inválido enviado por um usuário. Você pode marcar o registro como uma falha e receber uma mensagem de erro personalizada como ‘InvalidUsername’.

- Estado de sucesso - interrompe a execução com sucesso.

- Estado Pass - pode usar o estado Pass para passar a entrada do estado anterior para sua saída sem

realizando trabalho. Isso é útil quando você está depurando uma parte da sua máquina de estado e deseja ter visibilidade da saída de um estado específico.

	88







Referências:

https://docs.aws.amazon.com/step-functions/latest/dg/concepts-states.html https://

aws.amazon.com/blogs/aws/new-aws-step-functions-workflow -studio-a-low-code-visual-tool-for-buildi ng-state-machines/

Processamento de entrada e saída

Ao enviar uma solicitação de execução do Step Function, você fornece entrada na forma de JSON para o estado inicial do seu fluxo de trabalho. O estado consome os dados de entrada e encaminha qualquer saída para o próximo estado, que então se torna sua

entrada. Para aproveitar ao máximo a Step Function, deve-se dedicar algum tempo para entender como os dados fluem de um estado para outro. Além disso, conhecer as informações específicas que cada estado realmente precisa é fundamental para projetar um fluxo de trabalho bom e eficaz. Reconhecer quais dados cada estado exige é apenas metade da solução; controlá-lo é a outra metade.

Step Functions simplifica esta parte para nós.

Step Function possui um recurso opcional que permite manipular e filtrar dados à medida que eles entram e saem de um estado. É útil quando você tem uma grande quantidade de dados aninhados, mas deseja apenas uma parte deles para um estado específico trabalhar. Por exemplo, digamos que você tenha uma máquina de estado de processamento de imagem acionada por um evento S3.

Os seguintes dados JSON serão passados para o primeiro estado da sua máquina de estado. Tenha em mente que os seguintes dados foram truncados para maior clareza:

<!-- image -->

{

"version": "0", "id":

"3e4bfd68-4504-fee5-d557-fee0e690feac", "detail-type": "Chamada de API AWS via CloudTrail", "source": "aws.s3", "account ": "123456789012", "hora":

"2018-12-18T00:23:05Z", "região": "us-

east-1", "eventTime": "2018-12-18T00:23:05Z",

"eventSource":

"s3.amazonaws.com", "eventName": "PutObject", "awsRegion": "us-east-1", "sourceIPAddress": "0.0.0.0", "requestParameters":

{ "bucketName" : "media-tutorialsdojo", "key": "cat.jpg"

}

	89

<!-- image -->



}

Digamos que o primeiro estado seja uma função Lambda e precise conhecer o caminho S3 de cat.jpg. Sabendo disso, descartar todas as informações desnecessárias, exceto bucketName e chave, será seu objetivo inicial. “Mas podemos simplesmente analisar os dados do evento dentro da função Lambda?” você pode perguntar. O Step Functions foi projetado para facilitar a junção de várias partes do seu aplicativo. pretendo fazer isso com a menor sobrecarga possível. E uma das sobrecargas que pretendemos remover é a análise de dados.

Podemos usar os seguintes filtros para controlar os dados à medida que eles se movem por diferentes estados.

Filtros de entrada:

InputPath

- Seleciona uma parte da entrada do estado JSON.

	90

<!-- image -->



- Os estados de sucesso e falha não são suportados.

Exemplo:

Entrada original:

{

"mensagem": "olá mundo", "de": "carlo", "timestamp": 1639078426

}

Expressões JSONPath são usadas para extrair valores-chave de um texto JSON. Use o $. prefixo seguido pela chave nome.

Para obter o valor da chave da mensagem , usamos a expressão $.message :

"Olá Mundo"

Parâmetros

- permite construir uma nova carga JSON que é passada como entrada para um estado. • Somente os estados Map, Parallel e Pass são suportados.

Exemplo:

Entrada original:

{

"mensagem": "olá mundo", "de": "carlo", "timestamp": 1639078426

}

Criando uma nova entrada JSON usando parâmetros:

	91

<!-- image -->



{

"usuário.$": "$.from", "newMessage": "test123"

}

Os valores podem ser estáticos ou derivados da entrada JSON original. Ao fazer referência a pares de valores-chave de uma entrada JSON, use .$ no final da chave e no início do valor.

Resultado:

{

"usuário": "carlo", "newMessage": "test123"

}

Podemos usar os seguintes filtros para controlar a saída de um estado.

Filtros de saída:

Seletor de resultados

- usado para construir um novo objeto JSON com base no resultado de um estado. • Somente os estados Tarefa, Mapa e Paralelo são suportados.

Exemplo:

Resultado original:

{

"ExecutedVersion": "$LATEST", "Payload":

{ "statusCode": "200",

"body": "Olá!" },

"SdkHttpMetadata":

{ "HttpHeaders":

{ "Conexão": "keep-alive", "Content- Length": "43",

	92

<!-- image -->





"Tipo de conteúdo": "aplicativo/json",

"Data": "Qui, 16 de abril de 2022 17:58:15 GMT",

},

"HttpStatusCode": 200 },

"SdkResponseMetadata": {

"RequestId": "88fba57b-adbe-467f-abf4-daca36fc9028" },

"Código de Status": 200}

Aplicando o ResultSelector:

{

"newPayload":

{ "body.$": "$.Payload.body", "statusCode.$": "$.Payload.statusCode"

}

}

Resultado:

{

"newPayload": { "body":

"Olá!", "statusCode": "200"

}

}

Caminho do Resultado

- usado para incluir a entrada original na produção do estado.
- Somente os estados Task, Map, Parallel e Pass são suportados.

Exemplo:

Antes do filtro de saída:

	93

<!-- image -->





{

"newPayload": { "body":

"Olá!", "statusCode": "200"

}

}

Se ResultPath for deixado em branco ou $, o resultado se tornará a saída e a entrada do estado será ignorada; caso contrário, a entrada do estado será incluída no resultado.

Aplicando a expressão de caminho $.StateResult :

{

"message": "olá mundo", "from": "carlo", "timestamp": 1639078426, "StateResult": { "newPayload": { "body":

"Olá!", "statusCode": "200"

}

}

}

*O texto amarelo representa a entrada original.

OutputPath

- Filtra o resultado final antes de ser enviado para o próximo estado.
- Os estados de sucesso e falha não são suportados.

Exemplo:

Antes do filtro de saída:

	94

<!-- image -->





{

"message": "olá mundo", "from": "carlo", "timestamp": 1639078426, "StateResult": { "newPayload": { "body":

"Olá!", "statusCode": "200"

}

}

}

Aplicando a expressão $.StateResult.newPayload :

{

"body": "olá, mundo!", "statusCode": "200"

}

Referências:

https://docs.aws.amazon.com/step-functions/latest/dg/concepts-input-output-filtering.html https:// aws.amazon.com/blogs/compute/modeling-workflow-input-output -path-processing-with-data-flow-simulador /

	95

<!-- image -->





AWS ElasticBeanstalk

AWS Elastic Beanstalk é uma plataforma gerenciada que permite fazer upload do código do seu aplicativo na AWS e provisionar facilmente o ambiente de nuvem necessário. Você só precisa fazer upload do pacote do seu aplicativo escrito em Java, .NET, PHP, Node.js, Python, Ruby, Go ou Docker, e então o Elastic Beanstalk implantará os recursos necessários para executar seu aplicativo. Você pode executar um ambiente de servidor Web ou um ambiente de trabalho. Um ambiente de servidor Web executa um site estático, um aplicativo Web ou uma API Web que atende

solicitações HTTP, enquanto um ambiente de trabalho, por outro lado, executa um aplicativo de trabalho que processa cargas de trabalho de longa duração sob demanda. Este último também executa tarefas de acordo com uma programação definida por você e pode ser integrada à fila do Amazon SQS.

Políticas de implantação

- De uma vez

	96

<!-- image -->





- A versão mais recente é implementada em todas as instâncias do ambiente do Elastic Beanstalk no

mesmo tempo.

- Este é o método mais rápido de implantação, tornando-o ideal para ambientes de teste onde as liberações são feitas e revisadas o mais rápido possível.
- Durante a implantação, seu aplicativo fica indisponível por um período, dependendo de quanto tempo leva para implantar seu novo código com êxito. Portanto, essa implantação normalmente não é vista na produção.

- Rolando

	97

<!-- image -->





- A versão mais recente é implantada em lotes. • O

impacto da falha na implantação é menor em comparação com Tudo de uma vez, já que as reversões são aplicadas em lotes também.

- Ao contrário do All out once, esta política de implantação não tem nenhum tempo de inatividade, desde que a capacidade reduzida possa atender ao volume de tráfego durante a implantação.

- Rolando com um lote adicional

	98

<!-- image -->





- Uma variação do Rolling que resolve o problema de aplicativos executados com capacidade reduzida durante a implantação.

	99







- Quando uma nova versão é implantada, em vez de tirar uma instância de serviço, o Elastic Beanstalk inicia um lote temporário de instâncias com a versão atual. Dessa forma, o aplicativo sempre roda em plena capacidade. • A nova versão atende o tráfego

enquanto a implantação está em andamento; no entanto, alguns usuários podem continue a ver a versão antiga.

- Como o Elastic Beanstalk gira novas instâncias durante a implantação, certifique-se de que os limites do EC2 tenham capacidade suficiente para a implantação prosseguir. Por exemplo, digamos que você tenha uma cota de 20

instâncias por região e já esteja executando 19. Se o tamanho do lote for 2 instâncias, o Elastic Beanstalk não poderá criar essas instâncias extras porque excederia os limites do EC2 em sua conta.

- Imutável

- O Elastic Beanstalk cria um grupo secundário de Auto Scaling por trás da carga do ambiente

balanceador. A nova versão é testada primeiro em uma única instância dentro do novo grupo de escalonamento automático; se a instância passar nas verificações de integridade, o EB continuará a implantação em instâncias adicionais. BE

<!-- image -->

100







em seguida, transfere as novas instâncias para o grupo de escalonamento automático original. As instâncias antigas e o grupo temporário de escalonamento automático são encerrados após uma

implantação bem-sucedida. • Assim como o Rolling com um lote adicional, há um período em que tanto o novo quanto o antigo versões estão atendendo solicitações.

- O processo de reversão não causa tempo de inatividade, pois o grupo de escalonamento automático que hospeda a versão estável está isolado do grupo que executa a nova versão. Caso a implantação falhe, basta encerrar o grupo temporário de escalonamento automático. • O

aplicativo também funciona com capacidade total durante a implantação. •

Essa estratégia de implantação, no entanto, é cara e está sujeita a limites EC2 sob demanda, uma vez que a capacidade é duplicada por um breve período. É também o método de implantação mais lento.

- Divisão de tráfego

- Adequado para testes A/B ou canário. • O

Elastic Beanstalk instala a nova versão em um novo conjunto de instâncias e, em seguida, transfere uma porcentagem do tráfego especificada para as novas instâncias durante um determinado período de avaliação. Se o

<!-- image -->

101

<!-- image -->

 Associate por

e o

as instâncias passarem nas verificações de integridade até então, a implantação será bem-sucedida. O Elastic Beanstalk encaminhará o restante do tráfego para as novas instâncias e encerrará as instâncias antigas. Se as novas instâncias

não passarem nas verificações de integridade ou se você decidir cancelar a implantação, o Elastic Beanstalk simplesmente redirecionará o tráfego de volta para as instâncias antigas e encerrará as novas instâncias.

Referências:

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.rolling-version-deploy.html https:// docs.aws.amazon.com/whitepapers/latest/introduction-devops -aws/aeb-deployment-strategies.html

Implantação azul/verde O

Elastic Beanstalk, por padrão, executa uma atualização no local quando você implanta uma versão mais recente

do seu aplicativo. Isso pode causar um curto tempo de inatividade, pois seu aplicativo será interrompido enquanto o Elastic Beanstalk executa a atualização do aplicativo. As implantações Azul/Verde permitem implantar sem tempo de inatividade do aplicativo.

Em uma implantação Azul/Verde, você tem dois ambientes idênticos isolados um do outro. O ambiente “Azul” refere-se ao ambiente para o qual o tráfego atual do usuário é direcionado, enquanto o ambiente “Verde” é onde a versão mais recente do aplicativo é implantada. Depois que a nova versão for implantada e testada, você poderá transferir o tráfego do ambiente azul para o ambiente verde.

Para implementar uma implantação azul/verde para sua aplicação Elastic Beanstalk, você pode executar as seguintes etapas:

- Crie outro ambiente no qual você implementará a versão mais recente do seu aplicativo. Você pode clone seu ambiente atual para facilitar a criação.

- Quando o novo ambiente estiver pronto, implante uma nova versão do seu aplicativo. Faça seus testes no Terminal de URL do seu novo ambiente.

	102







- Após o teste, selecione seu ambiente de produção, clique em Ações > Trocar URLs do ambiente.

- Na página Trocar URLs de Ambiente, selecione o ambiente mais recente e clique em Trocar para aplicar o mudanças.

<!-- image -->

103







A maior vantagem de uma implantação azul/verde é que a mudança para uma nova versão do aplicativo não envolverá nenhum tempo de inatividade, já que você está apenas redirecionando o tráfego, ao contrário da implantação local. A segunda vantagem é que reverter para o ambiente anterior caso algo dê errado é muito mais fácil porque a comutação é feita no nível da rede

Referências:

https://docs.aws.amazon.com/whitepapers/latest/overview-deployment-options/bluegreen-deployments.html https:// docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.CNAMESwap .html

.ebextensions

A personalização de ambientes do Elastic Beanstalk pode ser feita de diversas maneiras. Você pode alterar

alguns parâmetros de configuração usando o Console AWS, a CLI do EB ou o AWS SDK. ebextensions é simplesmente outro método de customizar seu ambiente, desta vez através do uso de arquivos de configuração. Esses arquivos de configuração, que podem ser escritos em JSON ou YAML, devem ser colocados em uma pasta chamada .ebextensions. Embora os arquivos de configuração sejam escritos usando YAML ou JSON, sua extensão de arquivo deve ser sempre .config. Ao criar o

<!-- image -->

104



 Associate por

e o

.ebextensions, certifique-se sempre de colocá-la no nível raiz do pacote de origem do seu aplicativo. Não deve estar localizado em subpastas; caso contrário, o Elastic Beanstalk não os reconhecerá.

Além de personalizar ambientes EB, os arquivos de configuração também podem ser usados para personalizar os servidores web em suas instâncias EC2. Você pode, por exemplo, modificar a configuração do Nginx fornecida pelo Elastic Beanstalk sem precisar usar SSH em cada uma de suas instâncias. Você pode pensar em .ebextensions como Ansible para Elastic Beanstalk (embora ambos possam ser usados juntos) e pode ser sua principal ferramenta para gerenciamento de configuração de servidor.

Referências:

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions.html https://aws.amazon.com/ blogs/compute/introduzindo-a-nova-geração-de-aws-elastic -plataformas-beanstalk/

Política de ciclo de vida do

aplicativo Cada versão do aplicativo implantada no Elastic Beanstalk é rotulada de forma exclusiva. É fácil perder o controle do número de versões crescentes em seu aplicativo, especialmente se você estiver executando testes iterativos e lançando frequentemente alterações modestas no código. Com o tempo, o número de versões que você quase nunca usará aumentará e eventualmente atingirá a cota de versões do aplicativo.

A cota de versões do aplicativo é o número máximo de versões que podem ser implantadas em uma região da AWS.

Isso é definido como 1.000 por padrão e se aplica a todos os aplicativos; uma vez alcançado, você não poderá fazer upload de novas versões do aplicativo.

Existem duas opções para lidar com esse problema. Primeiro, você pode solicitar ao AWS Support um aumento de cota ou simplesmente excluir as versões que não precisa mais. A exclusão de versões antigas libera o número de versões disponíveis para uso por outros aplicativos. É aqui que a política de ciclo de vida do aplicativo se torna útil. Em vez de excluir manualmente versões que seu aplicativo provavelmente não usará mais, você pode definir uma política de ciclo de vida do aplicativo que faça isso para você.

<!-- image -->

105







A política de ciclo de vida do aplicativo especifica por quanto tempo as versões antigas devem ser retidas antes de serem excluídas permanentemente. Ele também instrui o Elastic Beanstalk a excluir versões se o número total de versões do aplicativo exceder um limite

especificado. Imagine que você tenha 10 aplicações do Elastic Beanstalk em uma região da AWS com a cota de versão padrão. Você pode considerar a criação de uma política de ciclo de vida que limite o número de versões por aplicativo a 99. Dessa forma, a versão total será sempre inferior a 1.000. O motivo pelo qual queremos manter o número total de versões menor que a cota de versão é que a política de ciclo de vida só entra em ação depois que o Elastic Beanstalk cria com êxito uma versão do aplicativo. Depois que a cota for atingida antes da implantação de uma nova versão, a

política de ciclo de vida não entrará em vigor e você deverá excluir algumas versões manualmente.

Existem duas regras de ciclo de vida que você pode escolher se ativar a política de ciclo de vida.

• Defina o limite de versões do aplicativo por contagem total - aqui você especifica o número máximo de versões que deseja alocar para um aplicativo. O Elastic Beanstalk criará uma nova versão e excluirá a antiga caso você não tenha atingido a cota naquela região.

• Defina o limite de versões do aplicativo por idade. Qualquer versão anterior ao valor colocado aqui será será excluído assim que você carregar uma nova versão.

Na opção Retenção, você pode escolher se deseja ou não manter o pacote de origem da versão da sua aplicação no Amazon S3. Se você optar por manter o pacote de origem no S3, o Elastic Beanstalk ainda excluirá a versão do aplicativo de seu registro, mas o código-fonte da versão permanecerá no Amazon S3. E se você optar por excluir o

<!-- image -->

106



 Associate por

e o

pacote de origem no S3, a versão do aplicativo no Elastic Beanstalk e o código-fonte no S3 serão excluídos.

Referência:

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/applications-lifecycle.html

Interface de linha de comando EB (CLI)

A CLI do EB é o conjunto de comandos do Elastic Beanstalk que você pode usar para gerenciar ambientes de aplicação a

partir de um terminal. Observe que a CLI do EB é diferente das APIs do Elastic Beanstalk acessíveis por meio do SDK da AWS. O EB

CLI simplifica o processo de implantação de alterações em seu ambiente EB. Por exemplo, se você deseja implantar uma mudança que você confirmou recentemente em seu repositório local, você pode usar o comando eb deploy e, nos bastidores, o EB CLI criará um arquivo ZIP dessa mudança e o implantará em suas instâncias .

Não há necessidade de empacotar seu código e carregá-lo manualmente no console do Elastic Beanstalk.

Além de um repositório local, você também pode usar o comando eb deploy para implantar alterações de um repositório do AWS CodeCommit. Você pode definir o repositório como CodeCommit usando o comando eb init. Ao usar o CodeCommit, sempre que você executar eb deploy, o EB CLI enviará novos commits para seu repositório CodeCommit e usará a revisão HEAD de sua ramificação para criar o arquivo que ele implanta nas instâncias do EC2 em seu ambiente. Como resultado, você pode implantar atualizações incrementais de código sem precisar carregar o projeto inteiro todas as vezes.

Referências:

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3.html https:// docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb3-cmd-commands.html

<!-- image -->

107







Serviço de fila simples da Amazon (SQS)

Fila padrão versus fila

FIFO O Amazon SQS oferece suporte a dois tipos de fila de mensagens: filas padrão e filas primeiro a entrar, primeiro a

sair (FIFO) . A fila Padrão entrega mensagens pelo menos uma vez. Embora isso garanta que nenhuma mensagem seja perdida, isso acarreta o custo de as mesmas mensagens serem entregues mais de uma vez, resultando em mensagens duplicadas na fila. A fila padrão oferece suporte à ordem de melhor esforço, o que significa que as mensagens recebidas na fila podem, às vezes, estar em uma sequência diferente daquela em que foram enviadas. A fila SQS FIFO, por outro lado, foi projetada para preservar a ordem das mensagens que chegam na fila. Além disso, as mensagens são entregues exatamente uma vez para ajudar a evitar duplicatas.

Em termos de rendimento, a fila Padrão supera a fila FIFO por uma grande margem. As filas padrão podem lidar com um número ilimitado de transações por segundo (TPS) por ação de API, enquanto as filas FIFO podem suportar apenas até 3.000 mensagens por ação de API.

Referências:

https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/standard-queues.html https:// docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/FIFO-queues.html

Conceitos

Tempo limite de visibilidade

O SQS não exclui mensagens automaticamente depois que elas são processadas por um aplicativo. Uma mensagem permanece em uma fila até que o período de retenção expire ou se o consumidor a excluir manualmente. Por esse motivo, se você tiver vários consumidores pesquisando uma fila, é provável que uma mensagem possa ser recuperada e processada mais de uma vez. Para atenuar esse problema, você pode ajustar o valor do tempo limite de visibilidade da sua fila. O tempo

limite de visibilidade é o período durante o qual o Amazon SQS impede que outros consumidores recebam e processem mensagens. Você pode modificar o tempo limite de visibilidade de suas mensagens na fila no SQS Console ou usar a API ChangeMessageVisibility. Não há garantia, entretanto, de que você nunca receberá a mesma mensagem duas vezes. Cabe a você descobrir o ponto ideal que funciona para sua aplicação.

Pesquisa curta vs. pesquisa longa

Polling é o método pelo qual o SQS recupera mensagens da fila e as envia ao consumidor solicitante. O SQS oferece suporte a dois métodos de pesquisa: pesquisa longa e pesquisa curta (padrão). Com a sondagem curta, a solicitação ReceiveMessage pesquisa apenas um subconjunto dos servidores SQS para localizar mensagens a serem incluídas na resposta. O SQS envia a resposta imediatamente, mesmo que a consulta não encontre mensagens. E como apenas uma sub-rede de servidores é pesquisada, uma solicitação pode não retornar todas as suas mensagens. A pesquisa curta é melhor para aplicativos urgentes ou aplicativos em lote que podem enviar outra consulta se tiverem recebido uma resposta vazia anteriormente. Para ativar a sondagem curta, defina o tempo de espera como 0.

<!-- image -->

108







Com sondagem longa, a solicitação ReceiveMessage pesquisa mensagens em todos os servidores SQS. O SQS retorna uma resposta após coletar pelo menos uma mensagem disponível, até o número máximo de mensagens especificado na solicitação, e só retornará uma resposta vazia se o tempo de espera da pesquisa expirar. O tempo máximo de espera de sondagem longa é de 20 segundos. A pesquisa longa ajuda a reduzir o custo de uso do SQS, eliminando o número de respostas vazias e falsas respostas vazias. Para ativar a sondagem longa, defina o tempo de espera para ser maior que 0.

Biblioteca de cliente estendida do Amazon SQS para Java

A carga útil máxima de uma mensagem suportada pelo SQS pode ter até 256 KB de tamanho e em qualquer formato. Você será cobrado por cada pedaço de carga útil de 64 KB como uma solicitação. Isso significa que quando você recupera uma mensagem de 256 KB, ela é tratada como quatro solicitações separadas. Em algumas situações, esse limite pode ser um gargalo. A maioria das soluções que vejo na Internet aproveita o poder do Amazon S3, no qual cargas maiores que 256 KB são armazenadas em um bucket S3 em vez de em uma fila

SQS. O link do objeto S3 é então enviado para a fila. Uma alternativa mais simples é utilizar a biblioteca de cliente estendida do Amazon SQS para Java. Esta biblioteca envolve as mesmas funções da solução que descrevi acima em APIs. A única desvantagem, claro, é o suporte limitado ao idioma. Se estiver usando uma linguagem diferente como NodeJs, você mesmo terá que codificar a solução.

Referências:

https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-short-and-long-pollin g.html https:// docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/ sqs-visibility-timeout.htm l https://docs.aws.amazon.com/ AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-s3-messages.html

<!-- image -->

109







Amazon Cognito

Grupo de usuários versus grupo de identidades

Os grupos de usuários do Amazon Cognito são usados para autenticar a identidade de um usuário usando nome de usuário/senhas. Você também pode autenticar usuários usando provedores de identidade externos, como Amazon, Facebook ou Google, ou uma

autenticação compatível com SAML, como Microsoft Active Directory. Observe que o Cognito User Pool é responsável apenas por obter os tokens JSON Web (JWT) fornecidos por esses provedores. Você pode ter uma lógica de validação em seu aplicativo que verifica o JWT em troca de acesso aos seus próprios recursos. O JWT também pode ser usado para trocar credenciais temporárias da AWS usando AWS STS ou Amazon Cognito Identity Pools.

Com os grupos de usuários do Cognito, você pode fornecer funcionalidade de inscrição e login para usuários de aplicativos móveis ou da web. Você não precisa criar ou manter nenhuma infraestrutura de servidor na qual os usuários serão autenticados.

Este diagrama mostra como a autenticação é tratada com grupos de usuários Cognito:

<!-- image -->



110







- Os usuários enviam solicitações de autenticação para grupos de usuários do Cognito.
- O grupo de usuários do Cognito verifica a identidade do usuário ou envia a solicitação para provedores de identidade, como Autenticação do Facebook, Google, Amazon ou SAML (com Microsoft AD).
- O token do grupo de usuários do Cognito é enviado de volta ao usuário.
- A pessoa pode então usar esse token para acessar suas APIs de back-end hospedadas em seus clusters EC2 ou no API Gateway e Lambda.

Características:

• Interface de usuário integrada para login/inscrição. Esta UI hospedada é personalizável; você pode alterar sua aparência, modificar o tamanho e a cor dos botões e campos de entrada e até mesmo fazer upload do logotipo da sua marca, se desejar.

<!-- image -->

111







• Autenticação multifator (MFA) • Verificação de credenciais comprometidas • Proteção contra controle de conta • Verificação de telefone e e-mail

• Aplicação de requisitos de senha fortes

Grupos de identidades do Amazon Cognito

Os grupos de identidades Cognito (identidades federadas) fornecem funcionalidades diferentes em comparação aos grupos de usuários. Pools de identidades são usados para autorização do usuário. Você pode criar identidades exclusivas para seus usuários e federá-las com seus provedores de identidade. Usando pools de identidades, os usuários podem obter credenciais temporárias da AWS para acessar outros serviços da AWS.

Os pools de identidades podem ser considerados o mecanismo real que autoriza o acesso aos recursos da AWS. Ao criar grupos de identidades, pense nisso como definir quem tem permissão para obter credenciais da AWS e usar essas credenciais para acessar os recursos da AWS.

Este diagrama mostra como a autorização é tratada com Cognito Identity Pools:

<!-- image -->

112







- O aplicativo da web ou aplicativo móvel envia seu token de autenticação para Cognito Identity Pools. O token pode vir de um provedor de identidade válido, como Cognito User Pools, Amazon ou Facebook.
- O Cognito Identity Pool troca o token de autenticação do usuário por credenciais temporárias da AWS para acessar recursos como S3 ou DynamoDB. As credenciais da AWS são enviadas de volta ao usuário.
- As credenciais temporárias da AWS serão usadas para acessar os recursos da AWS.

Você pode definir regras em Cognito Identity Pools para mapear usuários para diferentes funções do IAM para fornecer permissões detalhadas.

<!-- image -->

113







1. Aqui está um resumo da tabela que descreve o grupo de usuários e o grupo de identidades do Cognito:

Saiba mais sobre grupos de usuários	Conjuntos de identidades Cognito

Cuida das interações do IdP para você

Fornece credenciais da AWS para acessar recursos em nome dos usuários

Fornece perfis para gerenciar usuários

Fornece tokens padrão OpenID Connect e OAuth

Suporta regras para mapear usuários para diferentes

Funções do IAM

Livre

Preço por usuário ativo mensal

Referências:

https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html https:// aws.amazon.com/premiumsupport/knowledge-center/cognito-user-pools-identity -piscinas/

Concedendo acesso para identidades não autenticadas Se você

tiver um aplicativo que fornece ativos de mídia, como imagens ou vídeos do Amazon S3, convém ter algum controle sobre o que os usuários podem ou não fazer. Você pode, por exemplo, permitir que usuários registrados visualizem, carreguem e compartilhem imagens, enquanto usuários convidados só podem ver fotos postadas por pessoas com contas.

Obviamente, as permissões concedidas aos usuários convidados deveriam ser mais restritivas do que aquelas concedidas às identidades autenticadas.

Você pode ativar identidades não autenticadas na criação de um pool de identidades ou modificando a configuração de um pool de identidades existente. O Cognito Identity Pool com acesso não autenticado funciona fornecendo um identificador exclusivo e credenciais da AWS para seus usuários convidados. Você pode controlar suas permissões definindo a política associada à função de suas identidades não autenticadas. Para restringir os usuários convidados à visualização apenas de imagens, defina permissões somente leitura do S3 na política da função. Como resultado, os usuários convidados não poderão excluir, atualizar ou fazer upload de imagens para seu aplicativo.

Referências:

https://docs.aws.amazon.com/cognito/latest/developerguide/identity-pools.html https://docs.aws.amazon.com/ location/latest/developerguide/authenticating-using-cognito.html

<!-- image -->



114







AWS Amplificar

AWS Amplify é um dos muitos serviços de desenvolvimento da AWS que ajuda você a criar aplicativos móveis e web extensíveis e full-stack com mais rapidez. Ele permite que você inicie facilmente o desenvolvimento de seu aplicativo e dimensione automaticamente seus recursos com menos sobrecarga de gerenciamento.

Simplificando, o AWS Amplify é um conjunto de ferramentas e recursos desenvolvidos especificamente. Consiste em Amplify Studio, Bibliotecas Amplify, Amplify CLI e Amplify Hosting. Vamos abordar rapidamente seus diferentes módulos, um por um.

Amplificar Estúdio

Amplify Studio é um ambiente de desenvolvimento visual que simplifica o desenvolvimento de seus aplicativos web e móveis. Você pode construir facilmente sua IU de front-end com seu conjunto de componentes de IU prontos para uso, que podem ser conectados diretamente ao back-end de seu aplicativo. Como seus componentes de UI já estão pré-construídos, o número de seu código padrão será reduzido, permitindo que você tenha mais tempo para se concentrar na implementação da lógica de negócios do aplicativo.

Você pode definir seus modelos de dados, implementar autenticação de usuário e adicionar armazenamento de arquivos usando o Amplify Studio sem qualquer conhecimento de back-end. Além disso, você pode importar protótipos Figma criados por designers de aplicativos para o Amplify Studio para uma

colaboração mais integrada.

Amplificar Hospedagem

Amplify Hosting é um serviço de hospedagem e CI/CD totalmente gerenciado que permite hospedar aplicativos de página única (SPA) seguros, confiáveis e rápidos por meio da rede de entrega de conteúdo da AWS. Nos bastidores, ele implanta seus aplicativos na rede de entrega de conteúdo do

Amazon CloudFront, que vem com centenas de pontos de presença globalmente. Amplify Hosting também permite que você configure seu próprio domínio personalizado para seus aplicativos e adicione alarmes personalizados que enviam notificações se uma determinada métrica exceder um limite especificado por você.

• Principais recursos •

Suporta aplicativos (construídos com Next.js 12 ou posterior) que usam renderização do lado do servidor (SSR). • Possui

integração profunda com Cypress, que permite executar testes ponta a ponta (E2E). As configurações e comandos do Cypress devem ser incluídos nas configurações de compilação amplify.yml do seu aplicativo.

• Oferece suporte a repositórios externos como GitHub, Bitbucket e GitLab, facilitando a configuração de um pipeline de implantação contínua para seus aplicativos Web existentes. • Você pode visualizar alterações durante revisões

de código

<!-- image -->

115



 Associate por

e o

- Oferece proteção por senha para seu aplicativo da web para que ele não possa ser visualizado publicamente enquanto você desenvolve novos recursos.
- Fornece invalidações instantâneas de cache para garantir que todas as alterações de código sejam imediatamente visíveis para os usuários, sem limpar o cache manualmente. • Configure

reescritas e redirecionamentos para manter as classificações de SEO.

Bibliotecas AWS Amplify

As bibliotecas AWS Amplify são bibliotecas JavaScript de código aberto no Amplify Framework. Eles foram projetados especificamente para ajudá-lo a criar aplicativos móveis e web com tecnologia AWS. As bibliotecas Amplify JavaScript são suportadas em React, React Native, Angular, Ionic, Vue e em diferentes estruturas web e móveis.

Interface de linha de comando do Amplify

A interface de linha de comando do Amplify é um conjunto de ferramentas CLI que você pode usar para configurar e manter o back-end do seu aplicativo diretamente de sua área de trabalho local. A CLI do Amplify tem um fluxo de trabalho interativo e casos de uso intuitivos que você pode aproveitar, como autenticação, armazenamento e API. Ele permite que você teste seus recursos localmente e implante seu aplicativo em vários ambientes. Esta ferramenta fornece modelos de infraestrutura como código, que são carregados automaticamente no CloudFormation ou AWS SAM. Com a CLI do Amplify, você pode ter uma colaboração em equipe muito mais eficaz e fácil integração com o fluxo de trabalho

de CI/CD do Amplify.

Referências:

https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html https:// docs.amplify.aws/

AWS CodeCommit

O AWS CodeCommit é um serviço de controle de origem totalmente gerenciado que hospeda repositórios privados baseados em Git. CodeCommit funciona de forma semelhante a muitos repositórios de código por aí, como o GitHub. Portanto, se você já teve experiência no uso de algum desses serviços em seu projeto, agora você tem uma ideia do CodeCommit.

Principais recursos do CodeCommit:

- CodeCommit é nativamente seguro, pois usa apenas HTTPS ou SSH para autenticar transferências de arquivos.
- CodeCommit oferece repositórios ilimitados. Você pode armazenar qualquer tipo de arquivo de qualquer tamanho, incluindo aplicativos ativos como imagens e bibliotecas, junto com seu código.
- Nos bastidores, o CodeCommit usa Amazon S3 e DynamoDB para armazenar dados do repositório. seu armazenamento ilimitado, alta disponibilidade e durabilidade também são garantidos.
- As integrações com outros serviços AWS são muito mais fáceis e convenientes para você como desenvolvedor. Esse é especialmente o caso se a maioria das cargas de trabalho de desenvolvimento for realizada na AWS. Por exemplo, você pode usar o Elastic Beanstalk para implantar diretamente atualizações de código incrementais feitas em um CodeCommit

<!-- image -->

116

<!-- image -->

 Associate por

e o

repositório. Outro exemplo é quando você deseja monitorar eventos do repositório. Suponha que sua equipe queira ser alertada sempre que um novo branch for criado ou quando um commit for enviado para um branch. Você pode fazer isso criando um gatilho CodeCommit que aponta para um tópico do Amazon SNS.

Autenticação de acesso (HTTPS) no CodeCommit

Você pode autenticar no CodeCommit usando HTTPS de duas maneiras:

- Credenciais HTTPS Git - assim como as chaves de acesso programático, as credenciais GIT são chaves de longo prazo vinculadas a um usuário IAM. Este é o método mais simples de autenticação com CodeCommit via HTTPS. Basicamente, você só precisará fornecer as credenciais do GIT (nome de usuário e senha) na configuração inicial para executar os comandos do GIT com êxito.

- HTTPS Git Remote CodeCommit (GRC) - você pode usar credenciais de usuário do IAM ou credenciais temporárias obtidas assumindo funções do IAM para autenticar no CodeCommit. Você não precisa mais gerar uma credencial Git se quiser usar o GRC. Você será autenticado por meio das credenciais associadas à sua função/usuário IAM do IAM, por exemplo.

Referências:

https://aws.amazon.com/codecommit/features/ https:// docs.aws.amazon.com/codecommit/latest/userguide/setting-up.html

	117







AWS CodeBuild

O AWS Codebuild permite compilar, criar, executar testes e produzir um artefato do seu código. Isso pode ser integrado ao seu processo Cl/CD existente. Por exemplo, você está usando o AWS CodeCommit como controle de versão para seu repositório de código-

fonte. Depois que um desenvolvedor envia o novo código para a ramificação de Desenvolvimento, você pode ter um gatilho automático para o CodeBuild executar a construção do seu projeto, testar seu aplicativo e, em seguida, fazer upload do artefato de saída para o S3. O arquivo de artefato no S3 pode então ser usado por ferramentas de implantação, como AWS CodeDeploy, para implantá-lo em instâncias EC2, ECS ou funções Lambda.

Arquivo de especificação de construção

O arquivo de especificação de compilação é um arquivo YAML que define os comandos que o CodeBuild executará em cada etapa de compilação. O arquivo buildspec.yml pode ser definido quando você cria um projeto de build no Console AWS ou também pode ser incluído como parte do seu código-fonte. Se você estiver incluindo o arquivo buildspec como parte do seu código-fonte, ele deverá ser nomeado buildspec.yml (tudo em letras minúsculas) e deve ser colocado no nível raiz da pasta do seu projeto.

Referência:

https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html

Integrações com outros serviços AWS

Amazon Elastic Container Registry (ECR)

Amazon ECR é um serviço de registro Docker gerenciado na AWS. Se você já usou o Docker Hub antes, terá uma ideia do que é ECR. No Docker, para acessar imagens armazenadas em um registro privado, precisamos primeiro fazer login usando o docker login. Mas e no Amazon ECR? O Amazon ECR possui seu próprio método de autenticação. Como é um serviço que gerencia um registro de contêiner nos bastidores, você precisa primeiro ser autenticado no nível do ECR.

Isso significa que você não pode usar o comando docker login para fazer login diretamente em seu repositório ECR privado. Você pode pensar nisso como um acesso de dois níveis.

Primeiro, você precisa emitir o comando aws ecr get-login-password. Isso retorna um token de autenticação que você pode usar para autenticar em um registro do Amazon ECR. Você pode então passar o token de autenticação no sinalizador --password do comando docker login. Para melhor segurança, você pode opcionalmente passar a senha por meio do sinalizador --password-stdin para fornecer o token por meio do fluxo de entrada padrão. Isso evita que o token acabe no histórico ou nos arquivos de log do shell.

<!-- image -->

118



 Associate por

e o

aws ecr get-login-password \ --region

<região> \docker login \ -- username AWS\

--password-stdin <aws\_account\_id>.dkr.ecr.<região>.amazonaws.com

Digamos que você queira automatizar a construção da imagem de um arquivo docker, você pode pegar o comando acima e escrevê- lo na fase de pré-construção do seu arquivo buildspec e escrever um comando docker push na fase de pós-construção.

Amazon EventBridge (anteriormente conhecido como CloudWatch Events)

Amazon EventBridge é um serviço usado para criar aplicativos orientados a eventos na AWS. O EventBridge pode capturar eventos produzidos pelo seu ambiente de construção. Com EventBridge ou CloudWatch Events, você pode criar uma regra de evento que monitora o status de sua compilação — veja se ela está em andamento, bem-sucedida, com falha ou interrompida. Você pode então conectar um tópico SNS a esse evento para ser alertado se algo ruim acontecer durante a construção.

Armazenamento de parâmetros do AWS Systems Manager

O AWS Systems Manager Parameter Store fornece armazenamento seguro e hierárquico para gerenciamento de dados

de configuração e gerenciamento de segredos. Em termos simples, é um serviço que você pode usar para armazenar dados como senhas, credenciais de banco de dados, variáveis de ambiente e qualquer texto simples ou dados criptografados.

Então, por que você usaria esse serviço com o CodeBuild quando pode armazenar variáveis em seu ambiente de compilação? O motivo é que o CodeBuild tem um limite para o comprimento de todas as variáveis de ambiente que você pode usar. A compilação encontrará um erro se suas variáveis de ambiente (nomes e valores de chaves) atingirem um máximo combinado de cerca de 5.500 caracteres.

Uma solução recomendada pela AWS é armazenar variáveis de ambiente de grande porte no Amazon Systems Manager Parameter Store. Você pode então executar a API GetParameters em seu arquivo buildspec para recuperar essas variáveis na fase de pré-construção.

Referências:

https://docs.aws.amazon.com/codebuild/latest/userguide/troubleshooting.html#troubleshooting-large-env-va rs

https://docs.aws.amazon.com/codebuild/latest/userguide/sample-ecr.html

<!-- image -->

119







AWS CodeDeploy

Configurações de implantação

A configuração de implantação é um conjunto de regras e condições que você pode ajustar para instruir o CodeDeploy sobre quão agressiva ou conservadora será sua abordagem de implantação. Ao implantar uma nova versão do aplicativo na plataforma de

computação de destino (EC2, ECS ou Lambda), você pode ter várias opções para transferir o tráfego de rede para a versão mais recente.

Usando o CodeDeploy, você pode controlar quantas instâncias serão atualizadas a qualquer momento durante a implantação.

Isto é importante porque, durante as implantações, o aplicativo é interrompido enquanto a nova versão é implantada. Você deseja ter certeza de que há instâncias suficientes online para atender o tráfego, bem como a capacidade de reverter as alterações quando ocorrer um erro durante a implantação.

No Console AWS, ao clicar em CodeDeploy > Configurações de implantação, você verá a lista de estratégias de implantação definidas pela AWS que podem ser usadas para suas implantações. Você pode criar sua própria configuração de implantação se desejar, mas discutiremos aqui as mais comuns, que você provavelmente encontrará no exame.

<!-- image -->

120



 Associate por

e o

CodeDeployDefault.AllAtOnce – esta é a implantação mais rápida. O aplicativo será interrompido em todas as instâncias do EC2 e o CodeDeploy instalará a versão mais recente em todas as instâncias. O aplicativo deixará de servir o tráfego durante a implantação, pois todas as instâncias estarão offline.

CodeDeployDefault.OneAtATime – esta é a implantação mais lenta. O CodeDeploy interromperá apenas uma instância por vez. A implantação em todas as instâncias levará algum tempo, mas o aplicativo permanecerá on-line, pois apenas uma instância estará off-line por vez.

CodeDeployDefault.HalfAtATime – metade ou 50% das instâncias estarão offline durante a implantação, enquanto a outra metade estará online para atender o tráfego. Este é um bom equilíbrio entre uma implantação rápida e segura.

CodeDeployDefault.LambdaLinear10PercentEvery10Minutes – Implantação para funções Lambda. Esta implantação usará aliases no back-end para transferir o tráfego da versão antiga para a versão mais recente. Dez por cento do tráfego será transferido para a

versão mais recente a cada 10 minutos. A implantação será executada em intervalos de 10 minutos até que 100% do tráfego seja transferido para a versão mais recente.

CodeDeployDefault.LambdaCanary10Percent10Minutes – Implantação para funções Lambda. Esta implantação usará

aliases no back-end para transferir o tráfego da versão antiga para a versão mais recente. Inicialmente, 10% do tráfego será transferido para a versão mais recente. Isso durará apenas 10 minutos para que você tenha tempo de verificar os logs do aplicativo. Após 10 minutos, os 90% restantes do tráfego serão transferidos para a versão mais recente.

Referência:

https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html

Arquivo AppSpec

CodeDeploy gerencia cada estágio de implantação como uma coleção de ganchos de eventos de ciclo de vida por meio de um arquivo AppSpec. O arquivo AppSpec permite instruir o CodeDeploy sobre as tarefas de implantação que serão executadas durante todo o processo de implantação do seu aplicativo. Por exemplo, você pode instruir o CodeDeploy a instalar as dependências exigidas pelo seu aplicativo antes de instalar a nova versão do aplicativo ou pode instruir o CodeDeploy a alterar algumas permissões de arquivo antes de iniciar a implantação.

• O arquivo AppSpec pode ser gravado em YAML ou JSON.

• YAML é o único formato disponível para configurar AppSpec no EC2/On-premise.

• Você precisa instalar o CodeDeploy Agent para configurar o AppSpec no EC2/no local.

• O arquivo AppSpec deve estar incluído na pasta raiz do aplicativo.

Referência:

<!-- image -->

121







https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file.html

Ganchos de eventos de ciclo de vida

Você pode inserir scripts ou comandos personalizados em cada gancho de evento para controlar o processo de sua implantação. Os comandos são executados em sequência com base na ordem dos ganchos de eventos. Observe que cada plataforma de computador (Amazon ECS AWS Lambda, Amazon EC2, On-premises) possui diferentes eventos de gancho. Nesta seção, abordaremos os ganchos de eventos disponíveis em uma implantação EC2/no local.

- Início – O primeiro evento do ciclo de vida é o evento Início e inicia a instância para implantação. O CodeDeploy Agent executa isso automaticamente para você, o que significa que você não precisa incluir esse gancho de evento em seu arquivo AppSpec.
- ApplicationStop - usado para executar quaisquer scripts que irão preparar sua instância para receber o novo

versão do aplicativo. Por exemplo, se você estiver implantando uma nova versão do aplicativo, digamos v.2, poderá incluir um script que desabilitará a versão anterior v.1 neste gancho de evento.

- DownloadBundle - este evento é acionado automaticamente após o evento ApplicationStop. Você não precisa incluir isso em seu arquivo AppSpec. Durante este estágio, o CodeDeploy extrairá a nova versão v.2 de um repositório de origem para a instância, como o nome indica.

<!-- image -->

122







- BeforeInstall - este gancho de evento pode ser útil se você deseja fazer backup dos arquivos de configuração do seu aplicativo antigo ou de quaisquer logs antigos e armazená-los em outro lugar do disco, para que não sejam sobrescritos quando o novo aplicativo for copiado.
- Instalar - este evento é executado automaticamente. Durante o evento de instalação, o CodeDeploy copia seu novo arquivos do aplicativo para o destino do arquivo que você especificou.
- AfterInstall - este evento pode ser usado para decodificar informações de string de banco de dados, credenciais de aplicativos e talvez outros dados criptografados que você enviou como parte de seu pacote de aplicativos e mover tudo para seu destino adequado.
- ApplicationStart - use este evento para permitir que seu aplicativo volte a funcionar.
- ValidateService - este evento pode ser usado para executar qualquer script de validação para ver se a aplicação está

funcionando como pretendido.

- End - Assim como o gancho do evento Start, este é executado automaticamente; não há necessidade de incluir esse gancho de evento em seu arquivo AppSpec. O evento End notificaria o serviço central se a implantação foi bem-sucedida ou não.

Se algo der errado durante a implantação, você poderá escolher quais medidas tomar em seguida, como reverter para uma versão funcional conhecida do seu aplicativo.

Referências:

https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html#app spec-hooks-server https:// docs.aws.amazon.com/

codedeploy/latest/userguide/reference-appspec-file-example.html https://docs.aws.amazon.com/codedeploy/latest/ userguide/application-specification-files.html#appspec-files -on-ecs-compute -plataforma

Grupos de implantação

A coleção de instâncias ou funções do Lambda nas quais você deseja implantar uma revisão de aplicativo é chamada de grupo de implantação. Seu grupo de implantação compreende informações como função de serviço, que concede permissão ao CodeDeploy para acessar os recursos necessários da AWS para realizar seu trabalho.

<!-- image -->

123

<!-- image -->

 Associate por

e o

Você pode usar grupos de implantação para criar vários estágios em seu pipeline antes de implantar na produção. Por exemplo, para

garantir a qualidade do código, primeiro você pode implantar uma atualização de código em um conjunto de instâncias em um ambiente de teste. Depois disso, você pode implantá-lo em um ambiente de teste para teste. Por fim, se estiver satisfeito com o resultado da sua implantação,

você poderá mover o código para o seu ambiente de produção.

Referência:

https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-groups.html

AWS Code Pipeline

Ações de aprovação manual

Nem todas as organizações favorecem a ideia de um processo de implantação totalmente automatizado – implantação de códigos desde o controle de versão até a produção, sem intervenção humana. Na maioria das vezes, você designa alguém para assumir, testar e tomar a decisão final sobre enviar ou não as alterações de código para produção. É disso que se trata a entrega contínua . A principal diferença entre entrega contínua (AWS CodePipeline) e implantação contínua (AWS CodeDeploy) é a presença de aprovação manual.

CodeDeploy pega seu código de um repositório e o implanta em seus servidores sem intervenção humana. No AWS CodePipeline, você pode inserir um estágio de ação de aprovação manual antes de prosseguir para o estágio final de implantação. No estágio de aprovação manual, o CodePipeline pausará a implantação para que alguém em quem você confia possa revisar as alterações. Se o aplicativo não estiver se comportando da maneira esperada antes da alteração, o

	124







usuário autorizado pode rejeitar a implantação. Se isso acontecer, o CodePipeline interromperá a implantação. Por outro lado, se o usuário aprovar a alteração, o CodePipeline retoma a implantação na produção.

Referências:

https://docs.aws.amazon.com/codepipeline/latest/userguide/approvals-action-add.html https://aws.amazon.com/ blogs/devops/complete-ci-cd-with-aws -codecommit-aws-codebuild-aws-codedeploy -and-aws-codepipeline/

<!-- image -->

125



 Associate por

e o

AWS CodeArtifact

Os pacotes de software desempenham um papel importante no desenvolvimento, pois geralmente fornecem soluções prontas para uso para resolver problemas comuns ao trabalhar em projetos. Às vezes, também pode ser necessário construir uma biblioteca personalizada além das existentes para atender a casos de uso específicos. Isso não é grande coisa quando você está trabalhando sozinho em um projeto, porém, ao trabalhar em um ambiente colaborativo, alguns fatores devem ser considerados. Por exemplo, manter a

consistência em todo o seu processo de CI/CD; você não quer que sua equipe instale versões diferentes do mesmo pacote, pois isso pode causar problemas de incompatibilidade no futuro. Além disso, um desenvolvedor pode extrair bibliotecas de código aberto

da Internet. Sem a verificação adequada, você pode acabar com um aplicativo cheio de vulnerabilidades; portanto, é fundamental permitir apenas o uso de bibliotecas que foram revisadas e aprovadas pelos líderes da equipe.

AWS CodeArtifact ajuda a resolver esse problema. É um serviço de repositório de artefatos totalmente gerenciado que permite às equipes armazenar e compartilhar com segurança pacotes de software usados no desenvolvimento de aplicativos. Como o CodeArtifact

não tem servidor, você economiza no custo e no esforço de configuração de soluções de repositório tradicionais. O gerenciamento de pacotes usando o AWS CodeArtifact permite que as equipes trabalhem de forma independente e, ao mesmo tempo, garante que

cada membro use pacotes e versões aprovados semelhantes. Isso ajuda a evitar problemas de dependência, melhora a reutilização de código, reduz o tempo de entrega e impõe governança rigorosa e visibilidade de segurança sobre os artefatos.

CodeArtifact usa AWS KMS para proteger arquivos e AWS IAM para controlar o nível de acesso que diferentes usuários podem ter. Você

pode enviar e buscar artefatos de um repositório usando gerenciadores de pacotes populares, como NuGet, Maven, Gradle, npm, yarn, pip e twine.

Referências:

https://docs.aws.amazon.com/codeartifact/latest/ug/getting-started.html https:// aws.amazon.com/blogs/aws/software-package-management-with-aws-codeartifact /

<!-- image -->



126







AWS CodeStar

O AWS CodeStar ajuda você a configurar rapidamente os recursos do conjunto de ferramentas exigidos pela sua aplicação usando a AWS e outros serviços externos. O objetivo é simplificar ainda mais os processos DevOps, reunindo todas as ferramentas do conjunto de códigos, como CodeCommit, CodeBuild, CodeDeploy e CodePipeline, em um único painel. Outros serviços, como Amazon CloudWatch para monitoramento de aplicativos, AWS Cloud9 para edição de código e rastreamento opcional de problemas por meio do Jira também são incorporados. Isso dá aos usuários a capacidade de operar em um projeto, acompanhar atividades e visualizar o progresso em todas as fases de um processo de desenvolvimento a partir de um local centralizado, sem alternar entre guias.

Para começar com o CodeStar, você cria um projeto. Um projeto é simplesmente uma coleção de código-fonte e recursos da AWS necessários para implantar seu aplicativo. CodeStar lança projetos usando um modelo CloudFormation de sua escolha. Se estiver criando um projeto por meio do Console, você pode selecionar entre modelos predefinidos que variam de acordo com o tipo de aplicativo (por exemplo, aplicativo web, habilidade Alexa, serviço web), o host no qual o aplicativo é implantado (EC2, ElasticBeanstalk,

Lambda função) e linguagem de programação. CodeStar oferece suporte a tempos de execução como Node.Js, Python, Go, Ruby, Java, ASP.Net e PHP. Se de alguma forma os modelos pré-construídos não forem suficientes e você precisar de mais personalizações, tente criar projetos usando AWS CLI. Essa abordagem, no entanto, é avançada e requer experiência decente na escrita de modelos CloudFormation e na configuração de pipelines na AWS.

Você pode adicionar usuários do IAM como membros da equipe e conceder-lhes acesso com base nas funções que lhes foram atribuídas no projeto.

Referências:

https://docs.aws.amazon.com/codestar/latest/userguide/welcome.html https://aws.amazon.com/ blogs/devops/integrating-aws-device-farm-with-ci-cd -pipeline-to-run-cross-browser-s elenium-tests/

<!-- image -->



127

<!-- image -->





Amazon Code Guru

O Amazon CodeGuru é um serviço que pode analisar códigos Python e Java usando raciocínio automatizado e aprendizado de máquina para fornecer correções, recomendações para melhorar a qualidade do código e detecção de vulnerabilidades.

O Amazon CodeGuru tem dois componentes:

• Revisor do Amazon CodeGuru

• Detecta possíveis problemas no código, como erros de digitação, chamadas de API ausentes, registros inconsistentes, exceções ausentes e assim por diante, bem como falhas de segurança, como senhas codificadas e cadeias de conexão de banco de dados.

• Você pode integrar o CodeGuru em pipelines existentes para avaliar automaticamente alterações incrementais de código quando uma solicitação push ou pull é emitida.

• CodeGuru oferece suporte a repositórios CodeCommit, GitHub e BitBucket. • CodeGuru gera recomendações com base em cenários comuns. Tome nota que haverá

haverá momentos em que você não concordará com uma sugestão porque ela não é aplicável à sua situação. Se isso ocorrer, você poderá fornecer feedback ao CodeGuru Reviewer. A AWS usa o feedback do usuário para melhorar o CodeGuru e fornecer relatórios mais precisos.

• Perfilador do Amazon CodeGuru

• Coleta dados de desempenho do seu aplicativo e mostra uma visualização de como seu código está executando.

• CodeGuru Profiler sugere maneiras de melhorar seu código para resolver problemas como gargalos de CPU e processos de alta latência. • Suporta ambientes hospedados

em EC2, EKS, ECS, Fargate, Lambda ou no local.

Referências:

https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/welcome.html https://

aws.amazon.com/blogs/devops/detect-python-and-java-code-security -vulnerabilidades-com-codeguru-rev iewer/ https://aws.amazon.com/ blogs/

machine-learning/optimizing-application-performance-with-amazon-codeguru-profiler/

	128







Serviço de gerenciamento de chaves da AWS (KMS)

Chave AWS KMS

A chave KMS é o recurso mais básico do AWS KMS. Uma chave KMS inclui metadados, como ID da chave, data de criação, descrição e estado da chave. A chave KMS também contém o material de chave usado para criptografar e descriptografar dados. AWS KMS tem dois tipos de chaves:

- Simétrica - uma chave de 256 bits usada para criptografia e descriptografia.
- Assimétrico - um par de chaves RSA usado para criptografia e descriptografia ou assinatura e verificação (mas não ambos) ou um par de chaves de curva elíptica (ECC) usado para assinatura e verificação.

Três tipos de chave KMS:

- Gerenciado pelo cliente – você tem controle total sobre essas chaves KMS. Você é responsável pelo gerenciamento de chaves, que inclui configuração de políticas de chaves, rotação de materiais de chaves e gerenciamento do ciclo de vida de chaves.

- Gerenciados pela AWS : são chaves KMS em sua conta que são criadas, gerenciadas e usadas em sua conta.

nome por um serviço da AWS. Você não pode gerenciar, alternar e alterar as políticas de chaves gerenciadas pela AWS. Você também não pode usá-los diretamente em operações criptográficas; o serviço que os cria os utiliza em seu nome.

- De propriedade da AWS : são chaves KMS que um serviço da AWS cria, possui e gerencia para uso em vários Contas AWS. Você não pode visualizar, usar, rastrear ou auditar essas chaves KMS.

<!-- image -->

Tipo de chave KMS              Pode visualizar metadados

Pode gerenciar KMS Chave

Usado apenas para

o sua Conta AWS

Rotação automática

Gerenciado pelo cliente

Sim

Sim

Sim

Opcional.

A cada 365 dias

Gerenciado pela AWS

Sim

Não

Sim

Obrigatório. A cada 365 dias

De propriedade da AWS

Não

Não

Não

Varia



129



 Associate por

e o

O KMS gera material de chave para todas as chaves KMS criadas por padrão. Os materiais-chave padrão não podem ser extraídos, exportados,

visualizados ou gerenciados. Um material chave por si só não pode ser excluído; se quiser se livrar dele, você deve excluir a chave KMS à qual está associada. Você também pode importar seu próprio material de chave para uma chave KMS gerenciada pelo cliente. Também é possível armazenar chaves

KMS no AWS CloudHSM. Considere esta opção se você precisar proteger chaves em um HSM de locatário único que seja validado pelo FIPS 140-2 nível 3.

Referências:

https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#master\_keys https://tutorialsdojo.com/ aws-key-management-service-aws-kms/

Criptografia de envelope

Uma chave KMS é capaz de criptografar dados de até 4 KB, o que a torna inadequada para criptografia de dados grandes. Para criptografar dados com mais de 4 KB, como provavelmente acontecerá, você precisará usar um processo chamado criptografia de envelope.

A criptografia de envelope não é específica do KMS. Mas quando falamos sobre criptografia de envelope no contexto do KMS, refere-se ao processo de geração de uma chave de dados usando uma chave KMS. Em seguida, você usa essa chave de dados fora do KMS para criptografar um arquivo ou outra chave de dados; a profundidade da criptografia depende de você. Múltiplas camadas de segurança podem ser alcançadas gerando uma chave de dados secundária sob a chave de dados de nível superior e, em seguida, criptografando essa chave sob outra chave e assim por diante. O problema é que sempre deve

haver uma chave mestra que permaneça em texto simples para que você possa eventualmente descriptografar todas as chaves de dados. No KMS, a chave mestra é chamada de chave KMS.

Como prática recomendada de segurança, sempre certifique-se de que a chave de dados em texto simples seja excluída da memória após o uso.

Referências:

https://docs.aws.amazon.com/wellarchitected/latest/financial-services-industry-lens/use-envelope-encryption -with-customer-master-keys.html https://aws.amazon.com / blogs/segurança/importância-da-criptografia-e-

como-aws-pode-ajudar/

API KMS

Aqui está a lista dos comandos da API KMS mais comumente usados que você provavelmente encontrará no exame:

- Criptografar
    - converte dados de texto simples em texto cifrado usando uma chave KMS. • Lembre-

se de que a operação Criptografar só pode criptografar dados com menos de 4 KB: útil para gerar chaves de dados e criptografar pequenos dados, como IDs de usuários, senhas ou credenciais de banco de dados.

- Descriptografar
    - converte dados de texto cifrado de volta ao formato de texto simples usando uma chave KMS. • só pode ser usado em dados que foram criptografados com uma chave KMS.

<!-- image -->

130



 Associate por

e o

- Gerar DataKey
    - cria uma chave de dados usando uma chave KMS e retorna duas versões dela: um texto simples e um texto cifrado

chave de dados.

- a chave de dados de texto simples é usada para criptografar arquivos. •

você não pode usar a API Encrypt para criptografar dados usando a chave de dados de texto simples. Normalmente, você usará a chave de dados de texto simples para realizar operações criptográficas com a ajuda de uma biblioteca do lado do cliente como OpenSSL.

- GerarDataKeySemPlaintext
    - cria uma chave de dados usando uma chave KMS e retorna apenas a versão criptografada dela. • para criptografar/descriptografar arquivos, converta primeiro a chave de dados do texto cifrado em texto simples usando o Decrypt

API.

Referências: https://docs.aws.amazon.com/cli/latest/reference/kms/index.html https:// docs.aws.amazon.com/kms/latest/developerguide/programming-top.html

<!-- image -->

131







Amazon Cloud Front

O Amazon CloudFront possui três componentes básicos: a origem, a distribuição e o visualizador. A origem refere-se à origem do conteúdo, onde ele é gerado ou armazenado. A distribuição é um recurso do CloudFront que controla como o conteúdo é entregue aos usuários, incluindo armazenamento em cache e controles de acesso. O visualizador é o usuário final ou aplicativo que acessa e consome seu conteúdo.

O CloudFront oferece suporte à seguinte origem:

• Bucket Amazon S3 •

Elastic Load Balancer • Serviço AWS Elemental • Servidor HTTP

em execução em uma instância do Amazon EC2 • Servidor local

Política de protocolo do visualizador versus política de protocolo de origem

No Amazon CloudFront, você pode configurar como o CloudFront se comunica com o visualizador e o servidor de origem, respectivamente, por meio da política de protocolo do visualizador e da política de protocolo de origem.

Política de protocolo do visualizador

• Descreve o protocolo e a política de conexão entre o cliente (visualizador) e o CloudFront. • Suporta • HTTP e HTTPS •

Redireciona HTTP para

HTTPS • Somente HTTPS.

<!-- image -->



132



 Associate por

e o

Política do Protocolo de Origem

• descreve a política de protocolo de conexão entre o CloudFront e o servidor Origin. • Suporta • Somente HTTP • Somente HTTPS • Visualizador

de correspondências

• Selecionar Match viewer solicitará que o CloudFront use o mesmo protocolo que o visualizador. Isso pode ser útil quando você tem uma combinação de conteúdo HTTP e HTTPS e deseja evitar incompatibilidades de protocolo que possam afetar a entrega do seu conteúdo. • A Política de Protocolo de Origem não se aplica a endpoints de sites S3. Isso ocorre

porque os endpoints do site S3 suportam apenas conexões HTTP. Para impor a comunicação HTTPS entre o CloudFront e o S3, você deve alterar a configuração da política de protocolo do visualizador para "HTTP e HTTPS" ou "Redirecionar HTTP para HTTPS".

Nome de domínio personalizado

O CloudFront usa seu próprio certificado SSL para fornecer um nome de domínio HTTPS padrão do CloudFront no formato <cloudfront-distribution-

id.cloudfront.net> . Se desejar usar um nome de domínio personalizado, você deverá usar seu próprio certificado SSL. Certifique-se de que o domínio listado no certificado corresponda ao nome de domínio alternativo que você deseja usar. Você pode solicitar um ao ACM na região da Virgínia do Norte ou usar um

certificado importado armazenado no IAM.

Referência:

https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/using-https-cloudfront-to-custom-or igin.html

Gatilhos de eventos do CloudFront

Os gatilhos de eventos do CloudFront podem ser usados para executar determinadas ações para personalizar o comportamento da sua distribuição do CloudFront e criar experiências mais personalizadas para seus visualizadores.

<!-- image -->

133







Existem quatro eventos acionadores no CloudFront:

- Evento de solicitação do visualizador - ocorre quando o CloudFront recebe uma solicitação de um usuário final. Você pode usar isso evento para executar ações personalizadas, como autenticação de usuário.

Use quando:

- Modificar uma chave de cache, como cabeçalhos HTTP, cookies e parâmetros de string de consulta. • Geração de respostas personalizadas que não serão armazenadas em cache.

- Evento de solicitação de origem - ocorre quando há uma falta de cache e o CloudFront precisa recuperar o

conteúdo solicitado do servidor de origem. Você pode realizar ações como modificar os cabeçalhos da solicitação ou solicitar uma versão específica do conteúdo.

Use quando:

- Execução de ações em caso de falta de cache. •

Selecionar dinamicamente a origem da qual o CloudFront recuperará o conteúdo solicitado. • Reescrever o URL para a origem. • Gerar respostas personalizadas que

você pretende armazenar em cache.

- Evento de resposta de origem - ocorre depois que o CloudFront recebe uma resposta do servidor de origem, mas antes de armazená-la em cache no ponto de presença. Durante esse evento, você pode configurar o CloudFront para acionar determinadas ações, como

modificar os cabeçalhos de resposta ou o corpo da resposta antes que ela seja armazenada no ponto de presença.

Use quando:

- Modificar a resposta antes que o CloudFront a armazene em cache

<!-- image -->



134







- Evento de resposta do visualizador - ocorre antes do CloudFront retornar o conteúdo solicitado ao usuário. Você pode usar esse evento para acionar ações, como registrar a resposta ou modificar os cabeçalhos da resposta antes de entregá-la ao usuário.

Use quando:

- Modificar a resposta sem armazenar o resultado em cache

Referências:

https://docs.amazonaws.cn/en\_us/AmazonCloudFront/latest/DeveloperGuide/lambda-cloudfront-trigger-events .html https://docs.aws.amazon.com/

AmazonCloudFront/latest/DeveloperGuide/lambda-how -to-choose-event.html

Funções Lambda@Edge vs CloudFront

Lambda@Edge

O Lambda@Edge permite executar funções do Lambda mais perto dos usuários finais, é a resposta a todos os eventos de gatilho do CloudFront. Ao usar o Lambda@Edge, suas funções do Lambda são executadas em pontos de presença do CloudFront, que são distribuídos globalmente para fornecer acesso de baixa latência ao seu conteúdo. Isso significa que você pode processar e modificar solicitações e respostas mais próximas dos usuários finais, resultando em entrega de conteúdo mais rápida e em uma melhor experiência do usuário.

As funções do Lambda@Edge devem ser criadas na região N.Virginia (us-east-1). Além disso, o tempo de execução das funções do Lambda@Edge é limitado apenas a Python e Node.js.

Lambda@Edge é adequado, especialmente para processamento dinâmico de conteúdo. Por exemplo, você pode usar o Lambda@Edge para realizar tarefas de processamento de imagens em tempo real, como criar miniaturas de imagens ou converter um formato de imagem em outro. Isso pode ajudar a reduzir o tempo de carregamento e melhorar a experiência do usuário, ao mesmo

tempo que minimiza a necessidade de pré-processamento de todos os tamanhos de imagem possíveis.

Função CloudFront

A função do CloudFront permite executar funções JavaScript leves na borda da rede do CloudFront.

Ao contrário do Lambda@Edge, as funções do CloudFront só podem ser acionadas em solicitações e eventos de resposta do visualizador.

Embora o CloudFront Functions ofereça tempos de inicialização e execução mais rápidos em comparação ao Lambda@Edge, seu poder de processamento é bastante restrito. Além disso, é limitado no que pode fazer. Por exemplo, ele não tem acesso a um sistema de

arquivos, o que significa que você não pode executar determinadas tarefas como ler ou gravar arquivos, fazer solicitações de rede a serviços externos ou acessar bancos de dados diretamente.

<!-- image -->

135







Dito isso, se você deseja executar tarefas simples, como manipulação de cabeçalho, redirecionamentos de URL ou solicitação de autorização, considere usar o CloudFront Functions, pois é muito mais barato que o Lambda@Edge.

Referências:

https://aws.amazon.com/cloudfront/features https:// docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-at-the-edge.html https://docs.aws. amazon.com/ AmazonCloudFront/latest/DeveloperGuide/high\_availability\_origin\_failover.htm l

https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cloudfront-functions.html https://aws.amazon.com/ blogs/aws/introduzindo-cloudfront-functions-run-your-code-at -a-borda-com-baixa- latência-em-qualquer-escala/

Amazon S3

Classes de armazenamento de objetos

Padrão Amazon S3

Esta classe é usada principalmente para armazenar dados acessados com frequência (dados importantes). Ele oferece armazenamento de objetos de alta durabilidade, disponibilidade e desempenho para diversas cargas de trabalho. Ele replica dados para três ou mais zonas de disponibilidade para atingir alta disponibilidade de 99,99%. Uma aplicação comum para esta classe é o armazenamento de ativos estáticos da web, como arquivos Javascript, CSS ou imagens para distribuição. Em termos de custo, a classe S3 Standard é a mais cara entre todas as outras classes, portanto, revise adequadamente seus requisitos de armazenamento antes de usar esse tipo.

Acesso infrequente padrão do Amazon S3 (IA)

Como o nome indica, essa classe de armazenamento normalmente é usada para armazenar dados que são recuperados com menos frequência, mas que ainda exigem acesso rápido quando necessário. O S3 Standard-IA possui a mesma durabilidade e disponibilidade que a Classe Standard oferece, porém está sujeito a uma cobrança de duração mínima de armazenamento de 30 dias.

Acesso pouco frequente ao Amazon S3 em uma zona

Essa classe de armazenamento é mais barata que a Standard-IA porque armazena dados apenas em uma única zona de disponibilidade. Como prática recomendada, você não deve usar essa classe de armazenamento para cópias de backup ou quaisquer dados importantes que não possam ser facilmente reproduzidos.

<!-- image -->

136







Camadas inteligentes do Amazon S3

Essa classe de armazenamento foi projetada para otimizar custos, movendo automaticamente os dados para a classe mais econômica, sem qualquer sobrecarga operacional de sua parte. A classe de armazenamento S3 Intelligent-Tiering é adequada nos casos em que não está claro com que frequência seus dados serão acessados. Escolher a classe de armazenamento certa para economizar dinheiro requer alguns insights sobre o padrão de acesso do seu objeto. Isso

significa que você deve coletar informações sobre seus padrões de acesso aos dados, bem como aprender a interpretá-los e analisá-los para tomar a melhor decisão possível. Se a análise de dados não é sua preferência ou se você deseja economizar tempo, o S3 Intelligent-Tiering é a melhor opção para você.

Recuperação flexível do Amazon S3 Glacier

O Amazon S3 Glacier Flexible Retrieval é uma solução de arquivamento de baixo custo otimizada para backup, armazenamento de dados externo e recuperação de desastres. É adequado para dados raramente acessados (normalmente uma ou duas vezes por ano) e não requer a velocidade de recuperação rápida da

classe Standard. Ele também replica seus dados para três ou mais zonas de disponibilidade e oferece uma disponibilidade de dados de 99,99%. O S3 Glacier Flexible Retrieval oferece três opções de recuperação, cada uma com um preço diferente e uma janela de recuperação que varia de minutos a horas.

Três tipos de opções de recuperação de arquivo:

- Recuperações padrão (padrão) - permite que você acesse seus arquivos de geleiras dentro de 3 a 5 horas.

- Recuperações rápidas - permite recuperar seus dados arquivados em apenas 1 a 5 minutos, desde que sejam

o tamanho do arquivo não excede 250 MB. Esta opção tem a taxa de recuperação de dados mais alta e é útil em situações em que são necessárias solicitações urgentes de recuperação de arquivos. Você também pode configurar uma capacidade provisionada para garantir que a capacidade de recuperação de suas recuperações aceleradas esteja disponível conforme necessário.

- Recuperações em massa - As recuperações em massa são gratuitas; tudo o que você precisa pagar é o armazenamento. Esta opção é ótima para recuperar grandes quantidades de dados (petabytes) dentro de 5 a 12 horas.

Recuperação instantânea do Amazon S3 Glacier

O Amazon S3 Glacier Instant Retrieval é uma solução de arquivamento que pode fornecer tempos de recuperação em milissegundos.

Esta opção é recomendada para dados de longa duração gerados pelo usuário que precisam de acesso imediato, como imagens médicas, ativos de mídia ou dados genômicos. O S3 Glacier Instant Retrieval oferece a mesma taxa de transferência e tempos de acesso do S3 Standard e do S3 Standard-IA. Por esse motivo, o S3 Glacier Instant Retrieval é uma alternativa muito mais barata em relação ao S3 Standard IA para dados que são acessados apenas algumas vezes por ano,

como uma vez por trimestre.

<!-- image -->



137







Arquivo profundo do Amazon S3 Glacier

Esta é a classe de armazenamento mais barata do Amazon S3. Ele foi projetado para armazenar dados que exigem longos períodos de retenção (normalmente 10 anos ou mais) para atender aos requisitos de conformidade regulatória. O S3 Deep Archive replica dados em três ou mais zonas de disponibilidade e garante 99,99% de disponibilidade dos dados. No entanto, é significativamente mais barato e tem um tempo de recuperação mais longo. Tem uma duração mínima de armazenamento de 180 dias, o que equivale quase a 6 meses (a mais longa entre outras classes de armazenamento). Por esse motivo, os dados que você armazena aqui raramente devem ser acessados e não possuem um tempo de recuperação rigoroso. O S3 Glacier Deep Archive oferece duas opções de recuperação que variam de 12 horas (padrão) a 48 horas (estendido) (em massa).

Duração mínima de armazenamento

O Amazon S3 impõe uma duração mínima de armazenamento para objetos armazenados em todas as classes, exceto no S3 Standard. Se você excluir, substituir ou fazer a transição de objetos para uma classe de armazenamento diferente antes do final da duração mínima, ainda será cobrado por toda a duração.

Por exemplo, fazer upload de um objeto para o S3 Standard-IA custará toda a duração mínima de 30 dias, independentemente

do que você fizer com o objeto. Digamos que você os excluiu após 5 dias na esperança de economizar custos de armazenamento. A duração efetiva pela qual você será cobrado ainda seria de 30 dias, mesmo que você não tenha armazenado seus dados por tanto tempo. Além disso, você paga uma cobrança proporcional igual à cobrança de armazenamento pelos dias restantes.

Criptografia Amazon S3

- KMS de criptografia no lado do servidor (SSE-

KMS): • O Amazon S3 facilita a criptografia para você •

Você pode usar a chave KMS gerenciada pela AWS para S3 ou uma chave KMS gerenciada pelo cliente para criptografar o S3 objetos.

- Para criptografar com uma chave KMS gerenciada pelo cliente, adicione kms :GenerateDataKey e kms:Decrypt permissões para sua política de chaves.
- Para aplicar a criptografia de objetos à medida que eles são carregados, inclua uma condição no seu bucket

política que nega solicitações que não incluem o cabeçalho x-amz-server-side-encryption com aws:kms como valor.

- Criptografia no lado do servidor S3 (SSE-S3)
    - O Amazon S3 facilita a criptografia para você. • O Amazon

S3 usa uma chave KMS AES-256 que possui e gerencia para criptografia.

<!-- image -->

138







- Para impor a criptografia de objetos, inclua uma condição na sua política de bucket que negue

solicitações que não incluem o cabeçalho x-amz-server-side-encryption com AES256 como valor.

- Criptografia no lado do servidor - chaves de criptografia fornecidas pelo cliente (SSE-C)
    - O Amazon S3 facilita a criptografia, mas você precisa fornecer a chave de criptografia junto com os dados como parte da sua solicitação. • Para recuperar dados

criptografados, você deve incluir a mesma chave de criptografia como parte da sua solicitação para O Amazon S3 pode descriptografar os dados.

- O Amazon S3 não armazena suas chaves de criptografia. Você é responsável por gerenciá-los, ou seja, se você perder suas chaves de criptografia, seus dados estarão praticamente perdidos.
- Você deve incluir os seguintes cabeçalhos na sua solicitação:

- algoritmo de cliente de criptografia do lado do servidor x-amz • chave do cliente de criptografia do lado do servidor x-amz • chave do cliente de criptografia do

lado do servidor x-amz MD5

- SSE-C aceita apenas chaves AES-256 e rejeita solicitações feitas por HTTP. Só aceita HTTPS solicitações, portanto, ele impõe criptografia em trânsito e criptografia em repouso.

- Criptografia do lado do cliente •

Os dados são criptografados pelo remetente antes de chegarem ao Amazon S3. • O

gerenciamento de chaves e a criptografia/descriptografia de dados são de responsabilidade do remetente. • Você pode usar uma biblioteca criptográfica do lado do cliente, como OpenSSL ou AWS Encryption SDK, para ajudá-lo

com a criptografia e descriptografia de dados conforme você os envia e recupera.

Notificações de eventos S3

A notificação de eventos do S3 permite que você acione 'gatilhos' quando determinados eventos ocorrem em seu bucket do S3. Você pode configurar o S3 para enviar notificações para três destinos diferentes:

• Função Lambda - quando um objeto é carregado em seu bucket do S3, você pode usar notificações de eventos do S3 para publicar seus dados de evento em uma função do Lambda. Isso permite automatizar processos no objeto, como redimensionamento de imagens ou criação de miniaturas.

• Tópico SNS - você pode optar por assinar um tópico SNS e ser notificado quando um objeto S3 for criado ou excluído do seu intervalo.

• Fila SQS - você também pode enviar eventos para uma fila SQS e ter uma função Lambda para processá-los.

Isto é útil quando você deseja processar eventos em lotes em vez de executar a função em cada evento. Ao usar uma fila SQS como

buffer para um consumidor, como a função Lambda, você pode garantir que os eventos sejam processados com eficiência e na taxa desejada.

<!-- image -->

139



 Associate por

e o

Você pode criar uma notificação para os seguintes eventos:

• Criação de objetos • Exclusão de objetos •

Restauração de eventos de objetos

• Eventos de perda de objetos de armazenamento com redundância reduzida (RRS)

• Eventos de replicação

• Eventos de expiração do ciclo de vida do S3

• Eventos de transição do ciclo de vida do S3

• Eventos de arquivamento automático do S3 Intelligent- Tiering

• Eventos de marcação de objetos

• Eventos PUT da ACL de objetos

Se nenhum desses eventos corresponder ao seu caso de uso, você também poderá ativar o envio de notificações para o Amazon EventBridge.

Isso fará com que o S3 envie todos os eventos para o EventBridge, permitindo processá-los usando código personalizado ou integrações de terceiros.

Filtragem

Opcionalmente, você pode usar prefixos e sufixos para filtrar os objetos sobre os quais deseja receber notificações. Por exemplo, digamos que você tenha um bucket S3 contendo ativos estáticos para um aplicativo de mídia social e queira receber notificações somente quando imagens de

avatar forem carregadas. Você pode criar uma notificação de evento S3 com um filtro que corresponda ao prefixo avatar/. Isso significa que um objeto com a chave avatar/user1.jpg ou avatar/cat.png acionará uma notificação, mas um objeto com a chave icons/icon123.jpg não.

Observe que você não pode ter sufixos sobrepostos em duas regras se os prefixos estiverem sobrepostos para o mesmo tipo de evento. Suponha que você tenha duas regras de notificação de eventos do S3 configuradas. A primeira regra é configurada para acionar uma função Lambda sempre que um novo objeto é criado com um prefixo docs/ e um sufixo .pdf. A segunda regra aciona uma função Lambda sempre que um novo objeto

é criado com um prefixo docs/payslip/ e um sufixo .pdf. Agora, suponha que um novo arquivo PDF seja carregado na pasta docs/payslip/ no bucket S3. Esta chave de objeto corresponde a ambas as regras, pois possui um prefixo de documentos/ e um sufixo de .pdf. Como resultado, o S3 lançará um erro Configuração é definida de forma ambígua porque não pode determinar qual função Lambda deve ser acionada para este evento.

Referências:

https://docs.aws.amazon.com/AmazonS3/latest/userguide/NotificationHowTo.html https:// aws.amazon.com/premiumsupport/knowledge-center/lambda-s3-event-configuration-error/

<!-- image -->



140







Objeto S3 Lambda

O S3 Object Lambda permite adicionar seu próprio código para processar dados à medida que eles são recuperados de objetos S3 usando funções Lambda. Você pode transformar ou aumentar dados dinamicamente sem precisar modificar os dados de origem. Um caso de uso popular do S3 Object Lambda é a redação de informações de identificação pessoal (PII) de objetos armazenados no S3. PII é qualquer informação que possa ser usada para identificar um indivíduo, como nome, endereço de e-mail, número de telefone ou número de seguro social. Com o S3 Object Lambda, você não precisa mais modificar o objeto original ou criar uma cópia separada dele com as PII removidas.

Além de remover PIIs, o S3 Object Lambda também é adequado para aplicações como:

• Conversão entre formatos de dados, como conversão de XML em JSON. • Aumentar

dados com informações de outros serviços ou bancos

• Redimensionar e colocar marcas d'água em imagens dinamicamente usando detalhes específicos do chamador, como o usuário que solicitou

de dados.

o objeto. • Implementação de regras de autorização personalizadas para

• Compactar ou descompactar arquivos à medida que são baixados.

acessar dados.

<!-- image -->

Qual a diferença entre o S3 Object Lambda e a notificação de eventos do S3 + função Lambda?

No padrão de função S3 Event Notifications + Lambda, a função Lambda é acionada após a ocorrência de um evento de objeto. Por outro lado, no S3 Object Lambda, a função Lambda é executada como parte do processo de recuperação, o que significa que acontece em tempo

real e é aplicada aos dados à medida que são recuperados.

Referências:

https://aws.amazon.com/s3/features/object-lambda/ https://

aws.amazon.com/blogs/aws/introduzindo-amazon-s3-object-lambda-use-your-code-to- processar-dados-como-está -sendo-recuperados-de-s3/

Outros recursos importantes do bucket S3

• Políticas de ciclo de vida — usadas para mover automaticamente objetos de uma classe de armazenamento para outra, em um esforço para reduzir custos de armazenamento ou arquivar um objeto. As políticas de ciclo de vida também podem ser usadas para expirar objetos com versão e excluí-los permanentemente do seu bucket. Ao criar uma política de ciclo de vida, você configura dois parâmetros para cada ação de transição ou exclusão:

	141







- Se a política deve ser aplicada a todos os objetos no bucket ou apenas a um grupo de objetos com prefixo correspondente

- O número de dias após a criação do objeto antes da ação ser aplicada. Para migrar objetos de Standard para Standard-IA, One-Zone-IA ou S3 Intelligent-Tiering, é necessário um mínimo de 30 dias para a transição.

• Multipart Upload — Ao usar o aws s3 cp para copiar/fazer upload de arquivos grandes, o S3 usa implicitamente o

recurso de upload multiparte. O multipart upload funciona dividindo os dados em partes individuais que são carregadas em paralelo, tornando a velocidade de upload mais rápida. O Amazon S3 então reconstrói as partes carregadas nos dados originais. Ao fazer upload ou recuperar objetos criptografados usando SSE-KMS, você deve conceder à sua chave KMS as permissões kms:Decrypt e kms:GenerateDataKey*, pois as partes carregadas no S3 são criptografadas no lado do servidor. O Amazon S3 precisa primeiro descriptografar as peças antes que elas possam ser remontadas no objeto original.

• Hospedagem estática na Web — um bucket S3 pode ser configurado para hospedar um site estático simples. Você simplesmente precisa fazer upload dos ativos da sua página da web (Javascript, CSS, imagem, etc.) para o bucket e habilitar a hospedagem na web no console S3. Certifique-se de definir seus objetos como disponíveis publicamente também. O Amazon S3 emitirá

um endpoint de site para seu bucket. Este endpoint, no entanto, não oferece suporte a HTTPS. Uma solução alternativa para isso é colocar o bucket S3 atrás de uma distribuição do CloudFront e criptografar a conexão entre o cliente e o CloudFront usando HTTPS. A conexão entre o CloudFront e o S3 permanece sem criptografia. Você também pode atribuir ao seu site um nome de domínio personalizado configurando um registro CNAME no Route 53 apontando para o URL do seu bucket S3.

Para este caso, o nome de domínio e o nome do bucket S3 devem ser uma correspondência exata.

• Controle de versão — O controle de versão permite manter uma cópia de um objeto sempre que ele for sobrescrito como suas versões. Você pode preservar e restaurar uma versão específica de um objeto, se necessário. Esse recurso também protege você contra exclusões acidentais, pois o controle de versão coloca marcadores de exclusão em uma versão do objeto para marcá-lo como removido, em vez de excluí-lo permanentemente do bucket do S3. Por padrão, o controle de versão está desabilitado em buckets e você deve habilitá-lo explicitamente. Uma vez ativado, não pode ser desativado, mas pode ser suspenso. Quando você suspende o controle de versão, quaisquer atualizações futuras em seus objetos não criarão uma nova versão, mas as versões existentes ainda serão retidas. Como uma versão de um objeto também ocupa espaço de armazenamento, o versionamento incorrerá em custos adicionais do S3, portanto, use esse recurso apenas se precisar dele.

• Compartilhamento de recursos entre origens (CORS) — CORS é uma forma de aplicativos clientes carregados em um domínio para interagir com recursos em um domínio diferente. Quando esse recurso estiver desativado, as solicitações

direcionadas a um domínio diferente não funcionarão corretamente. Se o seu bucket S3 for usado para hospedagem na web, verifique se você precisa habilitar o CORS. Para configurar seu bucket para permitir solicitações de origem

cruzada, crie um documento de configuração CORS. Este é um documento com regras que identificam as origens que você permitirá

<!-- image -->

142



 Associate por

e o

acesse seu bucket, as operações (métodos HTTP) que darão suporte a cada origem e outras informações específicas da operação.

• URLs pré-assinados: por padrão, todos os buckets e objetos do S3 são privados e só podem ser acessados pelo proprietário do objeto. Os proprietários de objetos podem compartilhar objetos com outros usuários ou permitir que os usuários carreguem objetos em seus buckets S3 usando um URL predefinido. Um URL pré-assinado concede a outros permissão por tempo limitado para fazer download ou upload de objetos dos buckets S3 do proprietário. Quando os proprietários de

objetos criam URLs pré-assinados, eles precisam especificar suas credenciais de segurança, o nome do bucket e a chave do objeto, o método HTTP (GET para fazer download do objeto) e a data e hora de expiração. O proprietário do bucket então compartilha esses URLs com aqueles que precisam de acesso aos objetos ou aos buckets. Um URL pré-assinado pode ser usado muitas vezes, desde que não tenha expirado.

Referências:

https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html https:// tutorialsdojo.com/amazon-s3/

Raio X da AWS

O AWS X-Ray é um serviço de rastreamento distribuído que pode ajudar você a analisar e depurar possíveis problemas em um aplicativo distribuído, como aqueles criados usando uma arquitetura de microsserviços. Como os microsserviços se comunicam por meio de

APIs, um dos desafios de implementação é lidar com a latência adicional de rede entre cada serviço. Portanto, além de monitorar métricas de desempenho e logs de aplicativos, como você está acostumado com aplicativos monolíticos, também é necessário desenvolver uma maneira de rastrear a latência nos componentes do seu aplicativo para detectar interrupções, à medida que elas ocorrem.

Com o AWS X-ray, você pode determinar facilmente qual parte do seu aplicativo está causando um problema ou gargalo de desempenho. O recurso de mapa de serviço do AWS X-ray permite que você veja as solicitações dos usuários à medida que elas percorrem os componentes do seu aplicativo. O mapa de serviços é uma representação visual das conexões entre os serviços da sua aplicação que permite ver informações como a latência média e as taxas de falha de todos os serviços que fazem parte da sua aplicação.

O rastreamento ponta a ponta também é compatível com o AWS X-ray. Isso é útil se você deseja rastrear o caminho de uma única solicitação nos nós do aplicativo. O AWS X-ray pode ser usado em aplicativos executados no Amazon EC2, Amazon Elastic Container Service, ElasticBeanstalk ou até mesmo no AWS Lambda.

Referências:

<!-- image -->

143

<!-- image -->





https://aws.amazon.com/xray/

https://aws.amazon.com/blogs/aws/aws-x-ray-see-inside-of-your-distributed-application/

Conceitos chave

Segmento

Os aplicativos que você está rastreando enviam dados ao AWS X-Ray na forma de segmentos. Um segmento é um documento JSON que contém informações sobre uma solicitação, como a rapidez com que o trabalho foi concluído, o método da solicitação, o endereço do cliente, o agente do usuário e assim por diante. Os segmentos gerados a partir de solicitações comuns são agrupados em um rastreamento e recebem um ID de rastreamento. Os dados de rastreamento são usados pelo X-Ray para gerar um gráfico de serviço que permite interpretar visualmente solicitações de ponta a ponta nos componentes do seu aplicativo.

Subsegmento

Os subsegmentos permitem rastrear funções específicas em seu código. Isso pode fornecer informações de tempo mais granulares, bem como detalhes sobre as chamadas downstream feitas pelo seu aplicativo.

Abaixo está um exemplo de como os subsegmentos são usados com o SDK do X-Ray para Python:

de aws\_xray\_sdk.core importar xray\_recorder

@xray\_recorder.capture('register user') def register\_user(): # Faça algo aqui

registrador\_usuario()

No exemplo, importamos o SDK do X-Ray para Python para o código do aplicativo. Em seguida, colocamos o decorador @xray\_recorder.capture antes da função Register\_User, que é a função que queremos instrumentar. Você pode passar um nome para a função de captura ou deixar em branco para usar o nome da função.

O processo de instrumentação de códigos varia de acordo com a linguagem de programação que você está usando.

Daemon de Raio X

O X-Ray Daemon é um agente que atua como proxy entre o aplicativo que está sendo rastreado e o AWS X-Ray. O SDK do X-Ray não envia segmentos diretamente para o AWS X-Ray. Nos bastidores, o daemon do X-Ray armazena em buffer os segmentos em uma fila e os

carrega no AWS X-Ray em lotes. Observe que o processo para ativar



144







O X-Ray Daemon varia de uma plataforma de computação para outra. A tabela abaixo resume como ativar o daemon X-Ray em várias plataformas.

Plataforma de computação	Como habilitar o daemon X-Ray

EC2/no local Função Lambda

Pé de Feijão Elástico

Baixe e instale o daemon X-Ray Habilite a opção Rastreamento Ativo Habilite a opção X-Ray Daemon

Amazon ECS

Use uma imagem Docker que tenha o daemon X-Ray

<!-- image -->

Além de ativar o daemon do X-Ray, você também deve conceder a ele as permissões de IAM necessárias para que ele chame APIs do X-Ray em seu nome. Ele deve ter pelo menos as permissões PutTraceSegments e PutTelemetryRecords para publicar segmentos. Essas permissões podem ser concedidas de diferentes maneiras. Por exemplo, você pode anexar essas permissões a uma função do IAM que seu aplicativo

pode assumir. Se o aplicativo estiver hospedado no EC2, você poderá anexar a função ao perfil da instância do EC2. Para funções Lambda, as permissões devem ser anexadas à sua função de execução.

Outras características:

Expressões de filtro - usadas para pesquisar rastros relacionados a caminhos ou usuários específicos

Grupos - uma coleção de rastreamentos definidos por uma expressão de filtro. Os grupos são identificados pelo nome ou por um nome de recurso da Amazon e contêm uma expressão de filtro.

Anotações - pares simples de valores-chave que são indexados para pesquisa de rastreamentos. Use anotações para registrar dados que você deseja usar para agrupar rastreamentos.

Metadados - pares de valores-chave com valores de qualquer tipo. Os metadados não são indexados. Eles são destinados à gravação de dados que você deseja armazenar no rastreamento, mas não serão usados para pesquisar rastreamentos.

Referências:

https://docs.aws.amazon.com/xray/latest/devguide/xray-services.html https:// docs.aws.amazon.com/xray/latest/devguide/xray-api.html

	145







Amazon Event Bridge

O EventBridge atua como um hub central para eventos, onde diferentes fontes (por exemplo, serviços AWS, aplicativos personalizados e terceiros) podem publicar eventos e assinar eventos de interesse. Quando um evento é enviado

para um barramento de eventos EventBridge, ele é comparado com regras predefinidas e roteado para os assinantes apropriados.

Essas regras permitem filtrar eventos com base em atributos como a origem do evento, o conteúdo do evento ou uma combinação de ambos. Depois que uma regra corresponde a um evento recebido, ela pode acionar um ou mais destinos, como funções Lambda para realizar ações personalizadas, tópicos SNS para serem notificados ou fluxos de trabalho do AWS Step

Functions para executar uma máquina de estado.

Acesso entre contas ao Event Bus

Em uma estratégia de múltiplas contas em que os componentes de um aplicativo são isolados uns dos outros em contas separadas, um barramento de eventos central pode ser usado para facilitar a comunicação entre esses componentes. Ao configurar um barramento de eventos central em uma conta separada, você pode garantir que a comunicação entre os diferentes componentes do seu aplicativo seja segura e confiável. Cada componente pode publicar eventos no barramento de eventos central e outros componentes podem assinar esses eventos conforme necessário.

Suponha que você tenha três contas AWS: Conta A, Conta B e Conta C. A conta A é o hub central do seu barramento de eventos, contendo as configurações e permissões necessárias para que as outras contas se comuniquem com ela. A conta B contém os componentes de back-end do seu aplicativo e a conta C contém os componentes de análise de dados.

Para permitir que a Conta B e a Conta C publiquem eventos no barramento de eventos da Conta A, você deve primeiro criar um barramento de eventos na Conta A com a seguinte política baseada em recursos:

{

"Versão": "17/10/2012", "Declaração": [ {

"Sid": "AllowAccountBAccess", "Efeito": "Permitir",

"Diretor": {

"AWS": "arn:aws:iam::ACCOUNT\_B\_ID:root"

},

"Ação": [

"eventos:PutEvents",

<!-- image -->

146







"eventos:PutRule", "eventos:PutTargets"

],

"Recurso": "arn:aws:events:REGION:ACCOUNT\_A\_ID:event-bus/central-eb"

},

{

"Sid": "AllowAccountCAccess", "Efeito": "Permitir",

"Diretor": {

"AWS": "arn:aws:iam::ACCOUNT\_C\_ID:root"

},

"Ação":

[ "eventos:PutEvents", "eventos:PutRule", "eventos:PutTargets"

],

"Recurso": "arn:aws:events:REGION:ACCOUNT\_A\_ID:event-bus/central-eb"

}

]

}

Publicando eventos diretamente no barramento de eventos

Para enviar eventos diretamente para o barramento de eventos, você pode usar a API PutEvents. Ao usar esse método, você deve ter as permissões necessárias para publicar eventos no barramento de eventos central na conta A. Por exemplo, uma função

Lambda na conta B deve receber à sua função de execução as permissões necessárias para publicar eventos no barramento de eventos da conta A. .

<!-- image -->



147







Usando a regra do EventBridge para enviar eventos ao barramento de eventos central

Em vez de enviar eventos diretamente para o barramento de eventos central, você pode configurar regras do EventBridge em cada conta do remetente (Conta B e Conta C) que direcionam o barramento de eventos na Conta A. No lado do destinatário, configure uma ou mais regras que combinar eventos provenientes das contas do remetente. Apenas certifique-se de que as contas do remetente tenham as permissões corretas para enviar eventos para o barramento de eventos da Conta A. Essa estratégia é útil se você deseja coletar eventos relacionados a cada conta e reuni-los em um local central.

Referências:

https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-cross-account.html https://aws.amazon.com/ blogs/compute/simplifying-cross-account-access-with -amazon-eventbridge-resource e-policies/

Amazon CloudWatch

Publicação de métricas personalizadas

<!-- image -->

148

<!-- image -->

 Associate por

e o

Existem duas maneiras de enviar métricas personalizadas para logs do Cloudwatch.

- Usando o agente CloudWatch

- O agente Unified CloudWatch é um aplicativo de software para coletar métricas de nível de sistema, métricas personalizadas e logs de instâncias do EC2 e servidores locais. O Cloudwatch Metrics pode coletar diferentes tipos de dados de seus recursos AWS, porém, não captura tudo. Métricas internas importantes no nível do sistema, como o uso de memória, não são monitoradas diretamente pelo Cloudwatch, por exemplo. Nesses casos, a instalação do agente Cloudwatch em seus servidores facilita o monitoramento.

- Você precisa ter permissão para usar a operação PutMetricData para publicar métricas na Amazon CloudWatch.

- Se você estiver hospedando o agente em um servidor local, faça download da AWS CLI e configure suas credenciais (chave de acesso e acesso secreto) usando o aws configure. Certifique-se de que seu usuário IAM tenha permissão para usar PutMetricData. Para instâncias EC2, é recomendado usar perfis de instância em vez de credenciais programáticas.

- Usando a API PutMetricData

- Nos bastidores, o agente CloudWatch usa a API PutMetricData para enviar métricas ao AWS CloudWatch. Se você não quiser passar pelo processo de instalação e configuração do agente CloudWatch, ou talvez seu caso de uso simplesmente não exija isso, uma solução alternativa é simplesmente chamar a API PutMetricData diretamente. Você poderia, por exemplo, escrever seu próprio script de monitoramento que envia periodicamente métricas personalizadas usando PutMetricData.

Referências:

https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Install-CloudWatch-Agent.html https://aws.amazon.com/ premiumsupport/knowledge-center/cloudwatch-push-custom-metrics /

	149







Amazon CloudTrail

AWS CloudTrail é um serviço gerenciado que você pode usar para monitorar e registrar as atividades que foram realizadas por um usuário do IAM, uma função do IAM ou um serviço da AWS em sua conta da AWS. Todas as ações realizadas nas chamadas do Console de gerenciamento da AWS, da API ou da CLI são registradas como eventos pelo CloudTrail. O CloudTrail pode ajudá-lo a facilitar a governança, a conformidade, a auditoria operacional e a auditoria de risco da sua conta da AWS.

Digamos, por exemplo, que um membro da sua organização tenha chamado excessivamente a API StartInstances, que inicia instâncias do EC2. Com o CloudTrail, você pode identificar exatamente quem é responsável por iniciar essas instâncias, determinar o momento da ação, bem como o endereço IP de origem onde a ação se originou. Você também pode integrar o CloudTrail ao AWS CloudWatch e ao Amazon SNS para alertas. Por exemplo, você pode criar um alarme do CloudWatch que acione um tópico SNS sempre que o número de um determinado evento de API exceder o limite definido.

Referências:

https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html https:// aws.amazon.com/blogs/mt/category/management-tools/aws-cloudtrail/

Conceitos

Os eventos são o registro da atividade em uma conta da AWS. Essa atividade pode ser uma ação realizada por um usuário, função ou serviço monitorável pelo CloudTrail.

Existem três tipos de eventos que você pode registrar:

• Eventos de gerenciamento - eventos que incluem operações de gerenciamento que ocorreram em seu AWS conta, como logins de usuários. Os eventos de gerenciamento estão habilitados por padrão

• Eventos de dados - eventos que incluem operações de recurso executadas no próprio recurso ou dentro dele, como atividade de API em nível de objeto do S3 ou atividade de execução de função Lambda. Os eventos de dados de registro são cobrados e, portanto, desabilitados por padrão.

- Eventos do Insights : eventos que incluem atividades e comportamentos incomuns do usuário na sua conta.

Histórico de eventos

Mesmo sem criar uma trilha, você ainda pode visualizar o histórico de atividades da API na sua conta. Você pode visualizar eventos no histórico de eventos para obter visibilidade imediata das atividades de API que ocorreram na sua conta da AWS nos últimos 90 dias. Também é possível pesquisar e baixar registros de eventos.

<!-- image -->



150







Se você tiver uma alta atividade de API em um dia, o número de eventos do CloudTrail poderá ser esmagador. Seria difícil procurar eventos específicos que possam ser úteis na solução de problemas de um incidente de segurança.

Nesse caso, você pode usar as definições do filtro de eventos para visualizar apenas eventos específicos (no histórico de eventos) de seu interesse:

• Eventos somente leitura referem-se a operações de API que leem recursos. As operações de leitura são operações que não causam modificações em um recurso. Exemplos desses eventos são as ações da API Amazon S3 ListBuckets e Amazon CloudWatch Logs DescribeMetricsFilters .

No console do CloudTrail, defina o valor dos eventos somente leitura como “true” para visualizar eventos somente leitura.

- Eventos somente gravação referem-se a operações de API que modificam ou podem modificar recursos em sua conta. Exemplos são as operações de API DeleteBucket do Amazon S3 e Amazon EC2 TerminateInstances .

Para habilitar eventos somente gravação, defina o valor Somente leitura como “falso”.

Referências:

https://aws.amazon.com/cloudtrail/faqs/ https:// docs.aws.amazon.com/awscloudtrail/latest/userguide/logging-management-events-with-cloudtrail.ht ml

<!-- image -->

151







Gerenciador de segredos da AWS

Como prática recomendada, os dados confidenciais (por exemplo, credenciais de banco de dados, chaves de API, senhas) não devem ser codificados no código do seu aplicativo, pois isso pode levar a violações de segurança. Muitas vezes, também é recomendado alternar as senhas regularmente, portanto, caso seu código vaze on-line, as senhas não permanecerão válidas indefinidamente. Essas tarefas podem ser difíceis de implementar, ainda mais quando se trata de diferentes aplicações. Tradicionalmente, os desenvolvedores armazenam credenciais de aplicativos em variáveis de ambiente ou em arquivos de configuração separados. Embora essa abordagem possa funcionar bem para um único aplicativo, ela não se adapta bem ao lidar com aplicativos maiores ou mais complexos.

Isso é especialmente verdadeiro para microsserviços que possuem vários componentes, cada um com seu próprio conjunto de credenciais. É aqui que o AWS Secrets Manager pode ajudá-lo.

O Secrets Manager permite armazenar e gerenciar credenciais de aplicativos em um local centralizado. Isso elimina a necessidade de manter credenciais em vários locais, como arquivos de configuração ou variáveis de ambiente. Os dados armazenados no Secrets

Manager são chamados de 'segredos', que podem ser um conjunto de credenciais de banco de dados, um par chave-valor (por exemplo, chaves de API, tokens), um documento JSON ou até mesmo um certificado com uma longa cadeia de confiança.

O principal ponto de venda do Secrets Manager é sua capacidade de automatizar o processo de rotação de credenciais para Amazon RDS, Amazon Redshift e Amazon DocumentDB. Se você estiver usando um serviço de banco de dados que não seja da AWS ou precisar alternar outros tipos de segredos, como tokens Oauth, será necessário implementar a lógica para alternar credenciais

usando uma função Lambda.

<!-- image -->

152



 Associate por

e o

O Secrets Manager usa um KMS que gerencia por padrão para impor a criptografia em repouso, portanto, não é possível armazenar dados em texto simples. No entanto, você também pode especificar uma chave KMS personalizada.

Recuperando segredos

Ao criar um segredo, você associa um nome secreto a ele. Esse nome secreto simplesmente atua como um ponteiro para o segredo ao qual você pode se referir no código do seu aplicativo. Assim, por exemplo, em vez de codificar as credenciais do banco de dados, você

pode substituí-las por códigos que utilizam a API GetSecretValue para extrair os segredos em tempo de execução. Chamar repetidamente essa API para autenticação pode ser ineficiente devido à sobrecarga da rede e pode levar a atingir o limite da API mais

rapidamente. Como solução alternativa, o Secrets Manager fornece uma biblioteca do lado do cliente com a qual você pode trabalhar para armazenar segredos em cache localmente, em vez de recuperá-los sempre do Secrets Manager.

Referências:

https://aws.amazon.com/secrets-manager/ https:// docs.aws.amazon.com/secretsmanager/latest/userguide/rotate-secrets\_turn-on-for-db.html

Armazenamento de parâmetros do AWS Systems Manager

O Parameter Store permite criar parâmetros de valor-chave onde você pode armazenar configurações de aplicativos, variáveis de ambiente personalizadas, chaves de produto e credenciais em um único local. Ao contrário do Secrets Manager, o Parameter Store foi projetado para atender a uma ampla gama de casos de uso, não apenas para senhas ou credenciais de banco de dados. Se você

deseja armazenar parâmetros que não exigem criptografia, como IDs de AMI, IDs de grupos de segurança ou URLs, o Parameter Store é a melhor ferramenta para o trabalho, pois é muito mais barato.

Três tipos de parâmetros:

- String - pode ser qualquer bloco de texto que você deseja armazenar sem criptografia

- StringList - um tipo de parâmetro onde as strings são separadas por vírgulas.

- SecureString – um tipo de parâmetro para armazenar informações confidenciais, como senhas ou chaves de licença. Você pode especificar uma chave KMS gerenciada pelo cliente ou uma chave KMS gerenciada pela AWS para criptografar parâmetros. Ao contrário do Secrets Manager, o Parameter Store não possui um recurso integrado de rotação de senha, portanto, isso é

algo que você deve criar por conta própria.

Existem também duas camadas que você pode escolher ao criar um parâmetro:

- Nível padrão

<!-- image -->



153



 Associate por

e o

- Pode armazenar até 10.000 parâmetros. • O

tamanho máximo do valor do parâmetro pode ser de até 4 KB. • Sem taxa adicional.

- Nível avançado
    - Pode armazenar até 10.000 parâmetros. •

Suporta políticas de parâmetros, que permitem definir uma data de expiração ou tempo de vida para um parâmetro.

Você pode selecionar entre três políticas de parâmetros:

- Expiration - exclui um parâmetro em uma data e hora específicas • ExpirationNotification - permite que você receba uma notificação da Amazon

EventBridge quando um parâmetro está prestes a expirar dentro de um número especificado de dias ou horas.

- NoChangeNotification – permite receber uma notificação do Amazon EventBridge quando um parâmetro não foi modificado por um período especificado. Isso é útil nos casos em que você precisa identificar proativamente senhas que talvez precisem ser atualizadas. • O tamanho máximo do valor do parâmetro pode ser de até 8

KB. • Vem com cobrança mensal fixa

Referências:

https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html https://aws.amazon.com/ blogs/mt/the-right-way -to-store-secrets-using-parameter-store/

Amazon EC2

Dados do usuário da instância versus metadados da instância

Os dados do usuário de uma instância pertencem a um conjunto de comandos que são executados quando uma instância é criada. Você fornece os dados do usuário durante a criação da instância. Você pode usar esse recurso para inicializar tarefas de configuração comuns que normalmente são executadas durante a configuração de um novo ambiente, como download de atualizações de software, instalação

de pacotes de software ou edição de arquivos de configuração do servidor.

<!-- image -->

154

<!-- image -->





Os metadados de uma instância são um conjunto de informações disponíveis que descrevem sua instância do EC2. Metadados é um termo geral para coisas que descrevem dados. Por exemplo, em um arquivo JPG, além dos bits reais que compõem a

imagem, outras propriedades como dimensão, resolução e carimbo de data/hora também são incorporadas ao arquivo de imagem. O conceito é semelhante ao que são metadados de instância. É uma coleção de propriedades relevantes da instância do EC2, como AMI, nome do host, endereço IP público, endereço IP privado, tipo de instância, endereço MAC e muito mais.

	155







Os metadados da instância também permitem visualizar os grupos de segurança associados, as credenciais de segurança e as funções do IAM da sua instância do EC2. Lembre-se de que você só pode buscar os metadados da instância em uma instância em execução no Instance Metadata Service (IMDS), que pode ser acessado por

meio de http://169.254.169.254/latest/metadata endereço link-local. Este endereço não é acessível publicamente e é exclusivo apenas para instâncias EC2.

Referências:

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html https:// docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-data-retrieval.html

<!-- image -->

156



 Associate por

e o

Grupo de escalonamento automático

Escala vertical versus escala horizontal

Se uma pessoa está lutando para concluir um trabalho difícil, você tem duas opções: substituir essa pessoa por alguém que seja mais capaz de realizar a tarefa ou adicionar mais pessoas para ajudar. Este exemplo ilustra o conceito de escala. A primeira opção representa a escala vertical, enquanto a segunda é conhecida como escala horizontal.

O dimensionamento vertical envolve a substituição do seu servidor atual por um mais poderoso. Na AWS, se a carga da sua instância exceder frequentemente a capacidade da CPU, uma solução poderia ser simplesmente atualizá-la para um tipo de instância EC2 com mais núcleos. Por outro lado, o escalonamento horizontal é o processo de adicionar mais servidores para atender às demandas da sua aplicação.

Escalabilidade horizontal na AWS

O processo de escalabilidade horizontal é facilitado com a ajuda do serviço Auto Scaling, que permite que a capacidade computacional se adapte dinamicamente com base nos requisitos de carga. Um Auto Scaling Group (ASG) é uma coleção de instâncias do EC2 que

são tratadas como uma única unidade para fins de escalabilidade e gerenciamento.

Ao criar um ASG, você define um modelo de lançamento. Um modelo de execução serve como um modelo para as instâncias criadas em um grupo do Auto Scaling, descrevendo o ID da AMI, o tipo de instância, as configurações de segurança e outros parâmetros relacionados à instância. Com o modelo de lançamento implementado, você estabelece uma política de escalonamento automático que define a capacidade máxima e mínima, bem como seu comportamento de escalonamento. Por exemplo, você pode configurar o ASG para aumentar a escala sempre que a utilização da CPU exceder 60% e aumentar se for inferior a 30%. O dimensionamento também pode ser baseado em um

cronograma. Por exemplo, você pode manter uma capacidade específica para horários normais e adicionar capacidade apenas durante horários de pico.

Referências:

https://aws.amazon.com/ec2/autoscaling https:// docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroup.html

<!-- image -->



157

<!-- image -->





Construtor de imagens EC2

A imagem do EC2 simplifica o processo de criação, gerenciamento e implantação de Amazon Machine Images (AMIs) personalizadas com configurações, atualizações e patches de software específicos. Ele automatiza todo o processo de criação de imagens, permitindo manter AMIs consistentes e atualizadas para uso em vários ambientes, contas e regiões.

Casos de uso comuns

- Atualizações automatizadas de AMI para grupos de Auto Scaling

Suponhamos que você tenha um grupo do Auto Scaling com um modelo de inicialização que faz referência a uma AMI personalizada que contém a pilha de software do seu aplicativo. Como as instâncias do EC2 no grupo são apenas temporárias, elas não recebem patches de segurança ou atualizações de software durante o tempo de execução. Se quiser aplicar essas atualizações, você terá que executar uma instância da AMI atual, instalar as atualizações lá, tirar um snapshot da AMI dessa instância e, em seguida, reconfigurar o modelo de execução do seu ASG para fazer referência à nova AMI. Essas tarefas podem ser propensas a erros e difíceis de replicar entre contas ou regiões. Para simplificar esse processo, você pode usar um pipeline do EC2 Image Builder que cria um novo modelo de execução que faz referência à AMI mais recente do seu aplicativo.

- Reduza o tempo de inicialização de instâncias executadas em um grupo de Auto Scaling

O EC2 Image Builder permite reduzir ou até mesmo eliminar a necessidade de scripts de bootstrap em suas instâncias. Em vez disso, você pode usar o EC2 Image Builder para definir uma receita que inclua todos os pacotes de software, configurações e personalizações necessários para sua AMI. Ao usar uma AMI pré-configurada para as instâncias antes de serem executadas, você pode minimizar o tempo que uma instância leva para ficar disponível e começar a processar solicitações.

- Padronização de AMIs compatíveis com segurança em contas e regiões

O EC2 Image Builder permite impor controles e configurações de segurança consistentes em suas AMIs, que podem ser distribuídas em diferentes regiões e contas da AWS.

Referências:

https://docs.aws.amazon.com/imagebuilder/latest/userguide/what-is-image-builder.html https:// aws.amazon.com/blogs/security/how-to-set-up-continuous -golden-ami-vulnerabilidade-avaliações-com -inspetor-amazon

	158







Amazon Elastic Load Balancing (ELB)

O Elastic Load Balancing (ELB) distribui o tráfego de entrada entre vários destinos, como instâncias do Amazon EC2, funções

do AWS Lambda, contêineres do Amazon EKS, tarefas do Amazon ECS e outros componentes. O ELB é dimensionado à medida que o tráfego muda, permitindo lidar com milhões de solicitações por segundo. Os ELBs são normalmente usados em conjunto com o

ASG para fornecer um ponto único de acesso para usuários às instâncias EC2 subjacentes. Outra vantagem do ELB é que ele permite criar um ambiente altamente disponível para sua aplicação. Ao criar um ELB, a AWS atribui um nó do balanceador de carga na zona de disponibilidade especificada. Você pode rotear o tráfego para servidores em execução em diferentes zonas de disponibilidade. Portanto, supondo que você tenha servidores em três zonas de disponibilidade, caso um deles sofra uma interrupção, você ainda terá duas zonas não afetadas que podem receber tráfego.

Tipos de balanceador de carga

ELB oferece diferentes tipos de balanceadores de carga. O tipo de balanceador de carga depende do tráfego que você deseja distribuir. Outra coisa a verificar ao configurar um ELB é se o balanceador de carga seria voltado para a Internet ou interno.

Balanceador de carga de aplicativo (ALB)

Para rotear solicitações HTTP e HTTPS, um Application Load Balancer é uma boa opção. Como esse balanceador de carga funciona na camada 7, ele pode distribuir as solicitações HTTP e HTTPS do seu aplicativo web. Um ALB pode funcionar como um balanceador de carga interno e voltado para a Internet e funcionar para endereços IPv4 e IP de pilha dupla. Requer no mínimo duas sub-redes diferentes em zonas de disponibilidade diferentes. Observe que um certificado de servidor será necessário se você tiver um ouvinte configurado para o protocolo HTTPS. Você pode usar um certificado do AWS Certificate Manager ou do IAM.

Balanceador de carga de rede (NLB)

Um Network Load Balancer opera na camada de transporte (camada 4) e é capaz de lidar com milhões de solicitações por segundo em latências ultrabaixas. O Network Load Balancer também pode ser interno ou voltado para a Internet e também oferece

suporte a endereços IPv4 e IP de pilha dupla. Os NLBs veem apenas informações de tráfego, como portas de origem/destino, endereços IP e tamanhos de pacotes. Não considera os dados adicionais que

<!-- image -->



159







uma solicitação HTTP possui, como cabeçalhos, corpo, cookies, etc. Você pode configurar um Network Load Balancer usando apenas uma sub- rede, mas duas sub-redes são ideais para melhorar a tolerância a falhas do seu aplicativo. Certifique-se também de que o grupo-alvo tenha pelo menos um alvo válido para aceitar as solicitações. Se várias AZs forem especificadas, você poderá ativar o balanceamento de carga entre zonas para distribuir o tráfego em todos os destinos igualmente. A direção do tráfego da rede dependerá das regras definidas pelo ouvinte e pelo roteamento.

Balanceador de carga de gateway (GWLB)

Um Gateway Load Balancer facilita o gerenciamento de vários dispositivos virtuais. Um GWLB pode distribuir o tráfego entre vários dispositivos virtuais que suportam o Generic Network Virtualization Encapsulation (GENEVE). Você pode ativar o GWLB em uma única sub-rede, mas o grupo de destino deve ter pelo menos um destino que aceite o protocolo GENEVE. Observe que o Gateway Load Balancer oferece suporte apenas a endereços IPv4; não suporta IPv6 e dualstack.

Referências:

<!-- image -->



160

<!-- image -->





https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html https:// docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load -balanceamento-works.html

Componentes ELB

- Listener - um processo que verifica continuamente solicitações de conexão em seu balanceador de carga usando o

protocolo, porta ou qualquer outra configuração que você configurou. Por exemplo, você pode criar um ouvinte para solicitações HTTP que verifica qualquer tráfego de entrada que esteja usando a porta 80. Portanto, se o usuário inserir http://tutorialsdojo.com em um navegador da web, essa solicitação será captada pelo ouvinte. No entanto, se outro usuário enviar

uma solicitação HTTPS ao seu aplicativo, o tráfego poderá não ser roteado corretamente, pois o protocolo HTTPS usa a porta 443.

- Destino - pode ser uma instância EC2, um endereço IP, uma função Lambda ou uma tarefa ECS. Esses alvos são organizados em um recurso chamado Grupo-alvo. Todo o tráfego capturado pelo ouvinte é direcionado para um grupo de destino específico que contém os recursos de computação. Por exemplo, você pode criar um grupo de destino que contenha várias instâncias do

EC2 e um listener seguro que ouça todas as solicitações HTTPS na porta 443.

Condições da regra do listener do balanceador de carga do aplicativo

O AWS ELB Application Load Balancer é rico em recursos de roteamento que não podem ser encontrados em outros tipos de balanceadores de carga elásticos. Uma condição de regra do listener determina como o balanceador de carga roteia a solicitação para seus destinos registrados.

Você pode adicionar as seguintes condições a uma regra de listener para criar vários caminhos de roteamento em um único balanceador de carga:

	161







- host-header — Rota baseada no nome do host de cada solicitação. Também conhecido como roteamento baseado em host. Essa condição

permite oferecer suporte a vários subdomínios e diferentes domínios de nível superior usando um único balanceador de carga. Nomes de host e avaliações de correspondência não diferenciam maiúsculas de minúsculas.

- http-header — Rota baseada nos cabeçalhos HTTP de cada solicitação. Cabeçalhos padrão e personalizados são

suportado. O nome do cabeçalho e a avaliação de correspondência não diferenciam maiúsculas de minúsculas.

- http-request-method — Rota baseada no método de solicitação HTTP de cada solicitação. Você pode especificar

métodos HTTP padrão ou personalizados para o valor. A avaliação de correspondência diferencia maiúsculas de minúsculas, portanto, para rotear adequadamente as solicitações para essa condição, o método de solicitação deve corresponder exatamente ao valor inserido.

- path-pattern — Rota baseada em padrões de caminho nas URLs de solicitação. Também conhecido como roteamento baseado em caminho.

Esta condição permite rotear para vários destinos dependendo do caminho da URL fornecido na solicitação. O caminho do URL não inclui os parâmetros de consulta. A avaliação do caminho diferencia maiúsculas de minúsculas. • query-string —

Roteamento baseado em pares chave/valor ou valores nas strings de consulta. A avaliação da partida não é maiúsculas e minúsculas. Esta condição não inclui o caminho da URL na avaliação. • source-ip — Rota

baseada no endereço IP de origem de cada solicitação. O endereço IP deve ser especificado no formato CIDR. Os endereços IPv4 e IPv6 são suportados como valores para esta condição. Se um cliente estiver atrás de um proxy, a condição avaliará o endereço IP do proxy,

não o endereço IP do cliente.

Uma regra de ouvinte pode incluir até uma de cada uma das seguintes condições: cabeçalho de host, método de solicitação http, padrão de caminho e ip de origem; e inclua uma ou mais de cada uma das seguintes condições: cabeçalho http e string de consulta. Você também pode especificar até três avaliações de correspondência por condição, mas somente até cinco avaliações de correspondência por regra. Isso lhe dá mais valor para trabalhar para cada condição criada.

<!-- image -->

162







Referências:

https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html#rule-cond ition- types

https://tutorialsdojo.com/aws-elastic-load-balancing-elb https ://aws.amazon.com/elasticloadbalancing/

https://aws.amazon.com/blogs/aws/category/elastic-load-balancing/

<!-- image -->



163

<!-- image -->





Cabeçalhos com vários valores

Em alguns casos, você pode querer criar uma configuração híbrida para seu aplicativo em que algumas solicitações sejam roteadas para instâncias do EC2 enquanto outras sejam tratadas por uma função Lambda. Você pode adotar esse modelo para transferir algumas das tarefas normalmente executadas por suas instâncias EC2 para o AWS Lambda. Isso permite implantar instâncias menores e mais baratas, o que pode economizar custos no longo prazo.

Processar solicitações com funções Lambda como destino ALB pode ser um pouco complicado. Por padrão, se uma solicitação ou resposta de uma função Lambda incluir cabeçalhos/parâmetros de consulta com vários valores ou vários valores para a mesma chave de parâmetro de consulta, o ALB selecionará apenas o último valor.

Suponha que um cliente envie a solicitação de amostra:

https://tutorialsdojo.com?id=123&id=789

Ao receber a solicitação, o ALB incluirá queryStringParameters nos dados do evento enviados para a função Lambda. Este parâmetro contém o último parâmetro de consulta na solicitação do cliente.

"queryStringParameters": { "id": "789"}

Para incluir todos os valores dos parâmetros de consulta, basta ativar a configuração de vários valores no ALB. Uma vez habilitados, os cabeçalhos e parâmetros de consulta trocados entre o ALB e a função Lambda serão construídos como uma matriz em vez de uma string. Desta vez, em vez de queryStringParameters, o ALB usa multiValueQueryStringParameters

para representar os valores associados a um parâmetro de consulta específico.

"multiValueQueryStringParameters": { "id": ["123", "789"] }

Referências:

https://docs.aws.amazon.com/elasticloadbalancing/latest/application/lambda-functions.html#multi-value-he aders https://aws.amazon.com/ blogs/

networking-and-content- entrega / funções lambda como alvos para balanceadores de carga de aplicativo /

Preservando o endereço IP do cliente usando o cabeçalho X-Forwarded-For Se seu aplicativo

for fronteado por um Application Load Balancer (ALB), os logs do servidor conterão apenas o endereço IP do ALB como origem da solicitação. Isso ocorre porque o ALB intercepta o tráfego antes que ele seja

	164







passado para o seu servidor. Se você precisar determinar os endereços IP reais dos usuários que estão acessando seu servidor para fins de registro, poderá recuperá-los do cabeçalho X-Forwarded-For.

O snippet abaixo representa os cabeçalhos normalmente incluídos em uma solicitação HTTP que seu aplicativo pode ver no ALB.

<!-- image -->

Host: example.com User-

Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, como Gecko) Chrome/97.0.4692.99 Safari/537.36 Aceitar: text/html,application/xhtml+xml, application/xml;q=0.9,image/

avif,image/

webp,image/apng, */*;q=0.8,application/signed-exchange;v=b3;q=0.9 Accept-Encoding: gzip, deflate, br Accept-Language: en-US,en;q=0.9 Conexão: keep-alive X-Forwarded-For: 203.0.113.195

X-Forwarded-Proto: http Porta X-Forwarded: 80

- Amzn-Trace-Id: Raiz=1-61f1d2ba-6ea61b6a65f6c0975439a9a3

Na configuração do ALB, é possível configurar o atributo routing.http.xff\_header\_processing.mode para anexar para informar ao ALB para incluir o cabeçalho X-Forwarded-For na solicitação HTTP. Quando uma solicitação é feita por meio de uma série de proxies, o cabeçalho da solicitação X-Forwarded-For pode conter vários endereços IP separados por vírgulas. Neste caso, o endereço

IP mais à esquerda é normalmente o endereço IP do cliente original que fez a solicitação, e quaisquer endereços subsequentes representam os endereços IP de proxies intermediários na cadeia de solicitação.

Referências:

https://docs.aws.amazon.com/elasticloadbalancing/latest/application/x-forwarded-headers.html



165





Amazon Elasticache

Memcached x Redis

O Amazon ElastiCache é um serviço de armazenamento em cache que permite configurar, executar e dimensionar bancos de

dados na memória de código aberto, como Memcached e Redis. Como armazenam dados em RAM (memória de acesso aleatório), eles podem ler dados mais rapidamente do que bancos de dados baseados em disco. Grandes volumes de leituras costumam ser a

causa de lentidão no desempenho dos aplicativos. Uma camada de cache é um padrão comum para aliviar esse problema. Em vez de recuperar continuamente os dados acessados com mais frequência do armazenamento tradicional baseado em disco, você pode redesenhar seu aplicativo para armazenar e obter dados de uma instância de cache do Amazon ElastiCache. Este serviço, além do cache, pode ser utilizado em análises em tempo real, gerenciamento de sessões distribuídas, serviços geográficos e uma variedade de

outras aplicações.

O ElastiCache é classificado em dois tipos:

- O Amazon ElastiCache for Memcached é ideal para armazenar em cache estruturas de dados simples, como pares de chave-valor. O Memcached é multithread, o que significa que pode aproveitar vários núcleos de processamento, permitindo lidar com processos adicionais, aumentando a capacidade computacional. A desvantagem de usar o Memcached é a falta de funcionalidade de replicação de dados, o que pode afetar a disponibilidade do seu aplicativo.

- O Amazon ElastiCache for Redis oferece suporte a estruturas de dados mais avançadas, como listas, conjuntos, hashes, conjuntos ordenados. Ele também oferece funcionalidade avançada para classificação e classificação de dados, o que pode ser útil para aplicações como tabelas de classificação e classificações. Além disso, o ElastiCache for Redis oferece vários outros recursos, como mensagens pub/sub, indexação geoespacial e suporte a snapshots pontuais. A replicação de dados também está disponível, tornando-a uma solução de armazenamento confiável e de alta disponibilidade. Ao ativar o modo Cluster, os desenvolvedores podem criar um cluster Redis com vários nós primários e réplicas em duas ou mais zonas de disponibilidade, fornecendo recursos de redundância e failover.

Referência:

https://aws.amazon.com/elasticache/redis-vs-memcached/

Estratégias de

armazenamento em cache Existem vários padrões de design para armazenamento em cache de dados, cada um com uma

finalidade diferente que depende das necessidades do seu aplicativo. Existem dois padrões principais de cache que você deve conhecer no exam

Carregamento lento

<!-- image -->

166







O carregamento lento é talvez a estratégia de cache mais amplamente usada para aplicativos da web. Reduz o tempo de carregamento e melhora a capacidade de resposta, carregando dados no cache somente quando necessário. Como resultado, apenas os dados solicitados são armazenados em cache. O carregamento lento evita que o cache armazene dados que raramente são acessados. A desvantagem, entretanto, é a latência extra que ocorre durante uma falta de cache desde então. Além disso, os dados solicitados podem ficar desatualizados porque o cache só é atualizado com novas atualizações quando há uma falha

no cache. O diagrama abaixo ilustra como funciona o carregamento lento.

- O aplicativo tenta recuperar dados do cache. Se os dados forem encontrados no cache (cache hit), a função de chamada os retornará ao aplicativo.
- Se o cache não possuir os dados solicitados (cache miss), o cache envia uma resposta nula para o aplicativo.
- A lógica de cache do aplicativo trata a resposta nula recuperando os dados solicitados do banco de dados. Os dados solicitados são então gravados no cache antes de serem retornados ao aplicativo pela função de chamada.

<!-- image -->



167







O pseudocódigo abaixo é um exemplo de como você pode implementar uma lógica de carregamento lento.

get\_user(id\_do\_usuário)

registro = cache.get(user\_id)

if (registro == nulo)

query\_statement = "SELECT * FROM Usuários WHERE id = {user\_id}" registro = db.query(query\_statement) cache.set(user\_id,

registro)

registro de retorno

Escreva através

A estratégia write-through adiciona ou atualiza dados no cache sempre que novos dados são gravados no banco de dados. Como resultado, os dados que o aplicativo recupera do cache são sempre os mais recentes. Uma das desvantagens de uma estratégia write- through é a falta de dados ao adicionar novos nós. Isso se deve ao fato de que o cache só é atualizado quando uma operação de gravação é executada no banco de dados. Você pode implementar uma combinação de gravação e carregamento lento para resolver o problema de dados ausentes.

O diagrama abaixo ilustra como funciona o write-through.

- O aplicativo grava dados no banco de dados.
- O aplicativo grava dados no cache.

<!-- image -->

168

<!-- image -->





O pseudocódigo abaixo é um exemplo de como você pode implementar uma lógica write-through.

update\_username(user\_id, nome de usuário)

query\_statement = "ATUALIZAR Usuários SET nome de usuário = {username} WHERE id = {user\_id}" record = db.query(query\_statement) cache.set(user\_id, record)

return ok

Referência:

https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/Strategies.html

	169







Amazon Kinesis

Amazon Kinesis é um conjunto de serviços que ajuda você a trabalhar com streaming de dados. Possui quatro serviços, a saber, Amazon Kinesis Data Streams, Amazon Kinesis Data Firehose, Amazon Kinesis Data Analytics e Amazon Kinesis Video Streams. Para fins do exame, focaremos apenas no Amazon Kinesis Data Streams e no Amazon Kinesis Data Firehose.

Fluxo de dados do Kinesis

O Kinesis Data Stream permite ingerir dados em tempo real de diversas fontes, como dispositivos IoT, aplicativos web, logs do sistema e, em seguida, processá-los usando as ferramentas de sua escolha.

Fragmentos

Ao criar um stream do Kinesis, você define o número de fragmentos que deseja alocar. Um fragmento é uma unidade de capacidade que determina quantos dados podem ser gravados ou lidos de um fluxo a qualquer momento. Ao fazer o planejamento de capacidade, é importante considerar o tamanho médio do registro e o número de consumidores com os quais você lidará.

Se os seus registros forem grandes, talvez seja necessário provisionar mais fragmentos para lidar com o volume de dados. Da mesma forma, ter vários consumidores lendo dados do mesmo fragmento pode causar contenção e limitar a capacidade de rendimento do fragmento.

Modo de capacidade provisionada versus sob demanda

Você tem duas opções de provisionamento de capacidade: provisionado ou sob demanda.

- Modo provisionado
    - Um único fragmento suporta •

Um máximo de 1.000 registros/segundo e 1 MB/segundo para gravações. • Máximo de 2 MB/segundo para leituras. • Pode reter dados no

fluxo por 24 horas (padrão) até 365 dias. • Suporta criptografia no lado do servidor usando uma chave KMS

- Modo sob demanda
    - O Kinesis dimensiona automaticamente a capacidade de taxa de transferência com

base no tráfego. • Por padrão, um fluxo de dados começa com 4 MB/s de gravação e 8 MB/s de taxa de transferência de leitura, mas pode chegar a 200 MB/s e 400 MB/s para gravações e leituras , respectivamente.

<!-- image -->

171







- Se precisar de uma taxa de transferência mais alta, você poderá enviar um aumento de cota do AWS Support. • Adequado para requisitos de rendimento imprevisíveis e variados. •

Pode reter dados no stream por 24 horas (padrão) até 365 dias. • Suporta criptografia no lado do servidor usando uma chave KMS

Referências:

https://docs.aws.amazon.com/streams/latest/dev/key-concepts.html https:// aws.amazon.com/kinesis/data-streams/ https://

docs.aws.amazon .com/streams/latest/dev/service-sizes-and-limits.html

Gravando e lendo dados em fragmentos

Escrevendo em um fragmento

Você pode gravar em um fragmento usando a API PutRecord ou PutRecords . PutRecord permite gravar um único registro por vez, enquanto PutRecords permite gravar registros em lotes. Ao utilizar PutRecords, o Kinesis tentará processar todos os registros da solicitação, mesmo que haja falha no processamento de um dos registros, o que significa que a ordenação dos registros não

é garantida. Se você precisar garantir que os registros sejam processados na mesma ordem em que foram gravados no fragmento, use PutRecord.

Observe que cada dado gravado em um fluxo recebe um número de sequência exclusivo. Esses números de sequência aumentam com o tempo, portanto, os dados mais recentes terão um número de sequência maior que os dados mais antigos. No entanto, é importante observar que esses números de sequência são específicos de um fragmento específico no fluxo. Se você

estiver gravando dados em vários fragmentos no mesmo fluxo, os números de sequência aumentarão independentemente para cada fragmento. Para garantir que seus dados sejam estritamente ordenados, você precisa gravar em cada fragmento em série, um de cada vez, e adicionar o parâmetro SequenceNumberForOrdering em sua solicitação PutRecord.

Opcionalmente, você pode usar a estrutura Kinesis Producer Library (KPL) para gravar vários registros em vários fragmentos em uma única solicitação. Usar KPL em vez da API PutRecords nativa pode ajudar a reduzir a complexidade do seu código e facilitar a gravação de aplicativos robustos e escalonáveis. Observe que o KPL usa métodos de buffer para obter maior rendimento, o que significa que alguns atrasos no processamento são esperados. Se seu aplicativo não tolerar atrasos na gravação de dados em streams do

Kinesis, o KPL pode não ser a melhor escolha.

Lendo de um fragmento

A leitura de um fragmento normalmente envolve duas etapas:

<!-- image -->



172

<!-- image -->





- Obtenção de um iterador para o fragmento que você deseja ler. Isto pode ser feito ligando para o

API GetShardIterator e especificando o ID do fragmento e o tipo de iterador que você deseja usar. Um iterador

serve como um marcador que indica a posição do último registro lido.

- Use a API GetRecords e forneça o iterador junto com o número máximo de registros a serem lidos.

A resposta GetRecords inclui um novo iterador que pode ser usado para ler o próximo conjunto de registros. Em alguns casos, pode ser necessário obter um novo iterador separadamente, como quando o iterador atual expirou ou quando você precisa ler de uma posição diferente no fragmento.

Os iteradores expiram após um determinado período de tempo. Ao usar uma função Lambda para processar dados de

um stream, é importante monitorar a métrica IteratorAge . IteratorAge mede quanto tempo se passou desde que a função Lambda leu pela última vez um dado de um stream. Se a idade do iterador ficar muito alta, significa que a função Lambda está ficando para trás e não acompanhando a adição de novos dados ao fluxo. Isso pode causar problemas como processamento lento de novos dados, processamento duplicado de dados antigos ou até mesmo perda total de dados.

Os métodos a seguir podem ajudar a mitigar um IteratorAge crescente:

- Aumente a quantidade de memória alocada para sua função Lambda para que o tempo de processamento de registros seja mais rápido. Você também pode tentar otimizar o código da sua função para melhorar o tempo de execução sem custo adicional. • Aumentar a contagem de

fragmentos. • Aumente o tamanho

do lote da sua função Lambda. • Usar um fator de paralelização

para aumentar o número de invocações simultâneas do Lambda para cada fragmento

de um riacho.

- Ativar o recurso de distribuição aprimorada na transmissão.

Melhorar a distribuição

Imagine que existem várias funções Lambda que leem dados de um stream ao mesmo tempo. O que significa que eles podem ter que competir pelo acesso ao stream. Normalmente, estas funções teriam que competir pelo acesso ao fluxo, o que

poderia retardar a recuperação de dados, uma vez que estariam compartilhando a capacidade do fluxo.

No entanto, com a distribuição aprimorada, cada função obtém sua própria porção dedicada da capacidade do fluxo.

Portanto, se o fluxo puder lidar com 10 MB de dados por segundo e houver três consumidores usando distribuição aprimorada, cada função poderá receber até 2 MB de dados por segundo sem ter que competir com as outras. Isso pode reduzir a latência e aumentar a taxa de transferência de leitura.

Assim como KPL serve para publicar dados em um stream (Kinesis Consumer Library), KCL é uma estrutura para consumir dados. KCL fornece uma maneira simples de ler e processar dados de um stream do Kinesis usando um

	173

<!-- image -->





consumidor. Ele cuida de muitos dos detalhes de baixo nível envolvidos no consumo de dados, como o gerenciamento dos fragmentos do fluxo, a coordenação com outros consumidores e o tratamento de falhas.

Referências:

https://docs.aws.amazon.com/kinesis/latest/APIReference/API\_PutRecord.html https://docs.aws.amazon.com/ kinesis/latest/APIReference/API\_PutRecord.html https://docs. aws.amazon.com/streams/latest/dev/ troubleshooting-consumers.html https://aws.amazon.com/premiumsupport/knowledge-center/lambda-iterator- age/

Dimensionamento, refragmentação e processamento paralelo

- O Kinesis Resharding permite aumentar (dividir fragmentos) ou diminuir o número de fragmentos (mesclar fragmentos) em um stream para se adaptar às alterações na taxa de fluxo de dados através do stream. • A refragmentação é sempre

feita em pares. Você não pode dividir em mais de dois fragmentos em uma única operação e

você não pode mesclar mais de dois fragmentos em uma única operação.

- A Kinesis Client Library (KCL) rastreia os fragmentos no stream usando uma tabela do Amazon DynamoDB e se adapta às alterações no número de fragmentos resultantes da nova fragmentação. Quando novos fragmentos são criados como resultado da nova fragmentação, a KCL descobre os novos fragmentos e preenche novas linhas na tabela. • Os trabalhadores descobrem

automaticamente os novos fragmentos e criam processadores para lidar com os dados deles. A KCL também distribui os fragmentos no fluxo entre todos os trabalhadores disponíveis e registra

processadores.

- Ao usar a KCL, você deve garantir que o número de instâncias não exceda o número de fragmentos (exceto para fins de espera de falha).
- Um trabalhador pode processar qualquer número de fragmentos.

- Cada fragmento é processado por exatamente um trabalhador KCL e possui exatamente um registro correspondente processador.
- Você pode dimensionar seu aplicativo para usar mais de uma instância do EC2 ao processar um stream. Ao fazer isso, você permite que

os processadores de registro em cada instância trabalhem em paralelo. Quando o trabalhador KCL é iniciado na instância

dimensionada, ele faz o balanceamento de carga com as instâncias existentes, portanto, agora cada instância lida com a mesma quantidade de fragmentos.

- Para ampliar o processamento no seu aplicativo:

- Aumentar o tamanho da instância (porque todos os processadores de registro são executados em paralelo dentro de um processo) • Aumentar o número de instâncias até o número máximo de fragmentos abertos (porque os fragmentos

pode ser processado de forma independente)

- Aumentar o número de fragmentos (o que aumenta o nível de paralelismo)

Referência:

https://docs.aws.amazon.com/streams/latest/dev/kinesis-record-processor-scaling.html

	174



 Associate



Mangueira de dados Kinesis

Ao contrário do Kinesis Data Stream, que pode armazenar dados, o Kinesis Firehose é um serviço que pode fornecer dados de streaming quase em tempo real para um destino especificado, como Amazon S3, Amazon Redshift, Amazon OpenSearch Service ou um serviço personalizado via HTTP. O Kinesis Firehose armazena dados em buffer antes que eles sejam entregues a um destino. Por padrão, o Firehose armazena em buffer os dados recebidos por até 300 segundos (5 minutos) ou 128 MB, o que ocorrer primeiro.

Você não precisa provisionar capacidade para um stream do Kinesis Firehose, pois ele ajusta automaticamente os recursos usados com base no volume de dados de entrada. Você também pode transformar os dados antes da entrega usando uma função Lambda. Isso permite que você modifique e enriqueça facilmente seus dados conforme necessário, sem precisar gerenciar uma infraestrutura de processamento separada.

Referências:

https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html

Amazon Elastic Container Service (ECS)

Função de instância de contêiner do Amazon ECS versus função de execução de tarefa versus função de tarefa

Um cluster ECS é o primeiro recurso criado no Amazon ECS. Você define a infraestrutura subjacente do cluster, o modelo de provisionamento de instâncias (sob demanda ou spot), a configuração da instância (AMI, tipo, tamanho, volumes, par de

chaves, número de instâncias a serem executadas), a rede do cluster e a função da instância do contêiner. A função da instância de contêiner permite que o agente de contêiner do Amazon ECS em execução nas instâncias de contêiner chame ações da API do ECS em seu nome. Essa função anexa a política do IAM ecsInstanceRole.

<!-- image -->



175







Depois de criar seu cluster ECS, uma das primeiras coisas que você fará a seguir é criar sua definição de tarefa. Uma definição de tarefa é como uma folha de especificações para os contêineres Docker que serão executados em suas instâncias ou tarefas do ECS. A seguir estão os parâmetros definidos em uma definição de tarefa: • A imagem

do Docker a ser usada com cada contêiner em sua tarefa • Alocação de

CPU e memória para cada tarefa ou cada contêiner em uma tarefa • O tipo de inicialização a ser usado (EC2 ou Fargate) • O modo de rede do

Docker a ser usado para os contêineres em sua tarefa • A configuração de registro a

ser usada (ponte, host, awsvpc ou nenhum) • Se a tarefa deve continuar a ser executada se o contêiner for concluído ou falhar

• O comando que o contêiner executa quando é iniciado

• Volumes que devem ser montados nos contêineres em uma tarefa

• A função do IAM Task Execution fornece permissões de tarefas para extrair imagens do Docker e publicar

registros de contêiner.

Por último, como os contêineres em execução nas tarefas do ECS podem precisar fazer algumas chamadas de API da AWS, eles precisarão das permissões apropriadas para fazer isso. A função de tarefa fornece permissões do seu contêiner para

<!-- image -->

176

<!-- image -->





faça solicitações de API para serviços autorizados da AWS. Além das permissões padrão do ECS necessárias para executar tarefas e serviços, os usuários do IAM também exigem permissões iam:PassRole para usar funções do IAM para tarefas. Atribuir uma função de tarefa é opcional.

Referências:

https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task\_execution\_IAM\_role.html https://docs.aws.amazon.com/ AmazonECS/latest/developerguide/task-iam-roles.html https:// tutorialsdojo.com/amazon-elastic-container-service-

amazon-ecs/

Amazon OpenSearch Service (sucessor do Amazon Elasticsearch Service)

O Amazon OpenSearch Service é um serviço gerenciado desenvolvido com base no OpenSearch, uma plataforma de análise distribuída

e de código aberto adequada para aplicações como análise de logs, monitoramento de aplicações em tempo real e mecanismos de pesquisa.

O OpenSearch permite que os desenvolvedores executem facilmente uma pesquisa complexa de texto completo e filtrem consultas em documentos com mais eficiência do que os bancos de dados SQL e NoSQL tradicionais.

Uma maneira fácil de transmitir dados para um cluster OpenSearch é por meio do Amazon Kinesis Firehose. Se estiver enviando dados não estruturados, como logs do Apache, você poderá usar o recurso de transformação de dados do Kinesis Firehose, que aproveita o AWS Lambda para converter os logs em um formato exigido pelo seu cluster OpenSearch.

	177



 Associate por

e o

Referências:

https://docs.aws.amazon.com/opensearch-service/ https:// aws.amazon.com/opensearch-service/the-elk-stack/data-ingestion/

Serviços Amazon Elastic Kubernetes (Amazon EKS)

O Amazon EKS permite executar e dimensionar facilmente aplicações Kubernetes na nuvem AWS ou no local.

Kubernetes não é um serviço nativo da AWS. Kubernetes é uma ferramenta de orquestração de contêineres de código aberto usada para implantação e gerenciamento de aplicativos em contêineres. O Amazon EKS apenas cria recursos adicionais sobre esta plataforma, para que você possa executar Kubernetes na AWS com muito mais facilidade.

Se você tem aplicativos em contêineres executados no local e gostaria de migrar para a AWS, mas deseja manter seus aplicativos o mais independentes possível da nuvem, o EKS é uma ótima opção para sua carga de trabalho. Todas as ferramentas e plug-ins com suporte do Kubernetes que você usa localmente também funcionarão no EKS. Você não precisa fazer nenhuma alteração no código ao reformular a plataforma de seus aplicativos.

Um cluster EKS consiste em dois componentes: • O plano de controle do Amazon EKS • E os

nós do Amazon EKS registrados no plano de controle

O plano de controle do Amazon EKS consiste em nós do plano de controle que executam o software Kubernetes, como o etcd e o servidor API do Kubernetes. O plano de controle é executado em uma conta gerenciada pela AWS, e a API Kubernetes é exposta por meio do endpoint EKS do cluster. Os nós do Amazon EKS são executados na sua conta da AWS e se conectam ao plano de

controle do cluster por meio do endpoint do servidor da API e de um arquivo de certificado criado para o cluster.

Referências:

https://docs.aws.amazon.com/eks/latest/userguide/clusters.html https:// aws.amazon.com/premiumsupport/knowledge-center/eks-worker-nodes-cluster/

Amazon Atenas

O Amazon Athena é um serviço de consulta interativo e sem servidor que facilita aos desenvolvedores a análise de dados no Amazon S3 usando SQL, sem a necessidade de provisionar ou gerenciar qualquer infraestrutura.

Para começar a usar o Athena, primeiro você precisa criar um catálogo de dados no AWS Glue, que armazena os metadados dos conjuntos de dados armazenados no S3. Esse catálogo de dados pode ser criado e gerenciado por meio do AWS Management Console ou usando a API Glue.

Otimizando consultas

<!-- image -->



178



 Associate por

e o

Athena oferece suporte a vários formatos de dados, incluindo CSV, JSON, Parquet e ORC. O desempenho de suas consultas pode ser melhorado convertendo seus dados em formatos colunares, como Parquet e ORC. Você também pode implementar o particionamento de dados para limitar a quantidade de dados que precisam ser verificados por uma consulta. Isso pode fazer com que o Athena retorne os resultados da consulta mais rapidamente e com custo reduzido.

Aqui estão alguns exemplos de cenários em que o Amazon Athena poderia ser usado por desenvolvedores:

- Análise de log: um desenvolvedor precisa analisar os dados de log armazenados no S3 para entender o comportamento do usuário e identificar quaisquer problemas de desempenho. Eles podem usar o Athena para executar consultas SQL nos dados de log para extrair informações úteis, como atividade do usuário, taxas de erros e tempos de resposta.
- Inteligência de negócios: um desenvolvedor que trabalha em um projeto de inteligência de negócios precisa analisar grandes

conjuntos de dados armazenados no S3 para identificar tendências e insights que podem informar decisões de negócios. Eles podem usar o Athena para executar consultas nos dados, como calcular métricas como vendas por região ou identificar padrões no comportamento do cliente.

- Migração de dados: um desenvolvedor está trabalhando na migração de dados de um sistema antigo para um novo e precisa validar os dados antes de carregá-los no novo sistema. Eles podem usar o Athena para executar consultas SQL para verificar a integridade e consistência dos dados sem precisar carregar os dados em um banco de dados separado.

Referências:

https://docs.aws.amazon.com/athena/latest/ug/what-is.html https:// aws.amazon.com/blogs/big-data/analyzing-data-in-s3-using -amazon-atena/

<!-- image -->



179







Kit de desenvolvimento de nuvem AWS (CDK)

AWS Cloud Development Kit (CDK) é uma estrutura de desenvolvimento de software de código aberto para criar e gerenciar infraestrutura em nuvem usando linguagens de programação. Ele permite definir a infraestrutura em nuvem em uma linguagem de programação familiar, como TypeScript, JavaScript, C#, .NET, Python ou Go, em vez de escrever modelos CloudFormation em JSON ou YAML.

O principal ponto de venda do AWS CDK é que ele permite que você aplique as habilidades de programação e construções que você já conhece, como loops, condicionais e funções, para construir infraestrutura como código. Ao fazer isso, você pode reduzir significativamente a quantidade de código necessária e criar modelos IaC mais concisos e legíveis. Por outro lado, o modelo CloudFormation tende a ser mais detalhado e requer definição explícita de propriedades de recursos e mapeamentos de relacionamento.

Construções

Uma construção é o seu alicerce para definir a infraestrutura em nuvem. É uma classe que representa um recurso específico ou

grupo de recursos AWS. Por exemplo, uma construção pode ser tão simples quanto um bucket S3 ou algo mais complicado como um grupo de recursos: um cluster Amazon Elastic Container Service (ECS) executando um aplicativo em contêiner com um balanceador de

carga e um grupo de escalonamento automático. As construções do AWS CDK vêm em três níveis:

- Construções L1 (também conhecidas como recursos CFN) - estas são as construções de baixo nível que mapeiam diretamente para componentes que estão disponíveis no CloudFormation. Por exemplo, um grupo de segurança, um bucket S3 ou uma tabela DynamoDB.

- Construções L2 - são construções de nível superior construídas usando construções L1. Essas construções seguem as melhores práticas e padrões de design e vêm com recursos com configurações padrão adequadas, permitindo que você escreva recursos mais rapidamente sem se preocupar muito com os detalhes. Por exemplo, você pode criar uma VPC com sub-redes públicas e privadas em todas as zonas de disponibilidade em apenas duas linhas de código:

importar ec2 = require('@aws-cdk/aws-ec2');

const vpc = new ec2.VpcNetwork(este, 'VPC');

- Construções L3 (também conhecidas como Padrões) - estas são as construções de nível mais alto, são construídas sobre L2 constrói e fornece um nível mais alto de abstração e encapsulamento. Eles representam uma solução completa ou um grupo de recursos que trabalham juntos para atingir um objetivo específico. Arquiteturas construídas em cima

<!-- image -->

180



 Associate por

e o

das construções L3 seguem as melhores práticas e convenções, como o menor privilégio de acesso, o que pode ajudá-lo a melhorar a estrutura e a capacidade de manutenção de seus aplicativos CDK

Referências:

https://aws.amazon.com/blogs/aws/boost-your-infrastructure-with-cdk/ https:// docs.aws.amazon.com/cdk/v2/guide.html

Rota Amazônica 53

O Amazon Route 53 é um serviço web de sistema de nomes de domínio (DNS) altamente disponível e escalável. O DNS traduz nomes de domínio amigáveis (como "tutorialsdojo.com") em endereços IP (como "1.2.3.4"). Quando você insere um nome de domínio em seu navegador, o DNS ajuda seu computador a encontrar o endereço IP correto para que possa se conectar ao servidor correto e carregar o site que você deseja visitar.

O Route 53 funciona de forma semelhante a outros provedores de DNS, como CloudFlare e GoDaddy, com algumas funcionalidades extras. Você não é obrigado a usar o Route 53 como seu provedor de DNS se estiver usando a nuvem AWS, mas como o Route 53 está totalmente integrado a outros serviços da AWS, você sempre pode migrar do seu provedor atual para aproveitar esses benefícios. As funções principais do Route 53 podem ser resumidas em quatro seções:

1. Registro de domínio 2. Gerenciamento de DNS

- Gerenciamento de tráfego
- Monitoramento de disponibilidade

Gerenciamento de DNS

Você pode usar o Route 53 como seu serviço DNS mesmo que seus domínios estejam registrados em um registrador de domínio diferente. Ele é capaz de resolver consultas DNS para alvos em execução dentro e fora da AWS. No

gerenciamento de DNS, tudo começa nas zonas hospedadas. Uma zona hospedada é um contêiner para registros DNS e esses registros contêm informações sobre como você deseja rotear o tráfego para um domínio específico. As zonas hospedadas devem ter o mesmo nome do domínio associado. Existem dois tipos de zonas hospedadas que você pode criar: zona hospedada pública e zona hospedada privada. A principal diferença entre os dois é que, com zonas hospedadas públicas, os

registros armazenados nelas podem ser resolvidos publicamente. Por outro lado, zonas hospedadas privadas contêm registros que só podem ser resolvidos dentro de uma VPC associada, como se você deseja que um registro seja resolvido para uma instância privada do EC2, por exemplo.

Em cada zona hospedada pública, o Route 53 cria automaticamente um registro de servidor de nomes (NS) e um registro de início de autoridade (SOA). Depois, você pode criar registros adicionais nesta zona hospedada para apontar seu domínio e

subdomínios para seus terminais. Se você estiver migrando de um serviço DNS existente, também poderá importar um arquivo de zona

<!-- image -->



181







em vez disso, preencha automaticamente sua zona hospedada. Certifique-se de modificar os registros NS do serviço DNS para usar os servidores de nomes da AWS. Depois de executar as ações acima, basta aguardar a chegada das consultas DNS (e esperar que o TTL do cache DNS expire se os registros já existiam) e elas deverão ser resolvidas para seus alvos designados.

Outros registros versus não outros registros

Existem vários tipos de registros que você pode criar no Route 53, mas os mais comuns que você encontrará são o registro A, o registro AAAA e o registro CNAME. Além disso, cada um desses registros pode ser um registro com ou sem alias.

Registro de alias

• um tipo especial de registro que mapeia um nome de domínio para um recurso da Amazon. • Os recursos suportados incluem: • Um

registro A em sua zona hospedada •

Endpoint do API Gateway • Distribuição do CloudFront •

Elastic Load Balancer •

Ambiente do Elastic Beanstalk • Global Accelerator • Endpoint do

site S3 • Endpoint VPC

• Por exemplo, você pode disponibilizar seu site S3 em seu nome de domínio criando um registro Alias apontando para ele. Observe que o nome de domínio usado no registro (por exemplo, "shop.customtoys.com") deve corresponder exatamente ao nome do seu bucket S3 (por exemplo, "shop.customtoys.com.s3-

website-us-west-2. amazonaws.com"), caso contrário seu site poderá não ser acessível através do seu nome de domínio.

Registros sem alias •

Esses são os registros padrão que mapeiam domínios para endereços IP (um registro para endereços IPv4 e Registro AAAA para IPv6) ou outro domínio (CNAME).

• Não é possível criar um registro CNAME para o domínio raiz ou o ápice da zona. Por exemplo, se você tiver uma zona apex para "coolsite.com", poderá criar registros CNAME para subdomínios como "www.coolsite.com" ou "blog.coolsite.com", mas não poderá criar um registro CNAME para " exemplo.com" em si.

<!-- image -->



182



 Associate por

e o

Gestão de tráfego

Cada registro DNS do Route 53 também tem sua própria política de roteamento. Uma política de roteamento determina como o Route 53 responde às consultas DNS. Diferentes políticas de roteamento alcançam resultados diferentes:

• Política de roteamento simples – Resolve seu DNS para um recurso como ele está.

• Política de roteamento de failover – Use para configurar o failover de roteamento ativo-passivo. Você pode especificar dois registros DNS com o mesmo nome DNS e fazer com que apontem para dois destinos diferentes. Se o seu destino principal ficar indisponível, o Route 53 roteará automaticamente as solicitações recebidas bem-sucedidas para o seu destino secundário.

• Política de roteamento de geolocalização – Use quando desejar rotear o tráfego com base na localização dos seus usuários. Esta política ajuda você a fornecer conteúdo específico de geolocalização aos seus usuários.

• Política de roteamento de geoproximidade – Use quando desejar rotear o tráfego com base na localização dos seus recursos e, opcionalmente, transferir o tráfego de recursos em um local para recursos em outro. • Política de roteamento de

latência – use quando você tiver recursos em várias regiões da AWS e quiser rotear o tráfego para a região que fornece a melhor latência.

• Política de roteamento ponderado – Use para rotear o tráfego para vários recursos proporcionalmente aos pesos que você

atribuir para cada alvo. Quanto maior o peso, maior será a parcela de tráfego que ele recebe. Esta política pode ser usada quando você implanta uma nova versão de um aplicativo e deseja encaminhar apenas uma porcentagem do tráfego de usuários para ela. • Política de roteamento baseada em

IP – use quando quiser rotear o tráfego com base na localização dos seus usuários e saber de onde vem o endereço IP ou o tráfego. •

Política de roteamento de resposta multivalor – use quando quiser que o Route 53 responda a consultas DNS com até

oito registros saudáveis selecionados aleatoriamente. Os usuários que consultam esse tipo de registro podem escolher um alvo da resposta DNS para se conectar.

Algumas dessas políticas de roteamento podem, na verdade, ser usadas juntas, como latência e registros ponderados, para produzir um sistema de roteamento mais complexo.

Referências:

https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resource-record-sets-choosing-alias-non-alias. HTML

https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-configurando.html https://docs.aws.amazon.com/ Route53/latest/DeveloperGuide/dns-failover.html

Firewall de aplicativos da Web da AWS (WAF)

O AWS Web Application Firewall (AWS WAF) ajuda a proteger seus aplicativos web contra explorações comuns da web que podem causar indisponibilidade de aplicativos, comprometer a segurança ou consumir recursos excessivos.

<!-- image -->

183



 Associate



Com o AWS WAF, você pode evitar o trabalho e o esforço de ter que escrever regras do WAF do zero. AWS WAF

oferece uma ampla gama de regras WAF gerenciadas que foram cuidadosamente projetadas para identificar e bloquear um variedade de padrões de ataque comuns. Isso inclui, mas não está limitado a injeção de SQL e scripts entre sites

ataques.

O AWS WAF pode ser integrado ao seguinte serviço AWS:

• Amazon CloudFront

• Balanceador de carga de aplicativos (ALB)

• Gateway de API da Amazon

Declarações de regras do AWS WAF para filtrar o tráfego da web

O AWS WAF usa instruções de regras para filtrar solicitações da web e determinar a ação apropriada (permitir, bloquear ou

contagem) para aplicar a uma solicitação da web que corresponda a uma regra específica. As declarações de regras podem ser simples com apenas um

critério para uma correspondência, ou podem ser complexos e incluir múltiplas declarações combinadas usando AND, OR e NÃO operadores.

No AWS WAF, você pode escolher entre uma variedade de instruções de correspondência para criar regras simples e complexas

declarações:

Declaração de correspondência

Caso de uso

Correspondência geográfica

Permite permitir ou bloquear solicitações da Web com base no país de origem, criando uma ou mais declarações de correspondência geográfica ou geográfica.

Se você usar o recurso de restrição geográfica do CloudFront para bloquear um país, as solicitações de desse país são bloqueados e não são encaminhados ao WAF.

Correspondência de conjunto de IP

Inspeciona o endereço IP de uma solicitação em relação a um conjunto de endereços IP e endereços intervalos que você deseja permitir ou bloquear com seu WAF.

Instrução de regra de correspondência de rótulo

Inspeciona a solicitação de rótulos que foram adicionados por outras regras no mesmo ACL da web.

Conjunto de padrões Regex	Permite comparar padrões regex com um componente especificado de uma solicitação da web.

Restrição de tamanho

Compara o tamanho de um componente de solicitação com uma restrição de tamanho em bytes.

Ataque SQLi	Inspeciona código SQL malicioso em uma solicitação da Web.

Correspondência de strings

Procura uma string correspondente em um componente de solicitação da web. Se uma string correspondente for encontrado, o WAF permite/bloqueia a solicitação.

<!-- image -->



184





 e o

Ataque de script XSS	Inspeciona ataques de script entre sites em uma solicitação da Web.

Baseado em taxa

Rastreia a taxa de solicitações de cada endereço IP de origem e aciona uma ação de regra

em IPs com taxas que ultrapassam um limite. Você pode usar esse tipo de regra para bloquear temporariamente as solicitações de um endereço IP que está enviando solicitações excessivas.

<!-- image -->

A instrução de correspondência de condições IP Match do AWS WAF é altamente valiosa, pois permite bloquear com eficiência solicitações maliciosas provenientes de endereços IP abusivos conhecidos. Outro recurso essencial do AWS WAF é sua regra de limitação de taxa. A regra de limitação de taxa permite limitar o número de solicitações que podem ser enviadas ao seu aplicativo ou serviço a partir de um determinado endereço IP ou grupo de endereços IP.

Digamos que você esteja executando um aplicativo em um grupo de instâncias do EC2 atrás de um ALB, você poderia criar uma regra baseada em taxa que limitasse o número de solicitações dentro de um período de tempo especificado. Por exemplo, você pode definir o limite de 100 solicitações a cada 5 minutos. Em seguida, você criaria uma web ACL que incluísse a regra baseada em taxa e a associaria ao ALB. O AWS WAF intercepta solicitações recebidas e as avalia com base na regra configurada antes de encaminhá-las para o ALB. Se a

contagem de solicitações de um endereço IP exceder o limite, o AWS WAF poderá bloquear solicitações subsequentes desse endereço IP.

Observe que o AWS WAF é capaz de bloquear até 10.000 endereços IP com base em uma regra baseada em taxa. No entanto, em algumas situações em que há mais de 10.000 endereços IP enviando altas taxas de solicitações simultaneamente, pode ser necessário restringir o escopo das solicitações que o AWS WAF rastreia e conta. Para conseguir isso, você pode aninhar uma instrução de redução de escopo dentro da instrução baseada em taxa. Isso permite definir um conjunto específico de condições que devem ser atendidas antes que a regra baseada

em taxa seja aplicada. Por exemplo, você pode definir uma instrução de redução de escopo para contar apenas solicitações provenientes de intervalos de endereços IP específicos ou que contenham determinados parâmetros de cadeia de caracteres de consulta. Ao usar uma instrução de redução de escopo, o AWS WAF contará apenas as solicitações que correspondam aos critérios definidos, o que pode

ajudar a reduzir o número de endereços IP bloqueados com base na regra baseada em taxa.

Referências:

https://docs.aws.amazon.com/waf/latest/developerguide/waf-rules.html https://tutorialsdojo.com/ aws-waf

Amazon MemoryDB para Redis

Uma arquitetura de aplicação de três camadas normalmente inclui uma camada de apresentação, uma camada de aplicação e uma camada de banco de dados, com uma camada de cache frequentemente adicionada na frente do banco de dados para melhorar o desempenho da aplicação. O

	185

<!-- image -->





A camada de cache armazena dados na memória, tornando a recuperação de dados muito mais rápida, em oposição ao armazenamento mais lento baseado em disco, como no caso de um banco de dados como o MySQL.

Ao usar o Amazon MemoryDB for Redis como banco de dados principal, você pode simplificar essa arquitetura eliminando a necessidade de uma camada de cache separada. Com MemoryDB, você armazena dados diretamente na memória, fornecendo latência de leitura de microssegundos, latência de gravação de milissegundos de um dígito e alto rendimento para seu aplicativo.

'Mas a memória é volátil por natureza, então como o Amazon MemoryDB garante que os dados não sejam perdidos em caso de falhas?', você pode perguntar. O Amazon MemoryDB for Redis oferece durabilidade, consistência e capacidade de recuperação de dados, mantendo diversas cópias dos seus dados em diversas zonas de disponibilidade. MemoryDB for Redis também oferece recursos como failover automático, backups e replicação. Além disso, o MemoryDB for Redis é totalmente compatível com o protocolo Redis, portanto pode ser usado com clientes e aplicativos Redis existentes com alterações mínimas.

Referências:

https://aws.amazon.com/memorydb/faqs https://

aws.amazon.com/blogs/aws/introduzindo-amazon-memorydb-for-redis-a-redis-compatível-durable-in-m serviço de banco de dados emory/

AWS AppConfig

AWS AppConfig é um serviço gerenciado que ajuda os desenvolvedores a gerenciar e implantar configurações de aplicativos. Ele fornece um local centralizado para gerenciar configurações de aplicativos, que pode ser acessado por vários aplicativos e serviços.

AppConfig pode ser integrado aos seguintes serviços AWS:

• Extensão AWS Lambda

• AWS Secrets Manager •

Amazon Elastic Container Service (Amazon ECS) • Elastic Kubernetes Service (Amazon EKS) • AWS CodePipeline

Para usar o AWS AppConfig, os desenvolvedores primeiro precisam definir as configurações que desejam gerenciar. Isso pode incluir configurações de aplicativos, sinalizadores de recursos ou quaisquer outros dados de configuração. Os desenvolvedores podem usar o console AppConfig ou a AWS CLI para criar um perfil de configuração, que define os dados de configuração e os aplicativos ou serviços que podem acessá-los.

	186



 Associate por

e o

Após a criação do perfil de configuração, os desenvolvedores podem criar uma estratégia de implantação, que especifica como e quando implementar alterações nos dados de configuração. As estratégias de implantação podem ser baseadas em vários fatores, como a porcentagem de usuários que devem receber as alterações, a hora do dia em que as alterações devem ser implementadas ou a localização dos

usuários.

Referências:

https://aws.amazon.com/blogs/mt/how-cyberark-implements-feature-flags-with-aws-appconfig/ https:// docs.aws.amazon.com/appconfig/latest/userguide/ o que é appconfig.html

AWS AppSync

AWS AppSync é um serviço totalmente gerenciado que simplifica o processo de criação e implantação de APIs GraphQL.

Com o AWS AppSync, você pode conectar e combinar dados de diversas fontes de dados, como tabelas DynamoDB, funções Lambda, Amazon OpenSearch Service, bancos de dados Aurora e até mesmo fontes não AWS por meio de APIS HTTP. Você pode escrever lógica de negócios usando modelos de código pré-construídos para padrões comuns de API GraphQL.

Por que GraphQL em vez de descanso?

Ao contrário das APIs REST tradicionais, com GraphQL, os clientes podem especificar os dados exatos de que precisam e como eles devem ser formatados, reduzindo a busca excessiva ou insuficiente de dados. GraphQL também permite definir um único esquema que

descreve toda a API, facilitando o gerenciamento e a evolução da API ao longo do tempo.

Principais recursos do AppSync:

• Edição avançada de esquema GraphQL por meio do console AWS AppSync, incluindo GraphQL automático geração de esquema de

• Suporte do DynamoDB para JavaScript e TypeScript para escrever lógica de negócios que acessa fontes de dados • Armazenamento em cache de dados eficiente para otimizar o desempenho da API •

Integração com grupos de usuários do Amazon Cognito para controle de acesso refinado em nível por campo

Referências:

https://docs.aws.amazon.com/appsync/latest/devguide/what-is-appsync.html https://aws.amazon.com/ blogs/architecture/what-to-consider-when-modernizing-apis -com-graphql-on-aws/

<!-- image -->



187







Gerente de sistemas AWS

AWS Systems Manager, ou SSM, é um conjunto de serviços que fornece visibilidade e controle de sua nuvem e infraestrutura local. O SSM tem vários recursos que você pode aproveitar, a saber: • AWS Systems Manager Explorer • AWS

Systems Manager OpsCenter • AWS Systems Manager Incident Manager • AWS Systems

Manager Application Manager • AWS Systems Manager AppConfig • Armazenamento de parâmetros do AWS Systems Manager • AWS Systems Manager

Change Manager • Automação do AWS Systems Manager • Janelas de manutenção do AWS Systems Manager • Gerenciador de frota do AWS Systems Manager • Conformidade do AWS Systems Manager • Inventário do AWS Systems Manager • Gerenciador de sessão do  AWS  Systems  Manager  •  Comando de execução do AWS Systems Manager • Gerenciador de estado do AWS Systems Manager • AWS Systems Manager Patch Manager • Distribuidor do AWS Systems Manager • ...e muitos outros submódulos.

O AWS Systems Manager também possui um agente SSM, assim como um agente CloudWatch ou DataSync. Por meio desse agente SSM, o serviço Systems Manager pode gerenciar instâncias do Amazon EC2 e servidores locais.

O AWS Systems Manager Explorer é basicamente um painel de operações personalizável que permite explorar e visualizar vários relatórios técnicos relacionados aos seus recursos da AWS. O módulo Explorer mostra uma visão agregada dos dados de operações para suas contas da AWS e entre regiões da AWS. Esses dados são chamados de "OpsData" no AWS Systems Manager Explorer. O OpsData contém os metadados relevantes sobre seus dispositivos Edge, servidores locais, máquinas virtuais e instâncias do Amazon EC2 em seu ambiente híbrido.

Ele também inclui informações fornecidas por outros recursos do Systems Manager, como conformidade de associação do State Manager e detalhes de conformidade de patch do Patch Manager. O Systems Manager Explorer contém informações de suporte a serviços da AWS, bem como AWS Compute Optimizer, AWS Support AWS Config e AWS Trusted Advisor.

O Patch Manager automatiza o processo de aplicação de patches no sistema operacional de suas instâncias EC2 e servidores locais usando linhas de base de patches predefinidas e personalizadas. Você pode definir uma janela de manutenção agendada para

executar as atividades de correção para reduzir qualquer impacto operacional por meio do módulo Janela de Manutenção. Com o Estado

<!-- image -->



188

<!-- image -->





Manager, você pode controlar os detalhes de configuração ou o "estado" de seus recursos, como configurações

de servidor, hardware virtualizado e configurações de firewall. Você pode até associar manuais do Ansible, receitas do Chef, módulos do PowerShell e outros documentos do SSM aos seus recursos.

O Systems Manager Parameter Store fornece armazenamento e gerenciamento centralizados de seus "parâmetros", como senhas, strings de banco de dados, Amazon Machine Image IDs, códigos de licença, variáveis de ambiente, etc.

Você pode armazenar o parâmetro como um tipo de dados SecureString para instruir o SSM a criptografá-lo automaticamente usando uma chave mestra do cliente (CMK) no AWS KMS. Seu módulo OpsCenter fornece um local central onde você pode visualizar, investigar e resolver problemas operacionais relacionados aos seus recursos da AWS.

Este módulo também agrega e padroniza problemas operacionais, ao mesmo tempo que fornece dados contextualmente relevantes para ajudá-lo a diagnosticar e corrigir seus sistemas.

Gerenciador de certificados AWS

O AWS Certificate Manager (AWS ACM) é um serviço que permite provisionar, gerenciar e implantar facilmente certificados públicos e privados de Secure Sockets Layer/Transport Layer Security (SSL/TLS) para uso com serviços da AWS e seus recursos internos conectados. O serviço AWS ACM gerencia o ciclo de vida dos certificados; desde a criação, armazenamento, implantação e gerenciamento de renovações de serviços da AWS, como Amazon CloudFront, Amazon API Gateway e Elastic Load Balancing, para citar alguns. Ele também permite criar certificados privados para seus recursos internos e gerenciar o ciclo de vida do certificado centralmente. Certificados públicos e privados provisionados por meio do AWS Certificate Manager para uso com serviços integrados ao ACM são gratuitos.

Há também um serviço separado chamado AWS Private Certificate Authority (AWS Private CA) que está relacionado ao AWS Certificate Manager. ACM e AWS Private CA têm funções específicas no processo de criação e gerenciamento de certificados digitais que são usados para identificar recursos e proteger as comunicações de rede que passam pela Internet pública, em redes privadas e na nuvem. O serviço AWS Private CA permite criar certificados privados personalizáveis para uma ampla variedade de cenários, inclusive para serviços da AWS como ACM, Amazon Managed Streaming for Apache Kafka (MSK), IAM Roles Anywhere e Amazon Elastic Kubernetes Service (EKS). Todos esses serviços podem aproveitar certificados privados de CA privada, algo que o serviço AWS ACM não pode fornecer totalmente. A AWS Private CA também oferece suporte à criação de certificados privados para dispositivos de Internet das Coisas (IoT), sistemas externos, usuários corporativos e outros serviços.

	189

<!-- image -->





COMPARAÇÃO DE SERVIÇOS AWS

	190





S3 Standard vs S3 Standard-IA vs S3 One Zone-IA vs S3 Intelligent Tiering

Notas Adicionais:

• Os dados armazenados na classe de armazenamento S3 One Zone-IA serão perdidos em caso de destruição de

AZ. • O S3 Standard-IA custa menos que o S3 Standard em termos de preço de armazenamento, mas ainda oferece a mesma alta durabilidade, rendimento e baixa latência do S3 Standard.

• O S3 One Zone-IA tem custo 20% menor que o Standard-IA.

• É recomendado usar multipart upload para objetos maiores que 100 MB.

Os volumes SSD IOPS provisionados (io1, io2) são projetados para atender às necessidades de cargas de trabalho com

uso intensivo de E/S, principalmente cargas de trabalho de banco de dados, que são sensíveis ao desempenho e à consistência do armazenamento. Ao contrário do gp2, que usa um modelo de bucket e crédito para calcular o desempenho, um volume io1 permite especificar uma taxa de IOPS consistente ao criar o volume, e o Amazon EBS entrega dentro de 10% do desempenho de IOPS provisionado 99,9% do tempo durante um período. determinado ano. Provisioned IOPS SSD io2 é uma atualização do Provisioned IOPS

SSD io1. Ele oferece maior durabilidade de 99,999% e maior proporção de IOPS por GiB com 500 IOPS por GiB, tudo pelo mesmo custo dos volumes io1.

<!-- image -->

191

 Associate



<!-- image -->

Tipo de volume

GP3

GP2

isto2

io1

Descrição

SSD de uso geral

volume que equilibra

desempenho de preço para

Uma grande variedade de

transacional

cargas de trabalho

SSD de uso geral

volume que equilibra

desempenho de preço para

Uma grande variedade de

transacional

cargas de trabalho

Alta performance Volume SSD projetado

para negócios críticos sensível à latência formulários

Alta performance Volume SSD projetado

para sensível à latência transacional

cargas de trabalho

Casos de uso

desktops virtuais, solteiro tamanho médio

bancos de dados de instância

como MSFT SQL

Servidor e banco de dados Oracle,

baixa latência

aplicativos interativos, desenvolvimento

& teste, volumes de inicialização

Volumes de inicialização,

baixa latência

aplicativos interativos, desenvolvimento

& teste

Cargas de trabalho que

exigir

submilissegundo

latência e

IOPS sustentado

desempenho ou mais de 64.000 IOPS ou

- MiB/s de

Taxa de transferência

Cargas de trabalho que

exigem sustentação Desempenho IOPS ou mais de 16.000

IOPS e

Uso intensivo de E/S

cargas de trabalho de banco de dados

Tamanho do volume

1 GB – 16 TB

1 GB – 16 TB

4 GB – 16 TB

4 GB – 16 TB

Durabilidade

99,8% - 99,9%

durabilidade

99,8% - 99,9%

durabilidade

99,999%

99,8% - 99,9%

Máximo de IOPS/Volume

16.000

16.000

64.000

64.000

Rendimento máximo / Volume

Máximo de IOPS/instância

Máximo de IOPS/GB

Rendimento máximo/

Instância

Latência

milissegundo

milissegundo

milissegundo

milissegundo

Multi-anexação

Não

Não

Sim

Sim

Tipo de volume

st1

sc1

Descrição

Volume HDD de baixo custo projetado para

Armazenamento orientado ao rendimento para dados



192

 Associate



acessado com frequência,

cargas de trabalho com alto rendimento

que é raramente acessado

Cenários onde o armazenamento mais baixo custo é importante

Casos de uso

Big data, data warehouses, log

em processamento

Dados mais frios que exigem menos varreduras por dia

| Tamanho do volume                      | 125 GB – 16 TB                | 125 GB – 16 TB                |
|----------------------------------------|-------------------------------|-------------------------------|
| Durabilidade                           | 99,8% - 99,9% de durabilidade | 99,8% - 99,9% de durabilidade |
| Máximo de IOPS/Volume                  | 500                           | 250                           |
| Taxa de transferência/volume máximo    | 500MB/s                       | 250MB/s                       |
| Máximo de IOPS/instância               | 260.000                       | 260.000                       |
| Máximo de IOPS/GB                      | N / D                         | N / D                         |
| Taxa de transferência máxima/instância | 7.500MB/s                     | 7.500MB/s                     |
| Multi-anexação                         | Não                           | Não                           |

<!-- image -->



193

<!-- image -->





RDS versus DynamoDB

	194

<!-- image -->



	195





Notas Adicionais:

- O DynamoDB possui suporte integrado para transações

ACID. • O DynamoDB usa expressões de filtro porque não oferece suporte a consultas

complexas. • As implantações Multi-AZ para os mecanismos MySQL, MariaDB, Oracle e PostgreSQL utilizam replicação física síncrona. As implantações Multi-AZ para o mecanismo do SQL Server usam

replicação lógica síncrona.

<!-- image -->

196





Índice Secundário Global vs Índice Secundário Local

Um índice secundário é uma estrutura de dados que contém um subconjunto de atributos de uma tabela, juntamente com uma chave alternativa para dar suporte a operações de consulta. Uma tabela do Amazon DynamoDB pode ter vários índices secundários.

Índice secundário global	Índice secundário local

Definição

Um índice com uma chave de partição e uma chave de

classificação que pode ser diferente daquelas da tabela base.

Um índice que possui a mesma chave

de partição da tabela base, mas uma chave de classificação diferente.

Extensão da consulta

As consultas no índice podem abranger todos os dados da tabela base, em todas as partições.

Cada partição de um índice secundário local tem como escopo uma partição da tabela base

que possui o mesmo valor de chave de partição.

Chave primária Esquema

A chave de partição e, opcionalmente, a chave de classificação

Deve ser a chave de partição e a chave de classificação

Chave de partição Atributos

Qualquer atributo da tabela base do tipo string, número ou binário.

Deve ter o mesmo atributo da chave de partição da tabela base.

Atributos de chave de classificação Qualquer atributo de tabela base do tipo string, número ou binário.

Qualquer atributo da tabela base do tipo string, número ou binário.

Valores-chave

Não precisa ser único

O valor da chave de classificação não precisa ser

exclusivo para um determinado valor de chave de partição.

Restrições de tamanho

Por chave de partição Valor

Sem restrição.

Para cada valor de chave de partição, o tamanho total de todos os itens indexados deve

ser de 10 GB ou menos.

Operações de índice

- Pode ser criado durante a criação de uma tabela. • Pode ser

criado em uma tabela existente. • Pode ser excluído

de uma tabela existente.

- Pode ser criado durante a criação de uma tabela.

Consistência de leitura para consultas

Suporta consistência eventual apenas de atualizações e exclusões assíncronas

Você pode escolher consistência eventual ou consistência forte.

Provisionado

Cada índice secundário global tem suas próprias consultas ou varreduras em um local

<!-- image -->



197





Taxa de transferência

Consumo

configurações de taxa de transferência provisionadas para atividades de leitura e gravação que você precisa especificar. Consultas ou verificações em

um índice secundário global consomem unidades de capacidade do índice, não da tabela base.

Este também é o caso das atualizações do índice secundário global devido a gravações na tabela.

o índice secundário consome unidades de capacidade de leitura da tabela base.

Quando você grava em uma tabela e seus índices secundários locais são

atualizados, essas atualizações consomem

unidades de capacidade de gravação da tabela base.

Projetado Atributos

Com consultas ou verificações de índice secundário global, você só pode solicitar os atributos que são projetados no índice.

Se você consultar ou verificar um índice secundário local, poderá solicitar

atributos que não são projetados no índice. O DynamoDB buscará

automaticamente esses atributos da tabela.

Limite de índice (padrão)

20 índices

5 índices por tabela

Cálculo da capacidade de leitura/gravação do índice secundário global (modo de taxa de transferência provisionada)

- Leituras eventualmente consistentes consomem ½ unidade de capacidade de leitura. Portanto, cada consulta pode recuperar até

8 KB de dados por unidade de capacidade (4 KB x 2). O tamanho máximo dos resultados retornados por uma operação de consulta é de 1 MB.

- O custo total da taxa de transferência provisionada para uma gravação consiste na soma das unidades de capacidade de gravação consumidos pela gravação na tabela base e aqueles consumidos pela atualização dos índices secundários globais. Se

uma gravação em uma tabela não exigir uma atualização de índice secundário global, nenhuma capacidade de gravação será consumida do índice.

- O custo de uma operação de gravação depende dos fatores ff (assumindo tamanho de item de até 1 KB):
    - Se você gravar um novo item na tabela que define um atributo indexado ou atualizar um existente

item para definir um atributo indexado anteriormente indefinido, uma operação de gravação é necessária para colocar o item no índice.

- Se uma atualização na tabela alterar o valor de um atributo-chave indexado, serão necessárias duas gravações, uma para excluir o item anterior do índice e outra gravação para colocar o novo item no índice.

- Se um item estava presente no índice, mas uma gravação na tabela fez com que o atributo indexado fosse excluído, uma gravação será necessária para excluir a projeção do item antigo do índice. • Se um item não estiver presente no

índice antes ou depois da atualização do item, não há nenhum item adicional custo de gravação para o índice.

- Se uma atualização na tabela alterar apenas o valor dos atributos projetados no esquema de chave do índice, mas não alterar o valor de nenhum atributo-chave indexado, será necessária uma gravação para atualizar os valores dos atributos projetados no índice.

<!-- image -->

198





Cálculo da capacidade de leitura/gravação do índice secundário local (modo de taxa de transferência provisionada)

• Uma consulta de índice pode usar leituras eventualmente consistentes ou fortemente consistentes. Um fortemente

a leitura consistente consome uma unidade de capacidade de leitura; uma leitura eventualmente consistente consome apenas metade disso. O número de unidades de capacidade de leitura é a soma de todos os tamanhos de atributos projetados em todos os itens retornados (do índice e da tabela base), e o resultado é então arredondado para o próximo múltiplo de 4 KB.

O tamanho máximo dos resultados retornados por uma operação de consulta é de 1 MB. • O custo

total de transferência provisionado para uma gravação é a soma das unidades de capacidade de gravação consumidas pela gravação na tabela e aquelas consumidas pela atualização dos índices secundários locais. • O custo de

uma operação de gravação depende dos fatores ff (assumindo tamanho de item de até 1 KB):

• Se você gravar um novo item na tabela que define um atributo indexado ou atualizar um existente

item para definir um atributo indexado anteriormente indefinido, uma operação de gravação é necessária para colocar o item no índice.

• Se uma atualização na tabela alterar o valor de um atributo-chave indexado, serão necessárias duas gravações, uma para excluir o item anterior do índice e outra gravação para colocar o novo item no índice.

• Se um item estava presente no índice, mas uma gravação na tabela fez com que o atributo indexado fosse excluído, uma gravação será necessária para excluir a projeção do item antigo do índice. • Se um item não estiver presente no

índice antes ou depois da atualização do item, não há nenhum item adicional custo de gravação para o índice.

<!-- image -->

199

<!-- image -->





Serviços de contêiner EC2 ECS vs Lambda

	200





Elastic Beanstalk x CloudFormation x OpsWorks x CodeDeploy

<!-- image -->

- O AWS Elastic Beanstalk torna tudo ainda mais fácil

para que os desenvolvedores implantem e gerenciem rapidamente aplicativos na Nuvem AWS. Os desenvolvedores simplesmente fazem upload de seus aplicativos e o Elastic Beanstalk gerencia automaticamente os detalhes de implantação de provisionamento de capacidade, balanceamento de carga, escalonamento

- O AWS CloudFormation é um serviço que oferece aos

desenvolvedores e empresas uma maneira fácil de criar uma coleção de recursos relacionados da AWS e

provisioná-los de maneira ordenada e previsível.

Isso normalmente é conhecido como

“infraestrutura como código”.

- A principal diferença entre o CloudFormation e o Elastic Beanstalk é que o CloudFormation lida mais com a infraestrutura da

automático e monitoramento da integridade dos aplicativos

• O AWS CloudFormation

normalmente para aqueles que desejam implantar e gerenciar seus aplicativos em minutos na Nuvem AWS, sem se preocupar com a infraestrutura subjacente.

- O AWS Elastic Beanstalk oferece suporte às seguintes linguagens e pilhas de desenvolvimento: •

Apache Tomcat para aplicativos Java • Servidor HTTP Apache para aplicativos PHP • Servidor

HTTP Apache

para aplicativos Python • Servidor HTTP Apache ou

Nginx para aplicativos Node.js • Passenger ou Puma para aplicativos

Ruby • Aplicativos Microsoft IIS para .NET

- Java SE •

Docker • Go • O Elastic Beanstalk também oferece suporte ao

controle de versão

de implantação. Ele mantém uma cópia de implantações mais antigas para que seja fácil para o desenvolvedor

reverter quaisquer alterações feitas no aplicativo.

apresenta dois

conceitos: •

O modelo, um arquivo baseado em

texto no formato JSON ou YAML que

descreve todos os recursos e configurações da

AWS que você precisa implantar para executar seu aplicativo. • A pilha,

que é o conjunto de recursos da AWS criados e

gerenciados como uma única unidade

quando o AWS CloudFormation instancia um modelo. • O CloudFormation também

oferece

suporte a um recurso de reversão por meio de controles de versão de modelo.

Quando você tenta atualizar sua pilha, mas a implantação falha no meio do caminho, o CloudFormation reverterá automaticamente as alterações para seus estados de funcionamento anteriores.

- CloudFormation oferece suporte ao Elastic Beanstalk ambientes de aplicativos. Isso permite, por exemplo, criar e gerenciar um aplicativo hospedado no AWS Elastic Beanstalk junto com um banco de dados RDS para armazenar os dados do aplicativo.

- O AWS CloudFormation pode ser usado para

inicialize os softwares Chef (servidor e cliente) e Puppet

(mestre e cliente) em suas instâncias EC2. • O CloudFormation

também oferece suporte ao OpsWorks.







Você pode modelar componentes do OpsWorks (pilhas, camadas, instâncias e aplicativos) dentro de modelos do CloudFormation e provisioná-los

como pilhas do CloudFormation.

Isso permite documentar, controlar versões e compartilhar sua configuração do OpsWorks.

- O AWS CodeDeploy é um complemento recomendado do CloudFormation para gerenciar implantações e atualizações de aplicativos.

- AWS OpsWorks é um serviço de

gerenciamento de configuração que fornece instâncias gerenciadas do Chef e do Puppet. O OpsWorks permite usar Chef e Puppet para automatizar a forma como

os servidores são configurados, implantados e gerenciados em suas instâncias EC2 ou ambientes de computação locais.

- O OpsWorks oferece três serviços: • Chef Automate • Puppet

Enterprise • OpsWorks Stacks • O OpsWorks for

Puppet Enterprise permite usar o Puppet para automatizar o modo como os nós são configurados,

implantados e gerenciados, sejam eles instâncias do EC2 ou dispositivos locais. • O OpsWorks for

Chef

Automate permite criar servidores Chef gerenciados pela AWS e usar o Chef DK e outras ferramentas do Chef para gerenciá-los. • O OpsWorks Stacks permite criar pilhas

que ajudam a gerenciar recursos de nuvem em grupos especializados chamados camadas. Uma camada representa um conjunto de instâncias

EC2 que atendem a um propósito específico. As camadas dependem de receitas do Chef para lidar com tarefas como instalação de pacotes em instâncias,

implantação de aplicativos e execução de scripts. • Comparado ao

CloudFormation, OpsWorks

concentra-se mais na orquestração e configuração de software e menos no que e como a AWS

- O AWS CodeDeploy é um serviço que

coordena implantações de aplicativos em instâncias EC2 e instâncias executadas no local. Isso

facilita o lançamento rápido de novos recursos,

ajuda a evitar tempo de inatividade durante a implantação e lida com a complexidade da atualização de seus aplicativos.

- Diferentemente do Elastic Beanstalk, o CodeDeploy não lida automaticamente com provisionamento, escalabilidade e monitoramento de capacidade.
- Ao contrário do CloudFormation e do OpsWorks, CodeDeploy não lida com configuração e orquestração de infraestrutura. • O AWS CodeDeploy

é um serviço básico focado em ajudar os desenvolvedores a implantar e atualizar o software em qualquer instância, incluindo instâncias EC2 e instâncias executadas no local. AWS Elastic Beanstalk e

AWS OpsWorks são soluções completas de gerenciamento de aplicações. • Você cria um arquivo de configuração de

implantação para especificar como as implantações serão realizadas. • O CodeDeploy complementa

bem o CloudFormation ao implantar código em infraestrutura que é provisionada e gerenciada com o CloudFormation.

<!-- image -->

202





recursos são adquiridos.

Notas Adicionais:

• Elastic Beanstalk, CloudFormation ou OpsWorks são particularmente úteis para o método de implantação azul-verde, pois fornecem uma maneira simples de clonar a pilha de aplicativos em execução.

• CloudFormation e OpsWorks são mais adequados para AMIs pré-preparadas. •

CodeDeploy e OpsWorks são mais adequados para realizar atualizações de aplicativos no local. Para

atualizações descartáveis, você pode configurar um ambiente clonado com Elastic Beanstalk, CloudFormation e OpsWorks.

Referências:

https://aws.amazon.com/CloudFormation/faqs/ https:// aws.amazon.com/elasticbeanstalk/faqs/ https://

d1.awsstatic.com/whitepapers/overview-of-deployment-options- on-aws.pdf https://aws.amazon.com/

about-aws/whats-new/2014/03/03/aws-CloudFormation-supports-aws-opsworks/ https://aws.amazon.com/codedeploy /perguntas frequentes/

<!-- image -->



203

<!-- image -->





Grupo de segurança vs NACL

	204





Sua VPC possui um grupo de segurança padrão com as seguintes regras:

- Permita o tráfego de entrada de instâncias atribuídas ao mesmo grupo de segurança.
- Permita todo o tráfego de saída IPv4 e IPv6 se você tiver alocado um bloco CIDR IPv6.

Sua VPC tem uma Network ACL padrão com as seguintes regras:

- Permite todo o tráfego IPv4 de entrada e saída e, se aplicável, tráfego IPv6.
- Cada rede ACL também inclui uma regra não modificável e não removível cujo número de regra é um

asterisco. Esta regra garante que se um pacote não corresponder a nenhuma das outras regras numeradas, ele será negado.

<!-- image -->

205

<!-- image -->





Balanceador de carga de aplicativo versus balanceador de carga de rede versus balanceador de carga de gateway

	206





Recursos comuns entre os balanceadores de carga:

• Possui recursos de verificação de integridade da instância • Possui monitoramento integrado do CloudWatch

<!-- image -->

207

<!-- image -->





- Recursos de registro • Suporta failover zonal •

Suporta drenagem de conexão •

Suporta balanceamento de carga entre zonas (distribui uniformemente o tráfego entre instâncias registradas em AZs)

- Políticas de permissão de IAM baseadas em recursos • Permissões de IAM

baseadas em tags • Aderência de fluxo - todos os pacotes são enviados para um destino e retornam o tráfego proveniente do mesmo alvo.

	208





CloudTrail x CloudWatch

- CloudWatch é um serviço de monitoramento de recursos e aplicativos da AWS. CloudTrail é um serviço web que registra atividades de API em sua conta AWS. Ambas são ferramentas de monitoramento úteis na AWS. • Por padrão, o

CloudWatch oferece monitoramento básico gratuito para seus recursos, como instâncias EC2, volumes EBS e instâncias de banco de dados RDS. O CloudTrail também é habilitado por padrão quando você cria seu AWS

conta.

- Com o CloudWatch, você pode coletar e rastrear métricas, coletar e monitorar arquivos de log e definir alarmes.

O CloudTrail, por outro lado, registra informações sobre quem fez uma solicitação, os serviços utilizados, as ações executadas, os parâmetros das ações e os elementos de resposta retornados pelo serviço AWS.

Os logs do CloudTrail são armazenados em um bucket do S3 ou em um grupo de logs do CloudWatch Logs especificado

por você. • Você pode ativar o monitoramento detalhado dos seus recursos da AWS para enviar mais dados de métricas ao CloudWatch frequentemente, com um custo adicional.

- O CloudTrail oferece uma cópia gratuita dos logs de eventos de gerenciamento para cada região da AWS. Os eventos de gerenciamento incluem operações de gerenciamento realizadas em recursos da sua conta da AWS, como quando um usuário faz login na sua conta. Os eventos de dados de registro são cobrados. Os eventos de dados incluem operações de recurso executadas no próprio recurso ou dentro dele, como atividade de API em nível de objeto S3 ou atividade de execução de função Lambda. • O

CloudTrail ajuda a garantir conformidade e padrões regulatórios. • O CloudWatch Logs

informa sobre logs de aplicativos, enquanto o CloudTrail Logs fornece informações específicas sobre o que ocorreu em sua conta AWS.

- O CloudWatch Events é um fluxo quase em tempo real de eventos do sistema que descreve alterações nos recursos da AWS. O CloudTrail se concentra mais nas chamadas de API da AWS feitas em sua conta da AWS.
- Normalmente, o CloudTrail entrega um evento dentro de 15 minutos após a chamada da API. O CloudWatch fornece dados métricos em períodos de 5 minutos para monitoramento básico e períodos de 1 minuto para monitoramento detalhado. O agente do CloudWatch Logs enviará dados de log a cada cinco segundos por padrão.

<!-- image -->

209





CONSIDERAÇÕES FINAIS E DICAS

Graças às inovações trazidas pela nuvem, desenvolvedores como você podem trabalhar com menos transtornos e mais flexibilidade. É um momento emocionante para estar no campo do desenvolvimento, não apenas para desenvolvedores experientes, mas também para aqueles que são novos no setor. Acreditamos que existem práticas de desenvolvimento de software que devem continuar a ser aplicadas mesmo após a mudança de um ambiente local para a AWS. Embora a AWS compartilhe o que acredita serem as melhores práticas para o desenvolvimento de aplicações em seu ambiente, o principal benefício da nuvem é ter a liberdade de implementar o que você acha que é melhor para suas aplicações.

Além disso, há menos preocupação com a experimentação porque os recursos da AWS são substituíveis e devem ser tratados como tal. Isso lhe dá a oportunidade de descobrir o que funciona melhor para suas cargas de trabalho e implementá-

lo de maneira econômica.

Esperamos que nossas folhas de dicas tenham ajudado muito em sua análise para o exame AWS Certified Developer Associate. Este certificado AWS é procurado por desenvolvedores de todo o mundo, pois prova que eles possuem o conhecimento e as habilidades para desenvolver aplicativos adequadamente na AWS. Passar em um exame de certificação

da AWS não é uma tarefa fácil e a comunidade da AWS celebra os aprovados com orgulho e alegria. Nós da Tutorialsnos dedicamos a ajudar você a alcançar esses resultados também. Criamos nosso conteúdo especificamente para ajudá-lo a se preparar para os exames e equipá-lo com informações importantes para que você possa ter sucesso em sua função.

Escrevemos blogs, guias, folhas de dicas e exames práticos que também são constantemente atualizados com base em nossas experiências e no feedback de nossos alunos. Seu feedback é muito importante para nós, pois nos ajuda a melhorar nosso conteúdo e servir melhor a comunidade.

E com isso, nós da Tutorialsagradecemos por nos apoiar através deste eBook. Se você deseja validar o que aprendeu até agora, agora é um ótimo momento para conferir também nosso exame prático AWS Certified Developer Associate. Você também pode experimentar a versão de amostra gratuita de nosso curso de teste prático completo aqui. Ele preencherá as lacunas de seu conhecimento que você desconhece e lhe dará uma noção do ambiente real do exame. Dessa forma, você saberá o que esperar do exame real e poderá acompanhar melhor as questões. Se você tiver quaisquer problemas, preocupações ou comentários construtivos sobre nosso e-book, sinta-se à vontade para nos contatar em

support@tutorialsdojo.com.

Boa sorte com seu exame e adoraríamos receber sua resposta.

Seus parceiros de aprendizagem,

Jon , o e a equipe do Tutorials Dojo

<!-- image -->



210





SOBRE OS AUTORES

(10x certificado pela AWS)

Nascido e criado nas Filipinas, Jon é cofundador do Tutorials Dojo. Agora baseado em Sydney, Austrália, ele tem mais de uma década de experiência diversificada em bancos, serviços financeiros e telecomunicações. Ele é 10x certificado pela AWS, um AWS Community Builder e trabalhou com vários serviços em nuvem, como Google Cloud e Microsoft Azure.

Jon é apaixonado pelo que faz e dedica muito tempo criando cursos educacionais. Ele deu seminários de TI gratuitamente em diferentes universidades nas Filipinas e lançou sites educacionais usando seu próprio dinheiro e sem qualquer financiamento externo.

o (5x AWS Certified)

Carlo é engenheiro de nuvem e criador de conteúdo no Tutorials Dojo. Ele também é membro do construtor da comunidade AWS e possui 5 certificações AWS. Carlo é especialista em construir e automatizar soluções na Amazon Web Services Cloud.

<!-- image -->

211