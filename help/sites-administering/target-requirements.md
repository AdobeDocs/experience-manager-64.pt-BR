---
title: Pré-requisitos para integração com a Adobe Target
seo-title: Pré-requisitos para integração com a Adobe Target
description: Descubra os pré-requisitos para integração com a Adobe Target.
seo-description: Descubra os pré-requisitos para integração com a Adobe Target.
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 3%

---


# Pré-requisitos para integração com a Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Como parte da [integração do AEM e do Adobe Target](/help/sites-administering/target.md), você precisa se registrar no Adobe Target, configurar o agente de replicação e as configurações de atividade segura no nó de publicação.

## Registrando-se no Adobe Target {#registering-with-adobe-target}

Para integrar AEM com a Adobe Target, é necessário ter uma conta Adobe Target válida. Esta conta deve ter no mínimo **aprovador **permissões de nível. Ao se registrar no Adobe Target, você recebe um código de cliente. Você precisa do código do cliente e do nome de login e senha da Adobe Target para se conectar AEM à Adobe Target.

O Código do cliente identifica a conta do cliente Adobe Target ao chamar o servidor Adobe Target.

>[!NOTE]
>
>Sua conta também deve ser ativada pela equipe do Público alvo para usar a integração.
>
>
>Se não for o caso, entre em contato com o Atendimento [ao cliente da](https://docs.adobe.com/content/help/en/target/using/cmp-resources-and-contact-information.html)Adobe Target.

## Ativação do Agente de Replicação de Públicos alvos {#enabling-the-target-replication-agent}

O agente [de](/help/sites-deploying/replication.md) replicação de teste e Público alvo deve estar habilitado na instância do autor. Observe que esse agente de replicação não estará habilitado por padrão se você tiver usado o modo de execução [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) para instalar o AEM. Para obter mais informações sobre como proteger seu ambiente de produção, consulte a Lista de verificação [de](/help/sites-administering/security-checklist.md)segurança.

1. No home page AEM, clique ou toque em **Ferramentas** > **Implantação** > **Replicação**.
1. Clique ou toque em **Agentes no autor**.
1. Clique ou toque no agente de replicação **Testar e Público alvo (teste e público alvo)** e, em seguida, clique ou toque em **Editar**.
1. Selecione a opção Ativado e clique ou toque em **OK**.

   >[!NOTE]
   >
   >Quando você configura o Test and Público alvo Replication Agent, na guia **Transport** , o URI é definido por padrão como **tnt:///**. Não substitua este URI por **https://admin.testandtarget.omniture.com**.
   >
   >Observe que se você tentar testar a conexão com **tnt:///**, ocorrerá um erro. Esse comportamento é esperado, pois esse URI é apenas para uso interno e não deve ser usado com o **Test Connection**.

## Como proteger o nó de configurações da Atividade {#securing-the-activity-settings-node}

You must secure the activity settings node **cq:ActivitySettings** on the publish instance so that it is inaccessible to normal users. O nó de configurações de atividade só deve estar acessível ao serviço que lida com a sincronização de atividades com o Adobe Target.

O nó **cq:ActivitySettings** está disponível na lista CRXDE em `/content/campaigns/*nameofbrand*`* *no nó jcr:content do atividade;* *por exemplo `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Esse nó só é criado depois que você público alvo um componente.

O nó **cq:ActivitySettings** na jcr:content da atividade é protegido pelas seguintes ACLs:

* Negar tudo para todos
* Permitir jcr:read,rep:write para &quot;público alvo-atividade-autores&quot; (o autor é um membro deste grupo fora da caixa)
* Permitir jcr:read,rep:write para &quot;targetservice&quot;

Essas configurações garantem que os usuários normais não tenham acesso às propriedades do nó. Use as mesmas ACLs no autor e na publicação. Consulte Administração e segurança [do](/help/sites-administering/security.md) usuário para obter mais informações.

## Configuração do AEM externalizador {#configuring-the-aem-externalizer}

Ao editar uma atividade no Adobe Target, o URL aponta para **localhost** , a menos que você altere o URL no nó do autor AEM.

Para configurar o AEM externalizador:

1. Navegue até o console da Web OSGi em **https://&lt;servidor>:&lt;porta>/system/console/configMgr.**
1. Localize o Externalizador **de links CQ de** dia e insira o domínio do nó do autor.

   ![chlimage_1-120](assets/chlimage_1-120.png)

