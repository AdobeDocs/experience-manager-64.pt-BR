---
title: Configuração do SSL no Windows Vista
seo-title: Configuring SSL on Windows Vista
description: Saiba como configurar o SSL no Windows Vista.
seo-description: Learn how to configure SSL on Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 8eee2ed2-8263-47f2-b928-214fd9ab5f6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 4%

---

# Configuração do SSL no Windows Vista {#configuring-ssl-on-windows-vista}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Para configurar o SSL no Windows Vista™, você precisa de um certificado SSL com chaves RSA para autenticação. Você pode usar a ferramenta-chave Java para criar o certificado.

>[!NOTE]
>
>O Windows Vista não funcionará com chaves DSA.

Você pode executar keytool usando um único comando que inclui todas as informações necessárias para criar o certificado e o keystore.

**Criar um certificado SSL**

1. Em um prompt de comando, navegue até *[PÁGINA INICIAL DO JAVA]*/bin e digite o seguinte comando para criar o certificado e o armazenamento de chaves:

   `keytool -genkey -keyalg RSA -dname "CN=`*Nome do host* `, OU=`*Nome do grupo* `, O=`*Nome da empresa* `,L=`*Cidade*****Nome* `, S=`*Estado* `, C=`*Código do país* `" -alias`*&quot;Certificado LC&quot;* `-keypass` `*key*`*_**senha* `-keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >Substituir *[JAVA_HOME] com o diretório onde o JDK está instalado e substitua o texto em itálico por valores que correspondam ao seu ambiente.*

1. Tipo `changeit` como senha. Essa senha é o padrão para uma instalação Java, e o administrador do sistema pode tê-la alterado.
