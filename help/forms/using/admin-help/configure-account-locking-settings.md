---
title: Definir configurações de bloqueio de conta
seo-title: Configure account-locking settings
description: Use a opção Ativar bloqueio de conta para bloquear contas de usuário após um número especificado de falhas consecutivas de autenticação.
seo-description: Use the Enable Account Locking option to lock user accounts after a specified number of consecutive authentication failures.
uuid: 5ff3fb76-8b11-4818-9a75-40ed8e121da5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d4409c6b-f4ef-499c-8daa-e93a163ff8ab
exl-id: e407c643-5753-447e-ad4e-deb7b9eb2b55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 7%

---

# Definir configurações de bloqueio de conta {#configure-account-locking-settings}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Ao adicionar um domínio, especifique se deseja ativar o bloqueio da conta. Quando a opção Habilitar bloqueio de conta é selecionada, as contas de usuário são bloqueadas após um número especificado de falhas consecutivas de autenticação. Após um período especificado, o usuário pode tentar autenticar novamente. Esse recurso impede que os usuários tentem várias combinações de credenciais para acessar o sistema.

Use as configurações na página Gerenciamento de Domínio para especificar o número máximo de falhas de autenticação e o período em que as contas são bloqueadas. Essas configurações se aplicam a todos os domínios que têm o bloqueio de conta ativado.

1. No console de administração, clique em **[!UICONTROL Configurações > Gerenciamento de usuários > Gerenciamento de domínios]**.
1. Na caixa Máximo de Falhas de Autenticação Consecutiva, digite o número de vezes consecutivas em que um usuário pode tentar fazer logon sem êxito antes que sua conta seja bloqueada. O valor padrão é 20.
1. Na caixa Desbloquear a conta após (minutos) , digite o número de minutos de bloqueio da conta do usuário. Após o número especificado de minutos, o usuário pode tentar fazer logon novamente. O valor padrão é 30.
1. Clique em **[!UICONTROL Salvar]**.
