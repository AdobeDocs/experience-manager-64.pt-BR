---
title: Selecionar sua interface do usuário
seo-title: Selecting your UI
description: Configurar qual interface você usará para trabalhar no AEM
seo-description: Configure which interface you will use to work in AEM
uuid: af956219-178e-477b-a0cd-dd2341ed2ff0
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9cadec1b-f435-4fd8-b4bc-1a23a0cf11f3
exl-id: 415efbe0-95f5-4c9e-ac33-c4a384a8271e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 2%

---

# Selecionar sua interface do usuário{#selecting-your-ui}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Compreensão das interfaces do usuário

O ambiente de criação permite:

* [Criação](/help/sites-authoring/author.md) (incluindo [criação de página](/help/sites-authoring/author-environment-tools.md), [gerenciamento de ativos](/help/assets/home.md), [comunidades](/help/communities/author-communities.md))

* [Administração](/help/sites-administering/home.md) tarefas necessárias ao gerar e manter o conteúdo em seu site

Duas interfaces gráficas de usuário são fornecidas para isso. Elas podem ser acessadas por meio de qualquer navegador moderno.

1. Interface habilitada para toque

   * Esta é a interface de usuário de AEM padrão moderna.
   * É predominantemente cinza, com uma interface limpa e plana.
   * Projetada para uso em dispositivos de toque e desktop, a aparência é a mesma em todos os dispositivos, embora [visualizar e selecionar seus recursos](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) é ligeiramente diferente (toques versus cliques).

      * Desktop:

   ![screen_shot_2018-03-23at115248](assets/screen_shot_2018-03-23at115248.png)

   * Dispositivos tablet (ou desktop com menos de 1024 pixels de largura):

   ![screen_shot_2018-03-23at115505](assets/screen_shot_2018-03-23at115505.png)

1. IU Clássica

   * Essa é a interface do usuário herdada e está disponível no AEM por muitos anos.
   * É predominantemente verde.
   * Ele foi projetado para uso em dispositivos de desktop.
   * A documentação a seguir se concentra na interface do usuário moderna. Para obter informações sobre a criação na interface do usuário clássica, consulte o [Documentação de criação para a interface de usuário clássica](/help/sites-classic-ui-authoring/classicui.md).

   ![chlimage_1-232](assets/chlimage_1-232.png)

## Alternando interfaces do usuário

Embora a interface habilitada para toque agora seja a interface padrão e [paridade de recursos](../release-notes/touch-ui-features-status.md) tiver sido quase atingido com a administração e edição de sites, poderá haver momentos em que o usuário deseja alternar para a variável [interface clássica](/help/sites-classic-ui-authoring/classicui.md). Há várias opções para fazer isso.

>[!NOTE]
>
>Para obter detalhes sobre o status da paridade de recursos com a interface clássica, consulte o [Paridade de recursos da interface de toque](../release-notes/touch-ui-features-status.md) documento.

Há vários locais em que você pode definir qual interface do usuário deve ser usada:

