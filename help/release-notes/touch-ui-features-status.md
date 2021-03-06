---
title: Status do recurso da interface de toque
seo-title: Status do recurso da interface de toque
description: Notas de versão específicas da interface de usuário para toque Adobe Experience Manager 6.3.
seo-description: Notas de versão específicas da interface de usuário para toque Adobe Experience Manager 6.3.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
translation-type: tm+mt
source-git-commit: db26dd05f6c0997eeda462f27971cbcfa6737527
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 14%

---


# Status do recurso da interface de toque {#touch-ui-feature-status}

>[!CAUTION]
>
>Com a versão 6.4 do AEM, a [interface clássica está obsoleta](/help/release-notes/deprecated-removed-features.md). O Adobe não pretende fazer mais aprimoramentos na interface clássica e os usuários são incentivados a aproveitar os novos recursos avançados disponíveis na interface habilitada para toque.

A partir da versão 6.0, AEM introduziu uma nova interface de usuário chamada de &quot;interface habilitada para toque&quot; (também conhecida como &quot;interface de usuário para toque&quot;) que está alinhada ao Adobe Marketing Cloud e às diretrizes gerais da interface de usuário do Adobe. Com a quase partição de recursos atingida, essa interface se tornou a interface padrão em AEM com a interface legada orientada para desktop chamada de &quot;interface clássica&quot;.

Embora a maioria dos recursos esteja presente na interface habilitada para toque, há recursos que ainda não estão completos e serão adicionados em versões futuras.

A lista a seguir mostra o status atual dos recursos conforme implementado no AEM 6.4.

Para obter recomendações para clientes que atualizam para AEM 6.4, consulte [Interface do usuário Recommendations for Customers](/help/sites-deploying/ui-recommendations.md) para obter detalhes.

>[!NOTE]
>
>Observe que esta página só cobre a paridade de recursos com a interface clássica.
>
>Os recursos adicionados e exclusivos à interface habilitada para toque que não estão presentes na interface clássica não são listados.

>[!NOTE]
>
>Essa lista se esforça para ser completa, mas não deve ser considerada exaustiva.

## Legenda {#legend}

* **Concluído**: O recurso está totalmente disponível na interface habilitada para toque
* **Principalmente**: O recurso está disponível principalmente na interface habilitada para toque.
* **Ausente**: O recurso não está presente na interface habilitada para toque, a interface clássica deve ser usada para realizar essa ação.
* **Substituído**: O recurso foi substituído por uma nova implementação que funciona de forma diferente.
* **Removido**: O recurso não existe mais na interface habilitada para toque e não será substituído.

## Status do recurso: Administrador de sites {#feature-status-sites-admin}

