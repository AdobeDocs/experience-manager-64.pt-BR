---
title: Eventos OSGi para componentes das Comunidades
seo-title: OSGi Events for Communities Components
description: Eventos OSGi são enviados que podem acionar ouvintes assíncronos
seo-description: OSGi events are sent that can trigger asynchronous listeners
uuid: 317e2add-689d-4c99-ae38-0703b6649cb7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 25b7ac08-6cdc-4dd5-a756-d6169b86f9ab
exl-id: 3f7d1b95-729a-4c55-af96-efdb9617d333
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 5%

---

# Eventos OSGi para componentes das Comunidades {#osgi-events-for-communities-components}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

Quando os membros interagem com os recursos das Comunidades, os eventos OSGi são enviados e podem acionar ouvintes assíncronos, como notificações ou gamificação (pontuação e selo).

Um componente [SocialEvent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) A instância registra os eventos como `actions`que ocorrem para um `topic`. O SocialEvent inclui um método para retornar um `verb`associada à ação. Existe um *n-1* relação entre `actions`e `verbs`.

Para os componentes Comunidades entregues na versão, as tabelas a seguir descrevem a `verbs`definido para cada `topic`disponível para uso.

## Tópicos e verbos {#topics-and-verbs}

[Componente de calendário](calendar-basics-for-developers.md)
SocialEvent `topic`= com/adobe/cq/social/calendar

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria um evento de calendário |
| ADICIONAR | comentários do membro em um evento de calendário |
| ATUALIZAR | evento ou comentário do calendário do membro é editado |
| EXCLUIR | o evento ou comentário do calendário do membro é excluído |

[Componente Comentários](essentials-comments.md)
SocialEvent `topic`= com/adobe/cq/social/comment

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria um comentário |
| ADICIONAR | membro responde ao comentário |
| ATUALIZAR | o comentário do membro é editado |
| EXCLUIR | o comentário do membro é excluído |

[Componente Biblioteca de arquivos](essentials-file-library.md)
SocialEvent `topic`= com/adobe/cq/social/fileLibrary

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria uma pasta |
| ANEXAR | membro carrega um arquivo |
| ATUALIZAR | membro atualiza uma pasta ou arquivo |
| EXCLUIR | membro exclui uma pasta ou arquivo |

[Componente de fórum](essentials-forum.md)
SocialEvent `topic`= com/adobe/cq/social/forum

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria tópico do fórum |
| ADICIONAR | membro responde ao tópico do fórum |
| ATUALIZAR | o tópico ou a resposta do fórum do membro é editada |
| EXCLUIR | o tópico ou resposta do fórum do membro é excluído |

[Componente Diário](blog-developer-basics.md)
SocialEvent `topic`= com/adobe/cq/social/journal

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria um artigo de blog |
| ADICIONAR | membro comenta em um artigo do blog |
| ATUALIZAR | artigo ou comentário do blog do membro é editado |
| EXCLUIR | artigo ou comentário do blog do membro é excluído |

[Componente QnA](qna-essentials.md)
SocialEvent `topic` = com/adobe/cq/social/qna

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria uma pergunta QnA |
| ADICIONAR | membro cria uma resposta QnA |
| ATUALIZAR | pergunta ou resposta QnA do membro é editada |
| SELECIONAR | a resposta do membro é selecionada |
| CANCELAR SELEÇÃO | a resposta do membro é desmarcada |
| EXCLUIR | pergunta ou resposta QnA do membro é excluída |

[Componente de revisões](reviews-basics.md)
SocialEvent `topic`= com/adobe/cq/social/review

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria revisão |
| ATUALIZAR | a revisão do membro é editada |
| EXCLUIR | a revisão do membro é eliminada |

[Componente de classificação](rating-basics.md)
SocialEvent `topic`= com/adobe/cq/social/tally

