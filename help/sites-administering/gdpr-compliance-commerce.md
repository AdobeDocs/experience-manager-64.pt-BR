---
title: Comércio AEM - Prontidão para o RGPD
seo-title: Comércio AEM - Prontidão para o RGPD
description: 'null'
seo-description: 'null'
uuid: 7ca26587-8cce-4c75-8629-e0e5cfb8166c
contentOwner: carlino
discoiquuid: c637964a-dfcb-41fe-9c92-934620fe2cb3
translation-type: tm+mt
source-git-commit: 0db56cb77628b3e81b69382a314c30b43887bde6
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---


# Comércio AEM - Prontidão para o RGPD{#aem-commerce-gdpr-readiness}

>[!IMPORTANT]
>
>O RGPD é utilizado como exemplo nas seções abaixo, mas os detalhes abrangidos são aplicáveis a todas as normas de proteção de dados e privacidade; como o RGPD, o CCPA, etc.

O Regulamento Geral da Proteção de Dados da União sobre os direitos de privacidade dos dados entra em vigor em maio de 2018. Para obter mais informações, consulte a página do [RGPD no Centro](https://www.adobe.com/privacy/general-data-protection-regulation.html)de privacidade do Adobe.

>[!NOTE]
>
>Consulte [AEM Prontidão](/help/managing/data-protection-and-privacy.md) do RGPD para obter mais detalhes.

![screen_shot_2018-03-22at111606](assets/screen_shot_2018-03-22at111606.jpg)

Em nossas integrações de Comércio prontas para uso, AEM é a camada de experiência, consumindo serviços e enviando dados de volta para a plataforma de comércio do cliente que é executada em um modo sem cabeçalho.

Para algumas plataformas de comércio, armazenamos informações de perfis ( `/home/users`) e tokens de comércio (para fazer logon na plataforma de comércio) no AEM. Para estes casos de uso, leia [Manuseio de solicitações do RGPD para a plataforma](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md)AEM.

![screen_shot_2018-03-22at111621](assets/screen_shot_2018-03-22at111621.jpg)

## Tratamento de solicitações de RGPD para comércio AEM {#handling-gdpr-requests-for-aem-commerce}

Para a integração com o Commerce Cloud Salesforces, o AEM Commerce não armazena informações relevantes do RGPD. Você deve encaminhar a solicitação para a [Salesforce Cloud](https://documentation.demandware.com/).

Para as integrações hybris e IBM WebSphere, há alguns dados em AEM. Você deve usar as instruções [do RGPD da plataforma](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md) AEM e considerar estas questões:

1. **Onde meus dados são armazenados/usados?** As informações de perfil do usuário em cache, como nome, identificador do usuário de comércio, token, senha, dados de endereço e assim por diante, são exibidas AEM.
1. **Com quem compartilho os dados do RGPD cobertos?** Qualquer atualização dos dados relevantes do RGPD no AEM Commerce não é armazenada (exceto as informações relevantes do perfil, como mencionado acima), mas é enviada de volta à plataforma de comércio.
1. **Como excluir meus dados** do usuário? Exclua o perfil do usuário no AEM e chame a exclusão do usuário na plataforma de comércio.

>[!NOTE]
>
>Consulte o wiki [hybris](https://wiki.hybris.com/) ou a documentação [de Comércio](https://www-01.ibm.com/support/docview.wss?uid=swg27036450) Webphere, se necessário.

