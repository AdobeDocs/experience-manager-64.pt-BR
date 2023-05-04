---
title: Representações de vídeo
description: Representações de vídeo
contentOwner: AG
feature: Video,Renditions
role: User
exl-id: 9fc93034-e83a-42b5-901d-7867b4a850a8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 3%

---

# Representações de vídeo {#video-renditions}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Adobe Experience Manager Assets gera representações de vídeo para ativos de vídeo de vários formatos, incluindo OGG, FLV e assim por diante.

O AEM Assets suporta representações estáticas e dinâmicas (representações codificadas por DM) para ativos de mídia.

As representações estáticas são geradas nativamente usando FFMPEG (instalado e disponível no caminho do sistema) e armazenadas no repositório de conteúdo.

As representações codificadas em DM são armazenadas no servidor proxy e servidas no tempo de execução.

AEM ativos fornecem suporte de reprodução para essas execuções no lado do cliente.

Para exibir as representações de um ativo de vídeo específico, abra a página de ativos e toque no ícone Navegação global . Em seguida, escolha **[!UICONTROL Representações]** na lista.

![chlimage_1-478](assets/chlimage_1-478.png)

A lista de representações de vídeo é exibida no **[!UICONTROL Representações]** painel.

![chlimage_1-479](assets/chlimage_1-479.png)

Para configurar o servidor proxy para representações codificadas em DM, [configurar os serviços da Dynamic Media Cloud.](config-dynamic.md)

Para gerar representações de vídeo com os parâmetros desejados, [criar um perfil de vídeo correspondente](video-profiles.md).

Após configurar o servidor proxy e criar perfis de vídeo, é possível incluir essa predefinição de vídeo em um perfil de processamento e aplicar o perfil de processamento a uma pasta.

>[!NOTE]
>
>A reprodução de áudio não funciona para arquivos OGG e WAV no Internet Explorer 11. Um erro &quot;Origem inválida&quot; é exibido na página de detalhes do ativo para ativos com extensão OGG ou WAV.
>
>No MS Edge e no iPad , os arquivos OGG não são reproduzidos e geram um erro de formato Não suportado.