| **Verbo** | **Descrição** |
|---|---|
| ADICIONAR CLASSIFICAÇÃO | o conteúdo do membro foi atualizado |
| REMOVER CLASSIFICAÇÃO | o conteúdo do membro foi reduzido |

[Componente de votação](essentials-voting.md)
SocialEvent `topic`= com/adobe/cq/social/tally

| **Verbo** | **Descrição** |
|---|---|
| ADICIONAR VOTAÇÃO | o conteúdo do membro foi votado |
| REMOVER VOTAÇÃO | o conteúdo do membro foi rejeitado |

**Componentes habilitados para moderação**
SocialEvent `topic`= com/adobe/cq/social/moderação

| **Verbo** | **Descrição** |
|---|---|
| NEGAR | o conteúdo do membro é negado |
| SINALIZADOR COMO INADEQUADO | o conteúdo do membro é sinalizado |
| INADEQUADO | o conteúdo do membro não está sinalizado |
| ACEITAR | o conteúdo do membro é aprovado pelo moderador |
| FECHAR | membro fecha comentário a edições e respostas |
| ABRIR | membro reabre comentário |

## Eventos para componentes personalizados {#events-for-custom-components}

Para um componente personalizado, a variável [Classe abstrata do SocialEvent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) deve ser estendido d para registrar os eventos do componente como `actions`que ocorrem para um `topic`.

O evento personalizado substituiria o método `getVerb()` de forma a que `verb`é retornado para cada `action`. O `verb` retornado para uma ação pode ser usado normalmente (como `POST`) ou uma especializada para o componente (como `ADD RATING`). Existe um *n-1* relação entre `actions`e `verbs`.

>[!NOTE]
>
>Certifique-se de que uma extensão personalizada esteja registrada com uma classificação inferior a qualquer implementação existente no produto.

### Pseudo-código para o evento de componente personalizado {#pseudo-code-for-custom-component-event}

