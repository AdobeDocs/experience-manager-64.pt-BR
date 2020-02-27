---
title: Execuções de vídeo
description: Execuções de vídeo
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Video renditions {#video-renditions}

O Adobe Experience Manager (AEM) Assets gera renderizações de vídeo para ativos de vídeo de vários formatos, incluindo OGG, FLV e assim por diante.

O AEM Assets suporta representações estáticas e dinâmicas (execuções codificadas por DM) para ativos de mídia.

As execuções estáticas são geradas nativamente usando FFMPEG (instalado e disponível no caminho do sistema) e armazenadas no repositório de conteúdo.

As renderizações codificadas por DM são armazenadas no servidor proxy e servidas no tempo de execução.

Os ativos AEM fornecem suporte de reprodução para essas execuções no lado do cliente.

Para exibir as representações de um ativo de vídeo específico, abra sua página de ativo e toque no ícone Navegação global. Em seguida, escolha **[!UICONTROL Representações]** na lista.

![chlimage_1-478](assets/chlimage_1-478.png)

A lista de representações de vídeo é exibida no painel **[!UICONTROL Representações]** .

![chlimage_1-479](assets/chlimage_1-479.png)

Para configurar o servidor proxy para renderizações codificadas por DM, [configure os serviços da Dynamic Media Cloud.](config-dynamic.md)

Para gerar representações de vídeo com os parâmetros desejados, [crie um perfil](video-profiles.md)de vídeo correspondente.

Depois de configurar o servidor proxy e criar perfis de vídeo, você pode incluir essa predefinição de vídeo em um perfil de processamento e aplicar o perfil de processamento a uma pasta.

>[!NOTE]
>
>A reprodução de áudio não funciona para arquivos OGG e WAV no Internet Explorer 11. Um erro &quot;Origem inválida &quot; é exibido na página de detalhes do ativo para ativos com extensão OGG ou WAV.
>
>No MS Edge e iPad, os arquivos OGG não são reproduzidos e geram um erro de formato não suportado.
