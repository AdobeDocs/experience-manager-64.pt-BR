---
title: Notas de versão do Pacote de correções cumulativo AEM 6.4
description: Notas de versão específicas do Adobe Experience Manager 6.4 Cumulative Fix Packs.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 87843465e8e0b372dc457630b84bcb5e50628dea
workflow-type: tm+mt
source-wordcount: '2159'
ht-degree: 21%

---


# Notas de versão do AEM 6.4 Cumulative Fix Pack {#aem-cumulative-fix-pack-release-notes}

## Informações da versão {#release-information}

| Produtos | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versão | 6.4.8.1 |
| Tipo | Cumulative Fix Pack |
| Data | 04 de junho de 2020 |
| Pré-requisitos | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| URL de download | AEM 6.4.8.1 sobre distribuição [de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fcumulativefixpack%2Faem-6.4.8-cfp-1.0.zip) |

## O que está incluído no AEM 6.4.8.1 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.1 é uma atualização importante que inclui várias correções internas e de clientes desde a disponibilização geral do AEM 6.4 Service Pack 8 (6.4.8.0) em março de 2020.

AEM Cumulative Fix Pack 6.4.8.1 depende do AEM 6.4 Service Pack 8. Portanto, você deve instalar o pacote AEM Cumulative Fix Pack 6.4.8.1 após instalar AEM 6.4 Service Pack 8.

Alguns dos principais destaques do AEM 6.4.8.1 são:

* Remoção da integração do Compartilhamento de pacotes com o Adobe Experience Manager.
* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.21.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

## Lista de alterações {#list-of-changes}

O Adobe Experience Manager 6.4.8.1 fornece correções para os seguintes problemas.

### Sites {#sites-6481}

* Quando o nome de um componente local em um LiveCopy é idêntico ao nome de um componente no blueprint e o componente é lançado do blueprint, o termo _msm_move não é adicionado ao nome do componente local (NPR-33207).
* Os parâmetros anexados à solicitação original não são incluídos no URL de redirecionamento (NPR-33174).
* Quando a opção Coral.Select define emptyOption=true ou contém um item padrão com valor = &quot;&quot;, o arquivo dropdownshoide.js encontra um erro: TypeError não detectado: component.getValue não é uma função (NPR-33163).
* Quando um componente inclui outro componente como recurso de envio de dados, o espaço reservado do componente do container pai é substituído pelo espaço reservado dos componentes internos (NPR-33119).
* Quando você baseia um Fragmento de conteúdo em um schema e ele contém uma área de texto obrigatória ou um campo de caminho, o Fragmento de conteúdo não é salvo (NPR-33007)
* Ao criar um componente personalizado usando o componente de fragmento de experiência out-of-the-box e usá-lo em páginas de AEM Sites, AEM não exibe referências (uso) para o componente personalizado (NPR-32852).
* Quando uma página AEM Sites faz parte de um grande conjunto de conteúdo com várias cópias online, a pré-visualização do histórico de versão da página não é carregada (NPR-32772).
* Quando você promove uma inicialização, ele adiciona a combinação &quot;cq:LiveRelationship&quot; a cada componente adicionado na inicialização. Tem impacto em todas as inicializações, independentemente do lançamento com ou sem a seleção dos —  Herdar dados ao vivo da página de origem —  (NPR-32664).
* Quando start de paginação, o Seletor de fragmentos de experiência não carrega todos os itens (NPR-32605).
* Não é possível criar uma inicialização para uma página de AEM Sites. A criação de inicialização resulta em um erro (NPR-32544).
* Gerenciar publicação não inclui ativos referenciados na solicitação de fluxo de trabalho de ativação (NPR-32463).
* A verificação de integridade do Dispatcher exibe uma mensagem de `Invalid cookie header` aviso nos arquivos de registro (NPR-33630).
* A integração do Salesforce é vulnerável ao SSRF (NPR-32671).
* XSS refletido em PreferencesServlet (NPR-33439).

### Assets {#assets-6481}

* A contagem de ativos não é alterada de acordo com a alteração na seleção na Visualização da Lista (NPR-33285).

* O botão Avançar não está ativado ao selecionar o nó pai (onde a pasta filho único está visível) e depois selecionar a pasta filho (NPR-33284).

* A interface de usuário de toque não é renderizada (com erro) para usuários que não têm acesso de leitura na raiz do repositório, quando o modo DMS7 ou Híbrido está ativado (NPR-33175).

