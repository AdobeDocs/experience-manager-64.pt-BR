---
title: Configurar estrutura do site
seo-title: Setup Website Structure
description: Configurar diretórios
seo-description: Set up directories
uuid: a31edcd5-dab8-4a42-953b-1d076c2182b2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d18c0ece-4c4f-499c-ac94-a9aaa7f883c4
exl-id: 6d2226da-f691-4e8b-9494-a25e1c3d4b85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 2%

---

# Configurar estrutura do site {#setup-website-structure}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Para configurar seu site, as instruções abaixo descrevem as pastas a serem criadas nos seguintes locais:

* `/apps/an-scf-sandbox`
É aqui que residem os aplicativos e modelos personalizados

* `/etc/designs/an-scf-sandbox`
É aqui que residem os elementos de design baixáveis

* `/content/an-scf-sandbox`
É aqui que ficam as páginas da Web que podem ser baixadas

O código neste tutorial dependerá do nome da pasta principal ser o mesmo para o aplicativo, design e conteúdo. Se você escolher outro nome para o seu site, sempre substitua `an-scf-sandbox` com o nome que escolheu.

>[!NOTE]
>
>Sobre nomes:
>
>* Os nomes vistos no CRXDE são nomes de nós que formam o caminho para o conteúdo endereçável
>* Os nomes de nó podem conter espaços, mas quando usados em um URI, o espaço deve ser codificado como &#39;%20&#39; ou &#39;+&#39;
>* Os nomes de nó podem conter hifens e sublinhados, mas devem ser codificados quando referenciados como um nome de pacote em um arquivo Java. Os hifens e sublinhados são escapados com o sublinhado seguido pelo seu valor unicode:
   >
   >   * hífen torna-se &#39;_002d&#39;
   >   * underscore se torna &#39;_005f&#39;


## Configurar o Diretório de Aplicativos (/apps) {#setup-the-application-directory-apps}

O diretório /apps no repositório contém o código com implementa o comportamento e a renderização das páginas servidas do diretório /content.

O diretório /apps está protegido e não é acessível publicamente, como são os diretórios /content e /etc/designs.

1. Criar `/apps/an-scf-sandbox` pasta.

   Usando **[!UICONTROL CRXDE Lite]**, no painel explorador

   1. Selecione o `/apps` pasta
   1. Clique com o botão direito do mouse **[!UICONTROL Criar]**... ou puxe para baixo o **[!UICONTROL Criar...]** menu
   1. Selecionar **[!UICONTROL Criar Pasta...]** .
   1. No **[!UICONTROL Criar pasta]** , digite `an-scf-sandbox`
   1. Clique em **[!UICONTROL OK]**

1. Criar **[!UICONTROL componentes]** subpasta.

   1. Selecione o `/apps/an-scf-sandbox` pasta
   1. Clique em **[!UICONTROL Criar > Criar pasta]**
   1. No **[!UICONTROL Criar pasta]** , digite **[!UICONTROL componentes]**
   1. Clique em **[!UICONTROL OK]**

1. Criar **[!UICONTROL modelos]** subpasta.

   1. Selecione o `/apps/an-scf-sandbox` pasta
   1. Clique em **[!UICONTROL Criar > Criar pasta]**
   1. No **[!UICONTROL Criar pasta]** , digite **[!UICONTROL modelos]**
   1. Clique em **[!UICONTROL OK]**
   1. Selecionar novamente `/apps/an-scf-sandbox`
   1. Selecionar **[!UICONTROL Salvar tudo]**

   Como em qualquer processo de edição, salve com frequência. Se tiver problemas ao inserir dados, pode ser porque o tempo limite do seu logon foi excedido ou porque você precisa salvar as edições anteriores.

1. A estrutura no painel explorador do CRXDE Lite agora deve ser semelhante a esta:

   ![chlimage_1-44](assets/chlimage_1-44.png)

## Configurar o diretório de design (/etc/designs) {#setup-the-design-directory-etc-designs}

O diretório /etc/designs contém as imagens, scripts e folhas de estilos a serem baixadas junto com o conteúdo da página.

1. Para usar a ferramenta Designer na interface clássica, navegue até [https://&lt;server>:&lt;port>/miscadmin](http://localhost:4502/miscadmin).

   Observação: Se você usar o CRXDE Lite para criar um Nó do tipo `cq:Page`, o Controle de acesso e a Replicação não seriam definidos com as configurações padrão de uma página.

1. No painel do explorador, selecione o **[!UICONTROL Designs]** e clique em **[!UICONTROL Novo > Nova página]**.

   Insira:

   * Título: **Uma sandbox SCF**
   * Nome: **an-scf-sandbox**
   * Selecionar **Modelo da página de design**

   Clique em **[!UICONTROL Criar]**

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. Atualize o painel do explorador se a pasta &quot;An SCF Sandbox&quot; não for exibida.

1. Retorne ao CRXDE Lite (http:// localhost:4502/crx/de) e expanda /etc/designs para ver o nó chamado &quot;an-scf-sandbox&quot;.

   No painel inferior direito do CRXDE, é possível exibir a guia Propriedades, a guia Controle de acesso e a guia Replicação para ver o que foi definido usando o Modelo da página de design.

   ![chlimage_1-46](assets/chlimage_1-46.png)

## Configurar o Diretório de conteúdo (/content) {#setup-the-content-directory-content}

O diretório /content no repositório é onde o conteúdo do site reside. Os caminhos em /content compõem os caminhos do URL para solicitações do navegador.

*Depois* o [modelo de página](initial-app.md#createthepagetemplate) for criada como parte do aplicativo inicial, o conteúdo da página inicial poderá ser criado com base no template .... [**execute**](initial-app.md)
