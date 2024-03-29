---
title: Forms Portal | Tratamento de dados de utilizadores
seo-title: Forms Portal | Handling user data
description: O portal do AEM Forms fornece componentes que podem ser usados para listar formulários adaptáveis, formulários HTML5 e outros ativos do Forms na página do AEM Sites. Saiba como o portal do Forms armazena dados para formulários de rascunho e enviados. Saiba mais sobre como acessar dados de rascunho e formulários enviados para usuários conectados e anônimos nos armazenamentos de dados configurados e, se necessário, exclua-os.
seo-description: AEM Forms portal provides components that you can use to list adaptive forms, HTML5 forms, and other Forms assets on AEM Sites page. Learn how Forms portal stores data for draft and submitted forms. Dig deeper on how to access draft and submitted forms data for logged-in and anonymous users in the configured data stores, and if required, delete it.
uuid: 2ac2b2a9-b603-489a-86b8-a78b697f130d
contentOwner: vishgupt
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 48f841b7-0e7f-4216-9ee8-fb6e843acaf0
role: Admin
exl-id: 05dbb6ee-09fd-44ee-bb8b-a3f3ebb32f5a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---

# Forms Portal | Tratamento de dados de utilizadores {#forms-portal-handling-user-data}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O portal do AEM Forms fornece componentes que podem ser usados para listar formulários adaptáveis, formulários HTML5 e outros ativos do Forms na página do AEM Sites. Além disso, é possível configurá-lo para exibir rascunhos e formulários adaptáveis enviados e formulários HTML5 para um usuário conectado. Para obter mais informações sobre o portal de formulários, consulte [Introdução à publicação de formulários em um portal](/help/forms/using/introduction-publishing-forms.md).

Quando um usuário conectado salva um formulário adaptável como rascunho ou o envia, ele é exibido nas guias Rascunhos e Envios no portal de formulários. Os dados para rascunhos ou formulários enviados são armazenados no armazenamento de dados configurado para AEM implantação. Os rascunhos e envios de usuários anônimos não são exibidos na página do portal de formulários; no entanto, os dados são armazenados no armazenamento de dados configurado. Para obter mais informações, consulte [Configuração de serviços de armazenamento para rascunhos e envios](/help/forms/using/configuring-draft-submission-storage.md).

## Armazenamento de dados e dados do usuário {#user-data-and-data-stores}

O portal do Forms armazena dados para formulários de rascunho e enviados nos seguintes cenários:

* A ação de envio configurada no formulário adaptável é **Ação de envio do portal do Forms**.
* Para enviar ações diferentes de **Ação de envio do portal do Forms**, o **[!UICONTROL Armazenar dados no portal de formulários]** está ativada na função **Submissão** propriedades do contêiner de formulário adaptável.

Para cada rascunho e formulário enviado para usuários conectados e anônimos, o portal de formulários armazena os seguintes dados:

* Metadados de formulário, como o nome do formulário, o caminho do formulário, a ID de rascunho ou de envio, o caminho de anexos e a ID de dados do usuário
* Anexo de formulário como bytes de dados
* Dados do formulário como bytes de dados

Dependendo da persistência do armazenamento de dados configurado, os rascunhos e os dados de formulários enviados são armazenados nos seguintes locais.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Tipo de persistência</strong></p> </td> 
   <td><p><strong>Armazenamento de dados</strong></p> </td> 
   <td><p><strong>Local</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Padrão</p> </td> 
   <td><p>AEM repositório de instâncias de autor e publicação</p> </td> 
   <td><p><code>/content/forms/fp/</code></p> </td> 
  </tr> 
  <tr> 
   <td><p>Remoto</p> </td> 
   <td><p>Repositório AEM de instâncias de autor e AEM remotas</p> </td> 
   <td><p><code>/content/forms/fp/</code></p> </td> 
  </tr> 
  <tr> 
   <td><p>Banco de dados</p> </td> 
   <td><p>Repositório AEM de instâncias de autor e tabelas de banco de dados</p> </td> 
   <td>Tabelas de banco de dados <code>data</code>, <code>metadata</code>e <code>additionalmetadata</code></td> 
  </tr> 
 </tbody> 
</table>

## Acessar e excluir dados do usuário {#access-and-delete-user-data}

Você pode acessar dados de rascunho e formulários enviados para usuários conectados e anônimos nos armazenamentos de dados configurados e, se necessário, excluí-los.

### AEM instâncias {#aem-instances}

