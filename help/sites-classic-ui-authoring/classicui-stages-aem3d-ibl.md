---
title: Sobre o trabalho com palcos IBL
seo-title: Sobre o trabalho com palcos IBL
description: O AEM 3D oferece suporte à iluminação baseada em imagem (IBLS) para a visualização interativa e a renderização com o renderizador integrado Adobe Rapid Refine e renderizadores de terceiros. É possível criar palcos IBL com ferramentas de criação comuns, como o Autodesk Maya ou o Autodesk 3ds Max.
seo-description: O AEM 3D oferece suporte à iluminação baseada em imagem (IBLS) para a visualização interativa e a renderização com o renderizador integrado Adobe Rapid Refine e renderizadores de terceiros. É possível criar palcos IBL com ferramentas de criação comuns, como o Autodesk Maya ou o Autodesk 3ds Max.
uuid: 6598fb8a-65b0-4b84-8063-fdc94f6ea935
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: f9291151-851a-4aff-a50e-a24330ee0c13
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 77%

---


# Sobre o trabalho com palcos IBL{#about-working-with-ibl-stages}

O AEM 3D oferece suporte à iluminação baseada em imagem (IBLS) para a visualização interativa e a renderização com o renderizador integrado Adobe Rapid Refine™ e renderizadores de terceiros. É possível criar palcos IBL com ferramentas de criação comuns, como o Autodesk® Maya® ou o Autodesk® 3ds Max®.

## Imagens para IBL {#images-for-ibl}

As imagens usadas na iluminação baseada em imagem devem conter HDR para a obtenção de melhores resultados. Devem estar no formato de latitude/longitude com mapeamento esférico e cobertura total do ambiente.

Atualmente, o AEM 3D oferece suporte somente a TIFFs de 32 bits. Se necessário, use o Adobe Photoshop ou uma ferramenta semelhante para converter a imagem com HDR em TIFF usando as seguintes configurações na caixa de diálogo Exportar para TIFF do Adobe Photoshop:

* **[!UICONTROL Profundidade]** de bits - 32 bits (flutuante)
* **[!UICONTROL Ordem]** de pixels - intercalada (RGBRGB)
* **[!UICONTROL Compactação]** de imagem - LZW
* **[!UICONTROL Ordem]** de bytes - PC IBM

Embora uma única imagem com HDR geralmente seja suficiente para os palcos IBL, o AEM 3D oferece controle adicional sobre os efeitos de IBL, permitindo até três imagens separadas:

* **[!UICONTROL Imagem do ambiente de iluminação difusa]** - esse tipo de imagem deve ser uma imagem HDR, mas pode ser relativamente pequena, pois a imagem será bastante filtrada antes de ser usada para iluminação difusa.
* **[!UICONTROL Imagem do ambiente de reflexo]** - esse tipo de imagem é usado para criar reflexos nas superfícies dos objetos. Pode ser uma imagem RGB de 8 bits padrão com tamanho e resolução que forneçam a qualidade e a nitidez desejadas para os reflexos. Se uma imagem HDR for especificada, o AEM 3D a converterá em RGB de 8 bits antes de usar um algoritmo proprietário.
* **[!UICONTROL Imagem do ambiente de fundo]** - esse tipo de imagem é usado como um plano de fundo. Pode ser uma imagem RGB de 8 bits padrão e deve ter o tamanho, a resolução e o nível de detalhe desejados para o plano de fundo do palco. Se uma imagem HDR for especificada, o AEM 3D a converterá em RGB de 8 bits usando um algoritmo proprietário.

>[!NOTE]
>O algoritmo de conversão pode ter dificuldade com determinadas imagens IBL. Isso pode resultar em planos de fundo muito claros ou muito saturados na Visualização ou ao renderizar com o Rapid Refine. Nesses casos, a Adobe recomenda a utilização do Photoshop, ou de uma ferramenta semelhante, para converter manualmente a imagem IBL em uma imagem RGB de 8 bits. Faça upload dessa imagem separadamente e a adicione-a ao palco como a Imagem do ambiente de fundo. As imagens do ambiente de iluminação difusa e de reflexo sempre devem ser TIFF de 32 bits.


## Ajustar a aparência do palco IBL {#adjusting-the-ibl-stage-appearance}

É possível refinar a aparência do palco IBL com as seguintes propriedades de palco:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propriedade</strong><br /> </td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td>Detalhes do sol IBL</td> 
   <td><p>Permite ajustar a direção e a intensidade da fonte de luz suplementar que simula o sol. <span class="diff-html-added">Essa fonte de luz aumenta o brilho da iluminação e faz com que o objeto projete uma sombra projetada no plano do solo. A projeção de sombra é suportada ao renderizar com o Rapid Refine e ao visualizar com o Google Chrome. No entanto, não é suportada atualmente por outros navegadores.</span></p> 
    <ul> 
     <li><strong>lat</strong> - A posição vertical da fonte de luz solar (<code>0.0</code>-<code>1.0</code>).<br /> Uma definição de <code>0.0</code> está no horizonte (centro vertical da Imagem do Ambiente de Iluminação Difusa); <code>1.0</code> está no ápice (margem superior da Imagem do Ambiente de Iluminação Difusa).</li> 
     <li><strong>long</strong> - A posição horizontal da fonte de luz solar (<code>0.0</code>-<code>1.0</code>).<br /> Uma configuração de 0,0 corresponde à esquerda; 1,0 equivale à extrema direita da Imagem do ambiente de iluminação difusa.<br /> </li> 
     <li><strong>claro</strong> - O brilho da fonte de luz solar. Aumente esse valor para clarear a fonte de luz solar; diminua-o para escurecer. <br /> Uma configuração de <code>0</code> desativa a iluminação suplementar e desativa as sombras projetadas. O parâmetro não afeta os reflexos do ambiente.<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Altura da câmera IBL</td> 
   <td>Se o fundo IBL parecer distorcido perto do horizonte, é possível reduzir ou eliminar a distorção ajustando essa propriedade. <br /> </td> 
  </tr> 
  <tr> 
   <td>Iluminação do Ambiente</td> 
   <td><p><span class="diff-html-added">Permite controlar a iluminação difusa. Talvez seja necessário ajustar manualmente essa propriedade para corrigir o brilho da luz se a Imagem do ambiente de iluminação difusa for excepcionalmente clara ou escura (por exemplo, cenários noturnos).</span></p> 
    <ul> 
     <li><strong>r, g, b</strong> - Atualmente não utilizado.</li> 
     <li><strong>bright</strong> - Multiplicador <span class="diff-html-added">de brilho. Aumentar ou diminuir esse valor aumenta ou diminui a intensidade da luz geral (tanto a iluminação básica de IBL quanto o brilho da fonte de luz solar).</span></li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

