---
title: Organize seus ativos digitais
description: Organize seus ativos digitais, imagens, arquivos, pastas e assim por diante usando o Experience Manager.
contentOwner: AG
feature: Asset Management,Search
role: User
exl-id: 41e083b3-e956-4346-9a99-008de2c6a169
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 2%

---

# Organize seus ativos digitais {#organize-digital-assets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Todos os ativos digitais, metadados e conteúdo de documentos do Microsoft Office e PDF são extraídos e podem ser pesquisados. A pesquisa permite uma filtragem sofisticada em ativos e respeita totalmente as permissões apropriadas. Os metadados são abordados detalhadamente em metadados no Gerenciamento de ativos digitais.

[!DNL Experience Manager] O Assets é compatível com várias maneiras de organizar o conteúdo. Você pode organizá-las de maneira hierárquica usando pastas ou pode organizá-las de maneira não ordenada e ad hoc, usando, por exemplo, tags . Os usuários podem editar tags no Editor de ativos DAM, onde os ativos secundários, as representações e os metadados são exibidos.

## Organizar ativos em pastas {#organize-using-folders}

A maneira mais básica de organizar ativos é salvá-los em pastas. É análogo a organizar arquivos em pastas em nosso sistema de arquivos local. Para obter mais informações sobre como criar e gerenciar pastas, consulte [Gerenciar ativos](managing-assets-touch-ui.md). A forma como você nomeia arquivos e pastas, como organiza subpastas e como manipula os arquivos nessas pastas pode ter um impacto significativo na maneira como esses ativos são processados. Ao usar estratégias consistentes e apropriadas de nomenclatura de arquivos e pastas, juntamente com uma boa prática de metadados, você pode aproveitar ao máximo seu repositório de ativos digitais.

* Na maioria dos casos, o repositório de ativos digitais está sempre crescendo. Portanto, é importante formalizar o uso de metadados, a estrutura de pastas e a nomenclatura de arquivos no início do ciclo de criação de conteúdo.
* Use pastas somente para impor uma estrutura de armazenamento consistente para seus ativos digitais. Essa consistência ajuda a processar e gerenciar melhor seus ativos. Por exemplo, os ativos colocados nos seguintes tipos de pastas podem ajudar você a usar os [perfis para usar no processamento de ativos](processing-profiles.md):

   * **Pastas de desenvolvimento** - contém ativos digitais em que você está trabalhando no momento.
   * **Pastas de clientes** - contém ativos digitais com base em clientes ou nomes de projeto.
   * **Pastas primárias** - contém ativos originais digitais de origem.
   * **Pastas de representação** - contém representações e cópias dos ativos digitais originais e de origem.
   * **Pastas de tamanho de arquivo** - contém ativos digitais com base em tamanhos de arquivo pequenos, médios ou grandes.
   * **Pastas de preparo** - contém ativos digitais prontos para publicação ao vivo em seu site.
   * **Pastas de tipo MIME** - contém ativos digitais específicos para tipos MIME, como imagens, documentos e multimídia.
   * **Arquivar pastas** - contém ativos digitais descontinuados.
   * **Pastas baseadas em data** - contém ativos digitais com base em uma data de criação ou em uma data da última modificação.

* Crie um diretório de pastas que provavelmente não serão alteradas para que qualquer personalização ou automação continue a funcionar. Por exemplo, os perfis de processamento atribuídos continuam a funcionar.
* Se um ativo já estiver publicado, você usará [!DNL Experience Manager] para mover o ativo para outra pasta e republicar de seu novo local, o local do ativo publicado original ainda estará disponível, juntamente com o ativo republicado recentemente. O ativo publicado original, no entanto, é *perdido* para [!DNL Experience Manager] e não pode desfazer a publicação. Portanto, como prática recomendada, primeiro cancele a publicação de um ativo e depois o mova para uma pasta diferente.

## Organizar ativos usando tags {#use-tags-to-organize-assets}

Usando tags como metadados, você pode pesquisar ativos facilmente, criar coleções usando os resultados da pesquisa, aumentar a classificação de pesquisa para alguns ativos e aproveitar os algoritmos de IA da Adobe Sensei para a descoberta de ativos.

Os ativos Adobe Experience Manager usam um algoritmo de autoaprendizado para criar tags altamente descritivas que permitem encontrar o ativo certo em apenas alguns cliques. A marcação inteligente usa o Adobe Sensei, nossa inteligência artificial e estrutura de aprendizado de máquina, que pode ser treinada para reconhecer e aplicar tags padrão e específicas de negócios a imagens. As Tags inteligentes também podem identificar conteúdo, palavras individuais ou frases e aplicar automaticamente tags descritivas aos ativos

Para obter mais informações, consulte os seguintes artigos:

* [Sobre tags no AEM](/help/sites-authoring/tags.md)
* [Editar metadados de ativos](meta-edit.md)
* [Tags inteligentes aprimoradas no Assets](enhanced-smart-tags.md)

## Organizar como coleções {#organize-as-collections}

Com as coleções de ativos no Experience Manager Assets, você pode simplificar a capacidade de criar, editar e compartilhar ativos entre usuários. Crie vários tipos de coleções com base na maneira como você as usa, incluindo coleções que contêm uma lista de referência estática de ativos, pastas e coleções, bem como coleções que extrai ativos com base em critérios de pesquisa.  Você também pode criar coleções com ativos de diferentes locais e compartilhá-los com vários usuários com diferentes níveis de acesso, privilégios de visualização e edição.

Para obter mais informações, consulte [gerenciar coleções](managing-collections-touch-ui.md)

<!-- TBD items: add screenshots where applicable
Any hints/recommendations of when to use what method of organizing? Some examples of how organizing helps towards a better taxonomy and improved content velocity.
Add back links to blog posts by marketing?
-->

## Organize seus ativos para usar perfis {#organize-to-use-profiles}

Um perfil de processamento contém comandos de processamento de Ativos que se aplicam a ativos que são carregados em pastas predefinidas. Os perfis são usados para automatizar o processamento do conteúdo de uma pasta ou dos ativos carregados recentemente. Você pode aproveitar os perfis para organizar melhor seus ativos.

Padronizar o uso de metadados, a nomenclatura de arquivos e a estrutura de pastas garante que, à medida que seu conjunto de ativos digitais cresce, você possa aplicar perfis de processamento a pastas com maior precisão e consistência.

Para obter mais informações sobre vários perfis que você pode criar e gerenciar para processar ativos, consulte,

* [Perfis para processar metadados, imagens e vídeos](processing-profiles.md)
* [Perfis de metadados](metadata-profiles.md)
* [Perfis de vídeo](video-profiles.md)
* [Perfis de imagem do Dynamic Media](image-profiles.md)
