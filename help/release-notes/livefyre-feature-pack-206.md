---
title: Notas de versão do Livefyre Feature Pack 2.0.6
seo-title: Livefyre Feature Pack 2.0.6 Release Notes
description: Notas de versão do Livefyre Feature Pack 2.0.6
seo-description: Livefyre Feature Pack 2.0.6 Release Notes
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
exl-id: e09d2d59-41f0-4cf2-bcf3-ec3dbc3b8474
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# Notas de versão do Livefyre Feature Pack 2.0.6 {#livefyre-feature-pack-release-notes}

## Informações da versão {#release-information}

| Produtos | Livefyre Feature Pack 2.0.6 |
|--- |--- |
| Versão | 2.0.6 |
| Tipo | Versão de recurso |
| Data | 31 de agosto de 2018 |
| URL de download | Entre em contato com o administrador |
| Compatibilidade (*) | AEM 6.4 SP1, 6.4, 6.3 GA e 6.2 SP1 |
| Descrição | Esse pacote permite integrar os recursos de curadoria líderes do setor do Livefyre à sua instância do AEM, permitindo que você publique conteúdo valioso gerado pelo usuário (UGC) das redes sociais no seu site em minutos. |

## O que está incluído no Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Esse pacote integra os recursos de curadoria líderes do setor do Livefyre à sua instância do AEM, permitindo que você publique conteúdo valioso gerado pelo usuário (UGC) das redes sociais no seu site em minutos. Há três componentes diferentes para este pacote:

**Importar conteúdo UGC para o AEM Assets**

* Importe o conteúdo gerado pelo usuário (UGC) do Twitter e do Instagram do Livefyre Studio para o AEM Assets usando o Importador de UGC.
* Acesse sua biblioteca do Livefyre.
* Pesquise em tempo real no Twitter e no Instagram usando a Pesquisa do Livefyre Social.
* Gerenciar direitos no UGC.

**Adicionar componentes do Livefyre ao AEM Sites ou às comunidades**

* Crie e personalize instantaneamente experiências dinâmicas e envolventes usando um conjunto de componentes sociais, incluindo mapas, galerias e mural de mídia.
* Publique o UGC no AEM Sites ou nas Comunidades.

**Importar catálogos de produtos para o Livefyre com AEM Commerce**

* Integre facilmente seu catálogo de produtos existente ao Livefyre para impulsionar a participação e a conversão do usuário em seus sites, bem como fornecer experiências de UGC que podem ser compradas.
* Edite ou exclua itens no Catálogo de Produtos do Commerce do AEM e atualize automaticamente as alterações no Livefyre.

Para obter ajuda com a instalação, consulte [Integração com o Livefyre](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html).

### Informações adicionais sobre a versão {#additional-release-information}

Devido a atualizações que afetam a agregação de conteúdo de contas de usuários não empresariais do Instagram, não podemos mais postar comentários em seu nome ou verificar automaticamente as respostas do autor. [Clique aqui para saber mais](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>O Livefyre Feature Pack 2.0.6 não é compatível com AEM interface de usuário clássica.

#### Novo recurso ou melhoria {#new-feature-or-improvement}

* Adição da capacidade de pesquisar UGC antes de configurar direitos solicitar contas sociais no Livefyre. Você deve configurar contas sociais para solicitar direitos ou substituir a solicitação de direitos se você for o proprietário do conteúdo.
* Instagram e Twitter [Fluxo de trabalho de solicitação de direitos UGC](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html) O foi atualizado para estar em conformidade com as APIs mais recentes.
* O status dos direitos e as ações apropriadas são exibidos agora na tela de solicitação de direitos.

#### Correções de erros {#bug-fixes}

* Correção de um problema em que a exclusão de uma conta social no Livefyre Studio usada para solicitação de direitos causava um erro ao carregar a biblioteca UGC no AEM.
* Correção de um problema em que a contagem de ativos no estúdio do Livefyre não correspondia à contagem de ativos na biblioteca UGC AEM.
* Correção de um problema na biblioteca UGC em que os resultados filtrados eram exibidos após as opções de filtro serem redefinidas.
* Correção de um problema com AEM Commerce, em que os botões de chamada para ação redirecionavam os usuários para o URL incorreto.
* Correção de um problema no AEM Sites em que arrastar e soltar vários componentes no espaço reservado parsys fazia com que desaparecessem.
* Correção de um problema em que as contas sociais desativadas estavam disponíveis para seleção ao enviar uma solicitação de direitos.
* Correção de um problema em que arrastar e soltar o UGC dos Ativos no Sites gerava um erro.
* Correção de um problema em que arrastar e soltar componentes Chat e Liveblog no Sites não criava o aplicativo.
* Correção de um problema em que o Aplicativo de comentário gerava um erro quando os usuários tentavam fazer comentários.
* Correção de um problema em que a adição do Livefyre Media Wall App a um site criava um nó adicional no Java Content Repository.
* Correção de um problema que causava quebras de página e erros de console na pesquisa UGC do Instagram.
* Correção de um problema em que os ícones do usuário do Instagram geravam erros de API no Assets.
* Correção de um problema em que o aplicativo Revisões estava sendo adicionado a um site sem formato predefinido.
* Correção de um problema com a funcionalidade da interface do usuário de toque e a edição em linha.
* Correção de um problema que causava um erro ao importar determinados ativos de imagem do Instagram.
* Correção de um problema em que o Cliente HTTP Livefyre no AEM não suportava a configuração de proxy.
