---
title: Trabalhar com ativos AEM 3D
description: Saiba como trabalhar com ativos 3D no AEM 3D
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
exl-id: 3cee9b4f-c4be-4ffc-970c-5680c8ebba47
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 5%

---

# Trabalhar com ativos 3D AEM {#working-with-d-assets}

>[!IMPORTANT]
>
>AEM 3D no AEM 6.4 não é mais compatível. O Adobe recomenda usar o recurso de ativos 3D em [AEM como Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) ou [AEM 6.5.3 ou superior.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic)

O AEM 3D (Adobe Experience Manager 3D) permite carregar, gerenciar, visualizar e renderizar conteúdo 3D. O suporte para visualização e renderização é otimizado para objetos individuais.

Consulte também as [Notas de lançamento do AEM 3D](/help/release-notes/aem3d-release-notes.md).

Consulte também [Instalação e configuração do AEM 3D](install-config-3d.md).

## Sobre modelos e estágios em AEM 3D {#about-models-and-stages-in-aem-d}

AEM 3D permite visualizar e renderizar modelos 3D estáticos e independentes de alta qualidade em ambientes predefinidos chamados de Estágios. Basicamente, um estágio fornece &quot;iluminação&quot; para a cena 3D e as configurações de renderização em um aplicativo nativo, como o Autodesk® Maya® ou o Autodesk 3ds Max®. Além disso, opcionalmente, o palco pode incluir câmeras predefinidas, planos de fundo e geometria do plano base.

Arquivos 3D carregados que contêm luzes são considerados um estágio. Você pode reverter esses ativos para serem objetos 3D simples abrindo o ativo na página de detalhes do ativo. Toque em **[!UICONTROL Exibir propriedades]** e toque na guia **[!UICONTROL Básico]**. No cabeçalho Metadados , na lista suspensa Classe de ativo , selecione **[!UICONTROL 3D object]**.

Ao criar modelos 3D para uso em AEM 3D, esteja ciente do seguinte:

* Seus arquivos de modelo 3D devem conter apenas um objeto, sem planos de fundo, planos base, iluminação da cena ou câmeras.
* Coloque o modelo acima do plano base. Esse posicionamento é especialmente importante quando você visualiza ou renderiza palcos que fornecem um plano base. Uma configuração está disponível (e ativada por padrão) que faz com que o objeto seja movido para acima do plano base ao visualizar ou renderizar com o Rapid Refine. Essa configuração não afeta a renderização com renderizadores de terceiros (por exemplo, por meio do Maya) e, portanto, os objetos que não estão localizados acima do plano base podem estar parcialmente ocultos.
* Posicione o modelo de forma a que esteja razoavelmente centrado lateralmente em torno da origem do sistema de coordenadas (0,0,0). Isso garante uma boa experiência de visualização interativa para você.
* Além de mapas de textura, as referências de arquivo externo são compatíveis. Portanto, você deve incorporar qualquer conteúdo referenciado no arquivo de modelo principal antes de fazer upload no AEM.

   Consulte [Sobre o upload e o processamento de ativos 3D no AEM](upload-processing-3d-assets.md).

* A iluminação geral da cena é fornecida pelo palco. Assim, o Adobe não recomenda incluir luzes com arquivos de modelo 3D. Você pode incluir luzes no modelo. No entanto, eles devem ser específicos apenas do modelo. Por exemplo, pode ser necessário incluir iluminação adicional para iluminar uma parte do objeto que é obscurecida por outras partes. Portanto, não seria suficientemente visível apenas com as luzes de palco.

## Arquivos compatíveis no AEM 3D {#supported-files-in-aem-d}

Um ativo 3D típico tem um arquivo de modelo principal e nenhum ou mais arquivos referenciados. Os arquivos referenciados incluem coisas como mapas de textura ou imagens **IBL (iluminação baseada em imagem)**.

### Sobre o arquivo de modelo 3D principal {#about-the-primary-d-model-file}

O arquivo de modelo 3D principal contém a geometria real do modelo 3D e as definições dos materiais (padrão) aplicados às superfícies do modelo. AEM 3D suporta os seguintes formatos de arquivo de modelo 3D principal:

* Formato de arquivo Wavefront OBJ (`.obj`)

   O formato OBJ requer um ou mais arquivos MTL externos separados (Biblioteca de Modelos de Material) (`.mtl`).

