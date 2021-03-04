---
title: Requisitos técnicos
seo-title: Requisitos técnicos
description: Uma lista das plataformas de cliente e servidor compatíveis com o AEM.
seo-description: Uma lista das plataformas de cliente e servidor compatíveis com o AEM.
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
translation-type: tm+mt
source-git-commit: 95b5e70c1b474d4d207a5a33e8d1ab8ef39685b6
workflow-type: tm+mt
source-wordcount: '3271'
ht-degree: 2%

---


# Requisitos técnicos{#technical-requirements}

A Adobe oferece suporte ao Adobe Experience Manager (AEM) nas plataformas, conforme detalhado nas seguintes informações deste documento.

Para quaisquer problemas que estejam especificamente relacionados à própria plataforma, entre em contato diretamente com o fornecedor da plataforma.

>[!NOTE]
>
>Dependendo da plataforma na qual você instala o AEM, pode haver diferentes conjuntos de requisitos para o gerenciamento de usuários.

## Pré-requisitos {#prerequisites}

Requisitos mínimos para instalar o Adobe Experience Manager:

* Plataforma Java instalada, JDK Standard Edition ou outras máquinas virtuais Java compatíveis [Java](#java-virtual-machines)
* Arquivo de início rápido do Experience Manager (JAR independente ou WAR de implantação de aplicativo da Web)

### Requisitos mínimos de dimensionamento {#minimum-sizing-requirements}

Requisitos mínimos para executar o Adobe Experience Manager:

* 5 GB de espaço livre em disco no diretório de instalação
* Memória de 2 GB

>[!NOTE]
>
>* Os casos de uso de ativos digitais precisam de mais memória básica. Consulte [Implantação e manutenção](/help/sites-deploying/deploy.md#default-local-install) para obter detalhes.
>* [O ](/help/forms/using/installing-configuring-aem-forms-osgi.md) pacote do complemento AEM Forms requer 15 GB de espaço temporário.

>



Consulte as [Diretrizes de dimensionamento de hardware](/help/managing/hardware-sizing-guidelines.md) para obter mais informações.

### Níveis de suporte {#support-levels}

Este documento lista as plataformas de cliente e servidor compatíveis com o Adobe Experience Manager. A Adobe fornece vários níveis de suporte, tanto para configurações recomendadas quanto para outras configurações.

### Configurações suportadas {#supported-configurations}

A Adobe recomenda essas configurações e oferece suporte total como parte do contrato padrão de manutenção de software.

<table> 
 <tbody> 
  <tr> 
   <td>Nível de suporte</td> 
   <td>Descrição<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>A: Suportado</strong></td> 
   <td>A Adobe fornece suporte e manutenção completos para essa configuração. Essa configuração é contemplada pelo processo de garantia de qualidade da Adobe.</td> 
  </tr> 
  <tr> 
   <td><strong>R: Suporte restrito</strong></td> 
   <td>Para garantir o sucesso do projeto de nossos clientes, a Adobe fornece suporte total em um programa de suporte restrito, o que requer que condições específicas sejam atendidas. O suporte de nível R requer uma solicitação formal do cliente e a confirmação da Adobe. Para obter mais informações, entre em contato com o Atendimento ao cliente da Adobe.</td> 
  </tr> 
 </tbody> 
</table>

### Configurações não suportadas {#unsupported-configurations}

| Nível de suporte | Descrição |
|---|---|
| **Z: Não suportado** | A configuração não é suportada. A Adobe não faz declarações sobre se a configuração funciona e não oferece suporte a ela. |

## Plataformas compatíveis {#supported-platforms}

### Máquinas Virtuais Java {#java-virtual-machines}

O aplicativo requer uma Máquina Virtual Java para execução, fornecida pela distribuição do Java Development Kit (JDK).

O Adobe Experience Manager opera com as seguintes versões das máquinas virtuais Java:

>[!CAUTION]
>
>É recomendável rastrear os Boletins de segurança do fornecedor do Java para garantir a segurança dos ambientes de produção e instalar as Atualizações mais recentes do Java.

<table> 
 <tbody> 
  <tr> 
   <td>Plataforma</td> 
   <td>Nível de suporte<br /> </td> 
  </tr> 
  <tr> 
   <td>JDK do Oracle Java SE 11 [1]</td> 
   <td>Z: Não suportado </td> 
  </tr> 
  <tr> 
   <td>JDK do Oracle Java SE 10 [1]</td> 
   <td>Z: Não suportado </td> 
  </tr> 
  <tr> 
   <td>JDK do Oracle Java SE 9 [1]</td> 
   <td>Z: Não suportado</td> 
  </tr> 
  <tr> 
   <td><strong>Oracle Java SE 8 JDK - 64 bits</strong></td> 
   <td>A: Suportado [3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - compilação 2.9, JRE 1.8.0 [2]</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - compilação 2.8, JRE 1.8.0 [2]</td> 
   <td>A: Suportado</td> 
  </tr> 
 </tbody> 
</table>

1. O Oracle migrou para um modelo de &quot;Suporte de longo prazo&quot; (LTS) dos produtos Oracle Java SE. O Java 9 e 10 são versões não LTS do Oracle (consulte [Oracle Java SE support roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). A adobe fornecerá apenas o suporte para versões LTS do Java para executar o AEM na produção.

1. O IBM JRE só é suportado em conjunto com o WebSphere Application Server.
1. O suporte e a distribuição do Oracle Java SE JDK, incluindo todas as atualizações de manutenção de versões LTS além do fim das atualizações públicas, serão suportados pela Adobe diretamente para todos os clientes do AEM que usam a tecnologia Oracle Java SE. Consulte o [Suporte do Oracle Java para perguntas e respostas do Adobe Experience Manager](assets/adobe-oracle-java-license-agreement.pdf) para obter mais informações.

### Armazenamento e persistência {#storage-persistence}

Existem várias opções para implantar o repositório do Adobe Experience Manager. Consulte a lista a seguir para conhecer as tecnologias e opções de armazenamento suportadas.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plataforma</strong></td> 
   <td><strong>Descrição</strong></td> 
   <td><strong>Nível de suporte</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Sistema de arquivos com arquivos TAR [1]</strong></td> 
   <td>Repositório</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td><strong>Sistema de arquivos com armazenamento de dados [1]</strong></td> 
   <td>Binários</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Armazenar binários em arquivos TAR no sistema de arquivos [1]</td> 
   <td>Binários</td> 
   <td>Z: Não suportado para produção</td> 
  </tr> 
  <tr> 
   <td>Amazon S3</td> 
   <td>Binários</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Armazenamento de blobs do Microsoft Azure</td> 
   <td>Binários</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5, 6]</td> 
   <td>Repositório</td> 
   <td>A: Suportado com limitações</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3, 6]</td> 
   <td>Repositório</td> 
   <td>A: Suportado com limitações</td> 
  </tr> 
  <tr> 
   <td>MySQL 5.7</td> 
   <td>Banco de dados de formulários</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1<br /> </td> 
   <td>Banco de dados de formulários</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 10.5</td> 
   <td>Banco de dados do Repositório e Formulários</td> 
   <td>R: Suporte restrito (4)</td> 
  </tr> 
  <tr> 
   <td>Oracle Database 12c (12.1.x)</td> 
   <td>Banco de dados do Repositório e Formulários</td> 
   <td>R: Suporte restrito</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2017</td> 
   <td>Banco de dados de formulários</td> 
   <td>Z: Não suportado (4)</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2016</td> 
   <td>Banco de dados de formulários</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2014</td> 
   <td>Banco de dados de formulários</td> 
   <td>R: Suporte restrito (4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene (Quickstart integrado)</strong></td> 
   <td>Serviço de pesquisa</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Apache Solr</td> 
   <td>Serviço de pesquisa</td> 
   <td>A: Suportado</td> 
  </tr> 
 </tbody> 
</table>

1. &#39;Sistema de Arquivos&#39; inclui armazenamento de bloco compatível com POSIX. Isso inclui a tecnologia de armazenamento de rede. Considere que o desempenho do sistema de arquivos pode variar e influencia o desempenho geral. É recomendável carregar o AEM de teste em combinação com o sistema de arquivos remoto/de rede.
1. O Compartilhamento MongoDB não é compatível com o AEM.
1. O MongoDB Storage Engine WiredTiger é compatível somente.
1. Não é compatível com o AEM Forms.
1. O MongoDB Enterprise 3.6 é compatível a partir do AEM versão 6.4.2.0.
1. O suporte para MongoDB 3.4 chegou ao fim da vida útil (EOL), enquanto o MongoDB 3.6 deve atingir o EOL em 30 de abril de 2021. Observe que a Adobe só fornecerá suporte para problemas relacionados ao produto AEM a partir de agora.

>[!NOTE]
>
>Consulte [Implantação de comunidades](/help/communities/deploy-communities.md) para obter informações adicionais sobre o recurso do AEM Communities.

>[!NOTE]
>
>O MongoDB é um software de terceiros e não está incluído no pacote de licenciamento do AEM. Para obter mais informações, consulte a página [Política de licenciamento do MongoDB](https://www.mongodb.org/about/licensing/) .
>
>Para obter o máximo de sua implantação do AEM com o MongoDB, a Adobe recomenda licenciar a versão MongoDB Enterprise para se beneficiar do suporte profissional. Consulte [Implantações recomendadas](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) para obter mais informações.
>
>A licença inclui um conjunto de réplicas padrão, composto por uma instância primária e duas instâncias secundárias que podem ser usadas para o autor ou para as implantações de publicação.
>
>Caso deseje executar o autor e publicar no MongoDB, duas licenças separadas precisam ser compradas.
>
>O Atendimento ao cliente da Adobe ajudará a qualificar problemas relacionados ao uso do MongoDB com o AEM.
>
>Para obter mais informações, consulte a página [MongoDB para Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>Os bancos de dados relacionais compatíveis, conforme listado acima, são softwares de terceiros e não estão incluídos no pacote de licenciamento do AEM.
>
>Para executar o AEM 6.4 com um banco de dados relacional suportado, é necessário um contrato de suporte separado com um fornecedor de banco de dados. O Atendimento ao cliente da Adobe ajudará a qualificar problemas relacionados ao uso de bancos de dados relacionais com o AEM 6.4.
>
>**Observe que a maioria dos bancos de dados relacionais são suportados atualmente no Nível-R no AEM 6.4, que vem com critérios de suporte e um programa de suporte, conforme declarado na descrição de Nível-R acima.**

### Mecanismos de Servlet / Servidores de Aplicativos {#servlet-engines-application-servers}

O Adobe Experience Manager pode ser executado como um servidor independente (o arquivo JAR de início rápido) ou como um aplicativo da Web em um servidor de aplicativos de terceiros (o arquivo WAR).

A versão mínima necessária da API de servlet é o Servlet 3.1, mas abaixo do Servlet 4.0.

| Plataforma | Nível de suporte |
|---|---|
| **Mecanismo de Servlet integrado do Quickstart (Jetty 9.3)** | A: Suportado |
| Oracle WebLogic Server 12.2 (12cR2) | A: Suportado |
| IBM WebSphere Application Server Continuous Delivery (LibertyProfile) com Perfil Web 7.0 e IBM JRE 1.8 | A: Suportado |
| IBM WebSphere Application Server 9.0 | A: Suportado |
| Apache Tomcat 8.5.x | A: Suportado |
| JBoss EAP 7.1.0 com JBoss Application Server | A: Suportado (1) |
| JBoss EAP 7.0.0 com JBoss Application Server | A: Suportado |

1. Não é compatível com o AEM Forms.

### Sistemas operacionais do servidor {#server-operating-systems}

O Adobe Experience Manager funciona com as seguintes plataformas de servidor:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plataforma</strong></td> 
   <td><strong>Nível de suporte</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Linux, baseado na distribuição Red Hat</strong></td> 
   <td>A: Suportado (1)</td> 
  </tr> 
  <tr> 
   <td>Linux, baseado na distribuição Debian incl. Ubuntu</td> 
   <td>A: Suportado (4)</td> 
  </tr> 
  <tr> 
   <td>Linux, baseado na distribuição SUSE</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2012 R2</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Oracle Solaris 11</td> 
   <td>A: Suportado com limitações (3,5,7)<br /> R: Apoio limitado a novos contratos</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>A: Suportado com limitações (2,5,7)<br /> R: Apoio limitado a novos contratos</td> 
  </tr> 
 </tbody> 
</table>

1. O Linux Kernel 2.6, 3.x e 4.x inclui derivados da distribuição Red Hat, incluindo Red Hat Enterprise Linux, CentOS, Oracle Linux e Amazon Linux. Os recursos do complemento AEM Forms são compatíveis apenas com CentOS 7 e Red Hat Enterprise Linux 7.
1. AEM Assets: Consulte a seção [Suporte para write-back de metadados XMP](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets: Não há suporte para Dynamic Media Imaging. O Dynamic Media Video é compatível.
1. O AEM Forms é compatível somente com Ubuntu 16.04 LTS.
1. AEM Assets: Não há suporte para [Transformação de arquivo bruto](/help/assets/camera-raw.md)
1. AEM Forms: Sem suporte para o ambiente de produção
1. AEM Assets: Sem suporte para [PDF avançado Rasterizer](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms: Não suportado

### Ambientes de computação em nuvem e virtual {#virtual-cloud-computing-environments}

O Adobe Experience Manager é compatível com a execução em uma máquina virtual em ambientes de computação em nuvem, como o Microsoft Azure e o Amazon Web Services (AWS), em conformidade com os requisitos técnicos listados nesta página e de acordo com os termos de suporte padrão da Adobe.

A Adobe recomenda usar o Adobe Managed Services para implantar o AEM no Azure ou no AWS. O Adobe Managed Services fornece aos especialistas experiência e habilidades de implantar e operar o AEM nesses ambientes de computação em nuvem. Verifique nossa [documentação adicional sobre o Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

Em todos os outros casos de implantação do AEM no Azure ou AWS, ou em qualquer outro ambiente de computação em nuvem, o suporte da Adobe será contido no ambiente de computação virtual, em conformidade com as especificações técnicas listadas nesta página. Qualquer problema relatado relacionado ao AEM em execução em qualquer um desses ambientes de nuvem precisará ser reproduzível independentemente de qualquer serviço de nuvem específico ao ambiente de computação em nuvem, a menos que o serviço de nuvem seja especificamente aceito como parte dos requisitos técnicos listados nesta página, por exemplo, o armazenamento do Azure Blob ou o AWS S3.

Para obter recomendações sobre como implantar o AEM no Azure ou AWS, fora do Adobe Managed Services, recomendamos trabalhar diretamente com o provedor de nuvem ou parceiros da Adobe que oferecem suporte à implantação do AEM no ambiente de nuvem de sua escolha. O provedor ou parceiro de nuvem selecionado será responsável pelas especificações de dimensionamento, design e implementação da arquitetura., para atender aos requisitos específicos de desempenho, carga, escalabilidade e segurança.

### Plataformas do Dispatcher (Servidores da Web) {#dispatcher-platforms-web-servers}

O Dispatcher é o componente de balanceamento de carga e cache. [Baixe a versão](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html) mais recente do Dispatcher. O Experience Manager 6.4 requer o Dispatcher versão 4.3.1 ou superior.

Os seguintes servidores da Web são compatíveis com o Dispatcher versão 4.3.1:

| Plataforma | Nível de suporte |
|---|---|
| **Apache httpd 2.4.x**  (veja também 1.2 abaixo) | A: Suportado |
| Microsoft IIS 10 (Servidor de Informações da Internet) | A: Suportado |
| Microsoft IIS 8.5 (Servidor de Informações da Internet) | A: Suportado |

1. Os servidores da Web criados com base no código-fonte httpd do Apache terão o mesmo nível de suporte que a versão do httpd na qual se baseia. Em caso de dúvida, peça à Adobe confirmação do nível de suporte relacionado ao respectivo produto de servidor. Os seguintes casos:

   1. O servidor HTTP foi criado usando apenas distribuições oficiais de origem do Apache ou
   1. O servidor HTTP foi entregue como parte do sistema operacional no qual está sendo executado. Exemplos: IBM HTTP Server, Oracle HTTP Server

1. O Dispatcher não está disponível para o Apache 2.4.x para sistemas operacionais Windows.

## Plataformas compatíveis de clientes {#supported-client-platforms}

### Navegadores compatíveis para criação de interface de usuário {#supported-browsers-for-authoring-user-interface}

A interface do usuário do Adobe Experience Manager funciona com as seguintes plataformas de clientes. Todos os navegadores são testados com o conjunto padrão de plug-ins e complementos.

A interface do usuário do AEM é otimizada para telas maiores (geralmente notebooks e desktops) e fator de forma de tablet (como Apple iPad ou Microsoft Surface). O fator de forma de telefone não é suportado.

>[!NOTE]
>
>**Suporte para navegadores com ciclos de lançamento rápidos:**
>
>Atualizações de versão do Mozilla Firefox, Google Chrome e Microsoft Edge a cada poucos meses. A Adobe tem o compromisso de fornecer atualizações para o Adobe Experience Manager para manter o nível de suporte, conforme declarado abaixo, com as versões futuras desses navegadores.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Navegador</strong></td> 
   <td><strong>Suporte para interface do usuário<br /> </strong></td> 
   <td><strong>Suporte para interface clássica</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Google Chrome (Evergreen)</strong></td> 
   <td>A: Suportado</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge (Evergreen)</td> 
   <td>A: Suportado</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Microsoft Internet Explorer 11</td> 
   <td>A: Suportado</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox (Evergreen)</td> 
   <td>A: Suportado</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox último ESR [1]</td> 
   <td>A: Suportado</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 12.x no macOS</td> 
   <td>A: Suportado</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x no macOS</td> 
   <td>A: Suportado</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 10.x no macOS</td> 
   <td>A: Suportado</td> 
   <td>A: Suportado</td> 
  </tr> 
  <tr> 
   <td>Apple Safari no iOS 12.x</td> 
   <td>A: Suportado [2]</td> 
   <td>Z: Não suportado</td> 
  </tr> 
  <tr> 
   <td>Apple Safari no iOS 11.x</td> 
   <td>A: Suportado [2]</td> 
   <td>Z: Não suportado</td> 
  </tr> 
  <tr> 
   <td>Apple Safari no iOS 10.3</td> 
   <td>A: Suportado [2]</td> 
   <td>Z: Não suportado</td> 
  </tr> 
 </tbody> 
</table>

1. Versão de suporte estendido do Firefox [Saiba mais sobre isso em mozilla.org](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. suporte para Apple iPad

### Navegadores compatíveis com sites {#supported-browsers-for-websites}

Geralmente, o suporte de navegador para sites renderizados pelo AEM Sites depende da implementação de modelos de página do AEM, design e saída de componentes, e, portanto, está sob controle da parte que implementa essas partes.

### Clientes WebDAV {#webdav-clients}

**Microsoft Windows 7+**

Para se conectar com êxito com o Microsoft Windows 7+ a uma instância do AEM que não esteja protegida com SSL, a autenticação básica por rede não segura deve ser habilitada no Windows. Isso requer uma alteração no Registro do Windows do WebClient:

1. Localize a subchave do Registro:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Adicione a entrada do registro BasicAuthLevel a esta subchave usando um valor de 2 ou mais.

Consulte [KB do Suporte da Microsoft 841215](https://support.microsoft.com/default.aspx/kb/841215).

Para melhorar a capacidade de resposta do cliente WebDav no Windows - consulte [KB do suporte da Microsoft 2445570](https://support.microsoft.com/kb/2445570)

## Notas adicionais da plataforma {#additional-platform-notes}

Esta seção fornece observações especiais e informações mais detalhadas sobre a execução do Adobe Experience Manager e de seus complementos.

### IPv4 e IPv6 {#ipv-and-ipv}

Todos os elementos do Adobe Experience Manager (Instância, Dispatcher) podem ser instalados em redes IPv4 e IPv6.

A operação é contínua, pois nenhuma configuração especial é necessária. Você pode simplesmente especificar um endereço IP usando o formato adequado ao seu tipo de rede, se necessário.

Isso significa que, quando um endereço IP precisa ser especificado, você pode selecionar (conforme necessário) de:

* um endereço IPv6

   por exemplo `https://[ab12::34c5:6d7:8e90:1234]:4502`

* um endereço IPv4

   por exemplo `https://123.1.1.4:4502`

* um nome de servidor

   por exemplo, `https://www.yourserver.com:4502`

* o caso padrão de `localhost` será interpretado para instalações de rede IPv4 e IPv6

   por exemplo, `http://localhost:4502`

### Requisitos do complemento AEM Dynamic Media {#requirements-for-aem-dynamic-media-add-on}

O AEM Dynamic Media é desativado por padrão. Consulte [Ativando o Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Com o Dynamic Media ativado, os seguintes requisitos adicionais de sistema se aplicam:
>[!NOTE]
>
>Os seguintes requisitos de sistema se aplicam **_somente_** se você usar o Dynamic Media - Modo híbrido; Dynamic Media - O modo híbrido tem um servidor de imagem incorporado, que só é certificado em determinados sistemas operacionais.
>
>Para clientes do Dynamic Media que executam o Dynamic Media - modo Scene7 (ou seja, **dynamicmedia_scene7** runmode), não há requisitos de sistema adicionais; somente os mesmos requisitos de sistema do AEM. Dynamic Media - A arquitetura de modo Scene7 usa o serviço de imagem baseado em nuvem, não o serviço incorporado no AEM.

#### Hardware {#hardware}

Os seguintes requisitos de hardware se aplicam aos sistemas operacionais Linux e Windows:

* CPU Intel Xeon ou AMD Opteron com pelo menos 4 núcleos
* Mínimo de 16 GB de RAM

#### Linux {#linux}

O uso do Dynamic Media no Linux exige os seguintes pré-requisitos:

* RedHat Enterprise 7 ou CentOS 7 e posterior com os patches de correção mais recentes
* Sistema operacional de 64 bits
* Troca desabilitada (recomendada)
* SELinux desativado (consulte a observação a seguir)

>[!NOTE]
>
>Se a localidade estiver definida de modo que LC_CTYPE não seja igual a en_US.UTF-8, isso impedirá que a mídia dinâmica funcione. Para ver qual é o valor, digite &quot;locale&quot; no prompt de comando. Se não estiver definido como esse valor, defina a variável de ambiente LC_CTYPE como a string vazia, digitando &quot;export LC_CTYPE=&quot; antes de executar o AEM.

>[!NOTE]
>
>**Desabilitando o SELinux:** o Serviço de imagem não funciona com o SELinux ativado. Essa opção é ativada por padrão. Para corrigir esse problema, edite o arquivo **/etc/selinux/config** e altere o valor do SELinux de:
>
>`SELINUX=enforcing` para  `SELINUX=disabled`

>[!NOTE]
>
>**Arquitetura NUMA:** Sistemas com processadores com AMD64 e Intel EM64T são normalmente configurados como plataformas de arquitetura de memória não-uniformes (NUMA), o que significa que o kernel constrói vários nós de memória no momento da inicialização em vez de construir um único nó de memória.
>
>A construção de vários nós pode resultar no esgotamento da memória em um ou mais nós, antes que outros nós fiquem esgotados. Quando ocorre esgotamento de memória, o kernel pode decidir interromper processos (por exemplo, o Servidor de Imagem ou o Servidor de Plataforma) mesmo que haja memória disponível.
>
>Portanto, a Adobe recomenda que, se você estiver executando um sistema desse tipo, desative o NUMA usando a opção de inicialização **numa=off** para evitar que o kernel mate esses processos.

>[!NOTE]
>
>**O nome do host do servidor deve ser solucionável:** verifique se o nome do host do servidor é resolvível para um endereço IP. Se isso não for possível, adicione o nome de host totalmente qualificado e o endereço IP a **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* Troque o espaço igual a pelo menos o dobro da quantidade de memória física (RAM)

Para usar o Dynamic Media no Windows, os redistribuíveis do Microsoft Visual Studio 2010, 2013 e 2015 para x64 e x86 devem ser instalados.

x64

* O Microsoft Visual Studio 2010 redistribuível pode ser encontrado em [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)
* O Microsoft Visual Studio 2013 redistribuível pode ser encontrado em [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
* O Microsoft Visual Studio 2015 redistribuível pode ser encontrado em [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)

x86

* O Microsoft Visual Studio 2010 redistribuível pode ser encontrado em [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* O Microsoft Visual Studio 2013 redistribuível pode ser encontrado em [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* O Microsoft Visual Studio 2015 redistribuível pode ser encontrado em [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

#### MacOS {#macos}

* 10.9.x e posterior
* Somente suportado para fins de avaliação e demonstração

### Requisitos do Gerador de PDF para AEM Forms {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Produto</strong></p> </th> 
   <th><p><strong>Formatos compatíveis para conversão em PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Rastreamento clássico do Acrobat 2017</a></p> </td> 
   <td><p>XPS, formatos de imagem (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF e DWF</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2016</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF e TXT</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2013</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF e TXT</td> 
  </tr> 
  <tr> 
   <td>Corel WordPerfect X7</td> 
   <td>WP, WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formatos de imagem (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPX, JP2, J2K, J2C, JPC), HTML, M, RTF e TXT</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formatos de imagem (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPX, JP2, J2K, J2C, JPC), HTML, M, RTF e TXT</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>O PDF Generator suporta apenas versões em inglês, francês, alemão e japonês dos sistemas operacionais e aplicativos compatíveis.
>
>Além disso:
>
>* O PDF Generator requer [o Acrobat 2017 versão de rastreamento clássica 17.011.30078 ou posterior](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) para executar a conversão.
>* O AEM Forms suporta apenas edições de 32 bits de software suportado.
>* Os recursos PDF OCR (PDF pesquisável), Otimizar PDF e Exportar PDF são suportados somente no Microsoft Windows.
>* O serviço HTML2PDF está obsoleto no AIX.
>* As conversões do PDF Generator para OpenOffice são suportadas apenas no Windows, Linux e Solaris.
>* Os recursos OCR PDF, Otimizar PDF e Exportar PDF são suportados somente no Windows.
>* Uma versão do Acrobat é fornecida com o AEM Forms para ativar a funcionalidade do Gerador de PDF. A versão agrupada só deve ser acessada programaticamente com o AEM Forms, durante o período da licença do AEM Forms, para uso com o Gerador de PDF do AEM Forms. Para obter mais informações, consulte a descrição do produto AEM Forms de acordo com sua implantação ([No local](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) ou [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;

>



### Requisitos do AEM Forms Designer {#requirements-for-aem-forms-designer}

* Microsoft® Windows® 2012 Server R2, Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10
* Processador de 1 GHz ou mais rápido com suporte para PAE, NX e SSE2.
* 1 GB de RAM para 32 bits ou 2 GB de RAM para SO de 64 bits
* 16 GB de espaço em disco para 32 bits ou 20 GB de espaço em disco para SO de 64 bits
* Memória gráfica - 128 MB de GPU (256 MB recomendados)
* 2,35 GB de espaço disponível em disco rígido
* Resolução do monitor de 1024 X 768 pixels ou superior
* Aceleração de hardware de vídeo (opcional)
* Acrobat Pro DC, Acrobat Standard DC ou Adobe Acrobat Reader DC
* Privilégios administrativos para instalar o Designer

### Requisitos para write-back de metadados XMP do AEM Assets {#requirements-for-aem-assets-xmp-metadata-write-back}

O write-back de XMP é compatível e ativado para as seguintes plataformas e formatos de arquivo:

**Sistemas operacionais**

* Linux (32 bits, precisa de suporte para aplicativos de 32 bits em sistemas de 64 bits). Para obter etapas para instalar bibliotecas de clientes de 32 bits, consulte [Como habilitar a extração e o write-back de XMP no RedHat Linux de 64 bits](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

* Windows Server
* Oracle Solaris
* Mac OS X (64 bits)

**Formatos de arquivo**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### Requisitos do reprodutor do AEM Screens {#requirements-for-aem-screens-player}

O Player do AEM Screens versão 3.3.x é compatível com os seguintes sistemas operacionais:

* Microsoft Windows 10 Enterprise LTSB
* Google Chome OS 62+
* Google Android 5.1.1 com sistema Android WebView atualizado versão 52+
* Apple iOS 10.3+
* Apple macOS 10.12+
