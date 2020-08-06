---
title: Compare os recursos disponíveis no AEM Assets e na Biblioteca de mídia AEM
description: Perguntas frequentes sobre a AEM Assets e a Biblioteca de mídia AEM, incluindo as diferenças.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 1%

---


# AEM Assets vs. AEM MediaLibrary {#aem-assets-vs-aem-medialibrary}

O Adobe Experience Manager (AEM) Assets é parte integrante da plataforma AEM. Essa integração suave é considerada uma grande vantagem da AEM e garante consistência na gestão de conteúdo e alta produtividade para os autores de conteúdo.

## Perguntas frequentes {#frequently-asked-questions}

### O que é o AEM Assets? {#what-is-aem-assets}

O AEM Assets é um aplicativo da plataforma AEM que permite que nossos clientes gerenciem seus ativos digitais (imagens, vídeos, documentos e clipes de áudio) em um repositório baseado na Web. A AEM Assets inclui suporte a metadados, execuções, o Digital Asset Management Finder e a interface do usuário de administração da AEM Assets.

### O que é a Biblioteca de mídia AEM? {#what-is-the-aem-media-library}

A Biblioteca de mídia AEM é uma parte designada do repositório de conteúdo AEM WCM, onde as imagens e outros recursos compartilhados são armazenados. A Biblioteca de mídia usa os recursos de Gerenciamento de ativos digitais AEM WCM.

### O que eu recebo da AEM Assets que não faz parte AEM WCM? {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

Os recursos exclusivos que estão disponíveis somente para clientes da AEM Assets são:

1. a capacidade de extrair e editar metadados diferentes de título, tags e descrição.
1. o Administrador do AEM Assets, disponível na tela de boas-vindas, clicando no segundo botão ao lado do `siteadmin`.
1. Todas as etapas do fluxo de trabalho relacionadas ao Gerenciamento de ativos digitais, AEM inclusão de ativos, exclusão do AEM Assets, tratamento de subativos do AEM Assets, extração de metadados do AEM Assets.
1. bibliotecas incluindo o espaço do pacote `dam` im.

O uso desses recursos requer uma licença válida do AEM Assets.

### A AEM Assets está disponível como um pacote separado? {#is-aem-assets-available-as-a-separate-package}

Não. Para facilitar a instalação e a implantação, todos os aplicativos e complementos AEM são fornecidos em um único pacote com todas as funcionalidades incluídas. Isso não implica que você tenha permissão para usar todos os recursos do pacote.

#### Quero editar metadados de ativos digitais. Preciso de AEM Assets? {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

Se você estiver planejando editar metadados diferentes de título, descrição e tags, é necessário licenciar a AEM Assets.

#### Desejo redimensionar automaticamente as imagens após a importação. Preciso de AEM Assets? {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

Não. A redimensionamento e a transformação automática, orientada por fluxo de trabalho, de imagens estáticas, bem como a capacidade de gerenciar execuções fazem parte AEM Biblioteca de mídia. Esses recursos não exigem uma licença da AEM Assets.

### Desejo redimensionar imagens usando um componente de imagem personalizado. Preciso de AEM Assets? {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

O componente de imagem faz parte AEM WCM. A biblioteca de gráficos que está sendo usada pelo componente de imagem (mas também pela AEM Assets) faz parte da plataforma AEM e não exige uma licença da AEM Assets.

### Como posso impedir que meus usuários usem o AEM Assets se eu não licenciei o AEM Assets? {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

Você pode remover todos os workflows, componentes, taxonomias, opções e o administrador da AEM Assets específicos da AEM Assets da AEM. Isso evita que os usuários usem acidentalmente recursos do AEM Assets que você não licenciou.

### Quero adicionar imagens a uma página e cortar e redimensionar essas imagens. Preciso de AEM Assets? {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

Nesse caso de uso, não é necessário comprar o AEM Assets, nem mesmo o uso da Biblioteca de mídia é necessário para usar imagens em um site, já que o componente de imagem inteligente permite o upload de imagens diretamente na página.

>[!MORELIKETHIS]
>
>* [lista detalhada das diferenças de recursos](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)

