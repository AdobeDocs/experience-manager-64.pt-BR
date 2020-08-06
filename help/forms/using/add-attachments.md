---
title: Adicionar anexos
seo-title: Adicionar anexos
description: Adicione fotografias e notas de script como anotações à sua tarefa no aplicativo AEM Forms
seo-description: Adicione fotografias e notas de script como anotações à sua tarefa no aplicativo AEM Forms
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
translation-type: tm+mt
source-git-commit: 0ce79686522da4fb3d017068b623c76f81c6b23a
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# Adicionar anexos {#adding-attachments}

## Adicionar anexos em formulários sincronizados com o servidor do AEM Forms Workflow (AEM Forms em JEE) {#adding-annotations}

O aplicativo AEM Forms permite anexar imagens, anotações com script e notas de texto ao formulário sincronizado com o servidor AEM Forms JEE. Se o formulário for carregado de um servidor do AEM Forms Workflow, os anexos serão adicionados ao formulário. Você pode tocar no botão de anexo ![anexos-aplicativo](assets/attachments-app.png) para ver todos os anexos em um formulário juntos. A notificação vermelha especifica o número de anexos no formulário. Se não houver anexos no formulário, você não poderá ver o botão de notificações vermelhas. Se não houver anexos no formulário, quando você tocar no botão de anexos ![anexar](assets/attch.png), você obterá opções para anexar fotos ou scripts.

Suas opções são:

* **[!UICONTROL Galeria]**: Permite que você adicione uma imagem das imagens salvas no seu dispositivo.

* **[!UICONTROL Câmera]**: Permite tirar uma foto e adicioná-la ao formulário.

* **[!UICONTROL Notas]**: Permite adicionar um script ou uma nota de texto. Use o ![scribble](assets/scribble.png) para adicionar um scribble e o ![teclado](assets/keyboard.png) para adicionar uma nota de texto.

>[!NOTE]
>
>Os anexos adicionados por um usuário estão visíveis para outros usuários do aplicativo AEM Forms. Outros usuários não podem excluir anexos adicionados por um usuário.


### A tela Anexos {#the-attachments-screen}

Para ver todos os anexos em um lugar, toque em ![anexos-aplicativo](assets/attachments-app.png). Você pode adicionar, renomear e excluir anexos aqui.

![Todos os anexos em um local](assets/attachments-screen.png)

Você pode usar o botão **+** na tela Anexos para anexar outra imagem, um script ou um texto.

### Adicionar uma fotografia {#adding-a-photograph}

Você pode usar a câmera do seu dispositivo móvel ou imagens salvas no seu dispositivo para anexar uma foto no formulário.

1. Toque no botão de anexo ![se encaixe](assets/attch.png) na parte inferior da janela.
1. Toque em **[!UICONTROL Galeria]** ou **[!UICONTROL Câmera]** no pop-up exibido.
1. Com base na opção selecionada, execute o seguinte procedimento:

   1. Se você selecionar **[!UICONTROL Câmera]**.

      Tire uma foto. Em seguida, toque no botão **[!UICONTROL Use]** ![use-pic](assets/use-pic.png) .

      Ou toque no botão **[!UICONTROL Retake]** ![retake](assets/retake.png) (Retirar) para refazer a fotografia.

   1. Se você selecionar **[!UICONTROL Galeria]**.

      O navegador de imagem do dispositivo é exibido. No navegador de imagens do seu dispositivo, toque na imagem que deseja anexar.

### Adicionar uma observação {#adding-a-note}

A opção **Anotações** permite adicionar rabiscos à mão livre e anexos de texto no formulário.

1. Toque no botão de anexo ![se encaixe](assets/attch.png) na parte inferior da janela.
1. Toque em **[!UICONTROL Notas]** no pop-up exibido.
1. Na interface do usuário do Notes que é iniciada, capture um script à mão livre.

   ![Interface do script](assets/scribble-ui.png)
   **Figura:** *Rabisco*

   Você pode usar as seguintes opções na interface do Scribble:

   * **[!UICONTROL Limpar]**: Limpa a tela.
   * **[!UICONTROL Feito]**: Anexa o script atual.
   * **[!UICONTROL Cancelar]**: Descarta o script atual e sai da interface do usuário do Scribble.
   * ![teclado](assets/keyboard.png): Limpa o rabisco e permite que você adicione uma nota de texto.

   ![Teclado no script do aplicativo AEM Forms](assets/keyboard-inapp.png)

## Anexos em formulários sincronizados com os servidores AEM Forms sem o AEM Forms Workflow (AEM Forms no OSGi) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Os anexos para formulários móveis sincronizados com os servidores OSGi da AEM Forms funcionam de forma semelhante aos servidores AEM Forms JEE.

Os anexos de nível de formulário não são suportados para formulários adaptáveis carregados no aplicativo a partir de um servidor OSGi da AEM Forms. Para anexar imagens ou notas de texto, ative os anexos de nível de campo no formulário ao criá-lo. Arraste e solte o componente de anexo de arquivo do navegador de componentes no campo.

No caso de formulários adaptáveis, você pode visualização os arquivos anexados no documento de registro (DoR). Consulte [Gerar Documento de registro para formulários](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)adaptáveis não XFA.
