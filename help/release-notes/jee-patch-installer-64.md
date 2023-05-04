---
title: Instalador de patches do AEM Forms JEE
description: Instalador de patches do AEM Forms JEE
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
exl-id: ce5300ce-03f4-4e7b-bc5b-01a9968ebe06
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 23%

---

# Instalador de patches do AEM Forms JEE {#aem-forms-jee-patch-installer}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>[Entre em contato com o suporte](https://www.adobe.com/account/sign-in.supportportal.html) para mais informações ou para obter o sistema.

## Sobre o instalador de patches {#about-the-patch-installer}

O instalador de patches do Forms JEE AEM 6.4 inclui todos os problemas corrigidos de todos os componentes do Forms JEE AEM 6.4 disponíveis até o lançamento deste patch. Veja o mais recente  [Notas de versão do Cumulative Fix Pack](cfp-release-notes.md) para obter uma lista completa de problemas corrigidos.

## Pré-requisitos para instalar o patch {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## Instalação e configuração do patch {#installing-and-configuring-the-patch}

1. Faça um backup do &lt;*AEM_forms_root*>/implantar pasta. Isso é necessário caso você decida desinstalar a correção rápida.
1. Interrompa o servidor de aplicativos.
1. Extraia o arquivo do instalador de correção para o disco rígido.
1. No diretório nomeado de acordo com o seu sistema operacional:

   * **Windows**
Navegue até o diretório apropriado na mídia ou pasta de instalação do disco rígido onde você copiou o instalador e clique duas vezes no 
`aemforms64_cfp_install.exe` arquivo.

      * (Windows de 32 bits) `Windows\Disk1\InstData\VM`
      * (Windows de 64 bits) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris, AIX**
Navegue até o diretório apropriado e, a partir de um prompt de comando, digite 
`./aem64_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   Isso inicia um assistente de instalação que o guiará durante a instalação.

1. No painel de Introdução, clique em **[!UICONTROL Próximo]**.
1. Na tela Escolher pasta de instalação, verifique se o local padrão exibido está correto para a instalação existente ou clique em **[!UICONTROL Procurar]** para selecionar a pasta alternativa onde AEM formulários está instalado e clique em **[!UICONTROL Próximo]**.

1. Leia as informações no Resumo de correção rápida e clique em **[!UICONTROL Próximo]**.
1. Leia as informações no Resumo de pré-instalação e clique em **[!UICONTROL Instalar]**.
1. Quando a instalação estiver concluída, clique em **[!UICONTROL Próximo]**para aplicar as atualizações de correções rápidas aos arquivos instalados.
1. [Somente Windows] Execute uma das seguintes etapas:

   * Desmarque a opção Iniciar o Configuration Manager antes de clicar em Concluído. Execute o Configuration Manager posteriormente usando o `ConfigurationManager.bat` arquivo localizado em `[aem-forms root]\configurationManager\bin`. Usando `ConfigurationManager.bat` ajuda você a evitar a atualização manual do nome do axis.jar em arquivos .lax
   * Desmarque a opção Iniciar o Configuration Manager antes de clicar em Concluído. Antes de executar o gerenciador de configuração usando **ConfigurationManager.exe** ou **ConfigurationManager_IPv6.exe**, navegue até *&lt;aemforms_install_dir>\configurationManager\bin* diretório e atualização **axis.jar** para **axis-1.4.1.1.jar** nos seguintes arquivos:

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Somente baseado em Unix) A caixa de seleção Iniciar Gerenciador de Configuração é selecionada por padrão. Clique em **[!UICONTROL Concluído]** para executar o Gerenciador de configurações.

   Para executar o Gerenciador de configurações posteriormente, desmarque a opção Iniciar gerenciador de configurações antes de clicar em Concluído. Você pode iniciar o Configuration Manager posteriormente usando o script apropriado no `[AEM_forms_root]/configurationManager/bin` diretório.

1. Dependendo do servidor de aplicativos, escolha um dos seguintes documentos e siga as instruções em *Configuração e implantação de formulários AEM* seção.

   * [Instalação e implantação de formulários AEM para JBoss](http://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [Instalar e implantar formulários de AEM para o WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [Instalar e implantar formulários de AEM para o WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64)

1. (Somente JBoss) Após instalar o patch e configurar o servidor, exclua o tmp e os diretórios de trabalho do servidor de aplicativos JBoss.

## Configurações pós-implantação {#post-deployment-configurations}

### Configurações de SAML {#saml-configurations}

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
