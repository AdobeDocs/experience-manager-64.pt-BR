---
title: Resumo dos novos recursos | AEM 6.4 Forms
seo-title: New features summary | AEM 6.4 Forms
description: Resumo dos novos recursos e melhorias no AEM 6.4 Forms.
seo-description: Summary of new features and enhancements in AEM 6.4 Forms.
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
exl-id: 21b8ed83-9c0c-41ee-9fbb-56ccebaee132
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2038'
ht-degree: 1%

---

# Resumo dos novos recursos | AEM 6.4 Forms {#new-features-summary-aem-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Resumo dos novos recursos e melhorias no AEM 6.4 Forms.

O AEM Forms inclui vários novos recursos e aprimoramentos que simplificam ainda mais a criação, o gerenciamento e as experiências do usuário com formulários adaptáveis e comunicações interativas.

Leia para obter uma rápida introdução a novos recursos e melhorias. Visite a documentação para obter detalhes sobre a oferta de recursos. Além disso, consulte AEM 6.4 Forms [notas de versão](/help/release-notes/forms.md). Para obter a documentação completa do AEM 6.4 Forms, visite [Guia do Forms do AEM 6.4](/help/forms/home.md).

## Comunicações interativas {#interactive-communications}

![gerenciamento de correspondência](assets/correspondence-management.png)

As Comunicações interativas centralizam e gerenciam a criação, montagem e entrega de correspondências seguras, personalizadas e interativas, como correspondência comercial, cartas, documentos, declarações, avisos de benefícios, prospecto de gerenciamento de riqueza, emails de marketing, contas e kits de boas-vindas.

As Comunicações interativas usam a mesma tecnologia, processos e componentes subjacentes aos formulários adaptáveis para criar comunicações responsivas de vários canais, como formulários adaptáveis responsivos.

A comunicação interativa oferece vantagens significativas:

* Fornece integração OOTB com o Modelo de dados de formulário para permitir acesso fácil e simplificado a bancos de dados back-end e outros sistemas CRM, como o MS Dynamics
* Fornece uma interface de criação integrada para canais de impressão e Web
* Fornece interface de criação baseada em arrastar e soltar, semelhante à criação do Adaptive Forms, para canais de impressão e da Web.

A comunicação interativa é a abordagem padrão e recomendada para criar comunicações com clientes. Para continuar usando as letras AEM 6.3 Forms e AEM 6.2 Forms, é necessário instalar um pacote de compatibilidade.

### Criação de comunicações interativas multicanal {#multi-channel-interactive-communication-authoring}

Usando a comunicação interativa, você pode criar e editar documentos impressos e da Web em um único editor de documentos. Ao utilizar os mesmos fragmentos de documento para criar representações de ambos os canais, é possível eliminar a duplicação de esforços.
![printweb_2](assets/printweb_2.png)

Para obter mais informações, consulte [Visão geral das comunicações interativas](/help/forms/using/interactive-communications-overview.md).

### Editor de documentos WYSIWYG {#wysiwyg-document-editor}

O editor de documentos de arrastar e soltar WYSIWYG é amigável para os negócios. A interface intuitiva, a funcionalidade de arrastar e soltar, os componentes padrão, os modelos de dados e o repositório integrado para ativos facilitam e agilizam a criação de comunicações interativas.

Para criar uma comunicação Interativa ou editar uma existente, os usuários empresariais podem usar os seguintes blocos de construção: Canais, Conteúdo, Propriedades, Ativos, Componentes e Fontes de dados.

![arrastar-n-soltar-lf](assets/drag-n-drop-lf.png)

Para obter mais informações, consulte [Introdução à criação de comunicação interativa](/help/forms/using/introduction-interactive-communication-authoring.md).

### Gerar automaticamente versão da Web a partir do conteúdo impresso na comunicação interativa {#auto-generate-web-version-from-print-content-in-interactive-communication}

Os autores podem gerar automaticamente conteúdo de documentos da Web de documentos impressos para criar, visualizar e editar documentos impressos e da Web no mesmo editor. Os autores de comunicação interativa podem criar uma vez e publicar em todos os canais. Os autores de comunicação interativa podem usar os mesmos fragmentos de documento no canal de impressão e da Web para evitar a duplicação de esforços.

Para obter mais informações, consulte [Canal de impressão e canal da Web](/help/forms/using/web-channel-print-channel.md).

### Usar temas para criar estilo no canal da Web da comunicação interativa {#use-themes-to-style-web-channel-of-interactive-communication}

A comunicação interativa é compatível com temas. Você pode criar temas e aplicá-los à sua comunicação interativa. Um tema contém detalhes de estilo para componentes e painéis. Você pode reutilizar um tema em diferentes comunicações interativas para oferecer-lhes aparência e identidade visual comuns e consistentes.

