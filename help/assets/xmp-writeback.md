---
title: Write-back de XMP a execuções
description: Saiba como o recurso de write-back de XMP propaga as alterações de metadados de um ativo para todas as representações ou representações específicas do ativo.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 456f8c91-aacf-4db5-a329-2d1650ff0f2f
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 4%

---

# Write-back de XMP a execuções {#xmp-writeback-to-renditions}

Esse recurso de write-back de XMP em [!DNL Adobe Experience Manager Assets] replica as alterações de metadados nas representações do ativo original. Ao alterar os metadados de um ativo de dentro do Assets ou ao fazer upload do ativo, as alterações são armazenadas inicialmente no nó de metadados na hierarquia de ativos.

O recurso de write-back de XMP permite propagar as alterações de metadados para todas as representações ou representações específicas do ativo. O recurso grava somente as propriedades de metadados que usam `jcr` namespace, ou seja, uma propriedade chamada `dc:title` é gravada novamente, mas uma propriedade chamada `mytitle` não é.

Considere um cenário em que você modifica a propriedade [!UICONTROL Title] do ativo intitulado `Classic Leather` para `Nylon`.

![metadados](assets/metadata.png)

Nesse caso, os Ativos [!DNL Experience Manager] salvam as alterações na propriedade **[!UICONTROL Title]** no parâmetro `dc:title` para os metadados de ativos armazenados na hierarquia de ativos.

![metadata_stored](assets/metadata_stored.png)

No entanto, [!DNL Experience Manager Assets] não propaga automaticamente quaisquer alterações de metadados nas representações de um ativo. Consulte [como ativar XMP write-back](#enabling-xmp-writeback).

## Ativar XMP write-back {#enabling-xmp-writeback}

Para permitir que as alterações de metadados sejam propagadas para as representações do ativo ao carregá-lo, modifique a configuração **Adobe CQ DAM Rendition Maker** no Configuration Manager.

1. Abra o Configuration Manager a partir de `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra a configuração **[!UICONTROL Adobe CQ DAM Rendition Maker]**.
1. Selecione a opção **[!UICONTROL Propagar XMP]** e salve as alterações.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Habilitar XMP write-back para representações específicas {#enabling-xmp-writeback-for-specific-renditions}

Para permitir que o recurso Writeback de XMP propague alterações de metadados para selecionar representações, especifique essas representações na etapa de fluxo de trabalho Processo de Writeback de XMP do fluxo de trabalho WriteBack de Metadados de DAM . Por padrão, essa etapa é configurada com a representação original.

Para que o recurso Writeback de XMP propague metadados para as miniaturas de representação 140.100.png e 319.319.png, execute estas etapas.

1. No Experience Manager, navegue até **[!UICONTROL Tools > Workflow > Models]**.
1. Na página [!UICONTROL Modelos], abra o modelo de fluxo de trabalho **[!UICONTROL DAM Metadata Writeback]**.
1. Na página de propriedades **[!UICONTROL DAM Metadata Writeback]**, abra a etapa **[!UICONTROL Processo de Writeback XMP]**.
1. Na caixa de diálogo **[!UICONTROL Propriedades da etapa]**, toque/clique na guia **[!UICONTROL Processo]**.
1. Na caixa **[!UICONTROL Argumentos]**, adicione `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. Toque/clique em **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Para regenerar as representações de pirâmide TIFF de imagens do Dynamic Media com os novos atributos, adicione a etapa **[!UICONTROL Ativos de imagem de processo do Dynamic Media]** ao fluxo de trabalho de Writeback de metadados do DAM.
As representações PTIFF são criadas e armazenadas apenas localmente em um modo Híbrido do Dynamic Media. Salve o workflow.

As alterações de metadados são propagadas para as representações `thumbnail.140.100.png` e `thumbnail.319.319.png` do ativo, e não para os outros.

>[!NOTE]
>
>Para XMP problemas de write-back no Linux de 64 bits, consulte [Como ativar XMP write-back no RedHat Linux de 64 bits](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>Para obter mais informações sobre plataformas compatíveis, consulte [XMP pré-requisitos de gravação de metadados](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtrar metadados XMP {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] O suporta a filtragem de lista de bloqueios e lista de permissões de propriedades/nós para metadados de XMP que são lidos de binários de ativos e armazenados no JCR quando os ativos são assimilados.

Filtrar usando uma lista de bloqueios permite importar todas as propriedades de metadados XMP, exceto as propriedades especificadas para exclusão. No entanto, para tipos de ativos como arquivos INDD que têm grandes quantidades de metadados de XMP (por exemplo, 1000 nós com 10.000 propriedades), os nomes de nós a serem filtrados nem sempre são conhecidos antecipadamente. Se a filtragem usando uma lista de bloqueios permitir a importação de um grande número de ativos com vários metadados de XMP, a instância [!DNL Experience Manager] ou cluster poderá encontrar problemas de estabilidade, por exemplo, filas de observação obstruídas.

A filtragem de metadados de XMP por meio do lista de permissões resolve esse problema permitindo definir as propriedades de XMP a serem importadas. Dessa forma, quaisquer propriedades de XMP outras ou desconhecidas são ignoradas. Para ter compatibilidade com versões anteriores, você pode adicionar algumas dessas propriedades ao filtro que usa uma lista de bloqueios.

>[!NOTE]
>
>A filtragem funciona somente nas propriedades derivadas de fontes de XMP em binários de ativos. Para as propriedades derivadas de fontes não XMP, como formatos EXIF e IPTC, a filtragem não funciona. Por exemplo, a data de criação do ativo é armazenada na propriedade chamada `CreateDate` em EXIF TIFF. [!DNL Experience Manager] armazena esse valor no campo de metadados chamado  `exif:DateTimeOriginal`. Como a fonte é uma fonte não XMP, a filtragem não funciona nessa propriedade.

1. Abra o Configuration Manager a partir de `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra a configuração **[!UICONTROL Adobe CQ DAM XmpFilter]**.
1. Para aplicar a filtragem por meio de uma lista de permissões, selecione **[!UICONTROL Aplicar Lista de permissões a XMP Propriedades]** e especifique as propriedades a serem importadas na caixa **[!UICONTROL Nomes XML permitidos para XMP filtragem]**.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. Para filtrar XMP propriedades bloqueadas após aplicar a filtragem via lista de permissões, especifique aquelas na caixa **[!UICONTROL Nomes XML bloqueados para XMP filtragem]**. Salve as alterações.

   >[!NOTE]
   >
   >A opção **[!UICONTROL Aplicar Lista de bloqueios a XMP Propriedades]** é selecionada por padrão. Em outras palavras, a filtragem usando uma lista de bloqueios é ativada por padrão. Para desativar essa filtragem, desmarque a opção **[!UICONTROL Aplicar Lista de bloqueios a XMP Propriedades]**.
