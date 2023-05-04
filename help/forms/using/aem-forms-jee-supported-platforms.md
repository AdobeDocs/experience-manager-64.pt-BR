---
title: Plataformas compatíveis com AEM Forms no JEE
seo-title: Supported Platforms for AEM Forms on JEE
description: Lista de componentes de infraestrutura necessários e compatíveis para instalar o AEM Forms no JEE
seo-description: List of infrastructure components required and supported for installing AEM Forms on JEE
uuid: 22f05fd4-f9fc-423e-8a86-1e75df4b2b44
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 1b9f8d98-e7e8-4b9b-a0df-52ccba324da3
role: Admin
exl-id: 6609c625-0591-42fd-910b-c7c65d52c5f1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3366'
ht-degree: 1%

---

# Plataformas compatíveis com AEM Forms no JEE {#supported-platforms-for-aem-forms-on-jee}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Plataformas compatíveis {#supported-platforms}

### Níveis de suporte {#support-levels}

O AEM Forms no servidor JEE pode ser configurado usando qualquer combinação de sistemas operacionais suportados, servidores de aplicativos, bancos de dados, drivers de banco de dados, JDK, servidores LDAP e servidores de email.

Este documento lista as plataformas de cliente e servidor compatíveis com o AEM Forms no JEE. O Adobe fornece vários níveis de suporte, tanto para as configurações recomendadas quanto para outras configurações. O documento também lista outros softwares suportados e suas versões, exceções, definições de patch e políticas de suporte a patches de software de terceiros.

