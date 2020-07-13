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
source-git-commit: f1bf1545689b977a0f5074954df224db58cbd695
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 4%

---


# Notas de versão do Livefyre Feature Pack 2.0.6 {#livefyre-feature-pack-release-notes}

## Informações da versão {#release-information}

<table> 
 <tbody>
  <tr>
   <td>Produtos</td> 
   <td>Livefyre Feature Pack 2.0.6</td> 
  </tr>
  <tr>
   <td>Versão</td> 
   <td>2.0.6</td> 
  </tr>
  <tr>
   <td>Tipo</td> 
   <td>Versão do recurso</td> 
  </tr>
  <tr>
   <td>Data</td> 
   <td>31 de agosto de 2018</td> 
  </tr>
  <tr>
   <td>URL de download<br /> </td> 
   <td>Entre em contato com o administrador</td> 
  </tr>
  <tr>
   <td>Compatibilidade (*)</td> 
   <td>AEM 6.4 SP1, 6.4, 6.3 GA e 6.2 SP1</td> 
  </tr>
  <tr>
   <td>Descrição</td> 
   <td>Este pacote permite integrar os recursos de curadoria líderes do setor do Livefyre à sua instância do AEM, permitindo que você publique conteúdo valioso gerado pelo usuário (UGC) das redes sociais para seu site em minutos.</td> 
  </tr>
 </tbody>
</table>

## Qual a composição de Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Este pacote integra os recursos de curadoria líderes do setor do Livefyre à sua instância do AEM, permitindo que você publique conteúdo valioso gerado pelo usuário (UGC) das redes sociais para seu site em minutos. Há três componentes diferentes para este pacote:

**Importar conteúdo UGC para AEM Assets**

* Importe o conteúdo gerado pelo usuário (UGC) do Twitter e do Instagram do Livefyre Studio para o AEM Assets usando o Importador UGC.
* Acesse sua biblioteca do Livefyre.
* Pesquise em tempo real no Twitter e no Instagram usando o Livefyre Social Search.
* Gerenciar direitos no UGC.

**Adicionar componentes do Livefyre a AEM Sites ou comunidades**

* Crie e personalize instantaneamente experiências dinâmicas e envolventes usando um conjunto de componentes sociais, incluindo Mapas, Galerias e Muros de Mídia.
* Publicar UGC em AEM Sites ou comunidades.

**Importar catálogos de produtos para o Livefyre com o AEM Commerce**

* Integre facilmente seu catálogo de produtos existente ao Livefyre para incentivar o envolvimento e a conversão dos usuários em seus sites, além de fornecer experiências UGC que podem ser compradas.
* Edite ou exclua itens no Catálogo de produtos do AEM Commerce e atualize automaticamente as alterações no Livefyre.

Para obter ajuda com a instalação, consulte [Integração com o Livefyre](https://helpx.adobe.com/br/experience-manager/6-4/sites/administering/using/livefyre.html).

### Informações adicionais sobre a versão {#additional-release-information}

Devido a atualizações que afetam a agregação de conteúdo de contas de usuários não comerciais do Instagram, não podemos mais postar comentários em seu nome ou verificar automaticamente as respostas do autor. [Clique aqui para saber mais](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>O Livefyre Feature Pack 2.0.6 não é compatível com a interface do usuário do AEM Classic.

#### Novo recurso ou melhoria {#new-feature-or-improvement}

* Foi adicionada a capacidade de pesquisar UGC antes de configurar direitos para solicitar contas sociais no Livefyre. É necessário configurar contas sociais para solicitar direitos ou substituir a solicitação de direitos se você for o proprietário do conteúdo.
* O fluxo de trabalho [de solicitação de direitos](https://helpx.adobe.com/br/experience-manager/6-4/sites/administering/using/livefyre.html) UGC do Instagram e do Twitter foi atualizado para estar em conformidade com as APIs mais recentes.
* O status dos direitos e as ações apropriadas agora são exibidos na tela de solicitação de direitos.

#### Correções de erros {#bug-fixes}

* Correção de um problema em que a exclusão de uma conta social no Livefyre Studio usada para solicitação de direitos causava um erro ao carregar a biblioteca UGC no AEM.
* Correção de um problema em que a contagem de ativos no estúdio Livefyre não correspondia à contagem de ativos na biblioteca UGC do AEM.
* Correção de um problema na biblioteca UGC em que os resultados filtrados eram exibidos após as opções de filtro serem redefinidas.
* Correção de um problema com o AEM Commerce, no qual os botões de chamada para ação redirecionavam os usuários para o URL incorreto.
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

