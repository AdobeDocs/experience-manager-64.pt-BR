---
title: Adicionar ação personalizada à exibição de Listagem de ativos
seo-title: Add custom action to the Asset Listing view
description: Este artigo ensina como adicionar ação personalizada à exibição de Listagem de ativos
seo-description: This article teaches how to add custom action to the Asset Listing view
uuid: 72ce6c24-2758-4888-b797-1b134acc54d2
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: b35ea921-182f-4371-90f6-482d22694b42
feature: Correspondence Management
exl-id: 00b3efc5-ef1c-4b9d-957d-2eda01c0b985
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1396'
ht-degree: 3%

---

# Adicionar ação personalizada à exibição de Listagem de ativos {#add-custom-action-to-the-asset-listing-view}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

A solução Gerenciamento de correspondência permite adicionar ações personalizadas à interface do usuário Gerenciar ativos .

Você pode adicionar uma ação personalizada à exibição de Listagem de ativos para:

* Um ou mais tipos de ativos ou letras
* Execução (ação/comando torna-se ativo) na seleção de ativos/letras únicos ou diversos, ou sem seleção

Essa personalização é demonstrada com o cenário que adiciona um comando &quot;Baixar PDF simples&quot; à exibição de Lista de ativos para cartas. Esse cenário de personalização permite que os usuários baixem PDF simples de uma única carta selecionada.

### Pré-requisitos {#prerequisites}

Para concluir o seguinte cenário ou semelhante, você precisa de conhecimento de:

* CRX
* JavaScript
* Java

## Cenário: Adicione um comando à interface do usuário da lista de letras para baixar a versão de PDF simples de uma letra {#addcommandtoletters}

As etapas abaixo adicionam um comando &quot;Baixar PDF simples&quot; à exibição Lista de ativos para Cartas e permitem que os usuários baixem o PDF simples da carta selecionada. Usando essas etapas com o código e os parâmetros apropriados, é possível adicionar alguma outra funcionalidade a um ativo diferente, como dicionários de dados ou textos.

Para personalizar o Gerenciamento de correspondência para permitir que os usuários baixem um PDF de cartas simples, execute as seguintes etapas:

1. Ir para `https://[server]:[port]/[ContextPath]/crx/de` e faça logon como Administrador.

1. Na pasta apps , crie uma pasta nomeada items com caminho/estrutura semelhante à pasta items localizada na pasta de seleção usando as seguintes etapas:

   1. Clique com o botão direito do mouse no **[!UICONTROL items]** no caminho a seguir e selecione **[!UICONTROL Nó de sobreposição]**:

      `/libs/fd/cm/ma/gui/content/cmassets/jcr:content/body/content/header/items/selection/items`

      >[!NOTE]
      >
      >Esse caminho é específico para criar uma ação que funcione com a seleção de um ou mais ativos/letras. Se você quiser criar uma ação que funcione sem a seleção, será necessário criar um nó de sobreposição para o seguinte caminho e concluir as etapas restantes adequadamente:
      >
      >
      >`/libs/fd/cm/ma/gui/content/cmassets/jcr:content/body/content/header/items/default/items`

      ![Criar nó](assets/1_itemscreatenode.png)

   1. Certifique-se de que a caixa de diálogo Sobrepor nó tenha os seguintes valores:

      **[!UICONTROL Caminho:]** /libs/fd/cm/ma/gui/content/cmassets/jcr:content/body/content/header/items/selection/items

      **[!UICONTROL Localização:]** /apps/

      **[!UICONTROL Corresponder tipos de nó:]** Selecionado

      ![Nó de sobreposição](assets/2_createnodedownloadflatpdf.png)

   1. Clique em **[!UICONTROL OK]**. A estrutura de pastas é criada na pasta de aplicativos.

      Clique em **[!UICONTROL Salvar tudo]**.

