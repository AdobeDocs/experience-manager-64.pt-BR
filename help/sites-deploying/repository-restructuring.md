---
title: Reestruturação do repositório no AEM 6.4
seo-title: Repository Restructuring in AEM 6.4
description: Saiba mais sobre as noções básicas e o raciocínio por trás da reestruturação do repositório no AEM 6.4
seo-description: Learn about the basics and reasoning behind the repository restructuring in AEM 6.4
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
feature: Upgrading
exl-id: 6ff5a23a-c9b5-49ca-87b2-ba01eaf48a9f
source-git-commit: cda63b9ece88d8172fa4d9817e315c9cff88c224
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Reestruturação do repositório no AEM 6.4{#repository-restructuring-in-aem}

## Introdução {#introduction}

Antes do AEM 6.4, o código do cliente era implantado em áreas imprevisíveis do JCR que estavam sujeitas a alterações nas atualizações. Por causa disso, era comum que as versões formais do AEM substituíssem o código, a configuração ou o conteúdo personalizados. Além disso, às vezes, as alterações no cliente se sobrepunham AEM código de produto ou conteúdo, quebrando a funcionalidade do produto.

Ao definir claramente hierarquias para AEM código de produto e código de cliente, esses conflitos podem ser evitados.

Para esse fim, a partir do AEM 6.4 e para continuar em versões futuras, o conteúdo está sendo reestruturado de /etc para outras pastas no repositório, juntamente com diretrizes sobre o conteúdo que vai para onde, seguindo as seguintes regras de alto nível:

* AEM código de produto sempre será colocado em /libs, que não deve ser substituído pelo código personalizado
* O código personalizado deve ser colocado em /apps, /content e /conf

## Impacto nas atualizações do 6.4 {#impact-on-upgrades}

Ao atualizar para o AEM 6.4, um grande subconjunto do conteúdo em /etc será duplicado em outras pastas no repositório. Esses novos locais são os locais preferidos em que o conteúdo é referenciado. No entanto, todas as tentativas foram feitas para que a atualização do AEM 6.4 seja compatível com as localizações anteriores na pasta /etc, portanto, na maioria dos casos, as localizações antigas continuarão a ser referenciadas pelo código AEM até que as alterações sejam feitas ativamente — e em muitos casos manualmente — no aplicativo de um cliente. Da perspectiva da linha do tempo, há duas categorias de alterações:

* Com a atualização 6.4 - algumas das alterações de reestruturação /etc não são compatíveis com versões anteriores e, portanto, as modificações devem ser planejadas e implementadas como parte da atualização AEM 6.4.
* Antes da atualização 6.5 - a grande maioria das alterações na reestruturação /etc pode ser adiada até algum tempo no futuro pós-atualização. Como mencionado anteriormente, o código AEM 6.4 continuará referenciando os locais antigos até que as modificações sejam implementadas como parte de uma versão do cliente. Embora não haja uma linha do tempo forçada para a qual as alterações devem ser feitas, recomenda-se que elas sejam feitas antes da atualização 6.5, já que os recursos futuros podem depender dos novos locais que estão sendo referenciados. Além disso, a documentação de um determinado recurso fará referência por convenção aos novos locais e, portanto, pode ser confuso se os locais antigos ainda estiverem sendo usados.

### Orientação relativa à reestruturação {#restructuring-guidance}

Ao planejar uma atualização para o AEM 6.4, as seguintes páginas por solução devem ser referenciadas para avaliar o esforço de trabalho:

* [Restruturação do repositório comum a todas as soluções AEM](/help/sites-deploying/all-repository-restructuring-in-aem-6-4.md)
* [reestruturação de repositório AEM Sites](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md)
* [reestruturação de repositório AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html)
* [Reestruturação de repositório AEM Assets Dynamic Media](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)
* [reestruturação de repositório AEM Forms](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)
* [reestruturação de repositório AEM Communities](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md)
* [AEM reestruturação do repositório do Commerce](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-4.md)

Cada página contém duas seções correspondentes à urgência das alterações necessárias. Qualquer coisa na seção &quot;Atualização 6.4&quot; deve ser abordada como parte do projeto de atualização do AEM 6.4. Qualquer coisa em &quot;Antes da atualização 6.5&quot; pode ser adiada opcionalmente até a pós-atualização.

Cada entrada na página inclui um campo &quot;Orientação sobre reestruturação&quot;, que detalha a estratégia técnica recomendada para alinhar com o novo modelo de repositório 6.4, de modo que os novos locais sejam referenciados para o conteúdo anteriormente localizado na pasta /etc. Um campo &quot;Observações&quot; adicional fornece qualquer contexto útil adicional.
