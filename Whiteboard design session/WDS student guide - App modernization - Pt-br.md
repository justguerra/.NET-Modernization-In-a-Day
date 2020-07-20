![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
App modernization
</div>

<div class="MCWHeader2">
App Modernization .Net Sessão de Whiteboard - Guia do Estudante
</div>

<div class="MCWHeader3">
Fevereiro 2020
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2020 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Conteúdo**

<!-- TOC -->

- [App Modernization Sessão de Whiteboard Guia do Estudante](#app-modernization-sessão-de-whiteboard-guia-do-estudante)
  - [Resumo e objetivos do Aprendizado](#resumo-e-objetivos-do-aprendizado)
  - [Step 1: Revise o estudo de caso do cliente](#step-1-revise-o-estudo-de-caso-do-cliente)
    - [Situação do Cliente](#situação-do-cliente)
    - [Necessidades do Cliente](#necessidades-do-cliente)
    - [Dúvidas do Cliente](#dúvidas-do-cliente)
    - [Infográfico com cenários comuns](#infográfico-com-cenãrios-comuns)
  - [Passo 2: Defina a solução de prova de conceito ](#passo-2-defina-a-solução-de-prova-de-conceito)
  - [Passo 3: apresente a solução](#passo-3-apresente-a-solução)
  - [Conclusão](#conclusão)
  - [Referências-adicionais](#referências-adicionais)

<!-- /TOC -->

# App Modernization Sessão de Whiteboard Guia do Estudante

## Resumo e objetivos do Aprendizado

Nesta sessão de whiteboard, você trabalha com um grupo para projetar uma solução para modernizar aplicativos e infraestrutura locais herdados, aproveitando os serviços em nuvem. Como parte do esforço de modernização, os aprimoramentos de aplicativos são adicionados usando uma mistura de serviços da Web e móveis, todos protegidos pelo Azure Active Directory.

No final desta sessão, sua capacidade de projetar um plano de modernização para organizações que desejam mover serviços de on-premises local para a nuvem será aprimorada.


## Step 1: Revise o estudo de caso do cliente

**Objetivos**

Analise as neceessidades do seu consumidor.

Tempo: 15 minutos

Intruções: Com todos os participantes da sessão, o facilitador / PME apresenta uma visão geral do estudo de caso do cliente, além de dicas técnicas.

1. Conheça os participantes e o treinador da sua mesa.

2. Leia todas as instruções para as etapas 1 a 3 do guia do aluno.

3. Como equipe de mesa, revise o seguinte estudo de caso do cliente.

### Situação do Cliente

A Contoso, Ltd. (Contoso) é uma nova empresa em um negócio antigo. A empresa foi fundada em Auckland, Nova Zelândia, em 2011, por executivos seniores de seguros de vida. A ambiciosa nova empresa oferece uma gama completa de serviços de seguros de longo prazo para ajudar pessoas sem seguro.

Quase desde o início, a empresa cresceu muito mais rápido do que o previsto. Uma avalanche de negócios significou que os processos iniciais criados para gerenciar a documentação da política ficaram sobrecarregados. Os funcionários lutaram para lidar com isso, mesmo quando o número de funcionários aumentou de cinco para 110 durante os primeiros dois anos. "No início de 2013, tínhamos mais de 750.000 páginas de documentos de política parcialmente manuscritos arquivados em nossos escritórios", diz Charlene Mathis, gerente geral da Contoso. "Os funcionários voltados para o cliente não conseguiram recuperar as políticas rapidamente, e enfrentamos um gargalo de serviço. Os tempos de resposta lentos afetaram o atendimento ao cliente e a capacidade de localizar documentos rapidamente nos custou tempo e dinheiro".

Para superar esses desafios, os fundadores lançaram um projeto para criar um aplicativo que pudesse digitalizar e arquivar todos os documentos de políticas existentes e arquivar novas políticas à medida que os corretores os submetessem. Eles também tinham requisitos para permitir o encaminhamento automatizado de documentos de corretores, acesso seguro para corretores, acesso a informações de políticas e recuperação pronta de políticas para uma força de trabalho dispersa. O resultado desse projeto foi um aplicativo personalizado do Windows Forms chamado PolicyConnect. Os funcionários da Contoso usam o PolicyConnect para inserir metadados essenciais da política, incluindo o valor segurado, as informações do beneficiário, o tipo de política e quaisquer requisitos dedutíveis e imediatos, e associam isso aos documentos de política digitalizados.

O PolicyConnect foi criado usando uma arquitetura de aplicativo tradicional de n camadas. A camada de acesso a dados hospeda métodos para interagir com o banco de dados subjacente do SQL Server 2008 R2. Uma camada de lógica de negócios lida com coisas como login de usuário e regras de política. A camada de apresentação fornece a interface do usuário (User Interface  - UI). O design segue uma arquitetura orientada a serviços, com uma série de serviços WCF (Windows Communication Foundation) representando os serviços e recursos necessários para cada camada. O aplicativo armazena documentos de política associados como arquivos PDF em um servidor de arquivos acessível por meio de um compartilhamento de rede SMB em sua rede local. O PolicyConnect acessa esses arquivos usando um caminho canônico (sobrenome do cliente e número da política). Um banco de dados do SQL Server 2008 R2 hospeda os metadados da política para cada documento de política, que atualmente é inserido manualmente no PolicyConnect pelos membros da equipe da Contoso. A Contoso forneceu o seguinte diagrama sobre sua topologia atual:

![The Contoso topology diagram has a local area network comprised of the on-premises user, Application servers for authentication and authorization, policy management and data access service, database servers, and file servers. A VPN server connects them to the Remote User via PolicyConnect.](media/image2.png "The Contoso topology diagram has a local area network comprised of the on-premise user, Application servers for authentication and authorization, policy management and data access service, database servers, and file servers. A VPN server connects them to the Remote User via PolicyConnect.")

Atualmente, o aplicativo oferece suporte ao acesso por meio de uma conexão de rede virtual privada (VPN) para usuários fora da rede local da Contoso. Dessa forma, os corretores da Contoso não conseguem exibir dados ou documentos, a menos que seja concedido acesso à VPN. Este requisito provou ser demorado e frustrante para os corretores.

Os funcionários da Contoso confiam no email como um mecanismo de fluxo de trabalho relativo às tarefas de gerenciamento de documentos. Um grupo é responsável pela varredura e catalogação, enquanto outro grupo é responsável por atribuir as políticas ao corretor especificado. Os e-mails escritos manualmente são enviados aos corretores quando as políticas de seus clientes foram digitalizadas e indexadas. Eles estão usando o Office 365. Os executivos da empresa enfrentam desafios freqüentes na avaliação da produtividade e da taxa de transferência, devido ao fluxo de trabalho manual. Eles sentem que estão impedidos de obter rapidamente as informações de que precisam, pois cada nova pergunta parece precisar de mais desenvolvimento personalizado.

A Contoso começou recentemente a investigar maneiras de alavancar a nuvem para modernizar seu sistema de segurados e começar a solucionar vários problemas com o sistema PolicyConnect existente. No entanto, eles não têm nenhuma experiência tangível com a nuvem e estão procurando orientação sobre como melhor modernizar e tirar proveito das tecnologias em nuvem.


A Contoso declarou que sua maior prioridade é endereçar o fim do suporte para o SQL Server 2008 R2. Eles gostariam de migrar o banco de dados do SQL Server 2008 R2 para um banco de dados SQL totalmente gerenciado no Azure. Quando o banco de dados estiver na nuvem, eles desejam tirar proveito de alguns dos principais benefícios que foram ativados usando um serviço de banco de dados de plataforma como serviço (PaaS). Segundo a Contoso, ele não usa nenhum dos recursos "sofisticados" do SQL Server e espera que a migração possa ser um grande gol. Eles também gostariam de entender melhor os recursos de desempenho e segurança que podem aproveitar quando o banco de dados estiver em execução no Azure.

Outra prioridade é disponibilizar o sistema para funcionários e corretores via aplicativos da Web e móveis e eliminar o requisito para estabelecer uma conexão VPN. Eles também desejam armazenar políticas no armazenamento em nuvem para recuperação por meio de aplicativos  Web e móveis. Os aplicativos da Web e móveis devem permitir que os segurados efetuem login, analisem suas informações e recuperem uma cópia em PDF de sua política. Uma interface de programação de aplicativos (API), compartilhada pelos dois aplicativos, fornece acesso a dados e documentos de política. O objetivo é implantar o aplicativo Web, banco de dados e API na nuvem. Além disso, eles querem aprender mais sobre arquiteturas leves e sem servidor que podem ajudá-los a implementar algumas funcionalidades da API mais rapidamente. Eles mencionaram um possível caso de uso de fornecer acesso a documentos de políticas em armazenamento.

Como parte do processo de modernização do aplicativo, a Contoso também gostaria de saber mais sobre como a Pesquisa Cognitiva do Azure (Azure Cognitive Search) pode melhorar sua capacidade de encontrar documentos de política. O PolicyConnect armazena todos os documentos de política como arquivos PDF opacos em um compartilhamento de arquivos de rede, e os principais metadados são inseridos no aplicativo PolicyConnect manualmente. A pesquisa é limitada a nomes de arquivos e os metadados limitados inseridos manualmente. Atualmente, eles não podem procurar informações contidas nos documentos de política. Eles descobriram que os metadados inseridos manualmente não forneceram os melhores resultados para poder procurar e recuperar informações de política rapidamente.

Devido ao potencial desses novos aplicativos aumentarem a carga em seu banco de dados, eles desejam empregar práticas recomendadas para mitigar o impacto de consultas repetidas no banco de dados. Nessa linha, eles gostariam de implementar um tipo de placar que rastreia os usuários mais ativos em 24 horas, bem como aproximar o número de operações que o usuário executou no sistema em perpetuidade. Ambas as métricas são atraentes para o gerenciamento, a fim de obter uma compreensão superficial de quem são os usuários mais pesados e quanto eles usam o sistema.

A Contoso possui várias equipes de desenvolvimento que se concentram em unidades de negócios separadas (por exemplo, financeiro, vendas, conformidade e corretores). A liderança de TI está animada em mudar o máximo possível de lógica de negócios para APIs. No entanto, eles temem que, com o tempo, possa haver duplicação de esforços à medida que cada equipe desenvolve novas ou revisa APIs existentes. Eles também gostariam de abrir um subconjunto de APIs para uma rede de parceiros afiliados. Eles estão interessados em estratégias para ajudá-los a fornecer descoberta, segurança e gerenciamento do ciclo de vida de um ecossistema de API em evolução. Eles gostariam de análises avançadas e visualizações de dados do uso da API para ajudar a gerenciar o inventário da API.

De acordo com Charlene Mathis, "os aplicativos móveis representam uma maneira de capacitar nossos corretores e funcionários, trazendo nosso software para suas mãos. Nosso principal investimento é tornar possível a melhor versão de aplicativo móvel do PolicyConnect. Mas também queremos fornecer uma maneira simplificada para nossos departamentos internos criarem aplicativos personalizados rapidamente para automatizar micro-processos que economizam tempo sem ter que envolver nossos desenvolvedores ". Um microprocesso que ela mencionou é permitir que os funcionários definam regras. Por exemplo, quando um cliente VIP envia um email, ele recebe uma notificação do aplicativo no dispositivo móvel. Outro cenário seria permitir que os funcionários definissem fluxos de trabalho, como salvar automaticamente anexos em emails com documentos de política no local adequado no armazenamento em nuvem.

Com esse novo sistema, a Contoso gostaria de melhorar suas práticas de segurança. Na versão anterior, cada camada de aplicativo mantinha suas definições de configuração localmente. Por exemplo, a camada de acesso a dados armazenaria as cadeias de conexão do SQL Server localmente no disco. Eles gostariam de adotar uma abordagem de externalização de segredos como esses dos aplicativos Web e APIs e armazená-los em um local criptografado acessível apenas a serviços autorizados.

"Nossos fundadores querem um sistema de documentos que possa ser rapidamente adaptado para atender às mudanças nas necessidades dos negócios, mantendo os custos baixos", diz Mathis. "Eles não querem investir em infraestrutura no on-premisses se os recursos e o suporte de TI envolvidos acabarem retardando nosso crescimento. Eles têm uma estratégia clara de TI: 'Todos os sistemas para a nuvem'".

### Necessidades do Cliente

1. A Contoso deseja modernizar a arquitetura de sua solução, mantendo-a baseada em .NET.

2. Eles gostariam de uma maneira amigável para desenvolvedores .NET de implementar seu aplicativo móvel PolicyConnect para Android e iOS.

3. Eles estão procurando maneiras de capacitar seus usuários de negócios a criar aplicativos móveis internos que os ajudem a otimizar seus processos. Eles gostariam de adicionar esse recurso em menor tempo e investimento necessários para implementar aplicativos móveis em larga escala.

4. Eles querem melhorar o gerenciamento de segredos de aplicativos.

5. Eles desejam tornar os documentos de políticas pesquisáveis ​​em texto completo, com uma quantidade mínima de esforço de implementação.

6. Eles estão interessados ​​em aproveitar as tecnologias sem servidor(Serveless) para acelerar o desenvolvimento da API. Eles solicitaram uma prova de conceito (POC) que pode ser usada para recuperar documentos de política do armazenamento.

7. Eles querem migrar seu banco de dados do SQL Server 2008 R2 para um banco de dados SQL totalmente gerenciado no Azure. Uma vez no Azure, eles gostariam de aproveitar alguns dos principais benefícios habilitados usando um serviço de banco de dados PaaS.

8. A Contoso deseja entender como implantar um cache melhor em sua solução, tanto para diminuir a carga no banco de dados quanto para fornecer dashboards escaláveis com dados dos corretores.

### Dúvidas do Cliente

1. Vimos serviços como IFTTT (If This, Then That) que permitem aos usuários de negócios automatizar processos. O Microsoft Azure oferece algo semelhante?

2. Nossos desenvolvedores ouviram falar do Logic Apps. O Microsoft Flow o substituirá?

3. Existe uma maneira de armazenar com segurança segredos de aplicativos na nuvem?

4. Observamos que o Banco de Dados SQL do Azure não oferece suporte a todos os recursos disponíveis no SQL Server. No momento, não estamos usando esses recursos, mas estamos curiosos para saber quais são as opções para eles no Azure? Especificamente, estávamos pensando em Linked Servers(servidores vinculados), correio do banco de dados, SQL Server Agent Jobs e Service Broker.

5. Mover tudo para APIs parece ótimo, mas como podemos manter o controle de nosso inventário de APIs e gerenciar a descoberta, segurança, ciclo de vida e monitoramento no futuro? Existe algo que poderíamos usar para desenvolver rapidamente uma prova de conceito?

6. Utilizamos o .NET Framework há anos e, agora, no Visual Studio, temos opções para o .NET Framework, .NET Standard e .NET Core. À medida que criamos nossos novos aplicativos da Web e API, como escolhemos a estrutura correta?

### Infográfico com cenários comuns

![The Common scenario for an E-Commerce Website diagram has an Enterprise and an End User connected via an internet tier, a services tier, and a data tier.](media/image3.png "Common scenario for an E-Commerce Website diagram")

## Passo 2: Defina a solução de prova de conceito 

**Desafio**

Defina a solução de prova de conceito e prepare-se para apresentar para o clientes numa sessão de arquitetura/whiteboard de 15-minutos.

Tempo: 60 minutos

**Necessidades do Negócio**

DInstruções: Com todos os participantes em sua mesa, responda às seguintes perguntas e liste as respostas em um flipchart:

1. A quem você deve apresentar esta solução? Quem é seu público-alvo? Quem são os tomadores de decisão?

2. Quais necessidades de negócios do cliente você precisa abordar com sua solução?

**Design**

Instruções: Com todos os participantes em sua mesa, responda às seguintes perguntas em um flip chart:

* Arquitetura de alto nível *

1. Sem entrar em detalhes (as seções à seguir abordam os detalhes específicos), faça um diagrama de sua visão inicial para lidar com os requísitos de nível superior para aplicativos móveis e da web, gerenciamento de dados, pesquisa e extensibilidade.

* Aplicativos móveis e web *

1. Como a Contoso deve implementar o aplicativo móvel PolicyConnect?

2. Qual serviço do Azure hospedaria o site?

3. Qual serviço do Azure hospedaria os serviços que suportam o back-end do aplicativo móvel? Você sugeriria um aplicativo móvel ou um aplicativo de API? Por quê?

4. Que serviço do Azure forneceria uma solução de API leve e sem servidor para recuperar documentos de política do armazenamento de blobs do Azure?

5. Como você protegeria as informações confidenciais usadas pelo site e pelas APIs? Seja específico sobre o Serviço do Azure usado, como você o configuraria e como a lógica da Web ou API recuperaria seus segredos em tempo de execução.

6. Que recomendações você pode fazer para ajudar a Contoso a gerenciar seu inventário de API à medida que cresce no futuro? Existem serviços no Azure que podem fornecer o conceito de *Loja de API* e servir como caminho para o desenvolvimento no futuro?

*Gestão de dados*

1. Quais ferramentas você recomendaria que a Contoso usasse para migrar seu banco de dados? Como você os usaria? Seja específico.

2. Quais padrões e serviços você usaria para reduzir a carga no banco de dados? Implementar os placares? Seja específico nos serviços do Azure usados e como o aplicativo tiraria proveito deles.

3. Dado os requisitos deles, como você ativaria a pesquisa de texto completo nos documentos de política armazenados?

*Pesquisa*

1. Como a Pesquisa Cognitiva do Azure pode ser usada para extrair mais informações dos documentos de política da Contoso?

2. Os desenvolvedores da Contoso podem estender os recursos da Pesquisa Cognitiva do Azure para incluir habilidades cognitivas desenvolvidas internamente para enriquecer seu índice de pesquisa?

*Extensibilidade*

1. Como você permitiria que seus usuários de negócios criassem seus próprios aplicativos móveis internos que os ajudassem a otimizar seus processos sem o tempo e o investimento em recursos necessários para implementar aplicativos móveis em escala real?

2. Dada a sua resposta à pergunta anterior, como um usuário comercial da Contoso implementaria o cenário em que um email de alta prioridade é enviado ao email do Office 365 e em resposta uma notificação do aplicativo é exibida no dispositivo?

**Preparar**

Instruções: Com todos os participantes em sua mesa:

1. Identifique quaisquer necessidades do cliente que não sejam atendidas com a solução proposta.

2. Identifique os benefícios da sua solução.

3. Determine como você responderá às objeções do cliente.

Prepare uma apresentação em estilo de conversa de arquitetura de 15 minutos para o cliente.

### Passo 3: apresente a solução

**Resultado**

Apresente uma solução para o público-alvo do cliente em um formato de 15 minutos.

Tempo: 30 minutos

**Apresentação**

Instruções:

1. Emparelhe com outra mesa.

2. Uma mesa é a equipe da Microsoft e a outra mesa é o cliente.

3. A equipe da Microsoft apresenta sua solução proposta ao cliente.

4. O cliente faz uma das objeções da lista de objeções.

5. A equipe da Microsoft responde à objeção.

6. A equipe do cliente fornece feedback para a equipe da Microsoft.

7. As mesas trocam de função e repita as etapas 2 a 6.

## Conclusão

Tempo: 15 minutos

Instruções: As mesas se reúnem com o grupo maior para ouvir o facilitador / PME compartilhar a solução preferida para o estudo de caso.

## Referências adicionais

|                 |           |
|-----------------|-----------|
| **Description** | **Links** |
| Hi-resolution version of blueprint | <https://msdn.microsoft.com/dn630664#fbid=rVymR_3WSRo> |
| Getting started with Xamarin and Mobile Apps | <https://azure.microsoft.com/documentation/articles/app-service-mobile-xamarin-forms-get-started/> |
| Key Vault Developer's Guide | <https://azure.microsoft.com/documentation/articles/key-vault-developers-guide/> |
| About Keys and Secrets | <https://msdn.microsoft.com/library/dn903623.aspx> |
| Register an Application with AAD | <https://azure.microsoft.com/documentation/articles/key-vault-get-started/#register> |
| How to Use Azure Redis Cache | <https://azure.microsoft.com/documentation/articles/cache-dotnet-how-to-use-azure-redis-cache/> |
| Intro to Redis data types & abstractions | <http://redis.io/topics/data-types-intro> |
| Intro to PowerApps | <https://docs.microsoft.com/powerapps/getting-started> |
| Get Started with Flow | <https://flow.microsoft.com/documentation/getting-started/> |
| Indexing Documents in Blob Storage | <https://azure.microsoft.com/documentation/articles/search-howto-indexing-azure-blob-storage/> |
| Working with Azure Functions Proxies | <https://docs.microsoft.com/azure/azure-functions/functions-proxies> |
| Azure API Management Overview | <https://docs.microsoft.com/azure/api-management/api-management-key-concepts> |
| What is "cognitive search" in Azure Cognitive Search? | <https://docs.microsoft.com/azure/search/cognitive-search-concept-intro> |
