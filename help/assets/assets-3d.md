---
title: Trabalhar com ativos 3D
seo-title: Trabalhar com ativos 3D
description: Saiba como trabalhar com ativos 3D em AEM 3D
seo-description: Saiba como trabalhar com ativos 3D em AEM 3D
uuid: a1c1bb29-9d3d-4025-8142-ed9719434bf9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: 32143da1-09c8-45ce-b50d-32adf6efe383
translation-type: tm+mt
source-git-commit: 7c850ed0d20dd2ba2626242c67ba190e371f049f
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 6%

---


# Trabalhar com ativos 3D {#working-with-d-assets}

O AEM 3D (Adobe Experience Manager 3D) permite carregar, gerenciar, visualizar e renderizar conteúdo 3D. O suporte para visualização e renderização é otimizado para objetos individuais.

Consulte também as [Notas de lançamento do AEM 3D](/help/release-notes/aem3d-release-notes.md).

Consulte também [Instalação e configuração do AEM 3D](install-config-3d.md).

## Sobre modelos e estágios em AEM 3D {#about-models-and-stages-in-aem-d}

AEM 3D permite que você visualização e renderize modelos 3D estáticos e independentes de alta qualidade em ambientes predefinidos chamados Stages. Basicamente, uma etapa fornece &quot;iluminação&quot; para a cena 3D e as configurações para renderização em um aplicativo nativo, como Autodesk® Maya® ou Autodesk 3ds Max®. Além disso, opcionalmente, o palco pode incluir câmeras predefinidas, planos de fundo e geometria do plano de solo.

Os arquivos 3D carregados que contêm luzes são considerados um estágio. É possível reverter esses ativos para objetos 3D simples ao abrir o ativo na página de detalhes do ativo. Toque em Propriedades **[!UICONTROL da]** Visualização e, em seguida, toque na guia **[!UICONTROL Básico]** . No cabeçalho Metadados, na lista suspensa Classe de ativo, selecione o objeto **** 3D.

Ao criar modelos 3D para uso em AEM 3D, lembre-se do seguinte:

* Seus arquivos de modelo 3D devem conter apenas um objeto, sem planos de fundo, planos de fundo, iluminação de cena ou câmeras.
* Coloque o modelo acima do plano do solo. Esse posicionamento é especialmente importante quando você visualização ou renderiza estágios que fornecem um plano de solo. Uma configuração está disponível (e ativada por padrão) que faz com que o objeto seja movido acima do plano de solo ao visualizar ou renderizar com o Refinamento rápido. Essa configuração não afeta a renderização com renderizadores de terceiros (por exemplo, por meio de Maya) e, portanto, os objetos que não estão localizados acima do plano do solo podem estar parcialmente ocultos.
* Posicione o modelo de modo que fique razoavelmente centralizado lateralmente em torno da origem do sistema de coordenadas (0,0,0). Isso garante uma boa experiência de visualização interativa para você.
* Além de mapas de textura, as referências de arquivo externas são suportadas. Portanto, você deve incorporar qualquer conteúdo referenciado no arquivo de modelo primário antes de carregá-lo no AEM.

   Consulte [Sobre o upload e o processamento de ativos 3D no AEM](upload-processing-3d-assets.md).

* A iluminação geral da cena é fornecida pelo palco. Assim, o Adobe não recomenda incluir luzes com arquivos de modelo 3D. Você pode incluir luzes no modelo. No entanto, devem ser específicas apenas do modelo. Por exemplo, pode ser necessário incluir iluminação adicional para iluminar uma parte do objeto que é obscurecida por outras partes. Portanto, não seria suficientemente visível apenas com as luzes do palco.

## Arquivos suportados no AEM 3D {#supported-files-in-aem-d}

Um ativo 3D típico tem um arquivo de modelo primário e nenhum ou mais arquivos referenciados. Os arquivos referenciados incluem coisas como mapas de textura ou imagens **IBL (Image-Based Lighting)** .

### Sobre o arquivo de modelo 3D primário {#about-the-primary-d-model-file}

O arquivo de modelo 3D principal contém a geometria real do modelo 3D e as definições dos materiais (padrão) aplicados às superfícies do modelo. AEM 3D suporta os seguintes formatos de arquivo de modelo 3D principal:

* Formato de arquivo Wavefront OBJ (`.obj`)

   O formato OBJ requer um ou mais arquivos MTL externos separados (Biblioteca de modelos de materiais) (`.mtl`).

