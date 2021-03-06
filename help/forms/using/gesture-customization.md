---
title: Personalização do gesto
seo-title: Personalização do gesto
description: Personalize os gestos no aplicativo AEM Forms
seo-description: Personalize os gestos no aplicativo AEM Forms
uuid: 117e0e21-66bd-42f1-879c-6c1443991974
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 747d13d3-e7cc-4aa1-bcc8-4b57157e71ed
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Personalização do gesto {#gesture-customization}

Você pode personalizar os gestos do aplicativo AEM Forms para fornecer um método distinto de interação com o aplicativo. Por exemplo, você pode adicionar novos gestos para abrir ou fechar uma tarefa ou ponto de partida.

## Para personalizar gestos no aplicativo AEM Forms {#to-customize-gestures-in-aem-forms-app}

No aplicativo AEM Forms, o deslize para a esquerda abre uma nova tarefa ou ponto de partida enquanto o deslize para a direita não faz nada. O exemplo a seguir fornece etapas para abrir uma nova tarefa ou ponto de partida na execução dos gestos de deslizamento direito no aplicativo AEM Forms.

1. Abra seu projeto.

   * Para iOS, abra `Capture.xcodeproj` no Xcode
   * Para Android, abra o projeto do Android no Eclipse.
   * Para Windows, abra `MWSWindows.sln` no Visual Studio.

1. Navegue até a pasta visualização e abra o arquivo `task.js` para edição.

   * No Xcode, navegue até a pasta **Capturar > www > wsmobile > js > tempo de execução > visualização**.
   * No Eclipse, navegue até a pasta **assets > www > wsmobile > js > tempo de execução > visualização**.
   * No Visual Studio, navegue até a pasta **MWSWwindows > www > wsmobile > js > tempo de execução > visualização**.

   >[!NOTE]
   >
   >O arquivo tarefa.js contém a visualização de backbone associada a cada tarefa ou ponto de partida listado nas listas de tarefa ou ponto de partida.

1. No arquivo `task.js`, procure a propriedade eventos da visualização.

   A propriedade eventos é um mapa com cada entrada no formato:

   `"EventName Selector": "Function"`

   Quando você aciona um evento Javascript chamado `EventName`em um elemento HTML especificado por `Selector`, o `Function`é chamado.

1. Localizar

   * &quot;toque em .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;tocar em .taskOpenArea&quot;: &quot;onTaskClick&quot;,

      &quot;toque em .tarefa-content&quot; : &quot;onTaskClick&quot;,

      &quot;toque em .last_empty_div&quot; : &quot;onTaskClick&quot;,
   e substitua por

   * &quot;deslize .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;deslize .taskOpenArea&quot;: &quot;onTaskClick&quot;,

      &quot;deslize o conteúdo .tarefa&quot;: &quot;onTaskClick&quot;,

      &quot;deslize .last_empty_div&quot; : &quot;onTaskClick&quot;,


1. Salve e feche o arquivo `task.js`.
1. Crie e execute o aplicativo AEM Forms. Agora você pode abrir um usando com o dedo para a esquerda e o dedo para a direita.

Da mesma forma, é possível fazer alterações em outras visualizações para várias combinações de gestos, elementos HTML e funções.

