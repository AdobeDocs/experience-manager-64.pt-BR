---
title: Reconhecimento de certificados válidos e expirados em documentos PDF
seo-title: Recognizing valid and expired certificates in PDF documents
description: Saiba como reconhecer certificados válidos e expirados em documentos PDF.
seo-description: Learn how to recognize valid and expired certificates in PDF documents.
uuid: ceeff57a-586f-4f7b-852f-2a637f003d7e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4559218a-65ba-4577-ad26-7721e28971bc
exl-id: 6e2c109c-381f-455d-bd1d-b08c37c0bd67
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 3%

---

# Reconhecimento de certificados válidos e expirados em documentos PDF {#recognizing-valid-and-expired-certificates-in-pdf-documents}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Quando um documento do PDF com direitos de uso aplicados por extensões Reader for aberto no Adobe Reader, uma barra de status será exibida descrevendo os direitos de uso específicos ativados no documento PDF.

Quando o certificado digital que especifica os direitos de uso de um documento PDF expira e o documento PDF é aberto no Adobe Reader, uma caixa de diálogo é exibida avisando ao usuário que o documento PDF tem direitos de uso, mas esses direitos são desativados. Embora a mensagem indique que o documento PDF foi alterado ou adulterado, isso não é necessariamente o caso. O Adobe Reader exibe essa mensagem quando um certificado expira ou um documento é modificado. No Adobe Reader 7.0.x ou posterior, não é possível determinar qual caso é o problema no momento.

Após fechar a caixa de diálogo, o Adobe Reader abre o documento PDF. Os direitos de uso que foram aplicados usando extensões do Acrobat Reader DC não estão disponíveis, conforme esperado. Se o documento PDF for um formulário interativo, os campos do formulário serão bloqueados e o usuário não poderá alterar os dados do formulário.
