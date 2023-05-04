---
title: Gerenciar listas de revogação de certificado
seo-title: Managing certificate revocationlists
description: Saiba como gerenciar listas de revogação de certificados.
seo-description: Learn how to manage certificate revocation lists.
uuid: d8c4b64c-a273-4f5d-8b71-f6ea455c0f0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9744cc2d-5e6b-4341-9270-43d479bdca04
exl-id: 45741270-2d57-4d6d-92ef-65b6c1deb448
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 5%

---

# Gerenciar listas de revogação de certificado{#managing-certificate-revocationlists}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Usando o Gerenciamento de Armazenamento de Confiança, você pode importar, editar e excluir listas de revogação de certificados (CRLs). As listas de revogação de certificados codificadas em Base64 e DER são suportadas.

## Importar uma CRL {#import-a-crl}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Listas de revogação de certificados e, em seguida, clique em Importar.
1. Na caixa Alias , digite um identificador para a CRL.
1. Clique em Procurar para localizar a CRL e, em seguida, clique em OK.

## Exportar uma CRL {#export-a-crl}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Listas de revogação de certificados.
1. Clique no nome do alias da CRL a ser exportada e clique em Exportar.
1. Siga as instruções para exportar a CRL. As CRLs são exportadas na codificação Base64.
1. Clique em OK.

## Excluir uma CRL {#delete-a-crl}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Listas de revogação de certificados.
1. Marque as caixas de seleção das CRLs a serem excluídas, clique em Excluir e em OK.