O AEM Forms inclui um tema pronto para uso para Comunicações interativas. Usando um tema, você também pode personalizar a aparência de uma comunicação interativa em um dispositivo.

Para obter mais informações, consulte [Temas no AEM Forms](/help/forms/using/themes.md).

### Interface do agente aprimorada {#enhanced-agent-interface}

A interface do usuário do Agente agora oferece suporte para impressão e visualização da Web da comunicação interativa. Na mesma interface do Agente, você pode optar por editar o canal de impressão e visualizar o canal da Web de sua comunicação interativa multicanal. Campos, variáveis, elementos FDM e fragmentos de documento no canal de impressão podem ser configurados para serem modificados pelo agente na interface do usuário do Agente. O suporte ao modelo de dados de formulário permite gerar visualizações com dados de amostra pré-preenchidos.

Para obter mais informações, consulte [Preparar e enviar comunicação interativa usando a interface do usuário do agente](/help/forms/using/prepare-send-interactive-communication.md).

### Apresentar informações em gráficos {#present-information-in-charts}

A comunicação interativa oferece suporte a gráficos na Web e ao canal de impressão para comunicações mais avançadas. Usando gráficos como pizza, rosca, barra e coluna, você pode condensar e apresentar visualmente grandes quantidades de informações para fácil interpretação e análise.

![chart-2](assets/chart-2.png) ![gráfico](assets/chart.png)

Para obter mais informações, consulte [Uso de gráficos em Comunicações interativas](/help/forms/using/chart-component-interactive-communications.md).

### Conectores de dados prontos para o uso para preencher previamente documentos {#out-of-the-box-data-connectors-to-prefill-documents}

A comunicação interativa fornece integração de dados com ferramentas de negócios para se conectar a vários sistemas de negócios, incluindo sistemas CRM, e personalizar dados em documentos.

![fdm_ad](assets/fdm_ad.png)

Para obter mais informações, consulte [Usar modelo de dados de formulário](/help/forms/using/using-form-data-model.md).

### Editor de fragmento de documento aprimorado {#enhanced-document-fragment-editor}

Agora você pode usar elementos e regras do FDM em fragmentos de documento de comunicação interativa.

* Suporte para elementos de modelo de dados de formulário
* Mostrar ou ocultar um ativo/fragmento de texto usando regras
* Validar o valor de um elemento/variável
* Executar funções para calcular o valor de uma expressão matemática

Para obter mais informações, consulte:

* [Textos em Comunicações interativas](/help/forms/using/texts-interactive-communications.md)
* [Condições em comunicações interativas](/help/forms/using/conditions-interactive-communications.md)

### Pacote de compatibilidade para ativos existentes {#compatibility-package-for-existing-assets}

Por padrão, os ativos de carta das versões anteriores do AEM Forms não são compatíveis com esta versão. Se você pretende continuar usando as cartas do AEM 6.3 Forms e AEM 6.2 Forms, é necessário instalar o pacote Compatibilidade.

## Integração de dados {#data-integration}

![](do-not-localize/data-integeration-1.png)

[Integração de dados do AEM Forms](/help/forms/using/data-integration.md) permite configurar fontes de dados diferentes; como bancos de dados, serviços Web baseados em RESTful ou SOAP e serviços OData; para criar um modelo de dados de formulário que pode ser usado para vincular dados, preencher previamente e chamar serviços em formulários e documentos adaptáveis.

Há vários novos recursos e aprimoramentos na integração de dados nesta versão.

### Criar modelo de dados de formulário sem fonte de dados {#create-form-data-model-without-data-source}

Usuários empresariais e autores de formulários agora podem criar um modelo de dados de formulário, incluindo suas entidades e propriedades sem configurar uma fonte de dados, e podem ser usados para criar formulários e documentos adaptáveis. É possível vincular o modelo de dados de formulário a fontes de dados posteriormente. Elimina dependências de fontes de dados para criar formulários e documentos usando o modelo de dados de formulário.

Da mesma forma, é possível criar entidades e propriedades-filho em um modelo de dados de formulário existente e vinculá-las às entidades e propriedades correspondentes em uma fonte de dados posteriormente.

Para obter mais informações, consulte [Criar modelo de dados de formulário](/help/forms/using/create-form-data-models.md).

### Criar propriedades calculadas {#create-computed-properties}

Os autores e desenvolvedores do Forms podem criar propriedades computadas no modelo de dados de formulário. Eles permitem calcular um valor para a propriedade criando regras ou lógica nos dados disponíveis nas fontes de dados configuradas. Uma regra é uma expressão que é avaliada quando os dados são carregados no modelo de dados de formulário ou os valores das propriedades na alteração da expressão. Por exemplo, uma propriedade calculada chamada Instalações calcula a quantia mensal a ser paga para um empréstimo com base na taxa de juros especificada na fonte de dados e a quantia e duração do empréstimo especificadas pelo usuário no formulário.

