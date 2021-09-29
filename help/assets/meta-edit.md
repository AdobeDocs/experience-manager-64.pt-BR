---
title: Como editar ou adicionar metadados
description: Saiba mais sobre metadados de ativos no [!DNL Experience Manager] Assets e de várias maneiras pelas quais você pode editar metadados de ativos.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: f0522343-f8a9-4d89-8ce8-b3357ae3fe70
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 8%

---

# Como editar ou adicionar metadados {#how-to-edit-or-add-metadata}

Os metadados são informações adicionais sobre o ativo que pode ser pesquisado. Ele é automaticamente extraído quando você carrega uma imagem. É possível editar os metadados existentes ou adicionar novas propriedades de metadados a campos existentes (por exemplo, quando um campo de metadados está em branco).

Como as empresas precisam de vocabulários de metadados controlados e confiáveis, os ativos [!DNL Experience Manager] não permitem a adição ad hoc de novas propriedades de metadados. Embora os autores não possam adicionar novos campos de metadados para ativos, os desenvolvedores podem. Consulte [Criar nova propriedade de metadados para Assets](meta-edit.md#editing-metadata-schema).

## Editar metadados para um ativo {#editing-metadata-for-an-asset}

Para editar metadados:

1. Faça uma das seguintes opções:

   * Na interface do usuário do Assets, selecione o ativo e clique/toque no ícone **[!UICONTROL Exibir propriedades]** na barra de ferramentas.
   * Na miniatura do ativo, selecione a ação rápida **[!UICONTROL Exibir propriedades]** .
   * Na página de ativos, clique/toque no ícone **[!UICONTROL Exibir propriedades]** ![ícone de informações](assets/do-not-localize/info_icon.png) na barra de ferramentas.

   A página de ativo exibe todos os metadados do ativo. Esses metadados eram extraídos automaticamente quando eram carregados (assimilados) nos [!DNL Experience Manager] Ativos.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Faça edições nos metadados em várias guias, conforme necessário, e quando concluído, clique/toque em **[!UICONTROL Salvar]** na barra de ferramentas para salvar as alterações. Clique/toque em **[!UICONTROL Fechar]** para retornar à interface da Web do Assets.

   >[!NOTE]
   >
   >Se um campo de texto estiver vazio, não há nenhum conjunto de metadados existente. Você pode inserir um valor no campo e salvá-lo para adicionar essa propriedade de metadados.

Quaisquer alterações nos metadados de um ativo são gravadas de volta no binário original como parte de seus dados de XMP. Isso é feito por meio AEM fluxo de trabalho de write-back de metadados. As alterações feitas nas propriedades existentes (como `dc:title`) são substituídas e as propriedades recém-criadas (incluindo propriedades personalizadas como `cq:tags`) são adicionadas juntamente com o schema .

XMP gravação é suportada e ativada para as plataformas e formatos de arquivo descritos em [Requisitos técnicos.](/help/sites-deploying/technical-requirements.md)

## Editar esquema de metadados {#editing-metadata-schema}

Para obter detalhes sobre como editar o esquema de metadados, consulte [Edição de formulários de esquema de metadados](metadata-schemas.md#editing-metadata-schema-forms).

## Registrando um namespace personalizado em [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

Você pode adicionar seus próprios namespaces no AEM. Assim como há namespaces predefinidos, como cq, jcr e sling, você pode ter um namespace para os metadados do repositório e o processamento xml.

1. Vá para a página de administração do tipo de nó `https://[AEM_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Clique ou toque em **[!UICONTROL Namespaces]** na parte superior da página. A página de administração do namespace é exibida em uma janela.

1. Para adicionar um namespace, clique ou toque em **[!UICONTROL New]** na parte inferior.
1. Especifique um namespace personalizado na convenção de namespace XML (especifique a id no formato de um URI e um prefixo associado para a id) e clique ou toque em **[!UICONTROL Salvar]**.

## Dicas e limitações {#best-practices-limitations}

* As atualizações de metadados por meio da interface de usuário de toque alteram as propriedades dos metadados no namespace `dc`. Qualquer atualização feita por meio da API HTTP altera as propriedades dos metadados no namespace `jcr`. Consulte [como atualizar metadados usando a API HTTP](/help/assets/mac-api-assets.md#update-asset-metadata).

>[!MORELIKETHIS]
>
>* [Sobre metadados e sua necessidade no Assets](metadata.md)

