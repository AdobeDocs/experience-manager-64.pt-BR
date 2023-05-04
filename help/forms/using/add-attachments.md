---
title: Adição de anexos
seo-title: Adding attachments
description: Adicione fotografias e observações de rabisco como anotações à sua tarefa no aplicativo AEM Forms
seo-description: Add photographs and scribble notes as annotations to your task in the AEM Forms app
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
exl-id: ad1cc63a-cf99-456b-8b83-0605fb3ac6ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 1%

---

# Adição de anexos {#adding-attachments}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Adicionar anexos em formulários sincronizados com o servidor de fluxo de trabalho do AEM Forms (AEM Forms no JEE) {#adding-annotations}

O aplicativo AEM Forms permite anexar imagens, notas rabiscadas e notas de texto ao seu formulário sincronizado com o servidor AEM Forms JEE. Se o formulário for carregado a partir de um servidor de fluxo de trabalho do AEM Forms, os anexos serão adicionados ao formulário. Toque no botão anexo ![anexos-aplicativo](assets/attachments-app.png) para ver todos os anexos em um formulário juntos. A notificação vermelha especifica o número de anexos no formulário. Se não houver anexos no formulário, você não poderá ver o botão de notificações vermelhas. Se não houver anexos no formulário, ao tocar no botão anexos ![trava](assets/attch.png), você terá opções para anexar fotos ou scripts.

As opções são:

* **[!UICONTROL Galeria]**: Permite adicionar uma imagem das imagens salvas em seu dispositivo.

* **[!UICONTROL Câmera]**: Permite tirar uma imagem e adicioná-la ao formulário.

* **[!UICONTROL Notas]**: Permite adicionar um rabisco ou uma nota de texto. Use ![rabisco](assets/scribble.png) para adicionar um rabisco, e ![teclado](assets/keyboard.png) para adicionar uma nota de texto.

>[!NOTE]
>
>Os anexos adicionados por um usuário ficam visíveis para outros usuários do aplicativo AEM Forms. Outros usuários não podem excluir anexos adicionados por um usuário.

### A tela Anexos {#the-attachments-screen}

Para ver todos os anexos em um local, toque em ![anexos-aplicativo](assets/attachments-app.png). Você pode adicionar, renomear e excluir anexos aqui.

![Todos os anexos num local](assets/attachments-screen.png)

Você pode usar o **+** no ecrã Anexos para anexar outra imagem, rabisco ou texto.

### Adicionar uma fotografia {#adding-a-photograph}

Você pode usar a câmera de seu dispositivo móvel ou imagens salvas em seu dispositivo para anexar uma imagem no formulário.

1. Toque no botão de anexo ![trava](assets/attch.png) na parte inferior da janela.
1. Toque **[!UICONTROL Galeria]** ou **[!UICONTROL Câmera]** na janela pop-up exibida.
1. Com base na opção selecionada, execute o seguinte procedimento:

   1. Se você selecionar **[!UICONTROL Câmera]**.

      Tire uma foto. Em seguida, toque no **[!UICONTROL Use]** ![pic de uso](assets/use-pic.png) botão.

      Ou toque no **[!UICONTROL Retorne]** ![tentativa](assets/retake.png) botão para retomar a fotografia.

   1. Se você selecionar **[!UICONTROL Galeria]**.

      O navegador de imagens do dispositivo é exibido. No navegador de imagens do seu dispositivo, toque na imagem que deseja anexar.

### Adicionar uma observação {#adding-a-note}

O **Notas** A opção permite adicionar rabiscos à mão livre e anexos de texto no formulário.

1. Toque no botão de anexo ![trava](assets/attch.png) na parte inferior da janela.
1. Toque **[!UICONTROL Notas]** na janela pop-up exibida.
1. Na interface do usuário do Notes que é iniciada, capture um rabisco à mão livre.

   ![Interface de rabisco](assets/scribble-ui.png)
   **Figura:** *rabisco*

   Você pode usar as seguintes opções na interface do Scribble:

   * **[!UICONTROL Limpar]**: Apaga a tela.
   * **[!UICONTROL Concluído]**: Anexa o rabisco atual.
   * **[!UICONTROL Cancelar]**: Descarta o script atual e sai da interface do usuário do Scribble.
   * ![teclado](assets/keyboard.png): Apaga o rabisco e permite que você adicione uma nota de texto.

   ![Teclado no rabisco do aplicativo AEM Forms](assets/keyboard-inapp.png)

## Anexos em formulários sincronizados com os servidores da AEM Forms sem fluxo de trabalho do AEM Forms (AEM Forms no OSGi) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Os anexos de formulários móveis sincronizados com os servidores OSGi da AEM Forms funcionam de forma semelhante aos servidores AEM Forms JEE.

Os anexos no nível do formulário não são suportados em formulários adaptáveis carregados no aplicativo a partir de um servidor OSGi da AEM Forms. Para anexar imagens ou notas de texto, ative anexos em nível de campo no formulário ao criá-lo. Arraste e solte o componente de anexo de arquivo do navegador de componentes no campo .

No caso de formulários adaptáveis, é possível exibir os arquivos anexados no documento de registro (DoR). Consulte [Gerar Documento de Registro para formulários adaptáveis não XFA](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
