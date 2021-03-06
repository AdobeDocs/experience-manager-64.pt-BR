---
title: Conteúdo inicial do sandbox
seo-title: Conteúdo inicial do sandbox
description: Criar conteúdo
seo-description: Criar conteúdo
uuid: 9810fe47-8d1a-4238-9b9c-0cc47c63d97a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e8f28cd5-7950-4aab-bf62-3d4ed3d33cbd
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 5%

---


# Conteúdo inicial da caixa de proteção {#initial-sandbox-content}

Nesta seção, você cria as seguintes páginas que usam o [modelo de página](initial-app.md#createthepagetemplate):

* Site do SCF Sandbox, que redirecionará para a versão em inglês da página principal

   * SCF Sandbox - A página principal da versão em inglês do site

      * SCF Play - Filho da página principal na qual reproduzir

Embora este tutorial não seja disponibilizado em [cópias de idioma](../../help/sites-administering/tc-prep.md), ele foi projetado de modo que a página raiz possa implementar a detecção do idioma preferencial para o usuário por meio do cabeçalho HTML e redirecionar para a página principal apropriada para o idioma. A convenção é usar o código de país de duas letras para o nome do nó da página, por exemplo, &quot;en&quot; para inglês, &quot;fr&quot; para francês e assim por diante.

## Criar primeiras páginas {#create-first-pages}

Agora que há um [modelo de página](initial-app.md#createthepagetemplate), podemos estabelecer a página raiz do site no diretório /content.

1. A interface de usuário padrão atualmente fornece blueprints para a criação de sites. Como este tutorial está criando um site simples, a interface clássica é útil.

   Para alternar para a interface clássica, selecione navegação global e passe o mouse sobre o lado direito do ícone Projetos. Selecione o ícone *Alternar para a interface clássica* que é exibido:

   ![chlimage_1-36](assets/chlimage_1-36.png)

   A capacidade de alternar para a interface clássica deve ser [ativada por um administrador](../../help/sites-administering/enable-classic-ui.md).

1. Na [página de boas-vindas da interface clássica](http://localhost:4502/welcome.html), selecione **[!UICONTROL Sites]**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Como alternativa, acesse a interface clássica de sites diretamente navegando para [/siteadmin.](http://localhost:4502/siteadmin)

1. No painel explorador, selecione **[!UICONTROL Sites]** e, na barra de ferramentas, selecione **[!UICONTROL Novo > Nova página]**.

   Na caixa de diálogo **[!UICONTROL Criar página]**, digite o seguinte:

   * Título: `SCF Sandbox Site`
   * Nome: `an-scf-sandbox`
   * Selecione **[!UICONTROL Um modelo de reprodução em caixa de proteção SCF]**
   * Clique em **[!UICONTROL Criar]**

   ![chlimage_1-38](assets/chlimage_1-38.png)

1. No painel do explorador, selecione a página que você acabou de criar, `/Websites/SCF Sandbox Site`, e clique em **[!UICONTROL Nova > Nova página]**:

   * Título: `SCF Sandbox`
   * Nome: `en`
   * Selecione **Um modelo de reprodução em caixa de proteção SCF**
   * Clique em **Criar**

1. No painel do explorador, selecione a página que você acabou de criar, `/Websites/SCF Sandbox Site/SCF Sandbox`, e clique em **[!UICONTROL Nova > Nova página]**

   * Título: `SCF Play`
   * Nome: `play`
   * Selecione **[!UICONTROL Um modelo de reprodução em caixa de proteção SCF]**
   * Clique em **[!UICONTROL Criar]**

1. É assim que o site agora aparece no console Sites. Observe que as páginas secundárias do item selecionado no painel explorador são exibidas no painel direito, onde podem ser gerenciadas.

   ![chlimage_1-39](assets/chlimage_1-39.png)

   Esta é a visualização do repositório do que foi criado usando a ferramenta Site e o modelo:

   ![chlimage_1-40](assets/chlimage_1-40.png)

## Adicionar o caminho de design {#add-the-design-path}

Quando ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` foi criado usando a seção de designs do console Ferramentas, a propriedade &quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

foi definido, o que fornece a capacidade opcional de referenciar ativos de design em um script usando `currentDesign.getPath()`. Por exemplo

* &lt;>


   * Nome: `cq:designPath`
   * Tipo: `String`
   * Valor: `/etc/designs/an-scf-sandbox`

* Clique em verde `[+] Add`

O repositório deve ser exibido da seguinte forma:

![chlimage_1-41](assets/chlimage_1-41.png)

* Clique em **[!UICONTROL Salvar tudo]**

[ Problemas para salvar? Faça login novamente! ]

>[!NOTE]
>
>O uso de cq:designPath é opcional e não está relacionado ao [uso de clientlibs](develop-app.md#includeclientlibsintemplate), que são essencialmente necessários, pois os componentes do SCF usam [clientlibs](client-customize.md#clientlibs-for-scf) para gerenciar seus JS e CSS.

