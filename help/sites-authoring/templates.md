---
title: Criação de modelos de páginas
seo-title: Creating Page Templates
description: O modelo define a estrutura da página resultante e, com o editor de modelo, criar e manter modelos não é mais uma tarefa somente para desenvolvedores
seo-description: The template defines the structure of the resultant page and with the template editor, creating and maintaining templates is no longer a developer-only task
uuid: ffdc760d-9504-4d13-9f74-a58499632b78
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 5a96c306-790a-4721-a146-86fbceb376db
exl-id: 2af8eaed-3963-4016-9efa-a630d16a982b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4820'
ht-degree: 47%

---

# Criação de modelos de páginas   {#creating-page-templates}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Ao criar uma página, você deve selecionar um modelo, que será usado como a base para criar a nova página. O modelo define a estrutura da página resultante, qualquer conteúdo inicial e os componentes que podem ser usados.

Com o **Editor de modelos**, criar e manter modelos não é mais uma tarefa somente para desenvolvedores. Um tipo de usuário avançado, chamado de **autor de modelo**, também pode ser envolvido. Os desenvolvedores ainda são necessários para configurar o ambiente, criar bibliotecas de clientes e criar os componentes a serem usados, mas uma vez que essas noções básicas estejam em vigor, o **autor do modelo** terá a flexibilidade de criar e configurar modelos sem um projeto de desenvolvimento.

O **Console Modelos** permite que os autores de modelo:

* Criem um novo modelo ou copiem um modelo existente.
* Gerencie o ciclo de vida do modelo.

O **Editor de modelos** permite que os autores de modelo:

* Adicione componentes ao modelo e os posicione em uma grade responsiva.
* Pré-configurar os componentes.
* Defina quais componentes podem ser editados nas páginas criadas com o modelo.

Este documento explica como uma **autor do modelo** O pode usar o console e o editor de modelos para criar e gerenciar modelos editáveis.

Para obter informações detalhadas sobre como os modelos editáveis funcionam a um nível técnico, consulte o documento do desenvolvedor [Modelos de página - Editável](/help/sites-developing/page-templates-editable.md) para obter mais informações.

>[!NOTE]
>
>AEM 6.4.5.0 ou posterior é necessário para usar modelos editáveis com a variável [Editor de SPA](/help/sites-developing/spa-overview.md).

>[!NOTE]
>
>O **Editor de modelos** não oferece suporte para direcionamento diretamente no nível do modelo. As páginas criadas com base em um modelo editável podem ser direcionadas, mas os modelos em si não podem.

>[!CAUTION]
>
>Páginas e modelos criados com o **Console Modelos** não se destinam a ser usados com a interface do usuário clássica e esse uso não é suportado.

## Antes de começar {#before-you-start}

>[!NOTE]
>
>Um administrador precisa configurar uma pasta de modelo no **Navegador de configurações** e aplicar permissões apropriadas antes que um autor de modelo possa criar um modelo nessa pasta.

É importante considerar os seguintes pontos antes de começar:

