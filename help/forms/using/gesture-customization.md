---
title: Personalização de gestos
seo-title: Gesture customization
description: Personalizar os gestos no aplicativo AEM Forms
seo-description: Customize the gestures on your AEM Forms app
uuid: 117e0e21-66bd-42f1-879c-6c1443991974
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 747d13d3-e7cc-4aa1-bcc8-4b57157e71ed
exl-id: 238410e0-1623-49dc-b2fc-b5b2d5fb362b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 2%

---

# Personalização de gestos {#gesture-customization}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode personalizar os gestos do aplicativo AEM Forms para fornecer um método distinto de interação com o aplicativo. Por exemplo, você pode adicionar novos gestos para abrir ou fechar uma tarefa ou ponto de partida.

## Como personalizar gestos no aplicativo AEM Forms {#to-customize-gestures-in-aem-forms-app}

No aplicativo AEM Forms, o deslizamento à esquerda abre uma nova tarefa ou ponto de partida enquanto o deslizamento à direita não faz nada. O exemplo a seguir fornece etapas para abrir uma nova tarefa ou ponto de partida na execução dos gestos de deslizamento com o botão direito no aplicativo AEM Forms.

1. Abra o projeto.

   * Para iOS, abra `Capture.xcodeproj` no Xcode
   * Para Android, abra o projeto Android no Eclipse.
   * Para Windows, abra `MWSWindows.sln` no Visual Studio.

1. Navegue até a pasta de exibições e abra o `task.js` para edição.

   * No XCode, navegue até o **Capturar > www > wsmobile > js > tempo de execução > exibições** pasta.
   * No Eclipse, navegue até o **ativos > www > wsmobile > js > tempo de execução > exibições** pasta.
   * No Visual Studio, navegue até o **Windows > www > wsmobile > js > tempo de execução > exibições** pasta.

   >[!NOTE]
   >
   >O arquivo task.js contém a exibição de backbone associada a cada tarefa ou ponto de partida listado nas listas de tarefa ou ponto de partida.

1. No `task.js` , procure a propriedade events da exibição.

   A propriedade events é um mapa com cada entrada no formato :

   `"EventName Selector": "Function"`

   Ao acionar um evento Javascript chamado `EventName`em um elemento HTML especificado por `Selector`, o `Function`é chamado.

1. Localizar

   * &quot;toque em .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;toque em .taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;toque em .task-content&quot; : &quot;onTaskClick&quot;,

      &quot;toque em .last_empty_div&quot; : &quot;onTaskClick&quot;,
   e substitua por

   * &quot;swipe .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .task-content&quot; : &quot;onTaskClick&quot;,

      &quot;swipe .last_empty_div&quot; : &quot;onTaskClick&quot;,


1. Salve e feche o `task.js` arquivo.
1. Crie e execute o aplicativo AEM Forms. Agora você pode abrir um usando com o dedo esquerdo e o dedo direito.

Da mesma forma, é possível fazer alterações em outras exibições para várias combinações de gestos, elementos de HTML e funções.
