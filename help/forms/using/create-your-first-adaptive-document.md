---
title: NÃO PUBLICAR Crie seu primeiro documento adaptável
seo-title: DO NOT PUBLISH Create your first adaptive document
description: NÃO PUBLICAR
seo-description: DO NOT PUBLISH
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 2%

---


# NÃO PUBLICAR Crie seu primeiro documento adaptável {#do-not-publish-create-your-first-adaptive-document}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Caso de uso  {#use-case}

O We Finance é uma organização líder no domínio de Serviços Financeiros que oferece soluções financeiras abrangentes e personalizadas para atender às necessidades de diversos perfis de clientes.

Uma das apólices de seguro automático de seus clientes está expirando e eles estão enviando um lembrete, que é interativo e inclui um PDF, com a cotação de renovação. A comunicação também inclui outras informações, como prêmios de fidelidade e ofertas de descontos.

O portal é executado no Adobe AEM. A saída do canal de boas-vindas da Web e da impressão é criada usando os recursos de vários canais do Documento Adaptativo.

Você terá um documento adaptável semelhante ao seguinte no final do tutorial:
[ ![ad-1](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf)    [ ![ad-2](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)A criação de seu primeiro tutorial de documento adaptável é categorizada em etapas. Cada etapa é um artigo completo em si mesmo.

<table> 
 <tbody>
  <tr>
   <th>Você aprenderá</th> 
   <th>
    <ul> 
     <li>Criação de um documento adaptável e um modelo de dados de formulário.</li> 
     <li>Criação de modelos e temas para documentos adaptáveis.</li> 
     <li>Usar o editor de regras para criar regras comerciais.<br /> </li> 
     <li>Publicar um documento adaptável. <br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>Pré-requisitos</td> 
   <td>
    <ul> 
     <li>Configure AEM instância do autor. </li> 
     <li>Instalar complemento do AEM Forms. Para obter informações detalhadas, consulte <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">Instalar e configurar o AEM Forms</a>.</li> 
     <li>Obtenha o driver de banco de dados JDBC (arquivo JAR) do provedor de banco de dados. Os exemplos no tutorial são baseados no banco de dados MySQL e usam o driver de banco de dados JDBC do Oracle MySQL. </li> 
     <li>Configure um banco de dados contendo dados do cliente. Um banco de dados é essencial para criar um documento adaptável. Este tutorial usa um banco de dados para exibir o modelo de dados de formulário e os recursos de persistência do AEM Forms. </li> 
     <li>Criar/importar e ativar <a href="/help/forms/using/web-channel-print-channel.md">Modelos para impressão e canal da Web</a>.</li> 
     <li>Certifique-se de ter a variável <a href="/help/forms/using/document-fragments.md">Fragmentos de documento com base no FDM</a>.</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Etapa 1: Criar Modelo de Dados de Formulário {#step-create-form-data-model}

Um modelo de dados de formulário permite conectar um documento adaptável a diferentes fontes de dados. Por exemplo, AEM perfil de usuário, serviços da Web RESTful, serviços da Web baseados em SOAP, serviços OData e bancos de dados relacionais. Um modelo de dados de formulário é um esquema de representação de dados unificado de entidades comerciais e serviços disponíveis em fontes de dados conectadas. Você pode usar o modelo de dados de formulário com um documento adaptável para recuperar dados de fontes de dados conectadas. Para obter mais informações sobre o modelo de dados de formulário, consulte [Integração de dados do AEM Forms](/help/forms/using/data-integration.md).

Metas:

* Configurar a instância do banco de dados (Microsoft Dynamics) como fonte de dados
* Criar o modelo de dados de formulário usando o Microsoft Dynamics como fonte de dados
* Adicionar objetos de modelo de dados ao modelo de dados de formulário
* Configurar serviços de leitura e gravação para o modelo de dados de formulário
* Testar modelo de dados de formulário e serviços configurados com dados de teste

## Etapa 2: Criar um documento adaptável {#step-create-an-adaptive-document}

As Comunicações do cliente centralizam e gerenciam a criação, montagem e entrega de correspondências seguras, personalizadas e interativas, como correspondência comercial, cartas, documentos, declarações, avisos de benefícios, prospecto de gerenciamento de riqueza, emails de marketing, contas e kits de boas-vindas.

Usando documentos adaptáveis, você pode criar comunicações de clientes envolventes, responsivas, dinâmicas e adaptáveis. A AEM Forms fornece um editor WYSIWYG de arrastar e soltar para criar documentos adaptáveis.

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

Metas:

* Crie uma saída impressa e da Web de um documento adaptável com base no modelo de dados de formulário.
* Campos de layout de um formulário adaptável para exibir informações ao cliente
* Crie regras para recuperar e exibir informações do modelo de dados de formulário para o documento adaptável.

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## Etapa 3: Aplicar regras a campos de documento adaptáveis (somente canal da Web) {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

O documento adaptável fornece um editor para gravar regras em objetos de documento adaptáveis. Essas regras definem ações a serem acionadas em objetos de documento com base em condições predefinidas e ações do usuário no documento. Isso ajuda a garantir a precisão e acelera a experiência do usuário na versão da Web do documento adaptável. Para obter mais informações sobre regras de documentos adaptáveis e o editor de regras, consulte [editor de regras](/help/forms/using/rule-editor.md).

Metas:

* Criar e aplicar regras a campos de canal da Web de documentos adaptáveis
* Usar regras para acionar serviços de modelo de dados de documento no canal da Web

## Etapa 4: Estilo do documento adaptável (somente canal da Web) {#step-style-the-adaptive-document-web-channel-only}

Os documentos adaptáveis fornecem um editor para criar temas para os documentos adaptáveis e o estilo em linha. Um tema contém detalhes de estilo para componentes e painéis, e você pode reutilizar um tema em canais da Web de diferentes documentos. Os estilos incluem propriedades como cores de plano de fundo, cores de estado, transparência, alinhamento e tamanho. Quando você aplica o tema ao seu documento, o estilo especificado reflete nos componentes correspondentes do documento. Para obter mais informações, consulte [Temas](/help/forms/using/themes.md).

Metas:

* Criar tema para o canal Web de documentos adaptáveis
* Aplicar tema ao canal Web do documento adaptável
* Validar a aparência do canal Web do documento adaptável em dispositivos móveis e desktop

## Etapa 5: Publicar o documento adaptável {#step-publish-the-adaptive-document}

Depois de concluir a criação do documento adaptável, você precisa publicá-lo para que ele fique disponível na sua instância de publicação, onde os agentes podem usar o documento adaptável para criar as instâncias de comunicação baseadas nele.

Para publicar o documento adaptável, os autores do documento precisam ter as permissões necessárias.
