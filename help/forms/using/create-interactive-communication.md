---
title: Criar uma comunicação interativa
seo-title: Create an Interactive Communication
description: Crie uma Comunicação interativa usando o editor de Comunicação interativa. Use a funcionalidade de arrastar e soltar para criar a Comunicação interativa e pré-visualize as saídas de impressão e da Web em diferentes tipos de dispositivos.
seo-description: Create an Interactive Communication using the Interactive Communication editor. Use drag-and-drop functionality to build the Interactive Communication, and preview both print and web outputs on different device types.
uuid: b98e9a49-cef2-42f2-b484-8765b859895b
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c106aa41-cbc0-4daf-9ac6-6c0d23710010
feature: Interactive Communication
exl-id: a65b775d-040c-4069-b43a-6815be959b31
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3156'
ht-degree: 2%

---

# Criar uma comunicação interativa  {#create-an-interactive-communication}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Crie uma Comunicação interativa usando o editor de Comunicação interativa. Use a funcionalidade de arrastar e soltar para criar a Comunicação interativa e pré-visualize as saídas de impressão e da Web em diferentes tipos de dispositivos.

## Visão geral {#overview}

As Comunicações interativas centralizam e gerenciam a criação, montagem e delivery personalizado e correspondências interativas. Utilize a impressão como canal principal para a Web, você pode minimizar a duplicação de esforços na criação da saída da Web da Comunicação interativa.

### Pré-requisitos {#prerequisites}

A seguir estão os pré-requisitos para a criação de uma Comunicação Interativa:

* Configure um [Modelo de dados do formulário](/help/forms/using/data-integration.md) contendo dados de teste ou com uma fonte de dados real, como uma instância do Microsoft® Dynamics.
* Certifique-se de ter a [Fragmentos de documento](/help/forms/using/document-fragments.md).
* Certifique-se de que [Modelos para impressão e canal da Web](/help/forms/using/web-channel-print-channel.md).
* Certifique-se de que você tenha o [tema](/help/forms/using/themes.md) para o canal da Web.

## Criar a comunicação interativa {#createic}

1. Faça logon na instância do autor do AEM e navegue até **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms &amp; Documents]**.
1. Toque **[!UICONTROL Criar]** e selecione **[!UICONTROL Comunicação interativa]**. A página Criar comunicação interativa é exibida.

   ![create-interative-communication](assets/create-interactive-communication.png)

1. Insira as seguintes informações. :

   * **[!UICONTROL Título]**: Insira o título da Comunicação interativa.
   * **[!UICONTROL Nome*]**: O nome da Comunicação interativa é derivado do título inserido. Edite-a, se necessário.
   * **[!UICONTROL Descrição]**: Insira uma descrição sobre a Comunicação interativa.
   * **[!UICONTROL Modelo de dados do formulário*]**: Navegue e selecione o modelo de dados de formulário. Para obter mais informações sobre o Modelo de dados de formulário, consulte [Integração de dados do AEM Forms](/help/forms/using/data-integration.md).
   * **[!UICONTROL Serviço de preenchimento prévio]**: Selecione o serviço de preenchimento prévio para recuperar os dados e preencher previamente a Comunicação interativa.
   * **[!UICONTROL Tipo de pós-processo]**: Você pode selecionar AEM ou Forms workflow a ser acionado quando a Comunicação interativa for enviada. Selecione o tipo de workflow a ser acionado.
   * **[!UICONTROL Processo de postagem]**: Selecione o nome do workflow a ser acionado. Ao selecionar AEM fluxo de trabalho, forneça Attachment Path, Layout Path, PDF Path, Print Data Path e Web Data Path.
   * **[!UICONTROL Tags]**: Selecione as tags a serem aplicadas à Comunicação interativa. Você também pode digitar um nome de tag novo/personalizado e pressionar Enter para criá-lo.
   * **[!UICONTROL Autor]**: o nome do autor é obtido automaticamente do nome de usuário do usuário conectado.
   * **[!UICONTROL Data de publicação:]** Insira a data para publicar a Comunicação interativa.
   * **[!UICONTROL Data de cancelamento da publicação]**: Insira a data para cancelar a publicação da Comunicação interativa.