* Formato de arquivo Autodesk FBX (Filmbox) (`.fbx`)

   O formato de intercâmbio de ficheiros 3D do Autodesk; formatos binário e ASCII.

   Quando você cria arquivos FBX em aplicativos de terceiros, o Adobe recomenda as seguintes configurações (consulte a tabela abaixo). Essas configurações podem ajudá-lo a obter os melhores resultados para arquivos 3D que você pretende usar no AEM. Os nomes das opções são obtidos na caixa de diálogo Opções **[!UICONTROL de exportação para]** Autodesk Maya FBX.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opção na caixa de diálogo Exportar para Autodesk Maya FBX</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td>Preservar referências<br /> </td> 
   <td><p>Desmarcar.</p> <p>Atualmente, AEM 3D não suporta referências externas.</p> </td> 
  </tr> 
  <tr> 
   <td>Malha suave<br /> </td> 
   <td>Selecionar.</td> 
  </tr> 
  <tr> 
   <td>Converter superfícies NURBS em</td> 
   <td><strong>Malha de renderização de software</strong></td> 
  </tr> 
  <tr> 
   <td>Animação</td> 
   <td><p>Seleciona ou cancela a seleção.</p> <p>Se você optar por selecionar essa opção, AEM 3D ignorará as informações de animação no arquivo.</p> </td> 
  </tr> 
  <tr> 
   <td>Câmeras</td> 
   <td><p>Selecione para estágios <strong></strong>3D.</p> <p>Desmarque para modelos 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Luzes</td> 
   <td><p>Selecione para estágios <strong></strong>3D.</p> <p>Desmarque para modelos <strong></strong>3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Unidades - Automático</td> 
   <td>Selecionar. AEM 3D é convertido na importação.</td> 
  </tr> 
  <tr> 
   <td>Conversão de Eixo - Eixo Superior</td> 
   <td><p><strong>Y-up</strong></p> <p>O Y-up oferece resultados consistentes quando você exporta do Maya e é o sistema de coordenadas preferencial para arquivos FBX nesta versão AEM 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Incorporar mídia</td> 
   <td>Ambas as opções são suportadas. Se a opção incorporada estiver selecionada, AEM 3D extrai a mídia incorporada para uma pasta adjacente que tenha o mesmo nome do arquivo de modelo <code>.fbm</code> anexado a ela.</td> 
  </tr> 
  <tr> 
   <td>Formato de arquivo FBX - Tipo</td> 
   <td>Há suporte para <strong>Binário </strong>ou <strong>ASCII </strong>.</td> 
  </tr> 
  <tr> 
   <td>Formato de arquivo FBX - Versão</td> 
   <td>FBX 2014/2015 é recomendado. Outras versões também podem funcionar bem.</td> 
  </tr> 
 </tbody> 
</table>

Os seguintes formatos de arquivo adicionais são suportados se o Autodesk Maya estiver instalado e configurado nos servidores de criação AEM:

* Autodesk Maya

   Os formatos ASCII `.ma` e binário `.mb` .

* `Jupiter Tesselation (ISO 14306-1).jt`.

   Um formato de troca de dados CAD, colaboração e visualização de produto padrão do setor.

### Suporte para arquivos de mapa de textura {#support-for-texture-map-files}

As definições de material nos arquivos de modelo 3D podem incluir referências a arquivos de imagem externos que fornecem mapas de textura. AEM 3D suporta os seguintes tipos de arquivos de mapa de textura:

* Texturas coloridas difusas
* Texturas de cores especulares
* Texturas de cor ambiente
* Papéis de deslocamento (também chamados de mapas de relevo)
* Mapas normais
* Mapas de opacidade
* Mapas de aspereza (também chamados de Gloss, Refletivity, ou Cosine Power maps)

Os materiais no arquivo de modelo 3D principal podem fazer referência a outros tipos de mapas que são ignorados por AEM 3D.

### Imagens IBL (iluminação por imagem) {#ibl-image-based-lighting-images}

Um arquivo de modelo 3D que define um estágio pode fazer referência a uma única imagem de ambiente IBL. Atualmente, AEM 3D suporta apenas imagens TIFF de 32 bits em formato de latitude/longitude para IBL difuso e para reflexos. Para o plano de fundo de cena esférico, imagens RGB de 8 bits também são suportadas.

See [About working with IBL stages](working-with-ibl-stages.md).

>[!NOTE]
>
>Referências de arquivo - diferentes das descritas acima - que estão presentes no arquivo de modelo 3D principal são ignoradas no momento. AEM 3D não suporta referências a arquivos de modelo 3D secundários.
Y-up é o sistema de coordenadas preferencial para arquivos FBX nesta versão.

## Sombreamento de material em um arquivo de modelo 3D primário {#material-shading-in-a-primary-d-model-file}

O arquivo de modelo nativo original pode conter definições de material usadas com sombreadores como Cego, Lambert ou com sombreadores de procedimentos. Esses materiais potencialmente complexos são suportados apenas quando você renderiza usando o aplicativo nativo correspondente (como Autodesk Maya).

Para fins de visualização ou quando você renderiza usando o renderizador Rapid Refine™ padrão, todos os materiais são simplificados, substituídos ou ambos para que possam ser usados com um sombreador tipo Phong. Esse sombreador suporta um conjunto limitado de atributos. Outros atributos na definição do material são ignorados.

Consulte [Visualização de ativos 3D](viewing-3d-assets.md).

Consulte [Renderizar ativos 3D](rendering-3d-assets.md).

## Nomear materiais em um arquivo de modelo 3D primário {#naming-materials-in-a-primary-d-model-file}

Uma *superfície* é definida como a superfície de um modelo 3D coberto pelo mesmo material. Esse material também fornece o nome da superfície. Dessa forma, o Adobe recomenda que você nomeie os materiais incluídos nos arquivos de modelo 3D principais de acordo. Por exemplo, o uso de nomes específicos como &quot;Corpo&quot;, &quot;Windows&quot;, &quot;Pneus&quot; ou &quot;Arrependimentos&quot; é preferível ao uso de nomes vagos como &quot;Vermelho&quot;, &quot;Vidro&quot;, &quot;Borracha&quot;, &quot;Alumínio&quot;.

