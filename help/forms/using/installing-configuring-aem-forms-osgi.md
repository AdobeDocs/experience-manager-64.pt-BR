---
title: Instalar e configurar os recursos de captura de dados
seo-title: Instalar e configurar os recursos de captura de dados
description: Instale e configure formulários adaptáveis, PDF forms e HTML5 Forms. Configure o Adobe Analytics e o Adobe Target para formulários adaptáveis para analisar o uso de formulários e usuários de públicos alvos com base em seus perfis.
seo-description: Instale e configure formulários adaptáveis, PDF forms e HTML5 Forms. Configure o Adobe Analytics e o Adobe Target para formulários adaptáveis para analisar o uso de formulários e usuários de públicos alvos com base em seus perfis.
uuid: ce253b5a-eeb2-47d2-a6c9-e6f59384159a
contentOwner: khsingh
topic-tags: installing
discoiquuid: 1bb8360c-5543-484e-9712-590822211298
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '1836'
ht-degree: 1%

---


# Instalar e configurar os recursos de captura de dados {#install-and-configure-data-capture-capabilities}

Instale e configure formulários adaptáveis, PDF forms e HTML5 Forms. Configure o Adobe Analytics e o Adobe Target para formulários adaptáveis para analisar o uso de formulários e usuários de públicos alvos com base em seus perfis.

## Introdução {#introduction}

A AEM Forms fornece um conjunto de formulários para obter dados do usuário final: formulários adaptáveis, HTML5 Forms e PDF forms. Ele também fornece ferramentas para lista de todos os formulários disponíveis em uma página da Web, análise do uso de formulários e usuários de públicos alvos com base em seus perfis. Esses recursos estão incluídos no pacote complementar AEM Forms. O pacote complementar é implantado em uma instância de autor ou publicação do AEM.

**Formulários adaptativos:** esses formulários mudam a aparência com base no tamanho da tela do dispositivo, são envolventes e interativos na natureza. O Forms adaptável também pode se integrar ao Adobe Analytics, Adobe Sign e Adobe Target. Isso permitiu que você fornecesse formulários personalizados e experiências orientadas a processos para usuários com base em sua demografia e outros recursos. Também é possível integrar formulários adaptáveis à Adobe Sign.

**Os** formulários PDF são adequados para impressão perfeita em pixels e captura de informações digitais em um documento PDF. No avatar digital, você pode usar o Adobe Acrobat ou o Acrobat Reader para preencher esses formulários. É possível hospedar esses formulários em seu site ou usar o portal de formulários para lista desses formulários em um site AEM. Você também pode enviar esses formulários por email para outras pessoas como anexos. Esses formulários são mais adequados para ambientes de desktop.

**Os formulários HTML5** são a versão compatível com o navegador dos PDF forms. O HTML5 Forms é adequado para ambientes que não suportam plug-ins PDF. O HTML5 Forms permite a renderização de formulários baseados em XFA em dispositivos móveis e navegadores de desktop nos quais o PDF baseado em XFA não é compatível. Esses formulários são mais adequados para tablets e ambientes para desktop.

A AEM Forms é uma plataforma poderosa de nível empresarial e a captura de dados (formulários adaptáveis, PDF forms e Forms HTML5) é apenas uma das capacidades da AEM Forms. Para obter a lista completa dos recursos, consulte [Introdução ao AEM Forms](/help/forms/using/introduction-aem-forms.md).

## Topologia de implantação {#deployment-topology}

