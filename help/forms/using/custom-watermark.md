---
title: Marca d'água personalizada na visualização de PDF carta
seo-title: Marca d'água personalizada na visualização de PDF carta
description: Saiba como criar marca d'água personalizada na visualização de PDF de carta.
seo-description: Saiba como criar marca d'água personalizada na visualização de PDF de carta.
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
feature: Gerenciamento de correspondência
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Marca d&#39;água personalizada na visualização de PDF da letra {#custom-watermark-in-letter-pdf-preview}

## Visão geral {#overview}

Na interface Criar correspondência, os usuários do agente visualizam a correspondência na forma final em que é enviada para o processamento de postagens, como para e-mail ou impressão.

Para evitar o uso não autorizado desses dados, as organizações podem impor uma marca d&#39;água na visualização do PDF. A marca d&#39;água padrão é &quot;PREVIEW&quot;, que aparece no PDF.

Para ativar a marca d&#39;água em visualizar PDF, selecione a opção **[!UICONTROL Aplicar marca d&#39;água]** Durante a visualização em **[!UICONTROL Configurações de gerenciamento de correspondência]** em `https://[server]:[port]/system/console/configMgr`.

![marca d&#39;água padrão](assets/default-watermark.png)

Você pode usar as seguintes etapas para personalizar o texto e a aparência da marca d&#39;água:

## Personalizar a marca d&#39;água na visualização de PDF em Criar interface de usuário de correspondência {#customizewatermark-}

1. Vá para `https://[server]:[port]/[ContextPath]/crx/de` e faça logon como Administrador.
1. Na pasta apps, crie uma pasta chamada **[!UICONTROL previewwatermark]** com o caminho/estrutura semelhante à pasta de marca d&#39;água da visualização na pasta libs:

   1. Clique com o botão direito do mouse na pasta **visualizar marca d&#39;água **no seguinte caminho e selecione **Sobrepor nó**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Certifique-se de que a caixa de diálogo Sobrepor nó tenha os seguintes valores:

      **Caminho:** /libs/fd/cm/configFiles/previewwatermark

      **Local de sobreposição:** /apps/

      **Corresponder Tipos De Nó:** Marcado

      >[!NOTE]
      >
      >Não faça alterações na ramificação /libs. As alterações feitas podem ser perdidas, pois essa ramificação pode ser alterada sempre que você:
      >
      >* Atualizar na sua instância
      >* Aplicar um hotfix
      >* Instalar um pacote de recursos


   1. Clique em **OK** e em **Salvar tudo**. A pasta **[!UICONTROL previewwatermark]** é criada no caminho especificado.

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

   Para obter informações sobre como personalizar a aparência da marca d&#39;água, o texto e o alinhamento, consulte Adicionar e remover marcas d&#39;água e planos de fundo no documento [Assembler Service e DDX Reference](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf).

   >[!NOTE]
   >
   >No arquivo ddx, as referências ao resultado e à fonte devem permanecer inalteradas para output.pdf e input.pdf. O nome do arquivo ddx também não deve ser alterado.

1. Clique em **Salvar tudo**.

