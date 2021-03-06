---
title: Configure o projeto Xcode e crie o aplicativo iOS
seo-title: Configure o projeto Xcode e crie o aplicativo iOS
description: Explica como criar um aplicativo AEM Forms padrão para iOS.
seo-description: Explica como criar um aplicativo AEM Forms padrão para iOS.
uuid: 33ccf014-05af-43c2-abb2-e0bd9c89ce32
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 2dec23f7-6cca-4cc9-a78a-acd23ae7da5f
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---


# Configure o projeto Xcode e crie o aplicativo iOS {#set-up-the-xcode-project-and-build-the-ios-app}

A AEM Forms fornece o código fonte completo do aplicativo AEM Forms. A fonte contém todos os componentes para criar aplicativos AEM Forms personalizados. O arquivo de código fonte `adobe-lc-mobileworkspace-src-<version>.zip` é uma parte do pacote `adobe-aemfd-forms-app-src-pkg-<version>.zip` em Distribuição de software.

Para obter a fonte do aplicativo AEM Forms, execute as seguintes etapas:

1. Abra [Distribuição de software](https://experience.adobe.com/downloads). Você precisa de uma Adobe ID para fazer logon na Software Distribution (Distribuição de software).
1. Toque em **[!UICONTROL Adobe Experience Manager]** disponível no menu de cabeçalho.
1. Na seção **[!UICONTROL Filtros]**:
   1. Selecione **[!UICONTROL Forms]** na lista suspensa **[!UICONTROL Solution]**.
   2. Selecione a versão e o tipo do pacote. Você também pode usar a opção **[!UICONTROL Pesquisar downloads]** para filtrar os resultados.
1. Toque no nome do pacote aplicável ao seu sistema operacional, selecione **[!UICONTROL Aceitar termos do EULA]** e toque em **[!UICONTROL Download]**.
1. Abra [Gerenciador de pacotes](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) e clique em **[!UICONTROL Carregar pacote]** para fazer upload do pacote.
1. Selecione o pacote e clique em **[!UICONTROL Instalar]**.

1. Para baixar o arquivo de código fonte, abra `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` no seu navegador.

   O pacote de origem é baixado em seu dispositivo.

A imagem a seguir exibe o conteúdo extraído de `adobe-lc-mobileworkspace-src-<version>.zip`.

![mws-content](assets/mws-content.png)

A tabela a seguir detalha o conteúdo da pasta `adobe-lc-mobileworkspace-src-[version]/ios`.

<table> 
 <tbody> 
  <tr> 
   <th><p>Diretório</p> </th> 
   <th><p>Conteúdo</p> </th> 
  </tr> 
  <tr> 
   <td><p><code>CordovaLib</code></p> </td> 
   <td><p>PhoneGap SDK 6.4.0</p> </td> 
  </tr> 
  <tr> 
   <td><p><code>AEM Forms</code></p> </td> 
   <td><p>Recursos, plug-ins PhoneGap e o módulo principal do aplicativo</p> </td> 
  </tr> 
  <tr> 
   <td><p><code>AEM Forms.xcodeproj</code></p> </td> 
   <td><p>Projeto Xcode para aplicativo AEM Forms</p> </td> 
  </tr> 
  <tr> 
   <td><p><code>www</code></p> </td> 
   <td><p>HTML, CSS, imagens e arquivos JavaScript para o projeto do aplicativo AEM Forms</p> </td> 
  </tr> 
 </tbody> 
</table>

Para obter informações detalhadas sobre a assinatura de código e a adição de dispositivos ao portal de provisionamento do iOS, consulte [Configuração, Processo e Solução de problemas de assinatura de código do iOS](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html).

## Criar aplicativo AEM Forms padrão {#set-up-the-xcode-project}

1. Execute as seguintes etapas para configurar um projeto no Xcode e fornecer uma identidade de assinatura:

   Faça logon em sua máquina Mac que tenha o Xcode e o SDK do iOS instalados e configurados.

1. Copie o arquivo `adobe-lc-mobileworkspace-src-<version>.zip` da pasta de downloads para `[*User_Home*]/Projects/`.
1. Extraia o arquivo no diretório `[*User_Home*]/Projects/[your-project]`.
1. Navegue até o diretório ` [*User_Home*]/Projects/ `[your-project]`/adobe-lc-mobileworkspace-src-[version]/ios`.
1. Abra o projeto `AEM Forms.xcodeproj` no Xcode.
1. Clique em **AEM Forms**, em **PÚBLICOS ALVOS**, selecione **AEM Forms**. Selecione a guia **Criar configurações**, localize a seção **Direito de assinatura de código** e, nos campos Depurar e liberar, execute um dos seguintes procedimentos:

   * Deixe os campos não especificados para criar um aplicativo padrão do Mobile Workspace
   * Especifique os campos como explicado em [Criar um aplicativo AEM Forms seguro para iOS](/help/forms/using/building-secure-mobile-workspace-app.md) para criar um aplicativo AEM Forms seguro.

1. Na guia **Build Settings**, clique em **Todos** e em **Combinado**.
1. Na lista **Settings**, expanda **Assinatura de código**.
1. Para **Identidade de assinatura de código**, selecione a assinatura apropriada. Para obter informações detalhadas sobre como criar novas assinaturas, consulte [Criando e Baixando Perfis de Provisionamento de Desenvolvimento](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html).
1. Certifique-se de que a mesma assinatura esteja selecionada para **Depurar**, **Versão** e **Qualquer SDK do iOS**.
1. Substitua o seguinte código no arquivo `AEM Forms-info.plist`:

   ```java
   <key>NSAppTransportSecurity</key>
   <dict>
   <key>NSAllowsArbitraryLoads</key>
   <true/>
   </dict>
   ```

   com o seguinte ao substituir `yourserver.com` por um nome de host apropriado para seu servidor.

   ```java
   <key>NSAppTransportSecurity</key>
   <dict>
   <key>NSExceptionDomains</key>
   <dict>
   <key>yourserver.com</key>
   <dict>
   <!-Include to allow subdomains->
   <key>NSIncludesSubdomains</key>
   <true/>
   <!-Include to allow HTTP requests->
   <key>NSTemporaryExceptionAllowsInsecureHTTPLoads</key>
   <true/>
   <!-Include to support forward secrecy->
   <key>NSExceptionRequiresForwardSecrecy</key>
   <false/>
   <!-Include to specify minimum TLS version->
   <key>NSTemporaryExceptionMinimumTLSVersion</key>
   <string>TLSv1.1</string>
   </dict>
   </dict>
   </dict>
   ```

   >[!NOTE]
   >
   >Esta etapa é necessária somente se o aplicativo AEM Forms precisar se conectar a um servidor que não siga os requisitos de segurança do App Transport.

1. Em **PROJECT**, selecione **AEM Forms** e certifique-se de que a assinatura apropriada está selecionada para **Identidade de assinatura de código**, **Depurar**, **Versão** e **Qualquer SDK do iOS**.
1. Conecte um iPad provisionado a uma máquina Mac.
1. Selecione o dispositivo provisionado para o projeto **AEM Forms**.

   ![ipad](assets/ipad.png)

   Um dispositivo provisionado, iPad Air 2, está selecionado.

1. Selecione **Produto** > **Limpar**.
1. Selecione **Produto** > **Compilação**.

## Crie o instalador para o aplicativo AEM Forms {#build-the-installer-for-the-mobile-workspace-app}

É necessário arquivar o projeto Xcode para criar o instalador (um arquivo .ipa) e um arquivo de lista de propriedade (um arquivo .plist). O arquivo de lista de propriedade contém informações de configuração do aplicativo interno hospedado, como o nome e o local de hospedagem do aplicativo. Para obter mais informações sobre o arquivo de lista de propriedade, consulte [Sobre arquivos de Lista de propriedades de informações](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Conecte um iPad provisionado a uma máquina Mac. Para obter informações detalhadas sobre o provisionamento de um iPad, consulte [Criação e Download de Perfis de Provisionamento de Desenvolvimento](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html)
1. Selecione o dispositivo provisionado para o projeto **AEM Forms**.

   ![ipad-1](assets/ipad-1.png)

   Um dispositivo provisionado, iPad Air 2, está selecionado.

1. Selecione **Produto** > **Limpar**.
1. Selecione **Produto** > **Compilação**.
1. Selecione **Produto** > **Arquivo**.
1. No Organizer - Arquivos, selecione o arquivo mais recente do seu projeto e clique em **Distribuir**.
1. Selecione **Salvar para Enterprise ou Implantação ad-hoc** como o método de distribuição e clique em **Próximo**.
1. Selecione a **Identidade de assinatura de código** apropriada e clique em **Próximo**. Clique em **Permitir** para aplicar a assinatura.
1. Forneça o nome do aplicativo e selecione **Salvar para Distribuição corporativa**.
1. Forneça o **URL do aplicativo** para o aplicativo. Por exemplo, para hospedar o aplicativo em um servidor CRX, forneça o URL `https://[*LC_host*]:[*port*]/lc/content/distribution/mobileworkspace/APP_NAME.ipa`.
1. No campo **Título**, especifique AEM Forms.
1. Clique em **Salvar** e feche o Xcode.

   Um arquivo instalador, `AEM Forms.ipa`, e um arquivo de lista de propriedade, `AEM Forms-info.plist`, são criados no local especificado.

1. Abra o arquivo `AEM Forms-info.plist` em um editor.
1. Substitua todos os espaços no URL do arquivo .ipa por %20.
1. Salve e feche o arquivo `AEM Forms-info.plist`.
