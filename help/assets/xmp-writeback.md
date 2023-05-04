---
title: XMP gravação em representações
description: Saiba como o recurso de write-back de XMP propaga as alterações de metadados de um ativo para todas as representações ou representações específicas do ativo.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 456f8c91-aacf-4db5-a329-2d1650ff0f2f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 4%

---

# XMP gravação em representações {#xmp-writeback-to-renditions}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Este recurso de write-back de XMP em [!DNL Adobe Experience Manager Assets] replica as alterações de metadados nas representações do ativo original. Ao alterar os metadados de um ativo de dentro do Assets ou ao fazer upload do ativo, as alterações são armazenadas inicialmente no nó de metadados na hierarquia de ativos.

O recurso de write-back de XMP permite propagar as alterações de metadados para todas as representações ou representações específicas do ativo. O recurso grava somente as propriedades de metadados que usam `jcr` namespace, ou seja, uma propriedade chamada `dc:title` é gravado de volta, mas uma propriedade chamada `mytitle` não é.

Considere um cenário em que você modifica a variável [!UICONTROL Título] propriedade do ativo intitulado `Classic Leather` para `Nylon`.

![metadados](assets/metadata.png)

Nesse caso, a variável [!DNL Experience Manager] Os ativos salvam as alterações no **[!UICONTROL Título]** na `dc:title` para os metadados do ativo armazenados na hierarquia de ativos.

![metadata_stored](assets/metadata_stored.png)

No entanto, [!DNL Experience Manager Assets] não propaga automaticamente qualquer alteração de metadados nas representações de um ativo. Consulte [como habilitar XMP write-back](#enabling-xmp-writeback).

## Ativar XMP write-back {#enabling-xmp-writeback}

Para permitir que as alterações de metadados sejam propagadas para as representações do ativo ao carregá-lo, modifique o **Criador de representação do Adobe CQ DAM** no Configuration Manager.

1. Abra o Configuration Manager de `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra o **[!UICONTROL Criador de representação do Adobe CQ DAM]** configuração.
1. Selecione o **[!UICONTROL Propagar XMP]** e salve as alterações.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Habilitar XMP write-back para representações específicas {#enabling-xmp-writeback-for-specific-renditions}

Para permitir que o recurso Writeback de XMP propague alterações de metadados para selecionar representações, especifique essas representações na etapa de fluxo de trabalho Processo de Writeback de XMP do fluxo de trabalho WriteBack de Metadados de DAM . Por padrão, essa etapa é configurada com a representação original.

Para que o recurso Writeback de XMP propague metadados para as miniaturas de representação 140.100.png e 319.319.png, execute estas etapas.

1. No Experience Manager, navegue até **[!UICONTROL Ferramentas > Fluxo de trabalho > Modelos]**.
1. No [!UICONTROL Modelos] , abra o **[!UICONTROL Writeback de metadados DAM]** modelo de fluxo de trabalho.
1. Na página de propriedades **[!UICONTROL DAM Metadata Writeback]**, abra a etapa **[!UICONTROL Processo de Writeback XMP]**.
1. Na caixa de diálogo **[!UICONTROL Propriedades da etapa]**, toque/clique na guia **[!UICONTROL Processo]**.
1. No **[!UICONTROL Argumentos]** caixa, adicionar `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. Toque/clique **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Para regenerar as representações de TIFF de pirâmide de imagens do Dynamic Media com os novos atributos, adicione o **[!UICONTROL Ativos de imagem de processo Dynamic Media]** para o fluxo de trabalho DAM Metadata Writeback .
As representações PTIFF são criadas e armazenadas apenas localmente em um modo Híbrido do Dynamic Media. Salve o workflow.

As alterações de metadados são propagadas para as representações `thumbnail.140.100.png` e `thumbnail.319.319.png` do ativo, e não dos outros.

>[!NOTE]
>
>Para XMP problemas de write-back no Linux de 64 bits, consulte [Como habilitar XMP write-back no RedHat Linux de 64 bits](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>Para obter mais informações sobre plataformas compatíveis, consulte [Pré-requisitos de gravação de metadados de XMP](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtrar metadados XMP {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] O suporta a filtragem de lista de bloqueios e lista de permissões de propriedades/nós para metadados de XMP que são lidos de binários de ativos e armazenados no JCR quando os ativos são assimilados.

Filtrar usando uma lista de bloqueios permite importar todas as propriedades de metadados XMP, exceto as propriedades especificadas para exclusão. No entanto, para tipos de ativos como arquivos INDD que têm grandes quantidades de metadados de XMP (por exemplo, 1000 nós com 10.000 propriedades), os nomes de nós a serem filtrados nem sempre são conhecidos antecipadamente. Se a filtragem com uma lista de bloqueios permitir que um grande número de ativos com vários metadados de XMP seja importado, a variável [!DNL Experience Manager] instância ou cluster pode encontrar problemas de estabilidade, por exemplo, filas de observação obstruídas.

A filtragem de metadados de XMP por meio do lista de permissões resolve esse problema permitindo definir as propriedades de XMP a serem importadas. Dessa forma, quaisquer propriedades de XMP outras ou desconhecidas são ignoradas. Para ter compatibilidade com versões anteriores, você pode adicionar algumas dessas propriedades ao filtro que usa uma lista de bloqueios.

>[!NOTE]
>
>A filtragem funciona somente nas propriedades derivadas de fontes de XMP em binários de ativos. Para as propriedades derivadas de fontes não XMP, como formatos EXIF e IPTC, a filtragem não funciona. Por exemplo, a data de criação do ativo é armazenada na propriedade chamada `CreateDate` no TIFF EXIF. [!DNL Experience Manager] armazena esse valor no campo de metadados chamado `exif:DateTimeOriginal`. Como a fonte é uma fonte não XMP, a filtragem não funciona nessa propriedade.

1. Abra o Configuration Manager de `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra o **[!UICONTROL Adobe CQ DAM XmpFilter]** configuração.
1. Para aplicar a filtragem por meio de uma lista de permissões, selecione **[!UICONTROL Aplicar Lista de permissões às propriedades XMP]** e especifique as propriedades que serão importadas no **[!UICONTROL Nomes XML permitidos para filtragem de XMP]** caixa.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. Para filtrar as propriedades de XMP bloqueadas após aplicar a filtragem por lista de permissões, especifique as propriedades no **[!UICONTROL Nomes XML bloqueados para filtragem de XMP]** caixa. Salve as alterações.

   >[!NOTE]
   >
   >O **[!UICONTROL Aplicar Lista de bloqueios às propriedades XMP]** é selecionada por padrão. Em outras palavras, a filtragem usando uma lista de bloqueios é ativada por padrão. Para desativar essa filtragem, desmarque a opção **[!UICONTROL Aplicar Lista de bloqueios às propriedades XMP]** opção.
