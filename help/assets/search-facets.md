---
title: Pesquisar aspectos
description: Este artigo descreve como criar, modificar e usar facetas de pesquisa no AEM.
contentOwner: AG
feature: Search
role: Admin,Developer
exl-id: ef1c0b57-68cc-460e-ae45-e16b079194c2
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '2530'
ht-degree: 21%

---

# Pesquisar aspectos {#search-facets}

Saiba como criar, modificar e usar facetas de pesquisa no AEM.

Uma implantação corporativa do Adobe Experience Manager (AEM) Assets tem a capacidade de armazenar muitos ativos. Às vezes, encontrar o ativo certo pode ser árduo e demorado se você usar apenas os recursos de pesquisa genéricos do AEM.

Use aspectos de pesquisa no painel Filtros para adicionar mais granularidade à sua experiência de pesquisa e tornar a funcionalidade de pesquisa mais eficiente e versátil. Os aspectos de pesquisa adicionam várias dimensões (predicados) que permitem executar pesquisas mais complexas. O painel Filtros inclui algumas facetas padrão. Você também pode adicionar aspectos de pesquisa personalizados.

Em resumo, os aspectos de pesquisa permitem pesquisar ativos de várias maneiras, em vez de em uma única ordem taxonômica predeterminada. Você pode detalhar facilmente até o nível de detalhes desejado para uma pesquisa mais focada.

Por exemplo, se estiver procurando uma imagem, você pode escolher se deseja um bitmap ou uma imagem vetorial. Você pode reduzir ainda mais o escopo da pesquisa especificando o tipo MIME da imagem. Da mesma forma, ao pesquisar documentos, é possível especificar o formato, por exemplo PDF ou MS Word.

## Adicionar um predicado {#adding-a-predicate}

Os aspectos de pesquisa exibidos no painel Filtros são definidos no formulário de pesquisa subjacente usando predicados. Para exibir mais ou diferentes aspectos, você adiciona predicados ao formulário padrão ou usa um formulário personalizado que inclui facetas de sua escolha.

Para pesquisas de texto completo, adicione o predicado Texto completo ao formulário. Use o predicado Propriedade para procurar ativos que correspondam a uma única propriedade especificada. Use o predicado Opções para pesquisar ativos que correspondam a um ou mais valores para uma propriedade específica. Adicione o predicado Intervalo de datas para pesquisar ativos criados em um intervalo de datas especificado.

1. Toque/clique no logotipo [!DNL Experience Manager] e acesse **[!UICONTROL Ferramentas]** > **[!UICONTROL Geral]** > **[!UICONTROL Pesquisar Forms]**.
1. Na página Pesquisar Forms , selecione **[!UICONTROL Painel de pesquisa do administrador de ativos]** e toque em **Editar** ![aemassets_edit](assets/aemassets_edit.png).

   ![Localize e selecione o Painel de pesquisa do administrador de ativos](assets/assets_admin_searchrail.png)

   Localize e selecione o Painel de pesquisa do administrador de ativos

   >[!NOTE]
   >
   >Para usar a funcionalidade de pesquisa de pastas do **Painel de pesquisa do administrador de ativos** pré-configurado de uma versão anterior [!DNL Experience Manager], execute estas etapas:
   > 
   >1. Navegue até */conf/global/settings/dam/search/facets/assets/jcr:content/items* no CRX-DE.
   >1. Exclua o nó **type**.
   >1. No caminho */libs/settings/dam/search/facets/assets/jcr:content/items*, copie os nós **asset, directory, typeor, excludepaths** e **searchtype** no caminho mencionado na etapa 1.
   >1. Salve as alterações.


1. Na página Editar Forms de pesquisa , arraste um predicado da guia **[!UICONTROL Selecionar predicado]** para o painel principal. Por exemplo, arraste **[!UICONTROL Predicado de propriedade]**.

   ![Arraste e solte um predicado para personalizar os filtros de pesquisa](assets/drag_predicate.png)

   Arraste e solte um predicado para personalizar os filtros de pesquisa

1. Na guia Configurações , insira um rótulo de campo, um texto de espaço reservado e uma descrição para o predicado. Especifique um nome válido para a propriedade de metadados que deseja associar ao predicado.

   O rótulo do cabeçalho na guia Configurações identifica o tipo do predicado selecionado.

   ![Use a guia Configurações para fornecer as opções necessárias de um predicado](assets/settings.png)

   Use a guia Configurações para fornecer as opções necessárias de um predicado

