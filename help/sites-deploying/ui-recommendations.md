---
title: Recommendations da interface do usuário para clientes
seo-title: User Interface Recommendations for Customers
description: Uma lista de recomendações relacionadas às interfaces do usuário clássica e otimizada para toque.
seo-description: A list of recommendations related to the classic and touch-optimized user interfaces.
uuid: c661fb10-4dbc-4f8b-93be-3e77af1ad095
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 42bf42cb-0c6c-4390-8170-2c540c4d3ed3
exl-id: 1e5172d9-47a3-4d73-b749-166e201f4eef
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 1%

---

# Recommendations da interface do usuário para clientes{#user-interface-recommendations-for-customers}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Adobe Experience Manager 6.4 vem com duas interfaces de usuário - a interface de usuário unificada do Experience Cloud e a interface de usuário clássica.

Este documento tem como objetivo orientar os clientes para fazerem uma escolha sobre qual interface usar, dependendo de sua situação.

Termos de interesse:

* **Interface do usuário (ou interface padrão)**
Interface do usuário moderna que foi introduzida na versão 5.6.0 como uma visualização de tecnologia e estendida em versões subsequentes. É baseado na experiência unificada do usuário para o Adobe Experience Cloud, anteriormente conhecida como interface habilitada para toque ou interface do usuário para toque.

* **Interface clássica**
Interface do usuário baseada na tecnologia ExtJS que foi introduzida com o CQ 5.1 em 2008.

* **Administrador do site**
Recursos para gerenciar a hierarquia do site (mover, ativar, referências gerenciadas) e criar novas páginas.

* **Criação de página**
Recursos para adicionar/editar o conteúdo de uma página.

* **Administrador de DAM/Ativos**
Recursos para gerenciar ativos digitais (incluindo imagens, vídeo, documentos, downloads).

* **ContextHub**
Recursos para agregar informações sobre o visitante e usá-las para vários fins. Fornece uma interface de usuário para simular pessoas que visitam o site. A partir do AEM 6.2, o ContextHub substituiu a tecnologia anterior, o ClientContext.

## Geral {#general}

Nos últimos anos, o Adobe atualizou todas as soluções da Adobe Experience Cloud com uma interface de usuário unificada. Os usuários nas soluções Experience Cloud desfrutam de uma experiência consistente com padrões comuns sobre como usar e operar os aplicativos. Com cada versão, o Adobe refinou a interface do usuário com base no feedback dos clientes que trabalham nas várias soluções.

A interface de usuário original do Adobe Experience Manager (anteriormente conhecida como CQ5), introduzida em 2008 e usada por clientes que executam as versões 5.0-5.6.1, está presente no AEM 6.4. Isso garante que os clientes possam atualizar para o 6.4 e se beneficiar de uma plataforma atualizada com novos recursos, além de continuar usando a mesma interface do usuário.

O Adobe recomenda que os clientes planejem mudar para a nova interface do usuário em 2018/19. Isso pode ser feito durante a atualização para o 6.4 ou em projetos separados após a atualização, o que incluiria os ajustes necessários nas caixas de diálogo de personalizações e componentes.

O Adobe não planeja fazer aprimoramentos adicionais à interface clássica a partir do AEM 6.4. Observe que a interface do usuário clássica permanece totalmente compatível enquanto está obsoleta.

## Regras e Recommendations {#rules-and-recommendations}

