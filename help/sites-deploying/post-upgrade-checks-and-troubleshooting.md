---
title: Verificações e solução de problemas da pós-atualização
seo-title: Verificações e solução de problemas da pós-atualização
description: Saiba como solucionar problemas que podem aparecer após uma atualização.
seo-description: Saiba como solucionar problemas que podem aparecer após uma atualização.
uuid: 3f83e8fc-1c45-4ef0-b8da-d29ff483d3d5
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: bc8c9aa2-f669-41f3-a526-6146ff5cf0cd
translation-type: tm+mt
source-git-commit: 7e74796c60ffa785b712d21b34a909f373587cd9
workflow-type: tm+mt
source-wordcount: '1887'
ht-degree: 0%

---


# Verificações e solução de problemas da pós-atualização{#post-upgrade-checks-and-troubleshooting}

## Verificações de pós-atualização {#post-upgrade-checks}

Após a atualização [no local](/help/sites-deploying/in-place-upgrade.md) , as seguintes atividades devem ser executadas para finalizar a atualização. Pressupõe-se que AEM foi iniciado com o jar 6.4 e que a base de código atualizada foi implantada.

* [Verificar registros para o sucesso da atualização](#verify-logs-for-upgrade-success)

* [Verificar pacotes OSGi](#verify-osgi-bundles)

* [Verificar versão do Oak](#verify-oak-version)

* [Inspect a pasta PreUpgradeBackup](#inspect-preupgradebackup-folder)

* [Validação inicial de páginas](#initial-validation-of-pages)
* [Aplicar AEM Service Packs](#apply-aem-service-packs)

* [Migrar recursos AEM](#migrate-aem-features)

* [Verificar configurações de manutenção programadas](#verify-scheduled-maintenance-configurations)

* [Ativar agentes de replicação](#enable-replication-agents)

* [Ativar Tarefas Agendadas Personalizadas](#enable-custom-scheduled-jobs)

* [Executar plano de teste](#execute-test-plan)

### Verificar registros para o sucesso da atualização {#verify-logs-for-upgrade-success}

**upgrade.log**

Anteriormente, inspecionar o estado pós-atualização da sua instância exigia uma inspeção cuidadosa de vários arquivos de log, partes do repositório e do bloco de lançamento. Gerar um relatório de atualização posterior pode ajudar a detectar atualizações defeituosas antes de entrar em funcionamento.

A principal finalidade desse recurso é reduzir a necessidade de interpretação manual ou de lógica de análise complexa em vários endpoints necessários para qualificar o sucesso de uma atualização. A solução tem como objetivo fornecer informações inequívocas para que os sistemas externos de automação reajam ao sucesso ou à falha identificada de uma atualização.

Mais especificamente, garante que:

* As falhas de atualização detectadas pela estrutura de atualização podem ser centralizadas em um único relatório de atualização;
* O relatório de atualização inclui indicadores sobre a intervenção manual necessária.

Para acomodar isso, foram feitas alterações na maneira como os logs são gerados no `upgrade.log` arquivo.

Este é um exemplo de relatório que não mostra erros durante a atualização:

![1487887443006](assets/1487887443006.png)

Este é um exemplo de relatório que mostra um pacote que não foi instalado durante o processo de atualização:

![1487887532730](assets/1487887532730.png)

**error.log**

O error.log deve ser cuidadosamente revisado durante e após o start de AEM usando o jar da versão do público alvo. Quaisquer avisos ou erros devem ser revisados. Em geral, é melhor procurar problemas no início do log. Os erros que ocorrem mais tarde no log podem ser efeitos colaterais de uma causa raiz que é chamada mais cedo no arquivo. Se ocorrerem erros e avisos repetidos, consulte abaixo para [Analisar problemas com a atualização](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-upgrade).

### Verificar pacotes OSGi {#verify-osgi-bundles}

Navegue até o console do OSGi `/system/console/bundles` e verifique se os pacotes não foram iniciados. Se algum pacote estiver em um estado instalado, consulte o para determinar `error.log` o problema raiz.

### Verificar versão do Oak {#verify-oak-version}

Após a atualização, você verá que a versão do Oak foi atualizada para **1.8.2**. Para verificar a versão Oak, navegue até o console OSGi e verifique a versão associada aos pacotes Oak: Oak Core, Oak Commons, Oak Segment Tar.

### Pasta Inspect PreUpgradeBackup {#inspect-preupgradebackup-folder}

Durante a atualização, o AEM tentará fazer backup das personalizações e armazená-las abaixo `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>`. Para visualização desta pasta no CRXDE Lite, talvez seja necessário ativar o CRXDE Lite [temporariamente](/help/sites-administering/enabling-crxde-lite.md).

A pasta com o carimbo de data e hora deve ter uma propriedade nomeada `mergeStatus` com um valor de `COMPLETED`. A pasta **para processamento** deve estar vazia e o nó **substituído** indica quais nós foram substituídos durante a atualização. O conteúdo abaixo do nó **esquerdos** indica que não foi possível mesclar com segurança durante a atualização. Se sua implementação depender de qualquer um dos nós filhos (e ainda não estiver instalado pelo seu pacote de códigos atualizado), eles precisarão ser unidos manualmente.

Desative o CRXDE Lite após este exercício se estiver em um Palco ou ambiente de produção.

### Validação inicial de páginas {#initial-validation-of-pages}

Execute uma validação inicial em relação a várias páginas no AEM. Se você estiver atualizando um ambiente do autor, abra a página Start e a página de boas-vindas ( `/aem/start.html`, `/libs/cq/core/content/welcome.html`). Nos ambientes Autor e Publicar, abra algumas páginas do aplicativo e teste de fumaça que são renderizados corretamente. Se algum problema ocorrer, consulte o `error.log` para solucionar o problema.

### Aplicar AEM Service Packs {#apply-aem-service-packs}

Aplique todos os Service Packs relevantes AEM 6.4, se tiverem sido liberados.

### Migrar recursos AEM {#migrate-aem-features}

Vários recursos no AEM exigem etapas adicionais após a atualização. Uma lista completa desses recursos e etapas para migrá-los no AEM 6.4 pode ser encontrada na página [Atualização de código e personalizações](/help/sites-deploying/upgrading-code-and-customizations.md) .

### Verificar configurações de manutenção programadas {#verify-scheduled-maintenance-configurations}

#### Enable Data Store Garbage Collection {#enable-data-store-garbage-collection}

Se estiver usando um Arquivo Data Store, verifique se a tarefa de coleta de lixo do Data Store está ativada e adicionada à lista de manutenção semanal. As instruções estão descritas [aqui](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Isso não é recomendado para instalações personalizadas de armazenamento de dados S3 ou ao usar um armazenamento de dados compartilhado.

#### Ativar a Limpeza de Revisão Online {#enable-online-revision-cleanup}

Se estiver usando MongoMK ou o novo formato de segmento TarMK, verifique se a tarefa de limpeza de revisão está ativada e adicionada à lista de manutenção diária. Instruções descritas [aqui](/help/sites-deploying/revision-cleanup.md).

### Executar plano de teste {#execute-test-plan}

Execute um plano de teste detalhado conforme definido em Código de [atualização e Personalizações](/help/sites-deploying/upgrading-code-and-customizations.md) na seção Procedimento **de** teste.

### Ativar agentes de replicação {#enable-replication-agents}

Depois que o ambiente de publicação tiver sido totalmente atualizado e validado, ative os agentes de replicação no Ambiente Autor. Verifique se os agentes podem se conectar às respectivas instâncias de Publicação. Consulte Procedimento [de](/help/sites-deploying/upgrade-procedure.md) atualização para obter mais detalhes sobre a ordem dos eventos.

### Ativar Tarefas Agendadas Personalizadas {#enable-custom-scheduled-jobs}

Quaisquer trabalhos programados como parte da base de código podem ser ativados neste ponto.

## Analisando Problemas Com A Atualização {#analyzing-issues-with-upgrade}

Esta seção contém alguns cenários de problema que podem ser enfrentados ao longo do procedimento de atualização para o AEM 6.4.

Esses cenários devem ajudar a rastrear a causa básica dos problemas relacionados à atualização e devem ajudar a identificar problemas específicos do projeto ou produto.

### Recriando a configuração da Dynamic Media Cloud após a atualização {#dynamic-media-cloud-configuration}

Após a atualização para o AEM 6.4 de uma versão anterior, a Configuração da Dynamic Media Cloud a partir de configurações anteriores pode se tornar inacessível na interface de usuário do AEM 6.4 TouchUI. Para resolver esse problema, use o CRXDE Lite para remover as configurações anteriores e, em seguida, crie uma nova Configuração da Dynamic Media Cloud. Consulte também a reestruturação do repositório do [Dynamic Media no AEM 6.4](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md).

### Falha na migração do repositório  {#repository-migration-failing-}

A migração de dados do CRX2 para o Oak deve ser viável para qualquer cenário que comece com Instâncias de origem com base no CQ 5.4. Certifique-se de seguir exatamente as instruções de atualização neste documento, que incluem a preparação do, certificando-se de que nenhum autenticador personalizado personalizado foi iniciado via JAAS e que a instância foi verificada quanto a inconsistências antes de iniciar a migração. `repository.xml`

Se a migração ainda falhar, você pode descobrir qual é a causa principal inspecionando a `upgrade.log`. Se o problema ainda não for conhecido, informe-o ao Suporte ao cliente.

### A Atualização Não Foi Executada {#the-upgrade-did-not-run}

Antes de iniciar as etapas de preparação, execute a instância **de origem** primeiro executando-a com o comando java -jar aem-quickstart.jar. Isso é necessário para garantir que o arquivo quickstart.properties seja gerado corretamente. Se estiver faltando, a atualização não funcionará. Como alternativa, você pode verificar se o arquivo está presente olhando em baixo `crx-quickstart/conf` na pasta de instalação da instância de origem. Além disso, ao iniciar o AEM para iniciar a atualização, ele deve ser executado com o comando java -jar aem-quickstart.jar. A inicialização a partir de um script de start não irá AEM start no modo de atualização.

### Pacotes e pacotes falham ao atualizar  {#packages-and-bundles-fail-to-update-}

Se os pacotes não forem instalados durante a atualização, os pacotes que eles contêm também não serão atualizados. Essa categoria de problemas costuma ser causada pela configuração incorreta do armazenamento de dados. Eles também aparecerão como mensagens **ERROR** e **WARN** no error.log. Como na maioria desses casos o logon padrão pode falhar, você pode usar o CRXDE diretamente para inspecionar e localizar os problemas de configuração.

### Alguns pacotes AEM não estão alternando para o estado ativo {#some-aem-bundles-are-not-switching-to-the-active-state}

No caso de pacotes que não estão sendo inicializados, verifique se há dependências insatisfeitas.

Caso esse problema esteja presente, mas se baseie em uma instalação de pacote com falha, o que fez com que os pacotes não fossem atualizados, eles serão considerados incompatíveis para a nova versão. Para obter mais informações sobre como solucionar problemas, consulte **Pacotes e pacotes falham na atualização** acima.

Também é recomendável comparar a lista do pacote de uma nova instância AEM 6.4 com a atualizada para detectar os pacotes que não foram atualizados. Isso fornecerá um escopo mais próximo do que procurar no `error.log`.

### Pacotes personalizados que não alternam para o estado ativo {#custom-bundles-not-switching-to-the-active-state}

Caso seus pacotes personalizados não estejam alternando para o estado ativo, é provável que haja um código que não esteja importando a API de alteração. Isso levará, com frequência, a dependências insatisfeitas.

A API que foi removida deve ser marcada como obsoleta em uma das versões anteriores. Você pode encontrar instruções sobre a migração direta do seu código neste aviso de desaprovação. O Adobe visa ao controle de versão semântico, sempre que possível, para que as versões possam indicar alterações de quebra.

Também é melhor verificar se a mudança que causou o problema foi absolutamente necessária e revertê-la, caso não seja. Verifique também se o aumento da versão da exportação do pacote foi aumentado mais do que o necessário, após o controle de versão semântico restrito.

### Interface de usuário da plataforma com mau funcionamento {#malfunctioning-platform-ui}

No caso de determinadas funcionalidades da interface que não estão funcionando corretamente após a atualização, verifique se há sobreposições personalizadas da interface. Algumas estruturas podem ter sido alteradas e a sobreposição pode precisar de uma atualização ou está obsoleta.

Em seguida, verifique se há erros do Javascript que podem ser rastreados até extensões adicionadas personalizadas que estão conectadas às bibliotecas do cliente. O mesmo pode se aplicar para CSS personalizado que pode estar causando problemas no layout AEM.

Por fim, verifique se o Javascript não consegue lidar com a configuração correta. Normalmente, isso ocorre com extensões desativadas incorretamente.

### Componentes personalizados, modelos ou extensões de interface do usuário que funcionam mal {#malfunctioning-custom-components-templates-or-ui-extensions}

Na maioria dos casos, as causas raiz desses problemas são as mesmas dos pacotes que não foram iniciados ou dos pacotes que não estão sendo instalados com a única diferença que o start de problemas ocorre ao usar os componentes pela primeira vez.

A maneira de lidar com códigos personalizados incorretos é primeiro realizar testes de fumaça para identificar a causa. Depois de encontrá-lo, examine as recomendações nesta seção de [link] do artigo para saber como corrigi-las.

### Personalizações ausentes em etc {#missing-customizations-under-etc}

`/apps` e `/libs` são bem manipuladas pela atualização, mas as alterações em `/etc` podem precisar ser restauradas manualmente `/var/upgrade/PreUpgradeBackup` após a atualização. Verifique se há algum conteúdo que precise ser unido manualmente neste local.

### Analisando o error.log e o upgrade.log {#analyzing-the-error-log-and-upgrade-log}

Na maioria das situações, os registros precisam ser consultados em busca de erros para encontrar a causa de um problema. No entanto, no caso de atualizações, também é necessário monitorar problemas de dependência, já que os pacotes antigos podem não ser atualizados corretamente.

A melhor maneira de fazer isso é eliminar o error.log, removendo todas as mensagens que devem não estar relacionadas ao problema que você está enfrentando. Você pode fazer isso por meio de uma ferramenta como grep, usando:

```shell
grep -v UnrelatedErrorString
```

Algumas mensagens de erro podem não ser explicativas imediatamente. Nesse caso, observar o contexto em que ocorrem também pode ajudar a entender onde o erro foi criado. Você pode separar o erro usando:

* `grep -B` para adicionar linhas antes do erro;

ou

* `grep -A` para adicionar linhas depois.

Em alguns casos, também é possível encontrar mensagens WARN, pois pode haver casos válidos que levam a esse estado e o aplicativo nem sempre é capaz de decidir se esse é um erro real. Consulte também essas mensagens.

### Entrando em contato com o suporte ao Adobe {#contacting-adobe-support}

Se você tiver seguido os conselhos desta página e ainda estiver vendo problemas, entre em contato com o Suporte ao Adobe. Para fornecer o máximo de informações possível ao engenheiro de suporte que trabalha em seu caso, certifique-se de incluir o arquivo upgrade.log da sua atualização.
