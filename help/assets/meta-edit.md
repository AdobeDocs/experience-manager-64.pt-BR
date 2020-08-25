---
title: Como editar ou adicionar metadados
description: Saiba mais sobre os metadados de ativos no AEM Assets e sobre as várias maneiras pelas quais você pode editar os metadados de ativos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: e9f50a1ddb6a162737e6e83b976f96911b3246d6
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 8%

---


# Como editar ou adicionar metadados {#how-to-edit-or-add-metadata}

Metadados são informações adicionais sobre o ativo que pode ser pesquisado. Ele é extraído automaticamente quando você carrega uma imagem. Você pode editar os metadados existentes ou adicionar novas propriedades de metadados a campos existentes (por exemplo, quando um campo de metadados estiver em branco).

Como o empresa precisa de vocabulários de metadados controlados e confiáveis, a AEM Assets não permite a adição ad hoc de novas propriedades de metadados. Embora os autores não possam adicionar novos campos de metadados para ativos, os desenvolvedores podem. Consulte [Criação de nova propriedade de metadados para ativos](meta-edit.md#editing-metadata-schema).

## Editar metadados para um ativo {#editing-metadata-for-an-asset}

Para editar metadados:

1. Faça uma das seguintes opções:

   * Na interface do usuário Ativos, selecione o ativo e clique/toque no ícone Propriedades **[!UICONTROL da]** Visualização na barra de ferramentas.
   * Na miniatura do ativo, selecione a ação rápida Propriedades **[!UICONTROL da]** Visualização.
   * Na página do ativo, clique/toque no ícone Propriedades **[!UICONTROL da]** Visualização ícone ![informações da barra de ferramentas](assets/do-not-localize/info_icon.png) .

   A página do ativo exibe todos os metadados do ativo. Esses metadados foram extraídos automaticamente quando foram carregados (assimilados) no AEM Assets.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Faça edições nos metadados em várias guias, conforme necessário, e quando concluído, clique/toque em **[!UICONTROL Salvar]** na barra de ferramentas para salvar as alterações. Clique/toque em **[!UICONTROL Fechar]** para retornar à interface da Web do Assets.

   >[!NOTE]
   >
   >Se um campo de texto estiver vazio, não há metadados definidos. Você pode inserir um valor no campo e salvá-lo para adicionar essa propriedade de metadados.

Quaisquer alterações nos metadados de um ativo são gravadas de volta no binário original como parte de seus dados XMP. Isso é feito por meio do fluxo de trabalho de gravação de metadados AEM. As alterações feitas nas propriedades existentes (como `dc:title`) são substituídas e as propriedades recém-criadas (incluindo propriedades personalizadas como `cq:tags`) são adicionadas ao schema.

XMP write-back é compatível e habilitado para as plataformas e formatos de arquivo descritos em Requisitos [técnicos.](/help/sites-deploying/technical-requirements.md)

## Edição do Schema de metadados {#editing-metadata-schema}

Para obter detalhes sobre como editar schemas de metadados, consulte [Edição de formulários](metadata-schemas.md#editing-metadata-schema-forms)de schema de metadados.

## Registrando uma namespace personalizada no AEM {#registering-a-custom-namespace-within-aem}

Você pode adicionar suas próprias namespaces dentro do AEM. Assim como há namespaces predefinidas, como cq, jcr e sling, você pode ter uma namespace para os metadados do repositório e o processamento xml.

1. Vá para a página de administração do tipo de nó `https://[AEM_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Clique ou toque em **[!UICONTROL Namespaces]** na parte superior da página. A página de administração da namespace é exibida em uma janela.

1. Para adicionar uma namespace, clique ou toque em **[!UICONTROL Novo]** na parte inferior.
1. Especifique uma namespace personalizada na convenção de namespace XML (especifique a ID na forma de um URI e um prefixo associado para a ID) e clique ou toque em **[!UICONTROL Salvar]**.

## Dicas e limitações {#best-practices-limitations}

* Os metadados são atualizados por interface de usuário sensível ao toque e alteram as propriedades dos metadados na `dc` namespace. Qualquer atualização feita por meio da API HTTP altera as propriedades de metadados na `jcr` namespace. Consulte [como atualizar metadados usando a API](/help/assets/mac-api-assets.md#update-asset-metadata)HTTP.

>[!MORELIKETHIS]
>
>* [Sobre metadados e suas necessidades em ativos](metadata.md)