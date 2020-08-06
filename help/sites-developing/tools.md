---
title: Ferramentas de teste e rastreamento
seo-title: Ferramentas de teste e rastreamento
description: AEM fornece uma estrutura para testar a interface do usuário do componente e um mecanismo para testar e depurar componentes
seo-description: AEM fornece uma estrutura para testar a interface do usuário do componente e um mecanismo para testar e depurar componentes
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
translation-type: tm+mt
source-git-commit: 60f36a33471dbbd9ca877dbbedc82ade606a125c
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---


# Ferramentas de teste e rastreamento{#testing-and-tracking-tools}

## Testes {#testing}

AEM fornece:

* [uma estrutura para testar a interface do usuário](/help/sites-developing/hobbes.md)do componente.
* [um mecanismo para testar e depurar componentes](/help/sites-developing/developer-mode.md).

Estas são duas ferramentas de teste de fonte aberta:

**Selênio**

O Selenium é usado para teste de função em um navegador com um usuário por atividade. Ele registra as etapas de teste (cliques) como tabelas HTML ou classes Java.

Para obter mais informações, consulte [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

O JMeter é usado para rastrear solicitações e pode ser usado para testes funcionais, de desempenho e de estresse.

Para obter mais informações, consulte [http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/).

Há também muitas ferramentas proprietárias para automatizar testes e gerenciar planos de teste.

## Acompanhamento {#tracking}

As ferramentas a seguir estão facilmente disponíveis. No entanto, um problema chave em todos os casos é a disponibilidade dos dados para todos os membros da equipe do projeto - parceiro e cliente.

**Bugzilla**

Um sistema de rastreamento de erros que pode ser configurado de acordo com seus próprios requisitos.

**Planilhas**

Embora não seja especificamente uma ferramenta de rastreamento de erros, as planilhas geralmente são usadas incorretamente para essa finalidade, pois são fáceis de entender e a maioria dos usuários tem experiência de sua funcionalidade.

Se forem usados para rastreamento, então:

* devem ser mantidas simples.
* o número de folhas de cálculo individuais deve ser reduzido ao mínimo.
* devem ser atualizados regularmente.
* apenas uma cópia principal deve ser mantida e todos devem saber onde está a cópia principal.
* devem ser acessíveis a todos os membros do projeto.
* se a segurança for um problema (geralmente ocorre em empresas grandes) e o acesso comum não for possível, as cópias poderão ser distribuídas desde que todos entendam que são cópias e não podem ser atualizadas.

Novamente, há muitas ferramentas proprietárias para rastrear bugs e requisitos de recursos.
