---
title: Segurança de documento | Tratamento de dados de utilizadores
seo-title: Segurança de documento | Tratamento de dados de utilizadores
description: A segurança do documento AEM Forms permite criar, armazenar e aplicar configurações de segurança predefinidas a seus documentos. Ela garante que somente usuários autorizados possam usar os documentos. Saiba como a segurança de documentos organiza dados em tabelas de banco de dados, acessa e exporte dados de segurança de documentos para usuários nos bancos de dados e, se necessário, exclua-os permanentemente.
seo-description: A segurança do documento AEM Forms permite criar, armazenar e aplicar configurações de segurança predefinidas a seus documentos. Ela garante que somente usuários autorizados possam usar os documentos. Saiba como a segurança de documentos organiza dados em tabelas de banco de dados, acessa e exporte dados de segurança de documentos para usuários nos bancos de dados e, se necessário, exclua-os permanentemente.
uuid: 1624a465-8b0c-4347-a53f-1118bfa6e18f
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 898268cb-4426-421f-8f63-d75bd85cb57f
role: Admin
exl-id: eeffd886-8955-46eb-aa6d-dd4da5e8570c
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 0%

---

# Segurança de documento | Tratamento de dados de utilizadores {#document-security-handling-user-data}

A segurança do documento AEM Forms permite criar, armazenar e aplicar configurações de segurança predefinidas a seus documentos. Ela garante que somente usuários autorizados possam usar os documentos. Você pode proteger documentos usando políticas. Uma política é uma coleção de informações que inclui configurações de segurança e uma lista de usuários autorizados. Você pode aplicar uma política a um ou mais documentos e autorizar usuários adicionados ao gerenciamento de usuários do AEM Forms JEE.

<!-- Fix broken link For more information about how document security works, see AEM Forms JEE administration help. -->

## Armazenamento de dados e dados do usuário {#user-data-and-data-stores}

A segurança de documentos armazena políticas e dados relacionados a documentos protegidos, incluindo dados de usuários em um banco de dados, como My Sql, Oracle, MS SQL Server e IBM DB2. Além disso, os dados para usuários autorizados em uma política em armazenamento no gerenciamento de usuários. Para obter informações sobre dados armazenados no gerenciamento de usuários, consulte [Gerenciamento de usuários do Forms: Manipular dados do usuário](/help/forms/using/user-management-handling-user-data.md).

A tabela a seguir mapeia como a segurança do documento organiza dados em tabelas de banco de dados.

<table> 
 <tbody> 
  <tr> 
   <td>Tabela de banco de dados</td> 
   <td>Descrição</td> 
  </tr> 
  <tr> 
   <td><code>EdcPrincipalKeyEntity</code></td> 
   <td>Armazena informações sobre as chaves principais dos usuários. As chaves são usadas em fluxos de trabalho de segurança de documentos offline.</td> 
  </tr> 
  <tr> 
   <td><code>EdcAuditEntity</code></td> 
   <td>Armazena informações sobre eventos de auditoria como eventos de usuário, eventos de documento e eventos de política.</td> 
  </tr> 
  <tr> 
   <td><p><code>EdcLicenseEntity</code></p> </td> 
   <td>Armazena o registro de um documento protegido. Ele armazena os detalhes da licença para cada documento protegido.</td> 
  </tr> 
  <tr> 
   <td><p><code>EdcDocumentEntity</code></p> </td> 
   <td>Armazena o nome do documento para cada licença criada no sistema.</td> 
  </tr> 
  <tr> 
   <td><p><code>EdcRevokationEntity</code></p> </td> 
   <td>Armazena informações sobre a revogação e reinstalação de documentos protegidos.</td> 
  </tr> 
  <tr> 
   <td><code>EdcMyPolicyListEntity</code></td> 
   <td>Armazena informações sobre usuários que podem criar políticas pessoais exibidas na guia Minhas políticas na página Políticas . </td> 
  </tr> 
  <tr> 
   <td><code>EdcPolicyEntity</code></td> 
   <td>Armazena informações sobre políticas. Cada política corresponde a uma linha nesta tabela.</td> 
  </tr> 
  <tr> 
   <td><code>EdcPolicyXmlEntity</code></td> 
   <td>Armazena arquivos XML para políticas ativas. Um XML<sup> de política </sup>contém referências às IDs principais dos usuários associados à política. O XML da política é armazenado como um objeto Blob.</td> 
  </tr> 
  <tr> 
   <td><code>EdcPolicyArchiveEntity</code></td> 
   <td>Armazena informações sobre políticas arquivadas. Uma política arquivada contém seu XML de política armazenado como um objeto Blob.</td> 
  </tr> 
  <tr> 
   <td><p><code>EdcPolicySetPrincipalEntity</code></p> <p><code>EdcPolicySetPrincipalEnt</code> (Bancos de dados Oracle e MS SQL)</p> </td> 
   <td>Armazena o mapeamento entre o conjunto de políticas e os usuários.</td> 
  </tr> 
  <tr> 
   <td><code>EdcInvitedUserEntity</code></td> 
   <td>Armazena informações sobre o Usuário convidado.</td> 
  </tr> 
 </tbody> 
