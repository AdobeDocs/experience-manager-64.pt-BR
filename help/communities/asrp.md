---
title: ASRP - Provedor de Recursos de Armazenamento Adobe
seo-title: ASRP - Adobe Storage Resource Provider
description: Configurar o AEM Communities para usar um banco de dados relacional como armazenamento comum
seo-description: Set up AEM Communities to use a relational database as its common store
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
role: Admin
exl-id: 136c0913-c8b8-451d-bb28-3c3285c172a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---

# ASRP - Provedor de Recursos de Armazenamento Adobe {#asrp-adobe-storage-resource-provider}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Sobre o ASRP {#about-asrp}

Quando o AEM Communities é configurado para usar o ASRP como armazenamento comum, o conteúdo gerado pelo usuário (UGC) é acessível de todas as instâncias de autor e publicação sem a necessidade de sincronização nem replicação.

Consulte também [Características das opções de SRP](working-with-srp.md#characteristics-of-srp-options) e [Topologias recomendadas](topologies.md).

## Requisitos {#requirements}

É necessária uma licença adicional para a utilização do ASRP.

Para configurar seu site AEM Communities para usar o ASRP para UGC, entre em contato com seu representante de conta para:

* URL do centro de dados (endereço do ponto final ASRP)
* Chave do consumidor
* Chave secreta
* ID(s) de conjunto de relatórios

As chaves secretas e de consumidor são compartilhadas em todos os conjuntos de relatórios de uma empresa. Há um conjunto de relatórios por locatário.

## Configuração {#configuration}

### Selecionar ASRP {#select-asrp}

O [Console de configuração de armazenamento](srp-config.md) permite a seleção da configuração de armazenamento padrão, que identifica qual implementação do SRP usar.

**Sobre o autor**:

* Na navegação global: **[!UICONTROL Ferramentas > Comunidades > Configuração de armazenamento]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Selecionar **[!UICONTROL Fornecedor de Recursos de Armazenamento do Adobe (ASRP)]**
* As seguintes informações vêm do processo de provisionamento

   * **[!UICONTROL URL do centro de dados]**

      Puxe para baixo para selecionar o data center de produção identificado pelo seu representante de conta

   * **[!UICONTROL Report Suite padrão]**

      Insira o nome do conjunto de relatórios padrão

   * **[!UICONTROL Chave do consumidor]**

      Insira a chave do consumidor

   * **[!UICONTROL Segredo]**

      Inserir a chave secreta

* Selecione **[!UICONTROL Enviar]**

Prepare as instâncias de publicação:

* [Replicar a chave de criptografia](#replicate-the-crypto-key)
* [Replicar a configuração](#publishing-the-configuration)

Após enviar a configuração, teste a conexão:

* Selecionar **[!UICONTROL Testar configuração]**
para cada instância de criação e publicação, teste a conexão com o data center a partir do console Configuração de Armazenamento

* Por fim, verifique se os URLs do site para dados de perfil são roteáveis do data center por [externalização de links](#externalize-links).

### Replicar a chave de criptografia {#replicate-the-crypto-key}

A chave do consumidor e a chave secreta estão criptografadas. Para que as chaves sejam criptografadas/descriptografadas corretamente, a chave primária de criptografia do Granite deve ser a mesma em todas as instâncias AEM.

Siga as instruções em [Replicar a chave de criptografia](deploy-communities.md#replicate-the-crypto-key).

### Externalizar links {#externalize-links}

Para os links corretos de perfil e imagem de perfil, certifique-se de [Configurar o Link Externalizer](../../help/sites-developing/externalizer.md).

Certifique-se de definir os domínios como URLs roteáveis a partir do URL do data center (ponto de extremidade ASRP).

### Sincronização de Tempo {#time-synchronization}

Para que a autenticação com o ponto de extremidade ASRP tenha sucesso, as máquinas que executam seu AEM Communities hospedado devem ser sincronizadas no tempo, como com o [Protocolo de Hora da Rede (NTP)](https://www.ntp.org/).

### Publicar a configuração {#publishing-the-configuration}

O ASRP deve ser identificado como o armazenamento comum em todas as instâncias de autor e publicação.

Para disponibilizar a configuração idêntica no ambiente de publicação:

* **Sobre o autor**:

   * Navegar do menu principal para **[!UICONTROL Ferramentas > Operações > Replicação]**
   * Selecionar **[!UICONTROL Ativar árvore]**
   * **[!UICONTROL Caminho de início]**:

      * Navegue até `/etc/socialconfig/srpc/`
   * Desmarcar **[!UICONTROL Somente modificados]**
   * Selecionar **[!UICONTROL Ativar]**


## Atualização do AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Se você habilitar o ASRP em um site da comunidade publicado, qualquer UGC já armazenado em [JCR](jsrp.md) não estará mais visível, pois não há sincronização de dados entre o armazenamento local e o armazenamento na nuvem.

**`AEM Communities Extension`** O foi introduzido anteriormente no AEM 6.0 social communities as a cloud service. A partir AEM Comunidades 6.1, nenhuma configuração de nuvem é necessária, basta selecionar ASRP no [console de configuração de armazenamento](srp-config.md).

Devido à nova estrutura de armazenamento, é necessário seguir o [atualizar](upgrade.md#adobe-cloud-storage) instruções ao atualizar de comunidades sociais para comunidades.

## Gerenciar dados do usuário {#managing-user-data}

Para obter informações sobre *usuários*, *perfis de usuário* e *grupos de usuários*, normalmente inserido no ambiente de publicação, visite

* [Sincronização de usuários](sync.md)
* [Gerenciar usuários e grupos de usuários](users.md)

## Resolução de problemas {#troubleshooting}

### O UGC desaparece após a atualização {#ugc-disappears-after-upgrade}

Se estiver atualizando de um site existente da comunidade social do AEM 6.0, siga as [instruções de atualização](upgrade.md#adobe-cloud-storage), caso contrário, o UGC irá *appear* ser perdido.

### Erros de autenticação {#authentication-errors}

Se estiver recebendo erros de autenticação com o URL do data center e o AEM error.log contiver mensagens sobre carimbos de data e hora obsoletos, verifique se a sincronização de hora está acontecendo.

É recomendável usar uma ferramenta como [Protocolo de Hora da Rede (NTP)](https://www.ntp.org/) para sincronizar o tempo de todos os servidores de criação e publicação AEM.

### Novo conteúdo não aparece em pesquisas {#new-content-does-not-appear-in-searches}

A infraestrutura de armazenamento em nuvem Adobe usa *eventual consistência* para ajudar a atingir as metas de dimensionamento e desempenho. Por isso, o novo conteúdo não está disponível instantaneamente e pode levar vários segundos para aparecer nos resultados da pesquisa.

Embora o intervalo que afeta uma eventual consistência seja monitorado, entre em contato com o representante da conta, caso demore mais de alguns segundos para que o novo conteúdo apareça em pesquisas.

### UGC não visível no ASRP {#ugc-not-visible-in-asrp}

Verifique se o ASRP foi configurado para ser o provedor padrão, marcando a configuração da opção de armazenamento. Por padrão, o provedor de recursos de armazenamento é JSRP, não ASRP.

Em todas as instâncias de criação e publicação AEM, revise o console Configuração de armazenamento ou verifique o repositório AEM:

* No JCR, se [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Não contém um [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) , significa que o provedor de armazenamento é JSRP
   * Se o nó srpc existir e contiver nó [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration), as propriedades da configuração padrão devem definir o ASRP para ser o provedor padrão
