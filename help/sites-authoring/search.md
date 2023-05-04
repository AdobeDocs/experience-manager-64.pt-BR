---
title: Pesquisar
seo-title: Search
description: Encontre seu conteúdo mais rapidamente com uma pesquisa abrangente
seo-description: Find your content faster with comprehensive search
uuid: 1e80cf85-653f-4dde-930a-de05415b994f
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: cd87e1e8-5329-4e60-ac9d-2705f54d0da6
exl-id: 9e93b28b-627d-4676-82a6-d719de4d152a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 54%

---

# Pesquisar  {#search-features}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O ambiente de criação do AEM fornece vários mecanismos de pesquisa de conteúdo, dependendo do tipo de recurso.

>[!NOTE]
>
>Fora do ambiente de criação, outros mecanismos também estão disponíveis para pesquisa, como o [Query Builder](/help/sites-developing/querybuilder-api.md) e [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Noções básicas de pesquisa {#search-basics}

A pesquisa está disponível na barra de ferramentas superior:

![](do-not-localize/chlimage_1-17.png)

Com o painel de pesquisa, você pode:

* Pesquise por uma palavra-chave, um caminho ou uma tag específica.
* Filtre de acordo com os critérios específicos dos recursos, como datas modificadas, status da página, tamanho do arquivo, etc.
* Defina e use uma [pesquisa salva](#saved-searches) - com base nos critérios acima.

>[!NOTE]
>
>A pesquisa também pode ser invocada usando a tecla de atalho `/` (barra) sempre que o painel de pesquisa estiver visível.

## Pesquisar e filtrar {#search-and-filter}

Para pesquisar e filtrar os recursos:

1. Abrir **Pesquisar** (com a lupa na barra de ferramentas) e insira o termo de pesquisa. As sugestões serão feitas e poderão ser selecionadas:

   ![screen_shot_2018-03-23at101404](assets/screen_shot_2018-03-23at101404.png)

   Por padrão, os resultados da pesquisa ficarão limitados à sua localização atual (ou seja, o console e o tipo de recurso relacionado): 

   ![screen_shot_2018-03-23at101445](assets/screen_shot_2018-03-23at101445.png)

1. Se necessário, é possível remover o filtro de localização (selecione **X** no filtro que deseja remover) para pesquisar em todos os consoles/tipos de recurso.
1. Os resultados serão mostrados, agrupados de acordo com o console e o tipo de recurso relacionado.

   Você pode selecionar um recurso específico (para a ação adicional) ou detalhar selecionando o tipo de recurso desejado; por exemplo, **Exibir todos os sites**: 

   ![screen_shot_2018-03-23at101523](assets/screen_shot_2018-03-23at101523.png)

1. Se desejar mais detalhes, selecione o símbolo do Painel (parte superior esquerda) para abrir o painel lateral **Filtros e opções**.

   ![](do-not-localize/screen_shot_2018-03-23at101542.png)

   De acordo com o tipo de recurso, a Pesquisa mostrará uma seleção predefinida de critérios de pesquisa/filtro.

   O painel lateral permite selecionar:

   * Pesquisas salvas
   * Diretório de pesquisa
   * Tags
   * Critérios de pesquisa; por exemplo, datas modificadas, status de publicação, status da Live Copy.

   >[!NOTE]
   >
   >Os critérios de pesquisa podem variar:
   >
   >* Dependendo do tipo de recurso selecionado; por exemplo, os critérios de Ativos e comunidades são compreensivelmente especializados.
   >* Sua instância como a [Pesquisar Forms](/help/sites-administering/search-forms.md) pode ser personalizada (adequada ao local no AEM).


   ![screen_shot_2018-03-23at101619](assets/screen_shot_2018-03-23at101619.png)

1. Você também pode adicionar outros termos de pesquisa:

   ![screen_shot_2018-03-23at101710](assets/screen_shot_2018-03-23at101710.png)

1. Feche a **Pesquisa** com o **X** (canto superior direito).

>[!NOTE]
>
>Os critérios de pesquisa persistem ao selecionar um item nos resultados da pesquisa.
>
>Quando você seleciona um item na página de resultados da pesquisa e retorna à página de pesquisa após usar o botão Voltar do navegador, os critérios de pesquisa permanecem.

## Pesquisas salvas {#saved-searches}

Além de pesquisar por uma grande variedade de aspectos, também é possível salvar uma configuração de pesquisa específica para recuperar e usar em um estágio posterior:

1. Defina seus critérios de pesquisa e selecione **Salvar**.

   ![screen_shot_2018-03-23at101710-1](assets/screen_shot_2018-03-23at101710-1.png)

1. Atribua um nome, em seguida, use **Salvar** para confirmar:

   ![screen_shot_2018-03-23at101852](assets/screen_shot_2018-03-23at101852.png)

1. Sua pesquisa salva estará disponível no seletor da próxima vez que você acessar o painel de pesquisa:

   ![screen_shot_2018-03-23at102128](assets/screen_shot_2018-03-23at102128.png)

1. Depois de salvo, você pode:

   * Use **x** (em comparação ao nome da pesquisa salva) para iniciar uma nova consulta (a própria pesquisa salva não será excluída).
   * **Editar pesquisa salva**, altere as condições de pesquisa e **Salvar** novamente.

As pesquisas salvas podem ser modificadas ao selecionar a pesquisa salva e clicar em **Editar pesquisa salva** na parte inferior do painel de pesquisa.

![screen_shot_2018-03-23at102213](assets/screen_shot_2018-03-23at102213.png)
