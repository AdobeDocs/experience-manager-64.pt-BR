---
title: Perfis de imagem do Dynamic Media
seo-title: Dynamic Media Image Profiles
description: Crie Perfis de imagem que contêm configurações para a máscara de nitidez e recorte inteligente ou amostra inteligente, ou ambos, e aplique o perfil a uma pasta de ativos de imagem.
seo-description: Create Image Profiles that contain settings for unsharp mask, and smart crop or smart swatch, or both, then apply the profile to a folder of image assets.
uuid: 9049fab9-d2be-4118-8684-ce58f3c8c16a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: 4f9301db-edf8-480b-886c-b5e8fca5bf5c
exl-id: 895103c8-df58-40f0-85d6-e29637edce53
feature: Image Profiles
role: Admin,User
source-git-commit: c413f31498cdccf8ceea4afc225c570a40ba1819
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Perfis de imagem do Dynamic Media {#image-profiles}

Ao fazer upload de imagens, você pode cortar automaticamente a imagem ao fazer upload aplicando um Perfil de imagem à pasta.

>[!NOTE]
>
>O Recorte inteligente está disponível somente no modo Dynamic Media - Scene7.

>[!IMPORTANT]
>
>Os Perfis de imagem não se aplicam a arquivos PDF, GIF animado ou INDD (Adobe InDesign).


## Opções de corte {#crop-options}

Quando você implementa o Recorte inteligente em imagens, o Adobe recomenda a seguinte prática recomendada e aplica o seguinte limite:

| Tipo de limite | Prática recomendada | Limite imposto |
| --- | --- | --- |
| Número de Recortes Inteligentes por imagem | 5 | 100 |

Consulte também [Limitações do Dynamic Media](/help/assets/limitations.md).

<!-- CQDOC-16069 for paragraph directly below -->

As coordenadas de recorte inteligente dependem da taxa de proporção. Ou seja, para cada configuração de recorte inteligente em um Perfil de imagem, se a proporção for a mesma para as dimensões adicionadas no Perfil de imagem, a mesma proporção de aspecto será enviada para o Dynamic Media. Como resultado, o Adobe recomenda usar a mesma área de corte. Isso garante que não haja impacto para diferentes dimensões usadas no Perfil de imagem.

Cada geração de Corte inteligente que você cria requer processamento extra. Por exemplo, adicionar mais de cinco taxas de proporção de Corte inteligente pode resultar em uma taxa lenta de ingestão de ativos. Também pode causar um aumento da carga nos sistemas. Como você pode aplicar o Recorte inteligente no nível da pasta, o Adobe recomenda usá-lo nas pastas *only* quando necessário.

**Diretrizes para definir o Recorte inteligente em um perfil de imagem**
Para manter o uso do Smart Crop sob controle e otimizar o tempo de processamento e o armazenamento de colheitas, o Adobe recomenda as seguintes diretrizes e dicas:

* Os ativos de imagem que terão um recorte inteligente aplicado a eles devem ter no mínimo 50 x 50 pixels ou mais. &lt;!— CQDOC-20087>
* Não é permitido um Perfil de imagem que contenha dimensões de recorte inteligente duplicadas. &lt;!— CQDOC-20087>
* Não são permitidos perfis de imagem com nome duplicado que tenham opções de recorte inteligente definidas. &lt;!— CQDOC-20087>
* Crie Perfis de imagem em toda a página/no tipo de ativo para pastas e subpastas específicas, em vez de um perfil de recorte inteligente comum que é aplicado a todas as pastas ou a todos os ativos.
* Um Perfil de imagem aplicado às subpastas substitui um Perfil de imagem que é aplicado à pasta.
* Idealmente, tenha 10 a 15 recortes inteligentes por imagem para otimizar as taxas de tela e o tempo de processamento.
<!-- * Avoid creating duplicate smart crop profiles that have the same width and height values. 
* Name smart crops based on crop dimensions, not on end usage. Doing so helps to optimize for duplicates where a single dimension is used on multiple pages.-->

Você tem duas opções de recorte de imagem para escolher. Você também pode optar por automatizar a criação de amostras de cores e imagens ou preservar o conteúdo de corte nas resoluções do target.

>[!IMPORTANT]
>
>・ O Adobe recomenda que você analise todas as culturas e amostras geradas para garantir que elas sejam apropriadas e relevantes para sua marca e valores.
・ O formato de imagem CMYK não é compatível com o recorte inteligente.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opção</strong></td> 
   <td><strong>Quando usar</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td>Cortar pixel</td> 
   <td>Imagens de corte em massa com base somente em dimensões.</td> 
   <td><p>Para usar essa opção, selecione <strong>Corte de pixels</strong> na lista suspensa Opções de corte .</p> <p>Para cortar das laterais de uma imagem, você insere o número de pixels para cortar de qualquer lado ou de cada lado da imagem. A quantidade de imagens cortadas depende da configuração ppi (pixels por polegada) no arquivo de imagem.</p> <p>Um corte de pixels do Perfil de imagem é renderizado da seguinte maneira:<br /> </p> 
    <ul> 
     <li>Os valores são Superior, Inferior, Esquerda e Direita.</li> 
     <li>A parte superior esquerda é considerada 0,0 e o corte de pixels é calculado a partir daí.</li> 
     <li>Ponto de partida do corte: A esquerda é X e a parte superior é Y</li> 
     <li>Cálculo horizontal: dimensão de pixel horizontal da imagem original menos Esquerda e depois menos Direita.</li> 
     <li>Cálculo vertical: altura vertical do pixel menos Superior e depois menos Inferior.</li> 
    </ul> <p>Por exemplo, suponha que você tenha uma imagem de 4000 x 3000 pixels. Você usa valores: Superior=250, Inferior=500, Esquerda=300, Direita=700.</p> <p>Do canto superior esquerdo (300.250), corte usando o espaço de preenchimento de (4000-300-700, 3000-250-500 ou 3000.2250).</p> </td> 
  </tr> 
  <tr> 
   <td>Corte inteligente</td> 
   <td>Imagens de corte em massa com base em seu ponto focal visual.</td> 
   <td><p>O Smart Crop usa o poder da inteligência artificial no Adobe Sensei para automatizar rapidamente o corte de imagens em massa. O Recorte inteligente detecta e recorta automaticamente o ponto focal em qualquer imagem para capturar o ponto de interesse pretendido, independentemente do tamanho da tela.</p> <p>Para usar o Recorte inteligente, selecione <strong>Corte inteligente</strong> na lista suspensa Opções de recorte , à direita de Recorte responsivo de imagem, ative (ative) o recurso.</p> <p>Os tamanhos padrão de ponto de interrupção Grande, Médio e Pequeno geralmente abrangem a gama completa de tamanhos que a maioria das imagens é usada em dispositivos móveis e tablets, desktops e banners. Se desejar, você pode editar os nomes padrão de Grande, Médio e Pequeno.</p> <p>Para adicionar mais pontos de interrupção, clique em <strong>Adicionar corte</strong>; para excluir um corte, clique no ícone Garbage Can .</p> </td> 
  </tr> 
  <tr> 
   <td>Amostra de cor e imagem</td> 
   <td>Gerar uma amostra de imagem em massa para cada imagem.</td> 
   <td><p><strong>Observação</strong>: O Smart Swatch não é compatível com o Dynamic Media Classic.</p> <p>Localize e gere automaticamente amostras de alta qualidade a partir de imagens de produto que mostram cor ou textura.</p> <p>Para usar a Amostra de cores e imagens, selecione <strong>Corte inteligente</strong> na lista suspensa Opções de recorte , à direita de Amostra de cor e imagem, ative (ative) o recurso. Insira um valor de pixel nas caixas de texto Largura e Altura .</p> <p>Embora todas as recortes de imagem estejam disponíveis no painel Representações , as amostras são usadas somente por meio do recurso Copiar URL . É necessário usar seu próprio componente de visualização para renderizar a amostra em seu site. (A exceção a essa regra são os banners de carrossel. O Dynamic Media fornece o componente de visualização para a amostra usada em banners de carrossel.)</p> <p><strong>Uso de amostras de imagem</strong></p> <p>O URL para amostras de imagem é direto:</p> <p><code>/is/image/company/&lt;asset_name&gt;:Swatch</code></p> <p>em que <code>:Swatch</code> é anexada à solicitação de ativo.</p> <p><strong>Uso de amostras de cores</strong></p> <p>Para usar amostras de cores, você cria uma <code>req=userdata</code> com o seguinte:</p> <p><code>/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata</code></p> <p>Por exemplo, o seguinte é um ativo de amostra no Dynamic Media Classic:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch</code></p> <p>e aqui está o ativo de amostra correspondente <code>req=userdata</code> URL:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata</code></p> <p>O <code>req=userdata</code> A resposta é a seguinte:</p> <p><code class="code">SmartCropDef=Swatch
       SmartCropHeight=200.0
       SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200
       SmartCropType=Swatch
       SmartCropWidth=200.0
       SmartSwatchColor=0xA56DB2</code></p> <p>Você também pode solicitar um <code>req=userdata</code> resposta no formato XML ou JSON, como nos seguintes exemplos de URL respectivos:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml</code></p><p><code>SmartSwatchColor</code></p><p></p></td></tr></tbody></table>

## Tirar nitidez da máscara {#unsharp-mask}

Você usa **Tirar nitidez da máscara** para ajustar um efeito de filtro de nitidez na imagem final com resolução reduzida. Você pode controlar a intensidade do efeito, o raio do efeito (medido em pixels) e um limite de contraste que é ignorado. Esse efeito usa as mesmas opções do filtro &quot;Tirar nitidez da máscara&quot; da Adobe Photoshop.

>[!NOTE]
A Tirar nitidez da máscara é aplicada apenas a representações baixadas dentro do PTIFF (tiff de pirâmide) que têm uma resolução reduzida de mais de 50%. Isso significa que as representações de maior porte dentro do PTIFF não são afetadas pela máscara de nitidez, enquanto representações de menor tamanho, como miniaturas, são alteradas (e mostram a máscara de nitidez).

Em **Tirar nitidez da máscara**, você tem as seguintes opções de filtragem:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opção</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td>Quantidade</td> 
   <td>Controla a quantidade de contraste aplicado aos pixels da borda. O padrão é 1,75. Para imagens de alta resolução, é possível aumentá-lo para 5. Pense em Quantia como uma medida de intensidade de filtro. O intervalo é de 0 a 5.</td> 
  </tr> 
  <tr> 
   <td>Raio</td> 
   <td>Determina o número de pixels em torno dos pixels de borda que afetam a nitidez. Para imagens de alta resolução, insira de 1 a 2. Um valor baixo aplica nitidez apenas aos pixels de borda; um valor alto aplica nitidez a uma faixa mais ampla de pixels. O valor correto depende da imagem. O valor padrão é 0,2. O intervalo é de 0 a 250.</td> 
  </tr> 
  <tr> 
   <td>Limite</td> 
   <td><p>Determina o intervalo de contraste a ser ignorado quando o filtro de máscara de nitidez for aplicado. Em outras palavras, essa opção determina o quão diferentes os pixels com nitidez devem ser da área ao redor antes de serem considerados pixels de borda e terem nitidez. Para evitar a introdução de ruído, experimente valores entre 0 e 255.</p> </td> 
  </tr> 
 </tbody> 
</table>

A nitidez é descrita em [Nitidez de imagens](/help/assets/assets/sharpening_images.pdf).

## Criação de perfis de imagem do Dynamic Media {#creating-image-profiles}

Para definir parâmetros de processamento avançados para outros tipos de ativos, consulte [Configuração do processamento de ativos](config-dms7.md#configuring-asset-processing).

**Para criar perfis de imagem do Dynamic Media**:

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de imagem]**.
1. Toque **[!UICONTROL Criar]** para adicionar um Perfil de imagem.
1. Insira um nome de perfil e valores para Tirar nitidez da máscara, recortar ou amostra, ou ambos.

   Você pode achar útil usar um nome de perfil específico para a finalidade pretendida. Por exemplo, se você quiser criar um perfil que gera amostras somente, onde o Recorte inteligente está desativado e a Amostra de cor e imagem está ativada, você pode usar o nome de perfil &quot;Amostras inteligentes&quot;.

   Consulte também [Opções de recorte inteligente e amostra inteligente](#crop-options) e [Tirar nitidez da máscara](#unsharp-mask).

   ![cortar](assets/crop.png)

1. Toque **[!UICONTROL Salvar]**. O perfil recém-criado aparece na lista de perfis disponíveis.

## Editar ou excluir perfis de imagem do Dynamic Media {#editing-or-deleting-image-profiles}

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de imagem]**.
1. Selecione o Perfil de imagem que deseja editar ou remover. Para editá-lo, selecione **[!UICONTROL Editar perfil de processamento de imagem]**. Para removê-lo, selecione **[!UICONTROL Excluir perfil de processamento de imagem]**.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Se estiver editando, salve as alterações. Se estiver excluindo, confirme se deseja remover o perfil.

## Aplicação de um perfil de imagem do Dynamic Media a pastas {#applying-an-image-profile-to-folders}

Ao atribuir um Perfil de imagem a uma pasta, qualquer subpasta herda automaticamente o perfil da pasta pai. Esse fluxo de trabalho significa que você pode atribuir somente um Perfil de imagem a uma pasta. Dessa forma, considere cuidadosamente a estrutura de pastas de onde você faz upload, armazena, usa e arquiva ativos.

Se você atribuiu um perfil de imagem diferente a uma pasta, o novo perfil substituirá o perfil anterior. Os ativos de pasta existentes anteriormente permanecem inalterados. O novo perfil é aplicado aos ativos que são adicionados à pasta posteriormente.

As pastas que têm um perfil atribuído a elas são indicadas na interface do usuário pelo nome do perfil que aparece no cartão.

Ao adicionar um recorte inteligente a um Perfil de imagem existente, você deve reacionar a variável [Fluxo de trabalho do Ativo de atualização DAM](assets-workflow.md) se desejar gerar culturas para ativos existentes no repositório de ativos.

Você pode aplicar Perfis de imagem a pastas específicas ou globalmente a todos os ativos.

### Aplicação de perfis de imagem do Dynamic Media a pastas específicas {#applying-image-profiles-to-specific-folders}

Você pode aplicar um Perfil de imagem a uma pasta de dentro do **[!UICONTROL Ferramentas]** ou, se estiver na pasta, em **[!UICONTROL Propriedades]**. Esta seção descreve como aplicar perfis de imagem a pastas de ambas as maneiras.

As pastas que têm um perfil já atribuído a elas são indicadas ao exibir do nome do perfil logo abaixo do nome da pasta.

#### Aplicação de perfis de imagem do Dynamic Media a pastas da interface do usuário de Perfis {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de imagem]**.
1. Selecione o Perfil de imagem que deseja aplicar a uma ou várias pastas.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Toque **[!UICONTROL Aplicar perfil de processamento às pastas]** e selecione a pasta ou várias pastas que deseja usar para receber os ativos carregados recentemente e toque/clique **[!UICONTROL Aplicar]**. As pastas que têm um perfil já atribuído a elas são indicadas ao exibir do nome do perfil logo abaixo do nome da pasta.

#### Aplicação de perfis de imagem do Dynamic Media a pastas de Propriedades {#applying-image-profiles-to-folders-from-properties}

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ativos]**. Em seguida, navegue até a pasta pai da pasta à qual deseja aplicar um Perfil de imagem.
1. Na pasta, toque na marca de seleção para selecioná-la e, em seguida, toque em **[!UICONTROL Propriedades]**.
1. Toque na guia **[!UICONTROL Perfis de imagem]**. Na lista suspensa **[!UICONTROL Nome do perfil]**, selecione o perfil e toque em **[!UICONTROL Salvar e fechar]**. As pastas que têm um perfil já atribuído a elas são indicadas ao exibir do nome do perfil logo abaixo do nome da pasta.

   ![chlimage_1-256](assets/chlimage_1-256.png)

