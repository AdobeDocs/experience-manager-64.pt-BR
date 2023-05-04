---
title: Quadro de proteção do QREF
seo-title: The CSRF Protection Framework
description: A estrutura usa tokens para garantir que a solicitação do cliente seja legítima
seo-description: The framework makes use of tokens to guarantee that the client request is legitimate
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
exl-id: 533c348e-517f-4d70-a89c-bfc87f71a633
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 3%

---

# Quadro de proteção do QREF{#the-csrf-protection-framework}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Além do Apache Sling Referrer Filter, o Adobe também fornece uma nova Estrutura de Proteção do CSRF para proteger contra esse tipo de ataque.

A estrutura usa tokens para garantir que a solicitação do cliente seja legítima. Os tokens são gerados quando o formulário é enviado ao cliente e validado quando o formulário é enviado de volta ao servidor.

>[!NOTE]
>
>Não há tokens nas instâncias de publicação para usuários anônimos.

## Requisitos {#requirements}

### Dependências {#dependencies}

Qualquer componente que dependa do `granite.jquery` a dependência se beneficiará automaticamente do CSRF Protection Framework. Se esse não for o caso de nenhum de seus componentes, você deve declarar uma dependência para `granite.csrf.standalone` antes de poder usar a estrutura.

### Replicação da chave de criptografia {#replicating-crypto-keys}

Para usar os tokens, é necessário replicá-los `/etc/keys/hmac` binário para todas as instâncias na implantação. Uma maneira conveniente de copiar a chave HMAC para todas as instâncias é criar um pacote contendo a chave e instalá-la por meio do Gerenciador de Pacotes em todas as instâncias.

>[!NOTE]
>
>Certifique-se também de [Alterações na configuração do Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) a fim de utilizar o Quadro de Proteção do QREF.

>[!NOTE]
>
>Se você usar o cache de manifesto com seu aplicativo da Web, adicione &quot;**&amp;ast;**&quot; ao manifesto para garantir que o token não coloque a chamada de geração de token CSRF offline. Para obter mais informações, consulte esta seção [link](https://www.w3.org/TR/offline-webapps/).
>
>Para obter mais informações sobre ataques de CSRF e maneiras de atenuá-los, consulte o [Página OWASP de falsificação de solicitação entre sites](https://owasp.org/www-community/attacks/csrf).
