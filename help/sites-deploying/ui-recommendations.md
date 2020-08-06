---
title: Interface do usuário Recommendations para clientes
seo-title: Interface do usuário Recommendations para clientes
description: 'Uma lista de recomendações relacionadas às interfaces do usuário clássica e otimizada ao toque. '
seo-description: 'Uma lista de recomendações relacionadas às interfaces do usuário clássica e otimizada ao toque. '
uuid: c661fb10-4dbc-4f8b-93be-3e77af1ad095
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 42bf42cb-0c6c-4390-8170-2c540c4d3ed3
translation-type: tm+mt
source-git-commit: b01e95110bffc1ee96e0814e782d716ed949c1b4
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# Interface do usuário Recommendations para clientes{#user-interface-recommendations-for-customers}

O Adobe Experience Manager 6.4 vem com duas interfaces de usuário - a interface de usuário unificada do Experience Cloud e a interface de usuário clássica.

Este documento tem como objetivo orientar os clientes para fazerem uma escolha sobre qual interface usar, dependendo de sua situação.

Termos de interesse:

* **Interface de usuário (ou interface de usuário padrão)Interface de usuário** moderna que foi introduzida na versão 5.6.0 como uma pré-visualização de tecnologia e estendida em versões subsequentes. Ele é baseado na experiência unificada do usuário para o Adobe Experience Cloud, anteriormente conhecida como interface habilitada para toque ou interface de usuário para toque.

* **Interface clássica do** usuário com base na tecnologia ExtJS que foi introduzida com o CQ 5.1 em 2008.

* **Recursos de administração** do site para gerenciar a hierarquia do site (mover, ativar, referências gerenciadas) e criar novas páginas.

* **Recursos de criação** de página para adicionar/editar o conteúdo de uma página.

* **DAM/Assets Admin** Capacidades para gerenciar ativos digitais (incluindo imagens, vídeo, documentos, downloads).

* **Recursos do ContextHub** para agregação de informações sobre o visitante e usá-lo para vários fins. Fornece uma interface de usuário para simular pessoas que visitam o site. A partir do AEM 6.2, o ContextHub substituiu a tecnologia anterior, o Client Context.

## Geral {#general}

Nos últimos anos, a Adobe atualizou todas as soluções da Adobe Experience Cloud com uma interface de usuário unificada. Os usuários nas soluções de Experience Cloud desfrutam de uma experiência consistente com padrões comuns sobre como usar e operar os aplicativos. Com cada versão, o Adobe refinou sua interface de usuário com base no feedback dos clientes que trabalham nas várias soluções.

A interface de usuário original para Adobe Experience Manager (anteriormente conhecida como CQ5), apresentada em 2008 e usada pelos clientes que executam as versões 5.0-5.6.1, está presente no AEM 6.4. Isso garante que os clientes possam atualizar para a versão 6.4 e se beneficiar de uma plataforma atualizada com novos recursos, além de continuar usando a mesma interface do usuário.

A Adobe recomenda que os clientes planejem mudar para a nova interface do usuário em 2018/19. Isso pode ser feito durante a atualização para o 6.4 - ou em projetos separados após a atualização, o que incluiria os ajustes necessários nas caixas de diálogo de personalizações e componentes.

O Adobe não planeja fazer mais aprimoramentos na interface clássica a partir do AEM 6.4. Observe que a interface do usuário clássica continua totalmente suportada enquanto está sendo descontinuada.

## Regras e Recommendations {#rules-and-recommendations}

Veja a seguir uma lista de recomendações do Gerenciamento de produtos para Adobe Experience Manager 6.4:

