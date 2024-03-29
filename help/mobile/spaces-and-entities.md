---
title: Espaços e entidades
seo-title: Developing AEM Mobile Content Services
description: Esta página serve uma página de aterrissagem para desenvolver os Serviços de conteúdo da AEM Mobile.
seo-description: This page serves a landing page for developing AEM Mobile Content Services.
uuid: eab5a61b-a9e8-4863-90a3-df1f18510cd8
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
discoiquuid: ef568577-c74e-4fc2-b66e-eedac2948310
exl-id: d4f29e1a-4d5c-4bdf-b530-7cd51bf709e7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 1%

---

# Espaços e entidades{#spaces-and-entities}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>A Adobe recomenda usar o Editor de SPA para projetos que exigem renderização do lado do cliente com base em estrutura de aplicativo de página única (por exemplo, React). [Saiba mais](/help/sites-developing/spa-overview.md).

Um Espaço é um local conveniente para armazenar entidades expostas por meio da API REST dos serviços de conteúdo. Isso é especialmente útil porque um aplicativo (ou qualquer canal) pode ser associado a muitas entidades. Forçar as entidades a estarem em um espaço força a prática recomendada de agrupar os requisitos de um aplicativo. Como opção, você pode associar um aplicativo no AEM com um pequeno número de Espaços.

>[!NOTE]
>
>Para disponibilizar algo para qualquer canal do Content Services, ele precisa estar em um espaço.

## Criação de um espaço {#creating-a-space}

Se o usuário quiser expor um conjunto de conteúdo e ativos a um aplicativo móvel, ele criará o espaço usando o painel do AEM Mobile.

Pela primeira vez que o usuário que não tiver configurado os serviços de conteúdo para funcionar com espaços, o painel do AEM Mobile exibirá somente Aplicativos depois de selecionar **Serviços de conteúdo**.

>[!CAUTION]
>
>**Pré-requisitos para adicionar um espaço**
>
>Verifique a **Ativar os serviços de conteúdo AEM** para trabalhar com o Spaces e ativá-lo no painel de aplicativos do AEM Mobile.
>
>Consulte [Administração dos serviços de conteúdo](/help/mobile/developing-content-services.md) para obter mais detalhes.

Depois de configurar os Espaços no painel, siga estas etapas para criar Espaços:

1. Choose **Espaços** dos Serviços de conteúdo.

   ![chlimage_1-83](assets/chlimage_1-83.png)

1. Choose **Criar** para criar um espaço. Enter **Título**, **Nome** e **Descrição** para o espaço.

   Clique em **Criar**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

## Gerenciamento de um espaço {#managing-a-space}

Depois de criar um espaço, clique em à esquerda para gerenciar o espaço na lista.

É possível exibir propriedades do espaço, excluir o espaço ou publicar o espaço e seu conteúdo em uma instância de publicação de AEM.

![chlimage_1-85](assets/chlimage_1-85.png)

**Exibindo e editando propriedades de um espaço**

1. Selecione o espaço na lista
1. Choose **Propriedades** na barra de ferramentas
1. Clique em **Fechar** quando concluído

**Publicar um espaço** Quando um espaço é publicado, todas as pastas e entidades nesse espaço também são publicadas.

1. Selecione o espaço clicando no ícone na lista Console de Espaço
1. Choose **Publicar árvore**

>[!NOTE]
>
>Você pode **Cancelar publicação** um Space, que remove o espaço da instância de publicação.
>
>A imagem a seguir ilustra as ações que podem ser executadas, após a publicação do espaço.

![chlimage_1-86](assets/chlimage_1-86.png)

## Trabalhar com pastas em um espaço {#working-with-folders-in-a-space}

Os espaços podem incluir pastas para ajudar a organizar ainda mais o conteúdo e os ativos do espaço. Os usuários podem criar sua própria hierarquia em um espaço.

### Criação de pastas {#creating-a-folder}

1. Clique no espaço na lista no console de espaço e clique em **Criar pasta**

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. Insira o **Título**, **Nome,** e **Descrição** para a pasta

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Clique em **Criar** para criar a pasta em um espaço

## Cópia de idioma {#language-copy}

>[!CAUTION]
>
>A Cópia de idioma não está totalmente funcional para esta versão. Ela só define a estrutura.

O **Cópia de idioma** O recurso permite que os autores copiem sua Cópia de idioma principal e, em seguida, criem um Projeto e um Fluxo de trabalho para traduzir automaticamente o conteúdo. A Cópia de idioma cria a estrutura correta. Depois de adicionar uma pasta em um espaço, você pode adicionar Cópia de idioma ao seu espaço.

>[!NOTE]
>
>Recomenda-se que qualquer conteúdo que possa ser traduzido seja colocado no nó Language Copy .

### Adição de cópia de idioma {#adding-language-copy}

1. Depois de criar espaço, clique nesse espaço para criar uma cópia de idioma.

   Clique em **Criar** e escolha **Cópia de idioma**.

   ![chlimage_1-89](assets/chlimage_1-89.png)

   >[!NOTE]
   >
   >Os nós de Cópia de Idioma só podem existir como um filho direto do Espaço.

