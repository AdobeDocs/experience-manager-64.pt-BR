---
title: Salvar formulários como modelos
seo-title: Save forms as templates
description: Saiba como criar modelos a partir de formulários com dados necessários repetidamente.
seo-description: Learn how to create templates from forms with data required repeatedly.
uuid: 090c6271-4061-4adc-a063-9df4953b47ce
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e0df2f85-664a-47b3-a8c5-e986b975d421
exl-id: 355c4810-6e45-41cb-9b60-73225bd53526
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 2%

---

# Salvar formulários como modelos {#save-forms-as-templates}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Às vezes, quando os usuários preenchem um formulário, as entradas em alguns campos permanecem as mesmas. Para essas instâncias, é possível preencher os campos que exigem valores idênticos em cada instância e salvar o formulário ou rascunho como template. Agora, toda vez que você cria uma instância do template, os campos especificados já são preenchidos com valores especificados no template. Ajuda a economizar tempo e esforço necessários para preencher o formulário.

Execute as seguintes etapas para criar um modelo:

1. Abra um formulário e selecione ou preencha os campos que têm valores quase idênticos sempre que usá-lo. É possível incluir um anexo com o modelo que você normalmente adiciona ao preencher o formulário.
1. Toque no **Salvar como modelo** ![save_as_template](assets/save_as_template.png)ícone . Uma caixa de diálogo para especificar o nome do modelo é exibida.
1. Especifique o nome do modelo e toque em **Salvar**. O modelo aparece na pasta de modelo.

   Se existir um modelo com o mesmo nome, uma caixa de diálogo para confirmar a substituição do modelo existente será exibida. Para substituir o modelo existente pelo novo modelo, toque em **Continuar** ou para salvar o modelo com um nome diferente, toque em **Cancelar**.

Agora, você pode abrir o modelo salvo. Toda vez que um modelo é aberto, um novo formulário ou tarefa é criada e o formulário exibe os dados e opções salvos. Com modelos, você pode editar os dados pré-preenchidos, adicionar um anexo, salvar como rascunho, enviar a tarefa ou criar outro modelo usando-o. Modelos são específicos de dispositivos móveis e não são sincronizados com o servidor do Adobe Experience Manager Forms.

Também é possível excluir um modelo se ele não for mais necessário. Para excluir um modelo, navegue até a pasta de modelos, toque nas reticências e toque em **Excluir modelo**.

>[!NOTE]
>
>Um modelo está disponível localmente e não é sincronizado com o servidor. Limpar os dados locais do aplicativo exclui o modelo.