1. Na pasta de itens recém-criados, adicione um nó para o botão/ação personalizada em um ativo específico (Exemplo: downloadFlatPDF) usando as seguintes etapas:

   1. Clique com o botão direito do mouse no **[!UICONTROL items]** e selecione **[!UICONTROL Criar]** > **[!UICONTROL Criar nó]**.

   1. Certifique-se de que a caixa de diálogo Criar nó tenha os seguintes valores e clique em **[!UICONTROL OK]**:

      **[!UICONTROL Nome:]** downloadFlatPDF (ou o nome que deseja dar a essa propriedade)

      **[!UICONTROL Tipo:]** nt:unstructured

   1. Clique no novo nó que você criou (aqui downloadFlatPDF). O CRX exibe as propriedades do nó.
   1. Adicione as seguintes propriedades ao nó (aqui downloadFlatPDF) e clique em **[!UICONTROL Salvar tudo]**:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Nome</strong></td> 
    <td><strong>Tipo</strong></td> 
    <td><strong>Valor e descrição</strong></td> 
    </tr> 
    <tr> 
    <td>Classe </td> 
    <td>String</td> 
    <td>foundation-collection-action</td> 
    </tr> 
    <tr> 
    <td>foundation-collection-action</td> 
    <td>String</td> 
    <td><p>{"target": ".cq-manageasset-admin-children", "ativeSelectionCount": "single", "type": "LETRA"}<br /> <br /> <br /> <strong>ativeSelectionCount</strong> pode ser única ou múltipla para permitir seleções de um ou vários ativos nos quais a ação personalizada é executada.</p> <p><strong>type</strong> pode ser uma ou mais (vírgulas separadas por várias entradas) das seguintes opções: LETRA,TEXTO,LISTA,CONDIÇÃO,DATADICIONÁRIO</p> </td> 
    </tr> 
    <tr> 
    <td>ícone</td> 
    <td>String</td> 
    <td>icon-download<br /> <br /> O ícone que o Gerenciamento de correspondência exibe no lado esquerdo do seu comando/menu. Para obter diferentes ícones e configurações disponíveis, consulte <a href="https://docs.adobe.com/docs/en/aem/6-3/develop/ref/coral-ui/coralui3/Coral.Icon.html" target="_blank">Documentação de Ícones do CoralUI</a>.<br /> </td> 
    </tr> 
    <tr> 
    <td>jcr:primaryType</td> 
    <td>Nome</td> 
    <td>nt:unstructured</td> 
    </tr> 
    <tr> 
    <td>rel</td> 
    <td>String</td> 
    <td>botão download-simples-pdf</td> 
    </tr> 
    <tr> 
    <td>sling:resourceType</td> 
    <td>String</td> 
    <td>granite/ui/components/endor/actionbar/button</td> 
    </tr> 
    <tr> 
    <td>text</td> 
    <td>String</td> 
    <td>Baixe o Flat PDF (ou qualquer outra etiqueta)<br /> <br /> O comando que aparece na interface da Listagem de ativos</td> 
    </tr> 
    <tr> 
    <td>título</td> 
    <td>String</td> 
    <td>Baixar uma PDF simples da letra selecionada (ou qualquer outro rótulo/texto alternativo)<br /> <br /> O título é o texto alternativo que o Gerenciamento de correspondência exibe quando o usuário passa o mouse sobre o comando personalizado.</td> 
    </tr> 
    </tbody> 
    </table>

1. Na pasta apps , crie uma pasta chamada js com caminho/estrutura semelhante à pasta de itens localizada na pasta admin usando as seguintes etapas:

   1. Clique com o botão direito do mouse no **[!UICONTROL js]** no caminho a seguir e selecione **[!UICONTROL Nó de sobreposição]**: &quot;

      `/libs/fd/cm/ma/gui/components/admin/clientlibs/admin/js`

   1. Certifique-se de que a caixa de diálogo Sobrepor nó tenha os seguintes valores:

      **[!UICONTROL Caminho:]** /libs/fd/cm/ma/gui/components/admin/clientlibs/admin/js

      **[!UICONTROL Localização:]** /apps/

      **[!UICONTROL Corresponder tipos de nó:]** Selecionado

   1. Clique em **[!UICONTROL OK]**. A estrutura de pastas é criada na pasta de aplicativos. Clique em **[!UICONTROL Salvar tudo]**.

