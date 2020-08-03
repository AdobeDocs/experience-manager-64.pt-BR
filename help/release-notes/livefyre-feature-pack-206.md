---
title: Notas de versão do Livefyre Feature Pack 2.0.6
seo-title: Notas de versão do Livefyre Feature Pack 2.0.6
description: Notas de versão do Livefyre Feature Pack 2.0.6
seo-description: Notas de versão do Livefyre Feature Pack 2.0.6
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---


# Notas de versão do Livefyre Feature Pack 2.0.6 {#livefyre-feature-pack-release-notes}

## Informações da versão {#release-information}

| Produtos | Livefyre Feature Pack 2.0.6 |
|--- |--- |
| Versão | 2.0.6 |
| Tipo | Versão do recurso |
| Data | 31 de agosto de 2018 |
| URL de download | Entre em contato com o administrador |
| Compatibilidade (*) | AEM 6.4 SP1, 6.4, 6.3 GA e 6.2 SP1 |
| Descrição | Este pacote permite integrar os recursos de curadoria líderes do setor do Livefyre à sua instância de AEM, permitindo que você publique conteúdo valioso gerado pelo usuário (UGC) das redes sociais para seu site em minutos. |

## Qual a composição de Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Este pacote integra os recursos de curadoria líderes do setor do Livefyre à sua instância de AEM, permitindo que você publique conteúdo valioso gerado pelo usuário (UGC) das redes sociais para seu site em minutos. Há três componentes diferentes para este pacote:

**Importar conteúdo UGC para AEM Assets**

* Importe o conteúdo gerado pelo usuário (UGC) do Twitter e do Instagram do Livefyre Studio para o AEM Assets usando o Importador UGC.
* Acesse sua biblioteca do Livefyre.
* Pesquise em tempo real no Twitter e no Instagram usando o Livefyre Social Search.
* Gerenciar direitos no UGC.

**Adicionar componentes do Livefyre a AEM Sites ou comunidades**

* Crie e personalize instantaneamente experiências dinâmicas e envolventes usando um conjunto de componentes sociais, incluindo Mapas, Galerias e Muros de Mídia.
* Publicar UGC em AEM Sites ou comunidades.

**Importar catálogos de produtos para o Livefyre com comércio AEM**

* Integre facilmente seu catálogo de produtos existente ao Livefyre para incentivar o envolvimento e a conversão dos usuários em seus sites, além de fornecer experiências UGC que podem ser compradas.
* Edite ou exclua itens no Catálogo de produtos de comércio AEM e atualize automaticamente as alterações no Livefyre.

Para obter ajuda com a instalação, consulte [Integração com o Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html).

### Informações adicionais sobre a versão {#additional-release-information}

Devido a atualizações que afetam a agregação de conteúdo de contas de usuários não comerciais do Instagram, não podemos mais postar comentários em seu nome ou verificar automaticamente as respostas do autor. [Clique aqui para saber mais](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>O Livefyre Feature Pack 2.0.6 não suporta AEM interface clássica.

#### Novo recurso ou melhoria {#new-feature-or-improvement}

* Foi adicionada a capacidade de pesquisar UGC antes de configurar direitos para solicitar contas sociais no Livefyre. É necessário configurar contas sociais para solicitar direitos ou substituir a solicitação de direitos se você for o proprietário do conteúdo.
* O fluxo de trabalho [de solicitação de direitos](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html) UGC do Instagram e do Twitter foi atualizado para estar em conformidade com as APIs mais recentes.
* O status dos direitos e as ações apropriadas agora são exibidos na tela de solicitação de direitos.

#### Correções de erros {#bug-fixes}

* Correção de um problema em que a exclusão de uma conta social no Livefyre Studio usada para solicitação de direitos causava um erro ao carregar a biblioteca UGC no AEM.
* Correção de um problema em que a contagem de ativos no estúdio Livefyre não correspondia à contagem de ativos na biblioteca UGC AEM.
* Correção de um problema na biblioteca UGC em que os resultados filtrados eram exibidos após as opções de filtro serem redefinidas.
* Correção de um problema com Comércio AEM em que os botões de chamada para ação redirecionavam os usuários para o URL incorreto.
* Correção de um problema em AEM Sites em que arrastar e soltar vários componentes no espaço reservado parsys fazia com que ele desaparecessem.
* Correção de um problema em que as contas sociais desativadas estavam disponíveis para seleção ao enviar uma solicitação de direitos.
* Correção de um problema em que arrastar e soltar UGC de Ativos em Sites gerava um erro.
* Correção de um problema em que arrastar e soltar componentes de Bate-papo e Liveblog em Sites não criava o aplicativo.
* Correção de um problema em que o aplicativo Comentário gerava um erro quando os usuários tentavam comentar.
* Corrigido um problema no qual a adição do aplicativo Livefyre Media Wall a um site criava um nó extra no repositório de conteúdo Java.
* Corrigido um problema que causava quebras de página e erros de console na pesquisa do Instagram UGC.
* Correção de um problema em que os ícones de usuário do Instagram geravam erros de API no Assets.
* Correção de um problema em que o aplicativo Revisões estava sendo adicionado a um site sem formato predefinido.
* Correção de um problema com a funcionalidade de interface de usuário de toque e edição em linha.
* Correção de um problema que causava um erro ao importar determinados ativos de imagem do Instagram.
* Correção de um problema em que o Livefyre HTTP Client no AEM não suportava a configuração de proxy.