O pacote complementar AEM Forms é um aplicativo implantado no AEM. É necessário apenas um mínimo de uma instância de autor e publicação de AEM para executar os recursos de captura de dados da AEM Forms. A topologia a seguir é sugerida para executar os recursos de captura de dados da AEM Forms AEM Forms. Para obter informações detalhadas sobre a topologia, consulte [Arquitetura e topologias de implantação para AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![topologia recomendada](assets/recommended-topology.png)

## Requisitos do sistema {#system-requirements}

Antes de começar a instalar e configurar o recurso de captura de dados AEM Forms, verifique se:

* A infraestrutura de hardware e software está em vigor. Para obter uma lista detalhada do hardware e software suportados, consulte [requisitos técnicos](/help/sites-deploying/technical-requirements.md).

* O caminho de instalação da instância AEM não contém espaços em branco.
* Uma instância AEM está ativa e em execução. Na terminologia AEM, uma &quot;instância&quot; é uma cópia da AEM em execução em um servidor no modo de autor ou publicação. Você precisa de pelo menos duas [AEM instâncias (um Autor e uma Publicação)](/help/sites-deploying/deploy.md) para executar os recursos de captura de dados da AEM Forms:

   * **Autor**: Uma instância AEM usada para criar, carregar e editar conteúdo e administrar o site. Depois que o conteúdo estiver pronto para entrar em funcionamento, ele será replicado para a instância de publicação.
   * **Publicar**: Uma instância AEM que serve o conteúdo publicado ao público pela internet ou por uma rede interna.

* Os requisitos de memória são atendidos. O pacote suplementar AEM Forms requer:

   * 15 GB de espaço temporário para instalações baseadas no Microsoft Windows.
   * 6 GB de espaço temporário para instalações baseadas em UNIX.

* A replicação reversa e a replicação para as instâncias de autor e publicação estão definidas. Para obter detalhes, consulte [Replicação](/help/sites-deploying/replication.md).
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
   <td>libuídio</td> 
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

## Instalar o pacote de complementos do AEM Forms {#install-aem-forms-add-on-package}

O pacote complementar AEM Forms é um aplicativo implantado no AEM. O pacote contém a captura de dados da AEM Forms e outros recursos. Execute as seguintes etapas para instalar o pacote complementar:

1. Abra [Distribuição de software](https://experience.adobe.com/downloads). Você precisa de uma Adobe ID para fazer logon na Software Distribution (Distribuição de software).
1. Toque em **[!UICONTROL Adobe Experience Manager]** disponível no menu de cabeçalho.
1. Na seção **[!UICONTROL Filtros]**:
   1. Selecione **[!UICONTROL Forms]** na lista suspensa **[!UICONTROL Solution]**.
   2. Selecione a versão e o tipo do pacote. Você também pode usar a opção **[!UICONTROL Pesquisar downloads]** para filtrar os resultados.
1. Toque no nome do pacote aplicável ao seu sistema operacional, selecione **[!UICONTROL Aceitar termos do EULA]** e toque em **[!UICONTROL Download]**.
1. Abra [Gerenciador de pacotes](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) e clique em **[!UICONTROL Carregar pacote]** para fazer upload do pacote.
1. Selecione o pacote e clique em **[!UICONTROL Instalar]**.

   Você também pode baixar o pacote por meio do link direto listado no artigo [Versões da AEM Forms](https://helpx.adobe.com/br/aem-forms/kb/aem-forms-releases.html).

1. Depois que o pacote for instalado, você será solicitado a reiniciar a instância AEM. **Não reinicie imediatamente o servidor.** Antes de parar o servidor AEM Forms, aguarde até que as mensagens ServiceEvent REGISTERED e ServiceEvent UNREGISTERED parem de aparecer no arquivo  [AEM-Installation-Diretory]/crx-quickstart/logs/error.log e o log esteja estável.
1. Repita as etapas de 1 a 7 em todas as instâncias de Autor e Publicação.

## Configurações pós-instalação {#post-installation-configurations}

A AEM Forms tem algumas configurações obrigatórias e opcionais. As configurações obrigatórias incluem a configuração das bibliotecas BouncyCastle e o agente de serialização. As configurações opcionais incluem configuração do dispatcher, portal da Forms, Adobe Sign, Adobe Analytics e Adobe Target.

### Configurações obrigatórias pós-instalação {#mandatory-post-installation-configurations}

#### Configurar bibliotecas RSA e BouncyCastle {#configure-rsa-and-bouncycastle-libraries}

Execute as seguintes etapas em todas as instâncias de Autor e Publicação para inicializar e delegar as bibliotecas:

1. Pare a instância AEM subjacente.
1. Abra o arquivo [AEM de instalação]\crx-quickstart\conf\sling.properties para edição.

   Se você usou [AEM diretório de instalação]\crx-quickstart\bin\start.bat para AEM de start, edite sling.properties localizado em [AEM_root]\crx-quickstart\.

1. Adicione as seguintes propriedades ao arquivo sling.properties:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (Somente para AIX) Adicione as seguintes propriedades ao arquivo sling.properties:

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Salve e feche o arquivo e start a instância AEM.
1. Repita as etapas de 1 a 4 em todas as instâncias de Autor e Publicação.

#### Configurar o agente de serialização {#configure-the-serialization-agent}

Execute as seguintes etapas em todas as instâncias de Autor e Publicação para adicionar o pacote à lista de permissões:

1. Abra AEM Configuration Manager em uma janela do navegador. O URL padrão é `https://[server]:[port]/system/console/configMgr`.
1. Procure e abra **[!UICONTROL Configuração do Firewall de Deserialização]**.
1. Adicione o pacote **[!UICONTROL sun.util.calendário]** ao campo **[!UICONTROL lista de permissões]**. Clique em **[!UICONTROL Salvar]**.
1. Repita as etapas de 1 a 3 em todas as instâncias de Autor e Publicação.

### Configurações opcionais pós-instalação {#optional-post-installation-configurations}

#### Configurar o Dispatcher {#configure-dispatcher}

O Dispatcher está em cache e na ferramenta de balanceamento de carga para AEM. AEM O Dispatcher também ajuda a proteger AEM servidor contra ataques. Você pode aumentar a segurança da sua instância de AEM usando o Dispatcher em conjunto com um servidor Web de classe empresarial. Se você usar [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html), execute as seguintes configurações para AEM Forms:

1. Configurar acesso para AEM Forms:

   Abra o arquivo dispatcher.any para edição. Navegue até a seção de filtro e adicione o seguinte filtro à seção de filtro:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Salve e feche o arquivo. Para obter informações detalhadas sobre filtros, consulte [Documentação do Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Configure o serviço de filtro de quem indicou:

   Faça logon no gerenciador de configuração Apache Felix como administrador. O URL padrão do gerenciador de configuração é `https://[server]:[port_number]/system/console/configMgr`. No menu **[!UICONTROL Configurações]**, selecione a opção **[!UICONTROL Filtro de Quem indicou Apache Sling]**. No campo Permitir hosts, digite o nome de host do dispatcher para permitir como uma quem indicou e clique em **[!UICONTROL Salvar]**. O formato da entrada é `https://[server]:[port]`.

#### Configurar cache {#configure-cache}

O cache é um mecanismo para reduzir os tempos de acesso aos dados, reduzir a latência e melhorar as velocidades de entrada/saída (E/S). O cache de formulários adaptáveis armazena somente o conteúdo HTML e a estrutura JSON de um formulário adaptável sem salvar os dados pré-preenchidos. Ajuda a reduzir o tempo necessário para renderizar um formulário adaptável.

* Ao usar o cache de formulários adaptáveis, use o [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) para armazenar em cache as bibliotecas de clientes (CSS e JavaScript) de um formulário adaptável.
* Ao desenvolver componentes personalizados, mantenha o cache de formulários adaptáveis desativado no servidor usado para desenvolvimento.

Execute as seguintes etapas para configurar o cache de formulários adaptáveis:

1. Vá para AEM gerenciador de configuração do console da Web em `https://[server]:[port]/system/console/configMgr`.
1. Clique em **[!UICONTROL Configuração de Canais Web de Formulário Adaptável e Comunicação Interativa]** para editar os valores de configuração. Na caixa de diálogo editar valores de configuração, especifique o número máximo de formulários ou documentos que uma instância do servidor AEM Forms pode armazenar em cache no campo **[!UICONTROL Número de adaptáveis Forms]**. O valor padrão é 100. Clique em **[!UICONTROL Salvar]**.

   >[!NOTE]
   >
   >Para desativar o cache, defina o valor no campo Número de adaptáveis Forms como **0**. O cache é redefinido e todos os formulários e documentos são removidos do cache quando você desativa ou altera a configuração do cache.

#### Configurar a comunicação SSL para o Modelo de Dados de Formulário {#configure-ssl-communcation-for-form-data-model}

Você pode habilitar a comunicação SSL para o Modelo de dados de formulário. Para ativar a comunicação SSL para o modelo de dados de formulário, antes de iniciar qualquer instância do AEM Forms, adicione certificados ao Java Trust Store de todas as instâncias. Você pode executar o comando abaixo para adicionar os certificados: &quot;

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

#### Configurar Adobe Sign {#configure-adobe-sign}

A Adobe Sign habilita workflows de assinatura eletrônica para formulários adaptáveis. As assinaturas eletrônicas melhoram os workflows para processar documentos para áreas legais, de vendas, de folha de pagamento, de gerenciamento de recursos humanos e muitas outras áreas.

Em um cenário típico de formulários adaptáveis e Adobe Sign, um usuário preenche um formulário adaptável para solicitar um serviço. Por exemplo, um aplicativo de cartão de crédito e um formulário de benefícios para o cidadão. Quando um usuário preenche, envia e assina o formulário de aplicativo, ele é enviado ao provedor de serviço para que seja tomada uma ação adicional. O provedor de serviço revisa o aplicativo e usa o Adobe Sign para marcar o aplicativo aprovado. Para habilitar workflows semelhantes de assinatura eletrônica, é possível integrar o Adobe Sign ao AEM Forms.

Para usar o Adobe Sign com o AEM Forms, [Integre o Adobe Sign ao AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

#### Configurar Adobe Analytics {#configure-adobe-analytics}

A AEM Forms integra-se à Adobe Analytics, que permite capturar e rastrear métricas de desempenho para seus formulários e documentos publicados. O objetivo da análise dessas métricas é tomar decisões informadas com base nos dados sobre as alterações necessárias para tornar os formulários ou o documento mais utilizáveis.

Para usar o Adobe Analytics com o AEM Forms, consulte [Configurar análises e relatórios](/help/forms/using/configure-analytics-forms-documents.md).

#### Integrar Adobe Target {#integrate-adobe-target}

Seus clientes provavelmente abandonarão um formulário se a experiência que ele oferece não for envolvente. Embora seja frustrante para os clientes, também pode aumentar o volume e o custo de suporte para a sua organização. É crítico e desafiador identificar e fornecer a experiência certa do cliente que aumenta a taxa de conversão. AEM formulários contêm a chave para esse problema.

Os formulários AEM se integram à Adobe Target, uma solução Adobe Marketing Cloud, para oferecer experiências personalizadas e envolventes aos clientes em vários canais digitais. Para usar o Adobe Target em formulários adaptativos de teste A/B, [Integre o Adobe Target ao AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

## Próximas etapas {#next-steps}

Você configurou um ambiente para usar os recursos de captura de dados da AEM Forms. Agora, os próximos passos para usar esse recurso são:

* [Criar seu primeiro formulário adaptável](/help/forms/using/create-your-first-adaptive-form.md)
* [Criar seu primeiro formulário PDF](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/pdf/designer-quickstart.pdf)
* [Introdução ao HTML5 Forms](/help/forms/using/introduction.md)

