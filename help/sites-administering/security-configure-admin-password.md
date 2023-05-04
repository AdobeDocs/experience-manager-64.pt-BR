---
title: Configure a senha de administrador na instalação
seo-title: Configure the Admin Password on Installation
description: Saiba como alterar a Senha de administrador na instalação AEM.
seo-description: Learn how to change the Admin Password on AEM Installation.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
exl-id: 6dd289ee-13fd-46be-82cd-aa69852397c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 2%

---

# Configure a senha de administrador na instalação{#configure-the-admin-password-on-installation}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

Desde a versão 6.3, o AEM permite que a senha do administrador seja definida usando a linha de comando ao instalar uma nova instância.

Com versões anteriores do AEM, a senha da conta de administrador, juntamente com a senha de vários outros consoles, precisavam ser alteradas após a instalação.

Esse recurso adiciona o recurso de definir uma nova senha de administrador para o repositório e o Mecanismo Servlet durante a instalação de uma instância do AEM, eliminando a necessidade de fazer isso manualmente depois.

>[!CAUTION]
>
>Observe que o recurso não abrange o Felix Console, para o qual a senha precisa ser alterada manualmente. Para obter mais informações, consulte o [Seção Lista de verificação de segurança](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## Como Usá-Lo? {#how-do-i-use-it}

Esse recurso será acionado automaticamente se você optar por instalar o AEM por meio da linha de comando, em vez de clicar duas vezes no JAR de um explorador de sistema de arquivos.

A sintaxe geral para executar uma instância de AEM a partir da linha de comando é:

```shell
java -jar aem6.3.jar
```

Ao executar a instância a partir da linha de comando, você terá a opção de alterar a senha do administrador durante o processo de instalação:

![chlimage_1-116](assets/chlimage_1-116.png)

>[!NOTE]
>
>O prompt para alterar a senha do administrador só será exibido durante a instalação de uma nova instância do AEM.

## Utilização do sinalizador -nointerativo {#using-the-nointeractive-flag}

Você também pode optar por especificar a senha de um arquivo de propriedades. Isso é feito usando a variável `-nointeractive` sinalizador combinado com `-Dadmin.password.file` propriedade do sistema.

Veja um exemplo:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

A senha dentro do `passwordfile.properties` O arquivo precisa ter o formato abaixo:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Se você simplesmente usar a variável `-nointeractive` sem o `-Dadmin.password.file` propriedade do sistema, AEM usará a senha padrão do administrador sem solicitar que você a altere, essencialmente replicando o comportamento de versões anteriores. Esse modo não interativo pode ser usado para instalações automatizadas usando a linha de comando em um script de instalação.
