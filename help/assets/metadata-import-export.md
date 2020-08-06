---
title: Importação e exportação de metadados em massa
description: Este artigo descreve como importar e exportar metadados em massa.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 254a9dec248255f8f76db3531c65b54fb4ebff0c
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 9%

---


# Importação e exportação de metadados em massa {#bulk-metadata-import-and-export}

A AEM Assets permite importar metadados de ativos em massa usando um arquivo CSV. É possível fazer atualizações em massa para os ativos carregados recentemente ou os ativos existentes importando um arquivo CSV. Você também pode assimilar metadados de ativos em massa de sistemas de terceiros em formato CSV.

## Importar metadados {#import-metadata}

A importação de metadados é assíncrona e não impede o desempenho do sistema. A atualização simultânea dos metadados para vários ativos pode exigir muitos recursos devido à atividade de gravação XMP caso o sinalizador de fluxo de trabalho esteja marcado. Planeje tal importação durante o uso de servidor simplificado para evitar o impacto no desempenho de outros usuários.

>[!NOTE]
>
>Para importar metadados em namespaces personalizadas, registre primeiro as namespaces.

Para importar metadados em massa, siga estas etapas:

1. Navegue até a interface do usuário Ativos e toque/clique em **[!UICONTROL Criar]** na barra de ferramentas.
1. No menu, selecione **[!UICONTROL Metadados]**.
1. On the **[!UICONTROL Metadata Import]** page, tap/click the **[!UICONTROL Select File]**.  Selecione o arquivo CSV com os metadados.
1. Verifique se o arquivo CSV contém os seguintes parâmetros:

   | Parâmetros de importação de metadados | Descrição |
   |:---|:---|
   | [!UICONTROL Tamanho do lote] | Número de ativos em um lote para os quais os metadados devem ser importados. O valor padrão é 50. O valor máximo é 100. |
   | [!UICONTROL Separador de campos] | O valor padrão é `,` - uma vírgula. É possível especificar qualquer outro caractere. |
   | [!UICONTROL Delimitador de múltiplo valor] | Separador para valores de metadados. O valor padrão é `|` - um pipe. |
   | [!UICONTROL Inicializar fluxos de trabalho] | False por padrão. Quando definidas como true e as configurações padrão do Iniciador estiverem em vigor para o `DAM Metadata WriteBack Workflow` (que grava metadados nos dados binários XMP). Habilitar workflows de inicialização tem um impacto no desempenho do sistema. |
   | [!UICONTROL Nome de coluna do caminho do ativo] | Define o nome da coluna para o arquivo CSV com ativos. |

1. Toque/clique em **[!UICONTROL Importar]** na barra de ferramentas. Depois que os metadados são importados, uma notificação é enviada para sua caixa de entrada de Notificação. Navegue até a página de propriedades do ativo e verifique se os valores de metadados foram importados corretamente para ativos.

Para adicionar data e carimbo de data e hora ao importar metadados, use o `YYYY-MM-DDThh:mm:ss.fff-00:00` formato para data e hora. A data e a hora são separadas por `T`, `hh` é horas no formato de 24 horas, `fff` é nanossegundos e `-00:00` é deslocamento de fuso horário. Por exemplo, `2020-03-26T11:26:00.000-07:00` é 26 de março de 2020 às 11:26:00.000 da hora PST.

>[!CAUTION]
>
>Se o formato de data não corresponder `YYYY-MM-DDThh:mm:ss.fff-00:00`, os valores de data não serão definidos. Os formatos de data do arquivo CSV de metadados exportados estão no formato `YYYY-MM-DDThh:mm:ss-00:00`. Se desejar importá-lo, converta-o no formato aceitável adicionando o valor de nanossegundos indicado por `fff`.

## Exportar metadados {#export-metadata}

Alguns casos de uso para exportar metadados em massa são:

* Importe os metadados em um sistema de terceiros ao migrar ativos.
* Compartilhe metadados de ativos com uma equipe de projeto mais ampla.
* Teste ou audite os metadados para verificar a conformidade.
* Externalize os metadados para localização separada.

É possível exportar metadados para vários ativos em um formato CSV. Os metadados são exportados de forma assíncrona e não afetam o desempenho do sistema. Para exportar metadados, AEM percorre as propriedades do nó do ativo `jcr:content/metadata` e seus nós filhos e exporta as propriedades de metadados em um arquivo CSV.

Para exportar metadados de vários ativos em massa, siga estas etapas:

1. Selecione a pasta de ativos que contém os ativos para os quais deseja exportar metadados. Na barra de ferramentas, selecione **[!UICONTROL Exportar metadados]**.

1. Na caixa de diálogo Exportação [!UICONTROL de] metadados, especifique um nome para o arquivo CSV. Para exportar metadados para ativos em subpastas, selecione **[!UICONTROL Incluir ativos em subpastas]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Selecione as opções desejadas. Forneça um nome de arquivo e, se necessário, uma data.
1. Nas **[!UICONTROL Propriedades a serem exportadas]**, especifique se deseja exportar todas as propriedades ou propriedades específicas. Se você escolher Propriedades **[!UICONTROL seletivas]** a serem exportadas, adicione as propriedades desejadas.

1. Na barra de ferramentas, toque/clique em **[!UICONTROL Exportar]**. Uma mensagem confirma que os metadados são exportados. Feche a mensagem.

1. Abra a notificação da caixa de entrada do trabalho de exportação. Selecione o trabalho e clique em **[!UICONTROL Abrir]** na barra de ferramentas. Para baixar o arquivo CSV com os metadados, toque/clique em **[!UICONTROL Download de CSV]** na barra de ferramentas. Clique em **[!UICONTROL Fechar]**.

   ![csv_download](assets/csv_download.png)