<table> 
 <tbody> 
  <tr> 
   <th>Meu projeto...</th> 
   <th>Recomendações</th> 
  </tr> 
  <tr> 
   <td>Está apenas começando a usar o Adobe Experience Manager.</td> 
   <td>Use a interface padrão.</td> 
  </tr> 
  <tr> 
   <td><p>Usou AEM há algum tempo.</p> <p>Utilizou a interface do produto pronta para uso e desenvolveu componentes personalizados para os sites.<br /> </p> </td> 
   <td> 
    <ol> 
     <li>Atualização para 6.4</li> 
     <li>Usar a interface padrão para administração do site, ativos, ... etc.<br /> </li> 
     <li>Configure a ação "Editar página" para abrir o Editor de página da interface clássica. See <a href="#selecting-your-ui">Selecting Your UI</a>.</li> 
    </ol> <p>Em seguida, numa segunda fase:</p> 
    <ol> 
     <li>Atualize as caixas de diálogo dos componentes para usar o formato de caixa de diálogo Coral 3. O Adobe recomenda usar a Ferramenta <a href="/help/sites-developing/dialog-conversion.md">de conversão de</a> caixa de diálogo para atualizar os componentes.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Criou um site que usa o ClientContext com integrações.<br /> </td> 
   <td> 
    <ol> 
     <li>Atualização para 6.4</li> 
     <li>Usar a interface padrão para administração do site, ativos, ... etc.</li> 
     <li>Configure a ação "Editar página" para abrir o Editor de página da interface clássica. See <a href="#selecting-your-ui">Selecting Your UI</a>.</li> 
    </ol> <p>Em seguida, numa segunda fase:</p> 
    <ol> 
     <li>Atualize as caixas de diálogo dos componentes para usar o formato de caixa de diálogo Coral 3. O Adobe recomenda usar a Ferramenta <a href="/help/sites-developing/dialog-conversion.md">de conversão de</a> caixa de diálogo para atualizar os componentes.</li> 
     <li>Configure o ContextHub (a substituição do ClientContext) e atualize os modelos de página para usar o ContextHub. Observe que o ContextHub tem um modo de compatibilidade que permite carregar ClientContexts personalizados.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><p>Usou CQ/AEM há muitos anos.</p> <p>Ampliou a interface do usuário do produto (por exemplo, Administrador do site) e criou componentes com diálogos de edição abrangentes.</p> </td> 
   <td><p>Atualize para a versão 6.4 e configure a interface clássica como padrão para a criação de página para todos os usuários. See <a href="#selecting-your-ui">Selecting Your UI</a>.</p> <p>Em seguida, start um projeto para aplicar a personalização e otimizar as caixas de diálogo de componentes no formato Coral 3. Consulte <a href="#resources-to-help">Recursos para obter ajuda</a>.<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Perguntas frequentes {#faq}

Consulte o artigo da Base de conhecimento, Perguntas frequentes [sobre criação de interfaces de](https://helpx.adobe.com/experience-manager/kb/index/touchui_faq.html)toque, para obter detalhes; incluindo quaisquer informações sobre o agendamento de desaprovação para a interface clássica.

## Selecting Your UI {#selecting-your-ui}

Consulte [Seleção da interface do usuário](/help/sites-authoring/select-ui.md) para obter informações sobre como configurar seu sistema, conforme necessário.

## Status da interface otimizada para toque {#touch-optimized-ui-status}

Para obter detalhes sobre os aprimoramentos feitos na interface otimizada ao toque no AEM 6.3, consulte [Novidades](/help/release-notes/release-notes.md#what-s-new) nas Notas de versão.

Uma visão geral completa consulte a página Status [do recurso da interface de](/help/release-notes/touch-ui-features-status.md) toque

## Recursos para Ajuda {#resources-to-help}

Para obter informações gerais sobre a manipulação básica:

* [Trabalhar com o ambiente](/help/sites-authoring/home.md)Author.
* [Criar páginas](/help/sites-authoring/author-environment-tools.md).

Para obter informações detalhadas sobre o desenvolvimento:

* [Arquitetura](/help/sites-developing/touch-ui-concepts.md)de interface otimizada ao toque.
* Use a ferramenta [Conversão de](/help/sites-developing/dialog-conversion.md) diálogo para converter as caixas de diálogo Editar do componente da interface clássica para a interface otimizada ao toque.

* [Estrutura da interface otimizada para toque](/help/sites-developing/touch-ui-structure.md).

* [Personalizar os consoles na interface de usuário](/help/sites-developing/customizing-consoles-touch.md) otimizada ao toque (inclui código de amostra).

* [Personalizar a criação de página na interface otimizada](/help/sites-developing/customizing-page-authoring-touch.md) ao toque (inclui código de amostra).

* [AEM Sessão Gem na personalização](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html)otimizada ao toque.
* [Documentação](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)da interface do usuário Granite.

