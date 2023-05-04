---
title: Uso de CAPTCHA em formulários adaptáveis
seo-title: Using CAPTCHA in adaptive forms
description: Saiba como configurar AEM serviço CAPTCHA ou Google reCAPTCHA em formulários adaptáveis.
seo-description: Learn how to configure AEM CAPTCHA or Google reCAPTCHA service in adaptive forms.
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author, adaptive_forms
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
feature: Adaptive Forms
exl-id: 1129004b-5e8b-42fd-98ed-f203edde93b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 1%

---

# Uso de CAPTCHA em formulários adaptáveis {#using-captcha-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O CAPTCHA (Completamente Automated Public Turing test to tell Computers and Humans Além) é um programa comumente usado em transações online para distinguir entre humanos e programas ou bots automatizados. Ele coloca um desafio e avalia a resposta do usuário para determinar se é um humano ou um bot interagindo com o site. Impede que o usuário continue se o teste falhar e ajuda a tornar as transações online seguras, impedindo que bots postem spam ou fins mal-intencionados.

O AEM Forms suporta CAPTCHA em formulários adaptáveis. Você pode usar o serviço reCAPTCHA da Google para implementar CAPTCHA.

>[!NOTE]
>
>O AEM Forms suporta apenas o reCaptcha v2. Nenhuma outra versão é compatível.
>
>Não há suporte para CAPTCHA em formulários adaptáveis no modo offline no aplicativo AEM Forms.

## Configurar o serviço ReCAPTCHA pela Google {#google-recaptcha}

Os autores de formulários podem usar o serviço reCAPTCHA da Google para implementar CAPTCHA em formulários adaptáveis. Ele oferece recursos CAPTCHA avançados para proteger seu site. Para obter mais informações sobre como o reCAPTCHA funciona, consulte [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![recaptcha](assets/recaptcha.png)

Para implementar o serviço reCAPTCHA no AEM Forms:

1. Obter [par de chaves da API reCAPTCHA](https://www.google.com/recaptcha/admin) do Google. Inclui uma chave do site e um segredo.
1. Criar contêiner de configuração para serviços em nuvem.

   1. Ir para **[!UICONTROL Ferramentas > Geral > Navegador de configuração]**.
      * Consulte a [Documentação do Navegador de configuração](/help/sites-administering/configurations.md) para obter mais informações.
   1. Faça o seguinte para habilitar a pasta global para configurações de nuvem ou ignore esta etapa para criar e configurar outra pasta para configurações do serviço de nuvem.

      1. No Navegador de configuração, selecione o **[!UICONTROL global]** pasta e toque **[!UICONTROL Propriedades]**.
      1. Na caixa de diálogo Propriedades de configuração, ative **[!UICONTROL Configurações da nuvem]**.
      1. Toque **[!UICONTROL Salvar e fechar]** para salvar a configuração e sair da caixa de diálogo.
   1. No Navegador de configuração, toque em **[!UICONTROL Criar]**.
   1. Na caixa de diálogo Criar configuração, especifique um título para a pasta e habilite **[!UICONTROL Configurações da nuvem]**.
   1. Toque **[!UICONTROL Criar]** para criar a pasta habilitada para as configurações do serviço de nuvem.


1. Configure o serviço de nuvem para reCAPTCHA.

   1. Na instância do autor do AEM, acesse ![ferramentas](assets/tools.png) >  **Cloud Services**.
   1. Toque **[!UICONTROL reCAPTCHA]**. A página Configurações é aberta. Selecione o contêiner de configuração criado na etapa anterior e toque em **[!UICONTROL Criar]**.
   1. Especifique o nome, a chave do site e a chave secreta para o serviço reCAPTCHA e toque em **[!UICONTROL Criar]** para criar a configuração do serviço de nuvem.
   1. Na caixa de diálogo Editar componente , especifique o site e as chaves secretas obtidas na etapa 1. Toque **[!UICONTROL Salvar configurações]** em seguida, toque em **[!UICONTROL OK]** para concluir a configuração.

   Quando o serviço reCAPTCHA é configurado, ele está disponível para uso em formulários adaptáveis. Para obter mais informações, consulte [Uso de CAPTCHA em formulários adaptáveis](#using-captcha).

## Usar CAPTCHA em formulários adaptáveis {#using-captcha}

Para usar CAPTCHA em formulários adaptáveis:

1. Abra um formulário adaptável no modo de edição.

   >[!NOTE]
   >
   >Verifique se o contêiner de configuração selecionado ao criar o formulário adaptável contém o serviço de nuvem reCAPTCHA. Também é possível editar as propriedades adaptáveis do formulário para alterar o contêiner de configuração associado ao formulário.

1. No navegador de componentes, arraste e solte a **[!UICONTROL Captcha]** no formulário adaptável.

   >[!NOTE]
   >
   >Não é possível usar mais de um componente Captcha em um formulário adaptável. Além disso, não é recomendado usar CAPTCHA em um painel marcado para carregamento lento ou em um fragmento.

   >[!NOTE]
   >
   >O Captcha diferencia tempo e expira em cerca de um minuto. Portanto, é recomendável colocar o componente Captcha logo antes do botão Enviar no formulário adaptável.

1. Selecione o componente Captcha adicionado e toque ![cmppr](assets/cmppr.png) para editar suas propriedades.
1. Especifique um título para o widget CAPTCHA. O valor padrão é **Captcha**. Selecionar **[!UICONTROL Ocultar título]** se não quiser que o título apareça.
1. No **[!UICONTROL Serviço Captcha]** , selecione **[!UICONTROL reCaptcha]** para ativar o serviço reCAPTCHA, se você o tiver configurado conforme descrito em [Serviço ReCAPTCHA da Google](#google-recaptcha). Selecione uma configuração no menu suspenso Configurações . Além disso, selecione o tamanho como **[!UICONTROL Normal]** ou **[!UICONTROL Compacto]** para o widget reCAPTCHA.

   >[!NOTE]
   >
   >Não selecionar **[!UICONTROL Padrão]** no menu suspenso do serviço Captcha como o serviço AEM CAPTCHA padrão está obsoleto.

1. Salve as propriedades.

O serviço reCAPTCHA está ativado no formulário adaptável. Você pode visualizar o formulário e ver o CAPTCHA funcionando.
