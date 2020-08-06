---
title: Solução de problemas AEM
seo-title: Solução de problemas AEM
description: Saiba mais sobre como solucionar problemas com o AEM.
seo-description: Saiba mais sobre como solucionar problemas com o AEM.
uuid: d68e9ead-8aa6-4108-9f1e-85d7cd7a370f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 1bc19f9a-fa3f-43e3-813e-23ab0b708d43
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 10%

---


# Solução de problemas AEM{#troubleshooting-aem}

A seção a seguir aborda alguns problemas que podem ocorrer ao usar AEM, juntamente com sugestões sobre como solucioná-los.

>[!NOTE]
>
>Se você estiver solucionando problemas de criação no AEM, consulte [Solução de problemas para autores.](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>Ao enfrentar problemas, também é válida a verificação da lista de [Problemas conhecidos](/help/release-notes/known-issues.md) para a sua instância (pacotes de versões e serviços).

## Cenários de solução de problemas para administradores {#troubleshooting-scenarios-for-administrators}

A tabela a seguir fornece uma visão geral dos problemas que os administradores podem precisar resolver:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Função(ões)</strong></td> 
   <td><strong>Problema </strong></td> 
  </tr> 
  <tr> 
   <td>Administrador do sistema</td> 
   <td><p>Clicar no Duplo do jar do Quickstart não tem nenhum efeito ou abre o arquivo jar com outro programa (por exemplo, gerenciador de arquivamento)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrador do sistema</p> </td> 
   <td><p>Meu aplicativo em execução no CRX emite erros de falta de memória</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrador do sistema</p> </td> 
   <td><p>A tela de boas-vindas do AEM não é exibida no navegador após clicar no duplo AEM Início rápido do CM</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrador do sistema</p> <p>usuário administrador</p> </td> 
   <td><p>Como fazer um despejo de encadeamento</p> </td> 
  </tr> 
  <tr> 
   <td><p>Administrador do sistema</p> <p>usuário administrador</p> </td> 
   <td><p>Verificando sessões JCR não fechadas</p> </td> 
  </tr> 
 </tbody> 
</table>

## Problemas de instalação {#installation-issues}

Consulte Problemas [de instalação](/help/sites-deploying/troubleshooting.md#common-installation-issues) comuns para obter informações sobre os seguintes cenários de solução de problemas:

* Clique duas vezes no ícone de Início rápido não tem nenhum efeito ou o arquivo JAR é iniciado com outro programa (como o gerenciador do arquivos).
* Os aplicativos em execução em CRX resultam em erros de falta de memória.
* A tela de boas-vindas do AEM não exibe no navegador depois de clicar duas vezes no Início rápido do AEM.

## Métodos para solução de problemas de Análise {#methods-for-troubleshooting-analysis}

### Como fazer um despejo de encadeamento {#making-a-thread-dump}

O despejo de thread é uma lista de todos os threads Java que estão ativos no momento. Se o AEM não responder corretamente, o despejo de encadeamento poderá ajudá-lo a identificar bloqueios ou outros problemas.

### Usando o Sling Thread Dumper {#using-sling-thread-dumper}

1. Abra o console **da Web** AEM; por exemplo em `http://localhost:4502/system/console/`.

1. Selecione **Threads** na **guia Status** .

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### Usando jstack (linha de comando) {#using-jstack-command-line}

1. Encontre o PID (ID do processo) da instância do Java AEM.

   Por exemplo, você pode usar `ps -ef` ou `jps`.

1. Executar:

   `jstack <pid>`

1. Isso mostrará o despejo de thread.

>[!NOTE]
>
>Você pode anexar os despejos de thread a um arquivo de log usando o redirecionamento de `>>` saída:
>
>`jstack <pid> >> /path/to/logfile.log`

Consulte [Como tirar os Thread Dumps de uma documentação JVM](https://helpx.adobe.com/cq/kb/TakeThreadDump.html) para obter mais informações

### Verificando sessões JCR não fechadas {#checking-for-unclosed-jcr-sessions}

Quando a funcionalidade é desenvolvida para AEM WCM, as Sessões JCR podem ser abertas (comparável à abertura de uma conexão de banco de dados). Se as sessões abertas nunca forem fechadas, seu sistema poderá apresentar os seguintes sintomas:

* O sistema fica mais lento.
* Você pode ver um monte de CacheManager: redimensionarTodas as entradas no arquivo de log; o número a seguir (size=&lt;x>) mostra o número de caches, cada sessão abre vários caches.
* De tempos em tempos, o sistema fica sem memória (após algumas horas, dias ou semanas - dependendo da gravidade).

Para analisar sessões não fechadas e descobrir qual código não está fechando uma sessão, consulte o artigo da Base de conhecimento [Analisar sessões](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html)não fechadas.

### Usando o Adobe Experience Manager Web Console {#using-the-adobe-experience-manager-web-console}

O estatuto dos pacotes OSGi também pode dar uma indicação precoce de possíveis emissões.

1. Abra o console **da Web** AEM; por exemplo em `http://localhost:4502/system/console/`.

1. Selecione **Pacotes** na guia **OSGI** .

1. Marcar:

   * o Status dos pacotes. Se algum estiver Inativo ou insatisfeito, tente parar e reiniciar o pacote. Se o problema persistir, talvez seja necessário investigar mais detalhadamente usando outros métodos.
   * se algum dos pacotes tem dependências ausentes. Esses detalhes podem ser vistos clicando no Nome do pacote individual, que é um link (o exemplo a seguir não tem problemas):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)

