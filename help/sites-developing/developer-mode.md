---
title: Modo de desenvolvedor
seo-title: Developer Mode
description: O modo Desenvolvedor abre um painel lateral com várias guias que fornecem a um desenvolvedor informações sobre a página atual
seo-description: Developer mode opens a side panel with several tabs that provide a developer with infomation about the current page
uuid: 2ff0d85e-fe49-4506-b6d6-74cc060d7ea1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: efbe46a3-c37f-4b67-8b3a-188cfc75118b
exl-id: 733eddf1-48f9-45c2-a1b4-138cf32b4b59
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 2%

---

# Modo de desenvolvedor{#developer-mode}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Ao editar páginas em AEM, vários [modos](/help/sites-authoring/author-environment-tools.md#page-modes) estão disponíveis, incluindo o modo Desenvolvedor . Isso abre um painel lateral com várias guias que fornecem ao desenvolvedor informações sobre a página atual. As três guias são:

* **[Componentes](#components)** para exibir informações sobre estrutura e desempenho.
* **[Testes](#tests)** para executar testes e analisar os resultados.
* **[Erros](#errors)** para ver qualquer problema que esteja ocorrendo.

Isso ajuda um desenvolvedor a:

* Discover: quais páginas são compostas.
* Depuração: o que está acontecendo onde e quando, o que por sua vez ajuda a resolver os problemas.
* Teste: O aplicativo se comporta conforme esperado.

>[!CAUTION]
>
>Modo de desenvolvedor:
>
>* Está disponível somente na interface habilitada para toque (ao editar páginas).
>* Não está disponível em dispositivos móveis ou janelas pequenas no desktop (devido a restrições de espaço).
   >   * Isso ocorre quando a largura é inferior a 1024px.
>* Está disponível somente para usuários que são membros do `administrators` grupo.


>[!CAUTION]
>
>O modo Desenvolvedor só está disponível em uma instância de autor padrão que não está usando o modo de execução nosamplecontent.
>
>Se necessário, ele pode ser configurado para uso:
>
>* em uma instância do autor usando nosamplecontent run-mode
>* uma instância de publicação
>
>Deve ser desativado novamente após a utilização.

>[!NOTE]
>
>Consulte o:
>
>* Artigo da Base de conhecimento, [Solução de problemas AEM TouchUI](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html), para obter mais dicas e ferramentas.
>* Sessão AEM Gems sobre [Modo de desenvolvedor do AEM 6.0](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-developer-mode.html).


## Abrir o Modo de Desenvolvedor {#opening-developer-mode}

O modo Desenvolvedor é implementado como um painel lateral para o editor de páginas. Para abrir o painel, selecione **Desenvolvedor** no seletor de modo na barra de ferramentas do editor de páginas:

![chlimage_1-229](assets/chlimage_1-229.png)

O painel é dividido em duas guias:

* **[Componentes](/help/sites-developing/developer-mode.md#components)** - Mostra uma árvore de componentes, semelhante à [árvore de conteúdo](/help/sites-authoring/author-environment-tools.md#content-tree) para autores

* **[Erros](/help/sites-developing/developer-mode.md#errors)** - Quando ocorrem problemas, os detalhes são mostrados para cada componente.

### Componentes {#components}

![chlimage_1-230](assets/chlimage_1-230.png)

Isso mostra uma árvore de componentes que:

* Descreve a cadeia de componentes e modelos renderizados na página (SLY, JSP, etc.). A árvore pode ser expandida para mostrar o contexto na hierarquia.
* Mostra o tempo computacional do lado do servidor necessário para renderizar o componente.
* Permite expandir a árvore e selecionar componentes específicos dentro da árvore. A seleção fornece acesso aos detalhes do componente; como:

   * Caminho do repositório
   * Links para scripts (acessados no CRXDE Lite)

* Os componentes selecionados (no fluxo de conteúdo, indicado por uma borda azul) serão realçados na árvore de conteúdo (e vice-versa).

Isso pode ajudar a:

* Determine e compare o tempo de renderização por componente.
* Consulte e entenda a hierarquia.
* Entenda e melhore o tempo de carregamento da página ao encontrar componentes lentos.

Cada entrada de componente pode mostrar (por exemplo):

![chlimage_1-231](assets/chlimage_1-231.png)

* **Exibir detalhes**: um link para uma lista que mostra:

   * todos os scripts de componente usados para renderizar o componente.
   * o caminho do conteúdo do repositório para esse componente específico.

   ![chlimage_1-232](assets/chlimage_1-232.png)

* **Editar script**: um link que:

   * abre o script de componente no CRXDE Lite.

* Expandir uma entrada de componente (cabeça de seta) também pode mostrar:

   * A hierarquia no componente selecionado.
   * Tempos de renderização do componente selecionado de forma isolada, quaisquer componentes individuais aninhados dentro dele e o total combinado.

   ![chlimage_1-233](assets/chlimage_1-233.png)

>[!CAUTION]
>
>Alguns links apontam para scripts em `/libs`. No entanto, esses são apenas para referência, você **não deve** edite qualquer item em `/libs`, como qualquer alteração feita, pode ser perdida. Isso se deve ao fato de que essa ramificação está sujeita a alterações sempre que você atualiza ou aplica um hotfix/pacote de recursos. Quaisquer alterações necessárias devem ser feitas em `/apps`, consulte [Sobreposições e substituições](/help/sites-developing/overlays.md).

### Erros {#errors}

![chlimage_1-234](assets/chlimage_1-234.png)

Espero que a variável **Erros** sempre estará vazia (como acima), mas quando ocorrerem problemas, os seguintes detalhes serão mostrados para cada componente:

* Um aviso se o componente gravar uma entrada no log de erros, juntamente com detalhes do erro e links diretos para o código apropriado no CRXDE Lite.
* Um aviso se o componente abrir uma sessão de administrador.

Por exemplo, em uma situação em que um método indefinido é chamado, o erro resultante será mostrado na função **Erros** guia :

![chlimage_1-235](assets/chlimage_1-235.png)

A entrada de componente na árvore da guia Componentes também será marcada com um indicador quando ocorrer um erro.

### Testes {#tests}

>[!CAUTION]
>
>No AEM 6.2, os recursos de teste do modo Desenvolvedor foram reimplementados como um aplicativo de Ferramentas independente.
>
>Para obter detalhes completos, consulte [Testar sua interface do usuário](/help/sites-developing/hobbes.md).