Uma propriedade calculada reside localmente em um modelo de dados de formulário e não existe em uma fonte de dados. Você pode usar as propriedades computadas em formulários adaptáveis e comunicações interativas.

Para obter mais informações, consulte [Trabalhar com o modelo de dados de formulário](/help/forms/using/work-with-form-data-model.md).

### Visualizar formulários e documentos com dados de amostra {#preview-forms-and-documents-with-sample-data}

O modelo de dados de formulário permite gerar dados de amostra para propriedades de todas as entidades em um modelo de dados de formulário. Os dados gerados correspondem aos tipos de dados configurados para as propriedades. Ao visualizar um formulário ou documento adaptável associado ao modelo de dados de formulário, ele renderiza com dados de amostra pré-preenchidos.

Os dados de amostra são um conjunto de valores aleatórios que são alterados toda vez que você os gerar. No entanto, é possível editar e salvar os dados de amostra que persistem mesmo se você os gerar novamente. Por exemplo, se você editar e salvar os dados de amostra das propriedades Nome e Sobrenome e, posteriormente, adicionar outra propriedade ou entidade no modelo de dados de formulário e gerar novamente os dados de amostra, as propriedades Nome e Sobrenome mostrarão os valores salvos enquanto os valores de outras propriedades forem regenerados.

Para obter detalhes, consulte [Usar modelo de dados de formulário](/help/forms/using/using-form-data-model.md).

### Atualizar definições de origem de dados {#refresh-data-source-definitions}

Qualquer atualização em entidades ou propriedades da fonte de dados não é refletida automaticamente nos modelos de dados de formulário associados. O editor de modelo de dados de formulário agora possui recursos ![refresh_forms_di](assets/refresh_forms_di.png) (Atualizar definições da fonte de dados) que invalida o cache do servidor e busca o esquema atualizado da fonte de dados para refletir imediatamente no modelo de dados de formulário.

### Configurar fontes de dados usando a interface do usuário de toque {#configure-data-sources-using-touch-user-interface}

Com esta versão, a configuração de serviços em nuvem para fontes de dados está disponível na interface do usuário de toque. Além disso, o local para configurar serviços em nuvem foi alterado para **[!UICONTROL Ferramentas > Cloud Services > Fontes de dados]**. Consulte [Configurar fontes de dados](/help/forms/using/configure-data-sources.md).

## Adaptive Forms {#adaptive-forms}

