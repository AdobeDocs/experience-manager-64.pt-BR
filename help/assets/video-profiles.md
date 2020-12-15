---
title: perfis de vídeo Dynamic Media
seo-title: perfis de vídeo Dynamic Media
description: 'A Dynamic Media já vem com um perfil adaptável de codificação de vídeo predefinido. As configurações neste perfil predefinido são otimizadas para oferecer aos clientes a melhor experiência de visualização possível. '
seo-description: 'A Dynamic Media já vem com um perfil adaptável de codificação de vídeo predefinido. As configurações neste perfil predefinido são otimizadas para oferecer aos clientes a melhor experiência de visualização possível. '
uuid: cfb498f8-44a0-4d94-99b0-fed7c27f575b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: b893f366-279a-4872-9413-77626d3387ea
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '3100'
ht-degree: 18%

---


# perfis de vídeo Dynamic Media {#video-profiles}

A Dynamic Media já vem com um perfil adaptável de codificação de vídeo predefinido. As configurações neste perfil predefinido são otimizadas para oferecer aos clientes a melhor experiência de visualização possível. Quando você codifica seus vídeos principais usando o perfil Adaptive Video Encoding, durante a reprodução o player de vídeo ajusta automaticamente a qualidade do fluxo de vídeo com base na velocidade de conexão com a Internet de seus clientes. Isso é conhecido como streaming adaptável.

Estes são outros fatores que determinam a qualidade de seus vídeos:

* **Resolução do vídeo principal carregado**

   Se o vídeo MP4 foi gravado em uma resolução mais baixa, como 240p ou 360p, ele não pode ser transmitido em alta definição.

* **Tamanho do player de vídeo**

   Por padrão, **[!UICONTROL Largura]** no perfil Adaptive Video Encoding está definido como **[!UICONTROL Auto]**. Novamente, durante a reprodução, a melhor qualidade é usada com base no tamanho do player.

