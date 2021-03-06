---
title: Instalação e configuração de fluxo de trabalho centrado no Forms no OSGi
seo-title: Instalação e configuração de fluxo de trabalho centrado no Forms no OSGi
description: 'Instale e configure as Comunicações interativas do AEM Forms para criar correspondências comerciais, documentos, declarações, avisos de benefícios, emails de marketing, contas e kits de boas-vindas. '
seo-description: 'Instale e configure as Comunicações interativas do AEM Forms para criar correspondências comerciais, documentos, declarações, avisos de benefícios, emails de marketing, contas e kits de boas-vindas. '
uuid: 847c3351-dc46-4e60-a023-0f4e9e057c7c
topic-tags: installing
discoiquuid: 7333641e-8c8c-4b52-a7da-a2976c88592c
role: Admin
exl-id: 308b106f-4c5a-49d6-a7f6-c1e8a0bf62e9
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 5%

---

# Instalação e configuração de fluxo de trabalho centrado no Forms no OSGi {#installing-and-configuring-forms-centric-workflow-on-osgi}

## Introdução {#introduction}

As empresas coletam e processam dados de vários formulários, sistemas de back-end e outras fontes de dados. O processamento de dados envolve procedimentos de revisão e aprovação, tarefas repetitivas e arquivamento de dados. Por exemplo, revisar um formulário e convertê-lo em documento PDF. Quando feitas manualmente, as tarefas repetitivas podem levar muito tempo e recursos.

Você pode usar o [fluxo de trabalho centrado no Forms no OSGi](/help/forms/using/aem-forms-workflow.md) para criar rapidamente fluxos de trabalho adaptáveis baseados em formulários. Esses workflows podem ajudar você a automatizar workflows de revisão e aprovação, workflows de processos comerciais e outras tarefas repetitivas. Esses fluxos de trabalho também ajudam a processar documentos (criar, montar, distribuir e arquivar documentos PDF, adicionar assinaturas digitais para limitar o acesso a documentos, decodificar formulários com códigos de barras e muito mais) e usar o fluxo de trabalho de assinatura Adobe Sign com formulários e documentos.

Após a configuração, esses workflows podem ser acionados manualmente para concluir um processo definido ou serem executados de forma programática quando os usuários enviam um formulário ou uma comunicação interativa. O recurso está incluído no pacote complementar do AEM Forms.

O AEM Forms é uma plataforma avançada de nível empresarial. O fluxo de trabalho centrado na Forms no OSGi é apenas um dos recursos do AEM Forms. Para obter a lista completa de recursos, consulte [Introdução ao AEM Forms](/help/forms/using/introduction-aem-forms.md).

>[!NOTE]
>
>Com o fluxo de trabalho centrado na Forms no OSGi, você pode criar e implantar rapidamente fluxos de trabalho para várias tarefas na pilha OSGi, sem precisar instalar o recurso completo de Gerenciamento de processos na pilha JEE. Consulte uma [comparação](/help/forms/using/capabilities-osgi-jee-workflows.md) dos fluxos de trabalho de AEM centrados na Forms no OSGi e no Gerenciamento de processos no JEE para saber mais sobre as diferenças e semelhanças nos recursos.
>
>Após a comparação, se você optar por instalar o recurso de Gerenciamento de processos na pilha JEE, consulte [Instalar ou atualizar o AEM Forms no JEE](/help/forms/home.md) para obter informações detalhadas sobre a instalação e configuração da pilha JEE e os recursos de Gerenciamento de processos.

## Topologia de implantação {#deployment-topology}

O pacote do complemento AEM Forms é um aplicativo implantado em AEM. Você precisa de apenas um mínimo de uma instância de Autor ou Processamento do AEM (autor de produção) para executar o fluxo de trabalho centrado no Forms no recurso OSGi. Uma instância de processamento é uma instância [endurecida do AEM Author](/help/forms/using/hardening-securing-aem-forms-environment.md). Não execute nenhuma criação real, como a criação de fluxos de trabalho ou formulários adaptáveis, no autor da produção.

