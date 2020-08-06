---
title: Ferramentas de desenvolvedor AEM para Eclipse
seo-title: Ferramentas de desenvolvedor AEM para Eclipse
description: 'null'
seo-description: 'null'
uuid: 566e49f2-6f28-4aa7-bfe0-b5f9675310bf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: a2ae76a8-50b0-4e43-b791-ad3be25b8582
translation-type: tm+mt
source-git-commit: 8e2bd579e4c5edaaf86be36bd9d81dfffa13a573
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 1%

---


# Ferramentas de desenvolvedor AEM para Eclipse{#aem-developer-tools-for-eclipse}

![](do-not-localize/chlimage_1-9.png)

## Visão geral {#overview}

As Ferramentas do desenvolvedor do AEM para Eclipse são um plug-in do Eclipse baseado no plug-in [Eclipse para o Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) lançado sob a licença do Apache 2.

Ele oferta vários recursos que facilitam AEM desenvolvimento:

* Integração perfeita com instâncias AEM por meio do Eclipse Server Connector.
* Sincronização de pacotes de conteúdo e OSGI.
* Suporte de depuração com capacidade de troca automática de código.
* Inicialização simples de projetos AEM por meio de um Assistente de criação de projeto específico.
* Edição fácil das propriedades do JCR.

## Requisitos {#requirements}

Antes de usar as ferramentas do desenvolvedor AEM, é necessário:

