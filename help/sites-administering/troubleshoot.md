---
title: Solução de problemas do AEM
seo-title: Troubleshooting AEM
description: Saiba mais sobre como solucionar problemas com o AEM.
seo-description: Learn about troubleshooting issues with AEM.
uuid: d68e9ead-8aa6-4108-9f1e-85d7cd7a370f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 1bc19f9a-fa3f-43e3-813e-23ab0b708d43
exl-id: 34b509d5-4e80-4229-b155-40004856e87e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 4%

---

# Solução de problemas do AEM{#troubleshooting-aem}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A seção a seguir aborda alguns problemas que você pode encontrar ao usar o AEM, juntamente com sugestões sobre como resolvê-los.

>[!NOTE]
>
>Se você estiver solucionando problemas de criação no AEM, consulte [Solução de problemas para autores.](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>Ao enfrentar problemas, também vale a pena verificar a lista de [Problemas conhecidos](/help/release-notes/known-issues.md) para sua instância (pacotes de versões e serviços).

## Cenários de solução de problemas para administradores {#troubleshooting-scenarios-for-administrators}

A tabela a seguir fornece uma visão geral dos problemas que os administradores podem precisar para solucionar:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Função(ões)</strong></td> 
   <td><strong>Problema </strong></td> 
  </tr> 
  <tr> 
   <td>Administrador do sistema</td> 
   <td><p>Clicar duas vezes no jar do Quickstart não terá efeito ou abrirá o arquivo jar com outro programa (por exemplo, gerenciador de arquivos)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrador do sistema</p> </td> 
   <td><p>Meu aplicativo em execução no CRX gera erros de falta de memória</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrador do sistema</p> </td> 
   <td><p>A tela de boas-vindas AEM não é exibida no navegador após clicar duas vezes AEM CM Quickstart</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrador do sistema</p> <p>usuário administrador</p> </td> 
   <td><p>Fazer um despejo de encadeamento</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrador do sistema</p> <p>usuário administrador</p> </td> 
   <td><p>Verificando se há sessões JCR não fechadas</p> </td> 
  </tr> 
 </tbody> 
</table>

## Problemas de instalação {#installation-issues}

Consulte [Problemas de instalação comuns](/help/sites-deploying/troubleshooting.md#common-installation-issues) para obter informações sobre os seguintes cenários de solução de problemas:

* Clicar duas vezes no jar do Quickstart não terá efeito ou o arquivo JAR com outro programa (como o gerenciador de arquivos).
* Os aplicativos em execução em CRX lançam erros de falta de memória.
* A tela AEM Welcome não é exibida no navegador após clicar duas vezes AEM Quickstart.

## Métodos para análise de solução de problemas {#methods-for-troubleshooting-analysis}

### Fazer um despejo de encadeamento {#making-a-thread-dump}

O despejo de threads é uma lista de todos os threads Java que estão ativos no momento. Se AEM não responder corretamente, o despejo de thread poderá ajudar a identificar bloqueios ou outros problemas.

### Uso do despejo de encadeamento Sling {#using-sling-thread-dumper}

1. Abra o **Console da Web AEM**; por exemplo em `http://localhost:4502/system/console/`.

1. Selecione o **Threads** under **Status** guia .

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### Uso de jstack (linha de comando) {#using-jstack-command-line}

1. Encontre o PID (id do processo) da instância AEM do Java.

   Por exemplo, você pode usar `ps -ef` ou `jps`.

1. Executar:

   `jstack <pid>`

1. Isso mostrará o despejo de encadeamento.

>[!NOTE]
>
>Você pode anexar os dumps de encadeamento a um arquivo de log usando o `>>` redirecionamento de saída:
>
>`jstack <pid> >> /path/to/logfile.log`

Consulte a [Como tirar os despejos de encadeamento de uma JVM](https://helpx.adobe.com/cq/kb/TakeThreadDump.html) documentação para obter mais informações

### Verificando se há sessões JCR não fechadas {#checking-for-unclosed-jcr-sessions}

Quando a funcionalidade é desenvolvida para AEM WCM, as Sessões JCR podem ser abertas (comparável à abertura de uma conexão de banco de dados). Se as sessões abertas nunca estiverem fechadas, o sistema poderá apresentar os seguintes sintomas:

* O sistema fica mais lento.
* Você pode ver muito do CacheManager: resizeAll entradas no arquivo de log; o seguinte número (tamanho=&lt;x>) mostra o número de caches, cada sessão abre vários caches.
* De tempos em tempos, o sistema fica sem memória (após algumas horas, dias ou semanas - dependendo da gravidade).

Para analisar sessões não fechadas e descobrir qual código não está fechando uma sessão, consulte o artigo da Base de conhecimento [Analisar Sessões Não Fechadas](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html).

### Uso do Console da Web do Adobe Experience Manager {#using-the-adobe-experience-manager-web-console}

O status dos pacotes OSGi também pode fornecer uma indicação prévia de possíveis problemas.

1. Abra o **Console da Web AEM**; por exemplo em `http://localhost:4502/system/console/`.

1. Selecionar **Pacotes** under **OSGI** guia .

1. Verificar:

   * o Status dos pacotes. Se algum estiver Inativo ou insatisfeito, tente parar e reiniciar o pacote. Se o problema persistir, talvez seja necessário investigar mais detalhadamente usando outros métodos.
   * se qualquer um dos pacotes tem dependências ausentes. Esses detalhes podem ser visualizados clicando no Nome do pacote individual, que é um link (o exemplo a seguir não tem problemas):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
