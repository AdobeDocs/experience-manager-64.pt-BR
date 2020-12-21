---
title: Alterar a aparência (HBS)
seo-title: Alterar a aparência
description: Modificar os scripts HBS
seo-description: Modificar os scripts HBS
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# Alterar a aparência (HBS) {#alter-the-appearance-hbs}

Agora que os componentes do sistema de comentários personalizado no diretório do aplicativo (/apps) estão em vigor, com um resourceSuperType referenciando o sistema de comentários padrão e o Modelo/Visualização personalizado registrado, é possível modificar a implementação.

Para uma demonstração simples, um recurso visual, o avatar mostrado pelo usuário conectado que publica um comentário, é removido.

>[!NOTE]
>
>Para usar a extensão, a instância do sistema de comentários em um site a ser afetado (/content) deve definir resourceType como o sistema de comentários personalizado.

## Modificar os scripts HBS {#modify-the-hbs-scripts}

Usando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Abra [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Comente a tag que inclui o avatar para uma postagem de comentário (~ linha 21):

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* Abra [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Comente a tag que inclui o avatar para a próxima entrada de comentário (~ linha 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Selecione **Salvar tudo**

## Replicar aplicativo personalizado {#replicate-custom-app}

Após a modificação do aplicativo, é necessário rereplicar o componente personalizado.

Uma maneira de o fazer é

* No menu principal

   * Selecione **[!UICONTROL Ferramentas > Operações > Replicação]**
   * Selecionar `Activate Tree`
   * Definir `Start Path`: para `/apps/custom`
   * Desmarcar `Only Modified`
   * Botão Selecionar `Activate`

## Comentário modificado da visualização na página de amostra publicada {#view-modified-comment-on-published-sample-page}

[Continuando a ](extend-sample-page.md#publish-sample-page) experiência na instância de publicação, ainda conectado como o mesmo usuário, agora é possível atualizar a página no ambiente de publicação para visualização da modificação para remover o avatar:

![chlimage_1-81](assets/chlimage_1-81.png)

## Pacote de extensão de comentário de amostra {#sample-comment-extension-package}

Anexado é um pacote do aplicativo de comentários personalizado criado neste tutorial.

[Obter arquivo](assets/sample-comment-extension-6-1-fp3.zip)