### Aplicar um perfil de imagem do Dynamic Media globalmente {#applying-an-image-profile-globally}

Além de aplicar um perfil a uma pasta, também é possível aplicar um globalmente para que qualquer conteúdo carregado no AEM Assets em qualquer pasta tenha o perfil selecionado aplicado.

**Para aplicar um perfil de imagem do Dynamic Media globalmente**:

1. Siga uma das seguintes opções:

   * Navegar para **https://&lt;aem server=&quot;&quot;>/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam** e aplique o perfil e toque apropriados **Salvar**.

      ![chlimage_1-257](assets/chlimage_1-257.png)

   * Navegue até CRXDE Lite para o seguinte nó: `/content/dam/jcr:content`.

      Adicionar a propriedade `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` e tocar **[!UICONTROL Salvar tudo]**.

      ![configure_image_profiles](assets/configure_image_profiles.png)

## Edição do recorte inteligente ou da amostra inteligente de uma única imagem {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

>[!NOTE]
O Recorte inteligente está disponível somente no modo Dynamic Media - Scene7.

Você pode realinhar ou redimensionar manualmente a janela de recorte inteligente de uma imagem para refinar ainda mais seu ponto focal.

Depois de editar um recorte inteligente e salvar, a alteração é propagada em todos os locais em que você usa o recorte para as imagens específicas.

