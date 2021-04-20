---
title: FFmpeg para comunidades
seo-title: FFmpeg para comunidades
description: Como instalar e configurar o FFmpeg para comunidades
seo-description: Como instalar e configurar o FFmpeg para comunidades
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 1%

---


# FFmpeg para Comunidades {#ffmpeg-for-communities}

## Visão geral {#overview}

FFmpeg é uma solução para converter e transmitir áudio e vídeo e, quando instalado, é usado para a transcodificação adequada de [ativos de vídeo](../../help/sites-authoring/default-components-foundation.md#video), bem como para o recurso de habilitação do AEM Communities.

FFmpeg é usado no ambiente de criação para obter metadados para recursos de ativação carregados, bem como gerar uma miniatura para exibição ao listar o recurso de ativação.

## Instalar FFmpeg {#installing-ffmpeg}

FFmpeg deve ser instalado no(s) servidor(es) que hospeda a(s) instância(s) *author* do AEM.

1. Vá para [https://www.ffmpeg.org](https://www.ffmpeg.org/)
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
* Localize **[!UICONTROL Ativo de atualização do DAM]**
* Clique duas vezes para abrir o fluxo de trabalho para edição na interface clássica

   Local resultante: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Clique duas vezes na etapa **[!UICONTROL FFmpeg transcoding]** para acessar a caixa de diálogo Propriedades da etapa
* Na guia **[!UICONTROL Process]**:

   * **[!UICONTROL Argumentos]**: Limpar todas as entradas para desativar a transcodificação Valores padrão:  `profile:firefoxhq,profile:hq,profile:flv,profile:iehq`

![chlimage_1-372](assets/chlimage_1-372.png)

* Selecione **[!UICONTROL OK]** para fechar a caixa de diálogo `Step Properties`

* Selecione **[!UICONTROL Salvar]** para salvar o workflow `DAM Update Asset`

   (canto superior esquerdo)

