---
title: Alterar a aparência
seo-title: Alter the Appearance
description: Modificar o script
seo-description: Modify the script
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 4%

---

# Alterar a aparência {#alter-the-appearance}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Modificar o script {#modify-the-script}

O script comment.hbs é responsável pela criação do HTML geral para cada comentário.

Para não exibir o avatar ao lado de cada comentário publicado:

1. Copiar `comment.hbs`from `libs`para `apps`
   1. Selecionar `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Selecionar **[!UICONTROL Copiar]**
   1. Selecionar `/apps/social/commons/components/hbs/comments/comment`
   1. Selecionar **[!UICONTROL Colar]**
1. Abra a sobreposição `comment.hbs`
   * Clique duas vezes no nó  `comment.hbs`em `/apps/social/commons/components/hbs/comments/comment folder`
1. Encontre as seguintes linhas e exclua-as ou comente-as:

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

Exclua as linhas ou rode-as com &#39;&lt;!>—&#39; e &#39;—>&#39; para comentá-las. Além disso, os caracteres &#39;xxx&#39; estão sendo adicionados como um indicador visual de onde o avatar estaria.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## Replicar a sobreposição {#replicate-the-overlay}

Encaminhe o componente comentários sobrepostos para a instância de publicação usando a Ferramenta Replicação.

>[!NOTE]
>
>Uma forma mais robusta de replicação seria criar um pacote no Gerenciador de Pacotes e [ativar](../../help/sites-administering/package-manager.md#replicating-packages) sim. Um pacote pode ser exportado e arquivado.

Na navegação global, selecione **[!UICONTROL Ferramentas > Implantação > Replicação]** e depois **[!UICONTROL Ativar árvore]**.

Para o Caminho de início, insira `/apps/social/commons` e selecione **[!UICONTROL Ativar]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## Exibir resultados {#view-results}

Se você fizer logon na instância de publicação como administrador, por exemplo, http://localhost:4503/crx/de como administrador/administrador, poderá verificar se os componentes sobrepostos estão lá.

Se você fizer logoff e fizer logon novamente como `aaron.mcdonald@mailinator.com/password` e atualize a página, você observará que o comentário publicado não é mais exibido com um avatar, em vez disso, um simples &#39;xxx&#39; é exibido.

![chlimage_1-43](assets/chlimage_1-43.png)
