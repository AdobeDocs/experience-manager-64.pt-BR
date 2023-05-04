---
title: Fragmentos do documento
seo-title: Document Fragments
description: Fragmentos de documento, como texto, listas, condições e fragmentos de layout, no Gerenciamento de correspondência permitem que você forme os componentes estáticos, dinâmicos e repetíveis da correspondência do cliente.
seo-description: Document Fragments, such as Text, lists, conditions, and layout fragments, in Correspondence Management let you form the static, dynamic, and repeatable components of customer correspondence.
uuid: 053a17e5-69a5-463d-af4f-46a86534158f
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 1f48548c-4222-454d-ad16-53da37170de2
feature: Correspondence Management
exl-id: 54159851-bae1-4efd-8c8f-3a855776ecc4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 4%

---

# Fragmentos do documento {#document-fragments}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Fragmentos de documento são partes/componentes reutilizáveis de uma correspondência usando a qual você pode compor Comunicações/cartas interativas. Os fragmentos de documento são dos seguintes tipos:

* **Texto**: Um ativo de texto é uma parte do conteúdo que consiste em um ou mais parágrafos de texto. Um parágrafo pode ser estático ou dinâmico.

   * [Textos em Comunicações interativas](/help/forms/using/texts-interactive-communications.md)

* **Condição**: As condições permitem definir qual conteúdo é incluído no momento da criação da correspondência, com base nos dados fornecidos. A condição é descrita em termos de variáveis de controle. Uma variável de controle pode ser um elemento de dicionário de dados ou um espaço reservado.

   * [Condições em comunicações interativas](/help/forms/using/conditions-interactive-communications.md)

* **Lista:** Lista é um grupo de fragmentos de documento, incluindo texto, listas, condições e imagens. A ordem dos elementos da lista pode ser corrigida ou editável. Ao criar uma carta, você pode usar alguns ou todos os elementos da lista para replicar um padrão reutilizável de elementos.
* **Fragmento de layout**: Um fragmento de layout é um layout que pode ser usado em uma ou mais letras. Um fragmento de layout é usado para criar padrões repetíveis, especialmente tabelas dinâmicas. O layout pode conter campos de formulário típicos, como &quot;Endereço&quot; e &quot;Número de referência&quot;. Também contém subformulários vazios que indicam áreas de destino. Os layouts (XDPs) são criados no Designer e, em seguida, são carregados no AEM Forms.
