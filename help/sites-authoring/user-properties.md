---
title: Configurar o ambiente da sua conta
seo-title: Configuring your account environment
description: O AEM fornece a capacidade de configurar a sua conta e determinados aspectos do ambiente de criação
seo-description: AEM provides you with the capability to configure your account and certain aspects of the author environment
uuid: 01e76771-9ac8-4919-9e50-0a63826177d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6afbc889-c613-40e6-8a25-1570dff32d60
exl-id: f620e85e-8c77-41a3-a238-9b93c819909d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 56%

---

# Configurar o ambiente da sua conta{#configuring-your-account-environment}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O AEM fornece a capacidade de configurar a sua conta e determinados aspectos do ambiente de criação.

Usar o [Usuário](/help/sites-authoring/user-properties.md#user-settings) na [header](/help/sites-authoring/basic-handling.md#the-header) e o [Minhas preferências](#my-preferences) , você pode modificar suas opções de usuário.

## Configurações de usuário {#user-settings}

O **Usuário** a caixa de diálogo configurações dá acesso a:

* Representar como

   * Com o [Representar como](/help/sites-administering/security.md#impersonating-another-user) um usuário pode trabalhar em nome de outro usuário.

* Perfil

   * Oferece um link conveniente para o [configurações do usuário](/help/sites-administering/security.md))

* [Minhas preferências](/help/sites-authoring/user-properties.md#my-preferences)

   * Especifique várias configurações de preferências exclusivas para seu usuário

![screen_shot_2018-03-20at103808](assets/screen_shot_2018-03-20at103808.png)

## Minhas preferências {#my-preferences}

A caixa de diálogo **Minhas preferências** é acessada através da opção [Usuário](/help/sites-authoring/user-properties.md#user-settings) no cabeçalho.

Cada usuário pode definir certas propriedades para si mesmo.

![screen_shot_2018-03-20at102118](assets/screen_shot_2018-03-20at102118.png)

* **Idioma**

   Isso define o idioma a ser usado para a interface do usuário do ambiente de criação. Selecione o idioma necessário na lista disponível.

   Essa configuração também é usada para a interface clássica.

* **Gerenciamento de janelas**

   Isso define o comportamento ou a abertura de janelas. Selecione um dos seguintes:

   * **Várias janelas** (Padrão)

      * As páginas serão abertas em uma nova janela.
   * **Uma janela**

      * As páginas serão abertas na janela atual.


* **Mostrar ações do desktop para Ativos**

   Essa opção requer o aplicativo de desktop do AEM para uso.

* **Cor da anotação**

   Isso define a cor padrão usada ao fazer anotações.

   * Clique no bloco de cores para abrir o seletor de amostras e selecionar uma cor.
   * Como alternativa, insira o código hexadecimal da cor desejada no campo.

* **Apresentação de data relativa**

   Para melhorar a legibilidade, o AEM renderizará datas nos últimos sete dias como datas relativas (por exemplo, três dias atrás) e datas mais antigas como datas exatas (por exemplo, 20 de março de 2017).

   Essa opção define como as datas no sistema são exibidas. As opções disponíveis são as seguintes:

   * **Sempre mostrar data exata**: a data exata é sempre exibida (nunca uma data relativa).
   * **1 dia**: a data relativa é mostrada para datas dentro de um dia; caso contrário, uma data exata é mostrada.
   * **7 dias (padrão)**: a data relativa é mostrada para datas dentro de sete dias; caso contrário, uma data exata é mostrada.
   * **1 mês**: a data relativa é mostrada para datas dentro de um mês; caso contrário, uma data exata é mostrada.
   * **1 ano**: a data relativa é mostrada para datas dentro de um ano; caso contrário, uma data exata é mostrada.
   * **Sempre mostrar data relativa**: as datas exatas nunca são mostradas, e apenas as datas relativas são mostradas.

* **Habilitar atalhos**

   O AEM oferece suporte a vários atalhos de teclado que tornam a criação mais eficiente.

   * [Atalhos de teclado para editar páginas](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
   * [Atalhos de teclado para os consoles](/help/sites-authoring/keyboard-shortcuts.md)

   Essa opção ativa atalhos do teclado. Por padrão, eles estão ativados, mas podem ser desativados, por exemplo, se um usuário tiver determinados requisitos de acessibilidade.

* **Usar a experiência de criação clássica**

   Essa opção ativa [interface clássica](/help/sites-classic-ui-authoring/home.md)Criação de página baseada em . Por padrão, a interface de usuário padrão é usada.

* **Ativar a Página inicial dos ativos**

   Essa opção só estará disponível se o administrador do sistema tiver ativado a experiência da Página inicial do Ativos para toda a organização.
