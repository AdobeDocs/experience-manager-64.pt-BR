---
title: Ferramentas de teste e rastreamento
seo-title: Testing and Tracking Tools
description: O AEM fornece uma estrutura para testar a interface do componente e um mecanismo para testar e depurar componentes
seo-description: AEM provides a framework for testing component UI and a mechanism for testing and debugging components
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
exl-id: 9387cdb4-f8de-4229-90d1-59218ac17561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 3%

---

# Ferramentas de teste e rastreamento{#testing-and-tracking-tools}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Testes {#testing}

O AEM fornece:

* [uma estrutura para testar a interface do usuário do componente](/help/sites-developing/hobbes.md).
* [um mecanismo para testar e depurar componentes](/help/sites-developing/developer-mode.md).

Veja a seguir duas ferramentas de Teste de código aberto:

**Selênio**

O Selenium é usado para testes de função em um navegador com um usuário por atividade. Ele registra as etapas de teste (cliques) como HTML tables ou classes Java.

Para obter mais informações, consulte [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

O JMeter é usado para rastrear solicitações e pode ser usado para testes funcionais, de desempenho e de estresse.

Para obter mais informações, consulte [http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/).

Há também muitas ferramentas proprietárias para automatizar testes e gerenciar planos de teste.

## Rastreamento {#tracking}

As ferramentas a seguir estão facilmente disponíveis. No entanto, uma questão fundamental em todos os casos é a disponibilidade dos dados para todos os membros da equipe do projeto - parceiro e cliente.

**Bugzilla**

Um sistema de rastreamento de erros que pode ser configurado de acordo com seus próprios requisitos.

**Planilhas**

Embora não seja especificamente uma ferramenta de rastreamento de erros, as planilhas são frequentemente utilizadas incorretamente para essa finalidade, pois são fáceis de entender e a maioria dos usuários tem experiência de sua funcionalidade.

Se forem usados para rastreamento, então:

* devem ser simples.
* o número de folhas de cálculo individuais deve ser limitado ao mínimo.
* devem ser atualizados regularmente.
* apenas uma cópia principal deve ser mantida e todos devem saber onde está a cópia principal.
* devem ser acessíveis a todos os membros do projeto.
* se a segurança for um problema (geralmente ocorre em grandes empresas) e o acesso comum não for possível, as cópias poderão ser distribuídas desde que todos entendam que são cópias e não podem ser atualizadas.

Novamente, há muitas ferramentas proprietárias para rastrear bugs e requisitos de recursos.