</table>

## Acessar e excluir dados do usuário {#access-and-delete-user-data}

Você pode acessar e exportar dados de segurança de documentos para usuários nos bancos de dados e, se necessário, excluí-los permanentemente.

Para exportar ou excluir dados do usuário de um banco de dados, é necessário se conectar ao banco de dados usando um cliente de banco de dados e descobrir a ID principal com base em algumas informações pessoalmente identificáveis do usuário. Por exemplo, para recuperar a ID principal de um usuário usando uma ID de logon, execute o seguinte comando `select` no banco de dados.

No comando `select`, substitua o `<user_login_id>` pelo ID de logon do usuário cujo ID principal você deseja recuperar da tabela do banco de dados `EdcPrincipalUserEntity`.

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Depois de saber a ID principal, é possível exportar ou excluir os dados do usuário.

### Exportar dados do usuário {#export-user-data}

Execute os seguintes comandos de banco de dados para exportar dados de usuário para uma ID principal a partir de tabelas de banco de dados. No comando `select`, substitua `<principal_id>` pela ID principal do usuário cujos dados você deseja exportar.

>[!NOTE]
>
>Os comandos a seguir usam nomes de tabela de banco de dados em bancos de dados My SQL e IBM DB2. Ao executar esses comandos em bancos de dados Oracle e MS SQL, substitua `EdcPolicySetPrincipalEntity` por `EdcPolicySetPrincipalEnt` nos comandos.

```sql
Select * from EdcPrincipalKeyEntity where principalid = '<principal_id>';

Select * from EdcLicenseEntity where publisherId = '<principal_id>';

Select * from EdcDocumentEntity where id in (Select documentid from EdcLicenseEntity where publisherId = '<principal_id>');

Select * from EdcRevokationEntity where licenseid in (Select id from EdcLicenseEntity where publisherId = '<principal_id>');

Select * from EdcMyPolicyListEntity where principalId = '<principal_id>';

Select * from edcpolicyentity where policyownerId = '<principal_id>';

Select * from edcpolicyxmlentity where policyidref in (Select id from edcpolicyentity where policyownerId = '<principal_id>');

Select * from edcpolicyarchiveentity where policyownerId = '<principal_id>';

Select * from edcpolicysetprincipalentity where principalId = '<principal_id>';

Select * from edcinviteduserentity where principalId = '<principal_id>';
```

