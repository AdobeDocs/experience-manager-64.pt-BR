---
title: Problemas conhecidos no AEM 6.4
seo-title: Known Issues in AEM 6.4
description: Problemas conhecidos no Adobe Experience Manager 6.4
seo-description: Known Issues in Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
exl-id: ba65e853-d69a-4341-93c3-5628c60c403b
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 4%

---

# Problemas conhecidos {#known-issues}

Esta página mantém uma lista de problemas conhecidos lançados pelo Adobe Experience Manager 6.4 em abril de 2018. Para obter mais informações sobre problemas conhecidos, [entrar em contato com o suporte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=pt-BR).

## Dispositivos híbridos {#hybrid-devices}

Dispositivos híbridos não são compatíveis. Vários problemas podem ser encontrados ao usar esses dispositivos. Os seguintes procedimentos sugeridos ajudam a resolver muitos problemas:

Se estiver usando o Google Chrome como navegador:

* Tipo `chrome://flags/` na barra de endereços e pressione Enter.
* Clique em Ativar eventos de toque > Desativado.
* Reinicie o navegador (todas as guias e janelas).

Se você estiver usando o Mozilla Firefox como navegador:

* Tipo `about:config` na barra de endereços e pressione Enter.
* Filtre as configurações para `dom.w3c`.
* Verifique se as configurações estão `0` e `false`.
* Reinicie o navegador.

Se estiver usando o Microsoft Edge como navegador:

* Tipo `about:flags` na barra de endereços e pressione Return (Retornar).
* Role até Recursos experimentais e, em seguida, **[!UICONTROL Toque]**.
* Clique em **[!UICONTROL Ativar eventos de toque]**.
* Selecionar **[!UICONTROL Sempre desligado]**.
* Reinicie o navegador.

## Plataforma {#platform}

* **Painel de operações:** A barra de progresso não é mostrada quando a extensão .zip do arquivo de backup está ausente. (GRANITE-10713)
* **HTL:** O objeto Java Use com espaço em branco à direita na declaração do pacote congela o SightlyJavaCompilerService (GRANITE-20836)
* **Apache Felix/Sling:** O arquivo de configuração ainda está presente no repositório mesmo após configuration.delete() (GRANITE-20618)
* **Configurações da nuvem:** O console é interrompido após a edição do contêiner de configuração (GRANITE-20726)
* **Segurança:** A integração IMS falha com o caminho de contexto personalizado (GRANITE-20639)
* **Segurança:** Melhore a classificação padrão do JAAS de SSO, Módulos de logon externo e padrão (GRANITE-20590)
* **Ferramentas - CRX DE Lite:** A faixa de exibição de propriedades continua em movimento (GRANITE-12040)
* **Ferramentas - CRX DE Lite:** Não é possível salvar alterações em Tipos de Valor &quot;Longo&quot;, a menos que você clique duas vezes em Nome da Propriedade (GRANITE-12351)

* **Ferramentas - CRX DE Lite:** a pesquisa ctrl+F em arquivos de texto abertos fica presa na pesquisa RegExp (GRANITE-5996)

* **Ferramentas - CRX DE Lite:** Propriedade de nó não exibida após renomear o nó (GRANITE-7160)
* **IU:** Lista suspensa &quot;mais...&quot; não mostra todos os elementos quando abertos em um elemento de portátil no IE e no Firefox (GRANITE-16326)
* **IU:** A dica de ferramenta Informações fica oculta ao usar o layout de colunas fixas com 2 colunas lado a lado (GRANITE-16869)
* **IU:** Erro não tratado ao representar como um usuário que não existe (GRANITE-23228). Solução alternativa por [implementação de um manipulador de erros](/help/sites-developing/customizing-errorhandler-pages.md) para personalizar a mensagem de erro.

* **Omnisearch:** Pesquisas com exceção de causa de barra invertida (GRANITE-11769)
* **Omnisearch:** Abra &quot;Configurações de exibição&quot; na exibição de lista para fazer com que o filtro de pesquisa mude (GRANITE-16524)
* **Omnisearch:** Lista incorreta de configurações de coluna mostradas ao fazer a pesquisa de Ativos a partir do Sites (GRANITE-16527)

* **Omnisearch:** Os predicados do painel esquerdo estão sendo acompanhados pela solicitação do servidor Omnisearch (GRANITE-20524)
* **Omnisearch:** O Omnisearch não suporta caminhos de contexto (GRANITE-16044)

## Assets {#assets}

