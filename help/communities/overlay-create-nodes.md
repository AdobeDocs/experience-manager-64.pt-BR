---
title: Criar nós
seo-title: Create Nodes
description: Sobrepor o sistema de comentários
seo-description: Overlay the comments system
uuid: 802ae28b-9989-4c2c-b466-ab76a724efd3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cd4f53ee-537b-4f10-a64f-474ba2c44576
exl-id: fc044a4e-0037-405f-8c26-b388c6a98733
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 12%

---

# Criar nós {#create-nodes}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Sobreponha o sistema de comentários com uma versão personalizada copiando o número mínimo de arquivos necessários de /libs para /apps e modificando-os em /apps.

>[!CAUTION]
>
>O conteúdo da pasta /libs nunca é editado porque qualquer reinstalação ou atualização pode excluir ou substituir a pasta /libs enquanto o conteúdo da pasta /apps é deixado intocado.

Usando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) em uma instância do autor, comece criando um caminho na pasta /apps, que é idêntico ao caminho para os componentes sobrepostos na pasta /libs.

O caminho que está sendo duplicado é

* `/libs/social/commons/components/hbs/comments/comment`

Alguns nós no caminho são pastas e alguns são componentes.

1. Navegue até [http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. Criar `/apps/social` (se ainda não existir)
   * Selecionar `/apps` nó
   * **[!UICONTROL Criar > Pasta ...]**
      * Digite o nome: `social`
1. Selecionar `social` nó
   * **[!UICONTROL Criar > Pasta...]**
      * Digite o nome: `commons`
1. Selecionar `commons` nó
   * **[!UICONTROL Criar > Pasta...]**
      * Digite o nome: `components`
1. Selecionar `components` nó
   * **[!UICONTROL Criar > Pasta...]**.
      * Digite o nome: `hbs`
1. Selecionar `hbs` nó
   * **[!UICONTROL Criar > Criar componente..]**
      * Inserir Rótulo: `comments`
      * Inserir Título: `Comments`
      * Inserir descrição: `List of comments without showing avatars`
      * Super Type: `social/commons/components/comments`
      * Inserir Grupo: `Communities`
      * Clique em **[!UICONTROL Próximo]** until **[!UICONTROL OK]**
1. Selecionar `comments` nó

   * **[!UICONTROL Criar > Criar componente..]**

      * Inserir Rótulo: `comment`
      * Inserir Título: `Comment`
      * Inserir descrição: `A comment instance without avatars`
      * Super Type: `social/commons/components/comments/comment`
      * Inserir Grupo: `.hidden`
      * Clique em **[!UICONTROL Próximo]** until **[!UICONTROL OK]**
   * Selecionar **[!UICONTROL Salvar tudo]**
1. Excluir o padrão `comments.jsp`
   * Selecionar nó `/apps/social/commons/components/hbs/comments/comments.jsp`
   * Selecione **[!UICONTROL Excluir]**
1. Exclua o arquivo comment.jsp padrão
   * selecionar nó `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * Selecione **[!UICONTROL Excluir]**
   * Selecionar **[!UICONTROL Salvar tudo]**

>[!NOTE]
>
>Para preservar a cadeia de herança, a variável `Super Type` (propriedade) `sling:resourceSuperType`) dos componentes de sobreposição são definidos com o mesmo valor de `Super Type` dos componentes que estão sendo sobrepostos, neste caso
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`
>


A própria sobreposição `Type`(propriedade) `sling:resourceType`) deve ser uma referência automática relativa, para que qualquer conteúdo não encontrado em /apps seja procurado em /libs.
* Nome: `sling:resourceType`
* Tipo: `String`
* Valor: `social/commons/components/hbs/comments`

1. Selecione o verde `[+] Add`
   * Nome: `sling:resourceType`
   * Tipo: `String`
   * Valor: `social/commons/components/hbs/comments/comment`
1. Selecione o verde `[+] Add`
   * Selecionar **[!UICONTROL Salvar tudo]**

![chlimage_1-4](assets/chlimage_1-4.png)
