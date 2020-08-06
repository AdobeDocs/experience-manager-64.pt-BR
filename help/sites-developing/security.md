---
title: Segurança
seo-title: Segurança
description: start de segurança do aplicativo durante a fase de desenvolvimento
seo-description: start de segurança do aplicativo durante a fase de desenvolvimento
uuid: efd5f3bc-da07-4fc8-a6ce-f1e6f5084c9e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: d2267663-6c1d-413c-9862-e82e21ae6906
translation-type: tm+mt
source-git-commit: 0fb4d181b700e223becfee8e3e68a84d6f964c1d
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# Segurança{#security}

start de segurança do aplicativo durante a fase de desenvolvimento. A Adobe recomenda aplicar as seguintes práticas recomendadas de segurança.

## Usar sessão de solicitação {#use-request-session}

Seguindo o princípio de privilégios mínimos, o Adobe recomenda que cada acesso ao repositório seja feito usando a sessão vinculada à solicitação do usuário e o controle de acesso adequado.

## Protect contra script entre sites (XSS) {#protect-against-cross-site-scripting-xss}

Scripts entre sites (XSS) permitem que os invasores injetem código em páginas da Web visualizadas por outros usuários. Essa vulnerabilidade de segurança pode ser explorada por usuários maliciosos da Web para ignorar controles de acesso.

AEM aplica o princípio de filtrar todo o conteúdo fornecido pelo usuário na saída. A prevenção do XSS é atribuída à prioridade mais alta durante o desenvolvimento e o teste.

O mecanismo de proteção XSS fornecido pela AEM se baseia na Biblioteca [Java](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) AntiSamy fornecida pela [OWASP (Open Aplicação web Security Project)](https://www.owasp.org/). A configuração padrão do AntiSamy pode ser encontrada em

`/libs/cq/xssprotection/config.xml`

É importante adaptar essa configuração às suas próprias necessidades de segurança sobrepondo o arquivo de configuração. A documentação [oficial do](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) AntiSamy fornecerá todas as informações necessárias para implementar seus requisitos de segurança.

>[!NOTE]
>
>Recomendamos que você sempre acesse a API de proteção XSS usando a [XSSAPI fornecida pela AEM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/xss/XSSAPI.html).

Além disso, um firewall de aplicativo da Web, como [mod_security para Apache](https://www.modsecurity.org), pode fornecer controle central e confiável sobre a segurança do ambiente de implantação e proteger contra ataques de script entre sites não detectados anteriormente.

## Acesso às informações do Cloud Service {#access-to-cloud-service-information}

>[!NOTE]
>
>As ACLs para as Informações do Cloud Service, bem como as configurações de OSGi necessárias para proteger sua instância, são automatizadas como parte do Modo [Pronto para](/help/sites-administering/production-ready.md)Produção. Embora isso signifique que você não precisa fazer as alterações de configuração manualmente, ainda é recomendável revisá-las antes de entrar em operação com sua implantação.

Ao [integrar sua instância de AEM com o Adobe Marketing Cloud](/help/sites-administering/marketing-cloud.md) , você usa configurações [de](/help/sites-developing/extending-cloud-config.md)Cloud Service. As informações sobre essas configurações, juntamente com quaisquer estatísticas coletadas, são armazenadas no repositório. Recomendamos que, se você estiver usando essa funcionalidade, verifique se a segurança padrão nessas informações corresponde aos seus requisitos.

O módulo webservicesupport grava estatísticas e informações de configuração em:

`/etc/cloudservices`

Com as permissões padrão:

* ambiente do autor: `read` for `contributors`

* Publicar ambiente: `read` for `everyone`

## Protect contra ataques de falsificação de solicitação entre sites {#protect-against-cross-site-request-forgery-attacks}

Para obter mais informações sobre os mecanismos de segurança AEM empregados para mitigar ataques CSRF, consulte a seção Filtro [de Quem indicou de](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) Sling da Lista de verificação de segurança e a documentação [do Quadro de proteção](/help/sites-developing/csrf-protection.md)CSRF.