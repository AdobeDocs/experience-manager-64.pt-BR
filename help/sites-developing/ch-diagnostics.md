---
title: Diagnóstico do ContextHub
seo-title: Diagnóstico do ContextHub
description: O ContextHub fornece uma página de diagnósticos na qual você pode ver uma visão geral da estrutura do ContextHub
seo-description: O ContextHub fornece uma página de diagnósticos na qual você pode ver uma visão geral da estrutura do ContextHub
uuid: 94ef0696-3977-4781-ad32-9f4f117eb096
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6aa88583-5d34-4f77-a932-d47d84785eca
translation-type: tm+mt
source-git-commit: 39b6af8ee815e8f6fa6e0b4a0a6dc80f29165243
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Diagnóstico do ContextHub {#contexthub-diagnostics}

O ContextHub fornece uma página de diagnósticos na qual você pode ver uma visão geral da estrutura do ContextHub. Para abrir a página, vá para a página `contexthub.diagnostics.html` da instância do autor AEM, por exemplo:

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

A página Diagnóstico do ContextHub fornece informações sobre os armazenamentos e os módulos de interface do usuário que foram criados, as pastas da biblioteca do cliente que foram carregadas e os links para páginas úteis.

>[!NOTE]
>
>Para que as informações de diagnóstico sejam retornadas, o modo de depuração deve estar ativado, caso contrário, a página de diagnósticos ficará em branco. Consulte [este documento](/help/sites-administering/contexthub-config.md#debugging-contexthub) para obter detalhes sobre como ativar o modo de depuração.

>[!NOTE]
>
>Para configurações do ContextHub ainda localizadas sob seus caminhos herdados, o local da página de diagnósticos é `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Armazena {#stores}

A seção Lojas lista todos os armazenamentos do ContextHub que foram configurados. Cada item da lista consiste nas seguintes informações:

* **Título:** O tipo de  [loja em que a ](/help/sites-developing/ch-samplestores.md) loja se baseia.
* **path:** O caminho para o nó do repositório que armazena a configuração.
* **resourceType:** O caminho do nó do repositório no qual o tipo de armazenamento é definido.
* **clientlibs:** as categorias das bibliotecas clientes que são carregadas que implementam o tipo de armazenamento.

## Módulos {#modules}

A seção Módulos lista todos os módulos de interface do usuário do ContextHub que foram configurados. Cada item da lista consiste nas seguintes informações:

* **Título:** O tipo de módulo  [da interface ](/help/sites-developing/ch-samplemodules.md) em que o módulo da interface do usuário se baseia.
* **path:** O caminho para o nó do repositório que armazena a configuração.
* **resourceType:** O caminho do nó do repositório no qual o tipo de módulo da interface é definido.
* **clientlibs:** as categorias das bibliotecas clientes que são carregadas que implementam o tipo de módulo da interface do usuário.

## Clientlibs {#clientlibs}

A seção Clientlibs lista todas as pastas da biblioteca do cliente que o ContextHub carregou. As bibliotecas do cliente são categorizadas:

* **kernel.js:bibliotecas** clientes que implementam a estrutura do ContextHub, o mecanismo de segmento e os tipos de armazenamento.
* **ui.js:bibliotecas** de clientes que implementam os tipos de módulos de interface do usuário e interface do ContextHub.
* **style.css:arquivos** CSS carregados das bibliotecas do cliente.

## URLs {#urls}

A seção URLs contém links para os recursos do ContextHub:

* **Editor de configuração:** abre a página Configuração do  [ContextHub, ](/help/sites-administering/contexthub-config.md) onde você pode configurar lojas, modos de interface do usuário e módulos de interface do usuário.

* **Configuração dos módulos do ContextHub:** Abre o arquivo /etc/cloudsettings/default/contexthub.config.kernel.js, que contém a representação de objeto Javascript das configurações de armazenamento do ContextHub.
* **Configuração da interface do usuário do ContextHub:** Abre o arquivo /etc/cloudsettings/default/contexthub.config.ui.js, que contém a representação do objeto Javascript das configurações do modo da interface do usuário do ContextHub.
* **kernel.js:** abre o arquivo /etc/cloudsettings/default/contexthub.kernel.js, que contém o código fonte das bibliotecas clientes que implementam a estrutura do ContextHub, o mecanismo de segmento e os tipos de armazenamento.
* **ui.js:** abre o arquivo /etc/cloudsettings/default/contexthub.ui.js, que contém o código fonte das bibliotecas do cliente que implementam os tipos de módulo de interface do usuário e do ContextHub.
* **style.css:** abre o arquivo /etc/cloudsettings/default/contexthub.styles.css, que contém os estilos CSS para a interface do usuário e os módulos de interface do ContextHub.
