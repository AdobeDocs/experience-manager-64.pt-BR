---
title: Alterar a aparência (HBS)
seo-title: Alter the Appearance
description: Modificar os scripts HBS
seo-description: Modify the HBS scripts
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
exl-id: 358b70b8-8122-4eda-baa7-d9a58d6901f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 3%

---

# Alterar a aparência (HBS) {#alter-the-appearance-hbs}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Agora que os componentes do sistema de comentários personalizado no diretório do aplicativo (/apps) estão em vigor, com um resourceSuperType referenciando o sistema de comentários padrão e o Modelo/Exibição personalizado registrado, é possível modificar a implementação.

Para uma demonstração simples, um recurso visual, o avatar mostrado do usuário conectado que publica um comentário, é removido.

>[!NOTE]
>
>Para usar a extensão, a instância do sistema de comentários em um site a ser afetado (/content) deve definir resourceType para ser o sistema de comentários personalizado.

## Modificar os scripts HBS {#modify-the-hbs-scripts}

Usando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Abrir [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Comente a tag que inclui o avatar de uma postagem de comentário (~ linha 21):

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* Abrir [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Comente a tag que inclui o avatar da próxima entrada de comentário (~ linha 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Selecionar **Salvar tudo**

## Replicar aplicativo personalizado {#replicate-custom-app}

Após a modificação do aplicativo, é necessário replicar novamente o componente personalizado.

Uma maneira de fazer isso é

* No menu principal

   * Selecionar **[!UICONTROL Ferramentas > Operações > Replicação]**
   * Selecionar `Activate Tree`
   * Definir `Start Path`: para `/apps/custom`
   * Desmarcar `Only Modified`
   * Selecionar `Activate` botão

## Exibir Comentário Modificado na Página de Amostra Publicada {#view-modified-comment-on-published-sample-page}

[Continuar a experiência](extend-sample-page.md#publish-sample-page) na instância de publicação, ainda conectado como o mesmo usuário, agora é possível atualizar a página no ambiente de publicação para exibir a modificação e remover o avatar:

![chlimage_1-81](assets/chlimage_1-81.png)

## Pacote de extensão de comentário de amostra {#sample-comment-extension-package}

Anexado há um pacote de comentários personalizados criados neste tutorial.

[Obter arquivo](assets/sample-comment-extension-6-1-fp3.zip)
