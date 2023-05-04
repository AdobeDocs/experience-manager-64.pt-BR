---
title: Personalizar o layout e o posicionamento de mensagens de erro de um formulário adaptável
seo-title: Customize layout and positioning of error messages of an adaptive form
description: Você pode personalizar o layout e o posicionamento das mensagens de erro de um adaptador para.
seo-description: You can customize layout and positioning of the error messages of an adaptive for.
uuid: 18b6d770-8b68-4aa0-b866-6325a6ceabcf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: e1431ad9-3bae-4ac3-97e2-96dcbfce1f71
exl-id: a57bd3c4-2d50-4089-8279-1e403e9469bf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 1%

---

# Personalizar o layout e o posicionamento de mensagens de erro de um formulário adaptável {#customize-layout-and-positioning-of-error-messages-of-an-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode personalizar o layout e o posicionamento das mensagens de erro de um formulário adaptável. Você pode executar as seguintes personalizações:

* Personalizar o local e o layout da legenda de um campo sem fazer qualquer alteração nas propriedades de CSS correspondentes
* Personalizar a posição de mensagens de erro em linha
* Personalizar o conteúdo do indicador dinâmico de ajuda
* Personalizar a posição dos componentes do campo (legenda, widget, descrição curta, descrição longa e componentes do indicador de ajuda) sem fazer qualquer alteração nas propriedades de CSS correspondentes

## Personalizar layout de campos {#customize-layout-of-fields}

Você pode personalizar o layout de um único campo ou de todos os campos para alterar a posição da legenda e das mensagens de erro. Execute as seguintes etapas para aplicar um layout personalizado a um campo:

### Personalizar layout de um único campo {#customize-layout-of-a-single-field}

Execute as seguintes etapas para aplicar um layout personalizado a um único campo:

1. Abra o formulário em **Estilo** modo. Para abrir o formulário no modo de estilo, na barra de ferramentas da página, toque em ![lista suspensa de tela](assets/canvas-drop-down.png) > **Estilo**.
1. Na barra lateral, abaixo **Objetos de formulário**, selecione o campo e toque no botão editar ![botão editar](assets/edit-button.png).
1. Selecione o estado do campo que deseja personalizar e especifique o estilo desse estado.

   ![Especificação do estilo em linha de um campo](assets/edit-error-state.png)

### Personalizar o layout de todos os campos de um formulário {#customize-layout-of-all-the-fields-of-a-form}

Com o AEM Forms, agora é possível criar um tema e aplicá-lo ao formulário. O editor de temas permite que você especifique o estilo dos componentes do formulário em um local. Ao criar um tema, especifique o estilo em um nível de componente. Para obter mais informações sobre temas, consulte [Temas no AEM Forms](/help/forms/using/themes.md).

Crie um tema usando o Editor de temas para personalizar o layout de todos os campos do formulário. Depois de criar um tema, execute as seguintes etapas para aplicá-lo a um formulário:

1. Abra o formulário no modo de edição.
1. No modo de edição, selecione um componente e toque em ![nível de campo](assets/field-level.png) > **Contêiner de formulário adaptável** e toque em ![cmppr](assets/cmppr.png).
1. Na barra lateral, em Tema de formulário adaptável, selecione o tema que você criou usando o Editor de temas.

## Criar um layout de campo personalizado {#create-a-custom-field-layout}

1. Abra o CRXDE lite. O URL padrão é `https://[Server]:[Port]/crx/de`.
1. Copie um layout de campo do nó /libs/fd/af/layouts/field (Por exemplo, defaultFieldLayout) para o nó /apps (Por exemplo, /apps/af-field-layout).
1. Renomeie o nó copiado e o arquivo defaultFieldLayout.jsp . Por exemplo, errorOnRight.jsp.

1. Altere o valor das propriedades qdica e jcr:description do nó copiado. Por exemplo, altere o valor das propriedades para Error On Right

1. Para adicionar novos estilos e comportamento, crie uma biblioteca do cliente no nó /etc.

   Por exemplo, no local /etc/af-field-layout-clientlib, crie o nó client-library. Adicione a propriedade categories com o valor af.field.errorOnRight e o arquivo style.less com o seguinte código:

   ```css
   .widgetErrorWrapper {
   
    height: 38px;
    margin: 5px;
   
    .guideFieldWidget{
    width: 60%;
    float: left; 
    }
   
    .guideFieldError{
    overflow:hidden;
    width:40%; 
    }
   
   }
   ```

1. Para aprimorar a aparência e o comportamento, inclua a biblioteca do cliente criada no arquivo de layout (errorOnRight.jsp).
1. Abra a caixa de diálogo de edição do campo e selecione a opção **Estilo** guia . No **Configurar layout de campo** , selecione o layout recém-criado e clique em **OK**.

O pacote ErrorOnRight.zip contém um código para mostrar mensagens de erro no lado direito dos campos.

[Obter arquivo](assets/erroronright.zip)
