---
title: Importação e exportação de metadados em massa
description: Este artigo descreve como importar e exportar metadados em massa.
contentOwner: AG
feature: Metadata
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 9%

---


# Importação e exportação de metadados em massa {#bulk-metadata-import-and-export}

O AEM Assets permite importar metadados de ativos em massa usando um arquivo CSV. É possível fazer atualizações em massa dos ativos recém-carregados ou dos ativos existentes ao importar um arquivo CSV. Também é possível assimilar metadados de ativos em massa de sistemas de terceiros no formato CSV.

## Importar metadados {#import-metadata}

A importação de metadados é assíncrona e não impede o desempenho do sistema. A atualização simultânea dos metadados para vários ativos pode consumir muitos recursos devido XMP atividade de write-back se o sinalizador de workflow estiver marcado. Planeje essa importação durante o uso do servidor simplificado para evitar o impacto no desempenho para outros usuários.

>[!NOTE]
>
>Para importar metadados em namespaces personalizados, primeiro registre os namespaces.

Para importar metadados em massa, siga estas etapas:

1. Navegue até a interface do usuário do Assets e toque/clique em **[!UICONTROL Criar]** na barra de ferramentas.
1. No menu, selecione **[!UICONTROL Metadados]**.
1. Na página **[!UICONTROL Importação de metadados]**, toque/clique em **[!UICONTROL Selecionar arquivo]**.  Selecione o arquivo CSV com os metadados.
1. Verifique se o arquivo CSV contém os seguintes parâmetros:

   | Parâmetros de importação de metadados | Descrição |
   |:---|:---|
   | [!UICONTROL Tamanho do lote] | Número de ativos em um lote para o qual os metadados devem ser importados. O valor padrão é 50. O valor máximo é 100. |
   | [!UICONTROL Separador de campos] | O valor padrão é `,` - uma vírgula. É possível especificar qualquer outro caractere. |
   | [!UICONTROL Delimitador de múltiplo valor] | Separador para valores de metadados. O valor padrão é `|` - uma barra vertical. |
   | [!UICONTROL Inicializar fluxos de trabalho] | False por padrão. Quando definido como verdadeiro e as configurações padrão do Iniciador estão em vigor para `DAM Metadata WriteBack Workflow` (que grava metadados nos dados de XMP binários). Habilitar workflows de inicialização tem um impacto no desempenho do sistema. |
   | [!UICONTROL Nome de coluna do caminho do ativo] | Define o nome da coluna para o arquivo CSV com ativos. |

1. Toque/clique em **[!UICONTROL Importar]** na barra de ferramentas. Depois que os metadados são importados, uma notificação é enviada para a sua caixa de entrada de Notificação. Navegue até a página de propriedade do ativo e verifique se os valores de metadados foram importados corretamente para os ativos.

Para adicionar data e carimbo de data e hora ao importar metadados, use o formato `YYYY-MM-DDThh:mm:ss.fff-00:00` para data e hora. Data e hora são separadas por `T`, `hh` é hora no formato de 24 horas, `fff` é nanossegundos e `-00:00` é deslocamento de fuso horário. Por exemplo, `2020-03-26T11:26:00.000-07:00` é 26 de março de 2020 às 11:26:00.000 da hora do horário PST.

>[!CAUTION]
>
>Se o formato de data não corresponder a `YYYY-MM-DDThh:mm:ss.fff-00:00`, os valores de data não serão definidos. Os formatos de data do arquivo CSV de metadados exportado estão no formato `YYYY-MM-DDThh:mm:ss-00:00`. Se quiser importá-lo, converta-o no formato aceitável adicionando o valor de nanossegundos indicado por `fff`.

## Exportar metadados {#export-metadata}

Alguns casos de uso para exportar metadados em massa são:

* Importe os metadados em um sistema de terceiros ao migrar ativos.
* Compartilhe metadados de ativos com uma equipe de projeto mais ampla.
* Teste ou faça auditoria dos metadados para fins de conformidade.
* Externalize os metadados para localização separada.

Você pode exportar metadados para vários ativos em um formato CSV. Os metadados são exportados de forma assíncrona e não afetam o desempenho do sistema. Para exportar metadados, AEM percorre as propriedades do nó do ativo `jcr:content/metadata` e seus nós filhos e exporta as propriedades de metadados em um arquivo CSV.

Para exportar metadados de vários ativos em massa, siga estas etapas:

1. Selecione a pasta de ativos que contém ativos para os quais deseja exportar metadados. Na barra de ferramentas, selecione **[!UICONTROL Export metadata]**.

1. Na caixa de diálogo [!UICONTROL Exportação de metadados], especifique um nome para o arquivo CSV. Para exportar metadados para ativos em subpastas, selecione **[!UICONTROL Incluir ativos em subpastas]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Selecione as opções desejadas. Forneça um nome de arquivo e, se necessário, uma data.
1. Nas **[!UICONTROL Propriedades a serem exportadas]**, especifique se deseja exportar todas as propriedades ou propriedades específicas. Se você escolher **[!UICONTROL Seletivo]** propriedades a serem exportadas, adicione as propriedades desejadas.

1. Na barra de ferramentas, toque/clique em **[!UICONTROL Exportar]**. Uma mensagem confirma que os metadados são exportados. Feche a mensagem.

1. Abra a notificação da caixa de entrada do trabalho de exportação. Selecione o trabalho e clique em **[!UICONTROL Abrir]** na barra de ferramentas. Para baixar o arquivo CSV com os metadados, toque/clique em **[!UICONTROL Download de CSV]** na barra de ferramentas. Clique em **[!UICONTROL Fechar]**.

   ![csv_download](assets/csv_download.png)