* [Configuração da interface de usuário padrão para a sua instância](#configuring-the-default-ui-for-your-instance) - Isso definirá a interface padrão a ser exibida no logon do usuário, embora o usuário possa substituí-la e selecionar uma interface diferente para sua conta ou sessão atual.

* [Configuração da criação da interface clássica para sua conta](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account) - Isso definirá a interface de usuário a ser usada como padrão ao editar páginas, embora o usuário possa substituí-la e selecionar uma interface de usuário diferente para sua conta ou sessão atual.

* [Alternar para a interface clássica para a sessão atual](#switching-to-classic-ui-for-the-current-session) - Essa opção muda para a interface clássica na sessão atual.

* No caso de [criação de página o sistema faz certas substituições em relação à interface do usuário](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>Várias opções para alternar para a interface do usuário clássica não estão disponíveis imediatamente, elas devem ser configuradas especificamente para sua instância.
>
>Consulte [Ativar o acesso à interface clássica](/help/sites-administering/enable-classic-ui.md) para obter mais informações.

>[!NOTE]
>
>As instâncias atualizadas de uma versão anterior manterão a interface clássica para a criação de página.
>
>Após a atualização, a criação de página não será alternada automaticamente para a interface habilitada para toque, mas você pode configurá-la usando a variável [Configuração do OSGi](/help/sites-deploying/configuring-osgi.md) do **Serviço de Modo de Interface do Usuário de Criação de WCM** ( `AuthoringUIMode` serviço). Consulte [Substituições da interface do usuário para o Editor](#ui-overrides-for-the-editor).

## Configuração da interface de usuário padrão para sua instância {#configuring-the-default-ui-for-your-instance}

Um administrador do sistema pode configurar a interface do usuário vista na inicialização e logon usando [Mapeamento de raiz](/help/sites-deploying/osgi-configuration-settings.md).

Isso pode ser substituído pelos padrões do usuário ou pelas configurações da sessão.

## Configuração da criação da interface clássica para sua conta {#setting-classic-ui-authoring-for-your-account}

Cada usuário pode acessar seu [preferências do usuário](/help/sites-authoring/user-properties.md) para definir se deseja usar a interface clássica para criação de página (em vez da interface padrão).

Isso pode ser substituído pelas configurações da sessão.

## Alternar para a interface clássica para a sessão atual {#switching-to-classic-ui-for-the-current-session}

Ao usar a interface habilitada para toque, os usuários de desktop podem querer reverter para a interface clássica (somente desktop). Há vários métodos para alternar para a interface clássica na sessão atual:

* **Links de navegação**

   >[!CAUTION]
   >
   >Essa opção para alternar para a interface clássica não está disponível imediatamente, ela deve ser configurada especificamente para sua instância.
   >
   >
   >Consulte [Ativar o acesso à interface clássica](/help/sites-administering/enable-classic-ui.md) para obter mais informações.

   Se isso estiver ativado, sempre que você passar o mouse sobre um console aplicável, um ícone será exibido (símbolo de um monitor), tocar/clicar nele abrirá o local apropriado na interface clássica.

   Por exemplo, os links de **Sites** para **siteadmin**:

   ![screen_shot_2018-03-23at11924](assets/screen_shot_2018-03-23at111924.png)

* **URL**

   A interface clássica pode ser acessada usando o URL da tela de boas-vindas em `welcome.html`. Por exemplo:

   `http://localhost:4502/welcome.html`

   >[!NOTE]
   >
   >A interface habilitada para toque pode ser acessada via `sites.html`. Por exemplo:
   >
   >
   >`http://localhost:4502/sites.html`

### Alternar para a interface clássica ao editar uma página {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>Essa opção para alternar para a interface clássica não está disponível imediatamente, ela deve ser configurada especificamente para sua instância.
>
>Consulte [Ativar o acesso à interface clássica](/help/sites-administering/enable-classic-ui.md) para obter mais informações.

Se estiver ativado, **Abra a interface clássica** está disponível no **Informações da página** caixa de diálogo:

![chlimage_1-49](assets/chlimage_1-49.png)

### Substituições da interface do usuário para o Editor {#ui-overrides-for-the-editor}

As configurações definidas por um usuário ou administrador do sistema podem ser substituídas pelo sistema no caso de criação de página.

* Ao criar páginas:

   * O uso do editor clássico é forçado ao acessar a página usando `cf#` no URL. Por exemplo:

      `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * O uso do editor habilitado para toque é forçado ao usar `/editor.html` no URL ou ao usar um dispositivo de toque. Por exemplo:

      `http://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* Qualquer ação forçada é temporária e válida somente para a sessão do navegador

   * Um conjunto de cookies será definido dependendo se ativado para toque ( `editor.html`) ou clássica ( `cf#`) é usada.

* Ao abrir páginas por meio de `siteadmin`, serão efetuados controlos da existência de:

   * O cookie
   * Uma preferência de usuário
   * Se nenhum dos dois existir, o padrão será as definições feitas na variável [Configuração do OSGi](/help/sites-deploying/configuring-osgi.md) do **Serviço de Modo de Interface do Usuário de Criação de WCM** ( `AuthoringUIMode` serviço).

>[!NOTE]
>
>If [um usuário já definiu uma preferência para a criação de página](#setting-classic-ui-authoring-for-your-account), que não será substituído pela alteração da propriedade OSGi.

>[!CAUTION]
>
>Devido ao uso de cookies, conforme já descrito, nenhuma das ações abaixo é recomendável:
>
>* Editar manualmente o URL - Um URL não padrão pode resultar em uma situação desconhecida e em falta de funcionalidade.
>* Ter ambos os editores abertos ao mesmo tempo - Por exemplo, em janelas separadas.
>

