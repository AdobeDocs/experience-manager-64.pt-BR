---
title: Suporte para metadados IPTC
description: Saiba como o Adobe Experience Manager (AEM) Assets suporta os metadados IPTC, as avaliações criativas e as palavras-chave adicionadas aos ativos por meio do Adobe Bridge e de outros aplicativos de criação.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 7%

---


# Suporte para metadados IPTC {#support-for-iptc-metadata}

Saiba como o Adobe Experience Manager (AEM) Assets suporta os metadados IPTC, as avaliações criativas e as palavras-chave adicionadas aos ativos por meio do Adobe Bridge e de outros aplicativos de criação.

O Adobe Experience Manager (AEM) Assets suporta o padrão de metadados IPTC que é amplamente usado para descrever ativos. Dessa forma, a AEM Assets aprimora a aceitação de suas imagens entre vários partidos, incluindo fotógrafos, agências de criação, bibliotecas, museus e assim por diante.

O schema de metadados padrão para ativos agora incorpora os schemas de metadados IPTC Core e IPTC Extension para definir propriedades abrangentes de metadados que permitem que os usuários adicionem dados precisos e confiáveis sobre pessoas, locais e produtos mostrados em uma imagem. Também oferece suporte a datas, nomes e identificadores relacionados à criação da imagem, além de uma maneira flexível de expressar informações de direitos.

A página Propriedades dos ativos agora inclui guias separadas para exibir os metadados IPTC Core e IPTC Extension em campos editáveis.

1. Na interface do usuário Ativos, selecione uma imagem.
1. Clique ou toque no ícone **[!UICONTROL Propriedades]** na barra de ferramentas.
1. Na página Propriedades, clique/toque na guia **[!UICONTROL IPTC]** para visualização de metadados IPTC do ativo.
1. Edite as propriedades de metadados IPTC, conforme necessário.

   ![iptc_tab](assets/iptc_tab.png)

1. Clique/toque na guia **[!UICONTROL Extensão IPTC]** para exibir os metadados da Extensão IPTC do ativo.
1. Edite as propriedades de metadados da Extensão do ITPC, conforme necessário.
1. Tap/click **[!UICONTROL Save &amp; Close]** to save the changes.

## Suporte para classificação criativa {#creative-rating-support}

Além de exibir classificações individuais de usuários e classificações de agregação, a página Propriedades agora exibe as classificações atribuídas aos ativos por meio do Adobe Bridge e de outros aplicativos criativos

Essas classificações estão disponíveis na seção **[!UICONTROL Classificação criativa]**, na guia **[!UICONTROL Avançado]**.

Essa classificação é uma propriedade somente leitura e varia entre 1 e 5. Você pode pesquisar ativos com base em sua Classificação criativa no Painel de pesquisa.

No entanto, essa propriedade não está indexada no momento para evitar conflitos com as alterações personalizadas feitas pelos usuários.

## Suporte a palavra-chave {#keyword-support}

A guia **[!UICONTROL IPTC]** da página Propriedades também exibe palavras-chave adicionadas aos ativos por meio do Adobe Bridge e de outros aplicativos criativos. Você também pode editar essas palavras-chave e adicionar mais palavras-chave na guia **[!UICONTROL IPTC]** .

![keywords](assets/keywords.png)

