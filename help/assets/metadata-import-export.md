---
title: Importação e exportação de metadados em massa
description: Este artigo descreve como importar e exportar metadados em massa.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 956cdec4-2ba8-43c9-9122-564d764f4681
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 10%

---

# Importação e exportação de metadados em massa {#bulk-metadata-import-and-export}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

[!DNL Experience Manager] Os ativos permitem importar metadados de ativos em massa usando um arquivo CSV. É possível fazer atualizações em massa dos ativos recém-carregados ou dos ativos existentes ao importar um arquivo CSV. Também é possível assimilar metadados de ativos em massa de sistemas de terceiros no formato CSV.

## Importar metadados {#import-metadata}

A importação de metadados é assíncrona e não impede o desempenho do sistema. A atualização simultânea dos metadados para vários ativos pode consumir muitos recursos devido XMP atividade de write-back se o sinalizador de workflow estiver marcado. Planeje essa importação durante o uso do servidor simplificado para evitar o impacto no desempenho para outros usuários.

>[!NOTE]
>
>Para importar metadados em namespaces personalizados, primeiro registre os namespaces.

Para importar metadados em massa, siga estas etapas:

1. Navegue até a interface do usuário do Assets e toque/clique em **[!UICONTROL Criar]** na barra de ferramentas.
1. No menu, selecione **[!UICONTROL Metadados]**.
1. No **[!UICONTROL Importação de metadados]** toque/clique na página **[!UICONTROL Selecionar arquivo]**.  Selecione o arquivo CSV com os metadados.
1. Verifique se o arquivo CSV contém os seguintes parâmetros:

   | Parâmetros de importação de metadados | Descrição |
   |:---|:---|
   | [!UICONTROL Tamanho do lote] | Número de ativos em um lote para o qual os metadados devem ser importados. O valor padrão é 50. O valor máximo é 100. |
   | [!UICONTROL Separador de campos] | O valor padrão é `,` - uma vírgula. É possível especificar qualquer outro caractere. |
   | [!UICONTROL Delimitador de múltiplo valor] | Separador para valores de metadados. O valor padrão é `|` - um tubo. |
   | [!UICONTROL Inicializar fluxos de trabalho] | False por padrão. Quando definido como true e as configurações padrão estiverem em vigor para a variável `DAM Metadata WriteBack Workflow` (que grava metadados nos dados binários de XMP). Habilitar os workflows tem um impacto no desempenho do sistema. |
   | [!UICONTROL Nome de coluna do caminho do ativo] | Define o nome da coluna para o arquivo CSV com ativos. |

1. Toque/clique **[!UICONTROL Importar]** na barra de ferramentas. Depois que os metadados são importados, uma notificação é enviada para a sua caixa de entrada de Notificação. Navegue até a página de propriedade do ativo e verifique se os valores de metadados foram importados corretamente para os ativos.

Para adicionar data e carimbo de data e hora ao importar metadados, use `YYYY-MM-DDThh:mm:ss.fff-00:00` para data e hora. A data e a hora são separadas por `T`, `hh` é horas no formato de 24 horas, `fff` é nanossegundos e `-00:00` é deslocamento de fuso horário. Por exemplo, `2020-03-26T11:26:00.000-07:00` é 26 de março de 2020 às 11:26:00.000 AM PST time.

>[!CAUTION]
>
>Se o formato de data não corresponder `YYYY-MM-DDThh:mm:ss.fff-00:00`, os valores de data não são definidos. Os formatos de data do arquivo CSV de metadados exportado estão no formato `YYYY-MM-DDThh:mm:ss-00:00`. Se quiser importá-lo, converta-o para o formato aceitável adicionando o valor de nanossegundos indicado por `fff`.

## Exportar metadados {#export-metadata}

Alguns casos de uso para exportar metadados em massa são:

* Importe os metadados em um sistema de terceiros ao migrar ativos.
* Compartilhe metadados de ativos com uma equipe de projeto mais ampla.
* Teste ou faça auditoria dos metadados para fins de conformidade.
* Externalize os metadados para localização separada.

Você pode exportar metadados para vários ativos em um formato CSV. Os metadados são exportados de forma assíncrona e não afetam o desempenho do sistema. Para exportar metadados, [!DNL Experience Manager] percorre as propriedades do nó de ativo `jcr:content/metadata` e seus nós filhos e exporta as propriedades dos metadados em um arquivo CSV.

Para exportar metadados de vários ativos em massa, siga estas etapas:

1. Selecione a pasta de ativos que contém ativos para os quais deseja exportar metadados. Na barra de ferramentas, selecione **[!UICONTROL Exportar metadados]**.

1. No [!UICONTROL Exportação de metadados] , especifique um nome para o arquivo CSV. Para exportar metadados para ativos em subpastas, selecione **[!UICONTROL Incluir ativos em subpastas]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Selecione as opções desejadas. Forneça um nome de arquivo e, se necessário, uma data.
1. No **[!UICONTROL Propriedades a exportar]**, especifique se deseja exportar todas as propriedades ou propriedades específicas. Se você escolher **[!UICONTROL Seletiva]** para serem exportadas, adicione as propriedades desejadas.

1. Na barra de ferramentas, toque/clique **[!UICONTROL Exportar]**. Uma mensagem confirma que os metadados são exportados. Feche a mensagem.

1. Abra a notificação da caixa de entrada do trabalho de exportação. Selecione o trabalho e clique em **[!UICONTROL Abrir]** na barra de ferramentas. Para baixar o arquivo CSV com os metadados, toque/clique em **[!UICONTROL Download de CSV]** na barra de ferramentas. Clique em **[!UICONTROL Fechar]**.

   ![csv_download](assets/csv_download.png)
