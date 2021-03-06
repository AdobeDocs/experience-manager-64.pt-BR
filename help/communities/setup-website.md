---
title: Configurar estrutura do site
seo-title: Configurar estrutura do site
description: Configurar diretórios
seo-description: Configurar diretórios
uuid: a31edcd5-dab8-4a42-953b-1d076c2182b2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d18c0ece-4c4f-499c-ac94-a9aaa7f883c4
translation-type: tm+mt
source-git-commit: bd2eb8787a98fa9910cc540ba329466a0e72e0db
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 1%

---


# Configurar estrutura do site {#setup-website-structure}

Para configurar seu site, as instruções abaixo descrevem as pastas a serem criadas nos seguintes locais:

* `/apps/an-scf-sandbox`
É aqui que residem os aplicativos e modelos personalizados

* `/etc/designs/an-scf-sandbox`
Este é o local onde os elementos de design disponíveis para download residem

* `/content/an-scf-sandbox`
Este é o local onde as páginas da Web disponíveis para download residem

O código neste tutorial dependerá do nome da pasta principal ser o mesmo para o aplicativo, design e conteúdo. Se você escolher outro nome para seu site, substitua sempre `an-scf-sandbox` pelo nome que você escolheu.

>[!NOTE]
>
>Sobre nomes:
>
>* Os nomes vistos no CRXDE são nomes de nós que formam o caminho para o conteúdo endereçável
>* Nomes de nó podem conter espaços, mas quando usados em um URI, o espaço deve ser codificado como &#39;%20&#39; ou &#39;+&#39;
>* Os nomes de nó podem conter hifens e sublinhados, mas devem ser codificados quando referenciados como um nome de pacote dentro de um arquivo Java. Os hífens e os sublinhados são escapados com o sublinhado seguido pelo valor unicode:

   >
   >   
   * hífen torna-se &#39;_002d&#39;
   >   * underscore torna-se &#39;_005f&#39;


## Configurar o Diretório de Aplicativos (/apps) {#setup-the-application-directory-apps}

O diretório /apps no repositório contém o código com implementa o comportamento e a renderização das páginas fornecidas do diretório /content.

O diretório /apps está protegido e não é acessível publicamente, como são os diretórios /content e /etc/designs.

1. Crie a pasta `/apps/an-scf-sandbox`.

   Usando **[!UICONTROL CRXDE Lite]**, no painel do explorador

   1. Selecione a pasta `/apps`
   1. Clique com o botão direito do mouse em **[!UICONTROL Criar]**... ou puxe para baixo **[!UICONTROL Criar...Menu]**
   1. Selecione **[!UICONTROL Criar pasta...]** .
   1. Na caixa de diálogo **[!UICONTROL Criar pasta]**, digite `an-scf-sandbox`
   1. Clique em **[!UICONTROL OK]**

1. Crie a subpasta **[!UICONTROL components]**.

   1. Selecione a pasta `/apps/an-scf-sandbox`
   1. Clique em **[!UICONTROL Criar > Criar pasta]**
   1. Na caixa de diálogo **[!UICONTROL Criar pasta]**, digite **[!UICONTROL componentes]**
   1. Clique em **[!UICONTROL OK]**

1. Crie a subpasta **[!UICONTROL modelos]**.

   1. Selecione a pasta `/apps/an-scf-sandbox`
   1. Clique em **[!UICONTROL Criar > Criar pasta]**
   1. Na caixa de diálogo **[!UICONTROL Criar pasta]**, digite **[!UICONTROL modelos]**
   1. Clique em **[!UICONTROL OK]**
   1. Reselecione `/apps/an-scf-sandbox`
   1. Selecione **[!UICONTROL Salvar tudo]**

   Como em qualquer processo de edição, salve com frequência. Se você encontrar problemas com a inserção de dados, isso pode ocorrer porque seu login expirou ou você precisa salvar as edições anteriores.

1. A estrutura no painel explorador de CRXDE Lite deve ser parecida com isto:

   ![chlimage_1-44](assets/chlimage_1-44.png)

## Configurar o diretório de design (/etc/designs) {#setup-the-design-directory-etc-designs}

O diretório /etc/designs contém as imagens, scripts e folhas de estilo que serão baixadas juntamente com o conteúdo da página.

1. Para usar a ferramenta Designer na interface clássica, navegue até [https://&lt;server>:&lt;port>/miscadmin](http://localhost:4502/miscadmin).

   Observação: Se você usar CRXDE Lite para criar um Nó do tipo `cq:Page`, o Controle de acesso e a Replicação não serão definidos com as configurações padrão de uma página.

1. No painel explorador, selecione a pasta **[!UICONTROL Designs]** e clique em **[!UICONTROL Novo > Nova página]**.

   Digite:

   * Título: **Uma caixa de proteção SCF**
   * Nome: **an-scf-sandbox**
   * Selecione **Modelo de Página de Design**

   Clique em **[!UICONTROL Criar]**

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. Atualize o painel do explorador se a pasta &quot;Uma caixa de proteção SCF&quot; não for exibida.

1. Retorne ao CRXDE Lite (http:// localhost:4502/crx/de) e expanda /etc/designs para ver o nó chamado &quot;an-scf-sandbox&quot;.

   No painel inferior direito do CRXDE, você pode visualização a guia Propriedades, a guia Controle de acesso e a guia Replicação para ver o que foi definido usando o Modelo da página de design.

   ![chlimage_1-46](assets/chlimage_1-46.png)

## Configurar o Diretório de conteúdo (/content) {#setup-the-content-directory-content}

O diretório /content no repositório é onde o conteúdo do site reside. Os caminhos em /content compreendem os caminhos do URL para as solicitações do navegador.

*Depois* que os modelos de  [página ](initial-app.md#createthepagetemplate) forem criados como parte do aplicativo inicial, o conteúdo da página inicial poderá ser criado com base no modelo....  [**execute**](initial-app.md)