* Baixe e instale o [Eclipse IDE para desenvolvedores](https://eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/lunar)Java EE. Atualmente, as ferramentas de desenvolvedor do AEM são compatíveis com o Eclipse Kepler ou mais recente

* Pode ser usado com AEM versão 5.6.1 ou mais recente
* Configure a instalação do eclipse para garantir que você tenha pelo menos 1 gigabyte de memória heap, editando o arquivo de `eclipse.ini` configuração conforme descrito nas Perguntas frequentes do [Eclipse](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse%3F).

>[!NOTE]
>
>No macOS, você precisa clicar com o botão direito do mouse em **Eclipse.app** e selecionar **Mostrar conteúdo** do pacote para encontrar seu `eclipse.ini`**.**

## Como instalar as ferramentas do desenvolvedor AEM para o Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Depois de cumprir os [requisitos](#requirements) acima, você pode instalar o plug-in da seguinte maneira:

1. Navegue pelo site [**AEM **Developer Tools na web](https://eclipse.adobe.com/aem/dev-tools/).

1. Copie o link **de instalação**.

   Observe que, como alternativa, você pode baixar um arquivo em vez de usar o link de instalação. Isso permite a instalação offline, mas você perderá notificações automáticas de atualização dessa forma.

1. No Eclipse, abra o menu **Ajuda** .
1. Clique em **Instalar novo software**.
1. Clique em **Adicionar...**.
1. Em **Nome** , digite AEM Ferramentas do desenvolvedor.
1. Em **Local** , copie o URL de instalação.
1. Click **Ok**.
1. Verifique os plug-ins **AEM** e **Sling** .
1. Clique em **Avançar**.
1. Clique em **Avançar**.
1. Aceite os contratos de lixeira e clique em **Concluir**.
1. Clique em **Sim** para reiniciar o Eclipse.

## Como importar projetos existentes {#how-to-import-existing-projects}

>[!NOTE]
>
>Consulte [Como trabalhar com um pacote no Eclipse quando ele foi baixado do AEM](https://stackoverflow.com/questions/29699726/how-to-work-with-a-bundle-in-eclipse-when-it-was-downloaded-from-aem/29705407#29705407).

## A perspectiva AEM {#the-aem-perspective}

As Ferramentas de Desenvolvimento de AEM para Eclipse fornecem uma Perspectiva que oferta o controle total sobre seus projetos e instâncias de AEM.

![chlimage_1-2](assets/chlimage_1-2.jpeg)

## Exemplo de projeto de vários módulos {#sample-multi-module-project}

As ferramentas de desenvolvedor do AEM para Eclipse vêm com uma amostra de projeto de vários módulos que ajuda você a se familiarizar rapidamente com a configuração de um projeto no Eclipse, além de servir como um guia de práticas recomendadas para vários recursos AEM. [Saiba mais sobre o Tipo de Arquivo](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)do Projeto.

Siga estas etapas para criar o projeto de amostra:

1. No menu **Arquivo** > **Novo** > **Projeto** , navegue até a seção **AEM** e selecione **AEM Exemplo de projeto** de vários módulos.

   ![chlimage_1-69](assets/chlimage_1-69.png)

1. Clique em **Avançar**.

   >[!NOTE]
   >
   >Essa etapa pode levar algum tempo, pois m2eclipse precisa verificar os catálogos de arquétipos.

   ![chlimage_1-78](assets/chlimage_1-70.png)

1. Escolha **com.adobe.granite.archetypes : sample-project-archetype : (número mais alto)** no menu e clique em **Avançar**.

   ![chlimage_1-71](assets/chlimage_1-71.png)

1. Preencha um **Nome**, uma ID **de** grupo e uma ID **de** artefato para o projeto de amostra. Você também pode optar por definir algumas propriedades avançadas.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Em seguida, configure um servidor AEM ao qual o Eclipse se conectará.

   Para usar o recurso do depurador, é necessário ter iniciado o AEM no modo de depuração - o que pode ser obtido, por exemplo, adicionando o seguinte à linha de comando:

   ```
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. Click **Finish**. A estrutura do projeto é criada.

   >[!NOTE]
   >
   >Numa instalação nova (mais especificamente: quando as dependências maven nunca foram baixadas), você pode criar o projeto com erros. Nesse caso, siga o procedimento descrito em [Resolução de definição](#resolving-invalid-project-definition)de projeto inválida.

## Resolução de Problemas{#troubleshooting}

### Resolvendo Definição de Projeto Inválida {#resolving-invalid-project-definition}

Para resolver dependências inválidas e definição de projeto, siga estas instruções:

1. Selecione todos os projetos criados.
1. Clique com o botão direito do mouse. No menu **Maven** , selecione **Atualizar projetos**.
1. Verifique **Forçar Atualizações de Instantâneos/Versões**.
1. Clique em **OK**. O Eclipse tenta baixar as dependências necessárias.

### Habilitar a autocompletar da biblioteca de tags em arquivos JSP {#enabling-tag-library-autocompletion-in-jsp-files}

A autoconclusão da biblioteca de tags funciona fora da caixa, visto que as dependências adequadas são adicionadas ao projeto. Há um problema conhecido ao usar o AEM Uber Jar, que não inclui os arquivos tld e TagExtraInfo necessários.

Para contornar isso, verifique se o artefato org.apache.sling.scripting.jsp.taglib está localizado no classpath antes do AEM Uber Jar. Para projetos Maven, coloque a seguinte dependência no pom.xml antes do Uber Jar.

```xml
<dependency>
  <groupId>org.apache.sling</groupId>
  <artifactId>org.apache.sling.scripting.jsp.taglib</artifactId>
  <scope>provided</scope>
</dependency>
```

Certifique-se de adicionar a versão correta para a implantação do AEM.

## More information {#more-information}

A ferramenta oficial Apache Sling IDE para o site Eclipse fornece informações úteis:

* A ferramenta [**Apache Sling IDE para o Guia **do Usuário do Eclipse](https://sling.apache.org/documentation/development/ide-tooling.html), esta documentação o guiará pelos conceitos gerais, integração de servidor e recursos de implantação suportados pelas Ferramentas de Desenvolvimento AEM.
* A seção [Solução de problemas](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* Os problemas [conhecidos são listas](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

A seguinte documentação oficial do [Eclipse](https://eclipse.org/) pode ajudar a configurar seu ambiente:

* [Introdução ao Eclipse](https://eclipse.org/users/)
* [Sistema de ajuda do Eclipse Luna](https://help.eclipse.org/luna/index.jsp)
* [Integração Maven (m2eclipse)](https://www.eclipse.org/m2e/)