1. Choose **Idioma do Pacote de Conteúdo &amp;;** e insira o **&amp;Título;** em **Criar Cópia de Idioma** caixa de diálogo.

   Clique em **Criar**.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Depois de criar uma Cópia de idioma, ela aparecerá no seu espaço em **Mestrados em Idioma**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   >[!NOTE]
   >
   >Selecionar **Mestrados em Idioma** para exibir as pastas de cópia de idioma.

### Remover uma pasta do espaço {#removing-a-folder-from-the-space}

1. Selecione a pasta na lista de conteúdos de espaço
1. Clique em **Excluir** na barra de ferramentas

   >[!NOTE]
   >
   >Para navegar em uma pasta e ver seu conteúdo ou adicionar uma subpasta ou entidade, clique no título da pasta na lista de conteúdo do espaço.

## Trabalhar com entidades em um espaço {#working-with-entities-in-a-space}

As entidades representam o conteúdo exposto por meio do ponto de extremidade do serviço da Web. As entidades são armazenadas em espaços para que possam ser facilmente encontradas e sejam mantidas independentes da estrutura do repositório de AEM que armazena seu conteúdo relacionado.

Talvez você queira agrupar entidades em algum agrupamento lógico. Para fazer isso, é possível criar qualquer número de pastas.

Se filhos de entidades, que são outras entidades, forem coletados para modelagem de dados, o usuário do desenvolvedor poderá criar &quot;Modelos de grupo&quot; específicos do tipo de modelo &quot;Grupo de entidades&quot;, fornecido pronto para uso.

>[!NOTE]
>
>As entidades são sempre associadas a um espaço, de modo que a maior parte da interface do usuário da entidade é acessada por meio do console de espaço.

### Criando uma entidade {#creating-an-entity}

1. Abra o console Espaço e clique no título do espaço.

   Como opção, você pode navegar até a pasta clicando no título da pasta na lista.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Escolha o modelo para a entidade. Esse é o tipo de entidade que você deseja criar. Clique em Avançar.

   ![chlimage_1-93](assets/chlimage_1-93.png)

   >[!NOTE]
   >
   >Você tem a opção de escolher a variável **Modelo de ativos**, **Modelo de páginas** ou um modelo do tipo de entidade criado anteriormente.
   >
   >Consulte [Criação de um modelo](/help/mobile/administer-mobile-apps.md), para criar a entidade personalizada.

1. Insira um **Título**, **Nome**, **Descrição** e **Tags** para a entidade. Clique em **Criar**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

   Quando terminar, a entidade aparecerá nos descendentes de seu espaço.

### Editar uma entidade {#editing-an-entity}

1. Depois de criar uma entidade, vá para a pasta ou espaço e escolha a entidade no console Espaço para editar.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Selecione uma entidade para edição e clique em **Editar**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

   >[!CAUTION]
   >
   >Dependendo do modelo que você escolher para criar sua entidade, a interface do usuário será diferente para as propriedades de edição e exibição da sua entidade. Consulte as etapas abaixo para obter mais detalhes.

   ***Se você escolher o modelo para criar a entidade como Modelos de ativos***, clicando em **Editar** permite adicionar ativos, como mostrado na figura abaixo:

   ![chlimage_1-97](assets/chlimage_1-97.png)

   Como alternativa, você pode clicar em **Visualizar** para exibir o link json.

   ![chlimage_1-98](assets/chlimage_1-98.png)

   ***Se você escolher o modelo para criar a entidade como Modelos de páginas***, clicando em **Editar** permite adicionar ativos, como mostrado na figura abaixo:

   ![chlimage_1-99](assets/chlimage_1-99.png)

   Clique no ícone no **Caminho** para adicionar um ativo

   ![chlimage_1-100](assets/chlimage_1-100.png)

   >[!NOTE]
   >
   >Depois de adicionar uma entidade, ela deve ser salva para que o link Preview funcione. Para visualizar a visualização, clique em **Salvar**. Clicar no **Visualizar** mostra o json do ativo adicionado, como mostrado na figura abaixo:

   ![chlimage_1-101](assets/chlimage_1-101.png)

   >[!NOTE]
   >
   >Quando terminar de adicionar ativos à sua entidade, você poderá escolher **Salvar** para salvar as alterações ou escolha **Salvar e fechar** para salvar e redirecionar para a lista do console Espaço em que as entidades são definidas.

   Além disso, selecione uma entidade na lista console de espaço e clique em **Propriedades** para exibir e editar as propriedades de uma entidade definida.

   ![chlimage_1-102](assets/chlimage_1-102.png)

   Você pode editar o título, a descrição, as tags e adicionar os ativos à sua entidade.

   ![chlimage_1-103](assets/chlimage_1-103.png)

### Remover uma entidade {#removing-an-entity}

1. Selecione a entidade na lista de conteúdos de espaço

   ![chlimage_1-104](assets/chlimage_1-104.png)

1. Clique em **Excluir** na barra de ferramentas para remover a entidade específica do espaço

### Publicar uma entidade {#publishing-an-entity}

Você tem a opção de escolher **Publicar árvore** ou **Publicação rápida** para publicar sua entidade.

1. Selecione uma entidade na lista do console de espaço e clique em **Árvore de publicação **para publicar essa entidade e seus filhos.

   ![chlimage_1-105](assets/chlimage_1-105.png)

   **Ou**,

   Clique em **Publicação rápida** para publicar essa entidade específica.
