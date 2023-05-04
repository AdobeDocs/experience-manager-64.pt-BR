---
title: Status do recurso da interface de toque
seo-title: Touch UI Feature Status
description: Notas de versão específicas da interface do usuário para toque do Adobe Experience Manager 6.3.
seo-description: Release notes specific to Adobe Experience Manager 6.3 Touch UI.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
exl-id: e1422581-143b-4fce-976e-e5aa3360e2d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 15%

---

# Status do recurso da interface de toque {#touch-ui-feature-status}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Com a versão 6.4 do AEM, a variável [A interface do usuário clássica está obsoleta](/help/release-notes/deprecated-removed-features.md). O Adobe não planeja fazer aprimoramentos adicionais à interface clássica e os usuários são incentivados a aproveitar os novos recursos avançados disponíveis na interface habilitada para toque.

A partir da versão 6.0, o AEM introduziu uma nova interface de usuário chamada de &quot;interface habilitada para toque&quot; (também conhecida como &quot;interface de toque&quot;) que é alinhada à Adobe Marketing Cloud e às diretrizes gerais da interface do usuário do Adobe. Com quase a partição de recursos atingida, essa se tornou a interface padrão em AEM com a interface herdada orientada para desktop, chamada de &quot;interface clássica&quot;.

Embora a maioria dos recursos esteja presente na interface habilitada para toque, há recursos que ainda não foram concluídos e serão adicionados em versões futuras.

A lista a seguir mostra o status atual dos recursos conforme implementado no AEM 6.4.

Para obter recomendações para clientes que atualizam para o AEM 6.4, consulte [Recommendations da interface do usuário para clientes](/help/sites-deploying/ui-recommendations.md) para obter detalhes.

>[!NOTE]
>
>Observe que esta página só abrange a paridade de recursos com a interface clássica.
>
>Os recursos adicionados e exclusivos à interface habilitada para toque que não estão presentes na interface clássica não são listados.

>[!NOTE]
>
>Esta lista esforça-se por ser completa, mas não deve ser considerada exaustiva.

## Legenda {#legend}

* **Concluído**: O recurso está totalmente disponível na interface habilitada para toque
* **Principalmente**: A maioria dos recursos está disponível na interface habilitada para toque.
* **Ausente**: O recurso não está presente na interface habilitada para toque, a interface clássica deve ser usada para fazer essa ação.
* **Substituído**: O recurso foi substituído por uma nova implementação que funciona de forma diferente.
* **Removido**: O recurso não existe mais na interface habilitada para toque e não será substituído.

## Status do recurso: Administrador de sites {#feature-status-sites-admin}

