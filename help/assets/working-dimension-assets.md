---
title: Trabalhar com ativos da Adobe Dimension
description: Trabalhar com ativos da Adobe Dimension no AEM 3D.
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: be8f6361-607d-4529-aef0-e8978dfd04b4
feature: Ativos 3D
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Trabalhar com ativos da Adobe Dimension {#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>O pacote de recursos AEM 3D no AEM 6.4 não é mais suportado. O Adobe recomenda usar o recurso de ativos 3D em [AEM como Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) ou [AEM 6.5.3 ou superior.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) ao trabalhar com ativos Adobe Dimension.

O pacote de recursos AEM 3D oferece suporte a ativos Adobe Dimension (`.dn` arquivos) no AEM Assets , AEM Sites e AEM Screens.

Um novo visualizador 3D baseado no padrão de abertura glTF oferece recursos de visualização e Sites e Screens para ativos do Adobe Dimension.

## Sobre o serviço de conversão baseado em nuvem {#about-the-cloud-based-conversion-service}

Quando um ativo do Dimension é carregado no AEM, uma cópia do arquivo é encaminhada para um serviço baseado em nuvem gerenciado pelo Adobe hospedado no Amazon AWS. Esse serviço é convertido do formato de arquivo Dimension proprietário do Adobe para o formato glTF padrão aberto. O modelo 3D convertido é empacotado como um glTF binário (`.glb`). O AEM armazena o modelo convertido com o ativo Dimension principal como uma representação.

Você pode configurar o formato de conversão `.glb` usando uma de duas maneiras (consulte [Instalar e configurar AEM 3D](install-config-3d.md) para obter instruções):

* Inclua extensões específicas do Adobe para maximizar a qualidade visual ao usar o visualizador Adobe glTF para exibir ativos do Dimension no AEM Assets, AEM Sites ou AEM Screens. Isso torna as representações `.glb` incompatíveis com a maioria dos aplicativos de terceiros.
* Exclua extensões específicas do Adobe para obter compatibilidade da renderização `.glb` com aplicativos de terceiros. Isso limita a qualidade visual ao visualizar no AEM Assets, AEM Sites ou AEM Screens (por exemplo, sem iluminação IBL) para simular a qualidade de aplicativos típicos de terceiros.

A transferência dos arquivos Dimension/glTF de ou para o Amazon AWS e seu armazenamento temporário no AWS são totalmente protegidos. Esses arquivos persistem no Amazon AWS por um período mínimo; normalmente, não mais do que alguns minutos durante as operações normais.

Para habilitar o suporte para ativos Dimension, você deve obter credenciais do Adobe para acessar o serviço de conversão. Consulte [Instalar e configurar AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Se você instalar e usar as credenciais fornecidas, você entenderá e concordará que seus ativos 3D da Adobe Dimension serão transferidos para — e processados por — o serviço de conversão baseado em nuvem e gerenciado pelo Adobe hospedado no Amazon AWS.

### Visualização no AEM Assets {#viewing-on-aem-assets}

O pacote de recursos AEM 3D inclui um novo visualizador com base no padrão de abertura glTF usado para exibir ativos Adobe Dimension. Esse visualizador é selecionado automaticamente ao abrir um arquivo Dimension ou um glTF compactado na exibição Detalhes no AEM Assets ou com o componente 3D no AEM Sites.

Observe que a interface do usuário do visualizador glTF é um pouco diferente do visualizador 3D padrão usado para todos os outros tipos de ativos 3D.

#### Consulte também o seguinte: {#see-also-the-following}

* [AEM notas de versão 3D ](/help/release-notes/aem3d-release-notes.md) para restrições e limitações aplicáveis a ativos Dn e o visualizador glTF.
* [Trabalhar com o ](using-the-3d-sites-component.md) componente Sites 3D para propriedades de componentes específicas dos ativos do Adobe Dimension.
* [Instalação e configuração do AEM 3](install-config-3d.md) Para configurar o serviço de conversão baseado em nuvem.