Você pode executar o recorte inteligente novamente para gerar as culturas adicionais, se necessário.

Consulte também [Edição de recorte inteligente ou amostra inteligente de várias imagens](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**Para editar o recorte inteligente ou a amostra inteligente de uma única imagem**:

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ativos]**, em seguida, na pasta que tem um recorte inteligente ou um Perfil de imagem de amostra inteligente aplicado a ele.
1. Abra o conteúdo tocando na pasta.
1. Toque na imagem com o recorte inteligente ou a amostra inteligente que você deseja ajustar.
1. Na barra de ferramentas, toque em **[!UICONTROL Corte inteligente]**.

1. Siga um destes procedimentos:

   * Próximo ao canto superior direito da página, arraste a barra de controle deslizante para a esquerda ou para a direita para aumentar ou diminuir a exibição da imagem, respectivamente.
   * Na imagem, arraste uma alça de canto para ajustar o tamanho da área visível do corte ou amostra.
   * Na imagem, arraste a caixa/amostra para um novo local. Você só pode editar amostras de imagens; amostras de cores são estáticas.
   * Acima da imagem, toque  **[!UICONTROL Reverter]** para desfazer todas as edições e restaurar o corte ou a amostra original.

1. Próximo ao canto superior direito da página, toque em **[!UICONTROL Salvar]** e toque em **[!UICONTROL Fechar]** para retornar à pasta de ativos.

