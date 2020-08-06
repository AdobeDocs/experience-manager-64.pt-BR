---
title: Configuração do SSL no Windows Vista
seo-title: Configuração do SSL no Windows Vista
description: Saiba como configurar o SSL no Windows Vista.
seo-description: Saiba como configurar o SSL no Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# Configuração do SSL no Windows Vista {#configuring-ssl-on-windows-vista}

Para configurar o SSL no Windows Vista™, você precisa de um certificado SSL com chaves RSA para autenticação. Você pode usar a ferramenta-chave Java para criar o certificado.

>[!NOTE]
>
>O Windows Vista não funcionará com chaves DSA.

Você pode executar keytool usando um único comando que inclui todas as informações necessárias para criar o certificado e o keystore.

**Criar um certificado SSL**

1. Em um prompt de comando, navegue até *[JAVA HOME]*/bin e digite o seguinte comando para criar o certificado e o keystore:

   `keytool -genkey -keyalg RSA -dname "CN=`*Nome *do Host Nome`, OU=`*Nome* da `, O=`*Empresa Nome *da`,L=`*Cidade*****Nome* Código do `, S=`*Estado ** Código do`, C=`** `" -alias`**`-keypass``*key*`**`-keystore`*País&quot;LC Cert&quot;**senhakeystorename* `.keystore`

   >[!NOTE]
   >
   >Substitua *[JAVA_HOME]pelo diretório onde o JDK está instalado e substitua o texto em itálico por valores que correspondam ao seu ambiente.*

1. Digite `changeit` como a senha. Essa senha é o padrão para uma instalação Java e o administrador do sistema pode tê-la alterado.

