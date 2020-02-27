---
title: Trabalhar com ativos do Adobe Dimension
seo-title: Trabalhar com ativos do Adobe Dimension
description: Trabalhar com ativos do Adobe Dimension no AEM 3D.
seo-description: Trabalhar com ativos do Adobe Dimension no AEM 3D.
uuid: 476e6758-b3a1-42ba-a18d-bfc407c6a72e
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 4a601c2a-4ea1-4308-8ae8-704155f63c21
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f

---


# Trabalhar com ativos do Adobe Dimension {#working-with-adobe-dimension-assets}

O pacote de recursos 3D do AEM fornece suporte para ativos do Adobe Dimension (`.dn` arquivos) em AEM Assets, AEM Sites e AEM Screens.

Um novo visualizador 3D baseado no padrão aberto glTF oferece recursos de visualização e visualização de Sites e Telas para ativos do Adobe Dimension.

## Sobre o serviço de conversão baseado em nuvem {#about-the-cloud-based-conversion-service}

Quando um ativo Dimension é carregado no AEM, uma cópia do arquivo é encaminhada para um serviço com base em nuvem gerenciado pela Adobe hospedado no Amazon AWS. Esse serviço converte do formato de arquivo Dimension proprietário da Adobe para o formato glTF padrão aberto. O modelo 3D convertido é empacotado como um glTF binário (`.glb`). O AEM armazena o modelo convertido com o ativo Dimensão principal como uma execução.

Você pode configurar o formato de `.glb` conversão de duas formas (consulte [Instalação e configuração do AEM 3D](install-config-3d.md) para obter instruções):

* Inclua extensões específicas da Adobe para maximizar a qualidade visual ao usar o visualizador Adobe glTF para exibir ativos de Dimensão nos ativos AEM, Sites AEM ou Telas AEM. Isso torna as execuções `.glb` incompatíveis com a maioria dos aplicativos de terceiros.
* Exclua extensões específicas da Adobe para obter compatibilidade da `.glb` execução com aplicativos de terceiros. Isso limita a qualidade visual ao exibir nos ativos AEM, Sites AEM ou Telas AEM (por exemplo, sem iluminação IBL) para simular a qualidade de aplicativos típicos de terceiros.

A transferência dos arquivos Dimension/glTF para ou do Amazon AWS e seu armazenamento temporário no AWS estão totalmente protegidos. Esses arquivos persistem no Amazon AWS por um tempo mínimo; normalmente, não mais do que alguns minutos durante operações normais.

Para habilitar o suporte para ativos Dimension, você deve obter credenciais da Adobe para acessar o serviço de conversão. See [Installing and configuring AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Se você instalar e usar as credenciais fornecidas, compreenderá e concordará que seus ativos 3D do Adobe Dimension serão transferidos para — e processados por — o serviço de conversão baseado em nuvem gerenciado pela Adobe hospedado no Amazon AWS.

### Exibir nos ativos AEM {#viewing-on-aem-assets}

O pacote de recursos 3D do AEM inclui um novo visualizador com base no padrão aberto glTF, usado para exibir ativos do Adobe Dimension. Esse visualizador é selecionado automaticamente ao abrir um arquivo de Dimensão ou um glTF compactado na exibição Detalhe nos ativos AEM ou com o componente 3D nos sites AEM.

Observe que a interface de usuário do visualizador glTF é um pouco diferente do visualizador 3D padrão, usado para todos os outros tipos de ativos 3D.

#### See also the following: {#see-also-the-following}

* [Notas](/help/release-notes/aem3d-release-notes.md) de versão do AEM 3D para restrições e limitações aplicáveis aos ativos do Dn e do visualizador glTF.
* [Trabalhar com o componente](using-the-3d-sites-component.md) Sites 3D para propriedades de componentes específicas aos ativos do Adobe Dimension.
* [Instalação e configuração do AEM 3D](install-config-3d.md) para configurar o serviço de conversão baseado em nuvem.

