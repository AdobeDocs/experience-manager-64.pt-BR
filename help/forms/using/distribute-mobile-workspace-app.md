---
title: Distribuir aplicativo AEM Forms
seo-title: Distribute AEM Forms app
description: Use o Gerenciamento de dispositivos móveis (MDM) para a implantação em grande escala de aplicativos em dispositivos móveis.
seo-description: Use Mobile Device Management (MDM) for the large-scale deployment of apps on mobile devices.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
exl-id: c1bf0a0e-70f7-41dd-8b1a-c114d89a265b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 2%

---

# Distribuir aplicativo AEM Forms {#distribute-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Gerenciamento de dispositivos móveis (MDM) permite a implantação em grande escala de aplicativos em dispositivos móveis.

>[!NOTE]
>
>Essa distribuição é aplicável somente para dispositivos iOS e Android.

## Principais recursos geralmente fornecidos pelas soluções MDM: {#main-features-generally-provided-by-mdm-solutions}

* Ativar a inscrição de dispositivos no ambiente empresarial
* Permitir a configuração e a atualização das definições do dispositivo
* Impor conformidade com a segurança.
* Acesso móvel seguro aos recursos corporativos

Uma solução MDM juntamente com o Gerenciamento de aplicativos móveis permite gerenciar aplicativos internos, públicos e comprados em todos os dispositivos móveis da empresa.

O administrador do MDM pode fazer upload de arquivos ipa e apk para o servidor MDM e controlar os usuários que podem acessar os arquivos ipa ou apk. O administrador também pode controlar a configuração de perfil correspondente a cada aplicativo.

## Configurações de perfil que afetam o aplicativo AEM Forms {#profile-settings-affecting-the-aem-forms-app-br}

As seguintes configurações de Perfil no seu dispositivo afetarão o funcionamento do aplicativo AEM Forms no seu dispositivo:

* **Permitir a utilização da câmara** no **Funcionalidade do dispositivo** seção

Se você desativar **Permitir a utilização da câmara**, o recurso de câmera do [Anotação de fotos](/help/forms/using/add-attachments.md) não funcionará. Você precisa ativar esta opção para usar a câmera no aplicativo.

* **Exigir senha no dispositivo** na seção Políticas de código

Para ativar **criptografia de dados de aplicativos**, é recomendável ativar a variável **passcode** no seu dispositivo. Se a senha não estiver definida no dispositivo, os dados do aplicativo armazenados no dispositivo não serão criptografados.
