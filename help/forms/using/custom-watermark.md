---
title: Marca d'água personalizada na pré-visualização PDF carta
seo-title: Marca d'água personalizada na pré-visualização PDF carta
description: Saiba como criar uma marca d'água personalizada na pré-visualização PDF carta.
seo-description: Saiba como criar uma marca d'água personalizada na pré-visualização PDF carta.
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# Marca d&#39;água personalizada na pré-visualização PDF letra {#custom-watermark-in-letter-pdf-preview}

## Visão geral {#overview}

Na interface do usuário Criar correspondência, os usuários agentes pré-visualizações a correspondência na forma final em que é enviada para o processamento de postagens, como para envio por email ou impressão.

Para impedir o uso não autorizado desses dados, as organizações podem impor uma marca d&#39;água no PDF da pré-visualização. A marca d&#39;água padrão é &quot;PRÉ-VISUALIZAÇÃO&quot;, que aparece no PDF.

Para ativar a marca d&#39;água no PDF da pré-visualização, selecione a opção **[!UICONTROL Aplicar marca d&#39;água]** Durante a Pré-visualização em **[!UICONTROL Configurações de gerenciamento de correspondência]** em `https://[server]:[port]/system/console/configMgr`.

![marca d&#39;água padrão](assets/default-watermark.png)

Você pode usar as seguintes etapas para personalizar o texto e a aparência da marca d&#39;água:

## Personalizar a marca d&#39;água na pré-visualização PDF em Criar interface do usuário de correspondência {#customizewatermark-}

1. Vá para `https://[server]:[port]/[ContextPath]/crx/de` e faça logon como Administrador.
1. Na pasta apps, crie uma pasta chamada **[!UICONTROL previewwatermark]** com caminho/estrutura semelhante à pasta de marca d&#39;água da visualização na pasta libs:

   1. Clique com o botão direito do mouse na pasta **pré-marca d&#39;água **no seguinte caminho e selecione **Nó de sobreposição**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Certifique-se de que a caixa de diálogo Sobrepor nó tenha os seguintes valores:

      **Caminho:** /libs/fd/cm/configFiles/previewwatermark

      **Localização da sobreposição:** /apps/

      **Tipos De Nó De Correspondência:** Marcado

      >[!NOTE]
      >
      >Não faça alterações na ramificação /libs. Quaisquer alterações feitas podem ser perdidas, pois essa ramificação está sujeita a alterações sempre que você:
      >
      >* Atualizar na sua instância
      >* Aplicar uma correção
      >* Instalar um pacote de recursos


   1. Clique em **OK** e, em seguida, clique em **Salvar tudo**. A pasta **[!UICONTROL previewwatermark]** é criada no caminho especificado.

1. Copie e cole o arquivo dx da pasta &quot;/libs/fd/cm/configFiles/previewwatermark&quot; para a pasta &quot;/apps/fd/cm/configFiles/previewwatermark&quot; e clique em **[!UICONTROL Salvar tudo]**.
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

