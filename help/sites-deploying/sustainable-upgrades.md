---
title: Atualizações sustentáveis
seo-title: Atualizações sustentáveis
description: Saiba mais sobre atualizações sustentáveis no AEM 6.4.
seo-description: Saiba mais sobre atualizações sustentáveis no AEM 6.4.
uuid: 59d64af5-6ee0-40c8-b24a-c06848f70daa
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 5ca8dd7a-4efd-493e-8022-d2f10903b0a2
feature: Upgrading
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---


# Atualizações sustentáveis{#sustainable-upgrades}

## Estrutura de personalização {#customization-framework}

### Arquitetura (Funcional/Infraestrutura/Conteúdo/Aplicativo) {#architecture-functional-infrastructure-content-application}

A estrutura de personalização foi criada para ajudar a reduzir as violações em áreas não extensíveis do código (como APIS) ou conteúdo (como sobreposições) que não são amigáveis à atualização.

Há dois componentes da estrutura de personalização: a **Superfície da API** e a **Classificação de Conteúdo**.

#### Superfície da API {#api-surface}

Em versões anteriores do AEM, muitas APIs foram expostas por meio do Uber Jar. Algumas dessas APIs não eram destinadas a serem usadas pelos clientes, mas foram expostas ao suporte AEM funcionalidade em pacotes. Além disso, as APIs do Java serão marcadas como Públicas ou Privadas para indicar aos clientes quais APIs são seguras para usar no contexto de atualizações. Outras especificações incluem:

* As APIs Java marcadas como `Public` podem ser usadas e referenciadas por pacotes de implementação personalizados.

* As APIs públicas serão compatíveis com a instalação de um pacote de compatibilidade.
* O pacote de compatibilidade conterá um Uber JAR de compatibilidade para garantir compatibilidade com versões anteriores
* As APIs Java marcadas como `Private` destinam-se a ser usadas apenas por pacotes internos AEM e não devem ser usadas por pacotes personalizados.

>[!NOTE]
>
>O conceito de `Private` e `Public` neste contexto não deve ser confundido com noções Java de classes públicas e privadas.

![image2018-2-12_23-52-48](assets/image2018-2-12_23-52-48.png)

#### Classificações de conteúdo {#content-classifications}

AEM há muito tempo usa o principal de sobreposições e Sling Resource Merger para permitir que os clientes estendam e personalizem AEM funcionalidade. A funcionalidade predefinida que alimenta os consoles de AEM e a interface do usuário é armazenada em **/libs**. Os clientes nunca devem modificar nada abaixo de **/libs**, mas podem adicionar conteúdo adicional abaixo de **/apps** para sobrepor e estender a funcionalidade definida em **/libs** (Consulte Desenvolvimento com sobreposições para obter mais informações). Isso ainda causou vários problemas ao atualizar AEM, pois o conteúdo em **/libs** pode mudar, fazendo com que a funcionalidade de sobreposição se quebre de maneiras inesperadas. Os clientes também podem estender AEM componentes por meio de herança via `sling:resourceSuperType`, ou simplesmente referenciar um componente em **/libs** diretamente via sling:resourceType. Problemas de atualização semelhantes podem ocorrer com casos de uso de referência e substituição.

Para tornar mais seguro e fácil para os clientes entenderem quais áreas de **/libs** são seguras para usar e sobrepor o conteúdo em **/libs** foi classificado com as seguintes mixins:

* **Público (granite:PublicArea)**  - Define um nó como público, para que possa ser sobreposto, herdado (  `sling:resourceSuperType`) ou usado diretamente (  `sling:resourceType`). Os nós abaixo de /libs marcados como Público serão seguros para atualizar com a adição de um Pacote de Compatibilidade. Em geral, os clientes do devem utilizar apenas os nós marcados como Públicos.

* **Abstrato (granite:AbstractArea)**  - Define um nó como abstrato. Os nós podem ser sobrepostos ou herdados ( `sling:resourceSupertype`), mas não devem ser usados diretamente ( `sling:resourceType`).

* **Final (granite:FinalArea)**  - Define um nó como final. Os nós classificados como finais não podem ser sobrepostos ou herdados. Os nós finais podem ser usados diretamente por meio de `sling:resourceType`. Os subnós no nó final são considerados internos por padrão

* **Interno (granite:InternalArea)**  - Define um nó como interno. Os nós classificados como internos não podem ser sobrepostos, herdados ou usados diretamente. Esses nós são destinados apenas à funcionalidade interna de AEM

* **Sem anotação**  - Os nós herdam a classificação com base na hierarquia da árvore. A raiz / é, por padrão, Pública. **Os nós com um pai classificado como Interno ou Final também devem ser tratados como Interno.**

>[!NOTE]
>
>Essas políticas são aplicadas somente em relação aos mecanismos baseados no caminho de pesquisa do Sling. Outras áreas de **/libs** como uma biblioteca do lado do cliente podem ser marcadas como `Internal`, mas ainda podem ser usadas com inclusão padrão de clientlib. É importante que um cliente continue a respeitar a Classificação interna nesses casos.

#### Indicadores de tipo de conteúdo de CRXDE Lite {#crxde-lite-content-type-indicators}

As misturas aplicadas no CRXDE Lite mostrarão os nós de conteúdo e as árvores marcadas como `INTERNAL` como esmaecidas. Para `FINAL` somente o ícone fica esmaecido. Os filhos desses nós também aparecerão cinza. A funcionalidade Sobrepor nó está desativada em ambos os casos.

**Público**

![image2018-2-8_23-34-5](assets/image2018-2-8_23-34-5.png)

**Final**

![image2018-2-8_23-34-56](assets/image2018-2-8_23-34-56.png)

**Interno**

![image2018-2-8_23-38-23](assets/image2018-2-8_23-38-23.png)

**Verificação de integridade do conteúdo**

O AEM 6.4 será enviado com uma verificação de integridade para alertar os clientes se o conteúdo sobreposto ou referenciado for usado de uma maneira inconsistente com a classificação do conteúdo.

A **Sling/Granite Content Access Check** é uma nova verificação de integridade que monitora o repositório para ver se o código do cliente está acessando nós protegidos incorretamente no AEM.

Isso verificará **/apps** e normalmente levará vários segundos para ser concluído.

Para acessar essa nova verificação de integridade, você precisa fazer o seguinte:

1. Na Tela inicial do AEM, navegue até **Ferramentas > Operações > Relatórios de integridade**
1. Clique na **Verificação de Acesso ao Conteúdo do Sling/Granite** conforme mostrado abaixo:

   ![screen_shot_2017-12-14at55648pm](assets/screen_shot_2017-12-14at55648pm.png)

Após a conclusão da verificação, uma lista de avisos será exibida, notificando um usuário final do nó protegido que está sendo referenciado incorretamente:

![screenshot-2018-2-5relatórios de saúde](assets/screenshot-2018-2-5healthreports.png)

Depois de corrigir as violações, ele retornará ao estado verde:

![screenshot-2018-2-5violações de relatórios de saúde](assets/screenshot-2018-2-5healthreports-violations.png)

A verificação de integridade exibe informações coletadas por um serviço em segundo plano que verifica de forma assíncrona sempre que uma sobreposição ou tipo de recurso é usado em todos os caminhos de pesquisa do Sling. Se as combinações de conteúdo forem usadas incorretamente, isso relata uma violação.