1. No campo **[!UICONTROL Nome da propriedade]**, especifique um nome válido para a propriedade de metadados que deseja associar ao predicado. É o nome com base no qual a pesquisa é realizada. Por exemplo, insira `jcr:content/metadata/dc:description` ou `./jcr:content/metadata/dc:description`.

   Você também pode selecionar um nó existente na caixa de diálogo de seleção.

   ![Associar uma propriedade de metadados a um predicado no campo Nome da propriedade](assets/property_settings.png)

   Associar uma propriedade de metadados a um predicado no campo Nome da propriedade

1. Toque/clique em **[!UICONTROL Visualizar]** ![visualizar](assets/preview.png) para gerar uma visualização do painel Filtros, como ela aparece depois de adicionar o predicado.
1. Revise o layout do predicado no modo de Visualização.

   ![Visualizar o formulário de pesquisa antes de enviar as alterações](assets/preview-1.png)

   Visualizar o formulário de pesquisa antes de enviar as alterações

1. Para fechar a visualização, toque/clique em **[!UICONTROL Fechar]** ![fechar](assets/close.png) no canto superior direito da visualização.
1. Toque em **[!UICONTROL Concluído]** para salvar as configurações.
1. Navegue até o painel Pesquisar na interface do usuário do Assets. O predicado Propriedade é adicionado ao painel.
1. Insira uma descrição para o ativo a ser pesquisado na caixa de texto. Por exemplo, digite &quot;Adobe&quot;. Ao realizar uma pesquisa, os ativos com uma descrição correspondente ao &quot;Adobe&quot; são listados nos resultados da pesquisa.

## Adicionar um predicado de opções {#adding-an-options-predicate}

O predicado Opções permite adicionar várias opções de pesquisa no painel Filtros . Você pode selecionar uma ou mais dessas opções no painel Filtros para procurar ativos. Por exemplo, para pesquisar ativos com base no tipo de arquivo, configure opções, como Imagens, Multimídia, Documentos e Arquivos no formulário de pesquisa. Após configurar essas opções, a pesquisa é executada em ativos do tipo GIF, JPEG, PNG e assim por diante, ao selecionar a opção Imagens no painel Filtros .

Para mapear as opções para a respectiva propriedade, crie uma estrutura de nó para as opções e forneça o caminho do nó pai na propriedade Nome da propriedade do predicado Opções. O nó pai deve ser do tipo `sling`: `OrderedFolder`. As opções devem ser do tipo `nt:unstructured`. Os nós de opção devem ter as propriedades `jcr:title` e `value` configuradas.

A propriedade `jcr:title` é um nome amigável para a opção exibida no painel Filtros. O campo `value` é usado na query para corresponder à propriedade especificada.

Quando você seleciona uma opção, a pesquisa é executada com base na propriedade `value` do nó da opção e seus nós filhos, se houver. Toda a árvore sob o nó option é atravessada e a propriedade `value` de cada nó filho é combinada usando uma operação OR para formar a consulta de pesquisa.

Por exemplo, se você selecionar &quot;Imagens&quot; para tipos de arquivos, a consulta de pesquisa dos ativos será criada ao combinar a propriedade `value` usando uma operação OR. Por exemplo, a consulta de pesquisa de imagens é construída combinando os resultados correspondentes de *image/jpeg*, *image/gif*, *image/png*, *image/pjpeg* e *image/tiff* da propriedade `jcr:content/metadata/dc:format` usando uma operação OR.

![A propriedade Value de um tipo de arquivo, como visto no CRXDE, é usada para que as consultas de pesquisa funcionem](assets/chlimage_1-418.png)

A propriedade Value de um tipo de arquivo, como visto no CRXDE, é usada para que as consultas de pesquisa funcionem

Em vez de criar manualmente uma estrutura de nó para as opções no repositório CRX, defina as opções em um arquivo JSON especificando pares de valores chave correspondentes. Especifique o caminho do arquivo JSON no campo **[!UICONTROL Nome da propriedade]**. Por exemplo, defina os pares de valores chave, `image/bmp`, `image/gif`, `image/jpeg` e `image/png` e especifique os valores, como mostrado no seguinte arquivo JSON de amostra. No campo **[!UICONTROL Nome da propriedade]**, especifique o caminho CRX desse arquivo.

```json
{
    "options" :
 [
          {"value" : "image/bmp","text" : "BMP"},
          {"value" : "image/gif","text" : "GIF"},
          {"value" : "image/jpeg","text" : "JPEG"},
          {"value" : "image/png","text" : "PNG"}
 ]
}
```

Se quiser usar um nó existente, especifique-o usando a caixa de diálogo de seleção.

