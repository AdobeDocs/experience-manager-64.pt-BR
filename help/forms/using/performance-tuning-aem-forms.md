---
title: Ajuste de desempenho do servidor do AEM Forms
seo-title: Ajuste de desempenho do servidor do AEM Forms
description: Para que o AEM Forms tenha um desempenho ideal, você pode ajustar as configurações de cache e os parâmetros da JVM. Além disso, usar um servidor da Web pode aprimorar o desempenho da implantação do AEM Forms.
seo-description: Para que o AEM Forms tenha um desempenho ideal, você pode ajustar as configurações de cache e os parâmetros da JVM. Além disso, usar um servidor da Web pode aprimorar o desempenho da implantação do AEM Forms.
uuid: 77eaeecc-ca52-4d3d-92e6-1ab4d91b9edd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 5d672b56-00c4-46a0-974b-e174fbdf07d6
role: Admin
exl-id: bc750571-08a5-414c-aed5-4e839f6695ae
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 2%

---

# Ajuste de desempenho do servidor do AEM Forms {#performance-tuning-of-aem-forms-server}

Este artigo discute estratégias e práticas recomendadas que você pode implementar para reduzir gargalos e otimizar o desempenho de sua implantação do AEM Forms.

## Configurações de cache {#cache-settings}

Você pode configurar e controlar a estratégia de armazenamento em cache do AEM Forms usando o componente **Configurações do Mobile Forms** no Console de Configuração da Web AEM em:

* (AEM Forms no OSGi) `https://[server]:[port]/system/console/configMgr`
* (AEM Forms no JEE) `https://[server]:[port]/lc/system/console/configMgr`

As opções disponíveis para armazenamento em cache são as seguintes:

* **Nenhum**: Implica não armazenar em cache nenhum artefato. Isso, na prática, retarda o desempenho e requer alta disponibilidade de memória devido à ausência de cache.
* **Conservador**: Dica em armazenar em cache apenas os artefatos intermediários gerados antes da renderização do formulário, como um modelo contendo fragmentos em linha e imagens.
* **Agressivo**: Força o armazenamento em cache de quase tudo o que pode ser armazenado em cache, incluindo conteúdo HTML renderizado além de todos os artefatos do nível de armazenamento em cache do Conservador. Ele resulta no melhor desempenho, mas também consome mais memória para armazenar artefatos em cache. Estratégia agressiva de armazenamento em cache significa que você terá desempenho de tempo constante na renderização de um formulário, à medida que o conteúdo renderizado for armazenado em cache.

As configurações de cache padrão do AEM Forms podem não ser boas o suficiente para alcançar o desempenho ideal. Portanto, é recomendável usar as seguintes configurações:

* **Estratégia** de cache: Agressivo
* **Tamanho**  do cache (em termos de número de formulários): Conforme necessário
* **Tamanho** máximo do objeto: Conforme necessário

![Configurações do Mobile Forms](assets/snap.png)

>[!NOTE]
>
>Se você usar AEM Dispatcher para armazenar formulários adaptáveis em cache, ele também armazenará em cache formulários adaptáveis que contêm formulários com dados pré-preenchidos. Se esses formulários forem fornecidos AEM cache do Dispatcher, isso pode levar ao fornecimento de dados pré-preenchidos ou obsoletos para os usuários. Portanto, use AEM Dispatcher para armazenar em cache formulários adaptáveis que não usam dados pré-preenchidos. Além disso, um cache do dispatcher não invalida automaticamente os fragmentos em cache. Portanto, não o use para armazenar em cache fragmentos de formulário. Para esses formulários e fragmentos, use [Adaptive forms cache](/help/forms/using/configure-adaptive-forms-cache.md).

## Parâmetros da JVM {#jvm-parameters}

Para obter o melhor desempenho, é recomendável usar os seguintes argumentos da JVM `init` para configurar os `Java heap` e `PermGen`.

