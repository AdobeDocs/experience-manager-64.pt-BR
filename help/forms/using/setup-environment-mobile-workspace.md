---
title: Configurar ambiente para aplicativos AEM Forms
seo-title: Configurar ambiente para aplicativos AEM Forms
description: Hardware, software e licenças para criar e implantar o aplicativo AEM Forms.
seo-description: Hardware, software e licenças para criar e implantar o aplicativo AEM Forms.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# Configurar ambiente para aplicativos AEM Forms {#set-up-environment-for-aem-forms-app}

Você precisa do seguinte hardware, software e licenças para criar e implantar o aplicativo AEM Forms:

## Para dispositivos Windows {#for-windows-devices}

* Microsoft Windows 8.1 ou Windows 10
* Microsoft Visual Studio 2015
* Ferramentas do Microsoft Visual Studio para o Apache Cordova

## Para dispositivos iOS {#for-ios-devices}

* Apple Mac baseado em Intel executando Mac OS X 10.9.5 ou superior
* iOS SDK 8.4 ou superior
* Versão Xcode: Xcode 6.4 para OS X ou superior
* Associação ao programa corporativo para desenvolvedores iOS
* Certificado empresarial para distribuição de aplicativos iOS internos
* Apple iPad com iOS 8.4 ou posterior

## Para dispositivos Android {#for-android-devices}

* Android Development Toolkit (conjunto ADT) que pode ser baixado de [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Se o ambiente estiver configurado em um sistema MAC, o ADT deverá ser instalado na pasta Aplicativos.
* Se o ADT estiver instalado em qualquer outro local no MAC, ou se o ambiente estiver configurado em um sistema Windows, o caminho do SDK do ADT precisa ser atualizado no arquivo `local.properties` que está disponível na pasta `src\android` no arquivo de origem extraído `mobileworkspace-src.zip`. Neste arquivo, aponte a variável `sdk.dir` para o local do ADT SDK em sua área de trabalho.

>[!NOTE]
>
>O adobe-lc-mobileworkspace-src.zip contém o PhoneGap SDK 5.0. Certifique-se de que o SDK do PhoneGap não esteja pré-instalado.
