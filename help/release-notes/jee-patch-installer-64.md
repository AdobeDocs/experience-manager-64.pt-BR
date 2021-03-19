---
title: Instalador de patches do AEM Forms JEE
description: Instalador de patches do AEM Forms JEE
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 24%

---


# Instalador de patches do AEM Forms JEE {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Entre em contato com o ](https://www.adobe.com/account/sign-in.supportportal.html) Suporte para obter mais informações ou obter o patch.

## Sobre o instalador de patches {#about-the-patch-installer}

O instalador de patches do Forms JEE AEM 6.4 inclui todos os problemas corrigidos de todos os componentes do Forms JEE AEM 6.4 disponíveis até o lançamento deste patch. Consulte as [Notas de versão do Cumulative Fix Pack](cfp-release-notes.md) mais recentes para obter uma lista completa de problemas corrigidos.

## Pré-requisitos para instalar o patch {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## Instalar e configurar o patch {#installing-and-configuring-the-patch}

1. Faça um backup da pasta &lt;*AEM_forms_root*>/deploy. Isso é necessário caso você decida desinstalar a correção rápida.
1. Interrompa o servidor de aplicativos.
1. Extraia o arquivo do instalador de correção para o disco rígido.
1. No diretório nomeado de acordo com o seu sistema operacional:

   * **Windows**
Navegue até o diretório apropriado na mídia ou pasta de instalação do disco rígido onde você copiou o instalador e clique duas vezes no 
`aemforms64_cfp_install.exe` arquivo.

      * (Windows 32 bits) `Windows\Disk1\InstData\VM`
      * (Windows 64 bits) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris,**
AIXNavigate para o diretório apropriado e, a partir de um prompt de comando, digite 
`./aem64_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   Isso inicia um assistente de instalação que o guiará durante a instalação.

1. No painel de Introdução, clique em **[!UICONTROL Próximo]**.
1. Na tela Escolher pasta de instalação, verifique se o local padrão exibido está correto para a instalação existente ou clique em **[!UICONTROL Procurar]** para selecionar a pasta alternativa onde AEM formulários estão instalados e clique em **[!UICONTROL Avançar]**.

1. Leia as informações no Resumo de correção rápida e clique em **[!UICONTROL Próximo]**.
1. Leia as informações no Resumo de pré-instalação e clique em **[!UICONTROL Instalar]**.
1. Quando a instalação estiver concluída, clique em **[!UICONTROL Next]**para aplicar as atualizações de correções rápidas aos arquivos instalados.
1. [Windows ] apenasExecute uma das seguintes etapas:

   * Desmarque a opção Iniciar o Configuration Manager antes de clicar em Concluído. Execute o Configuration Manager posteriormente usando o arquivo `ConfigurationManager.bat` localizado em `[aem-forms root]\configurationManager\bin`. Usar `ConfigurationManager.bat` ajuda a evitar a atualização manual do nome do axis.jar em arquivos .lax
   * Desmarque a opção Iniciar o Configuration Manager antes de clicar em Concluído. Antes de executar o gerenciador de configuração usando **ConfigurationManager.exe** ou **ConfigurationManager_IPv6.exe**, navegue até o diretório *&lt;AEMForms_Install_Dir>\configurationManager\bin* e atualize **axis.jar** para **axis-1.4.1.1.1.1 .jar** nos seguintes arquivos:

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Somente baseado em Unix) A caixa de seleção Iniciar Gerenciador de Configuração é selecionada por padrão. Clique em **[!UICONTROL Concluído]** para executar o Gerenciador de configurações.

   Para executar o Gerenciador de configurações posteriormente, desmarque a opção Iniciar gerenciador de configurações antes de clicar em Concluído. Você pode iniciar o Configuration Manager posteriormente usando o script apropriado no diretório `[AEM_forms_root]/configurationManager/bin`.

1. Dependendo do servidor de aplicativos, escolha um dos seguintes documentos e siga as instruções na seção *Configuração e Implantação de formulários AEM*.

   * [Instalação e implantação de formulários AEM para JBoss](http://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [Instalar e implantar formulários de AEM para o WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [Instalar e implantar formulários de AEM para o WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64)

1. (Somente JBoss) Após instalar o patch e configurar o servidor, exclua o tmp e os diretórios de trabalho do servidor de aplicativos JBoss.

## Configurações pós-implantação {#post-deployment-configurations}

### Configurações SAML {#saml-configurations}

Se tiver a autenticação SAML configurada e enfrentado problemas com metadados IDP grandes, faça o seguinte após instalar o patch:

1. Defina a seguinte propriedade do sistema no servidor de aplicativos:\
   `um.saml.enable.large.xml=true`

1. Reinicie o servidor.
1. Exclua os provedores de autenticação SAML existentes e adicione-os novamente aos domínios existentes, conforme descrito nas configurações de SAML.

## Módulos afetados {#impacted-modules}

* Serviços de documento
* Segurança de documentos
* Foundation JEE
* Serviço PDFG

[Entre em contato com o suporte](https://www.adobe.com/account/sign-in.supportportal.html)
