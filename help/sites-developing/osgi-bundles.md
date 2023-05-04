---
title: Pacotes OSGI
seo-title: OSGI Bundles
description: Dicas para gerenciar seus pacotes OSGi
seo-description: Tips for managing your OSGi bundles
uuid: 07af7089-a233-4e5b-928c-76ddc0af8839
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8d3374ac-51dd-4ff5-84c9-495c937ade12
exl-id: 19df20a9-7c89-4dfa-8eca-81c4a14c21ff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---

# Pacotes OSGI{#osgi-bundles}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Usar controle de versão semântico {#use-semantic-versioning}

É possível encontrar as práticas recomendadas para a numeração semântica de versões acordadas em [https://semver.org/](https://semver.org/).

## Não incorpore mais classes e jars do que o estritamente necessário em pacotes OSGi {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}

As bibliotecas comuns devem ser transformadas em pacotes separados. Isso permitirá que elas sejam reutilizadas em seus pacotes. Quando quebrar uma *JAR* em um pacote OSGI, verifique as fontes online para ver se alguém já fez isso antes. Alguns locais comuns para encontrar os invólucros de pacote existentes são: Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse Bundle Recipes e o SpringSource Enterprise Bundle Repository.

## Depende das versões de pacote mais baixas necessárias {#depend-on-the-lowest-needed-bundle-versions}

Para compilar dependências de tempo em arquivos POM, sempre dependa da versão mais baixa necessária que expõe a API necessária. Isso permitirá maior compatibilidade com versões anteriores e facilitará as correções de backporting para versões mais antigas.

## Exportar um conjunto mínimo de pacotes de pacotes OSGi {#export-a-minimal-set-of-packages-from-osgi-bundles}

Assim que um pacote for exportado, criamos uma API para que outros dependam. Certifique-se de exportar o mínimo possível e verifique se o que está sendo exportado é uma API. É muito mais fácil usar um método/classe privado e torná-lo público do que pegar algo que já foi exportado e torná-lo privado.

As implementações devem sempre ser colocadas em um *impl* pacote. Por padrão, a variável *maven-bundle-plugin* exportará qualquer item no projeto que não tenha um *impl* em seu nome.

## Sempre defina explicitamente uma versão semântica para cada pacote exportado {#always-explicitly-define-a-semantic-version-for-each-package-exported}

Isso permitirá que os consumidores de sua API evoluam junto com você. Ao fazer isso, sempre siga as práticas recomendadas semânticas de controle de versão. Isso permitirá que os consumidores de sua API saibam quais tipos de alterações esperar em uma nova versão.

## Incluir informações de tipo de métrica quando expostas {#include-metatype-information-where-exposed}

Ao especificar informações de metattipo significativas, seus serviços e componentes serão mais fáceis de entender no console Felix. Uma lista de anotações e atributos SCR pode ser encontrada em: [https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html).
