---
title: Problemas conhecidos no AEM 6.4
seo-title: Problemas conhecidos no AEM 6.4
description: Problemas conhecidos no Adobe Experience Manager 6.4
seo-description: Problemas conhecidos na Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
translation-type: tm+mt
source-git-commit: 55b9105fab3947322649c7ed2b750497e486ec63
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 4%

---


# Problemas conhecidos {#known-issues}

Esta página mantém uma lista dos problemas conhecidos Adobe Experience Manager 6.4 lançados em abril de 2018. Para obter mais informações sobre problemas conhecidos, [entre em contato com o suporte](https://helpx.adobe.com/br/support/experience-manager.html).

## Dispositivos híbridos {#hybrid-devices}

Dispositivos híbridos não são suportados. Vários problemas podem ser encontrados ao usar esses dispositivos. Os procedimentos sugeridos a seguir ajudam a resolver muitos problemas:

Se você estiver usando o Google Chrome como navegador:
* Digite `chrome://flags/` na barra de endereços e pressione Enter.
* Clique em Ativar eventos de toque > Desativado.
* Reinicie o navegador (todas as guias e janelas).

Se você estiver usando o Mozilla Firefox como navegador:
* Digite `about:config` na barra de endereços e pressione Enter.
* Filtre as configurações para `dom.w3c`.
* Verifique se as configurações estão `0` e `false`.
* Reinicie o navegador.

Se você estiver usando o Microsoft Edge como navegador:

* Digite `about:flags` na barra de endereços e pressione Return.
* Role até Recursos experimentais e depois **[!UICONTROL Toque]**.
* Clique em **[!UICONTROL Ativar eventos]** de toque.
* Selecione **[!UICONTROL Sempre Desligar]**.
* Reinicie o navegador.

## Plataforma {#platform}

* **Painel de operações:** A barra de progresso não é exibida quando a extensão .zip do arquivo de backup está ausente. (GRANITE-10713)
* **HTL:** O objeto Java Use com espaço em branco à direita na declaração do pacote congela o SightlyJavaCompilerService (GRANITE-20836)
* **Apache Felix/Sling:** O arquivo de configuração ainda está presente no repositório mesmo depois de configuration.delete() (GRANITE-20618)
* **Configurações da nuvem:** O console é quebrado após a edição do container de configuração (GRANITE-20726)
* **Segurança:** A integração do IMS falha com o caminho de contexto personalizado (GRANITE-20639)
* **Segurança:** Melhore a classificação padrão JAAS de SSO, módulos de logon externos e padrão (GRANITE-20590)
* **Ferramentas - CRX DE Lite:** A visualização de propriedades continua subindo (GRANITE-12040)
* **Ferramentas - CRX DE Lite:** Não é possível salvar alterações em Tipos de Valor &quot;Longo&quot;, a menos que você clique com o duplo no Nome da Propriedade (GRANITE-12351)

* **Ferramentas - CRX DE Lite:** a pesquisa ctrl+F em arquivos de texto aberto fica travada na pesquisa RegExp (GRANITE-5996)

* **Ferramentas - CRX DE Lite:** Propriedade de nó não exibida após renomear o nó (GRANITE-7160)
* **IU:** Pulldown &quot;mais...&quot; não mostra todos os elementos quando abertos em um elemento de portátil no IE e no Firefox (GRANITE-16326)
* **IU:** A dica de ferramenta Informações fica oculta ao usar o layout de colunas fixas com 2 colunas lado a lado (GRANITE-16869)
* **IU:** Erro não tratado ao representar como um usuário que não existe (GRANITE-23228). Solução ao [implementar um manipulador](/help/sites-developing/customizing-errorhandler-pages.md) de erros para personalizar a mensagem de erro.

* **Omnisearch:** Pesquisas com exceção de causa de barra invertida (GRANITE-11769)
* **Omnisearch:** Abra &quot;Configurações de Visualização&quot; na visualização da lista para fazer com que o filtro de pesquisa mude (GRANITE-16524)
* **Omnisearch:** lista incorreta das configurações de coluna mostradas ao fazer a pesquisa de Ativos a partir de Sites (GRANITE-16527)

* **Omnisearch:** Os predicados do painel esquerdo estão acompanhando a solicitação do servidor Omnisearch (GRANITE-20524)
* **Omnisearch:** O Omnisearch não suporta caminhos de contexto (GRANITE-16044)

## Ativos {#assets}

* **Pesquisar**: A pesquisa não retornará nenhum resultado se a string de pesquisa for start com um espaço em branco [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Pesquisar**: Na interface clássica e as tags não estão visíveis na pesquisa (CQ-4235239)

* **IU**: A interface do usuário do ativo não responde após Copiar-Colar e Selecionar tudo (CQ-4236142)

* **IU**: Não é possível mover ativos após o carregamento lento (CQ-4236134)

* **Relatórios**: Erro na criação do relatório de modificação de ativos (CQ-4239744)

* **Relatórios**: A geração regular de relatórios de Ativo falha inconsistentemente (alguns relatórios permanecem na fila) (CQ-4239089)

* **Metadados**: Ao adicionar um campo de texto de vários valores ao schema do ativo, a regra de cascata de campos obrigatórios não funciona (CQ-4239333)

* **BrandPortal**: Publicar no BrandPortal não está funcionando para coleções (CQ-4238731)

* **Carregar**: Ao carregar ativos com caracteres especiais no nome do arquivo, a mensagem de erro de validação sobre os caracteres não permitidos não é exibida para cada ativo. Embora seja exibido somente para o primeiro ativo, a interface indica claramente ao usuário que o nome de arquivo do ativo fornecido não é permitido. (CQ-4256876)

## Communities {#communities}

* **Moderação** - Não é possível excluir a publicação-pai como uma única operação de exclusão da interface do usuário de moderação em massa (CQ-4236797)

* **Console** - o link Esqueceu o nome de usuário ou a senha está sendo redirecionado para a Página de logon em vez do formulário de recuperação de senha correspondente (CQ-4237682)

## Forms {#forms}

### Instalação e implantação

* (Somente JEE do AEM Forms) Ao inicializar o servidor de aplicativos JBoss durante a execução do Configuration Manager, retorna erros de invocação e inicialização do EJB. Entretanto, você pode ignorá-los. (Ref# CQ-4229793)
* Quando o AEM Forms for iniciado, o `SAX Security Manager could not be setup` aviso será exibido. (CQ-4297403)

### Comunicações interativas

* A interface do usuário do agente demora algum tempo para carregar as Comunicações interativas que incluem elementos de gráfico ou imagem. (CQ-4236630)
* O formato de exibição de dados na pré-visualização de impressão é dd-mm-aaaa enquanto na pré-visualização da Web é `dd-mmm-yy` (CQ-4237045)
* O canal da Web Interative Communication suporta apenas listas ordenadas e não ordenadas. Em fragmentos de documento de lista, a listagem e o recuo compostos não são suportados para o canal da Web da Comunicação Interativa. (CQ-4233672)
* Os seguintes problemas são observados quando o canal da Web é sincronizado com o canal de impressão:

   * O canal da Web leva algum tempo para sincronizar ao mudar do canal de impressão pela primeira vez.
   * O canal da Web não será sincronizado se o canal de impressão incluir um componente gráfico não configurado. Para resolver o problema, exclua o componente de gráfico e sincronize novamente.
   * Às vezes, a sincronização falha com o erro &quot;Ocorreu um erro ao sincronizar a Live Copy&quot;. Para resolver o problema, atualize a página.
   * O texto estático em um fragmento de layout é substituído pelo nome da célula da tabela quando a primeira coluna da tabela é uma coluna de cabeçalho no modelo de canal de impressão.
   * Não é possível adicionar componentes ou ativos em nenhum local além da parte inferior de uma comunicação de canal da Web. Para colocá-lo em outro local, adicione um painel na parte inferior do canal da Web e reorganize usando a árvore de conteúdo.
   * É possível mover o conteúdo para a área de público alvo herdada do canal da Web sem remover a herança da cópia ativa.

(CQ-4239780)

### Integração de dados

* As configurações de autenticação para serviços da Web baseados em SOAP não estão visíveis e, portanto, não podem ser configuradas nos serviços em nuvem. Para resolver o problema:

   1. No console CRXDE Lite, vá para o seguinte nó.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigWizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Atualize o valor da propriedade value para o mesmo valor da propriedade text.
   1. Clique em Salvar tudo para salvar a configuração.

(CQ-4238462)

### Integração com o Adobe Sign

* O scheduler Adobe Sign para de funcionar intermitentemente e, portanto, os formulários pendentes de assinatura não são movidos para envio. Para resolver o problema, reinicie o pacote de suporte **ao Scheduler Apache Sling do console da Web do AEM em https://** server [*:*] port [**]/system/console/bundles.

### Criação de formulários adaptáveis

* O componente Gráfico em formulários adaptáveis ocupa mais espaço do que normalmente.
* Uma exceção é retornada ao salvar propriedades para formulários adaptáveis, fragmentos de formulário adaptáveis ou comunicações interativas na interface do usuário do Forms Manager.
* O número máximo de caracteres especificado para uma caixa de texto de formulário adaptável não é respeitado em dispositivos Android 6.0 Samsung. (Ref# CQ-4235205)