Consulte também [Práticas recomendadas para codificação de vídeo](video.md#best-practices-for-encoding-videos).

>[!NOTE]
>
>Para gerar os metadados de um vídeo e as miniaturas de imagem de vídeo associadas, o próprio vídeo precisa passar pelo processo de codificação no Dynamic Media. No AEM, o fluxo de trabalho **[!UICONTROL Codificação de vídeo do Dynamic Media]** codifica o vídeo se você tiver ativado a mídia dinâmica e configurado os serviços da nuvem de vídeo. Esse fluxo de trabalho captura o histórico do processo de fluxo de trabalho e as informações de falha.
>
>Consulte [Monitorar o progresso da codificação de vídeo e da publicação no YouTube](video.md#monitoring-video-encoding-and-youtube-publishing-progress). Se você habilitou o Dynamic Media e configurou serviços de nuvem de vídeo, o fluxo de trabalho **[!UICONTROL Codificar vídeo]** do Dynamic Media entrará em vigor automaticamente quando você carregar um vídeo. (Se você não estiver usando mídia dinâmica, o fluxo de trabalho **[!UICONTROL Atualizar ativo do DAM]** entrará em vigor.)
>
>Os metadados são úteis quando você está procurando ativos. As miniaturas são imagens de vídeo estáticas geradas durante a codificação. Eles são exigidos pelo sistema AEM e usados na interface do usuário para ajudá-lo a identificar visualmente os vídeos na visualização **[!UICONTROL Cartões]**, **[!UICONTROL Resultados da pesquisa]** e na Lista **[!UICONTROL Ativo]**. Você pode ver as miniaturas geradas ao tocar no ícone **[!UICONTROL Representações]** (paleta do pintor) de um vídeo codificado.

Quando terminar de criar o perfil de vídeo, aplique-o a uma pasta ou várias pastas. Consulte [Aplicar um perfil de vídeo a pastas.](#applying-a-video-profile-to-folders)

Para definir parâmetros de processamento avançados para outros tipos de ativos, consulte [Configurando o Processamento de Ativos](config-dms7.md#configuring-asset-processing).

## Predefinições de codificação de vídeo adaptáveis {#adaptive-video-encoding-presets}

A tabela a seguir identifica perfis de codificação de práticas recomendadas para streaming de vídeo adaptável para dispositivos móveis e tablet e computadores desktop. É possível usar essas predefinições para qualquer vídeo com relação de aspecto.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Codec de formatação do vídeo</strong></td> 
   <td><strong>Tamanho do vídeo - Largura (px)</strong></td> 
   <td><strong>Tamanho do vídeo - Altura (px)</strong></td> 
   <td><strong>Manter taxa de proporção?</strong></td> 
   <td><strong>Taxa de bits de vídeo (Kbps)</strong></td> 
   <td><strong>Taxa De Quadros De Vídeo (Fps)</strong></td> 
   <td><strong>Codec de áudio</strong></td> 
   <td><strong>Taxa de bits de áudio (Kbps)</strong></td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>360</td> 
   <td>Sim</td> 
   <td>730</td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>540</td> 
   <td>Sim</td> 
   <td>2000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>720<br /> </td> 
   <td>Sim</td> 
   <td>3000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
 </tbody> 
</table>

## Criação de um perfil de codificação de vídeo Dynamic Media para streaming adaptável {#creating-a-video-encoding-profile-for-adaptive-streaming}

A Dynamic Media já vem com um perfil adaptável de codificação de vídeo predefinido - um grupo de configurações de upload de vídeo para MP4 H.264 - que é otimizado para a melhor experiência de visualização. Você pode usar esse perfil ao carregar seus vídeos.

No entanto, se esse perfil predefinido não atender às suas necessidades, você pode optar por criar seu próprio perfil adaptável de codificação de vídeo. Quando você usa a configuração **[!UICONTROL Codificar para transmissão adaptativa]**-*uma prática recomendada*- todas as predefinições de codificação adicionadas ao perfil são validadas para garantir que todos os vídeos tenham a mesma proporção. Além disso, os vídeos codificados são tratados como uma taxa de bits múltipla definida para streaming.

Ao criar o perfil de codificação de vídeo, você observará que a maioria das opções de codificação são preenchidas previamente com as configurações padrão recomendadas para ajudá-lo. No entanto, se você selecionar um valor diferente do padrão recomendado, esteja ciente de que isso pode resultar em baixa qualidade de vídeo durante a reprodução e outros problemas de desempenho.

Assim, para todas as predefinições de codificação de vídeo MP4 H.264 no perfil, os valores a seguir são validados para garantir que sejam os mesmos nas predefinições de codificação individuais no perfil, possibilitando o streaming adaptativo:

* Codec de formato de vídeo - MP4 H.264 (.mp4)
* Codec de áudio
* Taxa de áudio
* Manter taxa de proporção
* Codificação em dois passos
* Taxa de bits constante
* Perfil H264
* Taxa de amostra do áudio

Se os valores não forem os mesmos, você poderá continuar criando o perfil como está. No entanto, lembre-se de que o streaming adaptativo não será possível. Em vez disso, os usuários experimentarão o streaming de taxa de bits única. É recomendável editar as configurações de codificação para usar os mesmos valores em predefinições de codificação individuais no perfil. (Observe que o perfil de vídeo/editor predefinido deve aplicar a paridade das configurações de codificação de vídeo adaptáveis se **[!UICONTROL Codificar para transmissão adaptável]** estiver ativado.)

Consulte também [Criar um perfil de codificação de vídeo para streaming progressivo](#creating-a-video-encoding-profile-for-progressive-streaming).

Consulte também [Práticas recomendadas para codificação de vídeo](video.md#best-practices-for-encoding-videos).

Para definir parâmetros de processamento avançados para outros tipos de ativos, consulte [Configurando o Processamento de Ativos](config-dms7.md#configuring-asset-processing).

Quando terminar de criar o perfil de vídeo, aplique-o a uma ou várias pastas.

**Para criar um perfil de codificação de vídeo Dynamic Media para streaming** adaptável:

1. Toque ou clique no logotipo AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de vídeo]**.
1. Toque em **[!UICONTROL Criar]** para adicionar um novo perfil de vídeo.

1. Insira um nome e uma descrição para o perfil.
1. Certifique-se de que **[!UICONTROL Codificar para transmissão adaptativa]** esteja marcada (padrão).
1. Toque em **[!UICONTROL Adicionar predefinição de codificação de vídeo]**.
1. Na guia **[!UICONTROL Basic]**, defina as opções de vídeo e áudio.

   Toque no ícone de informações ao lado de cada opção para obter descrições adicionais ou configurações recomendadas com base no codec de formato de vídeo selecionado.

1. No cabeçalho Tamanho do vídeo, verifique se **[!UICONTROL Manter proporção]** está marcada.
1. Defina a resolução do tamanho do quadro de vídeo em pixels. Use o valor **[!UICONTROL Auto]** para dimensionar automaticamente de modo a corresponder à proporção de aspecto de origem (proporção largura/altura). Por exemplo, Auto x 480 ou 640 x Auto.

   Faça uma das seguintes opções:

   * No campo **[!UICONTROL Largura]**, digite **[!UICONTROL auto]**. No campo **[!UICONTROL Altura]**, insira um valor em pixels.
   * Para ajudá-lo a visualizar o tamanho do vídeo, toque no ícone **[!UICONTROL Information]** (i) à direita de **[!UICONTROL Height]** para abrir a página **[!UICONTROL Calculadora de tamanho]**. Use **[!UICONTROL Calculadora de tamanho]** para definir as dimensões de vídeo (representadas pela caixa azul) desejada. Toque em **[!UICONTROL X]** no canto superior direito quando terminar.

1. (Opcional) Toque na guia **[!UICONTROL Avançado]** e verifique se a caixa de seleção **[!UICONTROL Usar valores padrão]** está selecionada (recomendável). Como alternativa, modifique as configurações avançadas de vídeo e áudio.
1. No canto superior direito da página, toque em **[!UICONTROL Salvar]** para salvar a predefinição.
1. Faça uma das seguintes opções:

   * Repita as etapas de 5 a 10 para criar predefinições de codificação adicionais. (O streaming adaptável de vídeo requer mais de uma predefinição.)
   * No canto superior direito da página, toque **[!UICONTROL Salvar]** novamente para salvar o perfil.

## Monitorando o andamento de um trabalho de codificação {#monitoring-the-progress-of-an-encoding-job}

Um indicador de processamento (ou barra de progresso) é exibido para que você possa monitorar visualmente o progresso de um trabalho de codificação de vídeo.

Você também pode visualização o arquivo `error.log` para monitorar o progresso de um trabalho de codificação, para ver se a codificação foi concluída ou para ver quaisquer erros de trabalho. O `error.log` está localizado na pasta `logs` onde a instância do AEM está instalada.

## Criação de um perfil de codificação de vídeo Dynamic Media para streaming progressivo {#creating-a-video-encoding-profile-for-progressive-streaming}

Se você optar por não usar a opção **[!UICONTROL Codificar para transmissão adaptável]**, lembre-se de que todas as predefinições de codificação adicionadas ao perfil são tratadas como representações de vídeo individuais para transmissão de streaming com taxa de bits única ou entrega de vídeo progressiva. Além disso, não há validação para garantir que todas as representações de vídeo tenham a mesma proporção.

Dependendo do modo que você estiver executando, os codecs de formato de vídeo suportados são os seguintes:

* Modo Dynamic Media-Scene7: H.264 (.mp4)
* Modo Dynamic Media-Híbrido: H.264 (.mp4), WebM

Consulte também [Criar um perfil de codificação de vídeo para streaming adaptável](#creating-a-video-encoding-profile-for-adaptive-streaming).

Consulte também [Práticas recomendadas para codificação de vídeo](video.md#best-practices-for-encoding-videos).

Para definir parâmetros de processamento avançados para outros tipos de ativos, consulte [Configurando o Processamento de Ativos](config-dms7.md#configuring-asset-processing).

Quando terminar de criar o perfil de vídeo, aplique-o a uma ou várias pastas.

**Para criar um perfil de codificação de vídeo Dynamic Media para streaming progressivo:**

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de vídeo]**.
1. Toque em **[!UICONTROL Criar]** para adicionar um novo perfil de vídeo.
1. Insira um nome e uma descrição para o perfil.
1. Desmarque a caixa de seleção **[!UICONTROL Codificar para transmissão adaptativa]**.
1. Toque em **[!UICONTROL Adicionar predefinição de codificação de vídeo]**.
1. Na guia **[!UICONTROL Basic]**, defina as opções de vídeo e áudio.

   Toque no ícone **[!UICONTROL Information]** ao lado de cada opção para obter descrições adicionais ou configurações recomendadas com base no codec de formato de vídeo selecionado.

1. (Opcional) No cabeçalho **Tamanho do vídeo**, desmarque **[!UICONTROL Manter proporção]**.
1. No campo **[!UICONTROL Largura]**, digite **[!UICONTROL auto]**; à direita do campo **[!UICONTROL Altura]**, toque no ícone **[!UICONTROL Informações]**. Use a página **[!UICONTROL Calculadora de tamanho]** para definir ainda mais a dimensão de vídeo (caixa azul) como desejar. Toque em **[!UICONTROL X]** quando terminar.
1. (Opcional) Execute um dos procedimentos a seguir:

   * Toque na guia **[!UICONTROL Avançado]** e verifique se a caixa de seleção **[!UICONTROL Usar valores padrão]** está selecionada (recomendável).
   * Desmarque a caixa de seleção **[!UICONTROL Usar valores padrão]** e especifique as configurações de vídeo e áudio desejadas.

      Toque no ícone **[!UICONTROL Information]** ao lado de cada opção para obter descrições adicionais ou configurações recomendadas com base no codec de formato de vídeo selecionado.

1. No canto superior direito da página, toque em **[!UICONTROL Salvar]** para salvar a predefinição.
1. Faça uma das seguintes opções:

   * Repita as etapas de 5 a 10 para criar predefinições de codificação adicionais.
   * No canto superior direito da página, toque em **[!UICONTROL Salvar]** para salvar o perfil.

## Uso de parâmetros de codificação de vídeo adicionados personalizados {#using-custom-added-video-encoding-parameters}

Você pode editar um perfil de codificação de vídeo existente para aproveitar os parâmetros avançados de codificação de vídeo que não são encontrados na interface do usuário ao criar ou editar um Perfil de vídeo no AEM. Você pode adicionar um ou mais parâmetros avançados, como **[!UICONTROL minBitrate]** e **[!UICONTROL maxBitrate]**, ao seu perfil existente.

**Para usar parâmetros** de codificação de vídeo adicionados personalizados:

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Geral > CRXDE Lite]**.
1. Na página **[!UICONTROL CRXDE Lite]**, no painel **[!UICONTROL Explorer]** à esquerda, navegue até o seguinte:

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit*`

1. No painel no lado inferior direito da página, na guia **[!UICONTROL Propriedades]**, especifique **[!UICONTROL Nome]**, **[!UICONTROL Tipo]** e **[!UICONTROL Valor]** do parâmetro que pretende utilizar.

   Os seguintes parâmetros avançados estão disponíveis para uso:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Nome</strong></td> 
    <td><strong>Descrição</strong><br /> </td> 
    <td><strong>Tipo</strong><br /> </td> 
    <td><strong>Valor</strong></td> 
    </tr> 
    <tr> 
    <td><code>h264Level</code></td> 
    <td>Nível H.264 a ser usado para codificação. Normalmente, isso é determinado automaticamente com base nas configurações de codificação que você está usando.</td> 
    <td><code>String</code></td> 
    <td><p>10 * h264 nível</p> <p>Por exemplo, 3,0 = 30, 1,3 = 13)</p> <p>Nenhum valor padrão.</p> </td> 
    </tr> 
    <tr> 
    <td><code>keyframe</code></td> 
    <td>O número de públicos alvos entre quadros-chave. Calcule esse valor para gerar um quadro-chave a cada 2-10 segundos. Por exemplo, a 30 quadros por segundo, o intervalo do quadro-chave deve ser de 60 a 300.<br /> <br /> Intervalos menores de quadros-chave melhoram o comportamento de busca de fluxo e troca de fluxo para codificações de vídeo adaptáveis e também podem melhorar a qualidade para vídeos que têm muito movimento. No entanto, como os quadros-chave aumentam o tamanho de um arquivo, um intervalo de quadros-chave mais baixo normalmente resulta em uma qualidade de vídeo geral mais baixa em uma determinada taxa de bits.</td> 
    <td><code>String</code></td> 
    <td><p>Número positivo.</p> <p>O padrão é 300.</p> <p>O valor recomendado para HLS (HTTP Live Streaming) é 60-90.</p> </td> 
    </tr> 
    <tr> 
    <td><code>minBitrate</code></td> 
    <td><p>Taxa de bits mínima para permitir codificações de taxa de bits variável, em Kbps (kilobits por segundo).</p> <p>Este parâmetro só se aplica quando<strong> Usar a taxa de bits constante</strong> é desmarcada na guia Avançado quando você cria ou edita um perfil de codificação de vídeo.</p> <p>Consulte também <a href="/help/assets/video.md#bitrate">Taxa de bits</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Número positivo, em Kbps.</p> <p>Nenhum valor padrão.</p> </td> 
    </tr> 
    <tr> 
    <td><code>maxBitrate</code></td> 
    <td><p>Taxa de bits máxima para permitir codificações de taxa de bits variável, em Kbps.</p> <p>Este parâmetro só se aplica quando<strong> Usar a taxa de bits constante</strong> é desmarcada na guia Avançado quando você cria ou edita um perfil de codificação de vídeo.</p> <p>Consulte também <a href="/help/assets/video.md#bitrate">Taxa de bits</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Número positivo, em Kbps.</p> <p>Nenhum valor padrão. No entanto, o valor recomendado é até duas vezes maior que a taxa de bits de codificação.</p> </td> 
    </tr> 
    <tr> 
    <td><code>audioBitrateCustom</code></td> 
    <td>Defina o valor como <code>true</code> para forçar uma taxa de bits constante para o fluxo de áudio, se suportado pelo codec de áudio.</td> 
    <td><code>String</code></td> 
    <td><p><code>true</code>/<code>false</code></p> <p>O padrão é <code>false</code>.</p> <p>O valor recomendado para HLS (HTTP Live Streaming) é <code>false</code>.</p> <p> </p> </td> 
    </tr> 
    </tbody> 
   </table>

   ![chlimage_1-516](assets/chlimage_1-516.png)

1. Próximo ao canto inferior direito da página, toque em **[!UICONTROL Adicionar]**.
1. Faça uma das seguintes opções:

   * Repita as etapas 3 e 4 para adicionar outro parâmetro ao perfil de codificação de vídeo.
   * Próximo ao canto superior esquerdo da página, toque em **[!UICONTROL Salvar tudo]**.

1. No canto superior esquerdo da página **[!UICONTROL CRXDE Lite]**, toque no ícone **[!UICONTROL Início traseiro]** para voltar ao AEM.

### Edição de um perfil de codificação de vídeo do Dynamic Media {#editing-a-video-encoding-profile}

Você pode editar qualquer perfil de codificação de vídeo criado para adicionar, editar ou excluir predefinições de vídeo dentro desse perfil.

Por padrão, não é possível editar o perfil predefinido e predefinido **[!UICONTROL Adaptive Video Encoding]** que veio com o Dynamic Media. Em vez disso, você pode copiar facilmente o perfil e salvá-lo com um novo nome. Em seguida, é possível editar as predefinições desejadas no perfil copiado.

Consulte também [Práticas recomendadas para codificação de vídeo](video.md#best-practices-for-encoding-videos).

Para definir parâmetros de processamento avançados para outros tipos de ativos, consulte [Configurando o Processamento de Ativos](config-dms7.md#configuring-asset-processing).

**Para editar um perfil** de codificação de vídeo do Dynamic Media:

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de vídeo]**.
1. Na página **[!UICONTROL Perfis de vídeo]**, verifique o nome de um perfil de vídeo.
1. Na barra de ferramentas, toque em **[!UICONTROL Editar]**.
1. Na página **[!UICONTROL Perfil de codificação de vídeo]**, edite o nome e a descrição, conforme desejado.
1. Como prática recomendada, verifique se a caixa de seleção **[!UICONTROL Codificar para transmissão adaptável]** está selecionada.

   Toque no ícone de informações para obter uma descrição da transmissão adaptável. (Se você estiver editando um perfil de vídeo progressivo, não marque essa caixa de seleção.)

1. No cabeçalho **[!UICONTROL Predefinições de codificação de vídeo]**, adicione, edite ou exclua predefinições de codificação de vídeo que compõem o perfil.

   Toque no ícone **[!UICONTROL Information]** ao lado de cada opção nas guias **[!UICONTROL Basic]** e **[!UICONTROL Advanced]** para obter descrições adicionais ou configurações recomendadas com base no codec de formato de vídeo selecionado.

1. No canto superior direito da página, toque **[!UICONTROL Salvar]**.

### Copiando um perfil de codificação de vídeo do Dynamic Media {#copying-a-video-encoding-profile}

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de vídeo]**.
1. Na página **[!UICONTROL Perfis de vídeo]**, verifique o nome de um perfil de vídeo.
1. Na barra de ferramentas, toque em **[!UICONTROL Copiar]**.
1. Na página **[!UICONTROL Perfil de codificação de vídeo]**, digite um novo nome para o perfil.
1. Como prática recomendada, verifique se a caixa de seleção **[!UICONTROL Codificar para transmissão adaptável]** está selecionada. Toque no ícone de informações para obter uma descrição da transmissão adaptável. (Se você estiver copiando um perfil de vídeo progressivo, não marque a caixa de seleção.)

   No Dynamic Media - modo Híbrido, se uma predefinição de vídeo WebM fizer parte do perfil de vídeo, **[!UICONTROL Codificar para transmissão adaptável]** não será possível porque todas as predefinições devem ser MP4.
1. No cabeçalho **[!UICONTROL Predefinições de codificação de vídeo]**, adicione, edite ou exclua predefinições de codificação de vídeo que compõem o perfil.

   Toque no ícone **[!UICONTROL Information]** ao lado de cada opção nas guias **[!UICONTROL Basic]** e **[!UICONTROL Advanced]** para obter as configurações e descrições recomendadas.

1. No canto superior direito da página, toque **[!UICONTROL Salvar]**.

### Excluindo um perfil de codificação de vídeo do Dynamic Media {#deleting-a-video-encoding-profile}

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de vídeo]**.
1. Na página **[!UICONTROL Perfis de vídeo]**, verifique um ou mais nomes de perfis de vídeo.
1. Na barra de ferramentas, toque em **[!UICONTROL Delete]**.
1. Toque em **[!UICONTROL OK]**.

## Aplicar um perfil de vídeo Dynamic Media a pastas {#applying-a-video-profile-to-folders}

Quando você atribui um perfil de vídeo a uma pasta, qualquer subpasta herda automaticamente o perfil da pasta pai. Isso significa que você pode atribuir apenas um perfil de vídeo a uma pasta. Dessa forma, considere cuidadosamente a estrutura de pastas de onde você carrega, armazena, usa e arquiva ativos.

Se você atribuiu um perfil de vídeo diferente a uma pasta, o novo perfil substituirá o perfil anterior. Os ativos de pasta existentes anteriormente permanecem inalterados. O novo perfil é aplicado aos ativos adicionados posteriormente à pasta.

As pastas que têm um perfil atribuído a ele são indicadas na interface do usuário pelo nome do perfil que aparece no nome do cartão.

![chlimage_1-517](assets/chlimage_1-517.png)

Você pode aplicar perfis de vídeo a pastas específicas ou globalmente a todos os ativos.

### Aplicar perfis de vídeo a pastas específicas {#applying-video-profiles-to-specific-folders}

Aplique um perfil de vídeo a uma pasta no menu **[!UICONTROL Ferramentas]** ou, se estiver na pasta, em **[!UICONTROL Propriedades]**. Esta seção descreve como aplicar perfis de vídeo a pastas de ambas as maneiras.

As pastas que têm um perfil já atribuído a elas são indicadas ao exibir do nome do perfil logo abaixo do nome da pasta.

#### Aplicação de perfis de vídeo Dynamic Media a pastas da interface de usuário de Perfis {#applying-video-profiles-to-folders-from-profiles-user-interface}

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de vídeo]**.
1. Selecione o perfil de vídeo que deseja aplicar a uma pasta ou várias pastas.
1. Toque em **[!UICONTROL Aplicar perfil às pastas]** e selecione uma ou várias pastas que deseja usar para receber os ativos carregados recentemente e toque em **[!UICONTROL Aplicar]**. As pastas que têm um perfil já atribuído a elas são indicadas ao exibir do nome do perfil logo abaixo do nome da pasta.

#### Aplicar perfis de vídeo Dynamic Media a pastas a partir de Propriedades {#applying-video-profiles-to-folders-from-properties}

1. Toque no logotipo AEM e navegue até **[!UICONTROL Assets]** e, em seguida, até a pasta à qual deseja aplicar um perfil de vídeo.
1. Na pasta, toque na marca de seleção para selecioná-la e, em seguida, toque em **[!UICONTROL Propriedades]**.
1. Selecione a guia **[!UICONTROL Perfis de vídeo]** e selecione o perfil no menu suspenso e toque em **[!UICONTROL Salvar e fechar]**. As pastas que têm um perfil já atribuído a elas são indicadas ao exibir do nome do perfil logo abaixo do nome da pasta.

   ![chlimage_1-518](assets/chlimage_1-518.png)

### Aplicar um perfil de vídeo Dynamic Media globalmente {#applying-a-video-profile-globally}

Além de aplicar um perfil a uma pasta, também é possível aplicar um globalmente para que qualquer conteúdo carregado AEM ativos em qualquer pasta tenha o perfil selecionado aplicado.

**Para aplicar um perfil de vídeo Dynamic Media globalmente**:

1. Navegue até CRXDE Lite até o seguinte nó: `/content/dam/jcr:content`.
1. Adicione a propriedade **[!UICONTROL videoProfile]**: `/etc/dam/video/dynamicmedia/<name_of_video_encoding_profile>`
1. Toque em **[!UICONTROL Salvar tudo]**.

![chlimage_1-519](assets/chlimage_1-519.png)

## Remoção de um perfil de vídeo Dynamic Media de pastas {#removing-a-video-profile-from-folders}

Quando você remove um perfil de vídeo de uma pasta, qualquer subpasta herda automaticamente a remoção do perfil da pasta pai. No entanto, qualquer processamento de arquivos que tenha ocorrido dentro das pastas permanece intacto.

Remova um perfil de vídeo de uma pasta no menu **[!UICONTROL Ferramentas]** ou, se estiver na pasta, nas **[!UICONTROL Configurações da pasta]**. Esta seção descreve como remover perfis de vídeo de pastas de ambas as maneiras.

### Remoção de perfis de vídeo Dynamic Media de pastas por meio da interface de usuário de Perfis {#removing-video-profiles-from-folders-via-profiles-user-interface}

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de vídeo]**.
1. Selecione o perfil de vídeo que deseja remover de uma pasta ou de várias pastas.
1. Toque em **[!UICONTROL Remover Perfil da(s) pasta(s)]** e selecione a pasta ou várias pastas que deseja usar para remover o perfil e toque em **[!UICONTROL Remover]**.

   Você pode confirmar que o perfil de vídeo não é mais aplicado a uma pasta porque o nome não aparece mais abaixo do nome da pasta.

### Remoção de perfis de vídeo Dynamic Media de pastas por meio de Propriedades {#removing-video-profiles-from-folders-via-properties}

1. Toque no logotipo AEM e navegue até **[!UICONTROL Assets]** e, em seguida, até a pasta da qual você deseja remover um perfil de vídeo.
1. Na pasta, toque na marca de seleção para selecioná-la e, em seguida, toque em **[!UICONTROL Propriedades]**.
1. Selecione a guia **[!UICONTROL Perfis de vídeo]** e selecione **[!UICONTROL Nenhum]** no menu suspenso e toque em **[!UICONTROL Salvar e fechar]**. As pastas que têm um perfil já atribuído a elas são indicadas ao exibir do nome do perfil logo abaixo do nome da pasta.

