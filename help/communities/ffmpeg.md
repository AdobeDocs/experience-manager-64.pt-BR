---
title: FFmpeg para comunidades
seo-title: FFmpeg for Communities
description: Como instalar e configurar o FFmpeg para comunidades
seo-description: How to install and configure FFmpeg for Communities
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Admin
exl-id: 9ed54ee3-3509-4a43-a710-90f4543ccaf3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 3%

---

# FFmpeg para comunidades {#ffmpeg-for-communities}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

FFmpeg é uma solução para conversão e transmissão de áudio e vídeo e, quando instalado, é usado para a transcodificação adequada de [ativos de vídeo](../../help/sites-authoring/default-components-foundation.md#video) assim como para o recurso de habilitação do AEM Communities.

FFmpeg é usado no ambiente de criação para obter metadados para recursos de ativação carregados, bem como gerar uma miniatura para exibição ao listar o recurso de ativação.

## Instalação do FFmpeg {#installing-ffmpeg}

O FFmpeg deve ser instalado no(s) servidor(es) que hospeda o AEM *autor* instância(s).

1. Ir para [https://www.ffmpeg.org](https://www.ffmpeg.org/)
1. Baixe a versão mais recente do FFmpeg para seu ambiente específico (Macintosh, Windows ou Linux)

   * é importante manter o FFmpeg atualizado devido às vulnerabilidades de segurança em versões mais antigas

1. Instale o FFmpeg seguindo as instruções para o SO.

1. Verifique se o executável FFmpeg está definido no caminho do sistema.

   Você deve ser capaz de executar o FFmpeg a partir de qualquer diretório no seu sistema.

   * por exemplo, `ffmpeg -version`

## Configurar o serviço de transcodificação FFmpeg {#configure-ffmpeg-transcoding-service}

Por padrão, quando o FFmpeg é instalado, várias renderizações são configuradas (transcodificações) de acordo com a definição de fluxo de trabalho do Ativo de atualização DAM .

Como as transcodificações exigem muita CPU, é recomendável modificar a lista de representações de destino. Na maioria dos casos, a transcodificação não é necessária.

Para modificar o fluxo de trabalho do Ativo de atualização do DAM e, neste exemplo, desativar a transcodificação:

* Faça logon na instância do autor com privilégios administrativos
* Na navegação global: **[!UICONTROL Ferramentas > Fluxo de trabalho > Modelos]**
* Localizar **[!UICONTROL Ativo de atualização DAM]**
* Clique duas vezes para abrir o fluxo de trabalho para edição na interface clássica

   Local resultante: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Clique duas vezes no botão **[!UICONTROL Transcodificação FFmpeg]** etapa para acessar a caixa de diálogo Propriedades da etapa
* Em **[!UICONTROL Processo]** guia :

   * **[!UICONTROL Argumentos]**: Limpar todas as entradas para desativar a transcodificação Valores padrão: `profile:firefoxhq,profile:hq,profile:flv,profile:iehq`

![chlimage_1-372](assets/chlimage_1-372.png)

* Selecionar **[!UICONTROL OK]** para fechar o `Step Properties` diálogo

* Selecionar **[!UICONTROL Salvar]** para salvar o `DAM Update Asset` workflow

   (canto superior esquerdo)
