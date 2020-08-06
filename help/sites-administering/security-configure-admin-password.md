---
title: Configure a senha do administrador na instalação
seo-title: Configure a senha do administrador na instalação
description: Saiba como alterar a senha de administrador AEM instalação.
seo-description: Saiba como alterar a senha de administrador AEM instalação.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# Configure a senha do administrador na instalação{#configure-the-admin-password-on-installation}

## Visão geral {#overview}

Desde a versão 6.3, AEM permite que a senha do administrador seja definida usando a linha de comando ao instalar uma nova instância.

Com versões anteriores do AEM, a senha da conta do administrador, juntamente com a senha de vários outros consoles, precisavam ser alterados após a instalação.

Este recurso adiciona a facilidade de definir uma nova senha de administrador para o repositório e o Mecanismo Servlet durante a instalação de uma instância AEM, eliminando a necessidade de fazê-la manualmente depois.

>[!CAUTION]
>
>Observe que o recurso não abrange o Console do Felix, para o qual a senha precisa ser alterada manualmente. Para obter mais informações, consulte a seção [Lista de verificação de](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts)segurança relevante.

## Como Usá-Lo? {#how-do-i-use-it}

Esse recurso será acionado automaticamente se você optar por instalar AEM pela linha de comando, em vez de clicar no duplo no JAR de um explorador de sistemas de arquivos.

A sintaxe geral para executar uma instância AEM a partir da linha de comando é:

```shell
java -jar aem6.3.jar
```

Ao executar a instância a partir da linha de comando, você terá a opção de alterar a senha do administrador durante o processo de instalação:

![chlimage_1-116](assets/chlimage_1-116.png)

>[!NOTE]
>
>O prompt para alterar a senha do administrador só será exibido durante a instalação de uma nova instância AEM.

## Usando o sinalizador -nointerativo {#using-the-nointeractive-flag}

Você também pode especificar a senha de um arquivo de propriedades. Isso é feito usando o `-nointeractive` sinalizador combinado com a propriedade do `-Dadmin.password.file` sistema.

Veja abaixo um exemplo:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

A senha dentro do `passwordfile.properties` arquivo precisa ter o formato abaixo:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Se você simplesmente usar o `-nointeractive` parâmetro sem a propriedade `-Dadmin.password.file` system, AEM usará a senha de administrador padrão sem solicitar que você a altere, essencialmente replicando o comportamento de versões anteriores. Esse modo não interativo pode ser usado para instalações automatizadas usando a linha de comando em um script de instalação.

