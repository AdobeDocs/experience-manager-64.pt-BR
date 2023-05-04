---
title: Introdução ao AEM Forms
seo-title: Introduction to AEM Forms
description: Com o Adobe Experience Manager Forms, os usuários empresariais podem integrar formulários envolventes, responsivos e adaptáveis a sites da Web e móveis, simplificando o processo de inscrição digital e aumentando as taxas de conversão do cliente.
seo-description: With Adobe Experience Manager Forms, business users can integrate engaging, responsive, and adaptive forms into web and mobile sites, simplifying the digital enrollment process and increasing customer conversion rates.
uuid: 9e9a164a-4a74-4096-98b8-800ea610edd8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: a976a854-4bf2-49f8-871e-28bc597ac496
feature: Adaptive Forms
exl-id: 0a79111d-e42f-4eb6-8bc4-ab97424e7f90
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 10%

---

# Introdução ao AEM Forms {#introduction-to-aem-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Para obter informações sobre os recursos e as melhorias mais recentes no AEM Forms, consulte [Novidades no AEM Forms](/help/forms/using/whats-new.md).

## Sobre o AEM Forms {#about-aem-forms}

O Adobe Experience Manager (AEM) fornece uma solução fácil de usar para criar, gerenciar, publicar e atualizar formulários digitais complexos ao integrar-se a processos back-end, regras de negócios e dados.

O AEM Forms combina criação, gerenciamento e publicação de formulários, além de recursos de gerenciamento de correspondência, segurança de documentos e análises integradas para criar experiências envolventes e completas. Projetada para funcionar na Web e em canais móveis, a AEM Forms pode ser integrada com eficiência em seus processos comerciais, reduzindo processos e erros de papel e melhorando a eficiência.

A AEM Forms aproveita e estende os recursos de seus investimentos existentes em formulários XFA e na solução de LiveCycle Adobe.

Frequentemente em grandes empresas, os formulários são criados uma vez e reutilizados, por meio de uma cópia enviada para um sistema de gerenciamento de conteúdo. Manter um grande banco de dados de formulários atualizado e torná-los descobertos pode ser um desafio considerável. O AEM fornece um portal de formulários personalizável que garante que os clientes encontrem e acessem os formulários de que precisam, tanto na web quanto em canais móveis.

O AEM Forms fornece ferramentas de gerenciamento de formulários que não apenas permitem gerenciar formulários adaptáveis, como formulários XFA, PDF forms e ativos relacionados também. Para obter mais informações, consulte [Introdução ao gerenciamento de formulários](/help/forms/using/introduction-managing-forms.md).

![](do-not-localize/4th-draft.gif)

### Principais recursos {#key-capabilities}

Resumindo, a AEM Forms fornece recursos avançados de gerenciamento de formulários, como os seguintes, que reduzem os processos manuais e aumentam a satisfação do cliente.

* Um portal Forms centralizado para projetar e implantar formulários dinâmicos, incluindo PDF, HTML5 e formulários adaptáveis
* Uma interface gráfica de usuário fácil de usar para permitir que usuários empresariais importem, gerenciem, visualizem e publiquem formulários com facilidade
* Um diretório de formulários responsivos com recursos de pesquisa avançados usando palavras-chave, tags e metadados
* Detecção dinâmica do dispositivo e do local de um usuário para renderizar o formulário adequadamente em canais móveis e da Web
* Integração com o Adobe Analytics para medir efetivamente as métricas de uso do formulário
* Integração com os serviços eSign da Adobe Document Cloud ou Scribble para assinar eletronicamente documentos contendo informações confidenciais
* Recursos automatizados de publicação de formulários e a capacidade de fornecer comunicação oportuna, personalizada e consistente por meio de vários canais

## Tipos de formulário AEM {#aem-form-types}

O AEM Forms permite estender formulários novos e existentes para criar:

* HTML paginado perfeito para pixels e PDF forms que se parecem quase com papel, ou
* formulários adaptáveis que são renderizados automaticamente para o dispositivo e o navegador de um usuário.

**PDF forms**

O PDF forms pode ser preenchido offline, salvo localmente e os dados do formulário podem ser enviados na próxima vez que você estiver online. Você pode usar códigos de barras 2D para capturar dados de formulários e usar assinaturas digitais para validar a autenticidade dos usuários.