## Edição de recorte inteligente ou amostra inteligente de várias imagens {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

Depois de aplicar um Perfil de imagem - contendo o Recorte inteligente - a uma pasta, todas as imagens dessa pasta terão um recorte aplicado a elas. Se desejar, é possível *manualmente* realinhar ou redimensionar a janela de recorte inteligente em várias imagens para refinar ainda mais seu ponto focal.

Depois de editar um recorte inteligente e salvar, a alteração é propagada em todos os locais em que você usa o recorte para as imagens específicas.

Você pode executar o recorte inteligente novamente para gerar as culturas adicionais, se necessário.

**Para editar o recorte inteligente ou a amostra inteligente de várias imagens**:

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ativos]**, em seguida, em uma pasta que tenha um recorte inteligente ou um Perfil de imagem de amostra inteligente aplicado a ele.
1. Na pasta , toque no **[!UICONTROL Mais ações]** ícone (..) e toque em **[!UICONTROL Corte inteligente]**.

1. No **[!UICONTROL Editar recortes inteligentes]** , siga um destes procedimentos:

   * Ajuste o tamanho de visualização das imagens na página.

      À direita da lista suspensa nome do ponto de interrupção, arraste a barra de controle deslizante para a esquerda ou para a direita para alterar o tamanho da exibição da imagem visível.

      ![edit_smart_measures-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filtre a lista de imagens visíveis com base nos nomes dos pontos de interrupção. No exemplo abaixo, as imagens são filtradas no nome do ponto de interrupção &quot;Médio&quot;.

      Próximo ao canto superior direito da página, na lista suspensa, selecione um nome de ponto de interrupção para filtrar quais imagens você vê. (Veja a imagem acima.)

      ![edit_smart_measures-dropdownlist](assets/edit_smart_crops-dropdownlist.png)

   * Redimensione a caixa de recorte inteligente. Siga um destes procedimentos:

      * Se a imagem tiver um recorte inteligente ou apenas uma amostra inteligente, arraste a alça do canto da caixa de recorte para ajustar o tamanho da área visível do recorte.
      * Se a imagem tiver um recorte inteligente e uma amostra inteligente, arraste a alça do canto da caixa de recorte para ajustar o tamanho da área visível do recorte. Ou toque ou clique na amostra inteligente abaixo da imagem (as amostras de cores são estáticas), em seguida, arraste a alça do canto da caixa de corte para ajustar o tamanho da área visível da amostra.

      ![Redimensionamento do recorte inteligente de uma imagem.](assets/edit_smart_crops-resize.png)

   * Mova a caixa de recorte inteligente. Siga um destes procedimentos:

      * Se a imagem tiver um recorte inteligente ou apenas uma amostra inteligente, arraste a caixa de recorte para um novo local.
      * Se a imagem tiver um recorte inteligente e uma amostra inteligente, arraste a caixa de recorte inteligente para um novo local. Ou toque na amostra inteligente abaixo da imagem (as amostras de cores são estáticas) e arraste a caixa de recorte de amostra inteligente para um novo local.

      ![edit_smart_measures-move](assets/edit_smart_crops-move.png)

   * Desfaça todas as suas edições e restaure o recorte inteligente original ou a amostra inteligente (aplica-se somente à sessão de edição atual).

      Toque **[!UICONTROL Reverter]** acima da imagem.

      ![edit_smart_measures-revert](assets/edit_smart_crops-revert.png)



1. Próximo ao canto superior direito da página, toque em **[!UICONTROL Salvar]**. em seguida **[!UICONTROL Fechar]** para retornar à pasta de ativos.

## Remover um perfil de imagem das pastas {#removing-an-image-profile-from-folders}

Ao remover um Perfil de imagem de uma pasta, qualquer subpasta herda automaticamente a remoção do perfil da pasta pai. No entanto, o processamento de arquivos que ocorreu dentro das pastas permanece intacto.

Você pode remover um Perfil de imagem de uma pasta de dentro do **[!UICONTROL Ferramentas]** ou, se estiver na pasta, em **[!UICONTROL Propriedades]**. Esta seção descreve como remover perfis de imagem de pastas de ambas as maneiras.

### Remoção de perfis de imagem do Dynamic Media de pastas por meio da interface do usuário de Perfis {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Ativos > Perfis de imagem]**.
1. Selecione o Perfil de imagem que deseja remover de uma pasta ou de várias pastas.
1. Toque em **[!UICONTROL Remover perfil de processamento das pastas]** e selecione uma ou várias pastas que deseja usar para remover o perfil e toque em **[!UICONTROL Remover]**.

   Você pode confirmar que o Perfil de imagem não é mais aplicado a uma pasta porque o nome não aparece mais abaixo do nome da pasta.

### Remoção de perfis de imagem do Dynamic Media de pastas por meio de propriedades {#removing-image-profiles-from-folders-via-properties}

1. Toque no logotipo do AEM e navegue **[!UICONTROL Ativos]** e, em seguida, na pasta da qual você deseja remover um Perfil de imagem.
1. Na pasta, toque na marca de seleção para selecioná-la e toque em **[!UICONTROL Propriedades]**.
1. Selecione o **[!UICONTROL Perfis de imagem]** guia .
1. No **[!UICONTROL Nome do perfil]** , selecione **[!UICONTROL Nenhum]** e toque em **[!UICONTROL Salvar e fechar]**.

   As pastas que têm um perfil já atribuído a elas são indicadas ao exibir do nome do perfil logo abaixo do nome da pasta.
