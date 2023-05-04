---
title: Marca d'água personalizada na visualização de PDF de letra
seo-title: Custom watermark in letter PDF preview
description: Saiba como criar marca d'água personalizada na visualização de PDF de carta.
seo-description: Learn how to create custom watermark in letter PDF preview.
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
feature: Correspondence Management
exl-id: 8aeabd95-948d-4a54-b593-1eda8ddd731b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---

# Marca d&#39;água personalizada na visualização de PDF de letra {#custom-watermark-in-letter-pdf-preview}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

Na interface Criar correspondência, os usuários do agente visualizam a correspondência na forma final em que é enviada para o processamento de postagens, como para e-mail ou impressão.

Para evitar o uso não autorizado desses dados, as organizações podem impor uma marca d&#39;água no PDF de visualização. A marca d&#39;água padrão é &quot;PREVIEW&quot;, que aparece no PDF.

Para ativar a marca d&#39;água no PDF de visualização, selecione o **[!UICONTROL Aplicar marca d&#39;água]** Durante a opção Visualização em **[!UICONTROL Configurações de gerenciamento de correspondência]** at `https://[server]:[port]/system/console/configMgr`.

![marca d&#39;água padrão](assets/default-watermark.png)

Você pode usar as seguintes etapas para personalizar o texto e a aparência da marca d&#39;água:

## Personalizar a marca d&#39;água na visualização do PDF na interface do usuário Criar correspondência {#customizewatermark-}

1. Ir para `https://[server]:[port]/[ContextPath]/crx/de` e faça logon como Administrador.
1. Na pasta apps, crie uma pasta chamada **[!UICONTROL visualizar marca d&#39;água]** com caminho/estrutura semelhante à pasta de marca d&#39;água de visualização na pasta libs:

   1. Clique com o botão direito do mouse na pasta **visualizar marca d&#39;água **no caminho a seguir e selecione **Nó de sobreposição**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Certifique-se de que a caixa de diálogo Sobrepor nó tenha os seguintes valores:

      **Caminho:** /libs/fd/cm/configFiles/previewwatermark

      **Localização da sobreposição:** /apps/

      **Corresponder tipos de nó:** Verificado

      >[!NOTE]
      >
      >Não faça alterações na ramificação /libs. As alterações feitas podem ser perdidas, pois essa ramificação pode ser alterada sempre que você:
      >
      >* Atualizar na sua instância
      >* Aplicar um hotfix
      >* Instalar um pacote de recursos


   1. Clique em **OK** e, em seguida, clique em **Salvar tudo**. O **[!UICONTROL visualizar marca d&#39;água]** é criada no caminho especificado.

1. Copie e cole o arquivo ddx da pasta &quot;/libs/fd/cm/configFiles/previewwatermark&quot; para a pasta &quot;/apps/fd/cm/configFiles/previewmark&quot; e clique em **[!UICONTROL Salvar tudo]**.
1. Faça as alterações desejadas no arquivo ddx em /apps/fd/cm/configFiles/previewwatermark/.

   ```
   <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
    <PDF result="output.pdf">
     <PDF source="input.pdf"/>
           <Watermark opacity="15%" rotation="45">
            <StyledText>
                     <p font-family="Georgia" font-size="70pt" color="black" font-weight="bold">
                         PREVIEW
                    </p>
            </StyledText>
           </Watermark>
    </PDF>
   </DDX>
   ```

   Para obter informações sobre como personalizar a aparência da marca d&#39;água, o texto e o alinhamento, consulte Adicionar e remover marcas d&#39;água e planos de fundo na [Serviço de Assembler e Referência DDX](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf) documento.

   >[!NOTE]
   >
   >No arquivo ddx, as referências ao resultado e à fonte devem permanecer inalteradas para output.pdf e input.pdf. O nome do arquivo ddx também não deve ser alterado.

1. Clique em **Salvar tudo**.
