---
title: Instalação independente personalizada
seo-title: Instalação independente personalizada
description: 'Saiba mais sobre as opções disponíveis ao instalar uma instância AEM independente. '
seo-description: 'Saiba mais sobre as opções disponíveis ao instalar uma instância AEM independente. '
uuid: e1cb45c4-3b2b-4951-8f67-213072e825b3
contentOwner: Tyler Rushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: c9e51008-6009-49a2-9c74-1c610cef2e7f
translation-type: tm+mt
source-git-commit: b7e5c42009acb5044d1112e66b8e65b528355736
workflow-type: tm+mt
source-wordcount: '1523'
ht-degree: 1%

---


# Instalação independente personalizada{#custom-standalone-install}

Esta seção descreve as opções disponíveis ao instalar uma instância AEM independente. Você também pode ler Elementos [de](/help/sites-deploying/storage-elements-in-aem-6.md) Armazenamento para obter mais informações sobre como escolher o tipo de armazenamento de backend depois de instalar o AEM 6 recentemente.

## Alteração do número da porta renomeando o arquivo {#changing-the-port-number-by-renaming-the-file}

A porta padrão para AEM é 4502. Se essa porta não estiver disponível ou já estiver em uso, o Quickstart se configura automaticamente para usar o primeiro número de porta disponível da seguinte forma: 4502, 8080, 8081, 8082, 8083, 8084, 8085, 8888, 9362, `<random>`.

Você também pode definir o número da porta renomeando o arquivo jar quickstart, para que o nome do arquivo inclua o número da porta; por exemplo, `cq5-publish-p4503.jar` ou `cq5-author-p6754.jar`.

Há várias regras a serem seguidas ao renomear o arquivo jar quickstart:

* Ao renomear o arquivo, ele deve ser start `cq;` como em `cq5-publish-p4503.jar`.

* É recomendável que você *sempre* prefixe o número da porta com -p; como em cq5-publish-p4503.jar ou cq5-author-p6754.jar.

>[!NOTE]
>
>Isso garante que você não precise se preocupar em cumprir as regras usadas para extrair o número da porta:
>
>* o número da porta deve ser de 4 ou 5 dígitos
>* esses dígitos devem vir depois de um traço
>* se houver outros dígitos no nome do arquivo, o número da porta deverá ter o prefixo `-p`
>* o prefixo &quot;cq5&quot; no início do nome de arquivo é ignorado

>



>[!NOTE]
>
>Você também pode alterar o número da porta usando a `-port` opção no comando start.

## Modos de execução {#run-modes}

**Os modos** de execução permitem ajustar sua instância de AEM para uma finalidade específica; por exemplo, autor ou publicação, teste, desenvolvimento, intranet etc. Esses modos também permitem controlar o uso de conteúdo de amostra. Esse conteúdo de amostra é definido antes da criação da inicialização rápida e pode incluir pacotes, configurações etc. Isso pode ser especialmente útil para instalações prontas para produção quando você deseja manter sua instalação limpa e sem conteúdo de amostra. Para obter mais informações, consulte:

* [Modos de execução](/help/sites-deploying/configure-runmodes.md)

## Adicionando um provedor de instalação de arquivo {#adding-a-file-install-provider}

Por padrão, a pasta `crx-quickstart/install` é monitorada em busca de arquivos.\
Essa pasta não existe, mas simplesmente pode ser criada em tempo de execução.

Se um pacote, uma configuração ou um pacote de conteúdo for colocado nesse diretório, ele será automaticamente selecionado e instalado. Se for removido, ele será desinstalado.\
É outra maneira de colocar pacotes, pacotes de conteúdo ou configurações no repositório.

Isso é especialmente interessante para vários casos de uso:

* Durante o desenvolvimento, pode ser mais fácil colocar algo no sistema de arquivos.
* Se algo der errado, o console da Web e o repositório não poderão ser acessados. Com isso, você pode colocar pacotes adicionais neste diretório e eles devem ser instalados.
* A `crx-quickstart/install` pasta pode ser criada antes do início rápido e pacotes adicionais podem ser colocados lá.

