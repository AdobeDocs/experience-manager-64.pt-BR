---
title: Etapas de atualização para instalações do servidor de aplicativos
seo-title: Upgrade Steps for Application Server Installations
description: Saiba como atualizar instâncias de AEM que são implantadas pelos Servidores de Aplicativos.
seo-description: Learn how to upgrade instances of AEM that are deployed via Application Servers.
uuid: df3fa715-af4b-4c81-b2c5-130fbc82f395
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: c427c8b6-eb94-45fa-908f-c3d5a337427d
feature: Upgrading
exl-id: 1c72093e-82c8-49ad-bd3c-d61904aaab28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 1%

---

# Etapas de atualização para instalações do servidor de aplicativos{#upgrade-steps-for-application-server-installations}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esta seção descreve o procedimento que precisa ser seguido para atualizar AEM para instalações do Servidor de Aplicativos.

Todos os exemplos neste procedimento usam o JBoss como o Servidor de Aplicativos e implicam que você tenha uma versão funcional do AEM já implantada. O procedimento destina-se a documentar as atualizações realizadas a partir de **AEM versão 5.6 para 6.3**.

1. Primeiro, inicie o JBoss. Na maioria das situações, é possível fazer isso executando o `standalone.sh` script de inicialização, executando este comando a partir do terminal:

   ```shell
   jboss-install-folder/bin/standalone.sh
   ```

1. Se o AEM 5.6 já estiver implantado, verifique se os pacotes estão funcionando corretamente executando:

   ```shell
   wget https://<serveraddress:port>/cq/system/console/bundles
   ```

1. Em seguida, desimplante o AEM 5.6:

   ```shell
   rm jboss-install-folder/standalone/deployments/cq.war
   ```

1. Pare o JBoss.

1. Agora, migre o repositório usando a ferramenta de migração crx2oak:

   ```shell
   java -jar crx2oak.jar crx-quickstart/repository/ crx-quickstart/oak-repository
   ```

   >[!NOTE]
   >
   >Neste exemplo, oak-repository é o diretório temporário onde o repositório recém-convertido residirá. Antes de executar esta etapa, verifique se você tem a versão mais recente do crx2oak.jar.

1. Exclua as propriedades necessárias no arquivo sling.properties fazendo o seguinte:

   1. Abra o arquivo localizado em `crx-quickstart/launchpad/sling.properties`
   1. Texto da etapa Remova as seguintes propriedades e salve o arquivo:

      1. `sling.installer.dir`
      1. `felix.cm.dir`
      1. `granite.product.version`
      1. `org.osgi.framework.system.packages`
      1. `osgi-core-packages`
      1. `osgi-compendium-services`
      1. `jre-*`
      1. `sling.run.mode.install.options`

1. Remova os arquivos e pastas que não são mais necessários. Os itens que você precisa remover especificamente são:

   * O **pasta de inicialização/inicialização**. Você pode excluí-lo executando o seguinte comando no terminal: `rm -rf crx-quickstart/launchpad/startup`
   * O **arquivo base.jar**: `find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`
   * O **Arquivo BootstrapCommandFile_timestamp.txt**: `rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

1. Copie o armazenamento de segmentos recém-migrado para o local adequado:

   ```shell
   mv crx-quickstart/oak-repository/segmentstore crx-quickstart/repository/segmentstore
   ```

1. Copie também o armazenamento de dados:

   ```shell
   mv crx-quickstart/repository/repository/datastore crx-quickstart/repository/datastore
   ```

1. Em seguida, é necessário criar a pasta que conterá as configurações do OSGi que serão usadas com a nova instância atualizada. Mais especificamente, uma pasta chamada install precisa ser criada em **crx-quickstart**.

1. Agora, crie o armazenamento de nó e o armazenamento de dados que serão usados com o AEM 6.3. Você pode fazer isso criando dois arquivos com os seguintes nomes em **crx-quickstart\install**:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`

   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Esses dois arquivos configurarão AEM para usar um armazenamento de nó TarMK e um armazenamento de dados File.

1. Edite os arquivos de configuração para prepará-los para uso. Mais especificamente:

   * Adicione a seguinte linha em **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**:

      `customBlobStore=true`

   * Em seguida, adicione as seguintes linhas a **org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**:

      ```
      path=./crx-quickstart/repository/datastore
       minRecordLength=4096
      ```

1. Remova o modo de execução crx2 executando:

   ```shell
   find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \
   ```

1. Agora é necessário alterar os modos de execução no arquivo war AEM 6.3. Para fazer isso, primeiro crie uma pasta temporária que estará hospedando a guerra AEM 6.3. O nome da pasta neste exemplo será **temp**. Depois que o arquivo war for copiado, extraia seu conteúdo executando de dentro da pasta temporária:

   ```shell
   jar xvf aem-quickstart-6.3.0.war
   ```

1. Depois que o conteúdo tiver sido extraído, vá para a variável **WEB-INF** e edite a `web.xml` para alterar os modos de execução. Para localizar o local em que estão definidos no XML, procure a variável `sling.run.modes` string. Depois de encontrá-lo, altere os modos de execução na próxima linha de código, que por padrão é definida como author:

   ```shell
   <param-value >author</param-value>
   ```

1. Altere o valor do autor acima e defina os modos de execução como: author,crx3,crx3tar O bloco final de código deve ter esta aparência:

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. Recrie o jar com o conteúdo modificado:

   ```shell
   jar cvf aem62.war
   ```

1. Finalmente, implante o novo arquivo war:

   ```shell
   cp temp/aem62.war jboss-install-folder/standalone/deployments/aem61.war
   ```