1. Na pasta js , crie um arquivo chamado formaction.js com o código para a manipulação de ação do botão usando as seguintes etapas:

   1. Clique com o botão direito do mouse no **[!UICONTROL js]** no caminho a seguir e selecione **[!UICONTROL Criar > Criar arquivo]**:

      `/apps/fd/cm/ma/gui/components/admin/clientlibs/admin/js`

      Nomeie o arquivo como formaction.js.

   1. Clique duas vezes no arquivo para abri-lo no CRX.
   1. No arquivo formaction.js (na ramificação /apps), copie o código do arquivo formaction.js no seguinte local:

      `/libs/fd/cm/ma/gui/components/admin/clientlibs/admin/js/formaction.js`

      Em seguida, anexe o seguinte código no final do arquivo formaction.js (na ramificação /apps) e clique em **[!UICONTROL Salvar tudo]**:

      ```
      /* Action url for xml file to be added.*/
      var ACTION_URL = "/apps/fd/cm/ma/gui/content/commons/actionhandlers/items/letterpdfdownloader.html";
      
      /* File upload handling*/
      var fileSelectedHandler = function(e){
          if(e && e.target && e.target.value)
              $(".downloadLetterPDFBtn").removeAttr('disabled');
          else
              $(".downloadLetterPDFBtn").attr('disabled','disabled');
      }
      
      /*Handing of Download button in pop up.*/
      var downloadClickHandler = function(){
          $('#downloadLetterPDFDilaog').modal("hide");
          var element = $('.foundation-selections-item');
          var path = $(element).data("path");
          $("#fileUploadForm").attr('action', ACTION_URL + "?letterId="+path).submit();
      }
      
      /*Click handling on action button.*/
      $(document).on("click",'.download-flat-pdf-button',function(e){
          $("#uploadSamepledata").val("");
           if($('#downloadLetterPDFDilaog').length == 0){
              $(document).on("click",".downloadLetterPDFBtn",downloadClickHandler);
              $(document).on("change","#uploadSamepledata",fileSelectedHandler);
              $("body").append(downloadLetterPDFDilaog);
          }
            $('#downloadLetterPDFDilaog').modal("show");
      });
      
      /*Download popup.*/
      var downloadLetterPDFDilaog = '<div id="downloadLetterPDFDilaog" class="coral-Modal notice " role="dialog"  aria-hidden="true">'+
          '<form id="fileUploadForm" method="POST" enctype="multipart/form-data">'+
              '<div class="coral-Modal-header">'+
                  '<h2 class="coral-Modal-title coral-Heading coral-Heading--2" id="modal-header1443020790107-label" tabindex="0">Download Letter as PDF.</h2>'+
                  '<button type="button" class="coral-MinimalButton coral-Modal-closeButton" data-dismiss="modal">×</button>'+
              '</div>'+
              '<div class="coral-Modal-body" id="modal-header1443020790107-message" role="document" tabindex="0">'+
                  '<div class="coral-Modal-message">'+
                      '<p></p>'+
                  '</div>'+
                  '<div class="coral-Modal-uploader">'+
                      '<p>Select sample data for letter.</p>'+
                      '<input type="file" id="uploadSamepledata" name="file" accept=".xml" size="70px">'+
                  '</div>'+
              '</div>'+
           '</form>'+
              '<div class="coral-Modal-footer">'+
                  '<button type="button" class="coral-Button" data-dismiss="modal">Cancel</button>'+
                  '<button type="button" class="coral-Button coral-Button--primary downloadLetterPDFBtn" disabled="disabled">Download</button>'+
              '</div>'+
      '</div>';
      ```

      O código adicionado nesta etapa substitui o código na pasta libs, portanto, copie o código anterior para o arquivo formaction.js na ramificação /apps. Copiar o código da ramificação /libs para a ramificação /apps garante que a funcionalidade anterior também funcione.

      O código acima é para a ação específica de letras do comando criado neste procedimento. Para o tratamento de ações de outros ativos, modifique o código JavaScript.