* Os caracteres GB18030 que ocorrem em pastas e nomes de ativos mudam para em branco nos arquivos zip baixados (NPR-33150).

* A pasta extra é criada ao recortar inteligente um ativo que está dentro de uma pasta pai com `.` caractere de ponto em seu nome (NPR-32755).

* O carregamento lento não é acionado e não mais de 100 ativos são exibidos ao selecionar para revisar as tarefas na caixa de entrada de notificações (NPR-32749).

* A página de link para compartilhar a coleção está quebrada devido a alterações no coral-info (NPR-32510).

* O processamento de ativos enquanto o upload em massa fica travado (CQ-4293916).

* Vulnerabilidade SSRF no Experience Manager (NPR-33437).

### Plataforma {#platform-6481}

* O [!DNL Sling] filtro não será chamado se a entrada do `sling:match` mapa for criada em `/etc/maps` (NPR-33308).
* Todos os agentes de liberação são acionados ao desativar uma página (NPR-32941).
* Quando você usa a `ScriptProcessor` API para minimizar uma biblioteca JavaScript, o arquivo de log exibe uma mensagem de erro indicando que o código JavaScript não é compatível com o modo restrito. A API não fornece opção para ativar ou desativar o modo restrito. (NPR-32746).
* Quando um query SQL é executado por um tempo maior, por exemplo, 7 horas, AEM pára de responder (NPR-33043).

### Interface do usuário {#ui-6481}

* Quando você pesquisa ou navega por um caminho usando uma caixa de diálogo de seleção, a caixa de diálogo de seleção exibe todo o conteúdo do nó JCR selecionado em vez de exibir apenas as imagens (NPR-32712).

### Projetos de tradução {#tranlation-6481}

* Um `NullPointerException` erro é visto nos registros ao executar um trabalho de tradução (NPR-32220).

### Integrações {#integrations-6481}

* Scripts entre sites para JSON (NPR-32745).

### Communities {#communities-6481}

* Após a criação de um novo grupo, os autores não são redirecionados para a seção Grupo [!UICONTROL da] Comunidade no [!DNL Internet Explorer] 11 (NPR-33202).
* Ocorre um erro ao acessar a página [!UICONTROL Atividade Stream] (NPR-33152).
* Editar um [!DNL Communities] grupo e alterar a imagem em miniatura não atualiza a imagem em miniatura do grupo (NPR-32603).
* Ao criar uma versão de notificações e subscrições de Conteúdo gerado pelo usuário (UGC), uma ID incorreta da página de origem é armazenada (CQ-4289703).
* Problema de script entre sites (NPR-33212).

### Fluxo de trabalho {#workflow-6481}

* Alguns componentes não são exibidos na caixa de diálogo que aparece quando um usuário conclui um fluxo de trabalho que inclui uma etapa [!UICONTROL Participante da] caixa de diálogo (NPR-32989).

* A opção [!UICONTROL Linha] do tempo no painel esquerdo leva mais tempo para carregar do que o esperado (NPR-32850).

### Forms {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack não inclui correções para AEM Forms. Eles são entregues usando um pacote complementar separado do Forms. Além disso, é lançado um instalador cumulativo que inclui correções para o AEM Forms no JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

* Gerenciamento de correspondência: Quando um usuário cola o conteúdo de um [!DNL Word] documento, o fragmento do documento de texto não retém a formatação (NPR-33213).
* Forms adaptável: Uma nova linha de uma string em um dicionário de formulários adaptáveis adiciona `&#xa;` caracteres ao dicionário (NPR-33265).
* Forms adaptável: O usuário não pode salvar um formulário adaptável com mais de um anexo (NPR-33214).
* Forms adaptável: `AddInstance` e `RemoveInstance` os métodos para a classe Instance Manager não adicionam um número dinâmico de instâncias para fragmentos de carregamento lento em [!DNL Internet Explorer 11] (NPR-33201).
* Forms adaptável: A Analytics habilitada em um formulário adaptável incorporado em uma [!DNL Sites] página não grava dados para eventos Enviar e Abandonar (NPR-31359).
* Forms adaptável: Quando um usuário cola o conteúdo de um [!DNL Word] documento para um formulário adaptável e o envia, o formulário adaptativo enviado inclui caracteres unicode. Além disso, a conversão de PDF em PDF/A falha devido a caracteres unicode (NPR-33348).
* BackendIntegration: As solicitações do modelo de dados de formulário falham, pois o token de atualização expira devido ao estado inativo incorreto (NPR-33168).
* Serviços do Documento: Falha do serviço de conversão de PDF ao converter documentos PDF em PostScript devido à ausência de jars Gibson para [!DNL WebLogic] no [!DNL Linux] servidor (NPR-33515, CQ-4292239).
* Serviços do Documento: Quando um usuário converte um arquivo de texto em PDF, os caracteres japoneses não são renderizados corretamente (NPR-33239).
* XSS armazenado com o GuideSOMProviderServlet (NPR-32701).


