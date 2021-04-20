---
title: Trabalhar com o componente Sites 3D
seo-title: Trabalhar com o componente Sites 3D
description: AEM 3D inclui um componente AEM Sites que pode ser usado para implementar a visualização interativa de modelos 3D em páginas da Web.
seo-description: AEM 3D inclui um componente AEM Sites que pode ser usado para implementar a visualização interativa de modelos 3D em páginas da Web.
uuid: 4f06bab3-1e31-49ef-89e3-b26195966538
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 9017ab55-6d4a-4306-922f-223ab1b2504b
exl-id: bf87b470-08c8-44b4-95d9-1251586b0610
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 0%

---

# Trabalhar com o componente Sites 3D {#working-with-the-d-sites-component}

AEM 3D inclui um componente AEM Sites que pode ser usado para implementar a visualização interativa de modelos 3D em páginas da Web.

Depois de ter adicionado seu componente 3D, você pode [visualizar o ativo 3D nesse componente.](viewing-3d-assets.md)

## Adicionar o componente 3D ao modelo de página {#adding-the-d-component-to-the-page-template}

Você deve ativar o componente 3D na página antes de colocá-lo em uma página. Consulte [Edição de modelos](/help/sites-authoring/templates.md#editing-a-template-layout-template-author) para obter informações detalhadas sobre como ativar componentes em modelos.

**Adicionar o componente 3D ao modelo** de página:

1. Navegue até **[!UICONTROL Ferramentas > Geral > Modelos]**.

1. Navegue até o modelo de página no qual você deseja ativar o componente 3D e selecione o modelo.

1. Toque em **[!UICONTROL Editar]** para abrir o modelo.
1. Próximo ao canto superior direito da página, no menu suspenso, selecione o modo **[!UICONTROL Estrutura]**, se ele ainda não estiver ativo.

   ![image2017-11-14_15-33-57](assets/image2017-11-14_15-33-57.png)

1. Toque na região **[!UICONTROL Contêiner de layout]** para selecioná-lo.

1. Toque no botão **[!UICONTROL Policy]** para abrir o **[!UICONTROL Policy Editor]**.
1. Na seção **[!UICONTROL Properties]**, selecione a marca de seleção **[!UICONTROL 3D]** e toque em **[!UICONTROL Concluído]** para salvar as alterações e fechar o **[!UICONTROL Editor de Políticas]**.

   Agora é possível colocar o componente Sites 3D em todas as páginas que usam esse modelo.

## Adicionar o componente visualizador 3D a uma página da Web {#adding-the-d-viewer-component-to-a-web-page}

>[!CAUTION]
>
>Essa versão do AEM 3D suporta apenas uma instância do componente 3D em cada página da Web. Vários componentes 3D na mesma página não funcionam corretamente.

**Para adicionar o componente visualizador 3D a uma página** da Web:

1. Abra o AEM Sites e selecione a página da Web à qual deseja adicionar o componente 3D.

1. Toque no ícone **[!UICONTROL Editar]** (lápis) para abrir a página no editor de páginas. Verifique se o modo **[!UICONTROL Edit]** próximo à parte superior direita da página está selecionado.

   ![image2017-11-14_15-44-40](assets/image2017-11-14_15-44-40.png)

1. Toque no seletor do painel para abrir o painel lateral.

1. Toque no ícone de sinal de mais para abrir a lista **[!UICONTROL Componentes]**.

1. Arraste o componente **[!UICONTROL 3D Viewer]** da lista **[!UICONTROL Components]** para o local na página onde deseja que o visualizador 3D apareça.

## Configurar o componente 3D {#configuring-the-d-component}

1. No editor de páginas do AEM Sites, selecione o componente **[!UICONTROL Visualizador 3D]** que você adicionou anteriormente à página.

1. Toque no ícone **[!UICONTROL Configuração]** (chave) para abrir a caixa de diálogo de configuração do componente.

   É possível definir as seguintes propriedades de componentes:

   <table> 
    <tbody> 
    <tr> 
    <td>Propriedade</td> 
    <td>Descrição</td> 
    <td>Aplicabilidade</td> 
    </tr> 
    <tr> 
    <td>Altura (px)</td> 
    <td>Especifique a altura desejada do componente 3D em pixels. Se deixado em branco, o padrão será 600 pixels.</td> 
    <td> </td> 
    </tr> 
    <tr> 
    <td>Nome do palco</td> 
    <td><p>Selecione um Estágio 3D na lista de estágios disponíveis. O palco fornece fundo e iluminação.</p> <p>Consulte <a href="/help/assets/about-the-use-of-stages-in-aem-3d.md" target="_blank">Sobre o uso de palcos AEM Sites 3D</a>.</p> </td> 
    <td>Ignorado para ativos do Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Velocidade de rotação automática (RPM)</td> 
    <td><p>O visualizador 3D orbita a câmera continuamente após carregar e redefinir. A rotação automática termina quando o usuário inicia uma ação de órbita manual.</p> <p>Você pode especificar a velocidade de rotação em RPM usando os seguintes valores:</p> 
        <ul> 
        <li>Definir um valor positivo para girar à direita</li> 
        <li>Definir um valor negativo para girar para a esquerda</li> 
        <li>Defina um valor 0 para desativar a rotação automática.</li> 
        </ul> <p>O padrão é 3 RPM, o equivalente a 20 segundos por revolução completa.<br /> <br /> <strong>Observação:</strong> a velocidade de rotação assume uma taxa de quadros de 60/s. Normalmente, essa taxa é alcançada com modelos pequenos a moderadamente em hardware gráfico mais potente. Modelos maiores ou dispositivos mais lentos giram automaticamente em taxas mais baixas.</p> </td> 
    <td>Ignorado para ativos do Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Cor do botão de navegação</td> 
    <td>Use o seletor de cores para escolher a cor primária para os botões de controle do visualizador.</td> 
    <td>Ignorado para ativos do Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Cor do focalizador da navegação</td> 
    <td>Use o seletor de cores para escolher a cor de focalização/selecionada para os botões de controle do visualizador.</td> 
    <td>Ignorado para ativos do Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Mostrar amostras</td> 
    <td>Para uso futuro.</td> 
    <td>Ignorado para ativos do Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Mostrar predefinições da câmera GLTF</td> 
    <td>Mostre ou oculte as predefinições da câmera que podem estar presentes nos ativos do Adobe Dimension.</td> 
    <td>Somente para ativos Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Cor do fundo GLTF</td> 
    <td>Cor de plano de fundo padrão se o modelo 3D não incluir um plano de fundo.</td> 
    <td>Somente para ativos Adobe Dimension.</td> 
    </tr> 
    </tbody> 
   </table>

1. Toque na marca de seleção para salvar as alterações.

   Além das configurações disponíveis na caixa de diálogo de configuração do componente, há várias configurações globais disponíveis que podem ser modificadas por meio do CRXDE Lite.
Consulte [Configurações avançadas](advanced-config-3d.md) para obter informações detalhadas sobre essas configurações globais.

## Atribuir um modelo 3D ao componente {#assigning-a-d-model-to-the-component}

1. No editor de páginas do AEM Sites, clique no ícone **[!UICONTROL Assets]** para abrir a lista Ativos no painel lateral.

1. Selecione o filtro **[!UICONTROL Modelos 3D]** para ocultar tipos de ativos indesejados.

   ![screen_shot_2017-12-11at124258](assets/screen_shot_2017-12-11at124258.png)

1. Procure ou role até o ativo 3D que deseja visualizar na página que está sendo editada.

1. Arraste o ativo 3D da lista **[!UICONTROL Assets]** para o componente **[!UICONTROL Visualizador 3D]** colocado anteriormente na página.

   Os ativos Adobe Dimension são renderizados usando a nova tecnologia de visualizador baseada no padrão aberto glTF, enquanto todos os outros tipos de ativos 3D dependem do visualizador webGL clássico AEM 3D. O componente seleciona automaticamente o visualizador apropriado com base no tipo de modelo 3D.

## Visualização de uma página da Web que tenha um componente 3D {#previewing-a-web-page-that-has-a-d-component}

Embora a página da Web esteja no modo **[!UICONTROL Edit]**, o componente 3D exibe o modelo 3D, mas nenhuma interação com o modelo é possível.

Você pode visualizar a página da Web no editor de páginas com acesso total à funcionalidade do componente 3D.

Consulte também [Visualização de ativos 3D no componente 3D do Sites](viewing-3d-assets.md#viewing-d-assets-in-the-sites-d-component).

**Para visualizar uma página da Web que tenha um componente** 3D:

1. Siga um destes procedimentos:

   * Próximo ao canto superior direito da página, clique em **[!UICONTROL Preview]** para entrar no modo de visualização.
   * Exclua `/edit.html` do URL da página no navegador.

## Publicar a página e os ativos {#publishing-the-page-and-assets}

Consulte [Publicação de ativos](managing-assets-touch-ui.md) para obter informações sobre como publicar ativos. Consulte [Publicação de páginas](/help/sites-authoring/publishing-pages.md) para obter informações sobre como publicar páginas.

>[!NOTE]
>
>Usar o item de menu **[!UICONTROL Publicar página]** no menu **[!UICONTROL Informações da página]** publicará a página e todas as dependências de página primárias. As dependências secundárias que podem ser referenciadas pelo modelo 3D e/ou pelo estágio 3D, como mapas de textura e imagens IBL, não são publicadas quando você publica a página dessa maneira.
>
>O Adobe recomenda que você publique todos os ativos 3D e suas dependências diretamente do AEM Assets, antes de publicar a página da Web que faz referência a esses ativos.