![simplificação-da-criação-formulários-e-documentos_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### Melhore o desempenho de formulários adaptáveis com carregamento lento aprimorado {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading}

A funcionalidade de carregamento lento em formulários adaptáveis adia a inicialização de fragmentos de formulário até que sejam necessários. Melhora o desempenho de formulários grandes ao minimizar o tempo necessário para renderizar um formulário, resultando em uma melhor experiência do usuário.

Há vários aprimoramentos no recurso de carregamento lento nesta versão:

* O anexo de arquivo e os componentes Termos e condições são suportados em fragmentos de formulário com carregamento lento ativado.
* Fragmentos de formulário adaptáveis com carregamento lento habilitado são suportados em painéis repetíveis.
* Formulários adaptáveis com fragmentos ativados de carregamento lento são compatíveis com o aplicativo AEM Forms.

## Fluxos de trabalho de AEM centrados na Forms {#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

Com a capacidade de fluxos de trabalho de AEM centrados na Forms, você pode criar e implantar rapidamente fluxos de trabalho para várias tarefas na pilha OSGi. Não é mais necessário instalar o recurso de Gerenciamento de processos disponível na pilha JEE, simplificando a implantação e eliminando os custos de servidor e infraestrutura de aplicativos. Para obter mais informações, consulte [Fluxos de trabalho centrados na Forms no OSGi](/help/forms/using/aem-forms-workflow.md).

A seguir estão as melhorias nos fluxos de trabalho de AEM centrados na Forms: ・

* O editor de modelo de fluxo de trabalho está disponível na interface do usuário de toque. Ajuda a reduzir o tempo necessário para criar fluxos de trabalho de AEM centrados em formulários.
* Etapa do fluxo de trabalho para enviar emails. Por exemplo, você pode usar a etapa de email para enviar um documento de registro na conclusão de um fluxo de trabalho.
* Etapa de fluxo de trabalho para usar serviços de modelo de dados de formulário em um modelo de fluxo de trabalho. Essa etapa permite invocar serviços de integração de dados sem gravar nenhum código personalizado. Por exemplo, você pode invocar um serviço do GET para obter detalhes do funcionário de um arquivo de banco de dados sem gravar nenhum código personalizado.

## Aplicativo AEM Forms {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

O aplicativo AEM Forms permite que trabalhadores de campo sincronizem seus dispositivos móveis com um servidor AEM Forms e trabalhem em seus formulários. O aplicativo funciona perfeitamente quando o dispositivo está offline, salvando os dados localmente no dispositivo e sincronizando os dados com o servidor quando o dispositivo está novamente online. Para obter mais informações, consulte [Aplicativo AEM Forms](/help/forms/using/aem-forms-app.md).

Veja a seguir as melhorias no aplicativo AEM Forms:

* Formulários adaptáveis com fragmentos ativados de carregamento lento são compatíveis com o aplicativo AEM Forms.
* Formulários adaptáveis com modelo de dados de formulário são compatíveis com o aplicativo AEM Forms.

## Segurança de documentos {#document-security}

![aem-forms-document-security-](assets/aem-forms-document-security-.png)

Usando a segurança de documentos, você pode distribuir com segurança todas as informações salvas em um formato compatível. A segurança de documentos garante que somente usuários autorizados possam usar seus documentos. Estas são as principais alterações na segurança de documentos:

* A segurança do documento fornece um [Biblioteca de proteção portátil (PPL)](/help/forms/using/document-security-offerings.md) para proteger um documento localmente, sem enviá-lo ao servidor do AEM Forms. Somente as credenciais de segurança e os detalhes da política viajam pela rede para o servidor AEM Forms. AEM 6.4 A Forms introduziu a Biblioteca de Proteção Portátil (PPL) em um formato de pacote OSGi. Agora, você pode instalar diretamente a biblioteca PPL em um servidor AEM Forms e usar os recursos de AEM e PPL em conjunto.
* A segurança do documento C++ SDK e a biblioteca PPL C++ podem ser compiladas com o Microsoft Visual Studio 2013. A versão anteriormente suportada era o Microsoft Visual Studio 2010.

## Plataformas compatíveis {#supported-platforms}

O AEM Forms pode ser configurado usando qualquer combinação de sistemas operacionais, servidores de aplicativos, bancos de dados, drivers de banco de dados, JDK, servidores LDAP e servidores de email compatíveis. Estas são as principais alterações nas plataformas compatíveis:

<table> 
 <tbody> 
  <tr> 
   <td>Componente</td> 
   <td>Suporte adicionado</td> 
   <td>Suporte removido</td> 
  </tr> 
  <tr> 
   <td>Sistemas operacionais</td> 
   <td> 
    <ul> 
     <li>Microsoft Windows Server 2016</li> 
     <li>Oracle Linux 7 Update 3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM AIX 7.2 <sup>[1]</sup><br /> </li> 
     <li>Solaris 11 <sup>[1]</sup></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Servidores de aplicativos<br /> </td> 
   <td> 
    <ul> 
     <li>Red Hat JBoss EAP 7</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM Weblogic 12.1.3</li> 
     <li>IBM WebSphere 8.5.5</li> 
     <li>Red Hat JBoss EAP 6</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Bancos de dados</td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2016</li> 
     <li>MySQL 5.7.19 e posterior</li> 
     <li>IBM DB2 11.1</li> 
     <li>Arquitetura de multilocatários do Oracle</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2012<br /> </li> 
     <li>Microsoft SQL Server 2014</li> 
     <li>MySQL 5.5</li> 
     <li>IBM DB2 10.5<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Servidores LDAP</td> 
   <td> 
    <ul> 
     <li>Microsoft Ative Diretory 2016</li> 
     <li>IBM Tivoli Diretory Server 6.4</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Ative Diretory 2008</li> 
     <li>IBM Tivoli Diretory Server 6.3</li> 
     <li>Oracle Diretory Server Enterprise Edition 7.0</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Servidores de email</td> 
   <td> 
    <ul> 
     <li>Microsoft Office 365</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Novell Groupwake 7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Conectores</td> 
   <td> 
    <ul> 
     <li>Conector para Microsoft Sharepoint 2016</li> 
     <li>Conector para EMC Documentum 7.3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Conector para Microsoft Sharepoint 2007</li> 
     <li>Conector para Microsoft Sharepoint 2010</li> 
     <li>Conector para IBM Filenet 5.0</li> 
     <li>Conector para EMC Documentum 6.7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Navegadores</td> 
   <td> 
    <ul> 
     <li>Apple Safari 11.x no macOS</li> 
     <li>Apple Safari 11.x no iOS</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Navegador Blackberry para dispositivos Blackberry Z30 e Q10</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Aplicativo AEM Forms<br /> </td> 
   <td> 
    <ul> 
     <li>Android 4.4 ou superior</li> 
     <li>Apple iOS 10 ou superior</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

1. Os sistemas operacionais AIX e Solaris estão disponíveis apenas para clientes de atualização.
