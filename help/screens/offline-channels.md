---
title: Canais offline
seo-title: Canais offline
description: 'O AEM Screens player fornece suporte offline para canais aproveitando a tecnologia ContentSync. Siga esta página para saber mais sobre os manipuladores de atualização e ativar a configuração offline para um canal.  '
seo-description: 'O AEM Screens player fornece suporte offline para canais aproveitando a tecnologia ContentSync. Siga esta página para saber mais sobre os manipuladores de atualização e ativar a configuração offline para um canal.  '
uuid: 25766e79-a5a5-4b84-b235-e3050f725fbe
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: developing
discoiquuid: 609d5405-138f-47f7-9ac0-efaa32f8715b
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Canais offline{#offline-channels}

O Screens player fornece suporte offline para os canais, aproveitando a tecnologia ***ContentSync*** .

Os players usam um servidor http local para servir o conteúdo descompactado.

Quando um canal é configurado para execução *online*, o player serve os recursos de canal acessando o servidor AEM, mas quando o canal é configurado para execução *offline*, o player serve os recursos de canal de um servidor http local.

O fluxo de trabalho do processo é o seguinte:

1. Analisar as páginas desejadas
1. Coletar todos os ativos relacionados
1. Empacotar tudo em um arquivo zip
1. Baixe o zip e extraia-o localmente
1. Exibir cópia local do conteúdo

## Manipuladores de Atualização {#update-handlers}

O ***ContentSync*** usa manipuladores de atualização para analisar e coletar todas as páginas e ativos necessários para um projeto específico. O AEM Screens usa os seguintes manipuladores de atualização:

### Opções comuns {#common-options}

* *tipo*: o tipo de manipulador de atualização a ser usado
* *caminho*: caminho para o recurso
* *[targetRootDirectory]*: pasta de destino no arquivo zip

<table> 
 <tbody>
  <tr>
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrição</strong></td> 
   <td><strong>Opções</strong></td> 
  </tr>
  <tr>
   <td> canais</td> 
   <td>coleta um canal</td> 
   <td>extensão: extensão do recurso para coletar<br /> [pathSuffix='']: sufixo para adicionar ao caminho<br /> do canal [deep=true]: se as páginas secundárias devem ser analisadas recursivamente<br /> [includeImages=true]: incluir todas as imagens no canal<br /> [includeVideos=true]: inclua todos os vídeos no canal<br /> [includeProducts=true]: incluir todos os produtos no canal</td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>coletar a biblioteca de cliente especificada</td> 
   <td>[extension='']: pode ser css ou js, para coletar somente a primeira, ou apenas a última</td> 
  </tr>
  <tr>
   <td>ativos</td> 
   <td>coletar as representações de ativos</td> 
   <td>[execuções=[]]: lista de representações a serem coletadas. O padrão é a execução original</td> 
  </tr>
  <tr>
   <td>copiar</td> 
   <td>copiar a estrutura especificada do caminho</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Teste da configuração do ContentSync {#testing-contentsync-configuration}

Siga as etapas abaixo para testar a configuração do ContentSync:

1. Abra [http://localhost:4502/libs/cq/contentsync/content/console.html](http://localhost:4502/libs/cq/contentsync/content/console.html)
1. Selecione sua configuração na lista
1. Clique em Limpar cache
1. Clique em Atualizar cache
1. Clique em Download completo
1. Extraia o arquivo zip
1. Iniciar um servidor local na pasta extraída
1. Abra a página inicial e verifique o status do aplicativo

## Ativar a configuração offline para um canal {#enabling-offline-config-for-a-channel}

Siga as etapas abaixo para ativar a configuração offline para um canal:

1. Inspecione o conteúdo do canal e verifique se ele foi solicitado de uma instância do AEM (Online).

   ![chlimage_1-15](assets/chlimage_1-15.png)

1. Navegue até o painel do canal e clique em **... **em INFORMAÇÕES SOBRE** CANAL **Painel para alterar as propriedades.

   ![chlimage_1-16](assets/chlimage_1-16.png)

1. Navegue até as propriedades do canal e verifique se a caixa de seleção está desativada na guia **Canal** . Clique em **Salvar e fechar**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Antes que o conteúdo seja implantado corretamente no dispositivo, clique em **Atualizar conteúdo** offline.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   O status **Offline** em **PROPRIEDADES** também é atualizado de acordo.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspecione o conteúdo do canal e verifique se ele foi solicitado do Player-Cache local.

   ![chlimage_1-17](assets/chlimage_1-17.png)