Esta é uma lista de recursos que o administrador do site da interface clássica ( `/siteadmin`) tem e o status na interface habilitada para toque ( `/sites.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Recurso<br /> </strong></td> 
   <td><strong>Status<br /> </strong></td> 
   <td><strong>Comentário</strong></td> 
  </tr>
  <tr>
   <td>Navegar pela Hierarquia do Site</td> 
   <td>Concluir<br /> </td> 
   <td>AEM 6.4 introduziu uma visualização de <a href="/help/sites-authoring/basic-handling.md#content-tree">árvore de conteúdo</a>.</td> 
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
   <td>Criar nova inicialização</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Criar nova live copy <br /> </td> 
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
   <td>Pesquisar  </td> 
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
   <td>Publicar árvore</td> 
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
   <td>Propriedades de visualização/edição</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Definir permissões nas páginas</td> 
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
   <td>Mostrar diferença entre as versões antiga e atual<br /> </td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ações do Livecopy (implantação)</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Consulte cópias de idioma</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Localizar e Substituir</td> 
   <td>Falta<br /> </td> 
   <td>Use a interface clássica.</td> 
  </tr>
  <tr>
   <td>Caixa de entrada de notificação (eventos JCR)</td> 
   <td>Ausente</td> 
   <td>Use a interface clássica. Será substituído por uma implementação diferente.</td> 
  </tr>
  <tr>
   <td>Referências</td> 
   <td>Principalmente</td> 
   <td>A exibição de links de páginas de entrada será adicionada na versão 2019 do AEM.</td> 
  </tr>
 </tbody>
</table>

## Status do recurso: Editor de páginas {#feature-status-page-editor}

Esta é uma lista de recursos que o Editor de página da interface clássica ( `/cf#`) tem e o status na interface habilitada para toque ( `/editor.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Recurso</strong></td> 
   <td><strong>Status</strong></td> 
   <td><strong>Comentário</strong></td> 
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
   <td>Editar conteúdo importado por meio do Importador de design<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar e-mails</td> 
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
   <td>Editar Ofertas</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar modelos de Workflows<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Código: Editar e Pré-visualização</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pré-visualização responsiva<br /> </td> 
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
   <td>Start e mostrar fluxo de trabalho</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Tratamento do pacote de fluxo de trabalho</td> 
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
   <td>Use o Administrador do site para <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">copiar páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Mover página</td> 
   <td>Removido</td> 
   <td>Use o Administrador do Site para <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">mover páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Excluir página</td> 
   <td>Removido</td> 
   <td>Use o Administrador do site para <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">excluir páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Mostrar referências</td> 
   <td>Removido</td> 
   <td>Use o Administrador do site para <a href="/help/sites-authoring/author-environment-tools.md#references">ver a lista de referência detalhada</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Log de auditoria</td> 
   <td>Removido</td> 
   <td>Use o Administrador do site e <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">abrir o painel de atividade</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Criar versão</td> 
   <td>Removido</td> 
   <td>Use o Administrador do site para <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">criar novas versões</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Restaurar versão</td> 
   <td>Removido</td> 
   <td>Use o Administrador do site para <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">restaurar versões</a>.</td> 
  </tr>
  <tr>
   <td>Interromper inicializações</td> 
   <td>Removido</td> 
   <td>Use o Administrador do Site para alternar <a href="/help/sites-authoring/launches-promoting.md">entre inicializações</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Traduzir página</td> 
   <td>Removido</td> 
   <td>Use o Administrador do Site para <a href="/help/sites-administering/tc-manage.md">adicionar página a projetos de tradução</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Timewarp (escolha a data/hora e navegue no site como ele parecia)<br /> </td> 
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
   <td>Use a interface do usuário <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> para frente.</td> 
  </tr>
  <tr>
   <td>Localizador de conteúdo para os vários tipos de mídia<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Lista do componente</td> 
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
   <td>Arraste e solte o conteúdo diretamente no espaço reservado parsys com a criação automática do componente<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Status do recurso: Editores de texto, tabela e imagem {#feature-status-text-table-and-image-editors}

Esta é uma lista de recursos que o Texto da interface clássica, a Tabela e o Editor de imagem têm e o status na interface habilitada para toque.

<table> 
 <tbody>
  <tr>
   <td><strong>Recurso</strong></td> 
   <td><strong>Status </strong></td> 
   <td><strong>Comentário<br /> </strong></td> 
  </tr>
  <tr>
   <td>Editor de Rich Text</td> 
   <td>Concluir</td> 
   <td>Usável no local, na caixa de diálogo e em tela cheia.</td> 
  </tr>
  <tr>
   <td>Ativar/desativar plug-ins RTE</td> 
   <td>Concluir<br /> </td> 
   <td>Pode ser feito usando o <a href="/help/sites-authoring/templates.md">Editor de modelos</a>.</td> 
  </tr>
  <tr>
   <td>Usar RTE para texto sem formatação</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Links e âncora</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Mapa de caracteres</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Copiar/colar</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Colar do Microsoft Word<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Localizar e substituir</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Formatos de texto (negrito, ...)</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Sub e sobrescrito</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Justificar</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Listas (marcadores/números)</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Formato de parágrafo</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Estilos de texto</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Editor de código-fonte (Editar HTML)<br /> </td> 
   <td>Concluir<br /> </td> 
   <td>Disponível apenas na caixa de diálogo e em tela cheia.<br /> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Verificador ortográfico</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Tabela (editor de tabela incorporado)</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Desfazer/Refazer<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Permitir imagens em linha</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editor de tabela</td> 
   <td>Concluir</td> 
   <td>Usável no local, na caixa de diálogo e em tela cheia.<br /> </td> 
  </tr>
  <tr>
   <td>Arrastar e soltar imagem na célula da tabela<br /> </td> 
   <td>Concluir</td> 
   <td>Usável em linha</td> 
  </tr>
  <tr>
   <td>Editor de imagem <br /> </td> 
   <td>Concluir</td> 
   <td>Usável no local, na caixa de diálogo e em tela cheia.<br /> </td> 
  </tr>
  <tr>
   <td>Ativar/desativar plug-ins IPE</td> 
   <td>Concluir</td> 
   <td>Agora há uma interface no <a href="/help/sites-authoring/templates.md">Editor de modelos</a>.</td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Recortar</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Inverter</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Desfazer/Refazer</td> 
   <td>Concluir<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Mapa de imagem</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Girar</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Zoom</td> 
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
   <td><strong>Recurso<br /> </strong></td> 
   <td><strong>Status<br /> </strong></td> 
   <td><strong>Comentário</strong></td> 
  </tr>
  <tr>
   <td>Gerenciamento de tarefas</td> 
   <td>Substituído</td> 
   <td>6.0 introduziu <a href="/help/sites-authoring/projects.md">Projetos e Tarefas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Caixa de entrada do fluxo de trabalho<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Configuração do fluxo de trabalho para modelo de página (<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>Falta<br /> </td> 
   <td>Use a interface clássica.</td> 
  </tr>
  <tr>
   <td>Marcação da interface do usuário do administrador<br /> </td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Centro de controle MSM/Blueprint</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interface do usuário do Gerenciador de Blueprint</td> 
   <td>Concluir</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interface do usuário de configuração de implantação</td> 
   <td>Ausente</td> 
   <td>Use a interface clássica.</td> 
  </tr>
  <tr>
   <td>UI de usuário, grupos e permissões<br /> </td> 
   <td>Principalmente completo<br /> </td> 
   <td>Para a edição avançada de permissões, use a interface clássica.<br /> </td> 
  </tr>
  <tr>
   <td>Expurgar Versões (<code>/etc/versioning/purge.html</code>)</td> 
   <td>Ausente</td> 
   <td>Use a interface clássica.</td> 
  </tr>
  <tr>
   <td>Verificador de links externos (<code>/etc/linkchecker.html</code>)</td> 
   <td>Ausente</td> 
   <td>Usar interface clássica.<br /> </td> 
  </tr>
  <tr>
   <td>Editor em massa (<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>Falta<br /> </td> 
   <td>Use a interface clássica.</td> 
  </tr>
 </tbody>
</table>

