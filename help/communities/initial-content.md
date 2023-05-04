---
title: Conteúdo inicial da sandbox
seo-title: Initial Sandbox Content
description: Criar conteúdo
seo-description: Create content
uuid: 9810fe47-8d1a-4238-9b9c-0cc47c63d97a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e8f28cd5-7950-4aab-bf62-3d4ed3d33cbd
exl-id: 171fd95d-51f6-468b-84ed-4a757dba868e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 5%

---

# Conteúdo inicial da sandbox {#initial-sandbox-content}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Nesta seção, você cria as seguintes páginas que usam o [modelo de página](initial-app.md#createthepagetemplate):

* Sites de sandbox SCF, que redirecionarão para a versão em inglês da página principal

   * Sandbox do SCF - A página principal da versão em inglês do site

      * Reprodução do SCF - Filho da página principal na qual reproduzir

Embora este tutorial não seja fornecido [cópias de idioma](../../help/sites-administering/tc-prep.md), ele foi projetado para que a página raiz possa implementar a detecção do idioma preferencial do usuário por meio do cabeçalho HTML e redirecionar para a página principal apropriada para o idioma. A convenção é usar o código de país de duas letras para o nome do nó da página, por exemplo, &quot;en&quot; para inglês, &quot;fr&quot; para francês e assim por diante.

## Criar primeiras páginas {#create-first-pages}

Agora que existe um [modelo de página](initial-app.md#createthepagetemplate), podemos estabelecer a página raiz do site no diretório /content.

1. A interface de usuário padrão atualmente fornece blueprints para a criação de sites. Como este tutorial está criando um site simples, a interface clássica é útil.

   Para alternar para a interface clássica, selecione navegação global e passe o mouse sobre o lado direito do ícone Projetos . Selecione o *Alternar para a interface clássica* ícone que aparece:

   ![chlimage_1-36](assets/chlimage_1-36.png)

   A capacidade de alternar para a interface clássica deve ser [habilitado por um administrador](../../help/sites-administering/enable-classic-ui.md).

1. No [página de boas-vindas da interface clássica](http://localhost:4502/welcome.html), selecione **[!UICONTROL Sites]**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Como alternativa, acesse a interface clássica de sites diretamente ao navegar para [/siteadmin.](http://localhost:4502/siteadmin)

1. No painel do explorador, selecione **[!UICONTROL Sites]** e, na barra de ferramentas, selecione **[!UICONTROL Novo > Nova página]**.

   No **[!UICONTROL Criar página]** digite o seguinte:

   * Título: `SCF Sandbox Site`
   * Nome: `an-scf-sandbox`
   * Selecionar **[!UICONTROL Um modelo de reprodução de sandbox SCF]**
   * Clique em **[!UICONTROL Criar]**

   ![chlimage_1-38](assets/chlimage_1-38.png)

1. No painel do explorador, selecione a página que você acabou de criar, `/Websites/SCF Sandbox Site`e clique em **[!UICONTROL Novo > Nova página]**:

   * Título: `SCF Sandbox`
   * Nome: `en`
   * Selecionar **Um modelo de reprodução de sandbox SCF**
   * Clique em **Criar**

1. No painel do explorador, selecione a página que você acabou de criar, `/Websites/SCF Sandbox Site/SCF Sandbox`e clique em **[!UICONTROL Novo > Nova página]**

   * Título: `SCF Play`
   * Nome: `play`
   * Selecionar **[!UICONTROL Um modelo de reprodução de sandbox SCF]**
   * Clique em **[!UICONTROL Criar]**

1. Agora é assim que o site aparece no console Sites. Observe que as páginas filhas do item selecionado no painel do explorador são exibidas no painel direito, onde podem ser gerenciadas.

   ![chlimage_1-39](assets/chlimage_1-39.png)

   Esta é a visualização do repositório do que foi criado usando a ferramenta Site e o modelo:

   ![chlimage_1-40](assets/chlimage_1-40.png)

## Adicionar o caminho de design {#add-the-design-path}

When ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` foi criada usando a seção designs do console Ferramentas , a propriedade &quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

foi definido, o que fornece a capacidade opcional de fazer referência aos ativos de design em um script usando `currentDesign.getPath()`. Por exemplo

* &lt;% String favorIcon = currentDesign.getPath() + &quot;/favicon.ico&quot;; %>


   * Nome: `cq:designPath`
   * Tipo: `String`
   * Valor: `/etc/designs/an-scf-sandbox`

* Clique na cor verde `[+] Add`

O repositório deve ser exibido da seguinte maneira:

![chlimage_1-41](assets/chlimage_1-41.png)

* Clique em **[!UICONTROL Salvar tudo]**

[ Problemas ao salvar? Faça logon novamente! ]

>[!NOTE]
>
>O uso de cq:designPath é opcional e não está relacionado a [uso de clientlibs](develop-app.md#includeclientlibsintemplate), que são essencialmente necessárias à medida que os componentes do quadro SEPA para os cartões utilizam [clientlibs](client-customize.md#clientlibs-for-scf) para gerenciar o JS e o CSS.