>[!NOTE]
>
>* Para obter uma lista completa de exceções para plataformas de servidor compatíveis, consulte [Exceções às plataformas de servidor suportadas](#exceptions-to-supported-server-platforms).
>* O AEM Forms no JEE é compatível somente com as versões em inglês, francês, alemão e japonês dos sistemas operacionais e aplicativos compatíveis.
>


### Configurações recomendadas {#recommendedconfigurations}

O Adobe recomenda essas configurações e oferece suporte total ou restrito como parte do contrato padrão de manutenção de software:

<table> 
 <tbody> 
  <tr> 
   <th>Nível de compatibilidade</th> 
   <th>Descrição</th> 
  </tr> 
  <tr> 
   <td>A: Suportado<br /> </td> 
   <td>O Adobe oferece suporte e manutenção completos para essa configuração. Essa configuração é coberta pelo processo de garantia de qualidade do Adobe.</td> 
  </tr> 
  <tr> 
   <td>R: Suporte restrito</td> 
   <td>O Adobe fornece suporte total para essa configuração após atender a determinados pré-requisitos. Entre em contato com o suporte empresarial do Adobe para saber mais sobre os pré-requisitos e solicitar o suporte.</td> 
  </tr> 
  <tr> 
   <td>L: Apoio limitado</td> 
   <td>O Adobe oferece suporte e manutenção completos para essas configurações após determinados pré-requisitos serem atendidos. Nem todos os recursos estão disponíveis na configuração. Entre em contato com o suporte empresarial do Adobe para saber mais sobre os pré-requisitos e solicitar o suporte.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Configurações não suportadas {#unsupported-configurations}

| Nível de compatibilidade | Descrição |
|---|---|
| E: Espera-se que funcione | Espera-se que a configuração funcione, e não há relatórios em contrário. |
| Z: Não suportado | A configuração não é suportada. O Adobe não faz declarações sobre se a configuração funciona e não oferece suporte a ela. |

### Máquinas Virtuais Java (JVM) {#java-virtual-machines-jvm}

A Adobe Experience Manager Forms requer uma máquina virtual Java para execução, fornecida pela distribuição do Java Development Kit (JDK). A Adobe Experience Manager opera com as seguintes versões das máquinas virtuais Java:

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Platform</strong></p> </th> 
   <th><p><strong>Nível de compatibilidade</strong></p> </th> 
   <th><p><strong>Definições de patch compatíveis</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Oracle Java™ SE 8 (64 bits)</p> </td> 
   <td><p>A: Suportado</p> </td> 
   <td><p>Versões e atualizações secundárias</p> </td> 
  </tr> 
  <tr> 
   <td>Máquina Virtual IBM® J9 (compilação 2.8, JRE 1.8.0)</td> 
   <td>A: Suportado</td> 
   <td>Versões e atualizações secundárias</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* O AEM Forms no JEE suporta apenas JVMs de 64 bits em ambientes de produção.
>* É recomendável rastrear os Boletins de segurança do fornecedor do Java para garantir a segurança dos ambientes de produção e instalar as atualizações mais recentes do Java.
>


### Bancos de dados e persistência de CRX {#databases-and-crx-persistence}

#### Suporte à persistência de AEM {#aem-persistence-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Platform</strong></p> </td> 
   <td><p><strong> Descrição</strong></p> </td> 
   <td><p><strong>Nível de compatibilidade</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Sistema de arquivos</p> </td> 
   <td><p>Microkernel do Repositório (arquivos TAR MK)</p> </td> 
   <td><p>Compatível</p> </td> 
  </tr> 
  <tr> 
   <td><p>MongoDB Enterprise 3.4</p> </td> 
   <td><p>Microkernel do Repositório</p> </td> 
   <td><p>Compatível</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>Microkernel do Repositório</td> 
   <td>Compatível</td> 
  </tr> 
  <tr> 
   <td><p>Oracle Database 12c Release 1</p> </td> 
   <td><p>Microkernel do Repositório</p> </td> 
   <td><p>Compatível</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td><p>Microkernel do Repositório</p> </td> 
   <td><p>Compatível</p> </td> 
  </tr> 
 </tbody> 
</table>

* O MongoDB é um software de terceiros e não está incluído no pacote de licenciamento AEM. Para obter mais informações, consulte [Política de licenciamento do MongoDB](https://www.mongodb.org/about/licensing/) página.

* Para obter o máximo de sua implantação de AEM, o Adobe recomenda o licenciamento da versão MongoDB Enterprise para se beneficiar do suporte profissional.
* O Atendimento ao cliente do Adobe ajudará a solucionar problemas relacionados ao uso do MongoDB com AEM. Para obter mais informações, consulte o [MongoDB para página do Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
* &#39;Sistema de Arquivos&#39; inclui armazenamento de bloco compatível com POSIX. Isso inclui a tecnologia de armazenamento de rede. Considere que o desempenho do sistema de arquivos pode variar e influencia o desempenho geral. É recomendável carregar AEM de teste em combinação com o sistema de arquivos remoto/de rede.
* Somente o MongoDB Storage Engine WiredTiger é compatível.
* A Partilha de MongoDB não é suportada no AEM.
* O AEM Forms no JEE não oferece suporte ao MySQL para persistência de RDBMK.
* O módulo Segurança de documento não usa o Repositório de conteúdo. Isso significa que, se você estiver usando apenas a Segurança de documento e não planeja usar formulários HTML Workspace, HTML5 ou adaptáveis, não instale o Repositório de conteúdo.
* O AEM Forms no JEE é compatível com a arquitetura Oracle Multitenant.

#### Suporte a DATABASE {#database-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Platform</strong></p> </td> 
   <td><p><strong> Descrição</strong></p> </td> 
   <td><p><strong>Nível de suporte AEM 6.4</strong></p> </td> 
   <td><p><strong>Nível de suporte AEM Forms 6.4 no JEE</strong></p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>Microkernel do Repositório</td> 
   <td>Compatível</td> 
   <td>Compatível</td> 
  </tr> 
  <tr> 
   <td><p>Oracle Database 12c Release 1</p> </td> 
   <td><p>Microkernel do Repositório</p> </td> 
   <td><p>Compatível</p> </td> 
   <td><p>Compatível</p> </td> 
  </tr> 
  <tr> 
   <td><p>MySQL 5.7.19<br /> </p> </td> 
   <td><p>Microkernel do Repositório</p> </td> 
   <td><p>Espera-se que funcione</p> </td> 
   <td><p>Compatível</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td><p>Microkernel do Repositório</p> </td> 
   <td><p>Espera-se que funcione</p> </td> 
   <td><p>Compatível</p> </td> 
  </tr> 
 </tbody> 
</table>

### Drivers de banco de dados {#database-drivers}

<table> 
 <tbody> 
  <tr> 
   <th>Banco de dados </th> 
   <th><p><strong>Platform</strong></p> </th> 
   <th><p><strong>Definições de patch compatíveis</strong></p> </th> 
  </tr> 
  <tr> 
   <td>MySQL</td> 
   <td><p>MySQL Connector/J 5.7</p> <p>mysql-connector-java-5.1.44-bin.jar(versão 5.1.44)</p> </td> 
   <td><p>Fornecido com AEM Forms na instalação JEE</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server<br /> </td> 
   <td><p>Driver JDBC do Microsoft® SQL Server 6.2.1.0 (obsoleto) <br /> </p> <p>sqljdbc6.jar</p> </td> 
   <td><p>Fornecido com AEM Forms na instalação JEE.</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server<br /> </td> 
   <td><p>Driver Microsoft® SQL Server JDBC 6.2.2.0<br /> </p> <p>sqljdbc6.jar</p> </td> 
   <td><p>Baixar do site da Microsoft.</p> </td> 
  </tr> 
  <tr> 
   <td>Oracle</td> 
   <td><p>Driver JDBC do Oracle Database 12.1.0.2.0</p> <p>ojdbc7.jar (versão 12.1.0.2.0)<br /> </p> </td> 
   <td><p>Fornecido com AEM Forms na instalação JEE.</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2</td> 
   <td><p>Driver IBM® DB2 Universal JDBC 4.16.53 (db2jcc4.jar)</p> </td> 
   <td><p>Baixe o driver de <a href="https://www-01.ibm.com/support/docview.wss?uid=swg21363866" target="_blank">Site do IBM</a></p> </td> 
  </tr> 
 </tbody> 
</table>

### Servidores de aplicativos {#application-servers}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> Platform</strong></p> </td> 
   <td><p><strong>Nível de compatibilidade</strong></p> </td> 
   <td><p><strong>Definições de patch compatíveis</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle WebLogic Server 12.2.1 (12c R2) <sup>[1] [2] [4] [8]</sup></p> </td> 
   <td><p>A: Suportado</p> </td> 
   <td><p>Service pack e atualizações críticas</p> </td> 
  </tr> 
  <tr> 
   <td>IBM® WebSphere® Application Server 9.0 <sup>[2] [6]</sup><br /> </td> 
   <td>A: Suportado</td> 
   <td>Service pack e atualizações críticas</td> 
  </tr> 
  <tr> 
   <td><p>JBoss® Enterprise Application Platform (EAP) 7.0.6 <sup>[1] [4] [5] [7] [8][11]</sup></p> </td> 
   <td><p>A: Suportado</p> </td> 
   <td><p>Correções e correções cumulativas para a versão EAP compatível<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Os clusters IBM® WebSphere® são suportados apenas nas edições de implantação de rede.

### Sistemas operacionais para servidores {#server-operating-systems}

#### Ambientes de produção {#production-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong> Platform</strong></p> </th> 
   <th><p><strong>Nível de suporte</strong></p> </th> 
   <th><p><strong>Definições de patch compatíveis</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>A: Suportado</td> 
   <td>Pacotes de serviços e atualizações críticas</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server 2012 R2 V6.3</p> </td> 
   <td><p>A: Suportado</p> </td> 
   <td><p>Pacotes de serviços e atualizações críticas</p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle Solaris™ 11 - V5.11<sup> [3] [10]</sup></p> </td> 
   <td><p>L: Limitado</p> </td> 
   <td><p>Atualizações e correções</p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat Enterprise Linux 7 (Kernel 3.x)</br><b>Observação:</b> <a href="https://access.redhat.com/articles/4665701">Red Hat Enterprise Linux 6</a> O atinge a fase de Fim da Manutenção e as transições para a fase de Suporte ao Ciclo de Vida Estendido em 30 de novembro de 2020. O Adobe recomenda o Red Hat Enterprise Linux 7 para atualizações e novas instalações. As instalações existentes podem usar o Red Hat Enterprise Linux 6 durante a fase de Suporte Estendido ao Ciclo de Vida.</p> </td> 
   <td><p>A: Suportado</p> </td> 
   <td><p>Versões secundárias, atualizações cumulativas e atualizações críticas</p> </td> 
  </tr> 
  <tr> 
   <td><p>SUSE® Linux® Enterprise Server 12</p> </td> 
   <td><p>A: Suportado</p> </td> 
   <td><p>Service packs, correções cumulativas e atualizações críticas de segurança</p> </td> 
  </tr> 
  <tr> 
   <td>Oracle Linux® 7 Update 3</td> 
   <td>A: Suportado</td> 
   <td>Service packs, correções cumulativas e atualizações críticas de segurança</td> 
  </tr> 
  <tr> 
   <td>CentOS 7<sup> [9]</sup></td> 
   <td>A: Suportado</td> 
   <td>Service packs, correções cumulativas e atualizações críticas de segurança</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2 [10]</td> 
   <td>A: Suporte limitado</td> 
   <td>Service packs, correções cumulativas e atualizações críticas de segurança</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>O AEM Forms no JEE suporta apenas sistemas operacionais de 64 bits.

#### Ambiente virtualizado {#virtualized-environment}

Você pode executar o AEM Forms no JEE em uma máquina física ou em um ambiente virtual. No entanto, se você encontrar qualquer problema com o AEM Forms em um ambiente virtual, tente replicar o problema em uma máquina física. Se o problema persistir na máquina física, entre em contato com o Suporte do Adobe para obter uma resolução. Para problemas que não são replicados na máquina física, entre em contato com o fornecedor do ambiente virtual.

#### Ambientes de desenvolvimento {#development-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Plataforma (Versão básica)</strong></p> </th> 
   <th>Nível de compatibilidade</th> 
   <th><p><strong>Definições de patch compatíveis</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Windows® 10</p> </td> 
   <td>E: Espera-se que funcione</td> 
   <td><p>Service pack e atualizações críticas</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* O AEM Forms no JEE suporta apenas sistemas operacionais de 64 bits.
>* O serviço PDF Generator não é suportado no Windows 10.
>


### Exceções às plataformas de servidor suportadas {#exceptions-to-supported-server-platforms}

Considere as seguintes exceções ao escolher uma plataforma para configurar seu AEM Forms no servidor JEE.

1. O AEM Forms no JEE não suporta Oracle WebLogic e JBoss® no IBM® AIX®.
1. O AEM Forms no JEE não oferece suporte ao Oracle WebLogic e IBM® WebSphere® com MySQL.
1. O AEM Forms no JEE não é compatível com o Oracle Solaris™ com arquitetura Intel® (somente o SPARC® é compatível).
1. O AEM Forms no JEE não oferece suporte ao Oracle WebLogic e JBoss no SUSE Linux Enterprise Server 12. Somente o IBM WebSphere é compatível com o SUSE Linux Enterprise Server 12.
1. O AEM Forms no JEE não é compatível com nenhum JDK com JBoss® que não seja o Oracle Java™ SE.
1. O AEM Forms no JEE não é compatível com nenhum JDK com IBM® WebSphere® que não seja o IBM® JDK.
1. O AEM Forms no JEE não suporta IBM® DB2 com JBoss®.
1. O CRX-repository suporta persistência de tipo TarMK, MongoDB e bancos de dados relacionais (RDBMK). Não é possível ter dois sistemas de banco de dados diferentes entre o servidor de aplicativos e o repositório CRX. No entanto, em um ambiente AEM Forms no JEE, você pode usar o MongoMK com o repositório CRX e um banco de dados relacional compatível com o servidor de aplicativos.
1. O AEM Forms no JEE não é compatível com o servidor de aplicativos WebSphere no CentOS.
1. Os sistemas operacionais AIX e Solaris estão disponíveis apenas para clientes de atualização.
1. O AEM Forms no JEE não é compatível com o RBAC (controle de acesso baseado em função do JBoss).

Além disso, considere os seguintes pontos ao escolher o software para o Adobe AEM Forms em implantações JEE:

* O AEM Forms no JEE oferece suporte a atualizações, correções e pacotes de correções além da versão principal e secundária especificada do software suportado. No entanto, a atualização para a próxima versão principal ou secundária não é suportada, a menos que especificado.
* As instalações baseadas em cluster não oferecem suporte à persistência de TarMK. Para obter informações sobre a persistência suportada, consulte [Como escolher um tipo de persistência para uma instalação do AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).
* O AEM Forms no JEE é compatível com vários softwares de terceiros de acordo com nosso [Política de suporte a software de terceiros](#third-party-patch-support-policy).
* O AEM Forms no JEE oferece suporte a plataformas de acordo com o suporte fornecido por fornecedores terceirizados. Algumas combinações podem não ser permitidas por fornecedores terceirizados. Por exemplo, muitos fornecedores não certificaram seus servidores de aplicativos com o IBM® DB2. Como resultado, o AEM Forms no JEE também não é compatível com essas combinações. Para garantir que você escolha as versões de software compatíveis, verifique também a matriz de suporte dos fornecedores de terceiros.
* O AEM Forms no JEE não é compatível com o TarMK Cold Standby.
* O AEM Forms no JEE não oferece suporte a clustering vertical.
* O AEM Forms no JEE não oferece suporte ao banco de dados MySQL em um ambiente em cluster.
* RDBMK não funciona com bancos de dados DB2, MYSQL, MS SQL e Oracle quando os módulos JDBC do pacote são configurados no Weblogic.

### Servidores LDAP (opcional) {#ldap-servers-optional}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Produto (Versão base)</strong></p> </th> 
   <th><p><strong>Definições de patch compatíveis</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Oracle Unified Diretory (OUD) 11g Versão 2</td> 
   <td>Service packs</td> 
  </tr> 
  <tr> 
   <td>Microsoft Ative Diretory 2016</td> 
   <td>Versão de manutenção e pacotes de correção</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Ative Diretory 2012</p> </td> 
   <td><p>Atualizações fornecidas com o sistema operacional</p> </td> 
  </tr> 
  <tr> 
   <td><p>Serviços LDS do Microsoft Ative Diretory 2012</p> </td> 
   <td><p>Atualizações fornecidas com o sistema operacional</p> </td> 
  </tr> 
  <tr> 
   <td><p>IBM® Tivoli Diretory Server 6.4</p> </td> 
   <td><p>Pacotes de recursos e correções provisórias</p> </td> 
  </tr> 
  <tr> 
   <td>IBM Lotus Domino 8.5.0</td> 
   <td>Versão de manutenção e pacotes de correção</td> 
  </tr> 
  <tr> 
   <td>Novell eDirectory 8.8.7</td> 
   <td>Atualizações do produto</td> 
  </tr> 
 </tbody> 
</table>

### Servidores de email (opcional) {#email-servers-optional}

* IBM Lotus Domino 9.0
* Microsoft Exchange 2013
* Microsoft Office 365

### Gerentes de conteúdo e conectores correspondentes {#content-managers-and-corresponding-connectors}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Produto<br /> </strong></td> 
   <td><strong>Versão</strong></td> 
  </tr> 
  <tr> 
   <td>Servidor do IBM Content Manager</td> 
   <td>8.5 Fix Pack 2<br /> </td> 
  </tr> 
  <tr> 
   <td>Cliente do IBM Content Manager</td> 
   <td><p>Versão 8.5<strong> </strong>é compatível</p> </td> 
  </tr> 
  <tr> 
   <td>EMC Documentum</td> 
   <td>7.0 e 7.3</td> 
  </tr> 
  <tr> 
   <td>IBM Filenet</td> 
   <td>5.2</td> 
  </tr> 
  <tr> 
   <td>Microsoft Sharepoint</td> 
   <td>2013 e 2016<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Suporte para Cordova {#support-for-cordova}

O aplicativo AEM Forms agora é compatível com o Apache Cordova. A seguir estão as versões específicas da plataforma do Cordova que são compatíveis:

* Apache Cordova 6.4.0
* Cordova iOS 4.3.0
* Cordova Android 6.0.0
* Cordova Windows 4.4.3

### Suporte de software para PDF-Generator {#software-support-for-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Produto</strong></p> </th> 
   <th><p><strong>Formatos suportados para conversão para PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017 classic track</a></td> 
   <td>XPS, formatos de imagem (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPX, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF e DWF</td> 
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
   <td>WordPerfect X7</td> 
   <td>WP, WPD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2013</td> 
   <td>VSD, VSDX</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD, VSDX</td> 
  </tr> 
  <tr> 
   <td>Editor Microsoft® 2013</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Editor Microsoft® 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Projeto Microsoft® 2013</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Projeto Microsoft® 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formatos de imagem (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPX, JP2, J2K, J2C, JPC), HTML, M, RTF e TXT</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 3.4</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formatos de imagem (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPX, JP2, J2K, J2C, JPC), HTML, M, RTF e TXT</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>O PDF Generator suporta apenas versões em inglês, francês, alemão e japonês dos sistemas operacionais e aplicativos compatíveis.
>
>Além disso:
>
>* O PDF Generator requer a versão de 32 bits do [Acrobat 2017 classic track versão 17.011.30078 ou posterior](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) para executar a conversão.
>* O PDF Generator suporta apenas a versão de varejo de 32 bits do Microsoft Office Professional Plus e outros softwares necessários para a conversão.
>* O PDF Generator não é compatível com o Microsoft Office 365.
>* As conversões PDF Generator para OpenOffice são suportadas apenas no Windows, Linux e Solaris.
>* O serviço HTML2PDF está obsoleto no AIX.
>* Os recursos PDF, Optimize PDF e Export PDF do OCR são suportados apenas no Windows.
>* Uma versão do Acrobat é fornecida com o AEM Forms para habilitar a funcionalidade PDF Generator. A versão agrupada só deve ser acessada programaticamente com o AEM Forms, durante o período da licença do AEM Forms, para uso com o PDF Generator da AEM Forms. Para obter mais informações, consulte a descrição do produto AEM Forms de acordo com sua implantação ([No local](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) ou [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;
>


### Exceções ao suporte de acessibilidade {#exceptions-to-accessibility-support}

Os seguintes subsistemas do AEM Forms não são [508](https://www.section508.gov/) conforme:

* Interface adaptável de criação do Forms
* Interface do usuário de criação do Forms Manager
* Interface do usuário de criação do Gerenciamento de correspondência
* Interface do usuário do administrador (interface do usuário do Console de administração)

## Requisitos de sistema para AEM Forms no JEE {#system-requirements-for-aem-forms-on-jee}

### Requisitos mínimos de hardware {#minimum-hardware-requirements}

<table> 
 <tbody> 
  <tr> 
   <td>Platform</td> 
   <td>Requisito mínimo de hardware</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server</td> 
   <td>Processador Intel® Xeon® E5-2680, de 2,4 GHz ou equivalente<br /> VMWare ESX 5.1 ou posterior<br /> RAM: 6 GB (SO de 64 bits com JVM de 64 bits)<br /> Espaço livre em disco: 15 GB de espaço temporário mais 22 GB<br /> para AEM Forms no JEE</td> 
  </tr> 
  <tr> 
   <td>Sun Solaris</td> 
   <td>Processador UltraSPARC® IIIi de 1,5 GHz<br /> Particionamento de contêineres Solaris (regiões)<br /> RAM: 6 GB (SO de 64 bits com JVM de 64 bits)<br /> Espaço livre em disco: 6 GB de espaço temporário mais 22 GB<br /> para AEM Forms no JEE</td> 
  </tr> 
  <tr> 
   <td>IBM AIX</td> 
   <td>P6 Série 520 (Modelo 52A) 9131-52A, processador de 1,8 GHz<br /> Particionamento LPAR<br /> RAM: 6 GB (SO de 64 bits com JVM de 64 bits)<br /> Espaço livre em disco: 6 GB de espaço temporário mais 22 GB<br /> para AEM Forms no JEE</td> 
  </tr> 
  <tr> 
   <td>SUSE Linux Enterprise Server</td> 
   <td>Intel Xeon E5-2670v2, 1 vCPU, processador de 2,5 GHz<br /> AWS m3.medium (3 ECUs)<br /> RAM: 6 GB (SO de 64 bits com JVM de 64 bits)<br /> Espaço livre em disco: 6 GB de espaço temporário mais 22 GB<br /> para AEM Forms no JEE</td> 
  </tr> 
  <tr> 
   <td>Red Hat Enterprise Linux</td> 
   <td>Intel Xeon E5-2670v2, 1 vCPU, processador de 2,5 GHz<br /> AWS m3.medium (3 ECUs)<br /> RAM: 6 GB (SO de 64 bits com JVM de 64 bits)<br /> Espaço livre em disco: 6 GB de espaço temporário mais 22 GB<br /> para AEM Forms no JEE<br /> </td> 
  </tr> 
  <tr> 
   <td>Requisitos de hardware para um pequeno ambiente de produção</td> 
   <td> 
    <ul> 
     <li><strong>Ambiente alimentado pela Intel</strong>: Intel® Xeon® E5-2680, 2,4 GHz ou superior. O uso de um processador dual core melhora ainda mais o desempenho</li> 
     <li><strong>Ambiente alimentado pela Sun SPARC:</strong> UltraSPARC V ou posterior</li> 
     <li><strong>Ambiente alimentado pelo IBM AIX:</strong> Power6 ou posterior<br /> </li> 
     <li><strong>Memória: </strong>4 GB <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

Para obter requisitos adicionais, consulte:

* [Requisitos de sistema para um AEM Forms de servidor único na implantação do JEE](https://www.adobe.com/go/learn_aemforms_sysreq_single_64)
* [Requisitos de sistema para um AEM Forms em cluster na implantação JEE](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_64)

## Clientes compatíveis com AEM Forms no JEE {#supported-clients-for-aem-forms-on-jee}

### Workbench {#workbench}

>[!NOTE]
>
>Os sistemas operacionais de 32 e 64 bits são compatíveis.

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Platform</strong></p> </th> 
   <th><p><strong>Definições de patch compatíveis</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Windows® 10</p> <p>(Empresa, Pro, Básico)</p> </td> 
   <td>Pacotes de serviços e atualizações críticas</td> 
  </tr> 
  <tr> 
   <td>Servidor Microsoft® Windows® 2012 R2</td> 
   <td>Pacotes de serviços e atualizações críticas</td> 
  </tr> 
  <tr> 
   <td>Servidor Microsoft® Windows® 2016</td> 
   <td>Pacotes de serviços e atualizações críticas</td> 
  </tr> 
 </tbody> 
</table>

* Espaço em disco para instalação: 1,7 GB apenas para Workbench, 2,7 GB em uma única unidade para uma instalação completa do Workbench, do Designer e o conjunto de amostras de 400 MB para diretórios de instalação temporários - 200 MB no diretório temporário do usuário e 200 MB no diretório temporário do Windows

>[!NOTE]
>
>Se todos esses locais residirem em uma única unidade, deverá haver 1,5 GB de espaço disponível durante a instalação. Os arquivos copiados para os diretórios temporários são excluídos quando a instalação é concluída.

* Memória para executar o Workbench: 2 GB de RAM
* Requisito de hardware: Processador Intel® Pentium® 4 ou AMD equivalente, 1 GHz
* Resolução mínima do monitor de 1024 X 768 pixels ou superior com cor de 16 bits ou superior
* Conexão de rede TCP/IPv4 ou TCP/IPv6 ao AEM Forms no servidor JEE

>[!NOTE]
>
>Você deve ter privilégios Administrativos para instalar o Workbench no Windows. Se você estiver instalando usando uma conta que não seja de administrador, o instalador solicitará as credenciais de uma conta apropriada.

### Designer {#designer}

* Servidor Microsoft® Windows® 2012 R2, Servidor Microsoft® Windows® 2016, Servidor Microsoft® Windows® 2019, Microsoft® Windows® 10
* Processador de 1 GHz ou mais rápido com suporte para PAE, NX e SSE2.
* 1 GB de RAM para 32 bits ou 2 GB de RAM para SO de 64 bits
* 16 GB de espaço em disco para 32 bits ou 20 GB de espaço em disco para SO de 64 bits
* Memória gráfica - 128 MB de GPU (256 MB recomendados)
* 2,35 GB de espaço disponível em disco rígido
* Resolução do monitor de 1024 X 768 pixels ou superior
* Aceleração de hardware de vídeo (opcional)
* Acrobat Pro DC, Acrobat Standard DC ou Adobe Acrobat Reader DC
* Privilégios administrativos para instalar o Designer

### Adobe Acrobat e Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Acrobat e Adobe Reader (Base)</strong></p> </th> 
   <th><p><strong>Definições de patch compatíveis</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Acrobat 2017 (rastreamento clássico)</td> 
   <td>Versão 17.011.30078 ou posterior<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>A família de produtos Acrobat DC apresenta duas trilhas para Acrobat e Reader, que são produtos essencialmente diferentes: &quot;Classic&quot; e &quot;Continuous.&quot; Para obter detalhes e uma comparação das duas faixas, consulte [https://www.adobe.com/go/acrobatdctracks.](https://www.adobe.com/go/acrobatdctracks)

### Navegadores {#browsers}

#### Desktops {#desktops}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Navegador (Base)</strong></p> </th> 
   <th><p><strong>Nível de suporte</strong></p> </th> 
   <th><p><strong>Definições de patch compatíveis</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft Edge</p> </td> 
   <td><p>A: Suportado</p> </td> 
   <td><p>Service packs e atualizações</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mozilla Firefox 45.x</p> </td> 
   <td><p>A: Suportado</p> </td> 
   <td><p>Todas as atualizações</p> </td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome 46+</p> </td> 
   <td><p>A: Suportado</p> </td> 
   <td><p>Todas as atualizações</p> </td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x</td> 
   <td>A: Suportado</td> 
   <td>Todas as atualizações</td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome e Firefox no MAC OS X</p> </td> 
   <td><p>A: Suportado</p> </td> 
   <td><p>Todas as atualizações</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Algumas exceções relacionadas ao navegador para desktops são as seguintes:
>
>* A maioria dos navegadores modernos não suporta mais plug-ins com base NPAPI. Para obter informações sobre como isso afeta os aplicativos e fluxos de trabalho do AEM Forms, consulte [Descontinuação de plug-ins de navegador NPAPI e seu impacto](https://helpx.adobe.com/aem-forms/kb/discontinuation-of-npapi-plugins-impact-on-aem-forms.html).
>* O Safari é compatível somente no Macintosh OS X.


#### Clientes móveis {#mobile-clients}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Navegador (Base)</strong></p> </th> 
   <th><p><strong>Definições de patch compatíveis</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Chrome no Android™ 4.1.2 e superior</p> </td> 
   <td><p>Todas as atualizações</p> </td> 
  </tr> 
  <tr> 
   <td>Safari no iOS 15.1 e superior</td> 
   <td>Todas as atualizações</td> 
  </tr> 
  <tr> 
   <td>Internet Explorer no Windows 10</td> 
   <td>Todas as atualizações</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge<br /> </td> 
   <td>Todas as atualizações<br /> </td> 
  </tr> 
  <tr> 
   <td>Navegador Android nativo no Android™ 4.4 e superior</td> 
   <td>Todas as atualizações</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* O Forms Portal é compatível somente com o Safari no iPad.
>


### Aplicativo AEM Forms {#aem-forms-workspace-app}

#### Suporte a dispositivo móvel {#mobile-device-support}

O aplicativo AEM Forms está disponível nas seguintes plataformas:

| **Platform** | **Dispositivos compatíveis** |
|---|---|
| Apple iOS | Apple iPhone, iPad, iPad Air e iPad mini executando o iOS 15.1 e superior. |
| Google Android | Android 4.4 (Kit Android) e superior *[API Nível 19 e superior]*. O aplicativo AEM Forms é certificado em tablets Samsung Galaxy de 7 e 10 polegadas e em tablet Google Nexus de 7 polegadas e smartphones populares. |
| Microsoft Windows | Dispositivos Microsoft Surface, tablets, laptops e desktops que executam o sistema operacional Microsoft Windows 10. |

### Flash Player Adobe {#adobe-flash-player}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Flash Player (Base)</strong></p> </th> 
   <th><p><strong>Definições de patch compatíveis</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Versão mais recente do Flash Player</p> </td> 
   <td><p>Versões e atualizações secundárias</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Adobe will [pare de atualizar e distribuir o Flash Player no final de 2020](https://theblog.adobe.com/adobe-flash-update/).

### Extensão Adobe Document Security para Microsoft Office {#adobe-rights-management-extension-for-microsoft-office}

Clique em [here](https://www.adobe.com/br/products/livecycle/rightsmanagement/extension/downloads.html) para ver os requisitos de sistema para a extensão de segurança de documentos do Adobe para o Microsoft® Office.

### Exceções ao suporte ao cliente {#exceptions-to-client-support}

O Microsoft® Windows® 2012 não é suportado para todos os softwares especificados do lado do cliente, exceto Reader e Acrobat.

Além disso, o AEM Forms no JEE oferece suporte a atualizações, correções e pacotes de correções além da versão principal e secundária especificada do software suportado. No entanto, a atualização para a próxima versão principal ou secundária não é suportada, a menos que especificado.

## Política de suporte de patch de terceiros {#third-party-patch-support-policy}

Os requisitos de software de terceiros para o AEM Forms no JEE estão documentados na seção &quot;Requisitos do sistema&quot; de seus respectivos documentos de produto. Toda a documentação pode ser acessada em [https://adobe.com/go/learn_aemforms_documentation_64](https://adobe.com/go/learn_aemforms_documentation_64) .

As plataformas de referência de terceiros da AEM Forms no JEE indicam o nível de patch específico da infraestrutura de terceiros que estava atual durante o desenvolvimento e o lançamento do AEM Forms no JEE e a partir do nível mínimo de patch/service pack da infraestrutura compatível com essa versão do AEM Forms no JEE.

O Adobe oferece suporte a patches urgentes ou recomendados emitidos por fornecedores terceirizados após sua liberação, supondo que fornecedores terceirizados garantam compatibilidade retroativa com as versões compatíveis com o AEM Forms no JEE. O Adobe só oferecerá suporte a patches lançados após o nível mínimo de patch indicado na documentação AEM Forms no JEE.

Em alguns casos, o Adobe não oferece suporte a atualizações de terceiros que alteram funcionalidades importantes e, portanto, não oferecem suporte para compatibilidade com versões anteriores. Para obter detalhes sobre as atualizações compatíveis, consulte [Definições de patch compatíveis](https://helpx.adobe.com/aem-forms/aem-forms-third-party-software-patch.html) para produtos de fornecedor específicos e os tipos de patch suportados pelo Adobe.

Sob circunstâncias fora do controle do Adobe, os patches de terceiros que reivindicam compatibilidade com versões anteriores podem ter impacto negativo nos produtos do Adobe ou nos ambientes do cliente. Nesses casos, a Adobe recomenda que os clientes avaliem o impacto de qualquer patch urgente de terceiros antes de aplicá-los a sistemas críticos. A Adobe trabalhará com terceiros usando esforços comerciais razoáveis para resolver esses problemas, seja por meio de programas normais de suporte a Adobe ou por terceiros corrigindo o problema em seu patch. Isso não garante que um patch de terceiros recém-lançado que será suportado pelo Adobe funcione conforme documentado pelo fornecedor ou com o AEM Forms no JEE.

O Adobe reserva o direito de alterar as plataformas de referência de terceiros compatíveis com uma versão do AEM Forms no JEE e suas definições de patch compatíveis em qualquer ponto determinado.

Informações adicionais sobre patches de terceiros também podem ser encontradas pesquisando artigos da base de conhecimento relacionados ao seu produto no site de Suporte Adobe Enterprise.

[**Entre em contato com o suporte**](https://www.adobe.com/account/sign-in.supportportal.html)

## Histórico de revisão {#revision-history}


* 10 de outubro de 2021

   * Alterada a versão compatível do iOS para AEM Forms App para iOS 15.1. A versão anterior era iOS 12.