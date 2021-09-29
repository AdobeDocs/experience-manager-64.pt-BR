---
title: Metadados de edição em massa de vários ativos e coleções
description: Saiba como editar os metadados de muitos ativos e coleções simultaneamente para propagar rapidamente alterações de metadados comuns.
contentOwner: AG
feature: Asset Management,Metadata,Collections
role: User
exl-id: 3541b50a-f226-4a6a-9c2a-03a5f47f1c23
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 13%

---

# Gerenciar vários ativos e coleções {#managing-multiple-assets-and-collections}

Saiba como editar os metadados de vários ativos e coleções simultaneamente para propagar rapidamente alterações de metadados comuns.

Os Ativos do Adobe Enterprise Manager permitem editar os metadados de vários ativos simultaneamente, para que você possa propagar rapidamente alterações de metadados comuns a ativos em massa. Também é possível editar os metadados de várias coleções em massa.

Use a página de propriedades para executar alterações de metadados em vários ativos ou coleções:

* Alterar propriedades de metadados para um valor comum
* Adicionar ou modificar tags

Para personalizar a página de propriedades de metadados, incluindo adicionar, modificar e excluir propriedades de metadados, use o Editor de esquemas.

>[!NOTE]
>
>Os métodos de edição em massa funcionam para ativos disponíveis em uma pasta ou coleção. Para os ativos que estão disponíveis em pastas ou que correspondem a critérios comuns, é possível atualizar os metadados em massa dos resultados de pesquisa de ativos.

## Editar propriedades de metadados de vários ativos {#editing-metadata-properties-of-multiple-assets}

1. Na interface do usuário do Assets, navegue até o local dos ativos que deseja editar.
1. Selecione os ativos para os quais deseja editar propriedades comuns.
1. Na barra de ferramentas, clique em **[!UICONTROL Properties]** para abrir a página de propriedades dos ativos selecionados.
1. Modifique as propriedades de metadados para ativos selecionados nas várias guias.
1. Para exibir os metadados de um ativo específico, cancele a seleção dos ativos restantes na lista. Se você cancelar a seleção de alguns ativos na página [!UICONTROL Propriedades], os metadados desses ativos não serão atualizados.
1. Para selecionar um esquema de metadados diferente para os ativos, clique em **[!UICONTROL Settings]** na barra de ferramentas e selecione um esquema. Clique em **[!UICONTROL Salvar e fechar]**.
1. Para anexar os novos metadados aos existentes em campos que contêm vários valores, selecione o **[!UICONTROL Modo anexar]**. Se você não selecionar essa opção, os novos metadados substituirão os existentes nos campos. Clique em **[!UICONTROL Enviar]**.

![O esquema de metadados em massa se aplica a vários ativos](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>Em campos de valor único, os novos metadados não são anexados ao valor existente no campo mesmo se você selecionar o **[!UICONTROL Modo anexar]**.

## Configurar limite para atualização de metadados em massa {#configure-limit-for-bulk-metadata-update}

Para evitar uma situação semelhante ao DOS, [!DNL Experience Manager] limita o número de parâmetros suportados em uma solicitação do Sling. Ao atualizar metadados de muitos ativos de uma só vez, você pode atingir o limite e os metadados não são atualizados para mais ativos. [!DNL Experience Manager] gera o seguinte aviso nos logs:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Para alterar o limite, acesse **[!UICONTROL Ferramentas > Operações > Console da Web]** e altere o valor de [!UICONTROL Parâmetros de POST máximo] na configuração OSGi da [!UICONTROL Manipulação de parâmetro da solicitação do Apache].

>[!MORELIKETHIS]
>
>* [Editar metadados de várias coleções em massa](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)