>[!NOTE]
>
>Consulte também [Como instalar pacotes CRX automaticamente na inicialização](https://helpx.adobe.com/experience-manager/kb/HowToInstallPackagesUsingRepositoryInstall.html) do servidor para obter exemplos.

## Instalação e inicialização do Adobe Experience Manager como um serviço do Windows {#installing-and-starting-adobe-experience-manager-as-a-windows-service}

>[!NOTE]
>
>Certifique-se de executar o procedimento a seguir enquanto estiver conectado como Administrador ou start/executar essas etapas usando a seleção do menu de contexto **Executar como Administrador** .
>
>Fazer logon como um usuário com privilégios de administrador é **insuficiente**. Se você não estiver conectado como Administrador ao concluir essas etapas, você receberá erros de **Acesso negado** .

Para instalar e start AEM como um serviço do Windows:

1. Abra o arquivo crx-quickstart\opt\helpers\instsrv.bat em um editor de texto.
1. Se você estiver configurando um servidor Windows de 64 bits, substitua todas as instâncias de prunsrv por um dos seguintes comandos, de acordo com seu sistema operacional:

   * prunsrv_amd64
   * prunsrv_ia64

   Este comando chama o script apropriado que start o daemon de serviço do Windows em Java de 64 bits em vez de Java de 32 bits.

1. Para evitar que o processo seja direcionado para mais de um processo, aumente o tamanho máximo do heap e os parâmetros JVM PermGen. Localize o `set jvm_options` comando e defina o valor da seguinte forma:

   `set jvm_options=-XX:MaxPermSize=256M;-Xmx1792m`

1. Abra o prompt de comando, altere o diretório atual para a pasta crx-quickstart/opt/helpers da instalação AEM e digite o seguinte comando para criar o serviço:

   `instsrv.bat cq5`

   Para verificar se o serviço foi criado, abra Serviços no painel de controle Ferramentas administrativas ou digite `start services.msc` em Prompt de comando. O serviço cq5 é exibido na lista.

1. Start o serviço executando um dos procedimentos a seguir:

   * No painel de controle de serviços, clique em cq5 e clique em Start.

   ![chlimage_1-71](assets/chlimage_1-71.png)

   * Na linha de comando, digite net start cq5.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. O Windows indica que o serviço está em execução. AEM start e o executável prunsrv é exibido no Tarefa Manager. No navegador da Web, navegue até AEM, por exemplo, `http://localhost:4502` para start usando AEM.

   ![chlimage_1-73](assets/chlimage_1-73.png)

>[!NOTE]
>
>Os valores de propriedade no arquivo instsrv.bat são usados ao criar o serviço do Windows. Se você editar os valores de propriedade em instsrv.bat, será necessário desinstalar e reinstalar o serviço.

>[!NOTE]
>
>Ao instalar AEM como serviço, você deve fornecer o caminho absoluto para o diretório de registros no `com.adobe.xmp.worker.files.ncomm.XMPFilesNComm` do Configuration Manager.

Para desinstalar o serviço, clique em **Parar** no painel de controle **Serviços** ou na linha de comando, navegue até a pasta e digite `instsrv.bat -uninstall cq5`. O serviço é removido da lista no painel de controle **Serviços** ou da lista na linha de comando quando você digita `net start`.

## Redefinição do local do diretório de trabalho temporário {#redefining-the-location-of-the-temporary-work-directory}

O local padrão da pasta temporária da máquina java é `/tmp`. AEM também usa essa pasta, por exemplo, ao criar pacotes.

Se você quiser alterar o local da pasta temporária (por exemplo, se precisar de um diretório com mais espaço livre), defina um local `<new-tmp-path>` adicionando o parâmetro JVM:

`-Djava.io.tmpdir="/<new-tmp-path>"`

para:

* linha de comando de inicialização do servidor
* o parâmetro do ambiente CQ_JVM_OPTS no script serverctl ou start

## Outras opções disponíveis no arquivo Quickstart {#further-options-available-from-the-quickstart-file}

Outras opções e convenções de renomeação estão descritas no arquivo de ajuda do Quickstart, que está disponível por meio da opção -help. Para acessar a ajuda, digite:

* `java -jar cq5-<version>.jar -help`

```shell
Loading quickstart properties: default
Loading quickstart properties: instance
Setting properties from filename '/Users/Desktop/AEM/cq-quickstart-5.6.0.jar'
--------------------------------------------------------------------------------
Adobe Experience Manager Quickstart (build 20130129)                            
--------------------------------------------------------------------------------
Usage:                                                                          
 Use these options on the Quickstart command line.                              
--------------------------------------------------------------------------------

-help (--help,-h)
         Show this help message                                                 
-quickstart.server.port (-p,-port) <port>
         Set server port number                                                 
-contextpath (-c,-org.apache.felix.http.context_path) <contextpath>
         Set context path                                                       
-debug <port>
         Enable Java Debugging on port number; forces forking                   
-gui 
         Show GUI if running on a terminal                                      
-nobrowser (-quickstart.nobrowser)
         Do not open browser at startup                                         
-unpack
         Unpack installation files only, do not start the server (implies       
         -verbose)                                                              
-v (-verbose)
         Do not redirect stdout/stderr to files and do not close stdin          
-nofork
         Do not fork the JVM, even if not running on a console                  
-fork
         Force forking the JVM if running on a console, using recommended       
         default memory settings for the forked JVM.                            
-forkargs <args> [<args> ...]
         Additional arguments for the forked JVM, defaults to '-Xmx1024m        
         -XX:MaxPermSize=256m '.  Use -- to specify values starting with -,     
         example: '-forkargs -- -server'                                        
-a (--interface) <interface>
         Optional IP address (interface) to bind to                             
-pt <string>
         Process type (main/fork) - do not use directly, used when forking a    
         process                                                                
-r <string> [<string> [<string> [<string> [<string> [<string> [<string> [<string> [<string> [<string>]]]]]]]]]
         Runmode(s) - Use this to define the run mode(s)                        
-b <string>
         Base folder - defines the path under which the quickstart work folder  
         is created                                                             
-low-mem-action <string>
         Low memory action - what to do if memory is insufficient at startup    
-use-control-port
         Start a control port                                                   
-ll <level>
         Define launchpad log level (1 = error...4 = debug)                     
--------------------------------------------------------------------------------
Quickstart filename options                                                     
--------------------------------------------------------------------------------
Usage:                                                                          
 Rename the jar file, including one of the patterns shown below, to set the     
corresponding option. Command-line options have priority on these filename      
patterns.                                                                       
--------------------------------------------------------------------------------

-NNNN
         Include -NNNN.jar or -pNNNN in the renamed jar filename to run on port 
         NNNN, for example: quickstart-8085.jar                                 
-nobrowser
         Include -nobrowser in the renamed jar filename to avoid opening the    
         browser at startup, example: quickstart-nobrowser-8085.jar             
-publish
         Include -publish in the renamed jar filename to run cq5 in "publish"   
         mode, example: cq5-publish-7502.jar                                    
--------------------------------------------------------------------------------
The license.properties file
--------------------------------------------------------------------------------
  The license.properties file stores licensing information, created from the    
  licensing form displayed on first startup and stored in the folder from where 
  Quickstart is run.                                                            
--------------------------------------------------------------------------------
Log files
--------------------------------------------------------------------------------
  Once Quickstart has been unpacked and started, log files can be found under   
  ./crx-quickstart/logs.                                                        
--------------------------------------------------------------------------------
```

## Instalação do AEM no ambiente Amazon EC2 {#installing-aem-in-the-amazon-ec-environment}

Ao instalar o AEM em uma instância da Amazon Elastic Compute Cloud (EC2), se você instalar o autor e publicar na instância EC2, a instância Autor será instalada corretamente seguindo o procedimento sobre como [instalar uma instância da AEM](/help/sites-deploying/custom-standalone-install.md); no entanto, a instância Publicar se torna Autor.

Antes de instalar a instância Publicar no ambiente EC2, faça o seguinte:

1. Descompacte o arquivo jar para a instância de Publicação antes de iniciar a instância pela primeira vez. Para desempacotar o arquivo, use o seguinte comando:

   ```xml
   java -jar quickstart.jar -unpack
   ```

   >[!NOTE]
   >
   >Se você alterar o modo **após** iniciar a instância pela primeira vez, não poderá alterar o modo de execução.

1. Start a instância executando:

   ```xml
   java -jar quickstart.jar -r publish
   ```

   >[!CAUTION]
   >
   >Certifique-se de executar a instância primeiro após descompactá-la executando o comando acima. Caso contrário, o preenchimento quickstart.properties não será gerado. Sem esse arquivo, qualquer atualização futura de AEM falhará.

1. Na pasta **bin** , abra o script do **start** e verifique a seguinte seção:

   ```xml
   # runmode(s)
   if [ -z "$CQ_RUNMODE" ]; then
    CQ_RUNMODE='author'
   fi
   ```

1. Altere o modo de execução para **publicar** e salvar o arquivo.

   ```xml
   # runmode(s)
   if [ -z "$CQ_RUNMODE" ]; then
    CQ_RUNMODE='publish'
   fi
   ```

1. Pare a instância e reinicie-a executando o script do **start** .

## Verificando a instalação {#verifying-the-installation}

Os links a seguir podem ser usados para verificar se a instalação está operacional (todos os exemplos são baseados na execução da instância na porta 8080 do host local, na instalação do CRX em /crx e Launchpad em /):

* `http://localhost:8080/crx/de`

   O console CRXDE Lite.

* `http://localhost:8080/system/console`

   O Console da Web.

## Ações após a instalação {#actions-after-installation}

Embora haja muitas possibilidades de configurar AEM WCM, determinadas ações devem ser tomadas ou, pelo menos, revistas imediatamente após a instalação:

* Consulte a Lista de verificação [de](/help/sites-administering/security-checklist.md) segurança para obter as tarefas necessárias para garantir que seu sistema permaneça seguro.
* Analise a lista de usuários e grupos padrão instalados com AEM WCM. Verifique se você deseja executar ações em qualquer outra conta - consulte [Segurança e Administração](/help/sites-administering/security.md) do usuário para obter mais detalhes.

## Acesso ao CRXDE Lite e ao Console da Web {#accessing-crxde-lite-and-the-web-console}

Depois que AEM WCM tiver sido iniciado, você também poderá acessar:

* [CRXDE Lite](#accessing-crxde-lite) - usado para acessar e gerenciar o repositório
* [Console](#accessing-the-web-console) da Web - usado para gerenciar ou configurar os pacotes OSGi (também conhecido como console OSGi)

### Acesso ao CRXDE Lite {#accessing-crxde-lite}

Para abrir o CRXDE Lite, você pode selecionar **CRXDE Lite** na tela de boas-vindas ou usar o navegador para navegar até

```
 https://<<i>host</i>>:<<i>port</i>>/crx/de/index.jsp
```

Por exemplo:\
`http://localhost:4502/crx/de/index.jsp` ``

![installcq_crxdelite](assets/installcq_crxdelite.png)

### Acessar o Console da Web {#accessing-the-web-console}

Para acessar o console da Web do Adobe CQ, você pode selecionar o Console **do** OSGi na tela de boas-vindas ou usar o navegador para navegar até

```
 https://<<i>host</i>>:<<i>port</i>>/system/console
```

Por exemplo:\
`http://localhost:4502/system/console`\
ou para a página Pacotes\
`http://localhost:4502/system/console/bundles`

![chlimage_1-74](assets/chlimage_1-74.png)

Consulte Configuração do [OSGi com o Console](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) da Web para obter mais detalhes.

## Resolução de Problemas{#troubleshooting}

Para obter informações sobre como lidar com problemas que podem surgir durante a instalação, consulte:

* [Resolução de Problemas](/help/sites-deploying/troubleshooting.md)

## Uninstalling Adobe Experience Manager {#uninstalling-adobe-experience-manager}

Como AEM é instalado em um único diretório, não há necessidade de um utilitário de desinstalação. A desinstalação pode ser tão simples quanto excluir o diretório de instalação inteiro, embora a maneira como você desinstala o AEM dependa do que você deseja obter e do armazenamento persistente que você usa.

Se o armazenamento persistente estiver incorporado no diretório de instalação, por exemplo, na instalação padrão do TarPM, a exclusão de pastas também removerá os dados.

>[!NOTE]
>
>O Adobe recomenda que você faça backup do repositório antes de excluir AEM. Se você excluir todo o &lt;cq-installation-diretory>, excluirá o repositório. Para manter os dados do repositório antes de excluir, mova ou copie a pasta &lt;cq-installation-diretory>/crx-quickstart/repository em outro lugar antes de excluir as outras pastas.

Se a instalação do AEM usar um armazenamento externo, por exemplo, um servidor de banco de dados, a remoção da pasta não removerá os dados automaticamente, mas removerá a configuração do armazenamento, o que dificulta a restauração do conteúdo do JCR.