* **Pesquisar**: A pesquisa não retornará nenhum resultado se a string de pesquisa começar com um espaço em branco [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Pesquisar**: Na interface clássica e as tags não estão visíveis na pesquisa (CQ-4235239)

* **interface**: A interface do usuário do ativo fica sem resposta após Copiar-Colar e Selecionar tudo (CQ-4236142)

* **interface**: Não é possível Mover ativos após o carregamento lento (CQ-4236134)

* **Relatórios**: Erro na criação do Relatório de modificação de ativos (CQ-4239744)

* **Relatórios**: Geração agendada e regular de relatórios de Ativos falha inconsistentemente (alguns relatórios permanecem na fila) (CQ-4239089)

* **Metadados**: Ao adicionar campo de texto de vários valores ao esquema Ativo, a regra de cascata de campo obrigatório não funciona (CQ-4239333)

* **BrandPortal**: Publicar no BrandPortal não está funcionando para coleções (CQ-4238731)

* **Upload**: Ao fazer upload de ativos com caracteres especiais no nome do arquivo, a mensagem de erro de validação sobre os caracteres não permitidos não é exibida para cada ativo. Embora seja exibido somente para o primeiro ativo, a interface indica claramente ao usuário que o nome de arquivo do ativo fornecido não é permitido. (CQ-4256876)

## Communities {#communities}

* **Moderação** - Não é possível excluir a publicação-pai como uma única operação de exclusão da interface do usuário de moderação em massa (CQ-4236797)

* **Console** - Esqueceu o nome de usuário ou o link Senha está redirecionando para a Página de logon em vez do formulário de recuperação de senha correspondente (CQ-4237682)

## Forms {#forms}

### Instalação e implantação

* (Somente AEM Forms JEE) Ao inicializar o servidor de aplicativos JBoss durante a execução do Configuration Manager, retorna erros de falha de invocação e inicialização de EJB. No entanto, você pode ignorá-los. (Ref# CQ-4229793)
* Quando o AEM Forms for iniciado, a variável `SAX Security Manager could not be setup` for exibido. (CQ-4297403)

### Comunicações interativas

* A interface do usuário do agente leva algum tempo para carregar as Comunicações interativas que incluem elementos de gráfico ou imagem. (CQ-4236630)
* O formato de exibição de dados na visualização de impressão é dd-mm-aaaa enquanto na visualização da Web é `dd-mmm-yy` (CQ-4237045)
* O canal Web de Comunicação Interativa suporta apenas listas ordenadas e não ordenadas. Em fragmentos de documento de lista, a listagem composta e o recuo não são compatíveis com o canal da Web da Comunicação interativa. (CQ-4233672)
* Os seguintes problemas são observados quando o canal da Web é sincronizado com o canal de impressão:

   * O canal da Web leva algum tempo para sincronizar ao alternar do canal de impressão pela primeira vez.
   * O canal da Web não sincroniza se o canal de impressão incluir um componente de gráfico não configurado. Para resolver o problema, exclua o componente de gráfico e sincronize novamente.
   * A sincronização às vezes falha com o erro &quot;Ocorreu um erro ao sincronizar a Live Copy&quot;. Para resolver o problema, atualize a página.
   * O texto estático em um fragmento de layout é substituído pelo nome da célula da tabela quando a primeira coluna na tabela é uma coluna de cabeçalho no modelo de canal de impressão.
   * Não é possível adicionar componentes ou ativos em nenhum local diferente da parte inferior de uma comunicação de canal da Web. Para colocá-lo em outro local, adicione um painel na parte inferior do canal da Web e reorganize usando a árvore de conteúdo.
   * Pode mover o conteúdo para a área de destino herdada do canal da Web sem remover a herança da live copy.

(CQ-4239780)

### Integração de dados

* As configurações de autenticação para serviços da Web baseados em SOAP não estão visíveis e, portanto, não podem ser configuradas nos serviços em nuvem. Para resolver o problema:

   1. No console CRXDE Lite, vá para o seguinte nó.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlautenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Atualize o valor da propriedade value para o mesmo valor da propriedade text.
   1. Clique em Salvar tudo para salvar a configuração.

(CQ-4238462)

### Integração do Acrobat Sign

* O programador do Acrobat Sign para de funcionar intermitentemente e, portanto, os formulários pendentes não são movidos para envio. Para resolver o problema, reinicie o **Suporte ao Apache Sling Scheduler** pacote do console da Web AEM em https://[*server*]:[*porta*]/system/console/bundles.

### Criação adaptável do Forms

* O componente Gráfico em formulários adaptáveis ocupa mais espaço do que normalmente.
* Uma exceção é retornada ao salvar propriedades para formulários adaptáveis, fragmentos de formulário adaptáveis ou comunicações interativas na interface do usuário do Forms Manager.
* O número máximo de caracteres especificado para uma caixa de texto de formulário adaptável não é respeitado em dispositivos Android 6.0 Samsung. (Ref# CQ-4235205)
* Às vezes, ao enviar um formulário contendo um campo de carregamento HTML padrão de um dispositivo Apple iOS, o conteúdo do arquivo não é enviado e um arquivo de 0 bytes é recebido na outra extremidade. O Apple iOS 15.1 fornece uma correção para o problema.

