---
title: Instale e configure o ImageMagick para trabalhar com o [!DNL Experience Manager] Ativos
description: Saiba mais sobre o software ImageMagick, como instalá-lo, configurar a etapa do processo da linha de comando e usá-lo para editar, compor e gerar miniaturas de imagens.
contentOwner: AG
feature: Renditions,Developer Tools
role: Admin
exl-id: 9aeda88a-fd66-4fad-b496-3352a6ecab81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 2%

---

# Instale e configure o ImageMagick para trabalhar com o [!DNL Experience Manager Assets] {#install-and-configure-imagemagick-to-work-with-aem-assets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O ImageMagick é um plug-in de software para criar, editar, compor ou converter imagens de bitmap. Ele pode ler e gravar imagens em vários formatos (mais de 200), incluindo PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF e SVG. Use o ImageMagick para redimensionar, virar, espelhar, girar, distorcer, distorcer e transformar imagens. Você também pode ajustar as cores das imagens, aplicar vários efeitos especiais ou desenhar texto, linhas, polígonos, elipses e curvas usando o ImageMagick.

Use o manipulador de mídia do Adobe Experience Manager na linha de comando para processar imagens por meio do ImageMagick. Para trabalhar com vários formatos de arquivo usando o ImageMagick, consulte [Práticas recomendadas dos formatos de arquivo de ativos](assets-file-format-best-practices.md). Para saber mais sobre todos os formatos de arquivo compatíveis, consulte [Formatos compatíveis com os ativos](assets-formats.md).

Para processar arquivos grandes usando o ImageMagick, considere requisitos de memória mais altos do que o normal, possíveis alterações necessárias às políticas de IM e o impacto geral no desempenho. Os requisitos de memória dependem de vários fatores como resolução, profundidade de bits, perfil de cor e formato de arquivo. Se você pretende processar arquivos muito grandes usando o ImageMagick, faça o benchmark correto de [!DNL Experience Manager] servidor. Alguns recursos úteis são fornecidos no final.

>[!NOTE]
>
>Se estiver usando [!DNL Experience Manager] no Adobe Managed Services (AMS), entre em contato com o Suporte ao cliente do Adobe se você planeja processar muitos arquivos grandes do PSD ou PSB. O Experience Manager pode não processar arquivos PSB de resolução muito alta com mais de 30.000 x 23.000 pixels.

## Instalar o ImageMagick {#installing-imagemagick}

Várias versões dos arquivos de instalação do ImageMagic estão disponíveis para vários sistemas operacionais. Use a versão apropriada para seu sistema operacional.

1. Baixe o [Arquivos de instalação do ImageMagick](https://www.imagemagick.org/script/download.php) para seu sistema operacional.
1. Para instalar o ImageMagick no disco que hospeda o [!DNL Experience Manager] inicie o arquivo de instalação.

1. Defina a variável de caminho Ambiente para o diretório de instalação do ImageMagic.
1. Para verificar se a instalação foi bem-sucedida, execute o `identify -version` comando.

## Configurar a etapa do processo da linha de comando {#set-up-the-command-line-process-step}

Você pode configurar a etapa do processo da linha de comando para o caso de uso específico. Execute essas etapas para gerar uma imagem invertida e miniaturas (140x100, 48x48, 319x319 e 1280x1280) sempre que adicionar um arquivo de imagem JPEG a `/content/dam` no [!DNL Experience Manager] servidor:

1. No [!DNL Experience Manager] vá para o console Fluxo de trabalho (`https://[aem_server]:[Port]/workflow`) e abra o **[!UICONTROL Ativo de atualização DAM]** modelo de fluxo de trabalho.
1. No **[!UICONTROL Ativo de atualização DAM]** modelo de fluxo de trabalho, abra o **[!UICONTROL Miniaturas do EPS (fornecidas pelo ImageMagick)]** etapa.
1. No **[!UICONTROL Guia Argumentos]**, adicionar `image/jpeg` para **[!UICONTROL Tipos Mime]** lista.

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. No **[!UICONTROL Comandos]** digite o seguinte comando:

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. Selecione o **[!UICONTROL Excluir representação gerada]** e **[!UICONTROL Gerar representação da Web]** sinalizadores.

   ![select_flags](assets/select_flags.png)

1. No **[!UICONTROL Imagem ativada na Web]** , especifique os detalhes da representação com dimensões de 1280x1280 pixels. Além disso, especifique *magem/jpeg* no **[!UICONTROL Mimetype]** caixa.

   ![web_enabled_image](assets/web_enabled_image.png)

1. Toque/clique **[!UICONTROL OK]** para salvar as alterações.

   >[!NOTE]
   >
   >O `convert` pode não ser executado com determinadas versões do Windows (por exemplo, Windows SE), pois está em conflito com o comando nativo `convert` que faz parte da instalação do Windows. Nesse caso, mencione o caminho completo do utilitário ImageMagick. Por exemplo, especifique,
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. Abra o **[!UICONTROL Processar miniaturas]** e adicionar o tipo MIME `image/jpeg` under **[!UICONTROL Ignorar Tipos Mime]**.

   ![skip_mime_types](assets/skip_mime_types.png)

1. No **[!UICONTROL Imagem ativada na Web]** , adicione o tipo MIME `image/jpeg` nos termos do **[!UICONTROL Ignorar Lista]**. Toque/clique **[!UICONTROL OK]** para salvar as alterações.

   ![web_enabled](assets/web_enabled.png)

1. Salve o workflow.
1. Para verificar se o ImageMagic é capaz de processar as imagens corretamente, carregue uma imagem JPG para [!DNL Assets]. Verifique se uma imagem invertida e as representações são geradas para ela.

## Reduzir as vulnerabilidades de segurança {#mitigating-security-vulnerabilities}

Há várias vulnerabilidades de segurança associadas ao uso do ImageMagick para processar imagens. Por exemplo, o processamento de imagens enviadas pelo usuário envolve o risco de execução remota de código (RCE).

Além disso, vários plug-ins de processamento de imagens dependem da biblioteca ImageMagick, incluindo, entre outros, a imagem do PHP, o magnífico e o clipe de papel de Ruby e a imagem do Node.js.

Se você usar o ImageMagick ou uma biblioteca afetada, o Adobe recomenda atenuar as vulnerabilidades conhecidas executando pelo menos uma das seguintes tarefas (mas, de preferência, ambas):

1. Verifique se todos os arquivos de imagem começam com o esperado [&quot;bytes mágicos&quot;](https://en.wikipedia.org/wiki/List_of_file_signatures) correspondendo aos tipos de arquivo de imagem que você suporta antes de enviá-los para o ImageMagick para processamento.
1. Use um arquivo de política para desativar os codificadores vulneráveis do ImageMagick. A política global para o ImageMagick é encontrada em `/etc/ImageMagick`.

>[!MORELIKETHIS]
>
>* [Práticas recomendadas para processar vários formatos de arquivo usando [!DNL Assets]](assets-file-format-best-practices.md)
>* [Opções de linha de comando para ImageMagick](https://www.imagemagick.org/script/command-line-options.php)
>* [Exemplos básicos e avançados de uso do ImageMagick](https://www.imagemagick.org/Usage/)
>* [Ajuste de desempenho de ativos para o ImageMagick](performance-tuning-guidelines.md)
>* [Lista completa de formatos de arquivo suportados por [!DNL Assets]](assets-formats.md)
>* [Entender os formatos de arquivo e o custo de memória das imagens](https://www.scantips.com/basics1d.html)

