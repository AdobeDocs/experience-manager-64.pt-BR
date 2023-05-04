---
title: Criação de uma página para dispositivos móveis
seo-title: Authoring a Page for Mobile Devices
description: Ao criar uma página para dispositivos móveis, a página é exibida de uma maneira que emula o dispositivo móvel. Ao criar a página, você pode alternar entre vários emuladores para ver o que o usuário final vê ao acessar a página.
seo-description: When authoring a mobile page, the page is displayed in a way that emulates the mobile device. When authoring the page, you can switch between several emulators to see what the end-user sees when accessing the page.
uuid: ca16979d-6e5f-444d-b959-ae92542039b2
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 430a27b5-f344-404f-8bf8-0d91b49b605e
exl-id: 26324f89-f5e2-40bc-96b4-0f3faa08bdd1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 15%

---

# Criação de uma página para dispositivos móveis  {#authoring-a-page-for-mobile-devices}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Ao criar uma página para dispositivos móveis, a página é exibida de uma maneira que emula o dispositivo móvel. Ao criar a página, você pode alternar entre vários emuladores para ver o que o usuário final vê ao acessar a página.

Os dispositivos são agrupados nas categorias Recurso, Inteligente e Toque, de acordo com os recursos dos dispositivos para renderizar uma página. Quando o usuário final acessa uma página móvel, o AEM detecta o dispositivo e envia a representação que corresponde ao seu grupo de dispositivos.

>[!NOTE]
>
>Para criar um site móvel com base em um site padrão existente, crie uma live copy do site padrão. (Consulte [Criação de uma Live Copy para diferentes canais](/help/sites-administering/msm-livecopy.md).)
>
>Os desenvolvedores do AEM podem criar novos grupos de dispositivos. (Consulte [Criando Filtros de Grupo de Dispositivos.](/help/sites-developing/groupfilters.md))

Use o procedimento a seguir para criar uma página para dispositivos móveis:

1. No seu navegador, acesse **Siteadmin** console.
1. Abra o **Produtos** página abaixo **Sites** >> **Site de demonstração do Geometrixx Mobile** >> **Inglês**.

1. Alterne para um emulador diferente. Para fazer isso, é possível:

   * Clique no ícone do dispositivo na parte superior da página.
   * Clique no botão **Editar** no botão **Sidekick** e selecione o dispositivo no menu suspenso.

1. Arraste e solte a **Texto e imagem** componente da guia Móvel do Sidekick até a página.
1. Edite o componente e adicione texto. Clique em **OK** para salvar as alterações.

A página tem a mesma aparência que a seguinte:

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>Os emuladores são desativados quando uma página na instância de autor é solicitada em um dispositivo móvel. A criação pode ser feita usando a interface habilitada para toque.