[org.osgi.service.event.Event](https://osgi.org/javadoc/r4v41/org/osgi/service/event/Event.html);\
[com.adobe.cq.social.scf.core.SocialEvent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html);\
[com.adobe.granite.activitystreams.ObjectTypes](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ObjectTypes.html);\
[com.adobe.granite.activitystreams.Verbs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/Verbs.html);

```java
package com.mycompany.recipe;

import org.osgi.service.event.Event;
import com.adobe.cq.social.scf.core.SocialEvent;
import com.adobe.granite.activitystreams.ObjectTypes;
import com.adobe.granite.activitystreams.Verbs;

/* 
 * The Recipe type, passed to RecipeEvent(), would be a custom Recipe class 
 * that extends either 
 * com.adobe.cq.social.scf.SocialComponent 
 * or
 * com.adobe.cq.social.scf.SocialCollectionComponent
 * See https://docs.adobe.com/docs/en/aem/6-2/develop/communities/scf/server-customize.html
 */

/**
 * Defines events that are triggered on a custom component, "Recipe".
 */
public class RecipeEvent extends SocialEvent<RecipeEvent.RecipeActions> {

    private static final long serialVersionUID = 1L;
    protected static final String PARENT_PATH = "PARENT_PATH";

    /**
     * The event topic suffix for Recipe events
     */
    public static final String RECIPE_TOPIC = "recipe";

    /**
     * @param recipe - the recipe resource on which the event was triggered
     * @param userId - the user id of the user who triggered the action
     * @param action - the recipe action that triggered this event
     */
    public RecipeEvent(final Recipe recipe, final String userId, final RecipeEvent.RecipeActions action) {
        String recipePath = recipe.getResource().getPath();
        String parentPath = (recipe.getParentComponent() != null) ? 
                             recipe.getParentComponent().getResource().getPath() : 
                             recipe.getSourceComponentId();
        this(recipePath, userId, parentPath, action);
    }

    /**
     * @param recipePath - the path to the recipe resource (jcr node) on which the event was triggered
     * @param userId - the user id of the user who triggered the action
     * @param parentPath - the path to the parent node of the recipe resource
     * @param action - the recipe action that triggered this event
     */
    public RecipeEvent(final String recipePath, final String userId, final String parentPath) {
        super(RECIPE_TOPIC, recipePath, userId, action, 
              new BaseEventObject(recipePath, ObjectTypes.ARTICLE), 
              new BaseEventObject(parentPath, ObjectTypes.COLLECTION),
              new HashMap<String, Object>(1) {
            private static final long serialVersionUID = 1L;
            {
                if (parentPath != null) {
                    this.put(PARENT_PATH, parentPath);
                }

            }
        });
    }

    private RecipeEvent (final Event event) {
      super(event);
    }

    /**
     * List of available recipe actions that can trigger a recipe event.
     */
    public static enum RecipeActions implements SocialEvent.SocialActions {
        RecipeAdded, 
        RecipeModified, 
        RecipeDeleted;

        @Override
        public String getVerb() {
            switch (this) {
                case RecipeAdded:
                    return Verbs.POST;
                case RecipeModified:
                    return Verbs.UPDATE;
                case RecipeDeleted:
                    return Verbs.DELETE;
                default:
                    throw new IllegalArgumentException("Unsupported action");
            }
        }
    }

}
```

## Exemplo de EventListener para filtrar dados de fluxo de atividade {#sample-eventlistener-to-filter-activity-stream-data}

É possível ouvir eventos com o objetivo de modificar o que aparece no fluxo de atividades.

A amostra de pseudo-código a seguir removerá DELETE events para o componente Comentários do fluxo de atividades.

### Pseudo-código para EventListener {#pseudo-code-for-eventlistener}

Exige [pacote de recursos mais recente](deploy-communities.md#latestfeaturepack).

```java
package my.company.comments;

import java.util.Collections;
import java.util.Map;

import org.apache.commons.lang.StringUtils;
import org.apache.felix.scr.annotations.Activate;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Modified;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.commons.osgi.PropertiesUtil;
import org.osgi.service.component.ComponentContext;

import com.adobe.cq.social.activitystreams.listener.api.ActivityStreamProviderExtension;
import com.adobe.cq.social.commons.events.CommentEvent.CommentActions;
import com.adobe.cq.social.scf.core.SocialEvent;

@Service
@Component(metatype = true, label = "My Comment Delete Event Filter",
        description = "Prevents comment DELETE events from showing up in activity streams")
public class CommentDeleteEventActivityFilter implements ActivityStreamProviderExtension {

    @Property(name = "ranking", intValue = 10)
    protected int ranking;

    @Activate
    public void activate(final ComponentContext ctx) {
        ranking = PropertiesUtil.toInteger(ctx.getProperties().get("ranking"), 10);
    }

    @Modified
    public void update(final Map<String, Object> props) {
        ranking = PropertiesUtil.toInteger(props.get("ranking"), 10);
    }

    @Override
    public boolean evaluate(final SocialEvent<?> evt, final Resource resource) {
        if (evt.getAction() != null && evt.getAction() instanceof SocialEvent.SocialActions) {
            final SocialEvent.SocialActions action = evt.getAction();
            if (StringUtils.equals(action.getVerb(), CommentActions.DELETED.getVerb())) {
                return false;
            }
        }
        return true;
    }

    @Override
    public Map<String, ? extends Object> getActivityProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public Map<String, ? extends Object> getActorProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public String getName() {
        return "My Comment Delete Event Filter";
    }

    @Override
    public Map<String, ? extends Object> getObjectProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    /* Ensure a custom extension is registered with a ranking lower than any existing implementation in the product. */
    @Override
    public int getRanking() {
        return this.ranking;
    }

    @Override
    public Map<String, ? extends Object> getTargetProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public String[] getStreamProviderPid() {
        return new String[]{"*"};
    }

}
```
