---
title: Diagnósticos do ContextHub
seo-title: ContextHub Diagnostics
description: O ContextHub fornece uma página de diagnósticos onde você pode ver uma visão geral da estrutura do ContextHub
seo-description: ContextHub provides a diagnostics page where you can see an overview of the ContextHub framework
uuid: 94ef0696-3977-4781-ad32-9f4f117eb096
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6aa88583-5d34-4f77-a932-d47d84785eca
exl-id: 31926737-1a06-4fb9-b851-665095954875
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 2%

---

# Diagnósticos do ContextHub {#contexthub-diagnostics}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O ContextHub fornece uma página de diagnósticos, onde você pode ver uma visão geral da estrutura do ContextHub. Para abrir a página, vá para o `contexthub.diagnostics.html` página da instância do autor do AEM, por exemplo:

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

A página Diagnósticos do ContextHub fornece informações sobre as lojas e os módulos de interface do usuário que foram criados, as pastas da biblioteca do cliente que são carregadas e os links para páginas úteis.

>[!NOTE]
>
>Para que as informações de diagnóstico sejam retornadas, o modo de depuração deve estar ativado, caso contrário, a página de diagnósticos estará em branco. Consulte [este documento](/help/sites-administering/contexthub-config.md#debugging-contexthub) para obter detalhes sobre como habilitar o modo de depuração.

>[!NOTE]
>
>Para configurações do ContextHub ainda localizadas em seus caminhos herdados, o local da página de diagnósticos é `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Lojas {#stores}

A seção Lojas lista todos os armazenamentos do ContextHub que foram configurados. Cada item da lista consiste nas seguintes informações:

* **Título:** O [tipo de armazenamento](/help/sites-developing/ch-samplestores.md) na qual a loja se baseia.
* **caminho:** O caminho para o nó do repositório que contém a configuração.
* **resourceType:** O caminho do nó do repositório no qual o tipo de armazenamento é definido.
* **clientlibs:** As categorias das bibliotecas de clientes que são carregadas que implementam o tipo de loja.

## Módulos {#modules}

A seção Módulos lista todos os módulos de interface do usuário do ContextHub que foram configurados. Cada item da lista consiste nas seguintes informações:

* **Título:** O [Tipo de módulo da interface do usuário](/help/sites-developing/ch-samplemodules.md) que o módulo da interface do usuário se baseia em.
* **caminho:** O caminho para o nó do repositório que contém a configuração.
* **resourceType:** O caminho do nó do repositório no qual o tipo de módulo da interface do usuário é definido.
* **clientlibs:** As categorias das bibliotecas de clientes que são carregadas que implementam o tipo de módulo da interface do usuário.

## Clientlibs {#clientlibs}

A seção Clientlibs lista todas as pastas da biblioteca do cliente que o ContextHub carregou. As bibliotecas de clientes são categorizadas:

* **kernel.js:** Bibliotecas de clientes que implementam a estrutura do ContextHub, o mecanismo de segmento e os tipos de armazenamento.
* **ui.js:** Bibliotecas de clientes que implementam a interface do usuário e os tipos de módulo da interface do usuário do ContextHub.
* **style.css:** Arquivos CSS carregados de bibliotecas de clientes.

## URLs {#urls}

A seção URLs contém links para os recursos do ContextHub:

* **Editor de configuração:** Abre a variável [Página Configuração do ContextHub](/help/sites-administering/contexthub-config.md) onde você pode configurar armazenamentos, modos de interface do usuário e módulos de interface do usuário.

* **Configuração dos módulos do ContextHub:** Abre o arquivo /etc/cloudsettings/default/contexthub.config.kernel.js, que contém a representação de objeto Javascript das configurações de armazenamento ContextHub.
* **Configuração da interface do usuário do ContextHub:** Abre o arquivo /etc/cloudsettings/default/contexthub.config.ui.js, que contém a representação do objeto Javascript das configurações do modo de interface do usuário do ContextHub.
* **kernel.js:** Abre o arquivo /etc/cloudsettings/default/contexthub.kernel.js, que contém o código-fonte das bibliotecas de clientes que implementam a estrutura do ContextHub, o mecanismo de segmento e os tipos de armazenamento.
* **ui.js:** Abre o arquivo /etc/cloudsettings/default/contexthub.ui.js, que contém o código fonte das bibliotecas do cliente que implementam a interface do usuário e os tipos de módulo da interface do usuário do ContextHub.
* **style.css:** Abre o arquivo /etc/cloudsettings/default/contexthub.styles.css, que contém os estilos de CSS dos módulos de interface do usuário e do ContextHub.
