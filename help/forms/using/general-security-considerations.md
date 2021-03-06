---
title: Considerações gerais de segurança para AEM Forms no JEE
seo-title: Considerações gerais de segurança para AEM Forms no JEE
description: Saiba como se preparar para endurecer seu AEM Forms no ambiente JEE.
seo-description: Saiba como se preparar para endurecer seu AEM Forms no ambiente JEE.
uuid: c5f6ffc7-b987-4541-ab60-e97b4ff5b2a4
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 38132225-ecae-4887-8f3d-0b3845059130
role: Admin
exl-id: cde40670-ce9d-4b96-92d3-9e56cb15bdce
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 1%

---

# Considerações gerais de segurança para AEM Forms no JEE {#general-security-considerations-for-aem-forms-on-jee}

Saiba como se preparar para endurecer seu AEM Forms no ambiente JEE.

Este artigo fornece informações introdutórias que ajudam você a se preparar para proteger seu ambiente AEM Forms. Ele inclui informações de pré-requisito sobre o AEM Forms no JEE, sistema operacional, servidor de aplicativos e segurança de banco de dados. Revise essas informações antes de continuar a bloquear seu ambiente.

## Informações de segurança específicas do fornecedor {#vendor-specific-security-information}

Esta seção contém informações relacionadas à segurança sobre sistemas operacionais, servidores de aplicativos e bancos de dados que são incorporadas à AEM Forms na solução JEE.

Use os links nesta seção para encontrar informações de segurança específicas do fornecedor para seu sistema operacional, banco de dados e servidor de aplicativos.

### Informações de segurança do sistema operacional {#operating-system-security-information}

Ao proteger seu sistema operacional, considere cuidadosamente a implementação das medidas descritas pelo fornecedor do sistema operacional, incluindo o seguinte:

* Definir e controlar usuários, atribuições e privilégios
* Monitorar logs e trilhas de auditoria
* Remoção de serviços e aplicativos desnecessários
* Backup de arquivos

Para obter informações de segurança sobre sistemas operacionais compatíveis com o AEM Forms no JEE, consulte os recursos na tabela:

<table> 
 <thead> 
  <tr> 
   <th><p>Sistema Operacional</p> </th> 
   <th><p>Recurso de segurança</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>IBM® AIX® 7.2</p> </td> 
   <td><p><a href="https://www.ibm.com/support/knowledgecenter/ssw_aix_72/com.ibm.aix.security/security-kickoff.htm" target="_blank">Benefícios de segurança do IBM AIX</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server® 2012 </p> </td> 
   <td><p><a href="https://blogs.technet.com/b/secguide/archive/2014/08/13/security-baselines-for-windows-8-1-windows-server-2012-r2-and-internet-explorer-11-final.aspx" target="_blank">Guia de segurança do Windows Server 2012</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server® 2016 </p> </td> 
   <td><p><a href="https://cloudblogs.microsoft.com/windowsserver/2017/08/22/now-available-windows-server-2016-security-guide/">Guia de segurança do Windows Server 2016</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat® Linux® AP ou ES</p> </td> 
   <td><p><a href="https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/pdf/security_guide/Red_Hat_Enterprise_Linux-7-Security_Guide-en-US.pdf" target="_blank">Guia de segurança Red Hat Enterprise Linux</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Sun Solaris 11</p> </td> 
   <td><p><a href="https://docs.oracle.com/cd/E53394_01/html/E54807/index.html" target="_blank">Diretrizes de segurança e proteção</a></p> </td> 
  </tr> 
  <tr> 
   <td>Oracle Linux® 7 Update 3</td> 
   <td><a href="https://docs.oracle.com/cd/E52668_01/E54670/E54670.pdf" target="_blank">Guia de segurança para a versão 7</a><br /> </td> 
  </tr> 
  <tr> 
   <td>CentOS 7<sup> </sup></td> 
   <td><a href="https://wiki.centos.org/HowTos/OS_Protection" target="_blank">Documentação de proteção</a></td> 
  </tr> 
 </tbody> 
</table>

### Informações de segurança do servidor de aplicativos {#application-server-security-information}

Ao proteger o servidor de aplicativos, considere cuidadosamente a implementação das medidas descritas pelo fornecedor do servidor, incluindo o seguinte:

* Uso de nome de usuário de administrador não óbvio
* Desativação de serviços desnecessários
* Proteção do gerenciador de console
* Ativação de cookies seguros
* Fechamento de portas desnecessárias
* Limitação de clientes por endereços IP ou domínios
* Uso do Gerenciador de segurança do Java™ para restringir de forma programática privilégios

Para obter informações de segurança sobre servidores de aplicativos compatíveis com o AEM Forms no JEE, consulte os recursos nesta tabela.

<table> 
 <thead> 
  <tr> 
   <th><p>Servidor de aplicativos</p> </th> 
   <th><p>Recurso de segurança</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Oracle WebLogic®</p> </td> 
   <td><p>Procure por Entendendo a segurança do WebLogic em <a href="https://download.oracle.com/docs/">https://download.oracle.com/docs/</a>.</p> </td> 
  </tr> 
  <tr> 
   <td><p>IBM WebSphere®</p> </td> 
   <td><p><a href="https://www.ibm.com/developerworks/websphere/zones/was/security/" target="_blank">Proteção de aplicativos e seu ambiente</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat® JBoss®</p> </td> 
   <td><p><a href="https://docs.jboss.org/author/display/AS7/Security+subsystem+configuration">Configuração do subsistema de segurança</a></p> </td> 
  </tr> 
 </tbody> 
</table>

### Informações de segurança do banco de dados {#database-security-information}

Ao proteger seu banco de dados, considere implementar as medidas descritas pelo fornecedor do banco de dados, incluindo o seguinte:

* Restrição de operações com listas de controle de acesso (ACLs)
* Uso de portas não padrão
* Ocultar o banco de dados por trás de um firewall
* Criptografar dados confidenciais antes de gravá-los no banco de dados (consulte a documentação do fabricante do banco de dados)

Para obter informações de segurança sobre bancos de dados compatíveis com o AEM Forms no JEE, consulte os recursos nesta tabela.

<table> 
 <thead> 
  <tr> 
   <th><p>Banco de dados</p> </th> 
   <th><p>Recurso de segurança</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>IBM DB2® 11.1</p> </td> 
   <td><p><a href="https://www-01.ibm.com/software/data/db2/library/">Biblioteca da família de produtos DB2</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td>Pesquise na Web por "SQL Server 2016: Segurança"</td> 
  </tr> 
  <tr> 
   <td><p>MySQL 5</p> </td> 
   <td><p><a href="https://dev.mysql.com/doc/refman/5.0/en/security.html">Problemas gerais de segurança do MySQL 5.0</a></p> <p><a href="https://dev.mysql.com/doc/refman/5.1/en/security.html">Problemas gerais de segurança do MySQL 5.1</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle® 12c</p> </td> 
   <td><p>Consulte o capítulo Segurança na documentação do <a href="https://docs.oracle.com/database/121/TDPSG/GUID-6E2F4E53-5D87-4FCD-9C9C-6792217D7014.htm#TDPSG94426" target="_blank">Oracle 12g</a></p> </td> 
  </tr> 
 </tbody> 
</table>

Esta tabela descreve as portas padrão que precisam ser abertas durante o processo de configuração do AEM Forms no JEE. Se estiver se conectando por https, ajuste as informações da porta e os endereços IP de acordo. Para obter mais informações sobre como configurar portas, consulte o documento *Instalando e Implantando AEM Forms no JEE* para seu servidor de aplicativos.