**HTML forms**

Os formulários baseados no navegador HTML5 podem ser exibidos em dispositivos móveis e navegadores de desktop. Você pode assinar eletronicamente formulários HTML usando os serviços Scribble ou eSign.

**Formulários adaptáveis**

Os formulários adaptáveis podem se adaptar dinamicamente às respostas do usuário, adicionando ou removendo campos ou seções, conforme necessário. AEM permite reutilizar modelos de formulário Adobe XML para criar formulários adaptáveis.

### Recursos compatíveis {#supported-features}

Todos os tipos de formulários são compatíveis com os seguintes recursos:

* Layout dinâmico
* Validação do campo de formulário
* Ajuda sensível ao contexto
* Script e tratamento de dados XML
* Design e verificação de acessibilidade
* Capacidade de salvar formulários no lado do servidor
* Suporte para anexos de arquivo
* Integração com o HTML Workspace para captura de dados

## Coleta de dados offline {#offline-data-collection-br}

Depois que os dados do formulário forem enviados, o Adobe Experience Manager conectará os dados do formulário aos sistemas, regras de negócios e às pessoas necessárias.

A AEM Forms fornece o Forms Workspace, um aplicativo móvel que estende seus processos de negócios digitais para dispositivos móveis. Usando o Forms Workspace, você pode coletar e registrar dados mesmo quando estiver offline. O Forms Workspace aproveita os recursos do seu dispositivo móvel e permite capturar fotos, vídeos e coletar dados, como carimbos de data e hora e outras informações. Na próxima vez que você se conectar a uma rede, poderá sincronizar os dados coletados.

Capturar dados offline e sincronizá-los na próxima vez que você retornar online é especialmente útil para pessoas no campo. Melhora a produtividade e reduz erros.

**Vantagens de usar o Forms Workspace para coleta de dados offline**

* Aplicativo de espaço de trabalho HTML fácil de usar para atribuição e rastreamento de tarefas
* Ambiente de design de fluxo de trabalho de arrastar e soltar
* Conectores de gerenciamento de conteúdo corporativo (ECM)
* Suporte a padrões abertos, incluindo XML e SOAP para conectar dados de formulários com sistemas corporativos
* Relatórios de HTML prontos para uso monitoram os backlogs, as filas de trabalho e os KPIs (indicadores-chave de desempenho)
* Painéis personalizáveis para obter informações em tempo real sobre operações comerciais
* API para conexão com ferramentas de relatórios de terceiros

![](do-not-localize/3rd-draft.gif)

## Comunicação personalizada {#personalized-communication}

Uma parte importante de uma experiência digital de autoatendimento eficiente é fornecer informações oportunas e personalizadas que os usuários possam acessar de qualquer lugar e em qualquer dispositivo. Comunicações personalizadas e oportunas podem melhorar as taxas de conversão e a satisfação do usuário.

Usando o AEM Forms, os usuários empresariais podem criar experiências de usuário personalizadas atraentes, personalizando modelos de documento, incorporando informações de processos back-end e incluindo componentes interativos. Uma interface de usuário intuitiva ajuda usuários não técnicos a desenvolver regras de negócios que decidem quando gerar uma comunicação com base em uma pesquisa ou iniciar uma resposta gerada pelo usuário.

Documentos personalizados, como recibos, kits de boas-vindas e declarações podem ser facilmente entregues em vários canais. As organizações podem direcionar o tráfego para portais da web personalizados, resultando na inscrição ou compra de serviços adicionais.

**Principais recursos**

* Ambiente de criação de correspondência com suporte para modelos, blocos de conteúdo, regras de negócios e muito mais
* Conversão e montagem de documentos
* Suporte para entrega de documentos sob demanda ou em lote por meio de vários canais, incluindo Web, email e papel
* Trilhas de auditoria com histórico de alterações
* Suporte para assinaturas digitais para validar a integridade do conteúdo e a identidade do assinante
* Suplemento de segurança de documento para AEM Forms, incluindo criptografia, políticas de uso, rastreamento e auditoria

![](do-not-localize/layout-02.png)
**Figura:** *Fluxo de trabalho de comunicação personalizado simplificado*
