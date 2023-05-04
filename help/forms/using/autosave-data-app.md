---
title: Usar o salvamento automático no aplicativo AEM Forms
seo-title: Using autosave in AEM Forms app
description: Saiba como usar o recurso de salvamento automático no aplicativo AEM Forms que permite evitar perda de dados.
seo-description: Learn how to use autosave feature in AEM Forms app that lets you avoid data loss.
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
exl-id: 6eb00c31-6806-478a-99d1-55912798ea69
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 2%

---

# Usar o salvamento automático no aplicativo AEM Forms {#using-autosave-in-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Quando um usuário insere dados no aplicativo Adobe Experience Manager Forms, o recurso de salvamento automático os salva em intervalos regulares. O recurso de salvamento automático no aplicativo AEM Forms ajuda você a evitar perda de dados se o aplicativo for fechado acidentalmente.

Seu aplicativo pode fechar acidentalmente:

* Se o seu dispositivo desligar devido a pouca bateria
* Se o usuário matar o aplicativo
* Se ocorrer uma falha inesperada

Você pode especificar os intervalos após os quais o aplicativo salva os dados inseridos.

>[!NOTE]
>
>Selecione a frequência do salvamento automático criteriosamente. Operações frequentes de salvamento automático podem ter um impacto notório no desempenho do dispositivo.

Execute as seguintes etapas para usar o recurso de salvamento automático no aplicativo AEM Forms:

1. Faça logon no aplicativo e navegue até **[!UICONTROL Configurações > Geral]**.
1. Na tela Geral, use o **[!UICONTROL Frequência de Salvamento Automático]** para selecionar os intervalos em que deseja que o aplicativo salve os dados inseridos.
   [ ![Configuração da frequência de salvamento automático](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Ao reiniciar o aplicativo e fazer logon com o mesmo usuário, você é solicitado a restaurar a tarefa com a caixa de diálogo Recuperar tarefa não salva. Clique em **[!UICONTROL OK]** na caixa de diálogo Recuperar tarefa não salva para retomar o trabalho com a tarefa salva. Você pode clicar em **[!UICONTROL Cancelar]** para excluir os dados salvos correspondentes ao último salvamento automático acionado e começar a trabalhar com uma nova tarefa.

   Ao clicar em **[!UICONTROL OK]**, a tarefa é restaurada com os dados correspondentes ao salvamento automático mais recente acionado antes que o aplicativo travasse. Inclui os dados do formulário e todos os anexos associados à tarefa.
   [ ![Obter uma tarefa recuperada ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**A.** Um formulário de trabalho em andamento **B.** Aplicativo fechado à força **C.** O aplicativo foi reiniciado com a caixa de diálogo Recuperar tarefa não salva **D.** Formulário restaurado com dados originais
