---
title: Variações - Criação dos fragmentos de conteúdo
seo-title: Variations - Authoring Fragment Content
description: As variações permitem criar conteúdo para o fragmento, em seguida, criar variações desse conteúdo de acordo com a finalidade (se necessário).
seo-description: Variations allow you to author content for the fragment, then create variations of that content according to purpose (if required).
uuid: affccda0-be5f-47d2-85b6-8701b77ac932
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: 1cdb2dfc-623b-44cf-9a7b-98cfabbb1d0c
exl-id: 15a5fdc9-2878-4f95-83ee-02a2899aeb43
feature: Content Fragments
role: User
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '1738'
ht-degree: 85%

---

# Variações - Criação dos fragmentos de conteúdo {#variations-authoring-fragment-content}

>[!CAUTION]
>
>Algumas funcionalidades do Fragmento de conteúdo exigem a aplicação de [AEM 6.4 Service Pack 2 (6.4.2.0) ou posterior](../release-notes/sp-release-notes.md).

[Variações](content-fragments.md#constituent-parts-of-a-content-fragment) são um recurso importante de fragmentos de conteúdo, pois permitem criar e editar cópias do conteúdo principal para uso em canais e/ou cenários específicos.

Na guia **Variações**, é possível:

* [Inserir o conteúdo](#authoring-your-content) para o fragmento
* [Criar e gerenciar variações](#managing-variations) do conteúdo **Principal**

Executar uma variedade de outras ações, dependendo do tipo de dados que está sendo editado; por exemplo:

* [Inserir ativos visuais no fragmento](#inserting-assets-into-your-fragment) (imagens)
* Selecione entre [Rich text](#rich-text), [Texto sem formatação](#plain-text) e [Markdown](#markdown) para edição

* [Fazer upload de conteúdo](#uploading-content)

* [Visualizar as principais estatísticas](#viewing-key-statistics) (sobre textos multilinha)
* [Resumir texto](#summarizing-text)

* [Sincronizar as variações com o conteúdo Principal](#synchronizing-with-master)

>[!CAUTION]
>
>Depois que um fragmento tiver sido publicado e/ou referenciado, o AEM exibirá um aviso quando um autor abrir o fragmento para edição novamente. Isso serve para avisar que as alterações no fragmento também afetarão as páginas referenciadas.

## Criação de conteúdo {#authoring-your-content}

Ao abrir o fragmento de conteúdo para edição, a guia **Variações** será aberta por padrão. Aqui é possível criar conteúdo para o Principal ou quaisquer variações que você possua. É possível:

* fazer edições diretamente na guia **Variações**
* abra o [editor de tela cheia](#full-screen-editor) para:

   * selecionar o [Formato](#formats)
   * ver mais opções de edição (para formato [Rich text](#rich-text))
   * acessar uma variedade de [ações](#actions)

Por exemplo:

* Edição de um fragmento simples

   Um fragmento simples consiste em um campo de texto de várias linhas (ativos visuais podem ser adicionados a partir do editor de tela cheia).

   ![cfm-6420-21](assets/cfm-6420-21.png)

* Edição de um fragmento com conteúdo estruturado

   Um fragmento estruturado contém vários campos, de vários tipos de dados, que foram definidos no modelo de conteúdo. Para qualquer campo de várias linhas, a variável [editor de tela cheia](#full-screen-editor) está disponível.

   ![cfm-6420-16](assets/cfm-6420-16.png)

### Editor de Tela cheia {#full-screen-editor}

Ao editar um campo de texto de várias linhas, você pode abrir o editor de tela cheia:

![cf-fullscreeneditor-icon](assets/cf-fullscreeneditor-icon.png)

O editor de tela cheia fornece:

* Acesso a várias [ações](#actions)
* Dependendo do [formato](#formats), opções adicionais de formatação ([Rich text](#rich-text))

### Ações {#actions}

As seguintes ações também estão disponíveis (para todos os [formatos](#formats)) quando o editor de tela cheia (ou seja, texto multilinha) estiver aberto:

* Selecione o [format](#formats) ([Texto formatado](#rich-text), [Texto sem formatação](#plain-text), [Markdown](#markdown))
* [Mostrar estatísticas do texto](#viewing-key-statistics)
* [Fazer upload de conteúdo](#uploading-content)
* [Sincronizar com o Principal](#synchronizing-with-master) (ao editar uma variação)
* [Resumir texto](#summarizing-text)
* [Anotar](content-fragments-variations.md#annotating-a-content-fragment) seu texto

* [Inserir ativos visuais no fragmento](#inserting-assets-into-your-fragment) (imagens)

### Formatos {#formats}

As opções para editar texto de várias linhas dependem do formato selecionado:

* [Texto formatado](#rich-text)
* [Texto sem formatação](#plain-text)
* [Markdown](#markdown)

O formato pode ser selecionado no editor de tela cheia.

### Texto formatado {#rich-text}

A edição de rich text permite formatar:

* Negrito
* Itálico
* Sublinhado
* Alinhamento: esquerda, centro, direita
* Lista com marcadores
* Lista numerada
* Recuo: aumentar, diminuir
* Criar/quebrar hiperlinks
* Abrir o editor de tela cheia, onde as seguintes opções de formatação estão disponíveis:

   * Colar texto/do Word
   * Inserir uma tabela
   * Estilo do parágrafo: parágrafo, cabeçalho 1/2/3
   * [Inserir ativos visuais](#inserting-assets-into-your-fragment)
   * Pesquisar
   * Localizar/substituir
   * Verificador ortográfico
   * [Anotações](content-fragments-variations.md#annotating-a-content-fragment)

As [ações](#actions) também podem ser acessadas pelo editor de tela cheia.

### Texto sem formatação {#plain-text}

O texto sem formatação permite inserir rapidamente conteúdo sem formatação ou markdown. Também é possível abrir o editor de tela cheia para obter mais [ações](#actions).

>[!CAUTION]
>
>Se selecionar **Texto sem formatação**, você poderá perder qualquer formatação, marcação e/ou ativos inseridos no **Rich Text** ou no **Markdown**.

### Markdown {#markdown}

>[!NOTE]
>
>Para obter informações completas, consulte a documentação sobre [Markdown](content-fragments-markdown.md).

Isso permite formatar o texto usando markdown. Você pode definir:

* Cabeçalhos
* Parágrafos e quebras de linha
* Links
* Imagens
* Citações em bloco
* Listas
* Ênfase
* Blocos de código
* Escapes de barra invertida

Você também pode abrir o editor de tela cheia para obter mais [ações](#actions).

>[!CAUTION]
>
>Se você alternar entre **Rich Text** e **Markdown**, poderá ver efeitos inesperados com Cotas de bloqueio e Bloqueios de código, já que esses dois formatos podem ter diferenças na maneira como são tratados.

### Visualizar as principais estatísticas {#viewing-key-statistics}

Quando o editor de tela cheia estiver aberto, a ação **Estatísticas de texto** exibirá uma variedade de informações sobre o texto. Por exemplo:

![cfx-6420-22](assets/cfx-6420-22.png)

### Fazer upload de conteúdo {#uploading-content}

Para facilitar o processo de criação de fragmentos de conteúdo, é possível fazer o upload de um texto preparado em um editor externo e adicioná-lo diretamente ao fragmento.

### Resumo de texto {#summarizing-text}

O resumo de texto foi criado para ajudar os usuários a reduzir o comprimento do texto para um número predefinido de palavras, mas mantendo os pontos principais e o significado geral.

>[!NOTE]
>
>Em um nível mais técnico, o sistema mantém as frases que julga fornecer a *melhor relação entre densidade e exclusividade das informações* de acordo com algoritmos específicos.

>[!CAUTION]
>
>O fragmento de conteúdo deve ter uma pasta de idioma válida como ancestral; isso é usado para determinar o modelo de idioma a ser usado.
>
>Por exemplo, `en/`, como no seguinte caminho:
>
>`/content/dam/my-brand/en/path-down/my-content-fragment`

>[!CAUTION]
>
>O inglês está disponível pronto para uso.
>
>Outros idiomas estão disponíveis como Pacotes de modelo de idioma na Distribuição de software:
>
>* [Francês (fr) da Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)
>* [Alemão (de) da Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
>* [Italiano (IT) da Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
>* [Espanhol (es) da Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
>


1. Selecione o **[!UICONTROL Principal]** ou a variação exigida.
1. Abra o editor de tela cheia.

1. Selecione **[!UICONTROL Resumir texto]** na barra de ferramentas.

   ![cf-17](assets/cf-17.png)

1. Especifique o número alvo de palavras e selecione **[!UICONTROL Iniciar]**:
1. O texto original é apresentado lado a lado com o resumo proposto:

   * As frases que serão eliminadas são destacadas em vermelho e tachadas.
   * Clique em qualquer frase destacada para mantê-la no conteúdo resumido.
   * Clique em qualquer frase não destacada para eliminá-la.

   ![cfm-6420-23](assets/cfm-6420-23.png)

1. Selecione **[!UICONTROL Resumir]** para confirmar as alterações.

### Anotação de um fragmento de conteúdo {#annotating-a-content-fragment}

Para anotar um fragmento:

1. Selecione o **[!UICONTROL Principal]** ou a variação exigida.
1. Abra o editor de tela cheia.
1. Selecione algum texto. O **[!UICONTROL Anotar]** torna-se disponível.

   ![cfm-6420-24](assets/cfm-6420-24.png)

1. Uma caixa de diálogo será aberta. Aqui é possível inserir sua anotação.

1. Feche o editor de tela cheia e **[!UICONTROL Salvar]** o fragmento.

### Visualizar, editar e excluir anotações {#viewing-editing-deleting-annotations}

Anotações:

* São indicadas pelo destaque no texto, no modo de tela cheia e no modo normal do editor. Detalhes completos de uma anotação podem ser visualizados, editados e/ou excluídos ao clicar no texto destacado, o que abrirá novamente a caixa de diálogo.

   >[!NOTE]
   >
   >Um seletor suspenso é fornecido se várias anotações tiverem sido aplicadas a um texto.

* Quando você exclui o texto inteiro ao qual a anotação foi aplicada, a anotação também é excluída.

* Podem ser listadas e excluídas selecionando a guia **[!UICONTROL Anotações]** no editor do fragmento.

   ![cfm-6420-25](assets/cfm-6420-25.png)

* Podem ser visualizadas e excluídas na [Linha do tempo](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments) do fragmento selecionado.

### Inserir ativos no fragmento {#inserting-assets-into-your-fragment}

Para facilitar o processo de criação de fragmentos de conteúdo, você pode adicionar [Ativos](managing-assets-touch-ui.md) (imagens) diretamente no fragmento.

Eles serão adicionados à sequência de parágrafo do fragmento sem qualquer formatação; a formatação pode ser feita quando o [fragmento for usado/referenciado em uma página](/help/sites-authoring/content-fragments.md).

>[!CAUTION]
>
>Esses ativos não podem ser movidos ou excluídos em uma página de referência. Isso deve ser feito no editor do fragmento.
>
>No entanto, a formatação do ativo (por exemplo, seu tamanho) deve ser feita no [editor de páginas](/help/sites-authoring/content-fragments.md). A representação do ativo no editor de fragmento serve meramente para a criação do fluxo de conteúdo.

>[!NOTE]
>
>Existem vários métodos de adicionar [imagens](content-fragments.md#fragments-with-visual-assets) ao fragmento e/ou página.

1. Posicione o cursor na posição que deseja adicionar a imagem.
1. Use o ícone **[!UICONTROL Inserir ativo]** para abrir a caixa de diálogo de pesquisa.

   ![cf-insertasset-icon](assets/cf-insertasset-icon.png)

1. Na caixa de diálogo, é possível:

   * navegar até o ativo necessário no DAM
   * pesquisar o ativo no DAM

   Depois de localizado, selecione o ativo necessário clicando na miniatura.

1. Use **[!UICONTROL Selecionar]** para adicionar o ativo ao sistema de parágrafo do fragmento de conteúdo no local atual.

   >[!CAUTION]
   >
   >Se, após adicionar um ativo, você alterar o formato para:
   >
   >* **Texto simples:** o ativo será completamente perdido do fragmento.
   >* **Marcação**: o ativo não estará visível, mas ainda estará lá ao retornar para **Rich Text**.


## Gerenciamento de variações {#managing-variations}

### Criar uma variação {#creating-a-variation}

As variações permitem selecionar o conteúdo **Principal** e alterá-lo de acordo com a finalidade (se necessário).

Para criar uma nova variação:

1. Abra o fragmento e verifique se o painel lateral está visível.
1. Selecione **[!UICONTROL Variações]** na barra de ícones, no painel lateral.
1. Selecione **[!UICONTROL Criar variação]**.
1. Uma caixa de diálogo será aberta. Especifique o **[!UICONTROL Título]** e a **[!UICONTROL Descrição]** da nova variação.
1. Selecione **[!UICONTROL Adicionar]**; o fragmento **[!UICONTROL Mestre]** será copiado para a nova variação, que agora está aberta para [edição](#editing-a-variation).

   >[!NOTE]
   >
   >Ao criar uma nova variação, é sempre o **Principal** que é copiado, não a variação que está aberta no momento.

### Editar uma variação {#editing-a-variation}

Você pode fazer alterações no conteúdo de variação após:

* [Criar a variação](#creating-a-variation).
* Abrir um fragmento existente e, em seguida, selecionar a variação necessária no painel lateral.

![cfm-6420-26](assets/cfm-6420-26.png)

### Renomear uma variação {#renaming-a-variation}

Para renomear uma variação existente:

1. Abra o fragmento e selecione **[!UICONTROL Variações]** no painel lateral.
1. Selecione a variação necessária.
1. Selecione **[!UICONTROL Renomear]** no menu suspenso **[!UICONTROL Ações]**.

1. Digite o novo **[!UICONTROL Título]** e/ou **[!UICONTROL Descrição]** na caixa de diálogo resultante.

1. Confirme a ação **[!UICONTROL Renomear]**.

>[!NOTE]
>
>Isso só afeta o **Título** da variação.

### Excluir uma Variação {#deleting-a-variation}

Para excluir uma variação existente:

1. Abra o fragmento e selecione **[!UICONTROL Variações]** no painel lateral.
1. Selecione a variação necessária.
1. Selecione **[!UICONTROL Excluir]** no menu suspenso de **[!UICONTROL Ações]**.

1. Confirme a ação de **[!UICONTROL Exclusão]** na caixa de diálogo.

>[!NOTE]
>
>Não é possível excluir o **Principal**.

### Sincronização com o Principal {#synchronizing-with-master}

O **Principal** é parte integral de um fragmento de conteúdo e, por definição, contém a cópia principal do conteúdo, enquanto as variações contêm as versões individuais atualizadas e personalizadas desse conteúdo. Quando o Principal é atualizado, é possível que essas alterações também sejam relevantes para as variações e, portanto, precisam ser propagadas para elas.

Ao editar uma variação, você tem acesso à ação para sincronizar o elemento atual da variação com o Principal. Isso permite copiar automaticamente as alterações feitas no Principal para a variação necessária.

>[!CAUTION]
>
>A sincronização só está disponível para copiar alterações *do **Principal**para a variação*.
>
>Somente o elemento atual da variação será sincronizado.
>
>A sincronização só funciona no tipo de dados **Texto de várias linhas**.
>
>A transferência de alterações *de uma variação para o **Principal*** não está disponível como uma opção.

1. Abra o fragmento de conteúdo no editor de fragmentos. Certifique-se de que o **Principal** foi editado.
2. Selecione uma variação específica e, em seguida, a ação de sincronização apropriada:

   * no seletor suspenso de **Ações** — **Sincronizar elemento atual com o Principal**
   * a barra de ferramentas do editor de tela cheia — **Sincronizar com o Principal**

3. O Principal e a variação serão mostrados lado a lado:

   * verde indica conteúdo adicionado (à variação)
   * vermelho indica conteúdo removido (da variação)

   ![cfm-6420-27](assets/cfm-6420-27.png)

4. Selecione **[!UICONTROL Sincronizar]**. A variação será atualizada e mostrada.