## Install 6.4.8.1 {#install}

### Requisitos de configuração {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Para clientes com Pacotes de recursos instalados no AEM 6.4. Os pacotes de recursos opcionais fornecidos pelo Adobe têm dependências na versão de lançamento e nos service packs. Se você tiver algum Feature Pack instalado, entre em contato com a equipe de Atendimento ao cliente da AEM para validar a compatibilidade desses pacotes de recursos com este pacote de correções cumulativas para AEM 6.4.

* AEM 6.4.8.1 requires AEM 6.4.8.0. Please visit [upgrade documentation](../sites-deploying/upgrade.md) for detailed instructions.
* Em uma implantação com MongoDB e várias instâncias, instale o AEM 6.4.8.1 em uma das instâncias do autor usando o Gerenciador de pacotes.
* Antes de instalar o pacote de correção cumulativo, certifique-se de ter um instantâneo ou um backup atualizado da instância AEM.
* Reinicie a instância antes da instalação. Embora isso seja necessário apenas quando a instância ainda está no modo de atualização (e esse é o caso quando a instância foi atualizada de uma versão anterior), geralmente é recomendado se a instância estava sendo executada por um período de tempo maior.

>[!NOTE]
>
>A Adobe não recomenda remover ou desinstalar o pacote AEM 6.4.8.1.

### Instale o Cumulative Fix Pack {#install-cumulative-fix-pack}

Execute as seguintes etapas para instalar o Cumulative Fix Pack em uma instância do AEM 6.4.8.0 existente:

1. Clique no link [Software Distribution (Distribuição](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-1.0.zip) de software) para baixar o pacote.

