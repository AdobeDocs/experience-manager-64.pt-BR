---
title: Personalização de Tema
seo-title: Personalização de Tema
description: Como personalizar o tema do seu aplicativo AEM Forms.
seo-description: Como personalizar o tema do seu aplicativo AEM Forms.
uuid: 36632e67-1cc6-416d-ae80-d84bbabab4bd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: c72f608e-052a-4bf9-b7bc-ddf57483af35
exl-id: fb1e0bec-c943-4468-920d-8ef360a01365
source-git-commit: 2208d23985ebd913b6aa9dee3bf16ce7529a8fa6
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Personalização de Tema {#theme-customization}

Você pode personalizar o código HTML e o arquivo CSS para fornecer uma aparência distinta e específica da organização ao aplicativo AEM Forms. Por exemplo, você pode alterar a cor e a altura do plano de fundo de tarefas ou pontos de partida. O exemplo a seguir fornece instruções para a alteração:

* instruções de exibição no lugar da descrição
* número de rotas de exibição
* cor do gradiente de fundo

## Etapas {#steps}

1. Abra o projeto.

   * Para iOS, abra `Capture.xcodeproj` no Xcode
   * Para Android, abra o projeto Android no Eclipse.
   * Para Windows, abra `MWSWindows.sln` no Visual Studio.

1. Navegue até a pasta de modelos.

   * No Xcode, navegue até a pasta **Capture > www > wsmobile > js > runtime > templates** .
   * No Eclipse, navegue até a pasta **assets > www > wsmobile > js > runtime > templates** .
   * No Visual Studio, navegue até a pasta **MWSWWindows > www > wsmobile > js > tempo de execução > templates** .

1. Abra o arquivo `template.html` para edição.
1. Localize a seguinte string:

   ```
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else 
   ```

   Substitua por `<%`.

1. Localize o seguinte código no arquivo `template.html`:

   ```
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. Comente a linha a seguir e salve o arquivo.

   ```
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. Navegue até a pasta css.

   * No Xcode, navegue até **Capture > www > wsmobile > css**.
   * No Eclipse, navegue até **assets > www > wsmobile > css**.
   * No Visual Studio, navegue até **MWSWWindows > www > wsmobile > css**.

1. Abra o arquivo `_style.css` para edição.
1. Para imagem de plano de fundo, altere `#323232` para `#fff`.
1. Salve as alterações e feche o arquivo `_style.css`.
1. Abra o aplicativo AEM Forms.

   O aplicativo AEM Forms agora exibe instruções em vez de descrição.