Todos os rascunhos e dados de formulários enviados em instâncias AEM (autor, publicação ou remoto) para usuários conectados e anônimos são armazenados no `/content/forms/fp/` nó do repositório AEM aplicável. Toda vez que um usuário conectado ou anônimo salva um rascunho ou envia um formulário, uma `draft ID` ou `submission ID`, a `user data ID`e um aleatório `ID` para cada anexo (se aplicável) é gerado, que está associado ao respectivo projeto ou apresentação.

#### Acessar dados do usuário {#access-user-data}

Quando um usuário conectado salva um rascunho ou envia um formulário, um nó filho é criado com sua ID de usuário. Por exemplo, rascunhos e dados de envios para Sarah Rose, cuja ID de usuário é `srose` são armazenados em `/content/forms/fp/srose/` no repositório AEM. No nó ID do usuário, os dados são organizados em uma estrutura hierárquica.

A tabela a seguir explica como os dados de todos os rascunhos por `srose` é armazenado em AEM repositório.

>[!NOTE]
>
>Uma estrutura exata como `drafts` é replicado para formulários enviados para `srose` nos termos do `/content/forms/fp/srose/submit/` nó .
>
>Todos os projetos e submissões `anonymous` Os usuários do são armazenados no `/content/forms/fp/anonymous/` , que organiza rascunhos e envios para todos os usuários anônimos sob o `draft` e `submit` nós.

| Nó | Descrição |
|---|---|
| `/content/forms/fp/srose/drafts` | Dados do nó do contêiner para todos os rascunhos pelo usuário |
| `/content/forms/fp/srose/drafts/attachments/` | Organiza todos os anexos para o usuário com base na ID de rascunho |
| `/content/forms/fp/srose/drafts/attachments/<ID>` | Contém anexo para a ID selecionada no formato binário |
| `/content/forms/fp/srose/drafts/metadata/` | Organiza metadados de formulário para o usuário com base na ID de rascunho |
| `/content/forms/fp/srose/drafts/metadata/<draft ID>` | Contém metadados de formulário para a ID de rascunho selecionada |
| `/content/forms/fp/srose/drafts/data/` | Organiza dados de formulários para o usuário com base na ID de dados do usuário |
| `/content/forms/fp/srose/drafts/data/<user data ID>` | Contém dados de formulário para a ID de dados do usuário selecionada no formato binário |

#### Excluir dados do usuário {#delete-user-data}

Para excluir completamente os dados do usuário dos rascunhos e envios de um usuário conectado AEM sistemas, você deve excluir o `user ID` nó para um usuário específico do nó do autor. Você deve excluir dados manualmente de todas as instâncias de AEM aplicáveis.

Os rascunhos e dados de envio para todos os usuários anônimos são armazenados no `drafts` e `submit` nós sob `/content/forms/fp/anonymous`. Não há método para localizar dados para um usuário anônimo específico, a menos que algumas informações identificáveis sejam conhecidas. Nesse caso, você pode pesquisar as informações que identificam o usuário anônimo AEM repositório e excluir manualmente o nó que o contém de todas as instâncias AEM aplicáveis para remover dados do sistema AEM. No entanto, para excluir dados de todos os usuários anônimos, é possível excluir a variável `anonymous` para remover rascunhos e dados de envios para todos os usuários anônimos.

### Banco de dados {#database}

Quando o AEM é configurado para armazenar dados em um banco de dados, o rascunho do portal de formulários e os dados de envio são armazenados nas seguintes tabelas do banco de dados para usuários conectados e anônimos:

* dados
* metadados
* adtionalmetadata

#### Acessar dados do usuário {#access-user-data-1}

Para acessar rascunhos e dados de envios de um usuário conectado e anônimo nas tabelas do banco de dados, execute o seguinte comando de banco de dados. Na query, substitua `logged-in user` com a ID do usuário cujos dados você deseja acessar ou com `anonymous` para usuários anônimos.

```sql
select * from metadata, data, additionalmetadatatable where metadata.owner = 'logged-in user' and metadata.id = additionalmetadatatable.id and metadata.userdataID = data.id
```

#### Excluir dados do usuário {#delete-user-data-1}

Para excluir rascunhos e enviar dados para um usuário conectado das tabelas do banco de dados, execute o seguinte comando do banco de dados. Na query, substitua `logged-in user` com a ID do usuário cujos dados você deseja excluir ou com `anonymous` para usuários anônimos. Observe que para excluir dados de um usuário anônimo específico do banco de dados, é necessário encontrá-los usando algumas informações identificáveis e excluí-los das tabelas do banco de dados que contêm as informações.

```sql
DELETE FROM metadata, data, additionalmetadatatable USING metadata INNER JOIN data ON metadata.userdataID = data.id INNER JOIN additionalmetadatatable ON metadata.id = additionalmetadatatable.id WHERE metadata.owner = 'logged-in user'
```