>[!NOTE]
>
>O predicado Opções é um wrapper personalizado que inclui predicados de propriedade para demonstrar o comportamento descrito. No momento, não há ponto de extremidade REST disponível para oferecer suporte à funcionalidade nativamente.

1. Toque no logotipo [!DNL Experience Manager] e acesse **[!UICONTROL Ferramentas > Geral > Pesquisar Forms]**.
1. Na página **[!UICONTROL Pesquisar formulários]**, selecione **[!UICONTROL Painel de pesquisa do administrador de ativos]** e toque no ícone Editar.
1. Na página **[!UICONTROL Editar formulário de pesquisa]**, arraste o **[!UICONTROL Predicado de opções]** da guia **[!UICONTROL Selecionar predicado]** até o painel principal.
1. Na guia **[!UICONTROL Configurações]**, digite um rótulo e um nome para a propriedade. Por exemplo, para pesquisar ativos com base no formato, especifique um nome amigável para o rótulo, por exemplo, **[!UICONTROL Tipo de arquivo]**. Especifique a propriedade com base na qual a pesquisa deve ser realizada no campo de propriedade, por exemplo `jcr:content/metadata/dc:format.`
1. Faça uma das seguintes opções:

   * No campo **[!UICONTROL Nome da propriedade]**, mencione o caminho do arquivo JSON onde você define os nós das opções e especifica os pares de valores chave correspondentes.
   * Toque em ![Adicionar ícone](assets/do-not-localize/aem_assets_add_icon.png) ao lado do campo Opções para especificar o texto de exibição e o valor das opções que deseja fornecer no painel Filtros. Para adicionar outra opção, toque/clique em ![Add icon](assets/do-not-localize/aem_assets_add_icon.png) e repita a etapa.

1. Certifique-se de que **[!UICONTROL Seleção única]** esteja desmarcada para permitir que o usuário selecione várias opções para tipos de arquivos de cada vez (por exemplo, Imagens, Documentos, Multimídia e Arquivos). Se você marcar **[!UICONTROL Seleção única]**, o usuário poderá selecionar apenas uma opção para tipos de arquivo por vez.

   ![Os campos disponíveis no predicado Opções](assets/options_predicate.png)

   Os campos disponíveis no predicado Opções

1. No campo **Description**, insira uma descrição opcional e clique em **[!UICONTROL Concluído]**.
1. Navegue até o painel Pesquisar . O predicado Opções é adicionado ao painel **Pesquisar**. As opções para **[!UICONTROL Tipo de Arquivo]** são exibidas como caixas de seleção.

## Adicionar um predicado de propriedade de vários valores {#adding-a-multi-value-property-predicate}

O predicado Propriedade de vários valores permite pesquisar ativos por vários valores. Considere um cenário em que você tem imagens de vários produtos em [!DNL Experience Manager] Ativos e os metadados de cada imagem incluem um número SKU associado ao produto. Você pode usar este predicado para procurar imagens de produtos com base em vários números de SKU.

1. Clique no logotipo [!DNL Experience Manager] e acesse **[!UICONTROL Ferramentas]** > **[!UICONTROL Geral]** > **[!UICONTROL Pesquisar Forms]**.
1. Na página Pesquisar Forms , selecione **[!UICONTROL Painel de pesquisa do administrador de ativos]**, toque em **Editar** ![aemassets_edit](assets/aemassets_edit.png).
1. Na página Editar formulário de pesquisa, arraste um **[!UICONTROL Predicado de propriedades de vários valores]** da guia **[!UICONTROL Selecionar predicado]** para o painel principal.
1. Na guia **[!UICONTROL Settings]**, insira um rótulo e um texto de espaço reservado para o predicado. Especifique o nome da propriedade com base no qual a pesquisa deve ser realizada no campo de propriedade, por exemplo `jcr:content/metadata/dc:value`. Também é possível usar a caixa de diálogo de seleção para selecionar um nó.
1. Verifique se a opção **[!UICONTROL Suporte a delimitadores]** está selecionada. No campo **[!UICONTROL Delimitadores de entrada]**, especifique delimitadores para separar valores individuais. Por padrão, a vírgula é especificada como delimitador. É possível especificar um delimitador diferente.
1. No campo **Description**, insira uma descrição opcional e toque em **[!UICONTROL Concluído]**.
1. Navegue até o painel Filtros na interface do usuário do Assets. O predicado **[!UICONTROL Propriedade de vários valores]** é adicionado ao painel.
1. Especifique vários valores no campo Vários valores separados pelos delimitadores e execute a pesquisa. O predicado busca uma correspondência exata de texto para os valores especificados.