* Criar um novo modelo requer colaboração. Por esse motivo, a [Função](#roles) é indicada para cada tarefa.

* Dependendo de como sua instância está configurada, pode ser útil estar ciente de que AEM agora fornece [dois tipos básicos de modelo](/help/sites-authoring/templates.md#editable-and-static-templates). Isso não afeta a maneira como você [usar um modelo para criar uma página](#using-a-template-to-create-a-page), mas afeta o tipo de modelo que você pode criar e como uma página se relaciona com seu modelo.

### Funções {#roles}

A criação de um novo modelo usando o **Console de modelos** e o **Editor de modelos** exige a colaboração entre as seguintes funções:

* **Administrador**:

   * Cria uma nova pasta de modelos requer direitos de `admin`.
   * Tais tarefas também podem ser realizadas por um desenvolvedor

* **Desenvolvedor**:

   * Concentra-se nos detalhes técnicos/internos
   * Precisa de experiência com o ambiente de desenvolvimento.
   * Fornece ao autor do modelo as informações necessárias. 

* **Autor do modelo**:

   * Esse é um autor específico, membro do grupo `template-authors`

      * Isso atribui os privilégios e permissões necessários. 
   * Pode configurar o uso de componentes e outros detalhes de alto nível que exigem:

      * Algum conhecimento técnico

         * Por exemplo, usar padrões ao definir caminhos.
      * Informações técnicas do desenvolvedor.



Devido à natureza de algumas tarefas, como a criação de uma pasta, um ambiente de desenvolvimento é necessário, e isso requer conhecimento/experiência.

As tarefas detalhadas neste documento são listadas com a função responsável por executá-las.

### Modelos editáveis e estáticos {#editable-and-static-templates}

AEM agora oferece dois tipos básicos de modelos:

* Modelos editáveis

   * Pode ser [criado](#creating-a-new-template-template-author) e [editado](#editing-templates-template-authors) por autores de modelo usando o **Modelo** console e editor. O **Modelo** é acessível no **Geral** da seção **Ferramentas** console.
   * Após a criação da nova página, uma conexão dinâmica é mantida entre a página e o modelo. Isso significa que as alterações na estrutura do modelo e/ou no conteúdo bloqueado serão refletidas em qualquer página criada com esse modelo. As alterações no conteúdo desbloqueado (ou seja, inicial) não serão refletidas.
   * Use as políticas de conteúdo, que podem ser definidas no editor de modelo, para manter as propriedades de design. O modo Design no editor de páginas não é mais usado para modelos editáveis.

* Modelos estáticos

   * Os modelos estáticos foram disponibilizados para várias versões do AEM.
   * Eles são [fornecido por seus desenvolvedores](/help/sites-developing/page-templates-static.md), portanto, não podem ser criadas ou editadas por autores.
   * São copiados para criar a nova página, mas nenhuma conexão dinâmica existe depois disso (embora o nome do modelo seja registrado para obter informações).
   * Use [Modo Design](/help/sites-authoring/default-components-designmode.md) para manter as propriedades de design.
   * Como editar modelos estáticos é a tarefa exclusiva de um desenvolvedor, consulte o documento do desenvolvedor [Modelos de página - Estático](/help/sites-developing/page-templates-static.md) para obter mais informações.

Por definição, o console modelo e o editor de modelo permitem apenas a criação e edição de modelos editáveis. Portanto, este documento se concentra exclusivamente em modelos editáveis.

### Usando um modelo para criar uma página {#using-a-template-to-create-a-page}

Ao usar um modelo para [criar uma nova página](/help/sites-authoring/managing-pages.md#creating-a-new-page) não há diferença visível e nenhuma indicação entre modelos estáticos e editáveis. Para o autor da página, o processo é transparente.

## Criação e gerenciamento de modelos {#creating-and-managing-templates}

Ao criar um novo modelo editável:

* Use o console **Modelo**. Isso está disponível no **Geral** da seção **Ferramentas** console.

   * Ou diretamente em: [http://localhost:4502/libs/wcm/core/content/sites/templates.html/conf](http://localhost:4502/libs/wcm/core/content/sites/templates.html/conf)

* É possível [criar uma pasta para os modelos](#creating-a-template-folder-admin) se necessário
* [Criar um novo modelo](#creating-a-new-template-template-author), inicialmente vazio 

* [Definir propriedades adicionais](#defining-template-properties-template-author) para o modelo, se necessário
* [Editar o modelo](#editing-templates-template-authors) para definir o:

   * [Estrutura](#editing-a-template-structure-template-author) - conteúdo predefinido que não pode ser alterado nas páginas criadas com o modelo.
   * [Conteúdo inicial](#editing-a-template-initial-content-author) - conteúdo predefinido que pode ser alterado nas páginas criadas com o modelo.
   * [Layout](#editing-a-template-layout-template-author) - para um intervalo de dispositivos.
   * [Estilos](/help/sites-authoring/style-system.md) - defina os estilos a serem usados com o modelo e seus componentes.

* [Ativar o modelo](#enabling-a-template-template-author) para uso ao criar uma página
* [Permitir o modelo](#allowing-a-template-author) para a página ou ramificação necessária do seu site
* [Publicar o modelo](#publishing-a-template-template-author) para disponibilizá-lo no ambiente de publicação

>[!NOTE]
>
>Os **Modelos permitidos** geralmente são predefinidos quando seu site for inicialmente configurado.

>[!CAUTION]
>
>Nunca insira qualquer informação que precise ser [internacionalizado](/help/sites-developing/i18n.md) em um modelo.

### Criação de uma pasta de modelo - Administrador {#creating-a-template-folder-admin}

Uma pasta de modelo deve ser criada para que o projeto mantenha seus modelos específicos de projetos. Esta é uma tarefa de administrador e está descrita no documento [Modelos de página - Editável](/help/sites-developing/page-templates-editable.md#template-folders).

### Criação de um novo modelo - Autor do modelo {#creating-a-new-template-template-author}

1. Abra o **Console Modelos** (via **Ferramentas** -> **Geral**) e navegue até a pasta desejada.

   >[!NOTE]
   >
   >Em uma instância padrão do AEM, a pasta **global** já existe no console modelo. Isso mantém modelos padrão e atua como um fallback se nenhuma política e/ou tipo de modelo for localizado na pasta atual.
   >
   >É recomendável usar um [pasta de modelo criada para o seu projeto](/help/sites-developing/page-templates-editable.md#template-folders).

1. Selecione **Criar**, em seguida **Criar modelo** para abrir o assistente.

1. Escolha uma **Tipo de modelo**, em seguida selecione **Próximo**.

   >[!NOTE]
   >
   >Os tipos de modelos são layouts predefinidos e podem ser considerados modelos de um modelo. Eles são predefinidos pelos desenvolvedores ou pelo administrador do sistema. Mais informações podem ser encontradas no documento do desenvolvedor [Modelos de página - Editável](/help/sites-developing/page-templates-editable.md#template-type).

1. Complete o **Detalhes do modelo**:

   * **Nome do modelo**
   * **Descrição**

1. Selecione **Criar**. Uma confirmação será exibida, selecione **Abrir**[](#editing-templates-template-authors) para começar a editar o modelo ou **Concluído** para retornar ao console do modelo.

   >[!NOTE]
   >
   >Quando um modelo novo for criado, ele será marcado como **Rascunho** no console. Isso indica que ainda não está disponível para uso por autores da página.

### Definir propriedades do modelo - Autor do modelo   {#defining-template-properties-template-author}

Um template pode ter as seguintes propriedades:

* Imagem

   * Imagem a ser usada como uma [miniatura do modelo](/help/sites-authoring/templates.md#template-thumbnail-image) para auxiliar na seleção, como no assistente Criar página .

      * Pode ser carregado
      * Pode ser gerado com base no conteúdo do modelo

* Título

   * Um título usado para identificar o modelo, como no **Criar página** assistente.

* Descrição

   * Uma descrição opcional para fornecer mais informações sobre o modelo e seu uso, que pode ser visualizada, por exemplo, na variável **Criar página** assistente.

Para exibir e/ou editar as propriedades:

1. No **console Modelos**, selecione o modelo.
1. Selecione **Propriedades da exibição** na barra de ferramentas ou nas opções rápidas para abrir a caixa de diálogo.
1. Agora você pode exibir ou editar as propriedades do modelo.

>[!NOTE]
>
>O status de um modelo (rascunho, ativado ou desativado) é exibido no console.

#### Imagem em miniatura do modelo {#template-thumbnail-image}

Para definir a miniatura do modelo:

1. Edite as propriedades do modelo.
1. Escolha se deseja fazer upload de uma miniatura ou gerá-la a partir do conteúdo do template.

   * Para fazer upload de uma miniatura, clique ou toque em **Carregar imagem**
   * Se desejar gerar uma miniatura, clique ou toque em **Gerar visualização**

1. Para ambos os métodos, uma visualização da miniatura será exibida.

   Se não for satisfatório, clique ou toque em **Limpar** para carregar outra imagem ou gerar novamente a miniatura.

1. Quando estiver satisfeito com a miniatura, clique ou toque em **Salvar e fechar**.

### Ativar e permitir um modelo - Autor do modelo   {#enabling-and-allowing-a-template-template-author}

Para poder usar um modelo ao criar uma página é necessário:

* [Ativar o modelo](#enabling-a-template-template-author) para disponibilizá-lo para o uso na criação de páginas.
* [Permitir o modelo](#allowing-a-template-author) para especificar as ramificações de conteúdo nas quais o modelo pode ser usado.

#### Habilitar um modelo - Autor do modelo {#enabling-a-template-template-author}

Um modelo pode ser ativado ou desativado para torná-lo disponível ou indisponível na variável **Criar página** assistente.

>[!CAUTION]
>
>Quando um modelo estiver habilitado, um aviso será exibido quando um autor de modelo começar a atualizar o modelo. Isso serve para informar ao usuário que o modelo pode ser referenciado, de modo que qualquer alteração pode afetar as páginas que fazem referência ao modelo.

1. No **console Modelos**, selecione o modelo.
1. Selecione **Habilitar** ou **Desabilitar** da barra de ferramentas e depois na caixa de diálogo de confirmação.
1. Agora é possível usar o modelo ao [criar uma nova página](/help/sites-authoring/managing-pages.md#creating-a-new-page), embora você provavelmente queira [editar o modelo](#editing-templates-template-authors) de acordo com seus requisitos.

>[!NOTE]
>
>O status de um modelo (rascunho, ativado ou desativado) é exibido no console.

#### Ativar um modelo - Autor {#allowing-a-template-author}

Um modelo pode ser disponibilizado ou indisponibilizado para determinadas ramificações de página.

1. Abra as [Propriedades da página](/help/sites-authoring/editing-page-properties.md) da página raiz da ramificação onde deseja que o modelo fique disponível.

1. Abra a guia **Avançado**.

1. Em **Configurações do modelo** use **Adicionar campo** para especificar os caminhos aos seus modelos.

   O caminho pode ser explícito ou usar padrões. Por exemplo:

   `/conf/<your-folder>/settings/wcm/templates/.*`

   A ordem dos caminhos é irrelevante, todos os caminhos serão digitalizados e quaisquer modelos recuperados.

   >[!NOTE]
   >
   >Se a variável **Modelos permitidos** for deixada em branco, a árvore será crescente até que um valor/lista seja encontrado.
   >
   >Consulte [Disponibilidade de modelos](/help/sites-developing/templates.md#template-availability) - os princípios para modelos permitidos permanecem inalterados.

1. Clique em **Salvar** para salvar as alterações nas propriedades da página.

>[!NOTE]
>
>Geralmente os modelos permitidos são predefinidos para todo o site quando configurado.

### Publicar um modelo - Autor do modelo {#publishing-a-template-template-author}

À medida que o modelo for referenciado quando a página for renderizada, o modelo totalmente configurado precisará ser publicado, para estar disponível no ambiente de publicação.

1. No **console Modelos**, selecione o modelo.
1. Selecione **Publicar** na barra de ferramentas para abrir o assistente.
1. Selecione as **Políticas do conteúdo** para ser publicado em tandem.

1. Selecionar **Publicar** na barra de ferramentas para concluir a ação.

## Editar modelos - Autores do modelo   {#editing-templates-template-authors}

Ao criar ou editar um modelo, há vários aspectos que você pode definir. A edição de modelos é semelhante à criação de página.

Os seguintes aspectos de um template podem ser editados:

* [Estrutura](#editing-a-template-structure-template-author)

   Os componentes adicionados aqui não podem ser movidos/removidos das páginas resultantes pelos autores da página. Se você quiser que os autores da página possam adicionar e remover componentes às páginas resultantes, será necessário adicionar um sistema de parágrafo ao modelo.

   Quando os componentes são bloqueados, é possível adicionar conteúdo, que não pode ser editado pelos autores da página. Você pode desbloquear componentes para permitir que você defina [Conteúdo inicial](#editing-a-template-initial-content-author).

   >[!NOTE]
   >
   >No modo de estrutura, os componentes que são o pai de um componente desbloqueado não podem ser movidos, recortados ou excluídos.

* [Conteúdo inicial](#editing-a-template-initial-content-author)

   Quando um componente tiver sido desbloqueado, é possível definir o conteúdo inicial que será copiado para páginas resultantes, criado a partir do modelo. Esses componentes desbloqueados podem ser editados nas páginas resultantes.

   >[!NOTE]
   >
   >No modo de **conteúdo inicial**, bem como nas páginas resultantes, todos os componentes desbloqueados que tenham um pai acessível (isto é, componentes dentro de um contêiner de layout) podem ser excluídos.

* [Layout](#editing-a-template-layout-template-author)

   Aqui você pode predefinir o layout do modelo para os formatos de dispositivo necessários. O modo **Layout** de criação do modelo tem a mesma funcionalidade que o modo **[Layout](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)** da criação de página.

* [Políticas da página](#editing-a-template-structure-template-author)

   Em políticas de página, você pode conectar políticas de página predefinidas à página. Essas políticas da página definem as várias configurações de design.

* [Estilos](/help/sites-authoring/style-system.md)

   O sistema de estilos permite ao autor do modelo definir classes de estilo na política de conteúdo de um componente para que autores de conteúdo possam selecioná-las ao editarem o componente em uma página. Esses estilos podem ser variações visuais alternativas de um componente, tornando-o mais flexível.

   Consulte a [documentação do Style System](/help/sites-authoring/style-system.md) para obter mais informações.

O seletor de **Modo** na barra de ferramentas permite selecionar e editar o aspecto apropriado do modelo:

* [Estrutura](#editing-a-template-structure-template-author)
* [Conteúdo inicial](#editing-a-template-initial-content-author)
* [Layout](#editing-a-template-layout-template-author)

![chlimage_1-363](assets/chlimage_1-363.png)

Já a opção **Política de página** no menu **Informações de página** permite [selecionar as políticas de página necessárias](#editing-a-template-structure-template-author):

![screen_shot_2018-03-23at120604](assets/screen_shot_2018-03-23at120604.png)

>[!CAUTION]
>
>Se um autor começar a editar um modelo que já foi ativado, um aviso será exibido. Isso serve para informar ao usuário que o modelo pode ser referenciado, de modo que qualquer alteração pode afetar as páginas que fazem referência ao modelo.

### Editar um modelo - Estrutura - Autor do modelo {#editing-a-template-structure-template-author}

Em **Estrutura** modo como você define os componentes e o conteúdo para o modelo, a política para o modelo e seus componentes.

* Os componentes definidos na estrutura do modelo não podem ser movidos em uma página resultante nem excluídos de qualquer página resultante.
* Se desejar que os autores da página possam adicionar e remover componentes, adicione um sistema de parágrafo ao modelo.
* Os componentes podem ser desbloqueados e bloqueados novamente para permitir que você defina o [conteúdo inicial](#editing-a-template-initial-content-author).

* As políticas de design dos componentes e página são definidas.

![screen_shot_2018-03-23at120819](assets/screen_shot_2018-03-23at120819.png)

Em **Estrutura** modo do editor de modelos:

* **Adicionar componentes**

   Há vários mecanismos para adicionar componentes ao modelo:

   * No **Componentes** no painel lateral.
   * Ao usar a variável **Inserir componente** opção (**+** ícone ) disponível na barra de ferramentas dos componentes já no modelo ou na **Arraste componentes aqui** caixa.
   * Ao arrastar um ativo (no navegador de **Ativos** no painel lateral) diretamente no modelo para gerar o componente adequado no local.

   Depois de adicionado, cada componente é marcado com:

   * Uma borda
   * Um marcador para mostrar o tipo de componente
   * Um marcador para mostrar quando o componente foi desbloqueado

   >[!NOTE]
   >
   >Ao adicionar um componente de **Título** pronto ao modelo, ele conterá **estrutura** de texto padrão.
   >
   >
   >Se alterar e adicionar seu próprio texto, esse texto atualizado será usado quando uma página for criada a partir do modelo.
   >
   >
   >Se deixar o texto padrão (estrutura) como está, o título será padrão para o nome da página subsequente.

   >[!NOTE]
   >
   >Embora não seja idêntico, adicionar componentes e ativos a um modelo tem muitas coisa em comum com as ações semelhantes quando [criação de página](/help/sites-authoring/editing-content.md).

* **Ações do componente**

   Execute ações nos componentes depois de adicioná-los ao modelo. Cada instância individual tem uma barra de ferramentas que permite acessar as ações disponíveis. A barra de ferramentas depende do tipo de componente.

   ![screen_shot_2018-03-23at120909](assets/screen_shot_2018-03-23at120909.png)

   Além disso, ela pode ser dependente das ações executadas como quando uma política foi associada ao componente, o ícone de configuração de design é disponibilizado.

* **Editar e configurar**

   Com essas duas ações você pode adicionar conteúdo aos seus componentes.

* **Borda para indicar estrutura**

   Ao trabalhar no **Estrutura** um modo borda laranja indica o componente selecionado no momento. Uma linha pontilhada também indica o componente principal.

   Por exemplo, na captura de tela abaixo da variável **Texto** estiver selecionado, em um **Contêiner de layout** (responsivegrid).

   ![chlimage_1-364](assets/chlimage_1-364.png)

* **Política e propriedades (Geral)**

   As políticas de conteúdo (ou design) definem as propriedades de design de um componente. Por exemplo, os componentes disponíveis ou as dimensões mínima/máxima. Elas são aplicáveis ao modelo (e às páginas criadas com o modelo).

   Crie uma política de conteúdo ou selecione uma existente para um componente. Isso permite que definir os detalhes do design.

   ![chlimage_1-365](assets/chlimage_1-365.png) ![chlimage_1-366](assets/chlimage_1-366.png)

   A janela de configuração é dividida em dois.

   * Do lado esquerdo da caixa de diálogo, em **Política**, você tem a capacidade de selecionar uma política existente.
   * Do lado direito da caixa de diálogo, em **Propriedades**, você pode definir as propriedades específicas ao tipo de componente.

   As propriedades disponíveis dependem do componente selecionado. Por exemplo, para um componente de texto, as propriedades definem as opções de copiar e colar, as opções de formatação e o estilo de parágrafo, entre outras opções.

   ***Política***

   As políticas de conteúdo (ou design) definem as propriedades de design de um componente. Por exemplo, os componentes disponíveis ou as dimensões mínima/máxima. Elas são aplicáveis ao modelo (e às páginas criadas com o modelo).

   Em **Política** é possível selecionar uma política existente para aplicar ao componente por meio da lista suspensa.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   Uma nova política pode ser adicionada ao selecionar o botão adicionar ao lado da lista suspensa **Selecionar política**. Um novo título deve ser especificado no campo **Título da política**.

   ![chlimage_1-368](assets/chlimage_1-368.png)

   A política existente selecionada na lista suspensa **Selecionar política** pode ser copiada como uma nova política usando o botão copiar ao lado do menu suspenso. Um novo título deve ser especificado no campo **Título da política**. Por padrão, a política copiada será denominada **Cópia de X**, onde X é o título da política copiada.

   ![chlimage_1-369](assets/chlimage_1-369.png)

   É opcional uma descrição da política no campo **Descrição da política**.

   Na seção **Outros modelos que também utilizam a política selecionada**, você pode ver qual modelo utiliza a política selecionada na lista suspensa **Selecionar política**.

   ![chlimage_1-370](assets/chlimage_1-370.png)

   >[!NOTE]
   >
   >Se vários componentes do mesmo tipo forem adicionados como conteúdo inicial, a mesma política se aplica a todos os componentes. Isso reflete a mesma restrição em **[Modo Design](/help/sites-authoring/default-components-designmode.md)** para modelos estáticos.

   ***Propriedades***

   Em **Propriedades** é possível definir as configurações do componente. O cabeçalho tem duas guias:

   * Principal
   * Recursos

   *Principal*

   No **Principal** , as configurações mais importantes do componente são definidas.

   Por exemplo, para um componente de imagem, as larguras permitidas podem ser definidas junto com a ativação do carregamento lento.

   Se uma configuração permitir várias configurações, clique ou toque no botão **Adicionar** para adicionar outra configuração.

   ![chlimage_1-371](assets/chlimage_1-371.png)

   Para remover uma configuração, clique ou toque no botão **Excluir** localizado à direita da configuração.

   Para remover uma configuração, clique ou toque no botão** Excluir**.

   ![chlimage_1-372](assets/chlimage_1-372.png)

   *Recursos*

   O **Recursos** permite ativar ou desativar recursos adicionais do componente.

   Por exemplo, para um componente de imagem, você pode definir as proporções de corte, orientações de imagem permitidas e se os uploads são permitidos.

   ![chlimage_1-373](assets/chlimage_1-373.png)

   >[!CAUTION]
   >
   >Observe que no AEM, as proporções de corte estão definidas como **altura/largura**. Isso difere da definição convencional de largura/altura e é feita por motivos de compatibilidade de legado. Os usuários da criação de página não estarão cientes de qualquer diferença desde que você defina o **Nome** claramente, uma vez que este é exibido na interface do usuário.

   >[!NOTE]
   >
   >[As políticas de conteúdo para componentes que implementam o editor de rich text](/help/sites-administering/rich-text-editor.md) só podem ser definidas para opções disponibilizadas pelo RTE, por meio das configurações da interface.

* **Política e propriedades (contêiner de layout)**

   As configurações de política e propriedades de um contêiner de layout são semelhantes ao uso geral, mas com algumas diferenças.

   >[!NOTE]
   >
   >Configurar uma política é obrigatório para componentes de contêiner, pois permite definir componentes que estarão disponíveis no contêiner.

   A janela de configuração é dividida em dois, assim como no uso geral da janela.

   ***Política***

   As políticas de conteúdo (ou design) definem as propriedades de design de um componente. Por exemplo, os componentes disponíveis ou as dimensões mínima/máxima. Elas são aplicáveis ao modelo (e às páginas criadas com o modelo).

   Em **Política** é possível selecionar uma política existente para aplicar ao componente por meio da lista suspensa. Isso funciona exatamente da mesma forma que a janela de uso geral.

   ***Propriedades***

   Em **Propriedades** é possível escolher quais componentes estão disponíveis para o contêiner de layout e definir suas configurações. O cabeçalho tem três guias:

   * Componentes permitidos
   * Componentes padrão
   * Configurações responsivas

   *Componentes permitidos*

   No **Componentes permitidos** , defina quais componentes estão disponíveis para o contêiner de layout.

   * Os componentes são agrupados por seus grupos de componentes, que podem ser expandidos e recolhidos.
   * Um grupo inteiro pode ser selecionado, marcando o nome do grupo e todos podem ser desmarcados, desmarcando.
   * Um sinal de menos representa pelo menos um, mas não todos os itens em um grupo são selecionados.
   * Uma pesquisa está disponível para filtrar um componente por nome.
   * As contagens listadas à direita do nome do grupo de componentes representam o número total de componentes selecionados nesses grupos, independentemente do filtro.

   ![chlimage_1-374](assets/chlimage_1-374.png)

   *Componentes padrão*

   No **Componentes padrão** , você define quais componentes são associados automaticamente a determinados tipos de mídia, de modo que, quando um autor arrastar um ativo do navegador de ativos, AEM saiba com qual componente associá-lo. Observe que somente os componentes com zonas para soltar estão disponíveis para essa configuração.

   Clique ou toque em **Adicionar mapeamento** para adicionar um componente totalmente novo e o mapeamento de tipo MIME.

   Selecione um componente na lista e clique ou toque em **Adicionar tipo** para adicionar outro tipo MIME a um componente já mapeado. Clique no ícone **Excluir** para remover a um tipo MIME.

   ![chlimage_1-375](assets/chlimage_1-375.png)

   *Configurações responsivas*

   Na guia **Configurações responsivas**, é possível configurar o número de colunas na grade resultante do container de layout.

* **Desbloquear/bloquear componentes**

   Você desbloqueia/bloqueia componentes para definir se o conteúdo está disponível para alteração em **Conteúdo inicial** modo.

   Quando um componente é desbloqueado:

   * Um indicador de cadeado aberto é mostrado na borda.
   * A barra de ferramentas do componente será ajustada adequadamente.
   * Qualquer conteúdo já inserido não será mais exibido em **Estrutura** modo.

      * O conteúdo já inserido é considerado conteúdo inicial e é visível apenas no modo **Conteúdo inicial**.
   * Os pais do componente desbloqueado não podem ser movidos, recortados ou excluídos.

   ![chlimage_1-376](assets/chlimage_1-376.png)

   Isso inclui desbloquear componentes de contêiner para que outros componentes possam ser adicionados, no modo **Conteúdo inicial** ou nas páginas resultantes. Se você já tiver adicionado componentes/conteúdo ao contêiner antes de desbloqueá-lo, eles não serão mais exibidos quando estiverem no modo **Estrutura**, mas serão exibidos no modo **Conteúdo inicial**. No **modo Estrutura**, apenas o componente do contêiner será mostrado com sua lista de **Componentes permitidos**.

   ![chlimage_1-377](assets/chlimage_1-377.png)

   Para economizar espaço, o contêiner de layout não é expandido para acomodar a lista de componentes permitidos. Em vez disso, o contêiner se torna uma lista rolável.

   Os componentes configuráveis são mostrados com um ícone de **Política**, no qual você pode tocar ou clicar para editar a política e as propriedades desse componente.

   ![chlimage_1-378](assets/chlimage_1-378.png)

* **Relação com páginas existentes**

   Se a estrutura for atualizada depois de criar as páginas baseadas no modelo, então essas páginas refletirão as alterações no modelo. Um aviso é exibido na barra de ferramentas para lembrá-lo desse fato, junto com caixas de diálogo de confirmação.

   ![chlimage_1-379](assets/chlimage_1-379.png)

### Editar um modelo - Conteúdo inicial - Criação {#editing-a-template-initial-content-author}

**Conteúdo inicial** O modo é usado para o conteúdo definido que será exibido quando uma página for criada pela primeira vez com base no modelo. O conteúdo inicial pode ser editado pelos autores da página.

Embora todo o conteúdo criado no modo **Estrutura** seja visível no **Conteúdo inicial**, somente os componentes que foram desbloqueados podem ser selecionados e editados.

>[!NOTE]
>
>O modo **Conteúdo inicial** pode ser visto como um modo de edição para páginas criadas com esse modelo. Sendo assim, as políticas não estão definidas no modo **Conteúdo inicial**, mas no modo **[Estrutura](/help/sites-authoring/templates.md#editing-a-template-structure-template-author)**.

* Os componentes desbloqueados que estão disponíveis para edição são marcados. Quando selecionados, têm uma borda azul:

   ![chlimage_1-380](assets/chlimage_1-380.png)

* Os componentes desbloqueados têm uma barra de ferramentas, permitindo editar e configurar o conteúdo:

   ![chlimage_1-381](assets/chlimage_1-381.png)

* Se um componente do contêiner foi desbloqueado (no modo **estrutura**), você pode adicionar novos componentes ao contêiner (no modo **Conteúdo inicial**). Os componentes adicionados no modo **Conteúdo inicial** podem ser movidos para ou excluído das páginas resultantes.

   Você pode adicionar o componente utilizando a área **Arraste componentes até aqui** ou a opção **Inserir novo componente** na barra de ferramentas do contêiner apropriado.

   ![chlimage_1-382](assets/chlimage_1-382.png) ![chlimage_1-383](assets/chlimage_1-383.png)

* Se o conteúdo inicial do modelo for atualizado depois que as páginas forem criadas com base no modelo, então essas páginas não serão afetadas por alterações no conteúdo inicial no modelo.

>[!NOTE]
>
>O conteúdo inicial destina-se à preparação de componentes e do layout da página que servem como ponto de partida para a criação do conteúdo. Não se destina a ser o conteúdo real que permaneceria como está. Por isso, o conteúdo inicial não pode ser traduzido.

### Editar um modelo - Layout - Autor do modelo {#editing-a-template-layout-template-author}

É possível definir o layout do modelo para um intervalo de dispositivos. O [Layout responsivo](/help/sites-authoring/responsive-layout.md) para modelos funciona como na criação de página.

>[!NOTE]
>
>As modificações no layout serão refletidas no modo **Conteúdo inicial**, mas nenhuma alteração será vista no modo **Estrutura**.

![chlimage_1-384](assets/chlimage_1-384.png)

### Editar um modelo - Design da página - Autor/desenvolvedor do modelo {#editing-a-template-page-design-template-author-developer}

O design da página, incluindo as bibliotecas do lado do cliente e as políticas de página necessárias, é mantido na opção **Design da página** do menu **Informações da página**.

Para acessar o **Design da página** caixa de diálogo:

1. No **Editor de modelos**, selecione **Informações da página** na barra de ferramentas, em seguida **Design da página** para abrir a caixa de diálogo.
1. O **Design da página** é aberta e dividida em duas seções:

   * A metade esquerda define a variável [políticas da página](/help/sites-authoring/templates.md#page-policies)
   * A metade direita define a variável [propriedades da página](/help/sites-authoring/templates.md#page-properties)

   ![chlimage_1-385](assets/chlimage_1-385.png)

#### Políticas da página {#page-policies}

É possível aplicar uma política de conteúdo ao modelo ou às páginas resultantes. Isso define a política de conteúdo do sistema de parágrafo principal na página.

![chlimage_1-386](assets/chlimage_1-386.png)

* É possível selecionar uma política existente para a página na lista suspensa **Selecionar política**.

   ![chlimage_1-387](assets/chlimage_1-387.png)

   Uma nova política pode ser adicionada ao selecionar o botão adicionar ao lado da lista suspensa **Selecionar política**. Um novo título deve ser especificado no campo **Título da política**.

   ![chlimage_1-388](assets/chlimage_1-388.png)

   A política existente selecionada na lista suspensa **Selecionar política** pode ser copiada como uma nova política usando o botão copiar ao lado do menu suspenso. Um novo título deve ser especificado no campo **Título da política**. Por padrão, a política copiada será denominada **Cópia de X**, onde X é o título da política copiada.

   ![chlimage_1-389](assets/chlimage_1-389.png)

* Defina um título para a política no campo **Título da política**. É necessário que a política tenha um título para que possa ser facilmente selecionada na lista suspensa **Selecionar política**.

   ![chlimage_1-390](assets/chlimage_1-390.png)

* É opcional uma descrição da política no campo **Descrição da política**.
* Na seção **Outros modelos que também utilizam a política selecionada**, você pode ver qual modelo utiliza a política selecionada na lista suspensa **Selecionar política**.

   ![chlimage_1-391](assets/chlimage_1-391.png)

#### Propriedades da página {#page-properties}

Usando as propriedades de página, é possível definir as bibliotecas do lado do cliente necessárias usando a caixa de diálogo **Design da página**. Essas bibliotecas do lado do cliente incluem folhas de estilo e o javascript a serem carregados com o modelo e as páginas criadas com esse modelo.

![chlimage_1-392](assets/chlimage_1-392.png)

* Especifique as bibliotecas do lado do cliente que deseja aplicar às páginas criadas com este modelo. Inserção do nome de uma biblioteca no campo de texto na **Bibliotecas do lado do cliente** seção.

   ![chlimage_1-393](assets/chlimage_1-393.png)

* Se as várias bibliotecas forem necessárias, clique no botão Adicionar para adicionar um campo de texto extra para o nome da biblioteca.

   ![chlimage_1-394](assets/chlimage_1-394.png)

   Adicione quantos campos de texto forem necessário para suas bibliotecas do lado do cliente.

   ![chlimage_1-395](assets/chlimage_1-395.png)

* Defina a posição relativa das bibliotecas conforme necessário, ao arrastar os campos usando a alça de arrastar.

   ![chlimage_1-396](assets/chlimage_1-396.png)

>[!NOTE]
>
>Como o autor do modelo pode especificar a política de página no modelo, ele precisará obter detalhes das bibliotecas do lado do cliente apropriadas do desenvolvedor.

### Editar um modelo - Propriedades da página inicial - Criação {#editing-a-template-initial-page-properties-author}

Usando a opção **Propriedades da página inicial**, é possível definir as [propriedades de página](/help/sites-authoring/editing-page-properties.md) iniciais a ser usadas ao criar páginas resultantes.

1. No editor de modelo, selecione **Informações da página** na barra de ferramentas, em seguida **Propriedades da página inicial** para abrir a caixa de diálogo.

1. Na caixa de diálogo, é possível definir as propriedades que deseja aplicar às páginas criadas com esse modelo.

   ![chlimage_1-397](assets/chlimage_1-397.png)

1. Confirme suas definições com **Concluído**.

## Práticas recomendadas   {#best-practices}

Ao criar modelos, você deve considerar:

1. O impacto das alterações no modelo depois que as páginas forem criadas a partir desse modelo.

   Esta é uma lista das diferentes operações possíveis em modelos, juntamente com a forma como afetam as páginas criadas a partir delas:

   * Alterações na estrutura:

      * Eles são aplicados imediatamente às páginas resultantes.
      * A publicação do template alterado ainda é necessária para os visitantes visualizarem as alterações.
   * Alterações nas políticas de conteúdo e configurações de design:

      * Elas se aplicam imediatamente às páginas resultantes.
      * É necessária a publicação das alterações para que os visitantes vejam as alterações.
   * Alterações no conteúdo inicial:

      * Elas se aplicam apenas às páginas criadas após as alterações no modelo.
   * As alterações no layout dependem se o componente modificado fizer parte de:

      * Somente estrutura - aplicada imediatamente
      * Contém conteúdo inicial - somente em páginas criadas após a alteração

   Tome especial cuidado ao:

   * Bloquear ou desbloquear componentes em modelos ativados.
   * Isso pode ter efeitos colaterais, já que as páginas existentes já podem usá-lo. Normalmente:

      * Desbloquear componentes (que foram bloqueados) estará ausente nas páginas existentes.
      * Bloquear componentes (que eram editáveis) ocultará esse conteúdo nas páginas.

   >[!NOTE]
   >
   >AEM dá avisos explícitos ao alterar o status de bloqueio de componentes em modelos que não são mais rascunhos.

1. [Criar suas próprias pastas](#creating-a-template-folder-admin) para seus modelos específicos de site.
1. [Publicar seus modelos](#publishing-a-template-template-author) do **Modelos** console.
