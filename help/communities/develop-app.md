---
title: Desenvolver aplicativo de sandbox
seo-title: Develop Sandbox Application
description: Desenvolver aplicativo usando scripts de fundação
seo-description: Develop application using foundation scripts
uuid: 572f68cd-9ecb-4b43-a7f8-4aa8feb6c64e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 910229a3-38b1-44f1-9c09-55f8fd6cbb1d
exl-id: cd036e4a-0884-4ba0-83e9-7013583bbbae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 6%

---

# Desenvolver aplicativo de sandbox {#develop-sandbox-application}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Nesta seção, agora que o modelo foi configurado no [aplicação inicial](initial-app.md) e as páginas iniciais estabelecidas na seção [conteúdo inicial](initial-content.md) , o aplicativo pode ser desenvolvido usando scripts fundamentais, incluindo a capacidade de ativar a criação com componentes do Communities. No final desta seção, o site estará funcional.

## Uso de scripts de página de base {#using-foundation-page-scripts}

O script padrão, criado quando o componente que renderiza o modelo de página de reprodução foi adicionado, é modificado para incluir o head.jsp da página de base e um body.jsp local.

### Tipo de Recurso Super {#super-resource-type}

A primeira etapa é adicionar uma propriedade de supertipo de recurso à variável `/apps/an-scf-sandbox/components/playpage` para herdar os scripts e as propriedades do supertipo.

Uso do CRXDE Lite:

<!--Resolve steps below-->

* Nome: `sling:resourceSuperType`
* Tipo: `String`
* Valor: `foundation/components/page`

1. Clique na cor verde **[!UICONTROL [+] Adicionar]**
1. Clique em **[!UICONTROL Salvar tudo]**

![chlimage_1-231](assets/chlimage_1-231.png)

### Scripts de cabeçalho e corpo {#head-and-body-scripts}

1. Em **CRXDE Lite** painel do explorador, navegue até `/apps/an-scf-sandbox/components/playpage` e clique duas vezes no arquivo `playpage.jsp` para abri-lo no painel de edição.

#### /apps/an-scf-sandbox/components/playpage/playpage.jsp {#apps-an-scf-sandbox-components-playpage-playpage-jsp}

```xml
<%--

  An SCF Sandbox Play Component component.

  This is the component which renders content for An SCF Sandbox page.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" %><%
%><%
 // TODO add your code here
%>
```

1. Estando ciente de tags de script abertas/fechadas, substitua &quot; // TODO ...&quot; com inclusão de scripts para partes do cabeçalho e do corpo de &lt;html>.

   Com um super tipo de `foundation/components/page`, qualquer script não definido nessa mesma pasta resolverá para um script em `/apps/foundation/components/page` pasta (se existir), else para um script em `/libs/foundation/components/page` pasta.

#### /apps/an-scf-sandbox/components/playpage/playpage.jsp {#apps-an-scf-sandbox-components-playpage-playpage-jsp-1}

```xml
<%--

    An SCF Sandbox Play Component component: playpage.jsp

  This is the component which renders content for An SCF Sandbox page.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" %>
<html>
  <cq:include script="head.jsp"/>
  <cq:include script="body.jsp"/>
</html>
```

1. O script de base `head.jsp` não é necessário sobrepor, mas o script de base `body.jsp` está vazio.

   Para configurar a criação, sobreponha `body.jsp` com um script local e inclua um sistema de parágrafo (parsys) no corpo:

   1. navegue até `/apps/an-scf-sandbox/components`
   1. selecione o `playpage`nó
   1. clique com o botão direito do mouse e selecione `Create > Create File...`

      * Nome: **body.jsp**
   1. Clique em **[!UICONTROL Salvar tudo]**

   Abrir `/apps/an-scf-sandbox/components/playpage/body.jsp` e cole no seguinte texto:

   ```xml
   <%--
   
       An SCF Sandbox Play Component component: body.jsp
   
     This is the component which renders content for An SCF Sandbox page.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %>
   <body>
       <h2>Community Play</h2>
       <cq:include path="par" resourceType="foundation/components/parsys" />
   </body>
   ```

1. Clique em **[!UICONTROL Salvar tudo]**

**Exiba a página em um navegador no modo de edição:**

* Interface do usuário padrão: `http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html`

Você não deve apenas ver o cabeçalho **Reprodução da comunidade**, mas também a interface do usuário para editar o conteúdo da página.

O painel lateral Ativos/Componente é visto quando o painel lateral é aberto e a janela é larga o suficiente para o conteúdo lateral e o conteúdo da página a ser exibido.

![chlimage_1-232](assets/chlimage_1-232.png)

* IU Clássica: `http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html`

Veja a seguir como a página de reprodução aparece na interface clássica, incluindo o localizador de conteúdo (cf.):

![chlimage_1-233](assets/chlimage_1-233.png)

## Componentes das comunidades {#communities-components}

Para ativar os componentes do Communities para criação, comece seguindo estas instruções:

* [Acesso aos componentes das comunidades](basics.md#accessing-communities-components)

Para fins dessa sandbox, comece com **Comunidades** componentes (ativar marcando a caixa ):

* Comentários
* Fórum
* Avaliação
* Revisões
* Resumo das análises (exibir)
* Votação

Além disso, escolha **[!UICONTROL Geral]** componentes, como

* Imagem
* Tabela
* Texto
* Título (Foundation)

>[!NOTE]
>
>Os componentes habilitados para o par de páginas são armazenados no repositório como o valor da variável `components` da\
>`/etc/designs/an-scf-sandbox/jcr:content/playpage/par` nó .

## Página de aterrissagem {#landing-page}

Em um ambiente multilíngue, a página raiz incluiria um script que analisaria a solicitação do cliente para determinar o idioma preferencial.

Neste exemplo simples, a página raiz está sendo configurada estaticamente para redirecionar para a página em inglês, que pode ser desenvolvida no futuro para ser a página de aterrissagem principal com um link para a página de reprodução.

Altere o URL do navegador para a página raiz: `http://localhost:4502/editor.html/content/an-scf-sandbox.html`

* Selecione o ícone Informações da página
* Selecionar **[!UICONTROL Abrir propriedades]**
* Na guia AVANÇADO

   * Para a entrada Redirecionar, navegue até **[!UICONTROL Sites > Site de sandbox SCF > Sandbox SCF]**
   * Clique em **[!UICONTROL OK]**

* Clique em **[!UICONTROL OK]**

Depois que o site é publicado, navegar até a página raiz em uma instância de publicação redirecionará para a página em inglês.

A última etapa antes de reproduzir com os componentes do SCF de comunidades é adicionar uma Pasta da biblioteca do cliente (clientlibs) .... **[execute](add-clientlibs.md)**