## Adicionar um predicado de Tags {#adding-a-tags-predicate}

O predicado de tag permite que você realize pesquisas baseadas em tag para ativos. Por padrão, [!DNL Experience Manager] o Assets pesquisa ativos por uma ou mais tags correspondentes com base nas tags especificadas. Em outras palavras, a consulta de pesquisa executa uma operação OU usando as tags especificadas. No entanto, você pode usar a opção de correspondência de todas as tags para procurar ativos que incluem todas as tags especificadas.

1. Clique no logotipo [!DNL Experience Manager] e acesse **[!UICONTROL Ferramentas]** > **[!UICONTROL Geral]** > **[!UICONTROL Pesquisar Forms]**.
1. Na página Pesquisar Forms , selecione **[!UICONTROL Painel de pesquisa do administrador de ativos]** e toque em **Editar** ![aemassets_edit](assets/aemassets_edit.png).
1. Na página Editar formulário de pesquisa , arraste **[!UICONTROL Predicado de tags]** da guia Selecionar predicado para o painel principal.
1. Na guia Configurações , insira um texto de espaço reservado para o predicado. Especifique o nome da propriedade com base no qual a pesquisa deve ser realizada no campo de propriedade, por exemplo *jcr:content/metadata/cq:tags*. Como alternativa, você pode selecionar um nó no CRXDE na caixa de diálogo de seleção.
1. Configure a propriedade de caminho de tags raiz desse predicado para preencher várias tags na lista Tags.
1. Selecione a opção **[!UICONTROL Mostrar correspondência de todas as tags]** para procurar ativos que incluem todas as tags especificadas.

   ![Configurações típicas do predicado Tags](assets/tags_predicate.png)

   Configurações típicas do predicado Tags

1. No campo **[!UICONTROL Description]**, insira uma descrição opcional e clique/toque em **[!UICONTROL Concluído]**.
1. Navegue até o painel Pesquisar . O predicado **[!UICONTROL Tags]** é adicionado ao painel Pesquisar.
1. Especifique tags com base nas quais deseja pesquisar ativos ou selecione na lista de sugestões.

   ![Sugestão fornecida pelo AEM ao digitar o nome da tag](assets/chlimage_1-419.png)

   Sugestão fornecida pelo AEM ao digitar o nome da tag

1. Selecione **[!UICONTROL Corresponder a todos]** para procurar correspondências que incluam todas as tags especificadas.

## Adicionar outros predicados {#adding-other-predicates}

Semelhante à forma como você adiciona um predicado de Propriedade ou um predicado de Opções, você pode adicionar os seguintes predicados adicionais ao painel Pesquisar:

| Nome do predicado | Descrição | Propriedades |
|---|---|---|
| [!UICONTROL Texto completo] | Predicado de pesquisa para executar a pesquisa de texto completo em um nó de ativo inteiro. Ele é mapeado com o operador jcr:contains . Você pode especificar um caminho relativo se quiser realizar uma pesquisa de texto completo em uma parte específica do nó do ativo. | <ul><li>Etiqueta</li><li>Espaço reservado</li><li>Nome da propriedade</li><li>Descrição</li></ul> |
| [!UICONTROL Navegador de caminhos] | Pesquisar predicado para procurar ativos em pastas e subpastas em um caminho raiz pré-configurado | <ul><li>Espaço reservado</li><li>Caminho raiz</li><li>Descrição</li></ul> |
| [!UICONTROL Caminho] | Use-o para filtrar resultados no local. Você pode especificar caminhos diferentes como opções. | <ul><li>Etiqueta</li><li>Caminho</li><li>Descrição</li></ul> |
| [!UICONTROL Publicar status] | Pesquisar predicado para pesquisar ativos com base em seu status de publicação | <ul><li>Etiqueta</li><li>Nome da propriedade</li><li>Descrição</li></ul> |
| [!UICONTROL Data relativa] | O predicado de pesquisa para pesquisar ativos com base na data relativa de sua criação. Por exemplo, você pode configurar opções, como 2 meses atrás, 3 semanas atrás e assim por diante. | <ul><li>Etiqueta</li><li>Nome da propriedade</li><li>Data relativa</li></ul> |
| [!UICONTROL Intervalo] | predicado de pesquisa para pesquisar ativos que estão em um intervalo especificado. No painel Pesquisar , é possível especificar valores mínimos e máximos para o intervalo. | <ul><li>Etiqueta</li><li>Nome da propriedade</li><li>Descrição</li></ul> |
| [!UICONTROL Intervalo de datas] | Procure por ativos criados em um intervalo especificado para uma propriedade date . No painel Pesquisar , é possível especificar datas de Início e Término usando seletores de data. | <ul><li>Etiqueta</li><li>Espaço reservado</li><li>Nome da propriedade</li><li>Texto do intervalo (de)</li><li>Texto do intervalo (até)</li><li>Descrição</li></ul> |
| [!UICONTROL Data] | Procure por um predicado com base em um controle deslizante de ativos com base em uma propriedade de data. | <ul><li>Etiqueta</li><li>Nome da propriedade</li><li>Descrição</li></ul> |
| [!UICONTROL Tamanho do arquivo] | Predicado de pesquisa para pesquisar ativos com base em seu tamanho. É um predicado baseado em silder onde você seleciona as opções de controle deslizante de um nó configurável. As opções padrão são definidas em /libs/dam/options/predicates/filesize no repositório CRX. O tamanho do arquivo é fornecido em bytes. | <ul><li>Etiqueta</li><li>Nome da propriedade</li><li>Caminho</li><li>Descrição</li></ul> |
| [!UICONTROL Última modificação do ativo] | Pesquisar predicado para pesquisar ativos modificados recentemente | <ul><li>Nome da propriedade</li><li>Valor da propriedade</li><li>Descrição</li></ul> |
| [!UICONTROL Publicar status] | Pesquisar predicado para procurar ativos com base em seu status de publicação | <ul><li>Etiqueta</li><li>Nome da propriedade</li><li>Descrição</li></ul> |
| [!UICONTROL Classificação] | Predicado de pesquisa para pesquisar ativos com base em sua classificação média | <ul><li>Etiqueta</li><li>Nome da propriedade</li><li>Caminho da opção</li><li>Descrição</li></ul> |
| [!UICONTROL Status da expiração] | Pesquisar predicado para procurar ativos com base em seu status de expiração | <ul><li>Etiqueta</li><li>Nome da propriedade</li><li>Descrição</li></ul> |
| [!UICONTROL Oculto] | Procura predicado que define uma propriedade de campo oculto para procurar ativos | <ul><li>Nome da propriedade</li><li>Valor da propriedade</li><li>Descrição</li></ul> |

## Restauração de aspectos de pesquisa padrão {#restoring-default-search-facets}

Por padrão, um ícone Bloquear é exibido antes de **[!UICONTROL Painel de pesquisa do administrador de ativos]** na página **[!UICONTROL Pesquisar Forms]**. O ícone Bloquear desaparece se você adicionar facetas de pesquisa ao formulário, indicando que o formulário padrão foi modificado.

![Ícone de cadeado em relação a uma opção na página Pesquisar Forms indica que as configurações padrão estão intactas e não são personalizadas.](assets/locked_admin_rail.png)

Ícone de cadeado em relação a uma opção na página Pesquisar Forms indica que as configurações padrão estão intactas e não são personalizadas.

Para restaurar o aspecto de pesquisa padrão, execute estas etapas:

1. Selecione **[!UICONTROL Painel de pesquisa do administrador de ativos]** na página **[!UICONTROL Pesquisar Forms]**.
1. Toque em **[!UICONTROL Excluir]** ![deleteoutline](assets/deleteoutline.png) na barra de ferramentas.
1. Na caixa de diálogo de confirmação, toque em **[!UICONTROL Delete]** para remover as alterações personalizadas.

   Após excluir as alterações personalizadas nos aspectos de pesquisa, o ícone Bloquear será exibido novamente antes do **[!UICONTROL Painel de pesquisa do administrador de ativos]** na página **[!UICONTROL Formulários de pesquisa]**.

## Permissões do usuário {#user-permissions}

Se você não tiver uma função de administrador, esta é uma lista de permissões necessárias para executar ações de edição, exclusão e visualização envolvendo aspectos de pesquisa.

| Ação | Permissões |
|---|---|
| [!UICONTROL Editar] | Permissões de leitura e gravação no nó /apps no CRX |
| [!UICONTROL Excluir] | Permissões de leitura, gravação e exclusão no nó /apps no CRX |
| [!UICONTROL Visualizar] | Permissões de leitura, gravação e exclusão no nó /var/dam/content no CRX. Além disso, permissões de leitura e gravação no nó /apps. |

>[!MORELIKETHIS]
>
>* [Estender pesquisa do Assets](searchx.md)
>* [Pesquisar ativos](search-assets.md)
>* [Pesquisar ativos de vídeo](search-video-assets.md)

