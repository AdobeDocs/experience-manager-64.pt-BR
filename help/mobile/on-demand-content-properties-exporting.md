---
title: Uso das propriedades de conteúdo para exportar conteúdo
seo-title: Using Content Properties to Export Content
description: A página a seguir mostra as Propriedades e os nós do aplicativo.
seo-description: The following page shows App Properties and Nodes.
uuid: 73f1832f-e457-47d0-a0e1-80af90897d31
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: a3006835-b1d2-47d6-959a-cdb692e34e1e
exl-id: 27aa405d-2388-4f91-85d0-1a8709e0d5d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 6%

---

# Uso das propriedades de conteúdo para exportar conteúdo{#using-content-properties-to-export-content}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>A Adobe recomenda usar o Editor de SPA para projetos que exigem renderização do lado do cliente com base em estrutura de aplicativo de página única (por exemplo, React). [Saiba mais](/help/sites-developing/spa-overview.md).

Os aplicativos são representados como *cq:Pages* em AEM.

Eles compartilham as mesmas propriedades comuns encontradas em qualquer *cq:Page* além de outras mostradas abaixo que representam as propriedades de suporte da integração.

## Propriedades do aplicativo {#app-properties}

A tabela a seguir mostra **Propriedades e nós do aplicativo**.

<table>
 <tbody>
  <tr>
   <td><strong>PropertyName</strong></td>
   <td><strong>Tipo</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td>dps-cloudConfig</td>
   <td>String:Path</td>
   <td><p>Caminho para um Cloud Service móvel sob demanda configurado. Usado para ações sob demanda do AEM Mobile para dispositivos móveis (invocação de API)</p> <p>Essa associação é configurada por meio do bloco Gerenciar conexão , quando um autor escolhe um Cloud Service Mobile On-Demand para associar o aplicativo.</p> </td>
  </tr>
  <tr>
   <td>dps-exportTemplate</td>
   <td>String:Path</td>
   <td><p>Caminho para as configurações de exportação do aplicativo. A configuração de exportação é uma pasta com 2 templates de configuração de exportação do ContentSync filho;</p> <p><i>dps-article</i>: Configuração de exportação do ContentSync para exportar conteúdo do artigo</p> <p><i>dps-HTMLResources</i>: Configuração de exportação do ContentSync para exportar recursos compartilhados aplicativo/artigo</p> </td>
  </tr>
  <tr>
   <td>dps-projectId</td>
   <td>String</td>
   <td><p>Id/URI do projeto Mobile On-Demand ao qual este Aplicativo está vinculado/vinculado.</p> <p>Essa associação é configurada por meio do bloco Gerenciar conexão , quando um autor escolhe o projeto a partir de uma lista de projetos disponíveis para o Cloud Service Mobile On-Demand associado.</p> </td>
  </tr>
  <tr>
   <td>dps-projectTitle</td>
   <td>String</td>
   <td>Título do aplicativo.</td>
  </tr>
  <tr>
   <td>dps-resourceType</td>
   <td>String</td>
   <td>Tipo de conteúdo.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploaded</td>
   <td>Data</td>
   <td>Data do último upload de recursos compartilhados do AEM para o AEM Mobile.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploadedBy</td>
   <td>String:userid</td>
   <td>ID do usuário que realizou o último upload da solicitação de recursos compartilhados do AEM para o AEM Mobile.</td>
  </tr>
  <tr>
   <td>pge-dashboard-config</td>
   <td>String:Path</td>
   <td>Caminho para uma configuração de painel. O caminho pode ser redirecionado para uma configuração de painel personalizada, conforme necessário.</td>
  </tr>
  <tr>
   <td>sling:resourceType</td>
   <td>String:Path</td>
   <td><p>Caminho para um cq:Componente que é ou estende <i>mobileapps/core/components/instance.</i></p> <p>Isso fornece a presença e renderização no Catálogo de aplicativos.</p> </td>
  </tr>
 </tbody>
</table>

Você pode usar ***Propriedades de conteúdo*** para criar conteúdo. Consulte os seguintes recursos para criar e exportar artigos e recursos compartilhados:

* [Propriedades de conteúdo](/help/mobile/content-properties.md)
* [Criação da configuração de exportação de artigo](/help/mobile/creating-article-export-configuration.md)
* [Criando Configuração de Exportação de Recursos Compartilhados](/help/mobile/creating-shared-resources-export-configuration.md)
