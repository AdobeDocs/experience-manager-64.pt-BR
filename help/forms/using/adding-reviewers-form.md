---
title: Associar revisores de envio a um formulário
seo-title: Associar revisores de envio a um formulário
description: Saiba como associar revisores de envio a um formulário no AEM Forms. Os revisores associados analisam um formulário enviado por meio do portal de formulários.
seo-description: Saiba como associar revisores de envio a um formulário no AEM Forms. Os revisores associados analisam um formulário enviado por meio do portal de formulários.
uuid: 66834c2b-ae70-4a6e-ae8e-07d0e38de06b
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 7c39383b-b430-40a1-9bcb-f5aaccb616ad
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Associar revisores de envio a um formulário  {#associating-submission-reviewers-with-a-form}

Ao criar um formulário, você pode especificar usuários que revisam os envios do formulário por meio do portal de formulários e fornecem feedback. Sua organização pode coletar feedback e retrabalhar os formulários enviados.

O AEM Forms permite associar um grupo de revisores a um formulário. Os usuários adicionados a um grupo de revisão de um formulário visualizam os envios desse formulário e fornecem feedback.

Os grupos do revisor atribuídos a um formulário só podem revisar os envios do formulário especificado.

## Pré-requisitos {#prerequisite}

### Habilitar a propriedade de grupos do revisor de envio para formulários adaptáveis usando o editor de schemas de metadados {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Para associar um grupo de revisores a um formulário, edite o schema de metadados de formulários adaptáveis. Por padrão, não é possível adicionar um grupo de revisores a um formulário enviado.

Para editar o schema de metadados:

1. No modo de autor, em Experience Manager, clique em **[!UICONTROL Ferramentas > Ativos > Schemas]** de metadados.
1. Na página Schema Forms, navegue até **[!UICONTROL Forms > Forms Authored in AEM]**.

   O url da página é:

   ```
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/dam/content/schemaeditors/forms/forms/
    aem-authored
   ```

1. Selecione Formulário **** adaptável e clique em **[!UICONTROL Editar]**.
1. Na página Editar formulário, clique em **[!UICONTROL Avançado]**.
1. Na guia Avançado, arraste e solte o componente Texto **[!UICONTROL de linha]** única disponível em Formulário de compilação.
1. Selecione o componente de texto adicionado para ver suas configurações.

   Em Configurações, digite `./jcr:content/metadata/form-submission-reviewer-group` no campo Mapa para propriedade.

   O campo de grupo do revisor de envio nas propriedades Avançadas do formulário adaptável é ativado com o nome especificado em Rótulo do campo.

## Associar revisores de envio a um formulário {#associating-submission-reviewers-with-a-form-1}

Para associar revisores de envio a um formulário adaptável, crie um grupo de revisores e adicione usuários a ele. Adicione o grupo do revisor criado no campo do revisor de envio de formulário nas propriedades avançadas do formulário.\
Os grupos de usuários permitem associar diferentes conjuntos de revisores de envio a diferentes formulários adaptáveis. Este recurso impede uma revisão de envio de um usuário não autorizado.

Antes de executar as etapas a seguir, consulte [Pré-requisito](/help/forms/using/adding-reviewers-form.md#prerequisite).

Para criar um grupo e adicionar membros a ele, navegue até **[!UICONTROL Ferramentas > Operações > Segurança > Grupos]**.\
Para obter mais informações, consulte Administração [do usuário e Serviços](/help/sites-administering/security.md).\
Certifique-se de adicionar o grupo criado como membro do grupo de usuários predefinido: **revisores** de envio de formulários. Esse grupo de usuários é enviado com a AEM Forms e garante que os usuários sejam adicionados como revisores de envio.

Para associar grupos de usuários a um formulário adaptável:

1. No modo de criação, navegue até **[!UICONTROL Forms > Forms e Documentos]**.
1. Use a opção **[!UICONTROL Selecionar]** para selecionar um formulário adaptável e clique em Propriedades **[!UICONTROL da]** Visualização.
1. Na janela Propriedades do formulário, clique em **[!UICONTROL Editar]** e em **[!UICONTROL AVANÇADO]**.
1. Insira o grupo no campo do grupo do revisor de submissão e clique em **[!UICONTROL Concluído]**.

   O campo de grupo do revisor de envio é exibido com o nome especificado no schema de metadados editados dos formulários adaptáveis.

>[!NOTE]
>
>Replicar usuários e formulários para garantir a disponibilidade dos usuários e formulários na implementação remota da AEM Forms.
>
>Certifique-se de que todos os usuários sejam replicados como membros de revisão dos grupos de usuários na implementação remota.