1. Toque **[!UICONTROL Próximo]**. A tela para especificar detalhes do canal da Web e da impressão é exibida.
1. Insira o seguinte:

   * **[!UICONTROL Imprimir]**: Selecione essa opção para gerar o canal de impressão da Comunicação interativa.
   * **[!UICONTROL Modelo de impressão*:]** Procure e selecione um XDP como modelo de impressão.
   * **[!UICONTROL Use Imprimir Como Principal Para Canal Da Web:]** Selecione essa opção para criar o canal da Web em sincronia com o canal de impressão. Usar o canal de impressão como principal para o canal da Web garante que o conteúdo e o vínculo de dados do canal da Web sejam derivados do canal de impressão e as alterações feitas no canal de impressão sejam refletidas no canal da Web quando você tocar em Sincronizar. Os autores, no entanto, têm permissão para quebrar a herança de componentes específicos no canal da Web, conforme necessário. Para obter mais informações, consulte [Sincronizar canal Web com canal de impressão](/help/forms/using/create-interactive-communication.md#synchronize).
   * **[!UICONTROL Web:]** Selecione essa opção para gerar o canal da Web ou o resultado responsivo da Comunicação interativa.
   * **[!UICONTROL Modelo Web de Comunicação Interativa*:]** Procure e selecione o modelo da Web.
   * **[!UICONTROL Tema]** e **[!UICONTROL Selecionar Tema*]**: Navegue e selecione o tema para criar um estilo no canal da Web da Comunicação interativa. Para obter mais informações, consulte [Temas no AEM Forms](/help/forms/using/themes.md).
   Para obter mais informações sobre canal de impressão e canal da Web, consulte [Canal de impressão e canal da Web](/help/forms/using/web-channel-print-channel.md).

1. Toque **[!UICONTROL Criar]**. A Comunicação interativa é criada e uma caixa de alerta é exibida. Toque **[!UICONTROL Editar]** para começar a criar o conteúdo da Comunicação interativa, conforme explicado em [Adicionar conteúdo usando a interface do usuário de criação do Interative Communication](#step2). Como alternativa, toque em **[!UICONTROL Concluído]** e opte por editar a Comunicação interativa posteriormente.

## Adicionar conteúdo à comunicação interativa {#step2}

Após criar uma Comunicação interativa, você pode usar a interface de criação Comunicação interativa para construir seu conteúdo.

Para obter mais informações sobre a interface de criação do Interative Communication, consulte [Introdução à criação de Comunicações interativas](/help/forms/using/introduction-interactive-communication-authoring.md).

1. A interface de criação da Comunicação interativa é iniciada quando você toca em Editar, como mencionado em [Criar comunicação interativa](#createic). Como alternativa, você pode navegar até um ativo de Comunicação interativa existente no AEM, selecioná-lo e tocar em **[!UICONTROL Editar]** para iniciar a interface de criação da Comunicação interativa .

   Por padrão, o canal de impressão da Comunicação interativa é exibido, a menos que a Comunicação interativa seja somente de canal da Web. O canal Imprimir da Comunicação Interativa exibe áreas de destino, conforme disponível no modelo de canal XDP/impressão selecionado. Nesses campos e áreas de destino, é possível adicionar componentes ou ativos.

1. Com o canal Imprimir selecionado, selecione o **[!UICONTROL Componentes]** guia . Os seguintes componentes estão disponíveis no canal de impressão:

   | **Componente** | **Funcionalidade** |
   |---|---|
   | Gráfico | Adiciona um gráfico que pode ser usado na Comunicação interativa para representação visual de dados bidimensionais recuperados de uma coleção de modelo de dados de formulário. Para obter mais informações, consulte [Uso de gráficos em Comunicações interativas](/help/forms/using/chart-component-interactive-communications.md). |
   | Fragmento do documento | Permite adicionar um componente reutilizável, como texto, lista ou condição, a uma Comunicação interativa. O componente adicionado pode ser baseado em modelo de dados de formulário ou sem um modelo de dados de formulário. |
   | Imagem | Permite inserir uma imagem. |

   Arraste e solte os componentes em sua Comunicação interativa e configure-os conforme necessário.

1. Com o canal de impressão selecionado, vá para a função **[!UICONTROL Ativos]** e aplique o filtro para exibir somente os ativos que deseja visualizar.

   Usando o navegador Ativos, também é possível arrastar e soltar ativos diretamente nas áreas de destino da Comunicação interativa .

   ![assets-docfragments](assets/assets-docfragments.png)

1. Arraste e solte os fragmentos de documento na Comunicação interativa. A seguir estão os tipos de fragmentos de documento que você pode usar no canal de impressão da Comunicação interativa.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Tipo do fragmento do documento</strong></td> 
   <td><strong>Exemplo de finalidade</strong></td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/texts-interactive-communications.md" target="_blank">Texto</a></td> 
   <td>Texto para adicionar endereço, email do destinatário e texto do corpo da carta </td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/conditions-interactive-communications.md" target="_blank">Condição</a></td> 
   <td>Condição para adicionar a imagem de cabeçalho apropriada à comunicação com base no tipo da política: Standard ou Premium. <br /> </td> 
  </tr> 
  <tr> 
   <td>Lista</td> 
   <td>Grupo de fragmentos de documento, incluindo texto, condições, outras listas e imagens. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Para obter mais informações sobre fragmentos de documento, consulte [Fragmentos de documento](/help/forms/using/document-fragments.md).

1. Para configurar o vínculo de variáveis, toque em uma variável e selecione ![configure_icon](assets/configure_icon.png) (Configure) e configure as propriedades de vínculo no painel Propriedades na barra lateral.

   * **[!UICONTROL Nenhum]**: O agente preencherá o valor da variável .
   * **[!UICONTROL Fragmento de texto]**: Se selecionada, você pode procurar e selecionar um fragmento de documento de texto cujo conteúdo é renderizado no campo. Somente esses fragmentos de documento de texto podem ser vinculados a variáveis que não têm variáveis no .
   * **[!UICONTROL Objeto do Modelo de Dados]**: Selecione uma propriedade de modelo de dados de formulário cujo valor é preenchido no campo .
   Você também pode optar por configurar o fragmento de documento de texto relevante. O painel Propriedades exibe a lista de variáveis no fragmento do documento de texto. Você pode tocar em ![editar](assets/edit.png) (Editar) ao lado de um nome de variável para exibir as configurações dessa variável para edição.

1. Para adicionar uma tabela, com o canal de impressão selecionado, no **[!UICONTROL Ativos]** aplique o filtro para exibir somente os Fragmentos de layout. Arraste e solte o fragmento de layout necessário para a Comunicação interativa. Um fragmento de layout é baseado em um XDP e pode ser usado para criar layouts gráficos ou tabelas estáticas e dinâmicas no Interative Communication que são preenchidas com dados dinâmicos.

   Exemplo: Uma tabela de layout para exibir prêmio bruto, % de desconto de fidelidade e disponibilidade de assistência de emergência para políticas antigas e novas.

   Para obter mais informações sobre fragmentos de layout, consulte [Fragmentos de documento](/help/forms/using/document-fragments.md).

1. Com o canal de impressão selecionado, no **[!UICONTROL Ativos]** aplique o filtro para exibir imagens. Arraste e solte as imagens necessárias para a Comunicação interativa, como para o logotipo da empresa.

   Além disso, gerencie o seguinte na Comunicação interativa:

   * [Adição e configuração de gráficos](/help/forms/using/chart-component-interactive-communications.md)
   * [Sincronização do canal da Web com o canal de impressão](/help/forms/using/create-interactive-communication.md#synchronize)

      * Sincronização automática
      * Cancelar herança
      * Reativar herança
      * Sincronizar
   * [Anexos e acesso à biblioteca](/help/forms/using/create-interactive-communication.md#attachmentslibrary)
   * [Propriedades do campo XDP/Layout](/help/forms/using/create-interactive-communication.md#xdplayoutfieldproperties)
   * [Adicionar regras aos componentes](/help/forms/using/create-interactive-communication.md#rules)


1. Mudar para **[!UICONTROL Canal da Web]**. O canal da Web é exibido no editor de Comunicação interativa. Ao alternar do canal Impressão para o canal Web pela primeira vez, a sincronização automática ocorre. Para obter mais informações, consulte [Sincronização do canal da Web do canal de impressão](/help/forms/using/create-interactive-communication.md#synchronize).

   Como estamos usando Imprimir como principal para a Web neste exemplo, os espaços reservados no canal Imprimir, o conteúdo e o vínculo de dados são sincronizados com o canal da Web. No entanto, você pode alterar e personalizar o conteúdo específico no canal da Web, conforme necessário.

   ![webchannelassets](assets/webchannelassets.png)

1. Para adicionar componentes adicionais ao canal da Web, com o canal da Web selecionado, toque em **[!UICONTROL Componentes]**. Arraste e solte componentes no canal da Web da Comunicação interativa, conforme necessário, e continue a configurá-los.

   | Componentes | Funcionalidade |
   |---|---|
   | Gráfico | Adiciona um gráfico que pode ser usado na Comunicação interativa para representação visual de dados bidimensionais recuperados de uma coleção de modelo de dados de formulário. Para obter mais informações, consulte [Uso do componente de gráfico](/help/forms/using/chart-component-interactive-communications.md). |
   | Fragmento do documento | Permite adicionar um componente, texto, lista ou condição reutilizável a uma Comunicação interativa. O componente reutilizável adicionado a uma Comunicação interativa pode ser baseado em modelo de dados de formulário ou sem um modelo de dados de formulário. |
   | Imagem | Permite inserir uma imagem. |
   | Painel | O componente Painel é um espaço reservado para agrupar outros componentes e controla como um grupo de componentes, como acordeão e guias, é apresentado na Comunicação interativa. Um componente de painel também permite tornar um grupo de componentes repetíveis para o usuário final, como em várias entradas necessárias para preencher as credenciais educacionais. |
   | Tabela | Adiciona uma tabela que permite organizar dados em linhas e colunas. |
   | Área de destino | Insere uma área de destino em um canal da Web para organizar os componentes específicos do canal da Web. A área de destino é um contêiner simples que permite agrupar componentes específicos de canais da Web. |
   | Texto | Adiciona rich text ao canal da Web de uma Comunicação interativa. O texto também pode usar objetos de modelo de dados de formulário para tornar o conteúdo dinâmico. |

1. Conforme necessário, insira ativos no canal da Web.

   Você pode [visualizar sua comunicação interativa](#previewic) para ver a aparência da impressão e dos resultados da Web da Comunicação interativa e continuar fazendo alterações, conforme necessário.

## Visualizar a comunicação interativa {#previewic}

Você pode usar o **[!UICONTROL Visualizar]** para avaliar a aparência da Comunicação interativa. O canal da Web de Comunicação interativa também fornece uma opção para Emular a experiência de uma Comunicação interativa para vários dispositivos. Por exemplo, iPhone, iPad e Desktop. Você pode usar ambos **[!UICONTROL Visualizar]** e **[!UICONTROL Emulador]** ![régua](assets/ruler.png) opções em conjunto entre si para visualizar as saídas da Web de dispositivos de tamanhos de tela diferentes. Os dados de amostra na visualização são preenchidos a partir do modelo de dados de formulários especificado.

1. Selecione o canal (impressão ou Web) para visualizar e toque em visualização. A Comunicação interativa é exibida.

   >[!NOTE]
   >
   >A visualização é preenchida com os dados de amostra do modelo de dados de formulário especificado. Para obter mais informações sobre como visualizar a Comunicação interativa com alguns outros dados ou usar o serviço de preenchimento prévio, consulte [Usar modelo de dados de formulário](/help/forms/using/using-form-data-model.md) e [Trabalhar com o modelo de dados de formulário](/help/forms/using/work-with-form-data-model.md).

1. Para o canal da Web, use ![régua](assets/ruler.png) para exibir a aparência da Comunicação interativa em vários dispositivos.

   ![webchannelpreview](assets/webchannelpreview.png)

Além disso, você pode [Preparar e enviar comunicação interativa usando a interface do usuário do agente](/help/forms/using/prepare-send-interactive-communication.md).

## Configuração de propriedades na comunicação interativa  {#configuring-properties-in-interactive-communication}

### Anexos e acesso à biblioteca {#attachmentslibrary}

No canal Imprimir, você pode configurar os anexos e o acesso à biblioteca para permitir que o Agente gerencie anexos na interface do agente para a Comunicação interativa:

1. No canal Impressão, realce o Contêiner de documento e toque em **[!UICONTROL Propriedades]**.

   ![documentcontainerproperties](assets/documentcontainerproperties.png)

   O painel Propriedades é exibido na barra lateral.

   ![propriedades, anexos](assets/propertiesattachments.png)

1. Expandir **[!UICONTROL Anexos]** e especifique as seguintes propriedades:

   * **[!UICONTROL Permitir acesso à biblioteca]**: Selecione para habilitar o acesso da biblioteca para o agente na interface do usuário do agente. Se ativado, o Agente pode adicionar arquivos da biblioteca enquanto prepara a Comunicação interativa.
   * **[!UICONTROL Permitir Reordenação De Anexos]**: Selecione para permitir que o Agente reordene os anexos com a Comunicação interativa.
   * **[!UICONTROL Número Máximo De Anexos Permitidos]**: Especifique o número máximo de anexos permitidos com a Comunicação interativa.
   * **[!UICONTROL Arquivos a serem anexados]**: Toque **[!UICONTROL Adicionar]** e navegue para selecionar os arquivos a serem anexados e especifique o seguinte:

      * **[!UICONTROL Anexar este arquivo ao documento por padrão]**: É possível alterar essa opção se somente o anexo não for Obrigatório.
      * **[!UICONTROL Obrigatório:]** O agente não poderá remover o anexo na interface do agente.
   ![arquivos anexos](assets/attachfiles.png)

1. Toque **[!UICONTROL Concluído]**.

### Propriedades do campo XDP/Layout {#xdplayoutfieldproperties}

1. Ao editar o canal Imprimir de uma Comunicação interativa, passe o mouse sobre um campo, que é criado no modelo de canal Imprimir, e selecione ![configure_icon](assets/configure_icon.png) (Configurar).

   A caixa de diálogo Propriedades é exibida na barra lateral.

   ![xdpfieldproperties](assets/xdpfieldproperties.png)

1. Especifique o seguinte:

   * **[!UICONTROL Nome]**: Nome do nó JCR.
   * **[!UICONTROL Título]**: Insira um título que será visível para o Agente na interface do usuário do agente e na árvore Contêiner de documento.
   * **[!UICONTROL Tipo de vínculo]**: Selecione um dos seguintes tipos de vínculo para o campo .

      * Nenhum: O agente preencherá o valor da propriedade.
      * Fragmento de texto: Se selecionada, você pode procurar e selecionar um fragmento de documento de texto cujo conteúdo é renderizado no campo.
      * Objeto do modelo de dados: Selecione uma propriedade de modelo de dados de formulário cujo valor é preenchido no campo .
   * **[!UICONTROL Valores padrão]**: O valor padrão garante que o campo não fique vazio quando não houver um valor fornecido pelo objeto de modelo de dados ou fragmento de texto especificado. Se o tipo de vínculo de dados for nenhum, o valor padrão será preenchido previamente no campo.
   * **[!UICONTROL Editável por agente]**: Selecione para permitir que o agente edite o valor no campo na interface do usuário do agente. Essa configuração não se aplica se o Tipo de vínculo for Fragmento de texto.
   * **[!UICONTROL Rótulo]**: Especifique uma sequência de texto exibida com o campo para o Agente na interface do usuário do agente. Essa configuração não se aplica se o Tipo de vínculo for Fragmento de texto.
   * **[!UICONTROL Dica de ferramenta]**: Insira uma string de texto que estará visível com o mouse sobre o Agente na interface do usuário do agente. Essa configuração não se aplica se o Tipo de vínculo for Fragmento de texto.
   * **[!UICONTROL Obrigatório]**: Selecione para tornar o campo obrigatório para o Agente. Essa configuração não se aplica se o Tipo de vínculo for Fragmento de texto.
   * **[!UICONTROL Permitir várias linhas]**: Selecione esse campo para permitir várias linhas de texto como entrada no campo. Essa configuração não se aplica se o Tipo de vínculo for Fragmento de texto.


1. Toque ![done_icon](assets/done_icon.png).

## Aplicar regras aos componentes de Comunicação interativa {#rules}

Para condicionar componentes ou conteúdo na comunicação interativa, toque no componente/parte de conteúdo e selecione ![createruleicon](assets/createruleicon.png) (Criar regra) para iniciar o Editor de regras.

Para obter mais informações, consulte:

* [Editor de regras](/help/forms/using/rule-editor.md)
* [Introdução à criação de Comunicações interativas](/help/forms/using/introduction-interactive-communication-authoring.md)

## Uso de tabelas {#tables}

### Tabelas dinâmicas em comunicação interativa {#dynamic-tables-in-interactive-communication}

É possível adicionar tabelas dinâmicas em Comunicação interativa usando fragmentos de layout. As etapas a seguir usam um exemplo de declaração de cartão de crédito para ilustrar o uso de um fragmento de layout para criar uma tabela dinâmica em uma Comunicação interativa.

1. Verifique se o fragmento de layout necessário para criar a tabela está disponível no AEM.
1. No canal de impressão da Comunicação interativa, arraste e solte um fragmento de layout (com uma tabela de várias colunas) em uma Área de destino no navegador Ativo.

   ![lf_dragdrop](assets/lf_dragdrop.png)

   Uma tabela é exibida na área de layout Comunicação interativa .

   ![lf_dragdrop_table](assets/lf_dragdrop_table.png)

1. Especifique o vínculo de dados para cada uma das células da tabela. Para criar uma linha repetível, insira as propriedades do modelo de dados de formulário na linha pertencente a uma propriedade de coleção comum.

   1. Toque em uma célula na tabela e selecione ![configure_icon](assets/configure_icon.png) (Configurar).

      A caixa de diálogo Propriedades é exibida na barra lateral.

      ![lf_cell_properties](assets/lf_cell_properties.png)

   1. Configure as propriedades:

      * **[!UICONTROL Nome]**: Nome do nó JCR.
      * **[!UICONTROL Título]**: Insira um título que será visível no editor de Comunicação interativa.
      * **[!UICONTROL Tipo de vínculo]**&amp;ast;: Selecione um dos seguintes tipos de vínculo para o campo .

         * **[!UICONTROL Nenhum]**
         * **[!UICONTROL Objeto do modelo de dados]**: O valor de uma propriedade do modelo de dados de formulário é preenchido no campo .
      * **[!UICONTROL Objeto do Modelo de Dados]**: A propriedade do modelo de dados de formulário cujo valor é preenchido no campo .
      * **[!UICONTROL Valor padrão]**: O valor padrão garante que o campo não fique vazio quando não houver um valor fornecido pelo objeto de modelo de dados especificado. O valor padrão é preenchido previamente no campo .
      * **[!UICONTROL Editável por agente]**: Selecione para permitir que o agente edite o valor no campo na interface do usuário do agente.
   1. Toque ![done_icon](assets/done_icon.png).



1. Visualize a Comunicação interativa para ver a tabela renderizada com os dados.

   ![lf_preview](assets/lf_preview.png)

### Tabelas somente de canal da Web {#web-channel-only-tables}

Você pode criar uma tabela dinâmica somente de canal da Web em uma Comunicação interativa usando uma propriedade de modelo de dados de coleção do tipo . Essa tabela é uma representação das propriedades filhas de uma propriedade de coleção. É possível editar apenas as propriedades de formatação das várias células na tabela.

1. Alterne para o canal da Web e escolha exibir o navegador das Fontes de Dados.
1. Arraste e solte uma propriedade de coleção em um subformulário.

   Uma tabela é criada no subformulário.

1. Visualize a tabela na pré-visualização da Web da Comunicação interativa.

## Sincronização do canal da Web com o canal de impressão {#synchronize}

Ao selecionar Imprimir como Principal para Canal da Web ao criar uma Comunicação Interativa, o canal da Web é criado em sincronia com o canal Imprimir e o conteúdo e o vínculo de dados do canal da Web são derivados do canal de impressão e as alterações feitas no canal de impressão são refletidas no canal da Web quando você toca em Sincronizar.

Os autores, no entanto, têm permissão para quebrar a herança de componentes no canal da Web, conforme necessário.
![printweb_2-3](assets/printweb_2-3.png)
[Clique para ampliar](assets/printweb_2-3.png)

![Canais de impressão e da Web no Editor de comunicação interativa](assets/printweb_2-1.png)

### Sincronização automática {#auto-sync}

Se estiver usando o Canal de impressão como o principal para o canal da Web e você alternar para o canal da Web a partir do canal de Impressão, a sincronização automática ocorrerá. A sincronização automática traz os espaços reservados, o conteúdo e o vínculo de dados para o canal da Web a partir do canal de Impressão. Dependendo da complexidade e do conteúdo de sua Comunicação interativa, a sincronização automática pode levar algum tempo.

>[!NOTE]
>
>A sincronização dos canais sincroniza apenas os fragmentos de documento, imagens, condições, listas e fragmentos de layout do canal de impressão para o canal da Web. Os subformulários ou nós primários de que incluem tais elementos não são sincronizados.

### Cancelar herança {#cancel-inheritance}

No canal da Web, os componentes são incorporados nas áreas de destino.

Passe o mouse sobre a área de destino relevante no canal da Web e selecione ![cancelar herança](assets/cancelinheritance.png) (Cancelar herança) e, na caixa de diálogo Cancelar herança, toque em **[!UICONTROL Sim]**.

A herança dos componentes na área de destino é cancelada e agora você pode editá-los conforme necessário.

### Reativar herança {#re-enable-inheritance}

No canal da Web, se você cancelou a herança de um componente, é possível reativá-la. Para reativar a herança, passe o mouse sobre o limite da área de destino relevante, que inclui o componente, e toque em ![reabilitar herança](assets/reenableinheritance.png).

A caixa de diálogo Reverter herança é exibida.

![revertinheridade](assets/revertinheritance.png)

Se necessário, selecione **[!UICONTROL Sincronizar A Página Após Reverter A Herança]**. Selecione esta opção para sincronizar toda a comunicação interativa. Se você não selecionar essa opção, somente a área de destino relevante será sincronizada ao restabelecer a herança.

Toque **[!UICONTROL Sim]**.

### Sincronizar {#synchronize-1}

Se estiver usando Imprimir como Principal para Canal da Web e fizer alterações no canal de impressão, será possível tocar em Sincronizar para trazer as alterações recém-feitas para o canal da Web.

1. Para sincronizar o canal Web com o canal Imprimir, toque em **[!UICONTROL Sincronizar]**.

   A caixa de diálogo Sincronizar conteúdo do canal Principal é exibida.

   ![synchronizecontentfrommasterchannel](assets/synchronizecontentfrommasterchannel.png)

1. Toque em uma das seguintes opções:

   * **[!UICONTROL Descartar Alterações]**: Descarta todas as alterações feitas no canal da Web, independentemente das alterações feitas no canal da Web.
   * **[!UICONTROL Manter alterações]**: Sincroniza o conteúdo somente das áreas de destino nas quais a herança não é cancelada.
