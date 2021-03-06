---
title: Suporte para metadados IPTC
description: Saiba como o Adobe Experience Manager Assets suporta metadados IPTC, classificações criativas e palavras-chave adicionadas a ativos por meio do Adobe Bridge e outros aplicativos criativos.
contentOwner: AG
feature: Metadata
role: User,Admin,Leader
exl-id: 3e22e8e4-3675-4d6d-94f4-fc1a4d4801e8
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 7%

---

# Suporte para metadados IPTC {#support-for-iptc-metadata}

Saiba como o Adobe Experience Manager Assets suporta metadados IPTC, classificações criativas e palavras-chave adicionadas a ativos por meio do Adobe Bridge e outros aplicativos criativos.

O Adobe Experience Manager Assets é compatível com o padrão de metadados IPTC, usado amplamente para descrever ativos. Dessa forma, [!DNL Experience Manager Assets] melhora a aceitação de suas imagens entre vários partidos, incluindo fotógrafos, agências criativas, bibliotecas, museus e assim por diante.

O esquema de metadados padrão para ativos agora incorpora os esquemas de metadados IPTC Core e IPTC Extension para definir propriedades abrangentes de metadados que permitem aos usuários adicionar dados precisos e confiáveis sobre pessoas, locais e produtos mostrados em uma imagem. Também oferece suporte a datas, nomes e identificadores relacionados à criação da imagem e a uma maneira flexível de expressar informações de direitos.

A página Propriedades dos ativos agora inclui guias separadas para exibir os metadados da Extensão IPTC principal e IPTC em campos editáveis.

1. Na interface do usuário do Assets, selecione uma imagem.
1. Clique ou toque no ícone **[!UICONTROL Propriedades]** na barra de ferramentas.
1. Na página Propriedades , clique/toque na guia **[!UICONTROL IPTC]** para exibir os metadados IPTC do ativo.
1. Edite as propriedades de metadados IPTC, conforme necessário.

   ![iptc_tab](assets/iptc_tab.png)

1. Clique/toque na guia **[!UICONTROL Extensão IPTC]** para exibir os metadados da Extensão IPTC do ativo.
1. Edite as propriedades de metadados da Extensão ITPC , conforme necessário.
1. Toque/clique em **[!UICONTROL Salvar e fechar]** para salvar as alterações.

## Suporte para Classificação criativa {#creative-rating-support}

Além de exibir classificações de usuários individuais e classificações agregadas, a página Propriedades agora exibe as classificações atribuídas aos ativos por meio do Adobe Bridge e de outros aplicativos de criação

Essas classificações estão disponíveis na seção **[!UICONTROL Classificação criativa]**, na guia **[!UICONTROL Avançado]**.

Essa classificação é uma propriedade somente leitura e varia entre 1 e 5. Você pode pesquisar ativos com base em sua Classificação criativa no Painel de pesquisa.

No entanto, essa propriedade não está indexada no momento para evitar qualquer conflito com as alterações personalizadas feitas pelos usuários.

## Suporte a palavra-chave {#keyword-support}

A guia **[!UICONTROL IPTC]** da página Propriedades também exibe as palavras-chave adicionadas aos ativos por meio do Adobe Bridge e de outros aplicativos criativos. Também é possível editar essas palavras-chave e adicionar mais palavras-chave na guia **[!UICONTROL IPTC]**.

![keywords](assets/keywords.png)