Esta é uma lista de recursos do Administrador do site da interface clássica ( `/siteadmin`) tem e o status na interface habilitada para toque ( `/sites.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Destaque<br /> </strong></td> 
   <td><strong>Status<br /> </strong></td> 
   <td><strong>Comentar</strong></td> 
  </tr>
  <tr>
   <td>Navegar pela Hierarquia do Site</td> 
   <td>Concluir<br /> </td> 
   <td>AEM 6.4 apresenta uma <a href="/help/sites-authoring/basic-handling.md#content-tree">exibição em árvore de conteúdo</a>.</td> 
  </tr>
  <tr>
   <td>Iniciar fluxo de trabalho</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Criar nova página</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Criar novo site</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Criar novo lançamento</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Criar nova cópia dinâmica <br /> </td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Criar pasta</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mostrar status da publicação</td> 
   <td>Principalmente</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pesquisar</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Página Copiar/Colar (Duplicado)</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mover páginas</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicar páginas</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicar páginas sem direitos de replicação</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicar mais tarde</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Árvore de publicação</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Desfazer a publicação de páginas</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Cancelar a publicação de páginas sem direitos de replicação</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Desfazer a publicação mais tarde</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Excluir</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Bloquear/Desbloquear</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Exibir/editar propriedades</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Definir permissões na(s) página(s)</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Histórico da versão</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Restaurar versão</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Restaurar árvore e restaurar páginas excluídas</td> 
   <td>Ausente</td> 
   <td>Use a interface clássica.</td> 
  </tr>
  <tr>
   <td>Mostrar diferença entre a versão antiga e a atual<br /> </td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ações Livecopy (implantação)</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ver cópias de idioma</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Localizar e Substituir</td> 
   <td>Ausente<br /> </td> 
   <td>Use a interface clássica.</td> 
  </tr>
  <tr>
   <td>Caixa de entrada de notificações (eventos JCR)</td> 
   <td>Ausente</td> 
   <td>Use a interface clássica. Será substituída por uma implementação diferente.</td> 
  </tr>
  <tr>
   <td>Referências</td> 
   <td>Principalmente</td> 
   <td>A exibição de links de página de entrada será adicionada na versão de AEM de 2019.</td> 
  </tr>
 </tbody>
</table>

## Status do recurso: Editor de páginas {#feature-status-page-editor}

Esta é uma lista de recursos do Editor de página da interface clássica ( `/cf#`) tem e o status na interface habilitada para toque ( `/editor.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Destaque</strong></td> 
   <td><strong>Status</strong></td> 
   <td><strong>Comentar</strong></td> 
  </tr>
  <tr>
   <td>Editar páginas da Web</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar páginas da Web móveis<br /> </td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar conteúdo importado pelo Importador de design<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar E-Mails</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar aplicativos móveis</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar Forms</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar ofertas</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar modelos de fluxos de trabalho<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Código: Editar e visualizar</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Visualização responsiva<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modo: Editar design</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modo: Andaime</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modo: Status da Live Copy<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Adicionar anotações</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar propriedades<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Página de implantação</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Iniciar e mostrar fluxo de trabalho</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Entrega do pacote de fluxo de trabalho</td> 
   <td>Principalmente</td> 
   <td>Completamente acessível na interface habilitada para toque. A carga de vários fluxos de trabalho ainda é apresentada na interface clássica.<br /> </td> 
  </tr>
  <tr>
   <td>Bloquear/desbloquear página</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicar página <br /> </td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Desfazer a publicação da página</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Página de cópia</td> 
   <td>Removido<br /> </td> 
   <td>Use o administrador do site para <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">copiar páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Mover página</td> 
   <td>Removido</td> 
   <td>Use o administrador do site para <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">mover páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Excluir página</td> 
   <td>Removido</td> 
   <td>Use o administrador do site para <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">excluir páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Mostrar referências</td> 
   <td>Removido</td> 
   <td>Use o administrador do site para <a href="/help/sites-authoring/author-environment-tools.md#references">consulte a lista detalhada de referência</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Log de auditoria</td> 
   <td>Removido</td> 
   <td>Use o Administrador do site e <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">abrir o painel de atividades</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Criar versão</td> 
   <td>Removido</td> 
   <td>Use o administrador do site para <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">criar novas versões</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Restaurar versão</td> 
   <td>Removido</td> 
   <td>Use o administrador do site para <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">restaurar versões</a>.</td> 
  </tr>
  <tr>
   <td>Alternar inicializações</td> 
   <td>Removido</td> 
   <td>Use o administrador do site para <a href="/help/sites-authoring/launches-promoting.md">alternar entre inicializações</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Traduzir página</td> 
   <td>Removido</td> 
   <td>Use o administrador do site para <a href="/help/sites-administering/tc-manage.md">adicionar página a projetos de tradução</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Timewarp (escolha data/hora e navegue pelo site como ele parecia)<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Definir permissões</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interface do usuário de contexto do cliente<br /> </td> 
   <td>Substituído</td> 
   <td>Use o <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> Interface do usuário do que está avançando.</td> 
  </tr>
  <tr>
   <td>Localizador de conteúdo para os vários tipos de mídia<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Lista de componentes</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copiar e colar componentes<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Lista de componentes na área de transferência</td> 
   <td>Ausente</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Desfazer / Refazer</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Arrastar e soltar conteúdo no espaço reservado do componente</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Arraste e solte o conteúdo diretamente no espaço reservado do parsys com a criação automática do componente<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Status do recurso: Editores de texto, tabela e imagem {#feature-status-text-table-and-image-editors}

Esta é uma lista de recursos que a interface clássica Texto, Tabela e Editor de imagem têm e o status na interface habilitada para toque.

<table> 
 <tbody>
  <tr>
   <td><strong>Destaque</strong></td> 
   <td><strong>Status </strong></td> 
   <td><strong>Comentar<br /> </strong></td> 
  </tr>
  <tr>
   <td>Editor de rich text</td> 
   <td>Concluir</td> 
   <td>Usável no local, na caixa de diálogo e em tela cheia.</td> 
  </tr>
  <tr>
   <td>Ativar/desativar plug-ins do RTE</td> 
   <td>Concluir<br /> </td> 
   <td>Pode ser feito usando o <a href="/help/sites-authoring/templates.md">Editor de modelos</a>.</td> 
  </tr>
  <tr>
   <td>Usar RTE para texto sem formatação</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Links e âncora</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Mapa de caracteres</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Copiar/Colar</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Colar do Microsoft Word<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Localizar e Substituir</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Formatos de texto (negrito, ...)</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Sub &amp; Sobrescrito</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Justificar</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Listas (marcador/números)</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Formato do parágrafo</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Estilos de texto</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Editor de código-fonte (HTML de edição)<br /> </td> 
   <td>Concluir<br /> </td> 
   <td>Disponível somente na caixa de diálogo e em tela cheia.<br /> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Verificador Ortográfico</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Tabela (Editor de tabela incorporado)</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Desfazer/Refazer<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do RTE: Permitir imagens em linha</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editor de tabela</td> 
   <td>Concluir</td> 
   <td>Usável no local, na caixa de diálogo e em tela cheia.<br /> </td> 
  </tr>
  <tr>
   <td>Arrastar e soltar Imagem na célula da tabela<br /> </td> 
   <td>Concluir</td> 
   <td>Utilizável em linha</td> 
  </tr>
  <tr>
   <td>Editor de imagem <br /> </td> 
   <td>Concluir</td> 
   <td>Usável no local, na caixa de diálogo e em tela cheia.<br /> </td> 
  </tr>
  <tr>
   <td>Ativar/desativar plug-ins do IPE</td> 
   <td>Concluir</td> 
   <td>Agora há uma interface do usuário no <a href="/help/sites-authoring/templates.md">Editor de modelos</a>.</td> 
  </tr>
  <tr>
   <td>Plug-in do IPE: Cortar</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do IPE: Inverter</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do IPE: Desfazer/Refazer</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do IPE: Mapa de imagem</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do IPE: Girar</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in do IPE: Zoom</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Status do recurso: Ferramentas {#feature-status-tools}

Esta é uma lista de várias ferramentas que a interface clássica tem e o status na interface habilitada para toque.

<table> 
 <tbody>
  <tr>
   <td><strong>Destaque<br /> </strong></td> 
   <td><strong>Status<br /> </strong></td> 
   <td><strong>Comentar</strong></td> 
  </tr>
  <tr>
   <td>Gerenciamento de tarefas</td> 
   <td>Substituído</td> 
   <td>6.0 introduzido <a href="/help/sites-authoring/projects.md">Projetos e tarefas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Caixa de entrada do fluxo de trabalho<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Fluxo de trabalho para a configuração do modelo de página (<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>Ausente<br /> </td> 
   <td>Use a interface clássica.</td> 
  </tr>
  <tr>
   <td>Marcação da interface do usuário do administrador<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Centro de Controle de MSM/Blueprint</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interface do usuário do Gerenciador de Blueprint</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interface do usuário de configuração de implementação</td> 
   <td>Ausente</td> 
   <td>Use a interface clássica.</td> 
  </tr>
  <tr>
   <td>Interface do usuário do usuário, grupos e permissões<br /> </td> 
   <td>Principalmente completo<br /> </td> 
   <td>Para editar permissões avançadas, use a interface clássica.<br /> </td> 
  </tr>
  <tr>
   <td>Limpar versões (<code>/etc/versioning/purge.html</code>)</td> 
   <td>Ausente</td> 
   <td>Use a interface clássica.</td> 
  </tr>
  <tr>
   <td>Verificador de links externos (<code>/etc/linkchecker.html</code>)</td> 
   <td>Ausente</td> 
   <td>Use a interface clássica.<br /> </td> 
  </tr>
  <tr>
   <td>Editor em massa (<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>Ausente<br /> </td> 
   <td>Use a interface clássica.</td> 
  </tr>
 </tbody>
</table>