1. Na pasta apps , crie uma pasta nomeada items com caminho/estrutura semelhante à pasta items localizada na pasta actionhandlers usando as seguintes etapas:

   1. Clique com o botão direito do mouse no **[!UICONTROL items]** no caminho a seguir e selecione **[!UICONTROL Nó de sobreposição]**:

      `/libs/fd/cm/ma/gui/content/commons/actionhandlers/items/`

   1. Certifique-se de que a caixa de diálogo Sobrepor nó tenha os seguintes valores:

      **[!UICONTROL Caminho:]** /libs/fd/cm/ma/gui/content/commons/actionhandlers/items/

      **[!UICONTROL Localização:]** /apps/

      **[!UICONTROL Corresponder tipos de nó:]** Selecionado

   1. Clique em **[!UICONTROL OK]**. A estrutura de pastas é criada na pasta de aplicativos.

   1. Clique em **[!UICONTROL Salvar tudo]**.

1. No nó itens recém-criados , adicione um nó para o botão/ação personalizado em um ativo específico (Exemplo: letterpdfdownloader) usando as seguintes etapas:

   1. Clique com o botão direito do mouse na pasta de itens e selecione **[!UICONTROL Criar > Criar nó]**.

   1. Certifique-se de que a caixa de diálogo Criar nó tenha os seguintes valores e clique em **[!UICONTROL OK]**:

      **[!UICONTROL Nome:]** letterpdfdownloader (Ou o nome que você deseja dar a essa propriedade - deve ser exclusivo. Se você usar um nome diferente aqui, também especifique o mesmo na variável ACTION_URL do arquivo formaction.js.)

      **[!UICONTROL Tipo:]** nt:unstructured

   1. Clique no novo nó que você criou (aqui downloadFlatPDF). O CRX exibe as propriedades do nó.

   1. Adicione a seguinte propriedade ao nó (aqui letterpdfdownloader) e clique em **[!UICONTROL Salvar tudo]**:

      | **Nome** | **Tipo** | **Valor** |
      |---|---|---|
      | sling:resourceType | String | fd/cm/ma/gui/components/admin/clientlibs/admin |

