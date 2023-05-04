---
title: Como configurar o MongoDB para demonstração
seo-title: How to Setup MongoDB for Demo
description: Como configurar o MSRP para uma instância de autor e uma instância de publicação
seo-description: How to setup MSRP for one author instance and one publish instance
uuid: d2035a9e-f05c-4f90-949d-7cdae9646750
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0b126218-b142-4d33-a28c-a91ab4fe99ac
role: Admin
exl-id: e32fc619-6226-48c6-bbd7-1910963d1036
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 1%

---

# Como configurar o MongoDB para demonstração {#how-to-setup-mongodb-for-demo}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

Este tutorial descreve como configurar [MSRP](msrp.md) para *um autor* instância e *uma publicação* instância.

Com essa configuração, o conteúdo da comunidade é acessível de ambientes do autor e de publicação sem a necessidade de encaminhar ou reverter o conteúdo gerado pelo usuário (UGC).

Essa configuração é adequada para *não produção* ambientes como para desenvolvimento e/ou demonstração.

**A *produção* O ambiente deve:**

* Execute o MongoDB com um conjunto de réplicas
* Usar a SolrCloud
* Conter várias instâncias do editor

## MongoDB {#mongodb}

### Instalar o MongoDB {#install-mongodb}

* Baixar o MongoDB de [https://www.mongodb.org/](https://www.mongodb.org/)

   * Opção de SO:

      * Linux
      * Mac 10.8
      * Windows 7
   * Escolha da versão:

      * No mínimo, use a versão 2.6


* Configuração básica

   * Siga as instruções de instalação do MongoDB
   * Configurar para mondeus

      * Não é necessário configurar mongos ou compartilhamento
   * A pasta MongoDB instalada será chamada de &lt;mongo-install>
   * O caminho do diretório de dados definido será chamado de &lt;mongo-dbpath>


* O MongoDB pode ser executado no mesmo host que o AEM ou executado remotamente

### Iniciar MongoDB {#start-mongodb}

* &lt;mongo-install>/bin/mongod —dbpath &lt;mongo-dbpath>

Isso iniciará um servidor MongoDB usando a porta padrão 27017.

* Para o Mac, aumente o limite com o arg inicial &#39;ulimit -n 2048&#39;

>[!NOTE]
>
>Se MongoDB for iniciado *after* AEM, **reiniciar** all **AEM** para que se conectem corretamente ao MongoDB.

### Opção de produção de demonstração: Configurar Conjunto de Réplicas do MongoDB {#demo-production-option-setup-mongodb-replica-set}

Os seguintes comandos são um exemplo de configuração de um conjunto de réplicas com 3 nós no host local:

* bin/mongod —port 27017 —dbpath data —replSet rs0&amp;
* bin/mongo

   * cfg = {&quot;_id&quot;: &quot;rs0&quot;,&quot;version&quot;: 1, &quot;membros&quot;: [{&quot;_id&quot;: 0,&quot;host&quot;: &quot;127.0.0.1:27017&quot;}]}
   * rs.initiate(cfg)

* bin/mongod —port 27018 —dbpath data1 —replSet rs0&amp;
* bin/mongod —port 27019 —dbpath data2 —replSet rs0&amp;
* bin/mongo

   * rs.add(&quot;127.0.0.1:27018&quot;)
   * rs.add(&quot;127.0.0.1:27019&quot;)
   * rs.status()

## Solr {#solr}

### Instalar Solr {#install-solr}

* Baixar Solr de [Apache Lucene](https://archive.apache.org/dist/lucene/solr/):

   * Adequado para qualquer SO
   * Usar a versão 4.10 ou 5
   * A Solr requer o Java 1.7 ou superior

* Configuração básica

   * Siga a configuração Solr &#39;example&#39;
   * Nenhum serviço é necessário
   * A pasta Solr instalada será chamada de &lt;solr-install>

### Configurar o Solr para AEM Communities {#configure-solr-for-aem-communities}

Para configurar uma coleção Solr para MSRP para demonstração, há duas decisões a serem tomadas (selecione os links para a documentação principal para obter detalhes):

1. Executar Solr de forma autônoma ou [Modo SolrCloud](msrp.md#solrcloudmode)
1. Instalar [padrão](msrp.md#installingstandardmls) ou [avançado](msrp.md#installingadvancedmls) pesquisa multilíngue (MLS)

### Solar independente {#standalone-solr}

O método para executar o Solr pode ser diferente dependendo da versão e da maneira de instalação. O [Guia de referência de Solr](https://archive.apache.org/dist/lucene/solr/ref-guide/) é a documentação autoritativa.

Para simplificar, usando a versão 4.10 como exemplo, inicie o Solr no modo independente:

* cd para &lt;solrinstall>/exemplo
* java -jar start.jar

Isso iniciará um servidor HTTP Solr usando a porta padrão 8983. Você pode navegar até o console Solr para obter um console Solr para testes.

* console Solr padrão: [http://localhost:8983/solr/](http://localhost:8983/solr/)

>[!NOTE]
>
>Se Solr Console não estiver disponível, verifique os logs em &lt;solrinstall>/exemplo/logs. Verifique se a SOLR está tentando se vincular a um nome de host específico que não pode ser resolvido (por exemplo, &quot;user-macbook-pro&quot;).
Nesse caso, atualize o arquivo etc/hosts com uma nova entrada para esse nome de host (por exemplo, 127.0.0.1 user-macbook-pro) e Solr iniciará corretamente.

### SolrCloud {#solrcloud}

Para executar uma configuração básica (não de produção) da solrCloud, comece a solr com:

* java -Dbootstrap_confdir=./solr/collection1/conf -Dbootstrap_conf=true -DzkRun -jar start.jar

## Identifique o MongoDB como armazenamento comum {#identify-mongodb-as-common-store}

Inicie o autor e publique as instâncias de AEM, se necessário.

Se AEM estava em execução antes do MongoDB ser iniciado, as instâncias AEM precisarão ser reiniciadas.

Siga as instruções na página principal da documentação: [MSRP - MongoDB Common Store](msrp.md)

## Testar {#test}

Para testar e verificar o armazenamento comum do MongoDB, poste um comentário na instância de publicação e exiba-o na instância do autor, bem como exibir o UGC no MongoDB e no Solr:

1. Na instância de publicação, navegue até o [Guia de componentes da comunidade](http://localhost:4503/content/community-components/en/comments.html) e selecione o componente Comentários .
1. Faça logon para postar um comentário:
1. Insira o texto na caixa de entrada de texto do comentário e clique em **[!UICONTROL Post]**

   ![chlimage_1-191](assets/chlimage_1-191.png)

1. Basta exibir o comentário no [instância do autor](http://localhost:4502/content/community-components/en/comments.html) (provavelmente ainda está conectado como administrador / administrador).

   ![chlimage_1-192](assets/chlimage_1-192.png)

   Observação: enquanto houver nós JCR sob o *asipath* em nome do autor, trata-se do quadro SEPA para os cartões. O UGC real não está no JCR, está no MongoDB.

1. Exibir o UGC no mongodb **[!UICONTROL Comunidades > Coleções > Conteúdo]**

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. Exibir o UGC no Solr:

   * Navegue até o painel Solr: [http://localhost:8983/solr/](http://localhost:8983/solr/)
   * Usuário `core selector` para selecionar `collection1`
   * Selecionar `Query`
   * Selecionar `Execute Query`

   ![chlimage_1-194](assets/chlimage_1-194.png)

## Resolução de problemas {#troubleshooting}

### Nenhum UGC é exibido {#no-ugc-appears}

1. Certifique-se de que o MongoDB esteja instalado e em execução corretamente.

1. Verifique se o MSRP foi configurado para ser o provedor padrão:

   * Em todas as instâncias do autor e do AEM de publicação, revise a [Console de configuração de armazenamento](srp-config.md)

   ou verifique o repositório AEM:

   * No JCR, se [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

      * Não contém um [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) , significa que o provedor de armazenamento é JSRP
      * Se o nó srpc existir e contiver nó [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration), as propriedades da configuração padrão devem definir o MSRP como o provedor padrão


1. Certifique-se de que AEM foi reiniciado após a seleção do MSRP.