<table> 
 <thead> 
  <tr> 
   <th><p>Produto ou serviço</p> </th> 
   <th><p>Número da porta</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>JBoss</p> </td> 
   <td><p>8080</p> </td> 
  </tr> 
  <tr> 
   <td><p>WebLogic</p> </td> 
   <td><p>7001</p> </td> 
  </tr> 
  <tr> 
   <td><p>Servidor Gerenciado WebLogic</p> </td> 
   <td><p>Definir pelo administrador durante a configuração</p> </td> 
  </tr> 
  <tr> 
   <td><p>WebSphere</p> </td> 
   <td><p>9060, se a Segurança Global estiver ativada, o valor padrão da porta SSL será 9043.</p> <p>9080</p> </td> 
  </tr> 
  <tr> 
   <td><p>Servidor BAM</p> </td> 
   <td><p>7001</p> </td> 
  </tr> 
  <tr> 
   <td><p>SOAP</p> </td> 
   <td><p>8880</p> </td> 
  </tr> 
  <tr> 
   <td><p>MySQL</p> </td> 
   <td><p>3306</p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle</p> </td> 
   <td><p>1521</p> </td> 
  </tr> 
  <tr> 
   <td><p>DB2</p> </td> 
   <td><p>50000</p> </td> 
  </tr> 
  <tr> 
   <td><p>SQL Server</p> </td> 
   <td><p>1433</p> </td> 
  </tr> 
  <tr> 
   <td><p>LDAP</p> </td> 
   <td><p>A porta em que o servidor LDAP está sendo executado. Normalmente, a porta padrão é 389. No entanto, se você selecionar a opção SSL, a porta padrão normalmente é 636. Confirme com o administrador LDAP qual porta especificar.</p> </td> 
  </tr> 
 </tbody> 
</table>

### Configuração do JBoss para usar uma porta HTTP não padrão {#configuring-jboss-to-use-a-non-default-http-port}

O JBoss Application Server usa 8080 como a porta HTTP padrão. O JBoss também tem portas pré-configuradas 8180, 8280 e 8380, que são comentadas no arquivo jboss-service.xml. Se você tiver um aplicativo em seu computador que já use essa porta, altere a porta que o AEM Forms no JEE usa seguindo estas etapas:

1. Abra o seguinte arquivo para edição:

   Instalação de um único servidor: [Raiz JBoss]/standalone/configuration/standalone.xml

   Instalações de cluster: [Raiz JBoss]/domain/configuration/domain.xml

1. Altere o valor do atributo **port** na tag **&lt;socket-binding>** para um número de porta personalizado. Por exemplo, o seguinte usa a porta 8090:

   &lt;socket-binding name=&quot;http&quot; port=&quot;8090&quot; />

1. Salve e feche o arquivo.
1. Reinicie o servidor de aplicativos JBoss.

## AEM Forms em considerações de segurança do JEE {#aem-forms-on-jee-security-considerations}

Esta seção descreve alguns AEM Forms sobre problemas de segurança específicos de JEE que você deve conhecer.

### Credenciais de email não criptografadas no banco de dados {#email-credentials-not-encrypted-in-database}

As credenciais de email armazenadas pelos aplicativos não são criptografadas antes de serem armazenadas no AEM Forms no banco de dados JEE. Ao configurar um terminal de serviço para usar email, as informações de senha usadas como parte dessa configuração de ponto de extremidade não são criptografadas quando armazenadas no banco de dados.

### Conteúdo confidencial do Rights Management no banco de dados {#sensitive-content-for-rights-management-in-the-database}

O AEM Forms no JEE usa o banco de dados AEM Forms no JEE para armazenar informações confidenciais da chave de documento e outro material criptográfico usado para documentos de política. Proteger o banco de dados contra invasão ajuda a proteger essas informações confidenciais.

### Senha no formulário de texto limpo {#password-in-clear-text-format-in-adobe-ds-xml}

O servidor de aplicativos usado para executar o AEM Forms no JEE requer sua própria configuração para acessar seu banco de dados por meio de uma fonte de dados configurada no servidor de aplicativos. Certifique-se de que o servidor de aplicativos não exponha a senha do banco de dados em texto nítido em seu arquivo de configuração da fonte de dados.

O arquivo lc_[database].xml não deve conter senha no formato de texto limpo. Consulte o fornecedor do servidor de aplicativos sobre como criptografar essas senhas para o servidor de aplicativos.

>[!NOTE]
>
>O instalador turnkey do AEM Forms no JEE JBoss criptografa a senha do banco de dados.

O IBM WebSphere Application Server e o Oracle WebLogic Server podem criptografar senhas de fonte de dados por padrão. No entanto, confirme com a documentação do servidor de aplicativos para garantir que isso aconteça.

### Proteção da chave privada armazenada no Armazenamento de confiança {#protecting-the-private-key-stored-in-trust-store}

As chaves privadas ou credenciais importadas no Armazenamento de Confiança são armazenadas no AEM Forms no banco de dados JEE. Tome as precauções apropriadas para proteger o banco de dados e restringir o acesso somente a administradores designados.