* Formato de arquivo FBX do Autodesk (Filmbox) (`.fbx`)

   O formato de intercâmbio de ficheiros 3D do Autodesk; formatos binário e ASCII.

   Quando você cria arquivos FBX em aplicativos de terceiros, o Adobe recomenda as seguintes configurações (consulte a tabela abaixo). Essas configurações podem ajudá-lo a obter os melhores resultados para arquivos 3D que você pretende usar no AEM. Os nomes das opções são obtidos da caixa de diálogo **[!UICONTROL Opções de exportação FBX do Autodesk Maya]**.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opção na caixa de diálogo Exportar FBX do Autodesk Maya</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td>Preservar Referências<br /> </td> 
   <td><p>Desmarcar.</p> <p>AEM 3D atualmente não suporta referências externas.</p> </td> 
  </tr> 
  <tr> 
   <td>Malha Suave<br /> </td> 
   <td>Selecionar.</td> 
  </tr> 
  <tr> 
   <td>Converter superfícies NURBS em</td> 
   <td><strong>Malha de Renderização de Software</strong></td> 
  </tr> 
  <tr> 
   <td>Animação</td> 
   <td><p>Seleciona ou cancela a seleção.</p> <p>Se você optar por selecionar essa opção, AEM 3D ignorará as informações de animação no arquivo.</p> </td> 
  </tr> 
  <tr> 
   <td>Câmeras</td> 
   <td><p>Selecione para <strong>3D stage</strong>.</p> <p>Desmarque para modelos 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Luzes</td> 
   <td><p>Selecione para <strong>3D stage</strong>.</p> <p>Desmarque para <strong>3D models</strong>.</p> </td> 
  </tr> 
  <tr> 
   <td>Unidades - Automático</td> 
   <td>Selecionar. AEM 3D é convertido na importação.</td> 
  </tr> 
  <tr> 
   <td>Conversão de Eixo - Eixo para Cima</td> 
   <td><p><strong>Y-up</strong></p> <p>Y-up fornece resultados consistentes ao exportar do Maya e é o sistema de coordenadas preferido para arquivos FBX nesta versão AEM 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Incorporar mídia</td> 
   <td>Ambas as opções são compatíveis. Se a opção incorporada estiver selecionada, AEM 3D extrai a mídia incorporada para uma pasta adjacente que tenha o mesmo nome do arquivo de modelo com <code>.fbm</code> anexado a ela.</td> 
  </tr> 
  <tr> 
   <td>Formato de arquivo FBX - Tipo</td> 
   <td>Ambos <strong>Binário </strong>ou <strong>ASCII </strong>são suportados.</td> 
  </tr> 
  <tr> 
   <td>Formato de arquivo FBX - Versão</td> 
   <td>FBX 2014/2015 é recomendado. Outras versões também podem funcionar bem.</td> 
  </tr> 
 </tbody> 
</table>

Os formatos de arquivo adicionais a seguir são suportados se o Autodesk Maya estiver instalado e configurado nos servidores de criação de AEM:

* Autodesk Maya

   Os formatos ASCII `.ma` e binário `.mb`.

* `Jupiter Tesselation (ISO 14306-1).jt`.

   Um formato de troca de dados CAD padrão do setor, colaboração e visualização de produtos.

### Suporte para arquivos de mapa de textura {#support-for-texture-map-files}

As definições de material em arquivos de modelo 3D podem incluir referências a arquivos de imagem externos que fornecem mapas de textura. AEM 3D suporta os seguintes tipos de arquivos de mapa de textura:

* Texturas coloridas difusas
* Texturas coloridas especulares
* Texturas de cor ambiente
* Paps de deslocamento (também chamados de Bump maps)
* Mapas normais
* Mapas de opacidade
* Mapas de rugosidade (também chamados de Perda, Reflexidade ou Mapas de Energia Cosseno)

Os materiais no arquivo de modelo 3D principal podem fazer referência a outros tipos de mapas que são ignorados AEM 3D.

### Imagens IBL (iluminação baseada em imagem) {#ibl-image-based-lighting-images}

Um arquivo de modelo 3D que define um estágio pode fazer referência a uma única imagem de ambiente IBL. Atualmente, AEM 3D suporta apenas imagens TIFF de 32 bits no formato de latitude/longitude para IBL difuso e para reflexos. Para o fundo da cena esférica, imagens RGB de 8 bits também são compatíveis.

Consulte [Sobre como trabalhar com palcos IBL](working-with-ibl-stages.md).

>[!NOTE]
>
>Referências de arquivo - diferentes das descritas acima - que estão presentes no arquivo de modelo 3D principal são ignoradas no momento. AEM 3D não suporta referências a arquivos de modelo 3D secundários.
Y-up é o sistema de coordenadas preferido para arquivos FBX nesta versão.

## Sombreamento de material em um arquivo de modelo 3D primário {#material-shading-in-a-primary-d-model-file}

O arquivo de modelo nativo original pode conter definições de material usadas com sombreadores, como Cento, Lambert ou com sombreadores de procedimentos. Esses materiais potencialmente complexos são compatíveis somente quando você renderiza usando o aplicativo nativo correspondente (como o Autodesk Maya).

Para fins de visualização ou quando você renderiza usando o renderizador Rapid Refine™ padrão, todos os materiais são simplificados, substituídos ou ambos para que possam ser usados com um sombreador tipo Phong. Esse sombreador suporta um conjunto limitado de atributos. Outros atributos na definição do material são ignorados.

Consulte [Visualização de ativos 3D](viewing-3d-assets.md).

Consulte [Renderizar ativos 3D](rendering-3d-assets.md).

## Nomear materiais em um arquivo de modelo 3D primário {#naming-materials-in-a-primary-d-model-file}

Um *superfície* é definido como a superfície de um modelo 3D coberto pelo mesmo material. Esse material também fornece o nome da superfície. Dessa forma, o Adobe recomenda que você nomeie os materiais incluídos nos arquivos de modelo 3D principais de acordo. Por exemplo, o uso de nomes específicos como &quot;Corpo&quot;, &quot;Windows&quot;, &quot;Pneus&quot; ou &quot;Rims&quot; é preferível ao uso de nomes vagos como &quot;Vermelho&quot;, &quot;Vidro&quot;, &quot;Borracha&quot;, &quot;Alumínio&quot;.