1. Crie um arquivo chamado POST.jsp com o código para a manipulação de ação do comando no seguinte local:

   /apps/fd/cm/ma/gui/components/admin/clientlibs/admin

   1. Clique com o botão direito do mouse no **[!UICONTROL administrador]** no caminho a seguir e selecione **[!UICONTROL Criar > Criar arquivo]**:

      /apps/fd/cm/ma/gui/components/admin/clientlibs/admin

      Nomeie o arquivo como POST.jsp. (O nome do arquivo precisa ser somente POST.jsp.)

   1. Clique duas vezes no botão **[!UICONTROL POST.jsp]** para abri-lo no CRX.
   1. Adicione o seguinte código ao arquivo POST.jsp e clique em **[!UICONTROL Salvar tudo]**:

      Esse código é específico para o serviço de renderização de letras. Para qualquer outro ativo, adicione as bibliotecas java desse ativo a este código. Para obter mais informações sobre APIs do AEM Forms, consulte [API do AEM Forms](https://adobe.com/go/learn_aemforms_javadocs_63_en).

      Para obter mais informações sobre AEM bibliotecas, consulte AEM [Componentes](/help/sites-developing/components.md).

      ```xml
      /*Import libraries. Here we are downloading letter flat pdf with input xml data so we require letterRender Api. For any other Module functionality we need to first import that library. */            
      <%@include file="/libs/foundation/global.jsp"%>
      <!DOCTYPE html lang="en" PUBLIC "-//W3C//DTD XHTML 1.1//EN" "https://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
      <%@page import="com.adobe.icc.ddg.api.*"%>
      <%@page import="com.adobe.icc.dbforms.obj.*"%>
      <%@page import="com.adobe.icc.render.obj.*" %>
      <%@page import="com.adobe.icc.services.api.*" %>
      <%@page import="org.apache.sling.api.resource.*" %>
      <%@page import="java.io.File" %>
      <%@page import="java.util.*" %>
      <%@page import="com.adobe.livecycle.content.appcontext.AppContextManager"%>
      <%@page import=" com.adobe.icc.dbforms.exceptions.ICCException"%>
      <%@page import="java.io.InputStream" %>
      <%@page import="java.io.FileInputStream" %>
      <%@page import="org.apache.commons.io.IOUtils" %>
      <%@page session="false" contentType="text/html; charset=utf-8"%>
      <%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0"%>
      <%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %>
       <%@page session="false" contentType="text/html; charset=utf-8"%>
      <%
         AppContextManager.setCurrentAppContext("/content/apps/cm");
         /*Get letter id sent in js file.*/
          String letterId = request.getParameter("letterId");
          if(letterId.lastIndexOf("?") != -1)
              letterId = letterId.substring(0, letterId.indexOf("?"));
          String fileName = null;
          String letterName = null;
          InputStream inputStream = null;
          /*Get xml file data*/
          if (slingRequest.getRequestParameter("file") != null)
              inputStream = slingRequest.getRequestParameter("file").getInputStream();
          if(letterId != null){
              String xmlData = null;
              try{
                  xmlData = IOUtils.toString(inputStream, "UTF-8");
              }
              catch (Exception e) {
                  log.error("Xml data does not exists.");
              }
              /*letter Name from letter letter id.*/
              letterName = letterId.substring(letterId.lastIndexOf("/")+1);
              /*Invoking letter render services API.*/
              LetterRenderService letterRenderService = sling.getService(LetterRenderService.class);
              /*using CM renderLetter api to get pdfbytes.*/
              PDFResponseType  pdfResponseType= letterRenderService.renderLetter(letterId,xmlData,true,false,false,false);
              byte[] bytes = null;
              /*Downloading pdf bytes as pdf.*/
              if(pdfResponseType != null && pdfResponseType.getFile() != null){
                  bytes = pdfResponseType.getFile().getDocument();
                  /*set the response header to enable download*/
                  response.setContentType("application/OCTET-STREAM");
                  response.setHeader("Content-Disposition", "attachment;filename=\"" + letterName + ".pdf\"");
                  response.setHeader("Pragma", "cache");
                  response.setHeader("Cache-Control", "private");
                  out.clear();
                  response.getOutputStream().write(bytes);
              }
          }
          else{
              log.error("Letter id does not exists.");
          }
      %>
      ```

## Baixe o PDF de uma carta usando a funcionalidade personalizada {#download-flat-pdf-of-a-letter-using-the-custom-functionality}

Depois de ter adicionado a funcionalidade personalizada para baixar o PDF simples de suas cartas, você pode usar as seguintes etapas para baixar a versão simples do PDF da carta selecionada:

1. Ir para `https://[server]:[port]/[ContextPath]/projects.html` e faça logon.

1. Selecionar **[!UICONTROL Forms > Cartas]**. O Gerenciamento de correspondência lista as cartas disponíveis no sistema.
1. Clique em **[!UICONTROL Selecionar]** e clique em uma carta para selecioná-la.
1. Selecionar **[!UICONTROL Mais]** > &lt;download flat=&quot;&quot; pdf=&quot;&quot;> (A funcionalidade personalizada criada com as instruções deste artigo). A caixa de diálogo Baixar carta como PDF é exibida.

   O nome do item de menu, a funcionalidade e o texto alternativo estão de acordo com a personalização criada em [Cenário: Adicione um comando à interface do usuário da lista de letras para baixar a versão de PDF simples de uma letra.](#addcommandtoletters)

   ![Funcionalidade personalizada: Baixar o Flat PDF](assets/5_downloadflatpdf.png)

1. Na caixa de diálogo Baixar carta como PDF, selecione o XML relevante a partir do qual deseja preencher os dados no PDF.

   >[!NOTE]
   >
   >Antes de baixar a carta como um PDF simples, é possível criar o arquivo XML com os dados da carta usando a **[!UICONTROL Criar relatório]** opção.

   ![Baixar carta como PDF](assets/6_downloadflatpdf.png)

   A carta é baixada no computador como um PDF simples.