Veja a seguir uma lista de recomendações do Gerenciamento de produto para o Adobe Experience Manager 6.4:

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
   <td><p>Usa AEM há algum tempo.</p> <p>Usou a interface do usuário do produto pronta para uso e desenvolveu componentes personalizados para os sites.<br /> </p> </td> 
   <td> 
    <ol> 
     <li>Atualização para 6.4</li> 
     <li>Use a interface de usuário padrão para administração de sites, ativos, . etc.<br /> </li> 
     <li>Configure a ação "Editar página" para abrir o Editor de página da interface clássica. Consulte <a href="#selecting-your-ui">Selecionar sua interface do usuário</a>.</li> 
    </ol> <p>Em seguida, em uma segunda fase:</p> 
    <ol> 
     <li>Atualize suas caixas de diálogo de componentes para usar o formato de diálogo Coral 3. O Adobe recomenda usar a variável <a href="/help/sites-developing/modernization-tools.md">Ferramentas de Modernização AEM</a> para atualizar os componentes.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Criou um site que usa o ClientContext com integrações.<br /> </td> 
   <td> 
    <ol> 
     <li>Atualização para 6.4</li> 
     <li>Use a interface de usuário padrão para administração de sites, ativos, . etc.</li> 
     <li>Configure a ação "Editar página" para abrir o Editor de página da interface clássica. Consulte <a href="#selecting-your-ui">Selecionar sua interface do usuário</a>.</li> 
    </ol> <p>Em seguida, em uma segunda fase:</p> 
    <ol> 
     <li>Atualize suas caixas de diálogo de componentes para usar o formato de diálogo Coral 3. O Adobe recomenda usar a variável <a href="/help/sites-developing/modernization-tools.md">Ferramentas de Modernização AEM</a> para atualizar os componentes.</li> 
     <li>Configure o ContextHub (a substituição do ClientContext) e atualize os modelos de página para usar o ContextHub. Observe que o ContextHub tem um modo de compatibilidade que permite carregar ClientContexts personalizados.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><p>Usa CQ/AEM há muitos anos.</p> <p>Estendeu a interface do usuário do produto (por exemplo, o Administrador do site) e criou componentes com caixas de diálogo de edição abrangentes.</p> </td> 
   <td><p>Atualize para 6.4 e configure a interface clássica como padrão para a criação de página para todos os usuários. Consulte <a href="#selecting-your-ui">Selecionar sua interface do usuário</a>.</p> <p>Em seguida, inicie um projeto para aplicar personalização e otimizar caixas de diálogo de componentes no formato Coral 3. Consulte <a href="#resources-to-help">Recursos para Ajuda</a>.<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Perguntas frequentes {#faq}

Consulte o artigo da Base de conhecimento , [Perguntas frequentes sobre criação na interface de toque](https://helpx.adobe.com/experience-manager/kb/index/touchui_faq.html), para mais pormenores; incluindo quaisquer informações sobre o agendamento de descontinuação da interface clássica.

## Selecionar sua interface do usuário {#selecting-your-ui}

Consulte [Selecionar sua interface do usuário](/help/sites-authoring/select-ui.md) para obter informações sobre como configurar seu sistema, conforme necessário.

## Status da interface otimizada para toque {#touch-optimized-ui-status}

Para obter detalhes sobre as melhorias feitas na interface otimizada para toque no AEM 6.3, consulte [Novidades](/help/release-notes/release-notes.md#what-s-new) nas Notas de versão.

Uma visão geral completa do [Status do recurso da interface de toque](/help/release-notes/touch-ui-features-status.md) página

## Recursos para Ajuda {#resources-to-help}

Para informações de base sobre manipulação básica:

* [Trabalhar com o ambiente Autor](/help/sites-authoring/home.md).
* [Criação de páginas](/help/sites-authoring/author-environment-tools.md).

Para informações detalhadas sobre desenvolvimento:

* [Arquitetura da interface otimizada para toque](/help/sites-developing/touch-ui-concepts.md).
* Use o [Ferramentas de Modernização AEM](/help/sites-developing/modernization-tools.md) para converter caixas de diálogo de edição de componentes da interface clássica para a interface otimizada para toque.

* [Estrutura da interface otimizada para toque](/help/sites-developing/touch-ui-structure.md).

* [Personalização dos consoles na interface otimizada para toque](/help/sites-developing/customizing-consoles-touch.md) (inclui código de amostra).

* [Personalização da criação de página na interface otimizada para toque](/help/sites-developing/customizing-page-authoring-touch.md) (inclui código de amostra).

* [Documentação da interface do usuário do Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html).
