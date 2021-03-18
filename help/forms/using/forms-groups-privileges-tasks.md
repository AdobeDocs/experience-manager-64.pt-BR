---
title: AEM Forms em grupos e privilégios OSGi
seo-title: AEM Forms em grupos e privilégios OSGi
description: Atribua usuários aos grupos para gerenciar o AEM Forms no OSGi
seo-description: Atribua usuários aos grupos para gerenciar o AEM Forms no OSGi
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
role: Administrador
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 2%

---


# AEM Forms em grupos e privilégios OSGi {#aem-forms-on-osgi-groups-and-privileges}

Atribua usuários aos grupos para gerenciar o AEM Forms no OSGi

Você pode [criar grupos](/help/sites-administering/user-group-ac-admin.md#group-administration) e atribuir políticas e [usuários](/help/sites-administering/user-group-ac-admin.md#user-administration) aos grupos em AEM. Essas políticas controlam os privilégios dos usuários que fazem parte do grupo.

Depois de instalar [Pacote do complemento AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md), os grupos mencionados neste artigo, como forms-user e forms-power-user, ficam automaticamente disponíveis para atribuição. A tabela a seguir lista as tarefas que um usuário pode executar para o AEM Forms no OSGi com base nas atribuições de grupo:

<table> 
 <tbody>
  <tr>
   <td>Grupo</td> 
   <td>Tarefas</td> 
  </tr>
  <tr>
   <td>forms-user <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Criar, visualizar, publicar e enviar formulários adaptáveis</li> 
     <li>Criar, visualizar e publicar comunicações interativas e fragmentos de documento</li> 
     <li>Fazer upload de ativos para uma instância de AEM</li> 
     <li>Criar temas</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>usuários avançados de formulários</td> 
   <td>
    <ul> 
     <li>Criar, visualizar, publicar e enviar formulários adaptáveis</li> 
     <li>Criar, visualizar e publicar comunicações interativas e fragmentos de documento</li> 
     <li>Criar scripts para formulários adaptáveis usando o editor de código</li> 
     <li>Fazer upload de ativos incluindo scripts</li> 
     <li>Criar temas</li> 
     <li>Importar pacotes contendo XDP</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-submit-revisores</td> 
   <td>
    <ul> 
     <li>Envio de revisão</li> 
     <li>Aprovar ou rejeitar envios</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>autores de modelo <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Criar e visualizar formulários adaptáveis ou modelos de comunicações interativas</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-authors</p> </td> 
   <td>
    <ul> 
     <li>Criar e modificar um modelo de dados de formulário</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>cm-user-agent</td> 
   <td>
    <ul> 
     <li>Acessar cartas de gerenciamento de correspondência ou comunicações interativas usando a interface do usuário do agente</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>editores de fluxo de trabalho</p> </td> 
   <td>
    <ul> 
     <li>Criar um aplicativo de caixa de entrada</li> 
     <li>Criar um modelo de fluxo de trabalho</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>Usar AEM aplicativos da caixa de entrada</li> 
     <li>Gerenciar instâncias de fluxo de trabalho</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>Configurar o gerador de PDF</li> 
     <li>Configurar pasta assistida</li> 
     <li>Gerenciar aplicativos de fluxo de trabalho</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. O usuário com privilégios de grupo de usuários de formulários não pode gravar scripts para formulários adaptáveis.
1. O usuário com privilégios de grupo de autores de modelo não pode gravar scripts para modelos.

