---
title: Criar aparências personalizadas em formulários HTML5
seo-title: Create custom appearances in HTML5 forms
description: Você pode conectar widgets personalizados a um Forms móvel. Você pode estender widgets jQuery existentes ou desenvolver seus próprios widgets personalizados.
seo-description: You can plug in custom widgets to a Mobile Forms. You can extend existing jQuery Widgets or develop your own custom widgets.
uuid: afb16f42-e404-478b-82dd-4b5b59c4f184
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 5d860f05-3257-4cf7-93dd-77d226d59b39
feature: Mobile Forms
exl-id: e9e53b6d-6403-4d37-bac1-efaff0317f34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---

# Criar aparências personalizadas em formulários HTML5 {#create-custom-appearances-in-html-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode conectar widgets personalizados a um Forms móvel. Você pode estender widgets jQuery existentes ou desenvolver seus próprios widgets personalizados usando a estrutura de aparências. O mecanismo XFA usa vários widgets, consulte [Estrutura de aparência para formulários adaptáveis e HTML5](/help/forms/using/introduction-widgets.md) para obter informações detalhadas.

![Um exemplo de widget padrão e personalizado](assets/custom-widgets.jpg)
**Figura:** *Um exemplo de widget padrão e personalizado*

## Integração de widgets personalizados com formulários HTML5 {#integrating-custom-widgets-with-html-forms}

### Criar um perfil  {#create-a-profile-nbsp}

Você pode criar um perfil ou escolher um perfil existente para adicionar um widget personalizado. Para obter mais informações sobre como criar perfis, consulte [Criar perfil personalizado](/help/forms/using/custom-profile.md).

### Criar um widget {#create-a-widget}

Os formulários HTML5 fornecem uma implementação da estrutura do widget que pode ser estendida para criar novos widgets. A implementação é um widget jQuery *abstractWidget* que pode ser estendida para gravar um novo widget. O novo widget só pode ser funcional estendendo/substituindo as funções mencionadas abaixo.

<table> 
 <tbody> 
  <tr> 
   <td>Função/Classe</td> 
   <td>Descrição</td> 
  </tr> 
  <tr> 
   <td>renderizar</td> 
   <td>A função de renderização retorna o objeto jQuery para o elemento HTML padrão do widget. O elemento HTML padrão deve ser do tipo focalizável. Por exemplo, &lt;a&gt;, &lt;input&gt;e &lt;li&gt;. O elemento retornado é usado como $userControl. Se $userControl especificar a restrição acima, as funções da classe AbstractWidget funcionarão conforme esperado, caso contrário, algumas das APIs comuns (foco, clique) exigirão alterações. </td> 
  </tr> 
  <tr> 
   <td>getEventMap</td> 
   <td>Retorna um mapa para converter eventos HTML em eventos XFA. <br /> {<br /> desfoque: XFA_EXIT_EVENT,<br /> }<br /> Este exemplo mostra que o desfoque é um evento HTML e XFA_EXIT_EVENT é um evento XFA correspondente. </td> 
  </tr> 
  <tr> 
   <td>getOptionsMap</td> 
   <td>Retorna um mapa que fornece detalhes sobre qual ação executar na alteração de uma opção. As chaves são as opções fornecidas para o widget e os valores são as funções que são chamadas sempre que uma alteração nessa opção é detectada. O widget fornece manipuladores para todas as opções comuns (exceto valor e displayValue)</td> 
  </tr> 
  <tr> 
   <td>getCommitValue</td> 
   <td>A estrutura Widget carrega a função sempre que o valor do widget é salvo no XFAModel (por exemplo, no evento exit de um textField). A implementação deve retornar o valor salvo no widget. O manipulador é fornecido com o novo valor para a opção .</td> 
  </tr> 
  <tr> 
   <td>showValue</td> 
   <td>Por padrão, no XFA on enter event, o rawValue do campo é exibido. Essa função é chamada para mostrar o rawValue ao usuário. </td> 
  </tr> 
  <tr> 
   <td>showDisplayValue</td> 
   <td>Por padrão, no evento XFA on exit , o formattedValue do campo é exibido. Essa função é chamada para mostrar o formattedValue ao usuário. </td> 
  </tr> 
 </tbody> 
</table>

Para criar seu próprio widget, no perfil criado acima, inclua referências do arquivo JavaScript que contém funções substituídas e funções recém-adicionadas. Por exemplo, a variável *sliderNumericFieldWidget* é um widget para campos numéricos. Para usar o widget em seu perfil na seção de cabeçalho, inclua a seguinte linha:

```
window.formBridge.registerConfig("widgetConfig" , widgetConfigObject);
```

### Registrar widget personalizado com o mecanismo de script XFA  {#register-custom-widget-with-xfa-scripting-engine-nbsp}

Quando o código de widget personalizado estiver pronto, registre o widget com o mecanismo de script usando `registerConfig`API para [Form Bridge](/help/forms/using/form-bridge-apis.md). Ele utiliza o widgetConfigObject como entrada.

```
window.formBridge.registerConfig("widgetConfig",
        {
        ".<field-identifier>":"<name-of-the-widget>"
        }
    );
```

#### widgetConfigObject {#widgetconfigobject}

A configuração do widget é fornecida como um objeto JSON (uma coleção de pares de valores chave), onde a chave identifica os campos e o valor representa o widget a ser usado com esses campos. Uma configuração de amostra tem a seguinte aparência:

```
*{*

*“identifier1” : “customwidgetname”,  
“identifier2” : “customwidgetname2”,  
..  
}*
```

onde &quot;identificador&quot; é um seletor CSS jQuery que representa um campo específico, um conjunto de campos de um tipo específico ou todos os campos. A seguir, o valor do identificador é listado em casos diferentes:

| Tipo de identificador | Identificador | Descrição |
|---|---|---|
| Campo específico com nome do campo | Identificador: &quot;div.fieldname&quot; | Todos os campos com o nome &quot;nome do campo&quot; são renderizados usando o widget. |
| Todos os campos do tipo &quot;type&quot; (onde o tipo é NumericField, DateField e assim por diante).: | Identificador: &quot;div.type&quot; | Para Timefield e DateTimeField, o tipo é campo de texto, pois esses campos não são compatíveis. |
| Todos os campos | Identificador: &quot;div.field&quot; |  |