A topologia a seguir é indicativa para executar as Comunicações interativas da AEM Forms, o Gerenciamento de correspondência, a captura de dados da AEM Forms e o fluxo de trabalho centrado na Forms nos recursos OSGi. Para obter informações detalhadas sobre a topologia, consulte [Topologias de arquitetura e implantação para AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![topologia recomendada](assets/recommended-topology.png)

O fluxo de trabalho centrado no Forms do AEM Forms no OSGi executa AEM Caixa de entrada e AEM interface do usuário de criação do modelo de fluxo de trabalho nas instâncias de autor do AEM Forms.

## Requisitos do sistema {#system-requirements}

>[!NOTE]
>
>Pule para a seção [Próximas etapas](#next-steps) do documento, se você já tiver instalado o AEM Forms no OSGi, conforme explicado no artigo [instalar e configurar recursos de captura de dados](/help/forms/using/installing-configuring-aem-forms-osgi.md).

Antes de começar a instalar e configurar o fluxo de trabalho centrado no Forms no OSGi, verifique se:

* A infraestrutura de hardware e software está em vigor. Para obter uma lista detalhada de hardware e software suportados, consulte [requisitos técnicos](/help/sites-deploying/technical-requirements.md).

* O caminho de instalação da instância de AEM não contém espaços em branco.
* Uma instância de AEM está em execução. Na terminologia AEM, uma &quot;instância&quot; é uma cópia do AEM em execução em um servidor no modo de criação ou publicação. Você precisa de pelo menos uma instância AEM (Autor ou Processamento) para executar o fluxo de trabalho centrado no Forms no OSGi:

   * **Autor**: Uma instância AEM usada para criar, carregar e editar conteúdo e administrar o site. Quando o conteúdo estiver pronto para entrar em funcionamento, ele será replicado para a instância de publicação.
   * **Processamento:** uma instância de processamento é uma instância  [AEM ](/help/forms/using/hardening-securing-aem-forms-environment.md) Author com proteção. Você pode configurar uma instância de Autor e endurecê-la após executar a instalação.
   * **Publicar**: Uma instância de AEM que disponibiliza o conteúdo publicado ao público pela Internet ou por uma rede interna.

* Os requisitos de memória são cumpridos. O pacote do complemento AEM Forms requer:

   * 15 GB de espaço temporário para instalações baseadas no Microsoft Windows.
   * 6 GB de espaço temporário para instalações baseadas em UNIX.

* Requisitos adicionais para sistemas baseados em UNIX: Se você estiver usando o sistema operacional baseado em UNIX, instale os seguintes pacotes da mídia de instalação do respectivo sistema operacional.

<table> 
 <tbody>
  <tr>
   <td>expatriado</td> 
   <td>libxcb</td> 
   <td>freetype</td> 
   <td>libXau</td> 
  </tr>
  <tr>
   <td>libSM</td> 
   <td>zlib</td> 
   <td>libICE</td> 
   <td>libuuid</td> 
  </tr>
  <tr>
   <td>glibc</td> 
   <td>libXext</td> 
   <td><p>nss-softokn-freebl</p> </td> 
   <td>fontconfig</td> 
  </tr>
  <tr>
   <td>libX11</td> 
   <td>libXrender</td> 
   <td>libXrandr</td> 
   <td>libXinerama</td> 
  </tr>
 </tbody>
</table>

## Instalar o pacote complementar do AEM Forms {#install-aem-forms-add-on-package}

O pacote do complemento AEM Forms é um aplicativo implantado em AEM. O pacote contém um fluxo de trabalho centrado no Forms no OSGi e outros recursos. Execute as seguintes etapas para instalar o pacote complementar:

1. Abra a [Distribuição de softwares](https://experience.adobe.com/downloads). Você precisa de uma Adobe ID para fazer logon na Distribuição de softwares.
1. Clique em **[!UICONTROL Adobe Experience Manager]** disponível no menu de cabeçalho.
1. Na seção **[!UICONTROL Filtros]**:
   1. Selecione **[!UICONTROL Forms]** na lista suspensa **[!UICONTROL Solução]**.
   2. Selecione a versão e o tipo do pacote. Você também pode usar a opção **[!UICONTROL Pesquisar downloads]** para filtrar os resultados.
1. Toque no nome do pacote aplicável ao seu sistema operacional, selecione **[!UICONTROL Aceitar Termos do EULA]** e toque em **[!UICONTROL Download]**.
1. Abra [Gerenciador de pacotes](https://docs.adobe.com/content/help/br/experience-manager-65/administering/contentmanagement/package-manager.html) e clique em **[!UICONTROL Fazer upload de pacote]** para fazer upload do pacote.
1. Selecione o pacote e clique em **[!UICONTROL Instalar]**.

   Você também pode baixar o pacote por meio do link direto listado no artigo [AEM Forms releases](https://helpx.adobe.com/br/aem-forms/kb/aem-forms-releases.html).

1. Depois que o pacote for instalado, você será solicitado a reiniciar a instância do AEM. **Não reinicie imediatamente o servidor.** Antes de parar o servidor do AEM Forms, aguarde até que as mensagens ServiceEvent REGISTERED e ServiceEvent UNREGISTERED parem de aparecer no arquivo  [AEM-Installation-Diretory]/crx-quickstart/logs/error.log e o log seja estável.
1. Repita as etapas de 1 a 7 em todas as instâncias de Autor e Publicação.

## Configurações pós-instalação {#post-installation-configurations}

O AEM Forms tem algumas configurações obrigatórias e opcionais. As configurações obrigatórias incluem a configuração de bibliotecas BouncyCastle e o agente de serialização. As configurações opcionais incluem a configuração do dispatcher e do Adobe Target.

### Configurações obrigatórias pós-instalação {#mandatory-post-installation-configurations}

#### Configurar bibliotecas RSA e BouncyCastle  {#configure-rsa-and-bouncycastle-libraries}

Execute as seguintes etapas em todas as instâncias de Autor e Publicação para inicializar e delegar as bibliotecas:

1. Pare a instância AEM subjacente.
1. Abra o [AEM diretório de instalação]\crx-quickstart\conf\sling.properties para edição.

   Se você usou [AEM diretório de instalação]\crx-quickstart\bin\start.bat para iniciar o AEM, edite o sling.properties localizado em [AEM_root]\crx-quickstart\.

1. Adicione as seguintes propriedades ao arquivo sling.properties :

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (Somente para AIX) Adicione as seguintes propriedades ao arquivo sling.properties :

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Salve e feche o arquivo e inicie a instância de AEM.
1. Repita as etapas de 1 a 4 em todas as instâncias de Autor e Publicação.

#### Configurar o agente de serialização {#configure-the-serialization-agent}

Execute as seguintes etapas em todas as instâncias de Autor e Publicação para adicionar o pacote à  de lista de permissões:

1. Abra AEM Configuration Manager em uma janela do navegador. O URL padrão é `https://[server]:[port]/system/console/configMgr`.
1. Pesquise e abra **Configuração do Firewall de Deserialização**.
1. Adicione o pacote **sun.util.calendar** ao campo **lista de permissões**. Clique em Salvar.
1. Repita as etapas de 1 a 3 em todas as instâncias de Autor e Publicação.

### Configurações opcionais pós-instalação {#optional-post-installation-configurations}

#### Configurar o Dispatcher {#configure-dispatcher}

O Dispatcher está armazenando em cache e na ferramenta de balanceamento de carga para AEM. AEM Dispatcher também ajuda a proteger AEM servidor contra ataques. Você pode aumentar a segurança da sua instância do AEM usando o Dispatcher em conjunto com um servidor da Web de classe empresarial. Se você usar [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html), execute as seguintes configurações para o AEM Forms:

1. Configuração do acesso para AEM Forms:

   Abra o arquivo dispatcher.any para edição. Navegue até a seção de filtro e adicione o seguinte filtro à seção de filtro:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Salve e feche o arquivo. Para obter informações detalhadas sobre filtros, consulte a [documentação do Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Configure o serviço de filtro do referenciador:

   Faça logon no gerenciador de configuração do Apache Felix como administrador. O URL padrão do gerenciador de configuração é `https://[server]:[port_number]/system/console/configMgr`. No menu **Configurations**, selecione a opção **Apache Sling Referrer Filter**. No campo Permitir hosts , insira o nome do host do dispatcher para permitir como referenciador e clique em **Salvar**. O formato da entrada é `https://[server]:[port]`.

#### Configurar cache {#configure-cache}

O armazenamento em cache é um mecanismo para reduzir o tempo de acesso aos dados, reduzir a latência e melhorar as velocidades de entrada/saída (I/O). O cache de formulários adaptáveis armazena somente o conteúdo HTML e a estrutura JSON de um formulário adaptável sem salvar dados pré-preenchidos. Ajuda a reduzir o tempo necessário para renderizar um formulário adaptável.

* Ao usar o cache de formulários adaptáveis, use o [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) para armazenar em cache as bibliotecas de clientes (CSS e JavaScript) de um formulário adaptável.
* Ao desenvolver componentes personalizados, mantenha o cache de formulários adaptáveis desativado no servidor usado para desenvolvimento.

Execute as seguintes etapas para configurar o cache de formulários adaptáveis:

1. Vá para AEM gerenciador de configuração do console da Web em `https://[server]:[port]/system/console/configMgr`.
1. Clique em **[!UICONTROL Adaptive Form e Interative Communication Web Channel Configuration]** para editar seus valores de configuração. Na caixa de diálogo editar valores de configuração, especifique o número máximo de formulários ou documentos que uma instância do servidor do AEM Forms pode armazenar em cache no campo **Number of Adaptive Forms**. O valor padrão é 100. Clique em **Salvar**.

   >[!NOTE]
   >
   >Para desativar o cache, defina o valor no campo Number of Adaptive Forms como **0**. O cache é redefinido e todos os formulários e documentos são removidos do cache quando você desativa ou altera a configuração do cache.

#### Configurar o Adobe Sign {#configure-adobe-sign}

O Adobe Sign habilita fluxos de trabalho de assinatura eletrônica para formulários adaptáveis. As assinaturas eletrônicas melhoram os fluxos de trabalho para processar documentos para áreas legais, de vendas, de folha de pagamento, de gerenciamento de recursos humanos e muitas outras.

Em um fluxo de trabalho típico centrado no Adobe Sign e no Forms no OSGi, um usuário preenche um formulário adaptável para se candidatar a um serviço. Por exemplo, um aplicativo de cartão de crédito e um formulário de benefícios para o cidadão. Quando um usuário preenche, envia e assina o formulário de aplicativo, um fluxo de trabalho de aprovação/rejeição é iniciado. O provedor de serviços revisa o aplicativo AEM Caixa de entrada e usa o Adobe Sign para assinar eletronicamente o aplicativo. Para ativar fluxos de trabalho de assinatura eletrônica semelhantes, você pode integrar o Adobe Sign com o AEM Forms.

Para usar o Adobe Sign com AEM Forms, [Integre o Adobe Sign com AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

## Próximas etapas {#next-steps}

Você configurou um ambiente para usar um fluxo de trabalho centrado no Forms em recursos OSGi. Agora, as etapas para usar o recurso são:

* [Uso de fluxos de trabalho centrados no Forms no OSGi](/help/forms/using/aem-forms-workflow.md)
* [Referência da Etapa do fluxo de trabalho](/help/sites-developing/workflows-step-ref.md)
* [Pós-processamento de cartas e comunicações interativas](/help/forms/using/submit-letter-topostprocess.md)
