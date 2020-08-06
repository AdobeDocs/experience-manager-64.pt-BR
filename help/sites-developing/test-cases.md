---
title: Definição dos casos de teste
seo-title: Definição dos casos de teste
description: Os casos de teste devem se basear nos casos de uso e na especificação detalhada dos requisitos
seo-description: Os casos de teste devem se basear nos casos de uso e na especificação detalhada dos requisitos
uuid: 82dff825-da58-49a2-bf35-f5bb905e523d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 87a1f27a-765e-4882-9c06-5909e1610e1d
translation-type: tm+mt
source-git-commit: 0edddfde1e66ec487139f98e9ffafee885e61dfd
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# Definição dos casos de teste{#defining-your-test-cases}

Os casos de teste devem ser baseados no seguinte:

**Casos de uso**

* Eles definem a funcionalidade necessária em termos de interação entre os Atores (funções que iniciam certas ações) e o sistema.
* Os Casos de uso devem ser definidos pelo cliente.

**Especificação de requisitos detalhados**

* Todos os requisitos funcionais e de desempenho devem ser testados.

Os ensaios devem definir claramente:

* Pré-requisitos; podem abranger sistemas específicos, configurações ou experiência do testador.
* Medidas a adotar; a um nível de pormenor adequado.
* Resultados esperados.
* Critérios claros para aprovação ou falha.

O prospecto de automatizar os casos de teste é obviamente atraente, pois pode eliminar tarefas repetitivas.

## Testes manuais versus automatizados {#manual-versus-automated-tests}

No entanto, a automatização dos casos de ensaio constitui um investimento significativo, pelo que devem ser considerados certos aspectos:

* Requer tempo, esforço e experiência para configurar.
* Se o navegador for baseado, há um risco maior de problemas quando as atualizações do navegador são instaladas; exigindo mais tempo para corrigir.
* Só é realmente viável para grandes projetos.
* Bom quando várias versões estão sendo geradas para teste ou no plano de lançamento de longo prazo.

## Teste de aspectos específicos {#testing-specific-aspects}

Ao testar AEM alguns detalhes específicos são de especial interesse:

Ambientes de autor e publicação

Embora esteja coberto em [Ambientes](/help/sites-developing/the-basics.md#environments) , vale a pena destacar um fator decisivo de AEM no que diz respeito aos testes.

Você deve considerar AEM como duas aplicações:

* ambiente do **autor** Essa instância permite que os autores insiram e publiquem conteúdo.
Isso tem um conjunto pequeno e previsível de usuários, para os quais a funcionalidade e o desempenho específicos são fundamentais.
* o ambiente de **publicação** Essa instância apresenta o site em seu formulário publicado para acesso de visitantes.
Isso geralmente tem um conjunto maior de usuários, onde o volume de tráfego nem sempre é 100% previsível. O desempenho ainda é crucial - ao responder às solicitações. O armazenamento em cache e o balanceamento de carga também devem ser considerados.

Embora o mesmo software como tal, eles:

* servir diferentes finalidades
* têm requisitos diferentes em relação à funcionalidade e ao desempenho
* são configurados de forma diferente
* são ajustados separadamente
* cada um terá seu próprio conjunto de testes de aceitação

Por outras palavras, devem ser testados separadamente e com diferentes casos.

**Personalização**

Ao testar a personalização, cada caso de uso individual deve ser repetido usando várias contas de usuário para comprovar o comportamento.

O cache também deve ser verificado para verificar se o comportamento é correto.

**O Dispatcher**

A maioria dos projetos instalará o Dispatcher para armazenamento em cache e balanceamento de carga.

O teste é difícil (o armazenamento em cache ocorre em vários níveis e em vários locais) e deve ser feito em caixa preta. Os principais aspectos a serem testados são:

* **Precisão**; verifique se as atualizações de conteúdo são vistas pelo visitante do site.
* **Continuidade**; verifique se o site ainda está disponível quando um servidor é desligado.
* **Os clusters** são usados para fornecer:
   * **Failover** Se um servidor falhar, outros servidores no cluster assumirão o processamento.
   * **O balanceamento de** carga de desempenho com failover completo aumenta o desempenho de um cluster.

Quando usado para um projeto do cliente, o cluster deve ser testado para confirmar a operação correta da configuração.

## Teste de software de terceiros {#testing-third-party-software}

Todos os softwares de terceiros com interface para AEM serão referenciados nas Especificações de requisitos detalhados.

Os ensaios necessários (dependendo do âmbito definido) devem ser analisados e deve ser obtido um ensaio limpo.
