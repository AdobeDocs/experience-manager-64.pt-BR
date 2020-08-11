---
title: Sobre o upload e o processamento de ativos 3D no AEM
seo-title: Sobre o upload e o processamento de ativos 3D no AEM
description: Práticas recomendadas para fazer upload e processar ativos 3D.
seo-description: Práticas recomendadas para fazer upload e processar ativos 3D.
uuid: d8abf460-adff-4f0f-92ae-2c8651a17488
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: a0319701-21eb-4b7f-8b2e-ac81a7a75875
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 67%

---


# Sobre o upload e o processamento de ativos 3D no AEM {#about-the-uploading-and-processing-of-d-assets-in-aem}

>[!IMPORTANT]
>
>AEM 3D no AEM 6.4 não é mais suportado. O Adobe recomenda que você use o recurso de ativos 3D em [AEM como um Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) ou [AEM 6.5.3 ou superior.](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html).

Use mecanismos padrão de upload ou sincronização para trazer recursos 3D e seus arquivos referenciados associados ao AEM Assets.

Consulte [Upload de ativos](managing-assets-touch-ui.md#uploading-assets).

O Adobe recomenda que você carregue todos os arquivos referenciados antes ou ao mesmo tempo que carregue o arquivo de modelo 3D primário. No entanto, isso não é um requisito.

Quando o upload é concluído, seus arquivos 3D são convertidos, e um processamento adicional é aplicado para preparar o ativo para visualização e renderização.

## Práticas recomendadas para carregar ativos 3D {#best-practices-for-uploading-d-assets}

* Geralmente, não há restrições sobre onde você faz o upload do conteúdo 3D na hierarquia de pastas do AEM Assets. No entanto, a resolução automatizada de dependências de arquivos do AEM 3D tem limitações de alcance para controlar o tempo necessário para pesquisar repositórios de ativos muito grandes. Portanto, a Adobe recomenda que, ao fazer o upload de ativos 3D e seus dependentes de arquivos, você o faça com uma proximidade razoável de cada arquivo (pasta avô comum). Depois que as dependências de arquivos forem resolvidas, você poderá mover livremente o ativo 3D e seus dependentes para qualquer lugar dentro do repositório, sem perder os relacionamentos estabelecidos.
* A Adobe recomenda que você escolha uma estrutura de pastas consistente para o conteúdo 3D *antes* de fazer o upload. As dicas a seguir são algumas das abordagens sugeridas que você pode empregar:

   * **Mantenha uma pasta separada para cada ativo 3D que você carregar**.

      A pasta contém o arquivo de modelo 3D principal e todos os seus dependentes. Embora seja fácil implementar todos os ativos e dependentes em uma só pasta, é difícil procurar conteúdo. Isso também complica o compartilhamento de dependentes (mapas de textura) entre os modelos.

   * **Mantenha os modelos em uma pasta e os dependentes em uma subpasta ou pasta irmão**.

      Essa abordagem oferece suporte imediato para o compartilhamento de dependentes entre modelos. No entanto, pode se tornar difícil encontrar dependentes específicos quando o número de ativos é grande.

   * **Hierarquias de pastas separadas e paralelas para modelos e dependentes**.

      Você pode modelar essa abordagem para como os aplicativos de criação 3D, como o Autodesk Maya, preferem armazenar conteúdo.

* Ativos dependentes não devem ser excluídos, a menos que o ativo 3D associado ou os ativos que os referenciavam também sejam removidos. No entanto, você pode excluir ativos 3D sem a necessidade de excluir seus ativos dependentes. Se uma dependência for perdida acidentalmente, você poderá resolver facilmente a dependência para restaurá-la.

   Consulte Resolução de dependências de arquivos.

## Considerações de desempenho ao fazer o upload de arquivos 3D {#performance-considerations-when-uploading-d-files}

Em geral, converter e processar arquivos 3D consome recursos significativos de CPU e memória em um servidor. Esse processo também exige uma quantidade substancial de tempo. Os tempos de processamento geralmente variam muito, dependendo do tamanho do modelo e das capacidades do servidor. Por exemplo, um típico modelo pequeno com menos de 100 mil faces geralmente está pronto para visualização em menos de um minuto e é totalmente processado em 2 a 3 minutos. Por outro lado, um modelo grande com mais de um milhão de faces pode levar dezenas de minutos para ser processado completamente.

Tarefas de conversão, processamento e renderização são enfileiradas conforme necessário para evitar a redução excessiva do servidor. The message &quot;Waiting for processing...&quot; is sometimes shown in the **[!UICONTROL Card View]** at the time you uploaded assets. Esse status indica que outras tarefas de processamento ou renderização devem ser concluídas antes que o ativo atual seja processado.

Há mecanismos disponíveis para restringir o uso da CPU para processamento de ingestão e renderização. Consulte Configurações [](advanced-config-3d.md) avançadas para obter informações sobre como configurar os limites da CPU.

## Monitoramento do status de processamento dos seus arquivos 3D carregados {#monitoring-the-processing-status-of-your-uploaded-d-files}

In **[!UICONTROL Card View]** only, the processing status and progression is displayed as a progress banner on the asset&#39;s card. Cada modelo 3D carregado normalmente passa pelas seguintes 4 a 6 etapas de processamento solicitado:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Fase de processamento</strong><br /> </td> 
   <td><strong>Nomes de processamento</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>Processando</td> 
   <td>Processamento inicial básico e extração de metadados.</td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>Formato de conversão</td> 
   <td>O modelo 3D está sendo convertido de um formato nativo (Autodesk® Maya® ou Autodesk® 3ds Max®) para um formato intermediário (FBX).</td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>Criando pré-visualização</td> 
   <td>O arquivo FBX ou OBJ é assimilado e processado. Dependências de arquivos são avaliadas e resolvidas como referências de ativos, quando possível.</td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>Criando sombra</td> 
   <td>Opcional. Permite gerar uma sombra projetada de oclusão ambiente no plano de solo abaixo do objeto 3D. Consulte Configurações <a href="/help/assets/advanced-config-3d.md"></a> avançadas para ativar ou desativar esse processamento.</td> 
  </tr> 
  <tr> 
   <td>5<br /> </td> 
   <td>Criação de mapas de luz</td> 
   <td>Opcional. Permite aumentar a qualidade da visualização interativa e agilizar a renderização com o renderizador padrão. Consulte Configurações <a href="/help/assets/advanced-config-3d.md"></a> avançadas para ativar ou desativar esse processamento.</td> 
  </tr> 
  <tr> 
   <td>6<br /> </td> 
   <td>Criação de animação</td> 
   <td>Opcional. Permite renderizar uma animação simples que é usada como uma miniatura visual na Visualização de cartão. Consulte Configurações <a href="/help/assets/advanced-config-3d.md"></a> avançadas para ativar ou desativar esse processamento.</td> 
  </tr> 
  <tr> 
   <td>7<br /> </td> 
   <td>Aguardando processamento</td> 
   <td>Exibido quando outros ativos 3D têm prioridade de processamento. Por exemplo, ativos que foram enviados anteriormente, mas ainda não concluíram o processamento.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>You can view a 3D asset in **[!UICONTROL Detail View]** or render it after the Creating preview stage is complete. Você não precisa esperar que todas as etapas de processamento sejam concluídas.