1. Abra o Gerenciador [de](http://localhost:4502/crx/packmgr/index.jsp) pacotes e clique em **[!UICONTROL Carregar pacote]** para fazer upload do pacote.

1. Selecione o nome do pacote e clique em **[!UICONTROL Instalar]**.

>[!NOTE]
>
>**A caixa de diálogo na interface do usuário do Gerenciador de pacotes às vezes sai imediatamente durante a instalação da versão 6.4.8.1**
>
>Portanto, é recomendável aguardar a estabilização dos registros de erros antes de acessar a instância. O usuário deve aguardar registros específicos relacionados à desinstalação do pacote do atualizador antes de ter certeza de que a instalação foi bem-sucedida. Geralmente isso acontece no Safari, mas pode acontecer intermitentemente em qualquer navegador.

### Instalação automática {#auto-installation}

Há duas maneiras de instalar automaticamente o AEM 6.4.8.1 em uma instância em execução:

A. Coloque a embalagem em ..*/crx-quickstart/install* enquanto o servidor estiver em execução. O pacote é instalado automaticamente.

B. Use the [HTTP API from Package Manager](https://docs.adobe.com/content/docs/pt/crx/2-3/how_to/package_manager.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>O AEM 6.4.8.1 não oferece suporte à instalação do Bootstrap.

### Validar instalação {#validate-install}

1. A página Informações do produto (*/system/console/productinfo*) agora deve mostrar a string da versão atualizada &quot;Adobe Experience Manager, Versão 6.4.8.1&quot; em Produtos instalados.
1. Todos os pacotes OSGI são ATIVOS ou FRAGMENTOS no Console OSGi (Use o console da Web: /system/console/bundles).
1. O pacote OSGI org.apache.Jackrabbit.oak-core está na versão 1.8.17 ou superior (Use o console da Web: /system/console/bundles).

Para determinar a plataforma certificada para execução com esta versão do AEM Sites e do Assets, consulte Requisitos [](../sites-deploying/technical-requirements.md)técnicos.

>[!Nnota]
>On successful installation of the package, an informational message appears indicating that the content package has installed successfully, such as **&quot;Content Package AEM-6.4-Service-Pack-7 installed successfully.&quot;**

### Atualizar visualizadores do Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.1 contém a nova versão dos visualizadores do Dynamic Media (5.10.1) que ativa a verificação de nomes de duplicados na página Predefinição de imagem. Os clientes da Dynamic Media devem executar o seguinte comando para exibir as predefinições do visualizador de caixa para um estado atualizado.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

que copiará novas predefinições do visualizador para o local /conf.

### Instalar o pacote complementar do AEM Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Pule se você não estiver usando o AEM Forms. As correções do AEM Forms são entregues por meio de um pacote complementar separado.

1. Verifique se você instalou o AEM Cumulative Fix Pack.
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/br/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Install AEM Forms JEE installer {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Pule se você não estiver usando o AEM Forms no JEE. As correções no JEE do AEM Forms são entregues por meio de um instalador separado.

For information about installing the cumulative installer for AEM Forms JEE and post-deployment configuration, see [AEM Forms JEE Patch Installer 0016](https://helpx.adobe.com/br/aem-forms/quick-fixes/6-4/jee-patch-0016.html).

### Uber Jar {#uber-jar}

The Uber Jar for AEM 6.4.8.1 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8.1/).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.1</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Recursos removidos/obsoletos {#removed-deprecated-features}

Esta seção lista os recursos e funcionalidades removidos ou descontinuados do AEM 6.4.

| Área | Recurso | Substituição | Versão |
|---|---|---|---|
| Ativos | Gerenciar ação de tag para subativos | Nenhuma substituição | AEM 6.4.2.0 |
| Integração do Assets e da Adobe Creative Cloud | [O AEM ao compartilhamento](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) de pastas do Creative Cloud foi introduzido no AEM 6.2 como uma forma de fornecer aos usuários criativos acesso aos ativos do AEM. Uma nova funcionalidade lançada no aplicativo da Creative Cloud, o Adobe Asset Link, fornece uma experiência de usuário melhor e acesso avançado a ativos do AEM diretamente do Photoshop, InDesign e Illustrator. A Adobe não fará mais aprimoramentos no recurso de compartilhamento de pastas. Embora o recurso esteja incluído no AEM, os clientes são aconselhados a usar a substituição. | Adobe Asset Link ou aplicativo de desktop. Para obter mais informações, consulte o artigo [Integração da AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Problemas conhecidos {#known-issues}

* Ao instalar o AEM 6.4.8.1, a atualização da [!DNL Chrome] versão 83 está causando um problema na criação de pacotes. Use outros navegadores disponíveis, como [!DNL Internet Explorer] e [!DNL Firefox], ou outras opções de instalação de pacote padrão AEM para resolver o problema. O problema é resolvido após a instalação do AEM 6.4.8.1.

* Não é possível enviar um email para o servidor SMTP remoto usando o remetente de email padrão AEM, pois ele permite apenas a comunicação usando TLS v1.2. Remova o pacote `javax.mail:mail:1.5.0-b01` de `system/console` e atualize os pacotes para resolver o problema.

Para obter informações sobre os problemas conhecidos do AEM 6.4.8.0 Service Pack, consulte [AEM 6.4.8.0 Service Pack Release Notes](sp-release-notes.md).

## Pacotes de conteúdo e pacotes OSGi incluídos {#osgi-bundles-and-content-packages-included}

Os seguintes documentos de texto listam os pacotes OSGi e os Pacotes de conteúdo incluídos no AEM 6.4.8.1.

Lista de pacotes OSGi incluídos no AEM 6.4.8.1

[Obter arquivo](assets/6.4.8.1_osgi_bundles.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.8.1

[Obter arquivo](assets/6.4.8.1_content_packages.txt)

## Recursos úteis {#helpful-resources}

* [Notas de versão do AEM 6.4](../release-notes/release-notes.md)
* [Página do produto AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentação do AEM 6.4](https://helpx.adobe.com/support/experience-manager/6-4.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

## Sites restritos {#restricted-sites-new}

Estes sites estão disponíveis somente para clientes. Se você for um cliente e precisar de acesso, entre em contato com o gerente de contas da Adobe.

* [Baixe o produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Entre em contato com o Suporte ao cliente](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