```java
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>As configurações recomendadas são para o Windows 2008 R2 8 Core e Oracle HotSpot 1.7 (64 bits) JDK e devem ser dimensionadas para cima ou para baixo de acordo com a configuração do sistema.

## Uso de um servidor da Web {#using-a-web-server}

Formulários adaptáveis e formulários HTML5 são renderizados no formato HTML5. A saída resultante pode ser grande dependendo de fatores como o tamanho do formulário e as imagens no formulário. Para otimizar a transferência de dados, a abordagem recomendada é compactar a resposta HTML usando o servidor da Web do qual a solicitação está sendo veiculada. Essa abordagem reduz o tamanho da resposta, o tráfego da rede e o tempo necessário para transmitir dados entre máquinas de servidor e de cliente.

Por exemplo, execute as seguintes etapas para habilitar a compactação no Apache Web Server 2.0 de 32 bits com JBoss:

>[!NOTE]
>
>As instruções a seguir não se aplicam a nenhum servidor diferente do Apache Web Server 2.0 de 32 bits. Para ver as etapas específicas de qualquer outro servidor, consulte a documentação do produto correspondente.

As etapas a seguir demonstram as alterações necessárias para habilitar a compactação com o Apache Web Server

**Obtenha o software do servidor Web Apache aplicável ao seu sistema operacional**

* Windows: baixe o servidor da Web Apache no site do Apache HTTP Server Project.
* Solaris 64-bit: baixe o servidor da Web Apache do site Sunfreeware for Solaris.
* Linux: o servidor Web Apache é pré-instalado em um sistema Linux.

O Apache pode se comunicar com o CRX usando o protocolo HTTP. As configurações são para otimização usando HTTP.

1. Exclua as seguintes configurações de módulo no arquivo `APACHE_HOME/conf/httpd.conf`.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Para Linux, o padrão `APACHE_HOME` é `/etc/httpd/`.

1. Configure o proxy na porta 4502 do crx.

   Adicione a seguinte configuração no arquivo de configuração `APACHE_HOME/conf/httpd.conf`.

   ```java
   ProxyPass / https://<server>:4502/
   ProxyPassReverse / https://<server>:4502/
   ```

1. Ative a compactação. Adicione a seguinte configuração no arquivo de configuração `APACHE_HOME/conf/httpd.conf`.

   **Para formulários HTML5**

   ```java
   <Location /content/xfaforms>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   **Para formulários adaptáveis**

   ```java
   <Location /content/forms/af>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   Para acessar o servidor crx, use `https://[server]:80`, onde `server` é o nome do servidor no qual o servidor Apache está sendo executado.

## Uso de um antivírus em um servidor que executa o AEM Forms {#using-an-antivirus-on-server-running-aem-forms}

Você pode experimentar um desempenho lento nos servidores que executam um software antivírus. Um software antivírus sempre ativo (varredura ao acessar) verifica todos os arquivos de um sistema. Ele pode retardar o servidor e o desempenho da AEM Forms é afetado.

Para melhorar o desempenho, você pode direcionar o software antivírus para excluir os seguintes arquivos e pastas do AEM Forms da varredura sempre ativa (ao acessar):

* AEM diretório de instalação. Se não for possível excluir o diretório completo, exclua o seguinte:

   * [AEM diretório de instalação]\crx-repository\temp
   * [AEM diretório de instalação]\crx-repository\repository
   * [AEM diretório de instalação]\crx-repository\launchpad

* Diretório temporário do servidor de aplicativos. O local padrão é:

   * (Jboss) [AEM diretório de instalação]\jboss\standalone\tmp
   * (Weblogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
   * (Websphere) \Program Files\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(Somente AEM Forms no JEE)** Diretório de armazenamento de documentos global (GDS). O local padrão é:

   * (JBoss) `[appserver root]/server/[server]/svcnative/DocumentStorage`
   * (WebLogic) `[appserverdomain]/[server]/adobe/LiveCycleServer/DocumentStorage`
   * (WebSphere) `[appserver root]/installedApps/adobe/[server]/DocumentStorage`

* **(Somente AEM Forms no JEE)** Logs do servidor AEM Forms e diretório temporário. O local padrão é:

   * Logs do servidor - `[AEM Forms installation directory]\Adobe\AEM forms\[app-server]\server\all\logs`
   * Diretório temporário - [Diretório de instalação do AEM Forms]\temp

>[!NOTE]
>
>* Se você estiver usando um local diferente para GDS e diretório temporário, abra a Interface do usuário do administrador em `https://[server]:[port]/adminui)`, navegue até **Início > Configurações > Configurações do sistema principal > Configurações principais** para confirmar o local em uso.

* Se o servidor do AEM Forms tiver um desempenho lento mesmo depois de excluir os diretórios sugeridos, exclua também o arquivo executável Java (java.exe).