>[!NOTE]
>
>Para exportar dados da tabela `EdcAuditEntity`, use a API [EventManager.exportEvents](https://helpx.adobe.com/experience-manager/6-4/forms/ProgramLC/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) que utiliza [EventSearchFilter](https://helpx.adobe.com/experience-manager/6-4/forms/ProgramLC/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) como um parâmetro para exportar dados de auditoria com base em `principalId`, `policyId` ou `licenseId`.

Para obter dados completos sobre um usuário no sistema, você deve acessar e exportar dados do banco de dados de gerenciamento de usuários. Para obter mais informações, consulte [Gerenciamento de usuários do Forms: Manipular dados do usuário](/help/forms/using/user-management-handling-user-data.md).

### Excluir dados do usuário {#delete-user-data}

Faça o seguinte para excluir dados de segurança do documento para uma ID principal das tabelas do banco de dados.

1. Desligue o servidor AEM Forms.
1. Execute os seguintes comandos de banco de dados para excluir dados da ID principal das tabelas de banco de dados para segurança de documentos. No comando `Delete`, substitua `<principal_id>` pela ID principal do usuário cujos dados você deseja excluir.

   ```sql
   Delete from EdcPrincipalKeyEntity where principalid = '<principal_id>';
   
   Delete from EdcMyPolicyListEntity where principalId = '<principal_id>';
   
   Delete from edcpolicyarchiveentity where policyownerId = '<principal_id>';
   
   Delete from edcpolicysetprincipalentity where principalId = '<principal_id>';
   
   Delete from edcinviteduserentity where principalId = '<principal_id>';
   ```

   >[!NOTE]
   >
   >Para excluir dados da tabela `EdcAuditEntity`, use a API [EventManager.deleteEvents](https://helpx.adobe.com/experience-manager/6-4/forms/ProgramLC/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) que utiliza [EventSearchFilter](https://helpx.adobe.com/experience-manager/6-4/forms/ProgramLC/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) como um parâmetro para excluir dados de auditoria com base em `principalId`, `policyId` ou `licenseId`.

1. Os arquivos XML de política ativa e arquivada são armazenados nas tabelas do banco de dados `EdcPolicyXmlEntity` e `EdcPolicyArchiveEntity`, respectivamente. Para excluir dados de um usuário nessas tabelas, faça o seguinte:

   1. Abra o blob XML de cada linha na tabela `EdcPolicyXMLEntity` ou `EdcPolicyArchiveEntity` e extraia o arquivo XML. O arquivo XML é semelhante ao mostrado abaixo.
   1. Edite o arquivo XML para remover o blob da ID principal.
   1. Repita as etapas 1 e 2 para o outro arquivo.

   >[!NOTE]
   >
   >Você deve remover o blob completo dentro da tag `Principal` de uma ID principal ou o XML de política pode ficar corrompido ou inutilizável.

   ```xml
   <ns2:Principal PrincipalNameType="USER">
       <ns2:PrincipalDomain>OID</ns2:PrincipalDomain>
       <ns2:PrincipalName>56F33FEB-098A-1036-A651-00000A2A2656</ns2:PrincipalName>
   </ns2:Principal>
   </ns2:PolicyEntry>
       <ns2:Property PropertyName="isCertified">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string">false</ns2:PropertyValue>
       </ns2:Property>
       <ns2:Property PropertyName="encryptionAlgorithm">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string">AES128</ns2:PropertyValue>
       </ns2:Property>
       <ns2:Property PropertyName="AccessDeniedErrorMessage">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string"></ns2:PropertyValue>
       </ns2:Property>
   <ns2:PolicyEntry>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.onlineOpen" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.copy" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.offlineOpen" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.accessible" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.editNotes" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.edit" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.fillAndSign" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.printHigh" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.printLow" Access="ALLOW"/>
   ```

   Além de excluir dados diretamente da tabela `EdcPolicyXmlEntity`, há mais duas maneiras de fazer isso:

   **Uso do console de administração**

   1. Como administrador, faça logon no console de administração do Forms JEE em https://[*server*]:[*port*]/adminui.
   1. Navegue até **[!UICONTROL Serviços > Segurança de documentos > Conjuntos de políticas]**.
   1. Abra um conjunto de políticas e exclua o usuário da política.

   **Usando a página da Web de segurança do documento**

   Os usuários de segurança de documentos que têm permissões para criar políticas pessoais podem excluir dados do usuário de suas políticas. Para fazer isso:

   1. Os usuários que têm políticas pessoais fazem logon na página da Web de segurança do documento em https://[*server*]:[*port*]/edc.
   1. Navegue até **[!UICONTROL Services > Document Security > My Policies]**.
   1. Abra uma política e exclua o usuário da política.

   >[!NOTE]
   >
   >Os administradores podem pesquisar, acessar e excluir dados do usuário das políticas pessoais de outros usuários em **[!UICONTROL Serviços > Segurança de documentos > Minhas políticas]** usando o console de administração.

1. Exclua os dados da ID principal do banco de dados de gerenciamento de usuários. Para obter etapas detalhadas, consulte [Gerenciamento de usuários do Forms | Manipulação de dados do usuário](/help/forms/using/user-management-handling-user-data.md).
1. Inicie o servidor do AEM Forms.
