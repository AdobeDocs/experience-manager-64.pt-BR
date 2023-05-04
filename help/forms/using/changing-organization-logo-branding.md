---
title: Alteração do logotipo da organização para marcas
seo-title: Changing the organization logo for branding
description: Para a área de trabalho da AEM Forms da marca, forneça o logotipo de sua organização personalizando o logotipo padrão.
seo-description: To brand AEM Forms workspace provide the logo of your organization by customizing the default logo.
uuid: f0c340ee-2e54-4bb0-9c30-383cc1bbadb8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 2c651302-f4ef-4211-b897-f5942ed0ffb1
exl-id: 890e98af-0491-4b59-9a9b-6c245db54f0f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 4%

---

# Alteração do logotipo da organização para marcas {#changing-the-organization-logo-for-branding}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O logotipo da organização é exibido no canto superior esquerdo do espaço de trabalho do AEM Forms. Para atualizar o logotipo, siga as [Etapas genéricas da personalização do espaço de trabalho do AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) e, em seguida, execute as etapas a seguir.

1. Crie um logotipo e nomeie o arquivo como `NewWorkspace.png`. Coloque o arquivo de imagem na pasta /apps/ws/images usando um cliente WebDAV.

   >[!NOTE]
   >
   >O tamanho recomendado para a imagem do logotipo é de 218 px × 20 px.

   >[!NOTE]
   >
   >Para obter mais informações sobre o acesso WebDAV, consulte [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

1. Faça referência à nova imagem do logotipo na folha de estilos em /apps/ws/css/newStyle.css adicionando o seguinte estilo.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px; 
         }
   ```
