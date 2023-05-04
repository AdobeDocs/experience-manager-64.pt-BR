---
title: Adicionar comentário à página de exemplo
seo-title: Add Comment to Sample Page
description: Adicionar comentários personalizados a uma página
seo-description: Add Custom Comments to a page
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
exl-id: 96ef7e58-66c9-4985-973b-0c6fc7c39fd5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 1%

---

# Adicionar comentário à página de exemplo {#add-comment-to-sample-page}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Agora que os componentes do sistema de comentários personalizado estão no diretório do aplicativo (/apps), é possível usar o componente estendido. A instância do sistema de comentários em um site a ser afetado deve definir seu resourceType como o sistema de comentários personalizado e incluir todas as bibliotecas de clientes necessárias.

## Identificar Clientlibs Necessários {#identify-required-clientlibs}

As bibliotecas de clientes necessárias para o estilo e o funcionamento dos Comentários padrão também são necessárias para os Comentários estendidos.

O [Guia de componentes da comunidade](components-guide.md) identifica as bibliotecas de clientes necessárias. Navegue até o Guia de componentes e exiba o componente Comentários , por exemplo:

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

Observe as três bibliotecas de clientes necessárias para que os Comentários renderizem e funcionem corretamente. Eles precisarão ser incluídos onde os Comentários estendidos forem referenciados, bem como a variável [biblioteca cliente de comentários estendidos](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![chlimage_1-47](assets/chlimage_1-47.png)

## Adicionar comentários personalizados a uma página {#add-custom-comments-to-a-page}

Como pode haver apenas um sistema de Comentários por página, é mais simples criar uma página de exemplo, conforme descrito no [Criar uma página de exemplo](create-sample-page.md) tutorial.

Depois de criado, entre no modo Design e disponibilize o grupo de componentes Personalizado para permitir a `Alt Comments` componente a ser adicionado à página.

Para que o Comentário apareça e funcione corretamente, as bibliotecas de clientes para Comentários devem ser adicionadas à lista de clientlibslist para a página (consulte [Clientlibs para componentes do Communities](clientlibs.md)).

### Comentários Clientlibs na página de exemplo {#comments-clientlibs-on-sample-page}

![Comentários Clientlibs na página de exemplo](assets/chlimage_1-48.png)

### Autor: Comentário alternativo na página de exemplo {#author-alt-comment-on-sample-page}

![Comentário alternativo na página de exemplo](assets/chlimage_1-49.png)

### Autor: Exemplo de nó Comentários da Página {#author-sample-page-comments-node}

Você pode verificar o resourceType no CRXDE exibindo as propriedades do nó comments da página de exemplo em `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-50](assets/chlimage_1-50.png)

### Página Publicar exemplo {#publish-sample-page}

Depois que o componente personalizado é adicionado à página, também é necessário (re) [publicar a página](sites-console.md#publishing-the-site).

### Publicar: Comentário alternativo na página de exemplo {#publish-alt-comment-on-sample-page}

Depois de publicar o aplicativo personalizado e a página de exemplo, deve ser possível inserir um comentário. Quando estiver conectado, com um [usuário de demonstração](tutorials.md#demo-users) Para administrador, deve ser possível postar um comentário.

Aqui está aaron.mcdonald@mailinator.com postando um comentário:

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

Agora que parece que o componente estendido está funcionando corretamente com a aparência padrão, é hora de modificar a aparência.
