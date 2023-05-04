---
title: Configurar ambiente para o aplicativo AEM Forms
seo-title: Set up environment for AEM Forms app
description: Hardware, software e licenças para criar e implantar o aplicativo AEM Forms.
seo-description: Hardware, software, and licenses to build and deploy the AEM Forms app.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
exl-id: 5c60d1a6-a4a2-4131-81e6-e39a5ab07dcf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 3%

---

# Configurar ambiente para o aplicativo AEM Forms {#set-up-environment-for-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você precisa do seguinte hardware, software e licenças para criar e implantar o aplicativo AEM Forms:

## Para dispositivos Windows {#for-windows-devices}

* Microsoft Windows 8.1 ou Windows 10
* Microsoft Visual Studio 2015
* Ferramentas do Microsoft Visual Studio para o Apache Cordova

## Para dispositivos iOS {#for-ios-devices}

* Apple Mac baseado na Intel executando o Mac OS X 10.9.5 ou superior
* iOS SDK 8.4 ou superior
* Versão Xcode: Xcode 6.4 para OS X ou superior
* Associação ao programa iOS Developer Enterprise
* Certificado empresarial para distribuição de aplicativos iOS internos
* Apple iPad com iOS 8.4 ou posterior

## Para dispositivos Android {#for-android-devices}

* Kit de ferramentas de desenvolvimento do Android (pacote ADT) que pode ser baixado de [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Se o ambiente estiver configurado em um sistema MAC, o ADT deverá ser instalado na pasta Aplicativos.
* Se o ADT estiver instalado em qualquer outro local no MAC, ou se o ambiente estiver configurado em um sistema Windows, o caminho do SDK do ADT precisará ser atualizado em `local.properties` arquivo disponível em `src\android` pasta no arquivo de origem extraído `mobileworkspace-src.zip`. Nesse arquivo, aponte a variável `sdk.dir` para o local do SDK do ADT no desktop.

>[!NOTE]
>
>O adobe-lc-mobileworkspace-src.zip contém PhoneGap SDK 5.0. Certifique-se de que o PhoneGap SDK não esteja pré-instalado.
