---
title: Compare os recursos disponíveis nos ativos AEM e na biblioteca de mídia do AEM
description: Perguntas frequentes sobre os ativos AEM e a biblioteca de mídia do AEM, incluindo as diferenças.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968

---


# AEM Assets vs. AEM MediaLibrary {#aem-assets-vs-aem-medialibrary}

Os ativos Adobe Experience Manager (AEM) são parte integrante da plataforma AEM. Essa integração suave é considerada uma grande vantagem do AEM e garante consistência na gestão de conteúdo e alta produtividade para os autores de conteúdo.

## Perguntas frequentes {#frequently-asked-questions}

### O que é o AEM Assets? {#what-is-aem-assets}

Os ativos AEM são um aplicativo da plataforma AEM que permite que nossos clientes gerenciem seus ativos digitais (imagens, vídeos, documentos e clipes de áudio) em um repositório baseado na Web. Os ativos AEM incluem suporte a metadados, execuções, o Localizador de gerenciamento de ativos digitais e a interface de usuário de administração do AEM Assets.

### O que é a biblioteca de mídia do AEM? {#what-is-the-aem-media-library}

A Biblioteca de mídia do AEM é uma parte designada do repositório de conteúdo do WCM do AEM, onde as imagens e outros recursos compartilhados são armazenados. A Biblioteca de mídia usa os recursos de Gerenciamento de ativos digitais do WCM AEM.

### O que obtenho dos ativos AEM que não fazem parte do WCM AEM? {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

Os recursos exclusivos que estão disponíveis somente para clientes do AEM Assets são:

1. a capacidade de extrair e editar metadados diferentes de título, tags e descrição.
1. o Admin do AEM Assets, disponível na tela de boas-vindas, clicando no segundo botão ao lado do `siteadmin`.
1. Todas as etapas do fluxo de trabalho relacionadas ao Gerenciamento de ativos digitais, ou seja, a inclusão de ativos AEM, a exclusão de ativos AEM, o gerenciamento de subativos AEM Assets, a extração de metadados do AEM Assets.
1. bibliotecas incluindo o espaço do pacote `dam` im.

O uso desses recursos requer uma licença válida dos ativos AEM.

### Os ativos AEM estão disponíveis como um pacote separado? {#is-aem-assets-available-as-a-separate-package}

Não. Para facilitar a instalação e a implantação, todos os aplicativos e complementos AEM são fornecidos em um único pacote com todas as funcionalidades incluídas. Isso não implica que você tenha permissão para usar todos os recursos do pacote.

#### Quero editar metadados de ativos digitais. Preciso dos ativos AEM? {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

Se você estiver planejando editar metadados diferentes de título, descrição e tags, é necessário licenciar os ativos AEM.

#### Desejo redimensionar automaticamente as imagens após a importação. Preciso dos ativos AEM? {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

Não. A redimensionamento e a transformação automática de imagens estáticas por fluxo de trabalho, bem como a capacidade de gerenciar execuções, fazem parte da Biblioteca de mídia do AEM. Esses recursos não exigem uma licença do AEM Assets.

### Desejo redimensionar imagens usando um componente de imagem personalizado. Preciso dos ativos AEM? {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

O componente de imagem faz parte do AEM WCM. A biblioteca de gráficos que está sendo usada pelo componente de imagem (mas também pelos ativos AEM) faz parte da plataforma AEM e não exige uma licença dos ativos AEM.

### Como impedir que meus usuários usem ativos AEM se eu não licenciei ativos AEM? {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

Você pode remover do AEM todos os workflows, componentes, taxonomias, opções e o administrador do AEM Assets específicos. Isso impede que os usuários usem acidentalmente os recursos do AEM Assets que você não licenciou.

### Quero adicionar imagens a uma página e cortar e redimensionar essas imagens. Preciso dos ativos AEM? {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

Para esse caso de uso, não é necessário comprar ativos AEM, nem mesmo o uso da Biblioteca de mídia é necessário para usar imagens em um site, já que o componente de imagem inteligente permite o upload de imagens diretamente na página.

>[!MORELIKETHIS]
>
>* [lista detalhada das diferenças de recursos](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)

