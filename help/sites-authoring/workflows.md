---
title: Trabalhar com fluxos de trabalho
seo-title: Working with Workflows
description: Os fluxos de trabalho no AEM permitem automatizar uma série de etapas executadas em uma página ou ativo.
seo-description: Workflows in AEM allow you to automate a series of steps that are performed on a page or asset.
uuid: c4442d2a-c6b0-49d4-a1ce-384017c45bf0
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 7cb99618-d903-4cfb-b0d9-b23d189f6e78
exl-id: 8d318fd5-3d8f-4144-95c8-d90685378a91
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 18%

---

# Trabalhar com fluxos de trabalho{#working-with-workflows}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

AEM fluxos de trabalho permite automatizar uma série de etapas executadas em (uma ou mais) páginas e/ou ativos.

Por exemplo, ao publicar, um editor precisa revisar o conteúdo antes que um administrador do site ative a página. Um fluxo de trabalho que automatiza esse exemplo notifica cada participante quando é hora de executar o trabalho necessário:

1. O autor aplica o fluxo de trabalho à página.
1. O editor recebe um item de trabalho que indica que ele deve revisar o conteúdo da página. Ao terminar, indica que o item de trabalho está concluído.
1. O administrador do site recebe um item de trabalho que solicita a ativação da página. Ao terminar, indica que o item de trabalho está concluído.

Normalmente:

* Os autores de conteúdo aplicam fluxos de trabalho às páginas e participam dos fluxos de trabalho.
* Os workflows usados são específicos dos processos comerciais da organização.

As seguintes páginas abrangem:

* [Aplicação de fluxos de trabalho a páginas](/help/sites-authoring/workflows-applying.md)
* [Participar de fluxos de trabalho](/help/sites-authoring/workflows-participating.md)
